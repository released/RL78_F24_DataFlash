# RL78_F24_DataFlash
 RL78_F24_DataFlash

1. initial F24 EVB , to test data flash library

- UART : P15,P16 , to printf message

2. refer to document : R20CD0026EJ0100

https://www.renesas.com/en/document/oth/rl78-family-flash-memory-reprogramming-software-introduction?srsltid=AfmBOoorBWh_R-o9JLZl8Bgw3UVoWPQmjFYB2BGc9AYP7uG9vnW98Ef6

download F24 flash driver (RFD RL78 Type 02 ) : RFDRL78T02

https://www.renesas.com/us/en/document/scd/renesas-flash-driver-rl78-type02-rl78f23-and-rl78f24?r=488891

follow F24 flash driver : RFDRL78T02 user manual procedure

https://www.renesas.com/us/en/search?keywords=R20UT5009EJ

modify **cstart.asm** and section define in CS+

3. refer to \RFDRL78T02\sample\RL78_F24\DF\CCRL\source\cstart.asm and modify project cstart.asm ( add section ROM to RAM )

![image](https://github.com/released/RL78_F24_DataFlash/blob/main/cstart_asm_1.jpg)

![image](https://github.com/released/RL78_F24_DataFlash/blob/main/cstart_asm_2.jpg)

![image](https://github.com/released/RL78_F24_DataFlash/blob/main/cstart_asm_3.jpg)


4. below is CS+ property modification : Device

![image](https://github.com/released/RL78_F24_DataFlash/blob/main/CCRL_Link_Device.jpg)

smart configurator setting

![image](https://github.com/released/RL78_F24_DataFlash/blob/main/smc_01.jpg)

5. below is CS+ property modification : 

![image](https://github.com/released/RL78_F24_DataFlash/blob/main/CCRL_Link_Section1.jpg)

![image](https://github.com/released/RL78_F24_DataFlash/blob/main/CCRL_Link_Section2.jpg)

6. refer to \RFDRL78T02\sample\RL78_F24\DF\CCRL\source\cstart.asm\main.c

**key point** : must disable interrupt before call flash driver , and enable interrupt after call flash driver

refer to Data_Flash_init , Data_Flash_read , Data_Flash_write_test

```
  BSP_DI();
  
  // when use flash driver function
  
  BSP_EI();  
```

7. 

when power on will read data flash result 

press digit 1 , will write data flash 

press digit 2 , will read data flash 


below is log message

![image](https://github.com/released/RL78_F24_DataFlash/blob/main/log1.jpg)

