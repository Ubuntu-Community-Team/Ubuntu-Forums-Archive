---
title: "Man---i need install help !!!"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-09
:mad::confused::frown:
 
Well my new pc arrived yesterday---yay... But as expected i made a mess out of my install---boo...
 
The pc came with no os... I decided to install ubuntu first and maybe windows later...
 
 
**HERE IS WHERE I NEED HELP !!!**
 
 
1. I thought I made 2 partitions but it turned out i only had 1 on a 320gb hdd...
 
2. none of the drivers for mb, audio, gig lan, etc. were installed by the builder...
 
3. I have very little pc knowledge!!!
 
4. I do not know how to install the driver discs... All attempts have failed...
 
5. I think i need to somehow get 2 partitions created each abt 1/2 of the hdd ???
 
6. I am tempted to try to format the hdd and start from square 1 but don't know how...
 
7. Can anyone help me out here ??? Non-geek talk with really entry level language if at all possible please...
 
8. i am on a borrowed win 98 SLOW borrowed pc here and am itching to play with the new quad core !!! lol...
 
9. Thanks in advance for your help and time with my issues...
 
 
NOTAGEEK

---

### Post by Mark Phelps on 2009-07-09
Don't know how you ended up with one partition.  The default installation from the LiveCD creates two partitions, one to hold all the directories, and one for swap.

As to the drivers, if you're talking about MS Windows drivers, you can't use them in Ubuntu, since it needs Linux drivers and will automatically install them based on the results of hardware detection during install.

You can repartition the drive by booting from the LiveCD and running the Partition Editor.

---

### Post by alexlafreniere on 2009-07-09
Okay first off, what version of Ubuntu are you trying to install? For the purpose of answering questions I'm going to assume the latest, 9.04 for now. What kind of computer are you trying to install it on? Was it custom built? The LiveCD version of the Ubuntu install disc makes it fairly easy to partition your disc before install, it comes with a full version of GParted. What is the second partition for? Do you plan on dual-booting? If you can get the LiveCD to boot without any problems, you can be fairly sure that once installed the OS will behave exactly the same, only faster. To be sure, when trying to install again, i would select the option to use the whole disk, and start from scratch.

---

### Post by ZeldeR on 2009-07-09
you should install windows first ;)

---

### Post by night_fox on 2009-07-09
Firstly, as ZeldeR just said, its better to install windows, THEN install ubuntu. That way, your bootloader is a program called grub, which, unlike any windows bootloader, recognises other operating systems. So go and install windows first.

Secondly, you wont need any cd other than the ubuntu cd to install Ubuntu. Ubuntu has most of the drivers on the livecd, and can download drivers for all your peripherals 

Thirdly, when your in the partition editor on the livecd, always choose manual.

---

### Post by NOTAGEEK on 2009-07-09
> **Mark Phelps said:**
> As to the drivers, if you're talking about MS Windows drivers, you can't use them in Ubuntu, since it needs Linux drivers and will automatically install them based on the results of hardware detection during install.
 
You can repartition the drive by booting from the LiveCD and running the Partition Editor.
 
 
 
HMMM  I have no audio, lan, etc. and dont know how to turn them on...
 
 
 
 
> **alexlafreniere said:**
> Okay first off, what version of Ubuntu are you trying to install? For the purpose of answering questions I'm going to assume the latest, 9.04 for now. What kind of computer are you trying to install it on? Was it custom built? The LiveCD version of the Ubuntu install disc makes it fairly easy to partition your disc before install, it comes with a full version of GParted. What is the second partition for? Do you plan on dual-booting? If you can get the LiveCD to boot without any problems, you can be fairly sure that once installed the OS will behave exactly the same, only faster. To be sure, when trying to install again, i would select the option to use the whole disk, and start from scratch.
 
 
9.04---yes custom built pc (my fault huh ???) woulda shoulda coulda...  im thinking abt win 7 dual boot later... the live cd is installed... if i reinstall should i not format the hdd ???

---

### Post by NOTAGEEK on 2009-07-09
> **ZeldeR said:**
> you should install windows first ;)
 
 
 
Dont know if i want windows---but mighttry win 7 later... if i could get on the net i might install the win 7 rc but not sure...
 
 
 
> **night_fox said:**
> Firstly, as ZeldeR just said, its better to install windows, THEN install ubuntu. That way, your bootloader is a program called grub, which, unlike any windows bootloader, recognises other operating systems. So go and install windows first.
 
Secondly, you wont need any cd other than the ubuntu cd to install Ubuntu. Ubuntu has most of the drivers on the livecd, and can download drivers for all your peripherals 
 
Thirdly, when your in the partition editor on the livecd, always choose manual.
 
 
 
see above abt windows...  i have no net no audio etc and 9.04 is installed... guess i better try booting from the 9.04 disc and start over ???

---

### Post by apostate on 2009-07-09
> **NOTAGEEK said:**
> Dont know if i want windows---but mighttry win 7 later... if i could get on the net i might install the win 7 rc but not sure...
 
 
 

 
 
 
see above abt windows...  i have no net no audio etc and 9.04 is installed... guess i better try booting from the 9.04 disc and start over ???

Ok, hold on. Do you have internet on that box? If so, chances are you're 90% fine, you might just have an audio problem. By LAN do you mean no Windows file-sharing, or no *Internet*?

---

### Post by LewRockwell on 2009-07-09
Does/did the liveCD function with these devices?

ps-please don't make multiple threads regarding what is basically one trouble-call

thanks

.

---

### Post by NOTAGEEK on 2009-07-11
> **apostate said:**
> Ok, hold on. Do you have internet on that box? If so, chances are you're 90% fine, you might just have an audio problem. By LAN do you mean no Windows file-sharing, or no *Internet*?

hi---by lan i meant internet which i now have... i now also have audio although not much volume... 


> **LewRockwell said:**
> Does/did the liveCD function with these devices?

ps-please don't make multiple threads regarding what is basically one trouble-call

thanks.

lew---the live cd never seemed to do anything...  when i tried to run the os from disc it just sat there for abt 15 minutes and did nothing...  i then lost patience and installed the os...

---

### Post by carml on 2009-07-11
If the first time you choose Try Ubuntu without any change,yes it isn't an option to install,a better explanation of what you did could help us to understand how to help you. ;)

---

### Post by Elep.Repu on 2009-07-11
If you have no audio,
didn't have audio with the live disk,
and that is important to you,
then restart.
install windows.

After you've figured out all the drivers you need. Research on getting it all set up on linux. 
I'm surprised it isn't working for you,
ubuntu is pretty good at detecting these things..

---

### Post by Skorzen on 2009-07-11
Let us know what your PC is made of.
```
$ lspci
```

---

### Post by presence1960 on 2009-07-11
> **ZeldeR said:**
> you should install windows first ;)

it is not necessary to install windows first- that is the biggest myth on this forum. A lot of people perpetuate that myth because they do not understand the installation process for Linux and/or windows. If you install linux first, then install windows all that happens is your GRUB is overwritten by windows. All you need to do is restore GRUB after the install of windows is complete. see here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

read these please.

---

### Post by NOTAGEEK on 2009-07-11
> **carml said:**
> If the first time you choose Try Ubuntu without any change,yes it isn't an option to install,a better explanation of what you did could help us to understand how to help you. ;)

most all problems have have been resolved and i tagged this thread solved abr an hour ago... thanks...

> **Elep.Repu said:**
> If you have no audio,
didn't have audio with the live disk,
and that is important to you,
then restart.
install windows.

After you've figured out all the drivers you need. Research on getting it all set up on linux. 
I'm surprised it isn't working for you,
ubuntu is pretty good at detecting these things..


most glitches resolved---thread tagged solved abt an hour ago...  working to skill/nerve level to install ubuntu studio... thanks...

---

### Post by NOTAGEEK on 2009-07-11
> **Skorzen said:**
> Let us know what your PC is made of.
```
$ lspci
```


had to drop the $ off the beginning to get results...



kind of exiting huh ???

now if i only knew what that stuff meant... :guitar:

---

### Post by NOTAGEEK on 2009-07-11
> **presence1960 said:**
> it is not necessary to install windows first- that is the biggest myth on this forum. A lot of people perpetuate that myth because they do not understand the installation process for Linux and/or windows. If you install linux first, then install windows all that happens is your GRUB is overwritten by windows. All you need to do is restore GRUB after the install of windows is complete. see here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

read these please.


WOW !!!  good stuff... still above myskill level...  i guess this thread lives !!! thanks...

---

### Post by credobyte on 2009-07-11
> **Elep.Repu said:**
> If you have no audio,
didn't have audio with the live disk,
and that is important to you,
then restart.
try configuring/installing your audio drivers again.


Fixed :p

---

