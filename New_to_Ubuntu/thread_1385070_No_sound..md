---
title: "No sound."
date: 2010-01-19
forum: New to Ubuntu
---

### Post by ndrea on 2010-01-19
Hello! I have previously been using Ubuntu v8.04 but have now installed Ubuntu v9.10. 
Problem 1: I do not have sound but i tried to update the system over the Internet and many device drivers are functioning well including my two network cards. 
I request for help on how to fix this luck of sound problem.  Thanks.

---

### Post by SumTingWong on 2010-01-19
Have you checked that PCM isn't stuck at 0%?

---

### Post by ndrea on 2010-01-19
Yes i have.

---

### Post by SumTingWong on 2010-01-19
Did you upgrade to 9.10 from 8.04, or did you do a clean install?

---

### Post by ndrea on 2010-01-19
I had a fresh installation. No upgrade.

---

### Post by SumTingWong on 2010-01-19
Could you please post your lspci output?

---

### Post by ndrea on 2010-01-19
How do i get that?

---

### Post by SumTingWong on 2010-01-19
Applications >> Accessories >> Terminal. 

Type in;

```
lspci
```

And press enter. 

Then copy & paste the output back here.

---

### Post by ndrea on 2010-01-19
Here is my ispci:
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:09.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

---

### Post by SumTingWong on 2010-01-19
Uh oh pistachio, VIA :S

My friend has a VIA sound chip and that didn't work with 9.10 either. Maybe it's a bug?

---

### Post by SumTingWong on 2010-01-19
This may help.
> To enable the sound, double click on the speaker on your top menu bar. This will open up the volume control panel. Click on "File", place your mouse over "Change Device" then move over to "Via 8237 (Alsa Mixer)" and double-click. Now click on "Edit", scroll to and click on "Preferences". This will open another small window. Scroll down in that window until you find "External Amplifier" double click it so there is a check mark in the box in front of it, then click "close". You will now be back on the volume control panel. Click on "Switches" then uncheck "External Amplifier" . This seems counter-intuitive to me, but it works! Now just click back on the "Playback" tab and turn all the volumes up all the way. I went ahead and activated all of the controls and max'd out the volume on them all. Now you can just close the volume control window. If you want to test sound, just do the following:
 
 - click on "System/Preferences/Sound"
 - the sound preferences window will now open
 - click on the "Sounds" tab
 - click on the "> Play" button after "Log out" and you should hear sound now
 - you can now close the sound preferences window


---

### Post by ndrea on 2010-01-19
Ohoh! What's the way forward now? I kinda like this version of Ubuntu, it's much better than 8.04! What do you think?

---

### Post by SumTingWong on 2010-01-19
It's your computer not mine! What do YOU want?

---

### Post by ndrea on 2010-01-19
When i double click on the sound icon, i don't get any other menu. Right clicking however gets me the option to mute or sound preferences. I can't seem to get to that dialogue box where i can find "File" and the rest!

---

### Post by SumTingWong on 2010-01-19
Oh yes sorry! I forgot that the sound menu had changed in 9.10! 

Do you have any version of Windows available? That maybe the easiest answer to be honest.

---

### Post by overdrank on 2010-01-19
Maybe this thread can help
[Please read: Audio gotchas in Ubuntu 9.10]("http://ubuntuforums.org/showthread.php?t=1307019")

---

### Post by ndrea on 2010-01-19
Am not sure i understand you question well but i am running a network of machines with Windows XP. This machine is running Ubuntu 9.10 only. 
Are you saying i run back to Windows XP for this machine?

---

### Post by SumTingWong on 2010-01-19
> **ndrea said:**
> Am not sure i understand you question well but i am running a network of machines with Windows XP. This machine is running Ubuntu 9.10 only. 
Are you saying i run back to Windows XP for this machine?

If you're having audio problems then yes. A google search for your sound chip shows a history of problems with Linux. It's your choice, but you will most likely waste a lot of time for nothing.

---

