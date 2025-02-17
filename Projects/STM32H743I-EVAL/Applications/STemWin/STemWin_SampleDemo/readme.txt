﻿/**
  @page STemWin_SampleDemo Readme file
 
  @verbatim
  ******************************************************************************
  * @file    STemWin_SampleDemo/readme.txt 
  * @author  MCD Application Team
  * @brief   Description of STemWin Sample Demo application.    
  ******************************************************************************
  * @attention
  *
  * <h2><center>&copy; Copyright (c) 2017 STMicroelectronics.
  * All rights reserved.</center></h2>
  *
  * This software component is licensed by ST under Ultimate Liberty license
  * SLA0044, the "License"; You may not use this file except in compliance with
  * the License. You may obtain a copy of the License at:
  *                             www.st.com/SLA0044
  *
  ******************************************************************************
   @endverbatim

@par Application Description

This directory contains a set of source files that implement a sample
demonstration application allowing to show some of the STemWin Library capabilities 
on STM32H743xx devices.

The list of modules to be used is configured into the file Demo/GUIDEMO.h

All the demo modules are running sequentially. Throughout the demonstration, a
control frame window is displayed at the bottom right of the touch screen: it
includes a progress bar and two control buttons (Next + Halt) allowing to skip
or pause the currently running module.

@note Care must be taken when using HAL_Delay(), this function provides accurate delay (in milliseconds)
      based on variable incremented in SysTick ISR. This implies that if HAL_Delay() is called from
      a peripheral ISR process, then the SysTick interrupt must have higher priority (numerically lower)
      than the peripheral interrupt. Otherwise the caller ISR process will be blocked.
      To change the SysTick interrupt priority you have to use HAL_NVIC_SetPriority() function.
      
@note The application needs to ensure that the SysTick time base is always set to 1 millisecond
      to have correct HAL operation.

@note Care must be taken when HAL_RCCEx_PeriphCLKConfig() is used to select the RTC clock source; in this 
      case the Backup domain will be reset in order to modify the RTC Clock source, as consequence RTC  
      registers (including the backup registers) and RCC_BDCR register are set to their reset values.

@Note If the  application is using the DTCM/ITCM memories (@0x20000000/ 0x0000000: not cacheable and only accessible
      by the Cortex M7 and the  MDMA), no need for cache maintenance when the Cortex M7 and the MDMA access these RAMs.
      If the application needs to use DMA(or other masters) based access or requires more RAM, then  the user has to:
              - Use a non TCM SRAM. (example : D1 AXI-SRAM @ 0x24000000)
              - Add a cache maintenance mechanism to ensure the cache coherence between CPU and other masters(DMAs,DMA2D,LTDC,MDMA).
              - The addresses and the size of cacheable buffers (shared between CPU and other masters)
                must be	properly defined to be aligned to L1-CACHE line size (32 bytes). 
 
@Note It is recommended to enable the cache and maintain its coherence.
      Depending on the use case it is also possible to configure the cache attributes using the MPU.
      Please refer to the AN4838 "Managing memory protection unit (MPU) in STM32 MCUs"
      Please refer to the AN4839 "Level 1 cache on STM32F7 Series"

@par Keywords

Graphics, Display, STemWin, LTDC, LCD, GUI, Touch screen

@par Directory contents 

  - STemWin/SampleDemo/STemWin/Target/GUIConf.h                  Header for GUIConf_STM32H743I-EVAL.c
  - STemWin/SampleDemo/STemWin/Target/LCDConf.h        		     Header for LCDConf_STM32H743I-EVAL.c
  - STemWin/SampleDemo/Core/Inc/rtc.h                            Header for rtc.c
  - STemWin/SampleDemo/Core/Inc/main.h                           Main program header file
  - STemWin/SampleDemo/Core/Inc/stm32h7xx_hal_conf.h             Library Configuration file
  - STemWin/SampleDemo/Core/Inc/stm32h7xx_it.h                   Interrupt handlers header file
  - STemWin/SampleDemo/Core/Src/rtc.c                            Main file to configure RTC clock
  - STemWin/SampleDemo/STemWin/Target/GUIConf_STM32H743I-EVAL.c	 Display controller initialization
  - STemWin/SampleDemo/STemWin/Target/LCDConf_STM32H743I-EVAL.c  Configuration file for the GUI library
  - STemWin/SampleDemo/Core/Src/main.c                           Main program file
  - STemWin/SampleDemo/Core/Src/stm32h7xx_it.c                   STM32H7xx Interrupt handlers
  - STemWin/SampleDemo/Core/Src/system_stm32h7xx.c               STM32H7xx system file
  - STemWin/SampleDemo/STemWin/App/GUIDEMO_*.c                   All the sources files provided for SEGGER DEMO
  - STemWin/SampleDemo/STemWin/App/GUIDEMO.h                     DEMO modules configuration file

@par Hardware and Software environment 

  - This application runs on STM32H743xx devices.
    
  - This application has been tested with STM32H743I-EVAL evaluation board and can be
    easily tailored to any other supported device and development board.

@par How to use it ? 

In order to make the program work, you must do the following :
  - Open your preferred toolchain 
  - Rebuild all files and load your image into target memory
  - Run the application
 
 * <h3><center>&copy; COPYRIGHT STMicroelectronics</center></h3>
 */
