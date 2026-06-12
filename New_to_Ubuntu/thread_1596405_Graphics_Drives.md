---
title: "Graphics Drives"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by GaryLittlemore on 2010-10-14
I've got a problem due to using an old chipset, can anyone tell me how I upgrade the latest drivers for the below graphics card?

UMA architecture – ATI Mobility™ Radeon™, AGP 4x and 3D Architecture, MPEG2 and DVD playback, standard 16MB shared w/128MB main memory, 64MB shared w/256MB or more main memory, configurable up to 64MB.

---

### Post by jtarin on 2010-10-14
Why do you think you have a graphics related problem?
Post the results from the command ```
lspci
```

---

### Post by GaryLittlemore on 2010-10-14
I've got a problem with Mixxx crashing, see the below post:

[http://www.mixxx.org/forums/viewtopic.php?f=3&t=1702](http://www.mixxx.org/forums/viewtopic.php?f=3&t=1702)

```
gary@gary-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
00:0a.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

```

---

### Post by cascade9 on 2010-10-14
Offical support from ATI was dropped on those cards a while ago, so you cant run the ATI proprietary drivers. You will have to run the opensource drivers. 

You can try this-

sudo add-apt-repository ppa:org-edgers/ppa
sudo apt-get update
sudo apt-get-upgrade

Then reboot (LOL, so windows) 

BTW, the link to the bug, posted on the thread you linked to isn't the issue- 

> Here is a post that has similar problems to what you're having with glxgears: [Bug #563911]("http://us.generation-nt.com/bug-563911-libgl1-mesa-dri-r600-drmradeoncmdbuffer-22-kernel-failed-parse-rejected-command-stream-help-168968711.html"). So, sorry for not really having any good solution for you, but it's at least not a Mixxx bug I don't think. (though I could be wrong).Bug #563911 is "I was unable to execute any 3D application." while you said that GLX gears ran for you. So 3D does run. 

Because 3D does work, I dont think you'll fix the problem with new drivers, but you can try...

---

### Post by cascade9 on 2010-10-14
Well, thats a bug in the forums- you cant add 'code' tags without doing it manually if you edit a post. With my speeling skillz, I donae wanna try that LOL. 

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get-upgrade

```

---

### Post by GaryLittlemore on 2010-10-14
I've followed as you've put, It hasn't fixed my problem but thanks for trying to help.

Any other ideas?

---

### Post by GaryLittlemore on 2010-10-18
Anyone???

---

### Post by Mark Phelps on 2010-10-19
Sorry, but as already mentioned, you're running an "unsupported" ATI video chipset -- at least, as far as AMD/ATI is concerned.

The open-source drivers are the only ones that will work at all with that chipset and they don't have the extensive functionality or accelerated performance of the proprietary drivers.

You're pretty much stuck using them.

---

