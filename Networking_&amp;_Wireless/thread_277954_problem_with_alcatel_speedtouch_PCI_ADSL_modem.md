---
title: "problem with alcatel speedtouch PCI ADSL modem"
date: 2006-10-15
forum: Networking &amp; Wireless
---

### Post by quantik on 2006-10-15
Hi all,
I'm trying to get my internal modem to work.
It's a Speedtouch PCI with an Itex chipset

I found a driver for kernel 2.6, and it involves a recompilation, which i did. here is the readme that went with the driver:

```
The patch (use the latest version - the one with the highest number) is for 2.6.15(.*) kernels. 
Put itex.o in /root/. Use CONFIG_ATM=y (NOT m). 
Use gcc 2.9*. When you insmod pppoatm.ko (or in dmesg if it's static)
you'll see a message like 'len=92 - head=124'. 
If those figures do not match, 
it will NOT work. That's because you switched on to many/less kernel options. 
(See struct sk_buff in include/linux/skbuff.h). 
If head is too large you have to set some options to 'n'. 
If head is too small you have to set some options to 'y'. 
The driver wil be linked in the kernel at compile time, 
so you do not need to load any itex module at run time. 
The driver does not do 2.6 ACPI IRQ routing. 
Use kernel-option "acpi=noirq" or "acpi-off". 
Please mail me if it does (not) work: itex at jp.dhs.org.
```

i'm on the second line:(  : insmod pppoatm.ko
I have got a file named pppoatm.ko in /lib/modules/2.6.15-26-386/kernel/net/atm
but not in
/lib/modules/2.6.15.7-ubuntu1-itexone/kernel/net/atm (which is the directory that appeared after the kernel recompilation)

If i try 
```
insmod /lib/modules/2.6.15-26-386/kernel/net/atm/pppoatm.ko
```
It says : Invalid module format...

I dont know what to do now...
I must add that I am a complete linux newbie:-D 
Someone has an idea?
Thanks !

---

### Post by fishpie on 2006-10-29
Hi,

I think that the "invalid module format" message indicates that the kernel module that you are are trying to insert has been compiled with a different version of gcc than the kernel. From your message it seems that you have not compiled a pppoatm.ko kernel module. This may mean that ppp over atm has been statically compiled into the kernel i.e. built in, so no need to use the insmod command. 
Move into the directory that contains the kernel source that you compiled and type the following ```
grep CONFIG_PPPOATM .config
``` if this produces the following message "CONFIG_PPPOATM=y" then the ppp over ATM code has been statically compiled into the kernel, you should therefore according to the readme that you posted examine the output of the "dmesg" command to find the  'len=92 - head=124' messsage, If instead you get the message "CONFIG_PPPOATM=n" then the ppp over atm code will not have been compiled at all. If this is the case then you should open the .config file with a text editor and change the line that reads "CONFIG_PPPOATM=n" to "CONFIG_PPPOATM=m" and then recompile the kernel a pppoatm.ko module should be produced this time.

---

