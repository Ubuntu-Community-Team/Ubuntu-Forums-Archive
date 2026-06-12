---
title: "Samsung n145-JP02"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by tuxisapenguin on 2011-07-19
Hi,

I am considering buying a Samsung n145-JP02 netbook very soon, but I want to put Ubuntu onto it. I was wondering if anyone has any success stories with Ubuntu 10.10 UNR, 11.04, 10.04 LTS, or Kubuntu? I don't want to buy the computer if Ubuntu does not work great on the device.

Thanks!

---

### Post by tuxisapenguin on 2011-07-19
Xubuntu 11.04 would also be fine, by the way

---

### Post by maxfac on 2011-07-19
Samsung N210 here. Running 11.04. Works great (with some tweaking).

---

### Post by pqwoerituytrueiwoq on 2011-07-19
you may want to consider the netbook edition
[http://releases.ubuntu.com/lucid/ubuntu-10.04-netbook-i386.iso](http://releases.ubuntu.com/lucid/ubuntu-10.04-netbook-i386.iso)
if i have 2 panels (top/bottom) i prefer a screen hight of 792 pixels
768 would be ok with me for unity's one panel
the netbook edition is designed for small screens

---

### Post by Matt__ on 2011-07-19
The N140 works perfectly out of the box...the 145 needs some effort
[http://ubuntuforums.org/showthread.php?t=1680872&highlight=samsung+N145](http://ubuntuforums.org/showthread.php?t=1680872&highlight=samsung+N145)

---

### Post by tuxisapenguin on 2011-07-30
Got the n145, and it works great! Thanks everyone for the advice

---

### Post by rojaasensei on 2011-08-01
Using Samsung N150 Plus SG with XUBUNTU.

It's fantastic.  

Screen brightness is the only function I have not been able to enable.  Otherwise, the install was perfect.

---

### Post by Matt__ on 2011-08-01
@[rojaasensei]("http://ubuntuforums.org/member.php?u=1309764")
this worked on a friends N145
 
[FONT=arial][SIZE=2][COLOR=black]Tr[SIZE=2][FONT=Arial, Helvetica, sans-serif]y the following (from French Ubuntu forum)[/FONT][/SIZE]:[/COLOR][/SIZE][/FONT]```
sudo add-apt-repository ppa:voria/ppa
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install samsung-tools samsung-backlight
sudo reboot  
```[FONT=arial][SIZE=2][COLOR=black] 
   **[SIZE=2][FONT=Arial, Helvetica, sans-serif]I[/FONT][/SIZE]**t appears on some systems the function keys  begin working but the brightness does not change. In this case, try  appending &#8220;acpi_backlight=vendor&#8221; to the GRUB_CMDLINE_LINUX line in  Suspend / Resume below.[INDENT] ```
[SIZE=3]GRUB_CMDLINE_LINUX=&#8221;acpi_sleep=nonvs acpi_backlight=vendor&#8221;[/SIZE]
``` [/INDENT][/COLOR][/SIZE][/FONT]

---

