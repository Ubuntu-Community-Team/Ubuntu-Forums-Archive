---
title: "Help:no sound and wifi connection..."
date: 2009-08-09
forum: New to Ubuntu
---

### Post by ht^^ on 2009-08-09
[FONT=Comic Sans MS]hi!
i'm a really new user to ubuntu and i've been having problems with my sound and wifi connection...i installed 9.04 at first and now i've just switched to ubuntu ultimate...but in both OSs i have the same prob... :(

does anyone kno wat can i do?? i'm using a compaq laptop...[/FONT]

---

### Post by coldReactive on 2009-08-09
Tell us the output of **lspci** in terminal, use code bbcode tags around the output when you paste it here.

---

### Post by ht^^ on 2009-08-09
sorry! i dun understand...ummm...wat do i key in the terminal to get the output??

---

### Post by cariboo on 2009-08-09
Open ans Applications-->Accessories--?Termianl and type:

```
lspci
```

Highlight the output of the above command and use the middle mouse button to paste it into your next post. Please use the [noparse]```

```[/noparse] tags to enclose the output, as it makes it much easier to read.

---

### Post by ht^^ on 2009-08-09
umm...i hope this is what u wanted...sorry, i'm not sure if its the correct format u asked for...
[FONT=&quot]00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)[/FONT]
  [FONT=&quot]00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)[/FONT]
  [FONT=&quot]00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)[/FONT]
  [FONT=&quot]00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)[/FONT]
  [FONT=&quot]00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)[/FONT]
  [FONT=&quot]00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)[/FONT]
  [FONT=&quot]00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)[/FONT]
  [FONT=&quot]00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)[/FONT]
  [FONT=&quot]00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)[/FONT]
  [FONT=&quot]00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)[/FONT]
  [FONT=&quot]00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)[/FONT]
  [FONT=&quot]00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)[/FONT]
  [FONT=&quot]00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)[/FONT]
  [FONT=&quot]00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)[/FONT]
  [FONT=&quot]00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)[/FONT]
  [FONT=&quot]00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)[/FONT]
  [FONT=&quot]00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)[/FONT]
  [FONT=&quot]00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)[/FONT]
  [FONT=&quot]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)[/FONT]
  [FONT=&quot]00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)[/FONT]
  [FONT=&quot]00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)[/FONT]
  [FONT=&quot]00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)[/FONT]
  [FONT=&quot]03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)[/FONT]
  [FONT=&quot]04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)[/FONT]
  [FONT=&quot]05:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller[/FONT]
  [FONT=&quot]05:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller[/FONT]
  [FONT=&quot]05:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller[/FONT]
  [FONT=&quot]05:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller[/FONT]

---

### Post by CaptainMark on 2009-08-09
your setup is recongnizing onboard hd audio ports, what type of connectors are you using for your speakers

---

### Post by ht^^ on 2009-08-09
captainmark: i'm using just my laptop speakers...

---

### Post by 3rdalbum on 2009-08-09
So the little Network Manager icon on the top panel doesn't show any network when you click on it? In order to find out what wireless chipset it is, we'll need you to put:

```
lsusb
```

into the terminal.

---

### Post by ht^^ on 2009-08-09
3rdalbum: yup...it doesn't show any networks there...here's what i got from the terminal...

   Bus 008 Device 003: ID 064e:c108 Suyin Corp.
  Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 004 Device 014: ID 1c4f:0003  
  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 001 Device 003: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
  Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[FONT=&quot][/FONT]

---

### Post by coldReactive on 2009-08-09
> **ht^^ said:**
> 3rdalbum: yup...it doesn't show any networks there...here's what i got from the terminal...

   Bus 008 Device 003: ID 064e:c108 Suyin Corp.
  Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 004 Device 014: ID 1c4f:0003  
  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 001 Device 003: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
  Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[FONT=&quot][/FONT]

```

  Bus 001 Device 003: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]

```

is your network interface.

---

### Post by ht^^ on 2009-08-09
coldreactive: okie...so what do u suggest i do to get it working??

---

### Post by ht^^ on 2009-08-09
coldreactive: ok....so what do u suggest i do to get it working??

---

### Post by coldReactive on 2009-08-09
> **ht^^ said:**
> coldreactive: ok....so what do u suggest i do to get it working??

I'm sorry, but google is being unhelpful at the moment, so I suggest waiting for an appropriate person to help you. (All I've been able to find is people with different revisions of your kind of hardware.)

Might want to try searching it yourself using [this link here](http://www.google.com/#hl=en&q=Hewlett-Packard+Wireless+(Bluetooth+%2B+WLAN)+ubuntu). If you find a solution MAKE SURE you post back here with the solution.

---

### Post by ht^^ on 2009-08-09
coldreactive: ok! thanks for trying! :)

---

### Post by miegiel on 2009-08-09
> **coldReactive said:**
> ```

  Bus 001 Device 003: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]

```

is your network interface.

Strange, his **lspci** also lists a wifi device.
```
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

**@ht^^**
Anyway, if wifi and audio hardware is listed, so ubuntu found the hardware and can use it. So far so good.

You need to keep in mind that both getting sound out of your speakers and connecting to something over a network requires a long chain of "connections". For example with sound, an application needs to use the right sound device in ubuntu, ubuntu needs to send the sound on to the right hardware, etc.

Since your hardware is found check how they are set up in *System > Preferences > Network Connections* and *System > Preferences > Sound*.

After that, for sound you'll need to check if the levers are up far enough and if they might be muted. I had a lever muted and hidden once, so make sure you also check for that.

---

### Post by trinidadflores on 2009-08-09
> **miegiel said:**
> Strange, his **lspci** also lists a wifi device.
```
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

Broadcom is the ones that make the Hewlett-Packard Wireless (Bluetooth + WLAN) Interface for HP.

---

### Post by ht^^ on 2009-08-09
> **miegiel said:**
> Strange, his **lspci** also lists a wifi device.
```
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

**@ht^^**
Anyway, if wifi and audio hardware is listed, so ubuntu found the hardware and can use it. So far so good.

You need to keep in mind that both getting sound out of your speakers and connecting to something over a network requires a long chain of "connections". For example with sound, an application needs to use the right sound device in ubuntu, ubuntu needs to send the sound on to the right hardware, etc.

Since your hardware is found check how they are set up in *System > Preferences > Network Connections* and *System > Preferences > Sound*.

After that, for sound you'll need to check if the levers are up far enough and if they might be muted. I had a lever muted and hidden once, so make sure you also check for that.
miegiel: i don't think i have a 'lever' problem...coz i can hear the startup sound (it comes out 'stuttering' though!)
n i still cant detect any wireless networks...:(...any suggestions??

---

### Post by miegiel on 2009-08-09
> **ht^^ said:**
> miegiel: i don't think i have a 'lever' problem...coz i can hear the startup sound (it comes out 'stuttering' though!)
n i still cant detect any wireless networks...:(...any suggestions??

Don't "think" make sure! I made that mistake once :D You can't rely the login sound, some "user" sound settings change as you logon.

I'm a bit hesitant to tell you what to do because I'm using karmic (the oktober 2009 edition of ubuntu) and I use hardy. I kind of skipped intrepid and jaunty and there are always subtle differences. So don't trust me 100% here ;)

Go to *volume control* and make sure to unhide any hidden levers and try every lever. Especially the master and PCM levers should be at/near the top.

An alternative to *volume control* is *alsamixer*, you start it from a terminal. It looks more primitive, but works basically the same (just no mouse). Use the arrow keys ;) and M (un)mutes channels.

One of the "tools" I use while figuring out why my machine makes no sound is the *PulseAudio Volume Meter*. It's not installed by default, but you can find it in the *Sound and Video* section of *Add/Remove*. If you can see the volume meter jump but don't hear it, 4 things can be going wrong.
[LIST]
[*]**levers** are at the bottom or muted (there they are again)
[*]ubuntu is sending the "sound" to the **wrong hardware**, but your lspci only lists 1 piece of audio hardware.
[*]ubuntu is sending the "sound" to the **wrong output**, for example the headphone jack instead of the built in speakers.
[*]the **cable** isn't plugged in (properly), but that makes no sense with built in speakers.
[/LIST]
If the volume meter doesn't jump the sound isn't being picked up by ubuntu, which usually means the program that is making the sound isn't configured right and you should check the settings of the program.

BTW, what program are you using to "make" the sound?

Regarding the wireless, can you post the terminal output of *ifconfig* please. And do you get a network system tray icon and does it show your *networking* and *wireles network* enabled or disabled or not at all?

---

