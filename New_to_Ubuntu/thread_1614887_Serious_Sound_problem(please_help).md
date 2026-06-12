---
title: "Serious Sound problem(please help)"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by Shafaet on 2010-11-06
I used ubuntu 9.10 64but for 4-5 months. My sound card is creative sound blaster audigy and it worked nice with Karmic koala. Then i installed 10.04 lucid lynx 32bit. Some days went fine and then suddenly all sound disappeared. I tried to fix the problem using ubuntu-bug audio but i couldnt. Then i reinstalled the os again thinking i might have done some damage to kernel. But again the same problem occured after few days,this time i was confident that i didnt change any settings. Then I removed lucid lynx and installed 10.10 maverick meerkat 64 bit. Again some days went fine but the sound disappeared again today. Now please tell me what should i do. I afraid i have to leave Ubuntu if i cant fix it. PLEASE HELP.

Sound Card: sound blaster audigy(CA0106),driver auto detected
Speaker: Altec Lansing
Intel Core 2 duo processor with gigabyte motherboard

---

### Post by maverick555 on 2010-11-06
First start a music player and play a song.now open sound preference and change the output section to duplex.if still no luck check with each one and reply.

---

### Post by Shafaet on 2010-11-06
I tried this before and tried it again. It doesn't seem to work. Why the sound works fine for some day and suddenly disappears?

---

### Post by Hippytaff on 2010-11-06
Are you sure theres nothing wrong with the hardware...does it work ok in any other os?

---

### Post by sandyd on 2010-11-06
> **Shafaet said:**
> I used ubuntu 9.10 64but for 4-5 months. My sound card is creative sound blaster audigy and it worked nice with Karmic koala. Then i installed 10.04 lucid lynx 32bit. Some days went fine and then suddenly all sound disappeared. I tried to fix the problem using ubuntu-bug audio but i couldnt. Then i reinstalled the os again thinking i might have done some damage to kernel. But again the same problem occured after few days,this time i was confident that i didnt change any settings. Then I removed lucid lynx and installed 10.10 maverick meerkat 64 bit. Again some days went fine but the sound disappeared again today. Now please tell me what should i do. I afraid i have to leave Ubuntu if i cant fix it. PLEASE HELP.

Sound Card: sound blaster audigy(CA0106),driver auto detected
Speaker: Altec Lansing
Intel Core 2 duo processor with gigabyte motherboard
some apps for some reason set the pcm slider to 0 or mute some of the outputs

check
```

alsamixer
```
and make sure nothing is muted or at low volume

---

### Post by thunk77 on 2010-11-06
Did you update the kernel?

There's a package called linux-backports-modules-alsa in Synaptic

Can you please check that you have the corresponding version with your kernel installed?

e.g. if you use kernel 2.6.32-25, is the alsa backports package version 2.6.32-25 installed?

---

### Post by Shafaet on 2010-11-06
Hardware is ok,I can here sound on xp.

[FONT=monospace]in alsamixer nothing is 0 except[/FONT] the last 2 fields(S/PDIF,S/PDIF D>) and i am not able to change them. 


@thunk77: no i didnt update kernel. i searched the package you mentioned in synaptic and found that it is not "installed". Then i installed it. i checked the kernel version,its allright.

and also i tried this command:

```
sudo aptitude --purge reinstall linux-sound-base alsa-base  alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r`  libasound2
```

BUT STILL NO SOUND :( :(

---

### Post by Hippytaff on 2010-11-06
whats the output of
```

lspci

```

---

### Post by Shafaet on 2010-11-06
here it is:
```
shafaet@shafaet-EP43-UD3L:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: ATI Technologies Inc RV730XT [Radeon HD 4670]
01:00.1 Audio device: ATI Technologies Inc RV710/730
03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:01.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
shafaet@shafaet-EP43-UD3L:~$ 

```

ubuntu is detecting the sound card

---

### Post by Hippytaff on 2010-11-06
ok. Is this driver installed  - CA0106
I cant remember the command for  searching drivers, and   I'm not on my. ubuntu box  to test it....think  its modprobe...anyone?

---

### Post by QLee on 2010-11-06
[QUOTE=Hippytaff]ok. Is this driver installed  - CA0106
I cant remember the command for  searching drivers, and   I'm not on my. ubuntu box  to test it....think  its modprobe...anyone?[/QUOTE]
Humm, not exactly sure what you mean by "searching drivers" but modprobe is a command for installing and removing them. You're probably thinking of lsmod to show status of the modules in the kernel.

You might also want to have Shafaet do the lspci piped through grep for audio because it looks like there are two audio interfaces. So, lspci | grep audio.

I wonder if Shafaet, checked that both interfaces do not have any chanels muted, especially the interface that the speakers are attached to.

---

### Post by Shafaet on 2010-11-06
Yes the driver is installed. I heard crystal clear sound just one day ago and today its gone! its the 3rd time this happened and every time i had to reinstall the os.

---

### Post by Hippytaff on 2010-11-06
> **QLee said:**
> Humm, not exactly sure what you mean by "searching drivers" but modprobe is a command for installing and removing them. You're probably thinking of lsmod to show status of the modules in the kernel.

You might also want to have Shafaet do the lspci piped through grep for audio because it looks like there are two audio interfaces. So, lspci | grep audio.

I wonder if Shafaet, checked that both interfaces do not have any chanels muted, especially the interface that the speakers are attached to.

lsmod - that's it

---

### Post by Shafaet on 2010-11-06
thats the pipe result:
```
shafaet@shafaet-EP43-UD3L:~$ lspci | grep audio
05:01.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
shafaet@shafaet-EP43-UD3L:~$ 

```

I have checked,nothing is muted.

---

### Post by Hippytaff on 2010-11-07
Looks like the driver is installed.

---

### Post by QLee on 2010-11-07
[QUOTE=Shafaet]thats the pipe result:
```
shafaet@shafaet-EP43-UD3L:~$ lspci | grep audio
05:01.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
shafaet@shafaet-EP43-UD3L:~$ 

```...[/QUOTE]
Oops, the grep for lower case "audio" didn't pickup the device,
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller, 
that was in the lspci result you showed us in post 9. That was my mistake, when I mentioned two audio devices I should have just pointed them out to you instead of trying to let you find them on your own. I was in a hurry at the time and didn't note the capitalisation, the kind of mistake that happens when I hurry and don't read as carefully as I should.

---

### Post by Shafaet on 2010-11-07
Problem Solved :guitar:

I replaced Alsa with OSS and sound is back.

[https://help.ubuntu.com/community/OpenSound#Ubuntu%20Intrepid/GNOME%202.24%20%28and%20later%29](https://help.ubuntu.com/community/OpenSound#Ubuntu%20Intrepid/GNOME%202.24%20%28and%20later%29)

---

