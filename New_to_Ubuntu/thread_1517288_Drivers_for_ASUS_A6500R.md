---
title: "Drivers for ASUS A6500R"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by FishBone08 on 2010-06-24
I've Installed Ubuntu 8.04 on my laptop ASUS A6500R(really old, I know), and i don't have any other OS installed. 

My question is how do i install drivers for my laptop on ubuntu, such as WIFI, video, sound, etc. I've tried the update drivers on ubuntu and it updates perfectly but i still have no WIFI and Sound on my laptop.


Any advice?
I'm completely new to ubuntu, just explored it's features, I'm aquainted with it's basic functions though.


Thanks in Advance :p

---

### Post by k3lt01 on 2010-06-24
With regards to your WiFi you may need to use ndiswrapper and windows drivers. Ndiswrapper  is a "wrapper" that allows you to use windows drivers for your wifi so if you can locate Windows drivers, preferably XP, thn you will have a good chance of getting your wifi going.

I can't help with your sound driver issue though. The only thing I can suggest its that you make sure your sound isn't muted and that you make sure the correct devices are selected. I know it sounds condescending and it isn't intended to be but these are things often overlooked.

---

### Post by Mark Phelps on 2010-06-24
> **FishBone08 said:**
> I've Installed Ubuntu 8.04 on my laptop ASUS A6500R(really old, I know), and i don't have any other OS installed. 

My question is how do i install drivers for my laptop on ubuntu, such as WIFI, video, sound, etc. 

Basically, you don't.  Linux is not MS Windows -- where you go rummaging around for drivers.  In Linux, the drivers are found and installed as a byproduct of installing the OS.

If something specific isn't working, post a thread about that and we'll try to help.

As to video drivers, if there is nothing offered to you in Hardware Drivers, there is nothing available.  Linux installs open source video drivers by default.

---

### Post by sandyd on 2010-06-24
> **Mark Phelps said:**
> Basically, you don't.  Linux is not MS Windows -- where you go rummaging around for drivers.  In Linux, the drivers are found and installed as a byproduct of installing the OS.

If something specific isn't working, post a thread about that and we'll try to help.

[s]**As to video drivers, if there is nothing offered to you in Hardware Drivers, there is nothing available.  Linux installs open source video drivers by default.**[/s]
This may not be the case. If the OP does not have Internet (he/she said wifi wasn't working), the available drivers cannot be shown.

I guess that the first thing we have to do is to get the wifi working.

@OP, can you run
```

lspci
``` in the terminal and post the output? (Applications -> Accessories -> Terminal)

---

### Post by FishBone08 on 2010-06-25
> **k3lt01 said:**
> With regards to your WiFi you may need to use ndiswrapper and windows drivers. Ndiswrapper  is a "wrapper" that allows you to use windows drivers for your wifi so if you can locate Windows drivers, preferably XP, thn you will have a good chance of getting your wifi going.

I can't help with your sound driver issue though. The only thing I can suggest its that you make sure your sound isn't muted and that you make sure the correct devices are selected. I know it sounds condescending and it isn't intended to be but these are things often overlooked.

So I can run ASUS WLAN driver using ndiswrapper? I downloaded it last time but i couldn't figure out how to work it. Can you give me step by step instructions? (sorry, noob here, :lolflag:).

As for the other drivers guys, it seems to be functioning properly as said, ubuntu doesn't need drivers like windows, but my sound still isn't working, oh, and i made sure it's not muted, etc.

It's pretty much down to those two problems the WIFI and sound.

Thanks again.:p

---

### Post by k3lt01 on 2010-06-25
> **FishBone08 said:**
> So I can run ASUS WLAN driver using ndiswrapper? I downloaded it last time but i couldn't figure out how to work it. Can you give me step by step instructions? (sorry, noob here, :lolflag:).No problems. I'm assuming that you have the driver files unpacked, i.e. not as an .exe file. If you have an .exe file you will need to get the unpacked files because you need them separated for this process.

OK here goes

Go into Synaptic, download and install ndiswrapper-common and ndiswrapper-utils-1.9. Once they are installed follow this process.
```
# Notes. Make sure drivers are visible on the Desktop then copy and paste each command into a terminal to install the wireless network drivers for your wireless card.

# Notes. Replace xxxxxxxx.inf with the name of your .inf file.

cd Desktop

sudo ndiswrapper -i xxxxxxxx.inf

ndiswrapper -l

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

echo "ndiswrapper"|sudo tee -a /etc/modules

sudo shutdown -r now
```

Reboot your machine and you should have a working Wifi, if you don't it is likely that your drivers aren't compatible and you will need to locate another set, maybe Windows 2000 or Vista etc.

Hope this helps, let us know how you go.

---

