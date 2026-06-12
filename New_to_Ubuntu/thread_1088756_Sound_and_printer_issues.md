---
title: "Sound and printer issues"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by Vonnick on 2009-03-06
I just registered and I'm new to Linux.

Alright, I installed Ubuntu 8.10 3 days ago and absolutely nothing worked. I had to use ndiswrapper for my wireless card, and a few alternate drivers for my wireless keyboard/mouse. The only thing I can't get to work is sound and my printer. I have no clue what to do about the sound and I tried every solution I found. Nothing worked. Ubuntu seems to see my printer, but the recommended driver does nothing. I changed a lot of stuff with the sound, so I did a reinstall and now I have a fresh system, except for the 246 security updates which are installing now. I probably won't be able to do any root commands while it's updating, but you can just tell me what you need to know and how to get that information and I will post it. 

Also, where can I find my soundcard model? :(

---

### Post by jbrown96 on 2009-03-06
> **Vonnick said:**
> I just registered and I'm new to Linux.

Alright, I installed Ubuntu 8.10 3 days ago and absolutely nothing worked. I had to use ndiswrapper for my wireless card, and a few alternate drivers for my wireless keyboard/mouse. The only thing I can't get to work is sound and my printer. I have no clue what to do about the sound and I tried every solution I found. Nothing worked. Ubuntu seems to see my printer, but the recommended driver does nothing. I changed a lot of stuff with the sound, so I did a reinstall and now I have a fresh system, except for the 246 security updates which are installing now. I probably won't be able to do any root commands while it's updating, but you can just tell me what you need to know and how to get that information and I will post it. 

Also, where can I find my soundcard model? :(

You can do root commands while installing packages; you just can't have multiple installers running at the same time. 

You can find your sound hardware with ```
lspci | grep Audio
``` if you just run lspci then it will show you all your hardware.

---

### Post by cariboo on 2009-03-06
What make/model of printer are you trying to install?  the more information you give us the better.

Jim

---

### Post by Vonnick on 2009-03-06
It's a cheap Dell AIO Photo 926.

Also, here are the results for lspci | grep audio

```

tyler@tyler-desktop:~$ lspci | grep audio
00:0c.0 Multimedia audio controller: Rockwell International Riptide PCI Audio Controller
tyler@tyler-desktop:~$ 
```

---

### Post by chrisod on 2009-03-06
The Dell AIO printers are generally Windows only. They are the printer equivalent of a Winmodem. You are probably out of luck on the printer.

---

### Post by Vonnick on 2009-03-06
Good thing I still have Winblows for that.

Does anyone know what I can do about the sound? I don't get anything at all.

---

### Post by Bearly Able on 2009-03-06
I was having sound problems and came across [this guide]("http://ubuntuforums.org/showthread.php?t=997506"), which seems to be pretty comprehensive.  Hope it helps.

---

### Post by Vonnick on 2009-03-06
I tried that before. It didn't work. Thanks, though.

---

### Post by sneeks on 2009-03-06
dell's are normally re-branded lexmark printers,u can get some of them to work,what model??

---

### Post by Vonnick on 2009-03-06
Dell AIO Photo 926.

---

### Post by kansasnoob on 2009-03-06
Regarding the sound I'd like to see the output from terminal of:

```
aplay -l
```

BTW, that's a lower case L.

---

### Post by Vonnick on 2009-03-06
**** List of PLAYBACK Hardware Devices ****
card 0: Riptide [Riptide], device 0: RIPTIDE [RIPTIDE]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2

---

### Post by kansasnoob on 2009-03-06
Well it looks like you may need to switch to OSS!

[ATTACH]105561[/ATTACH]

[ATTACH]105562[/ATTACH]

Not very well supported hardware!

---

### Post by Vonnick on 2009-03-06
Do I change all of the sound options to OSS?

---

