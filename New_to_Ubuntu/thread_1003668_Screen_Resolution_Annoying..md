---
title: "Screen Resolution: Annoying."
date: 2008-12-06
forum: New to Ubuntu
---

### Post by Thilo Kuhlman on 2008-12-06
That's probably not how you spell annoying...never mind. Anywho, my screen resolution on my video card is stuck on a low resolution. Here is a screenie so you can feel my pain: 
[IMG]http://i339.photobucket.com/albums/n472/sk8_ov_all_day/Screenshot.png[/IMG]
Any suggestions? Please help!

---

### Post by s.fox on 2008-12-06
Go to 

System---> Preferences----> Screen Resolution

Hope this helps

---

### Post by zwaardmeester on 2008-12-06
I would do the following. 

Turn off display effects via System->Preferences->Appearance->Visual Effects-> None. 

Change screen resolution via System->Preference->Screen resolution.

If that not works, please post the output of the shell-command "lspci".

---

### Post by lovelyvik293 on 2008-12-06
Just go to system->preferences->screen resolution and change the resolution.

---

### Post by alienexplorers on 2008-12-06
What graphic card are you running?  Do you have the restricted drivers loaded for it?
Did you use envyng or another method?  Exactlly what driver version are you running?  If running Nvidia then try running:
> gksudo nvidia-settings
If you are not running nvidia have you tried starting in recovery mode and waited for the menu to come up and selected xfix.  When that is done click on resume normal boot.

---

### Post by Thilo Kuhlman on 2008-12-06
> **Ash R said:**
> Go to 

System---> Preferences----> Screen Resolution

Hope this helps
I, being 14 and still managed to install Ubuntu, dispite crashing and partioning, think I would of thought of that. The problem is no number above this :
[IMG]http://i339.photobucket.com/albums/n472/sk8_ov_all_day/Screenshot-1.png?t=1228615608[/IMG]
I don't want to take my computer apart; I have cord that, if moved, may not decide to work anymore. So I cannot anwser that really long question...wait, i think maybe a trident...somehting...HOLY FRIKEN MONKEY BALLS! I found it!

"
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 11)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 11)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 11)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 11)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 11)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 11)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 11)
02:00.0 VGA compatible unclassified device: 3DLabs Permedia II 2D+3D (rev 01)
02:03.0 SCSI storage controller: Adaptec AIC-7861 (rev 01)
02:04.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
"
There. Any ideas? Also, fat penguin dude, that first sentence is a question, and therefore requires a period.

           Spanks in advanced,
                  Thilo Kuhlman

__________________________________
PS. I know I am a ******* about grammar: it makes myself feel better when I correct other people.Tool.

---

### Post by coolethan on 2008-12-07
ok you will need to use the screens and graphics GUI. I'm pretty sure it is not in the menu by default so right click on applications or anywhere in that area and select edit menus. when the window pops up select on the left hand side the "other" option. now after doing that the selections on the right hand side should change and you should see a "screens and graphics". check the box and close the window. now under applications you will see "other" and under that "screens and graphics" open up S&G and select your monitor and graphics card. you don't actually have to select the exact model of your monitor but as long as you get the brand name right you should be good. the graphics card however should be exactly what it is. hope this helps, for some reason people tend to think we're all idiots and point us towards "screen resolution" which by now people should know, if you are in deep enough trouble to make a thread in the forum, it obviously isn't working. this solved my problems in hardy and now i've switched to intrepid so i have to solve it all over again and screens and graphics is obsolete in this version.

---

### Post by Thilo Kuhlman on 2008-12-08
I want to give you a friggin hug. Thanks.

---

### Post by coolethan on 2008-12-08
> **Thilo Kuhlman said:**
> I want to give you a friggin hug. Thanks.

you are very welcome i had this problem and wouldn't you know it if the first 5 people told me to go to screen resolution and after much explaining finally figured out screens and graphics had to be manually placed on the menu which by default it was there in 7.1 anyways so i did that and S&G wouldn't actually open and that made me really mad but nobody had the answer anyways i finally figured out that by logging in as root i could open it and after doing that it opened up normally under my regular user name. so ya you're very welcome, any more questions?

---

