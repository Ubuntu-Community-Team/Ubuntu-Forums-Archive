---
title: "Wireless help."
date: 2011-03-11
forum: New to Ubuntu
---

### Post by mc228608 on 2011-03-11
**Wireless problems** 
I have 04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
 
so i need the required firmware files to make my wireless work.
I have been trying to find help for some time now, but i don't believe  that Ive been expressing the correct parameters so here we go:
 
>>I need to navigate to my Home Folder an open up a file Via The terminal
HOW?
NO i can not use the ether net for it does not work as well.
NO I cant double click because its not a software package its a Tar archi...
NO i am not able to hit open with and find GDebi either
 
I pretty much need to follow these (as follows) instruction:
 
 
**b43 - No Internet access**
 
If you do not have any other means of Internet access on your computer,  you will have to install b43-fwcutter and patch packages from the  install media. After that you will need to setup firmware manually  (without the firmware automatically downloading and being set up). 
**[FONT=&quot]Setp 1.[/FONT]** 
b43-fwcutter is located on the Ubuntu install media under **[FONT=&quot]../pool/main/b/b43-fwcutter/[/FONT]** and patch is located under **[FONT=&quot]../pool/main/p/patch/[/FONT]** **[FONT=&quot]or[/FONT]** both in the official repositories online. 
Double click on the package to install **[FONT=&quot]or[/FONT]** in a **[FONT=&quot]terminal[/FONT]** (under the desktop menu **[FONT=&quot]Applications > Accessories > Terminal[/FONT]**) navigate to the folder containing the package and issue the following command: 
:/b43-fwcutter/$ sudo dpkg -i b43-fwcutter*
**[FONT=&quot]Step 2.[/FONT]** 
On a computer with Internet access, download the required firmware files from [[COLOR=#444444]http://downloads.openwrt.org/sources...a-3.130.20.0.o[/COLOR]]("http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o") and [[COLOR=#444444]http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2[/COLOR]]("http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2") 
**[FONT=&quot]Step 3.[/FONT]** 
Copy the downloaded files to your home folder and execute the following  commands consecutively in a terminal to extract and install the  firmware: 
~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2~$ sudo b43-fwcutter -w  /lib/firmware wl_apsta-3.130.20.0.o~$ sudo b43-fwcutter --unsupported -w  /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
**[FONT=&quot]Step 4.[/FONT]** 
Under the desktop menu **[FONT=&quot]System > Administration > Hardware Drivers[/FONT]**, the **[FONT=&quot]b43[/FONT]** drivers can be activated for use. 
**[FONT=&quot]Note:[/FONT]** A computer restart may be required before using the wifi card. 
**LiveCD/LiveUSB**
 
**[FONT=&quot]Note:[/FONT]** The install media contents are mounted under **[FONT=&quot]/cdrom[/FONT]** of the filesystem. 
**[FONT=&quot]Step 5.[/FONT]** 
For temporary use with the LiveCD and LiveUSB environments, instead of a  computer restart, in a terminal issue the following commands: 
~$ sudo modprobe -r b43 ssb~$ sudo modprobe b43

---

### Post by williejones on 2011-03-11
> >>I need to navigate to my Home Folder an open up a file Via The terminalFrom the terminal type

```
cd ~
```The ~ is beside the number 1 (with shift key) on my keyboard

---

