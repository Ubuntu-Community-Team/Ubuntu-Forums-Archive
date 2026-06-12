---
title: "Upgrading to 9.04 killed my sound!"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by Zvarri on 2009-07-01
Yesterday I upgraded from Ubuntu 8.10 to 9.04. After the installation, I am getting zero sound playback through the Sounds preferences options or applications like Rhythmbox and Firefox. No error messages, no indication of conflicts, just zero playback.

Not really sure where to start diagnosing the issue. Can anyone help?

---

### Post by Edgeworth on 2009-07-01
Maybe a driver issue. System>Administration>Hardware Drivers
See if there's one available.
We would need the output of lscpi to diagnose further.

---

### Post by Zvarri on 2009-07-01
lscpi produces nothing, but lspci produces the following:

```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 740 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0b.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

```

In System -> Administration -> Hardware Drivers, no proprietary drivers were found.

Just want to note that I had no sound issues leading up to the upgrade to 9.04.

---

### Post by halitech on 2009-07-01
I have yet to see sound drivers show up in Hardware Drivers, thats not to say that someday they won't :)

whats the output of
```
aplay -l
```
also check alsamixer and make sure nothing is muted

---

### Post by Zvarri on 2009-07-01
aplay -l outputs the following:

```

card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I've verified nothing is muted in alsa.

---

### Post by Zvarri on 2009-07-07
Bumping in hope that someone brighter than myself might see something I've missed.

---

### Post by CatKiller on 2009-07-07
I did see this on the other half's computer. I'd been messing around with trying to get audio streamed over the network when she was on 8.10 (which I'd failed to achieve) and when she upgraded to 9.04 last week there was no sound from anything. Undoing the multicast things that I'd changed made everything work again. I'm pretty sure that the main thing was opening paprefs and unchecking the "Enable Multicast/RTP sender."

---

### Post by Zvarri on 2009-07-07
That did the trick! Thanks for the input, everyone. My sound now works again!

---

### Post by psionicinvasion on 2009-07-07
I started with 9.04 about a month ago, so please forgive my newness. I'm having the same problem, how do I open Pulse Audio Preferences?

---

### Post by CatKiller on 2009-07-08
Applications -> Accessories -> Terminal```
paprefs
```If it isn't already installed, it's in the Universe repository.

---

### Post by Zvarri on 2009-07-08
If it's installed, it should also be accessible through System -> Preferences -> Pulseaudio Preferences.

For those of us who aren't command line-inclined.

---

### Post by psionicinvasion on 2009-07-08
ok, now I feel dumb. 
Anyway that didn't work, it was already unchecked, are there any other solutions?

---

### Post by Sealbhach on 2009-07-08
Put 

aplay -l

in a terminal and paste the result here.

.

---

### Post by psionicinvasion on 2009-07-08
```
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I also tried running 8.04 to see whether it was a software version problem or hardware, it still didn't work, so I'm leaning toward either hardware incompatibility or malfunction.

---

### Post by Sealbhach on 2009-07-08
it could be worth a try putting in a line at then end of alsa-conf, take a look at the guide here:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

.

---

### Post by psionicinvasion on 2009-07-08
when i ran the first command, to find out my sound card type, i got:
```
******@******-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory

```
does this mean it's not reading my sound card at all?

---

### Post by Sealbhach on 2009-07-09
> **psionicinvasion said:**
> when i ran the first command, to find out my sound card type, i got:
```
******@******-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory

```does this mean it's not reading my sound card at all?

Looks like it.

Check in Synaptic that you have alsa-base installed. If you have, then I'm not sure what else to suggest. 

.

---

### Post by misswham on 2009-07-11
i upgraded to 9.04 on my laPTOP and everything is fine except no sound  I went to hardware drivers and the only one thats there is one for madwifi and they said dont activate if i am already getting a connection.  i am so what could be the problem with my sound?

---

### Post by srnupsen on 2009-07-23
When I was troubleshooting, I had to use "card1" instead of "card0". Thus:

```
cat /proc/asound/[COLOR="Red"]card1[/COLOR]/codec#* | grep Codec
```

Is there a difference between card0 and card1?

---

