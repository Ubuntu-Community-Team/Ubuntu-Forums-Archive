---
title: "Need to build installer"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by platinumsteel on 2008-05-02
Hi can someone help me how to understand this...I am new to ubuntu and I woud like to install drivers for my hawkings wireless adapter (HWU54G) Can anyone provide a step by step break down on how to install this...Your help will be greatly appreciated...thanks
2.2 Build and install the package: 
The package contains drivers for ZD1211 and ZD1211B. If you doesn’t have specified request, both of them will be installed. 
Under the extracted directory, there is a Makefile in it. Because our driver can support for kernel 2.4 and kernel 2.6, there are two sets of rule in the Makefile. One has to modify the Makefile according to the path of “kernel source tree” and the version of the kernel in your system. In the Makefile, you may see the following statements, 
# if the kernel is 2.6.x, turn on this 
#KERN_26=y 
#KERNEL_SOURCE=/usr/src/linux-2.6.7 
# if the kernel is 2.4.x, turn on this 
KERN_24=y 
KERNEL_SOURCE=/usr/src/linux-2.4.20-8 
If you want to build the kernel under the kernel of 2.4.x, one has to let the variable KERN_24=y and comment the KERN_26=y like that as the example above and modify the variable KERNEL_SOURCE to the path which you install the kernel source. After doing these things, one just need to type the “make”, and the driver module will be generated and installed. 

2.3 Install individual driver: 
If you only need driver of ZD1211 or ZD1211B, you can issue :

 make ZD1211REV_B=0 (0 for ZD1211, 1 for ZD1211B)
 make ZD1211REV_B=0 install (0 for ZD1211, 1 for ZD1211B)

to install the driver.

---

