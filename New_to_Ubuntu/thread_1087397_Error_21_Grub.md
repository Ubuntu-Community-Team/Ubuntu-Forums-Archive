---
title: "Error 21 Grub"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by Somiac on 2009-03-05
Okay, has anyone had this issue and I would like to know an answer like step by step or detailed on what to do so I don't kill my laptop.

Basically what happens is my computer brings up that error if my external harddrive isn't plugged in(which is what has ubuntu on it).

Some people say I have to reinstall Ubuntu with making it so when I boot from CD, my INTERNAL HDD is higher priority on the boot list then the External HDD.

But I want to make sure this is exactly what needs to be done, or is there more I need to do, or possibly less? like a way to fix without reinstalling Ubuntu...

---

### Post by sahabcse on 2009-03-05
Hi

Try to fix the grub. For fixing the grub follow below url

====================================
[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
===================================

Regards,
Sahab

---

### Post by Somiac on 2009-03-05
And what if I don't have the recovery DVD for win vista? :(
Also, will it still ask which OS I want to load if my ex.HD is plugged in after doing these steps?

---

### Post by sahabcse on 2009-03-05
Hi

You can select the system recovery mode from window vista DVD itself otherwise you try to use ubuntu live cd.

---

### Post by sahabcse on 2009-03-05
Add the external harddisk and boot from ubuntu live cd and follow the steps..............

---

### Post by sazan on 2009-03-05
Use your live CD and you can overwrite MBR using this command ->

```
sudo lilo -M /dev/sda mbr
```

hope it works :P

---

### Post by Somiac on 2009-03-05
Thanks for the pointer, however my loader is GRUB not lilo.

---

### Post by Somiac on 2009-03-05
Please note that I do not have the Vista CD(s) any longer. I am a Linux/Ubuntu newbie and would appreciate step by step instructions
(or a URL page with the step by step instructions). Thank you.

---

### Post by sazan on 2009-03-05
ok tell me in detail, what is there in your internal hdd (OS wise), do you have dual boot, or is it that you only hav one OS that is Ubuntu in external drive ??

---

### Post by Somiac on 2009-03-05
My setup is
Windows Vista on my internal HDD on my laptop, it's the only OS on it.

Ubuntu 8.10 is on my External HDD again only OS on that also.

---

### Post by sazan on 2009-03-05
can you connect your external drive, run ubuntu and give me the output of this command ->

```
cat /boot/grub/menu.lst
```

I think you need to change your boot order

---

### Post by Somiac on 2009-03-05
Yea I tried that, as in making it so when it goes to the boot menu windows vista is highlighted instead of Ubuntu? 
I will get the results of that command anyway give me like five minutes to post them up. But I think it more has to do with the GRUB boot thing being on the external harddrive and not internal or something...but I'll brb with the results of that command.

---

### Post by sazan on 2009-03-05
Also try following setting >

change the CMOS settings to detect the HD's 





enter Standard CMOS Setup



set the Primary Master to:

Type = User, Mode = LBA

by scrolling through the options



then set the Primary Slave to:

Type = Auto, Mode = Auto

---

### Post by Somiac on 2009-03-05
What is CMOS? And how do I get to it? lol! Again I'm new at this stuff...

---

### Post by sazan on 2009-03-05
go to your BIOS settings (pressing del or F2 watever ur setting is), just browse through the options available , you will find it somewhere.
Just try and let me know

---

### Post by Somiac on 2009-03-05
Okay, so my BIOS only has option to change time and date, boot order of the different hardwares, set a startup password, and allow boot from external HDD.

I have tried both enable and disable the boot from external HDD, I have also changed the boot order also...

I got the error 21 on accident again and this is exactly what it says (or close to it)

Loading GRUB Menu.....
Error 21.

That's whenever the Harddrive is not plugged into my laptop. And when it is plugged in it gives me the option to boot either ubuntu or WinVista.

---

### Post by sazan on 2009-03-05
you should have missed the setting, 
well the only solution I can find for you is to overwrite the MBR either with windows recovery tool or using linux live CD

I will recomend you to use the command I gave to overwrite MBR and let me know if it works.

 I think it should work well .

---

### Post by Somiac on 2009-03-05
What does the lilo thing in that command do? Sorry just tryin to understand also.. Because when I search it says theres two different boot systems, GRUB and LILO...so I wasn't sure if you thought I was using lilo or not?

---

### Post by sazan on 2009-03-05
[http://lwn.net/Articles/89772/](http://lwn.net/Articles/89772/)

[http://tldp.org/HOWTO/Linux-i386-Boot-Code-HOWTO/bootloader.html](http://tldp.org/HOWTO/Linux-i386-Boot-Code-HOWTO/bootloader.html)

---

### Post by Somiac on 2009-03-05
So what does your command do exactly may I ask? I'm just paranoid of typing in random commands lol!
And when you say use LiveCD do you mean to boot from it and go into the install windows? or what...

---

### Post by seppl82 on 2009-03-05
Hey,

i've had the same issue some days ago.
Okay. The problem is that grub is written to the MBR of the Internal disc and not to the MBR of the external disc.

You can fix it that way.
Boot ubuntu from your installation and typein

(while /dev/sdb is your usb stick)

grub-install /dev/sdb

To fix the windows MBR problem use this tool in windows
[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

For details look @ my thread here:
[http://ubuntuforums.org/showthread.php?t=1085883](http://ubuntuforums.org/showthread.php?t=1085883)

---

### Post by Somiac on 2009-03-05
OKay, so wait, can you give me step by step on how to do it so when I reboot I dont forget =P

Basically I put in the LIVECD and goto Ubuntu Setup? and type in grub-install /dev/sdb?

And did that fdisdk /mbr command work on DOS? and when they say DOS can you do it in the command prompt inside of windows?! and if it didn't that fixmbr program works for vista HomePremium correct?

I think that's all my questions for now...

---

### Post by seppl82 on 2009-03-05
Okay,

as far as i understood you, you can boot your ubuntu if you have the external storeage connected, right?

So what you would like is a system that is a windows that is running on the internal drive without the external disc connected right?

Currently you can boot windows and ubuntu if you have the external disc connected.

To fix the issue first of all you need to write the bootloader to the external disc (this allows you to start from the bios using the external disc as the boot device).

Kind Regards
/Seppl

---

### Post by Somiac on 2009-03-05
that mbr program you gave for fxing windows, does it work with windows vista? because it says nowhere in the documentation it's for vista, and says it's *Windows NT, Windows 2000, Windows XP, Windows Server 2003 and Windows PE*...

---

### Post by seppl82 on 2009-03-05
The Documentation itself (the html file that is created after you start the tool says it is able to handle vista)

see here:
[http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm)

You can download the latest version here
[http://www.sysint.no/Download/tabid/162/language/en-US/Default.aspx](http://www.sysint.no/Download/tabid/162/language/en-US/Default.aspx)

nevertheless, the mbr is identical in all windows versions.

---

### Post by Somiac on 2009-03-05
Okay, I did the grub-install and restored the mbr and all is well! THANKS! After like 5 hours of searching and looking Finally someone with a straight forward answer!! Thanks a lot Seppl ^_^

---

### Post by seppl82 on 2009-03-05
I had exactly the same issue 3 Days ago :-)

---

