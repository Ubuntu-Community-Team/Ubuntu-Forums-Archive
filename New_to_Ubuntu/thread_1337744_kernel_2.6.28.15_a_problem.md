---
title: "kernel 2.6.28.15 a problem"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by DarinB on 2009-11-25
what a load of crap!!!!
I had this problem 3 months ago, and got a bunch of brilliant thoughts on the forum. i ended up with a grub boot failure did a full clean reinstall of jaunty, pc working fine. last week the system of auto updates went to 2.6.28.16, what do ya know same problems as before. crashes freeze what ever you call it. At least with windows you can ctrl alt del here a total freeze, hit the power button. I am now booting to 2.6.28.11 and i will see what is going on. I think this sucks, so much! windows is crap and i am starting to have my doubts about ubuntu!!!! i was fine with Hardy, all these interim upgrades they just cause heart ache. I went to ubuntu to save my self from the time wasting garbage from windows only to be replaced with this nonsense.

---

### Post by NoaHall on 2009-11-25
Why are you using 9.04 then? Update to 9.10.
If you're having problem with your graphics card, then I believe 9.10 has better support, and the same applies to wireless adapters.

And if everything goes over, why not go back to 8.04? It's still supported.

---

### Post by pi.boy.travis on 2009-11-25
> **DarinB said:**
> what a load of crap!!!!
I had this problem 3 months ago, and got a bunch of brilliant thoughts on the forum. i ended up with a grub boot failure did a full clean reinstall of jaunty, pc working fine. last week the system of auto updates went to 2.6.28.16, what do ya know same problems as before. crashes freeze what ever you call it. At least with windows you can ctrl alt del here a total freeze, hit the power button. I am now booting to 2.6.28.11 and i will see what is going on. I think this sucks, so much! windows is crap and i am starting to have my doubts about ubuntu!!!! i was fine with Hardy, all these interim upgrades they just cause heart ache. I went to ubuntu to save my self from the time wasting garbage from windows only to be replaced with this nonsense.

If you could provide a more specific description of your system, which version of Ubuntu you are using, and the conditions that cause the problem, we should be able to help you through your problem. . .

---

### Post by MockY on 2009-11-25
I understand you frustration. I'm having major problems with later kernels on one of the systems I am working on as well. Though my issues started with the 2.6.28-16 kernel.

---

### Post by walt.smith1960 on 2009-11-25
+1 on the Kernel version. Mine is showing 2.6.31-15. Some people have had rough going with Karmic. I can't complain. I've been using Karmic since about the 3rd or 4th alpha version. The alpha versions had minor versions but were still usable.  Karmic NBR seems a lot better than Jaunty on the Eee 1005HAB.

---

### Post by DarinB on 2009-11-25
This time the problem started with the .16 as well. 
I am really pissed off.  now i will just turn the 'f'ing thing off and get away from it. 
should a spent the 2 k on a Mac. not a new tricked out pc....sheeesh! I really want to love Ubuntu the concept is great but in practicality it is pure crap!!!!! 
The Canonical people should be embarrassed for putting out crap that does not work. I'll come back to this when i am in a better mood. Bunch of BS Ubuntu Sheeesh!

---

### Post by NoaHall on 2009-11-25
> **DarinB said:**
> This time the problem started with the .16 as well. 
I am really pissed off.  now i will just turn the 'f'ing thing off and get away from it. 
should a spent the 2 k on a Mac. not a new tricked out pc....sheeesh! I really want to love Ubuntu the concept is great but in practicality it is pure crap!!!!! 
The Canonical people should be embarrassed for putting out crap that does not work. I'll come back to this when i am in a better mood. Bunch of BS Ubuntu Sheeesh!

The fact you aren't taking on board anything we've said, and you have not listed your problems, I now declare that you are a troll and either you don't want help or you don't need help.

---

### Post by pi.boy.travis on 2009-11-25
> **DarinB said:**
> This time the problem started with the .16 as well. 
I am really pissed off.  now i will just turn the 'f'ing thing off and get away from it. 
should a spent the 2 k on a Mac. not a new tricked out pc....sheeesh! I really want to love Ubuntu the concept is great but in practicality it is pure crap!!!!! 
The Canonical people should be embarrassed for putting out crap that does not work. I'll come back to this when i am in a better mood. Bunch of BS Ubuntu Sheeesh!


If you would please provide some more information, I would be more than happy to assist you as best as I can.

---

### Post by DarinB on 2009-11-25
If you had any idea how painful it has been dealing with this you would have more compassion and not call me a troll. Please Give me a list of what you need to know about my system since you seem to be so knowledgeable. 
Or are you a post pubescent child playing at computers. 
sincerely 
the troll

---

### Post by NoaHall on 2009-11-25
> **DarinB said:**
> If you had any idea how painful it has been dealing with this you would have more compassion and not call me a troll. Please Give me a list of what you need to know about my system since you seem to be so knowledgeable. 
Or are you a post pubescent child playing at computers. 
sincerely 
the troll

I can't ask you until I know what's wrong.

Some generally useful info - 

I guess you are using Jaunty?
What is your graphics card?
What are your problems?

---

### Post by pi.boy.travis on 2009-11-25
> **DarinB said:**
> If you had any idea how painful it has been dealing with this you would have more compassion and not call me a troll. Please Give me a list of what you need to know about my system since you seem to be so knowledgeable. 
Or are you a post pubescent child playing at computers. 
sincerely 
the troll

We have all had our fair share of technological troubles. . . 

-If you could list what hardware you are using, CPU, RAM, graphics card, etc.  The more info the better.

-Exactly what conditions cause the freeze?  If it is over a specific period of time, is it consistent?  Does a certain application cause it?  If you could post the contents of the file /var/log/syslog that would be helpful as well.

-What is the exact nature of the freeze?  Can you still move the mouse?  Can you use ctrl + alt + F1 to switch to a console?  

I once had to reimage six production servers at three in the morning, as my business depends on them. . .  My uptime is measured in dollars and cents.

---

### Post by DarinB on 2009-11-25
Ok i will take a deep breath 
I am using Jaunty 
firefox 3.08 when i used 3.5xx i had constant freezes. 
not only firefox but the whole pc freezes. 
a brand new nvidia 9500gt 1GB asus Psnli motherboard.
three HDD's with a seperate /home hdd and /mnt/music hdd. lets see core 2 duo running 32 bit jaunty. 
i went through many troubleshooting things until i thought it was my nvidia card the pc manufacturer sent me a new card (above) 
I can't exactly remember all we did. but only a few days ago the kernel was updated to .15 to .16 I thought it would work since the impression was it was the graphics card. but after two days with .16 the freezes started again,,,,
After all the ranting I did above **i do appreciate all your help!!!!!! thank you**

---

### Post by DarinB on 2009-11-25
oh by the way i was running .11 kernel up to about two weeks ago...

---

### Post by NoaHall on 2009-11-25
Hm. It sounds like your nvidia drivers is messing up the kernel.
I suggest you either upgrade(fresh install for best results) to Karmic, or you:

Download the driver from the nvidia site.
Boot into recovery mode, and then -
```
sudo apt-get remove nvidia*
```
```
/home/user/location/of/nvidiafile
```
Run that, and then when it asks if you want to compile the kernel module, select yes.
Restart, and see if it works.

---

### Post by DarinB on 2009-11-25
I will need more info on downloading the nvidia driver. 
when i tried the third party drivers from restricted drivers it messed up my system totally

---

### Post by NoaHall on 2009-11-25
Download it from here - [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by DarinB on 2009-11-25
which one?
nix Drivers
 
 

Graphics Drivers

Linux IA32
Latest Version: 190.42
Latest Legacy GPU version (71.86.xx series): 71.86.11
Latest Legacy GPU version (96.43.xx series): 96.43.14
Latest Legacy GPU version (173.14.xx series): 173.14.22
Archive

Linux IA64
Latest Version: 1.0-5336
Archive

Linux AMD64/EM64T
Latest Version: 190.42
Latest Legacy GPU Version (71.86.xx series): 71.86.11
Latest Legacy GPU Version (96.43.xx series): 96.43.14
Latest Legacy GPU Version (173.14.xx series): 173.14.22
Archive

FreeBSD x86
Latest Version: 190.42
Latest Legacy GPU Version (71.86.xx series): 71.86.11
Latest Legacy GPU Version (96.43.xx series): 96.43.14
Latest Legacy GPU Version (173.14.xx series): 173.14.22
Archive

Solaris x64/x86
Latest Version: 190.42
Latest Legacy GPU version (96.43.xx series): 96.43.14
Latest Legacy GPU version (173.14.xx series): 173.14.22
Archive

NVIDIA nForce Drivers

Open source drivers for NVIDIA nForce hardware are included in the standard Linux kernel and leading Linux distributions. This page includes information on open source drivers, and driver disks for older Linux distributions including 32-bit and 64-bit versions of Linux.

PODCAST

Andy Ritger and Christian Zander of NVIDIA speak with Will Backman of bsdtalk ([http://bsdtalk.blogspot.com/](http://bsdtalk.blogspot.com/)) about the NVIDIA FreeBSD graphics driver. In the interview Backman, Zander and Ritger discuss the motivations for NVIDIA supporting FreeBSD, the technical issues to resolve in order to improve NVIDIA's FreeBSD Graphics Driver support (also discussed here: [http://lists.freebsd.org/pipermail/freebsd-hackers/2006-June/016995.html](http://lists.freebsd.org/pipermail/freebsd-hackers/2006-June/016995.html)), the configurability and features exposed by the driver, and licensing and NVIDIA's open source efforts.

---

### Post by kansasnoob on 2009-11-25
@DarinB,

It can be frustrating!

Kernel updates can hose configurations for your graphics card, audio card, wireless, etc!

Usually you can select to boot into the earlier kernel and get your work done. Then when you have the time & patience you can work it all out.

Some distros choose not to upgrade as often as Ubuntu just for this reason (ie: Linux Mint is based on Ubuntu but you'll almost never see a kernel update).

I personally don't like that! I want new and stable!

Sadly sometimes I must compromise.

---

### Post by DarinB on 2009-11-25
how do i do this???? If you could post the contents of the file /var/log/syslog that would be helpful as well.
maybe before i mess up the graphics.

---

### Post by handydan918 on 2009-11-25
The OP has discovered the joys of using testing/unstable vs. stable.
This is an excellent example of how the Debian development model could prevent about half of the posts to the fora here...

---

### Post by pi.boy.travis on 2009-11-25
> **DarinB said:**
> how do i do this???? If you could post the contents of the file /var/log/syslog that would be helpful as well.
maybe before i mess up the graphics.

Now that we know the cause of your issue, this is no longer necessary.

---

### Post by pi.boy.travis on 2009-11-25
> **handydan918 said:**
> the op has discovered the joys of using testing/unstable vs. Stable.
This is an excellent example of how the debian development model could prevent about half of the posts to the fora here...

+1

---

### Post by DarinB on 2009-11-25
hey pi, i think i missed something when did we find out the problem??? and what is the problem???

---

### Post by pi.boy.travis on 2009-11-25
> **DarinB said:**
> hey pi, i think i missed something when did we find out the problem??? and what is the problem???

It would seem that the problem is your nvidia driver.  I would follow the aforementioned recommendations and see how that turns out.

Ubuntu 9.10 has been notorious for nvidia troubles so far. . .

---

### Post by DarinB on 2009-11-25
what if it kills my system what do i do to save it?

---

### Post by pi.boy.travis on 2009-11-25
> **DarinB said:**
> what if it kills my system what do i do to save it?

Worst comes to worst, we can set you up with the vesa driver.

---

### Post by DarinB on 2009-11-25
yep i think that is how i am now. 
after a restricted driver mess. 
which one do i download linux IA32 or freeBSDx86 the others seem to be for amd 64 systems.

---

### Post by DarinB on 2009-11-25
oh yeah which recovery mode for the .16 kernel or the .11 kernel or even .15 kernel i have all three i am using the .11 right now

---

### Post by pi.boy.travis on 2009-11-25
> **DarinB said:**
> oh yeah which recovery mode for the .16 kernel or the .11 kernel or even .15 kernel i have all three i am using the .11 right now

I would use the .16, but as long as the new driver gets installed, it shouldn't matter.

---

### Post by DarinB on 2009-11-25
I tried to follow the above i went into recovery mode but i got a screen to fix things i did not get a terminal or gui. Not sure how to proceed with the instructions given, here they are again 
[B][I]Download the driver from the nvidia site.
Boot into recovery mode, and then -
Code:

sudo apt-get remove nvidia*

Code:

/home/user/location/of/nvidiafile

Run that, and then when it asks if you want to compile the kernel module, select yes.
Restart, and see if it works.[/I][/B]

---

### Post by DarinB on 2009-11-25
> Download the driver from the nvidia site.
Boot into recovery mode, and then -
Code:
sudo apt-get remove nvidia*
Code:
/home/user/location/of/nvidiafile
Run that, and then when it asks if you want to compile the kernel module, select yes.
Restart, and see if it works.
 **Can any one explain how to do this? when i boot to recovery mode i don't get a terminal to add these commands also the nvidia driver i downloaded is a tar ball??????**

---

### Post by NoaHall on 2009-11-26
Oh right, sorry, forgot they did that.
Well, extract it first(gui method is probably easier)
Then, when you do boot into recovery mode, select the "root" option.
From there, enter the commands I provided you with.
Let me know if you need anymore help.

---

### Post by DarinB on 2009-11-26
i never figured out the recovery mode method but i was able to get the 190.42 nvidia driver through the repos by adding the ppa and updating. then i went to the hardware drivers and activated it. I am not sure if this is what you had in mind, **does it make a difference that it is not compiled in the kernel?** *(sorry i have no idea what i just wrote)* 
I have some more functionality. although i cant permanently save my xserver config setting it comes up an error. can't backup xserver cofig file. so at reboot my screen res goes back to 1400 x 900 which is fine (I have been using that for a while)  I can view full screen Hulu only occasional choppiness, but viewable, and much better. i did get a firefox freeze with abc.com but not an xserver freeze i was able to force quit firefox. Not sure if this helped the original problem much... Oh! i can play full screen on ninjatv, with out the 190.42  driver if i clicked the full screen button it caused firefox to close. I do believe you are correct though about the nvidia driver. I am not sure that it is installed how you wanted it. when i booted to the earlier kernel .11 i went to low res vesa driver. therefore i boot automatically to .16 with start up manger app. And here i am. **Any other ideas on the freeze?** I have always had nvidia problems with ubuntu all the way back two pcs ago, earlier nvidia cards, and ubuntu versions... i always gave up and used the vesa drivers. It maybe time to figure this whole thing out.
what really is unfortunate is that on the windows side of my hdd even with vista my video is awesome the HD is amazing very sad it not very good at all with ubuntu.

---

### Post by NoaHall on 2009-11-26
Okay, here's how you save the x file -

Open a terminal, and put in
```
gksudo nvidia-settings
```

Otherwise, you don't have permission to save it.

It doesn't matter you didn't do it from recovery mode, but the problem is that it won't work with the older kernels, only the latest one.

My advice to you is to do a fresh install.

---

### Post by DarinB on 2009-11-26
thank you very much i hope this will help. If i keep it like it is will the nvidia driver work with the next kernel or will i have to activate it in hardware drivers?

---

### Post by NoaHall on 2009-11-26
Hm. I'm not quite sure, but I think it should work. Although, I'm not sure if Jaunty will get another kernel update.

---

### Post by running_rabbit07 on 2009-11-26
> **DarinB said:**
> how do i do this???? If you could post the contents of the file /var/log/syslog that would be helpful as well.
maybe before i mess up the graphics.

I haven't read the full thread as there is more arguing then I prefer to read. 

Here is the easiest way to gain access to your older kernel and even set grub to boot it every time.```
sudo apt-get install startupmanager
``` This program will allow you to select which kernel to boot on every start-up. Good luck and sorry to see you had this problem.

---

### Post by philinux on 2009-11-26
To  DarinB

Have you got the proposed repo's active by any chance?

System>admin>software sources> Updates tab

If so untick proposed.

Click the backports link below if you have.

---

### Post by sandy8925 on 2009-11-26
I've been installing and using the driver from the Nvidia website and haven't had any problems so far in any of the kernels (other than the fact that I had to reinstall it for each new kernel update). I use an AGP Geforce 6600GT by the way.

 To make it easier for you what you should do is run the command to reset xorg.conf to using vesa drivers (i forgot the exact command - it has phigh somewhere in it).

Go to [www.nvidia.com](www.nvidia.com)

Click on the download driver link and select whatever applies (the OS,graphics card model,32/64 bit etc.) Then download the driver. It will most likely have a .run extension.

You'll have to install the driver with root permission. Run it as:
  sudo ./NVIDIA-.........run 

You have to do this without xserver running so you can use the command: sudo /etc/init.d/gdm stop to stop xserver (there's a different way to do this in karmic) and sudo /etc/init.d/gdm start to start xserver again. There's no need to restart after installing the driver. You should also make sure that nvidia-xconfig is run so that xorg is configured to use the nvidia driver after installation.

Hope this helps you.

---

### Post by DarinB on 2009-11-26
I tried to save the settings. but they won't save even running it a gksudo nvidia-settings in terminal to open the nvidia console. after i change the screen res. and then hit apply then save button but it won't stick after the log out and log in

---

### Post by NoaHall on 2009-11-26
Hm.. That's very weird. Your xorg.conf must get written over every time. 

Again, I suggest you either do a fresh install of Hardy or of Karmic.

---

### Post by DarinB on 2009-11-26
I fear that may be the only solution, I am not too thrilled with what i have heard about karmic, so far. 
I have been thinking of hardy, i have four soon five people i set up with hardy as a dual boot and they are all happy. I will think about it. then i will be good until next summer after the dust settles with lucid. OR  I am considering backing up all my HDDs and going ext 4 on all drives. But with a clean install of lucid, some time next summer. I will hold of and see if i have many system freezes or just firefox stuff.

---

