---
title: "Limited sound. Help, please!"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by peterinmalaga on 2009-10-24
I'm a Newbie and have  been using Ubuntu 9.04 for about a week. I was using Vista before and had sound on everything (speakers, USB phone, headphones) but since moving to Ubuntu only the sound on my headphones works. I have searched the forums, tried lots of stuff, googled, you name it. Can anyone help, please?

---

### Post by nigel_nb on 2009-10-26
Right click on the speaker icon in the top right corner of gnome-panel (Top menu) Select "Open Volume Control" and select preferences under the playback tab.  Now you find all your devices with checkboxes next to them.  Tick all the playback devices.  Check if any of them is mute.  Try unmuting them and checking if the sound works.

Since you are having the audio on your headset, the drivers should be working.

---

### Post by mapes12 on 2009-10-26
Applications>Terminal and type ```
alsamixer
```press enter to bring up the program and check what's in there.

---

### Post by 3rdalbum on 2009-10-26
What sort of sound card do you have? Please post the output of this command:

```
lspci
```

And we might be able to help.

---

### Post by peterinmalaga on 2009-10-26
Thanks very much for all the help.
3rd album, here is the response:
peter@peter-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
peter@peter-laptop:~$

---

### Post by peterinmalaga on 2009-10-26
Hi Mapes12, I used to live in Stone!
Here is the response:
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.18 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: Realtek ALC662 rev1                                                    &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00]                                                  &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9484;&#9472;&#9472;&#9488;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9474;
&#9474;    &#9474;OO&#9474;     &#9474;OO&#9474;               &#9474;OO&#9474;     &#9474;OO&#9474;               &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;     100             100<>100 100<>100 100<>100  100<>100 100<>100 100<>100   &#9474;
&#9474; < Master >Headphon    PCM     Front   Front Mi  Front Mi   Line     Mic      

Don't know if you can make anything of this. I am not sure how to do a screen capture, so tried cutting and pasting the Terminal response. The outcome was that all the columns looked identical (3 almost identical horizontal divisions in red, green and white) exzcept for headphone, where there was nothing above the word "Headphone".

---

### Post by peterinmalaga on 2009-10-26
Thanks, NigelNB, Tried all that but it didn't do the trick.To be honest I can live without the speakers on my laptop, they were never fantastic and I can use external speakers for videos. The one I really miss is the USB phone: with this I would ring family and friends on their landlines in other countries (for free with voipstunt!)

---

### Post by nigel_nb on 2009-10-26
Can you check this link out.  This bug seems to be the same as yours and you seem to be using a similar card too

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027)

Get back if it does not

---

### Post by peterinmalaga on 2009-10-28
Thanks NigelNB. I tried that (with 1 or 2 of the variants suggested by people) but still no luck. Now my start-up is much slower and I get the message "Warning: all config files need .conf: /etc/modprobe /alsa.d alsa base".In fact I did put this command in the Terminal. I am considering reinstalling Ubuntu 9.04 but shall wait a little bit.

---

### Post by peterinmalaga on 2009-10-31
Problem solved thanks to upgrade to Ubuntu 9.10. I'm impressed with 9.10!

---

### Post by nigel_nb on 2009-10-31
great.. cheers to karmic :)

---

