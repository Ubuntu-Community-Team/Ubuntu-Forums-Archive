---
title: "Activating Visuall Effects Crashes Lucid Lynx"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by baluvix on 2010-05-27
I have a fresh install of Lucid Lynx 10.04 on an Intel Dual Core, 2GB RAM, 160 GB HDD machine. Ubuntu runs fine as long as visual effects are not activated. But a few minutes after activating visual effects, my systems freezes and needs a manual reset to bring it back to life. I don't have a dedicated graphics card installed on my system. 

lshw -C display at the terminal gave the following output:

WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:fea80000-feafffff ioport:dc00(size=8) memory:d0000000-dfffffff(prefetchable) memory:fea40000-fea7ffff

Is it because my systems graphics are low spec, or because it does not have a dedicated graphics card, that activating visual effects causes it to freeze?

---

### Post by germanix on 2010-05-27
It does not really matter if the graphics are dedicated or not. I would assume that your problem is with your graphics chip. I run a Sony Vaio with a Intel graphics media accelerator 900 with 128 MB Ram (shared) and I can not activate the visual effects in full. I run the normal effects but any higher setting would also crash my system.
Sorry!

---

### Post by baluvix on 2010-05-27
Thanks, sir. I think your hunch should be correct. I triple boot on my machine (Ubunutu/PCLOS/XP). PCLOS also has the same issue, activate visual effects and the system fails to respond after a few minutes. I wonder if putting in a grahpics card would solve the problem. And is there a way to get the Ubuntu to respond (without doing a hard reset)?

Thanks and regards

---

### Post by germanix on 2010-05-28
Before you run off and get a new graphics card you should first see if the problem maybe lies with your graphic driver. You may have to install the correct driver for your graphics card.
1. Go to System>Administration>Hardware Drivers
2. Supply your password in the authorization dialog box and click OK
3. In the Hardware Drivers window, check the enabled box beside your graphics card device driver
4. A dialog box appears, asking you to confirm that you want to enable the driver. It explains that enabling the driver enables visual effects on your desktop. Click the enable button.
5. The summary dialog box appears to tell you what new software will be installed. Click the apply button.
6. The driver will be downloaded and installed. Then the Changes Applied dialog box will appear to tell you that the changes are completed. Click the close button.
7. In the hardware drivers window, click the close button.
8. You need to restart the computer so that Ubuntu will use the new driver. Select System>Quit, and then click restart

( the above explains how it is done in Ubuntu 8.04, I assume it is still the same in 10.04)
My laptop is now 5 years old and my graphics card does not support 3D graphics, if you also have an old system (more than 3 years) you may have a similar problem, but try the driver first to see.
Hope this helps you.

---

### Post by baluvix on 2010-05-28
Thanks. 

System > Administration > Hardware Drivers searches for available drivers and says "No proprietary drivers are in use on this system."

---

### Post by germanix on 2010-05-28
Well it seems there are no third party drivers for your graphics card. I guess your only option now is to get a dedicated graphics chip that will both support 3D and will also run under Linux (a driver is available for it) I suggest you ask in the Forums which graphic card would be best suited for your needs. I myself do not run compiz fusion and do not care to have a fancy graphic chip as I only use my laptop for work, so I am sorry that I can not help you any further with this problem. You will have to start a new thread to ask about which card would be best.
Have a nice day

---

### Post by tom.swartz07 on 2010-05-28
I recently tweaked a script that helps you determine if you could run compiz on your computer. I have it attached. 

Post back any relevant results?

---

### Post by tom.swartz07 on 2010-05-28
also, if you do decide to buy a dedicated graphics card, go with nvidia. ATI cards are bollocks. Most of the ATI cards dont work with anything past 8.04, and the ones that do are really expensive for just casual use.

---

### Post by baluvix on 2010-05-29
Thanks, Germanix and Tom. I ran Tom's script and it said that glxinfo was not installed. I used the software center to install glxinfo and then activated graphics (just about medium effects - the cubic workspace swtich effect is really nice). Usually, the system should have frozen by now compared to my earlier experiences, but it's been smooth sailing so far. Let me wait for some more time before I can jump to a conclusion.

Thanks for your guidance.

---

### Post by baluvix on 2010-05-29
I was just beginning to feel good, when Ubuntu froze again. This time it lasted for about 45 minutes. I guess it's not fully solved yet. And by the way, is there a way to get Ubuntu to respond when it freezes like this? Or is a system restart the only option?

Thanks.

---

### Post by wise_crypt on 2010-05-29
> **tom.swartz07 said:**
> I recently tweaked a script that helps you determine if you could run compiz on your computer. I have it attached. 

Post back any relevant results?

:) thank you, just being curious which part did you tweak actually ?

---

### Post by Kangarooo on 2010-05-29
If ur having compiz crash then use ubuntu-bug compiz to post bug report
or make apport auto collect crashes so if its omly compiz crashing then apport will give crash report to immidiatly post crash.
to make apport auto start look [https://wiki.ubuntu.com/Apport#How](https://wiki.ubuntu.com/Apport#How) to enable apport
```
 to start now
sudo service apport start force_start=1
to start on pc start
sudo nano /etc/default/apport
... and change enabled from "0" to "1".

```

if on crash as u think is compiz crash all computer is unresponsive but didnt shutdown but still can be accesed thrue ssh but not thrue tty1-6 and ur having it since 10.04 then u having one of new bugs witch affected if using intel.
heres writen about them
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
and possible solutions also there. if u want help posting some info then while crash happens u have to do some identification thrue ssh. other wise try thouse solutions as they are getting updated from bug reports already made.
For example for me this crash happens when opening many tabs in google-chrome and/or YT video.

Heres my bug report [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/586960](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/586960) witch is Dublicated to bug report witch is made to collect all intel freezes with one solution in it [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541492?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541492?comments=all)
solution for i845 is putting another kernel
```

sudo apt-add-repository ppa:brian-rogers/graphics-fixes
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install linux-image-2.6.34-52-generic

```
to know if u have 845 or other look in terminal
```
lspci
```
and if theres writen one of nummbers xx845 then u have this. other card solutions check in [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by baluvix on 2010-05-29
Thanks Kangarooo. As I mentioned earlier my systes uses Intel Corporation 82945G/GZ Integrated Graphics Controller. I've read your suggestions and the links that you've provided. After installing glxinfo, and after that successful run for 45 minutes, I just can't get Ubuntu to keep settings; it changes to "none"  when restarted. I think my system is just not compatible to run compiz.  

Regards

---

### Post by tom.swartz07 on 2010-05-31
> **wise_crypt said:**
> :) thank you, just being curious which part did you tweak actually ?

I mostly just cleaned it up around the edges, it was a bit tricky to use and get info from in its original state.

and I made it easier to get the --banana trick! :P

Anyone that has that script, run it with the --banana argument for a laugh.

IE```
./compiz-check.sh --banana
```

---

### Post by tom.swartz07 on 2010-05-31
> **baluvix said:**
> Thanks Kangarooo. As I mentioned earlier my systes uses Intel Corporation 82945G/GZ Integrated Graphics Controller. I've read your suggestions and the links that you've provided. After installing glxinfo, and after that successful run for 45 minutes, I just can't get Ubuntu to keep settings; it changes to "none"  when restarted. I think my system is just not compatible to run compiz.  

Regards

That may be possible. I was able to use compiz for the longest time, and just this past version, 10.04, I can no longer run them- the versions of X and compiz are not compatible with my card.

---

### Post by Zip247 on 2010-05-31
Although not nearly as fancy as Compiz, you could use the metacity composition.  

From [http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html](http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html)

Simple Compositing

Some of you may not need or want superfluous Compiz visual effects running when you're not making it a point to show them off. Perhaps you lack the hardware or restricted drivers for accelerated graphics necessary for Compiz or maybe you just don't want to use as many system resources but still want basic compositing which some applications depend on. In that case, Metacity, the default window manager for GNOME, works great! You can enable it graphically, or with a simple command, but make sure to disable Compiz effects in Appearance first.

To enable it graphically, hit Alt+F2 to open the "Run Applicatoin" dialog and enter "gconf-editor" to launch the GNOME Configuration Editor. In the left-hand sidebar, navigate to Apps &#10230; metacity &#10230; general and in the main box check "compositing_manager" which will go into effect instantly.

I happen to like this seeing as my laptop can not handle compiz.

---

### Post by Catharsis on 2010-05-31
3D Graphics (compiz) has been broken on 945g ever since Karmic. You can follow the progress at Bug #475429 [1]. Just, please don't post comments. There's enough information already. If you want to contribute, please upload your information to the 945 wiki [2].

[1]: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/475429](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/475429)
[2]: [https://wiki.ubuntu.com/X/Lucidi945Freezes](https://wiki.ubuntu.com/X/Lucidi945Freezes)

---

### Post by baluvix on 2010-05-31
Thanks for your support everyone. I have disabled compiz and enabled metacity for now.

---

