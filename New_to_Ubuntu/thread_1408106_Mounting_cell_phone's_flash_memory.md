---
title: "Mounting cell phone's flash memory?"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by knurledflanges on 2010-02-16
Hello,
I have a Samsung "multimedia" phone (A777) with a 2gb micro sd card that I use for music and also sometimes as a portable storage drive. Under XP, which I recently migrated away from, the phone showed up like any other portable device when it was plugged in, and files could be copied and pasted from it. How do I do this in Ubuntu? Some apps, like Rhythmbox, can see the phone when it's plugged in and use their own read/copy/paste/delete functionality with it, but I can't figure out how to simply open it in a file manager and work with its files like any other drive. Nautilus sees it, but when I try to open it, instead of listing files it simply says something along the lines of "Portable Audio Player" and gives an option to open it with Rhythmbox. Thunar, which is what I use most of the time since I normally use xfce, doesn't appear to see it at all.

If I do 'lsusb' in a terminal, here's what I get:
```
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04e8:5a0f Samsung Electronics Co., Ltd MTP Device
Bus 003 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1058:1003 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```The "Samsung Electronics Co., Ltd MTP Device" is it.

---

### Post by Temposs on 2010-02-16
As you can see, it is an MTP device. MTP stands for Media Transfer Protocol. This means that for a program to see the device, it has to understand MTP. Rhythmbox has an MTP plugin enabled by default, so that's why it works, but the file browsers generally don't deal with MTP, because they aren't media players.

Generally, for something to be seen in the file manager, it has to be formatted as a mass storage device.

But, maybe someone else knows of a way to mount an MTP device on a file browser.

---

### Post by niffcreature on 2010-02-16
i have a nokia 5310 with 1gb.
in settings>connectivity>usb data cable, it has and option for "data storage"
i know your phone is different, but it might have a similar option. when i do this i can explore it with the file browser.

---

### Post by 0x29a on 2010-02-16
I would also suggest using a micro SD adapter to use the card as a flash drive. The operating system then sees a standard block device. I have a LG Voyager (VX10000), and this method works great. The phone creates a file structure on the card and I can just move things to or from the card using the appropriate directory.

I also use bitpim, which supports my phone, but the flash drive method of data transfer works best for me for normal data (pics, music, etc). transfers. Plus, I don't have to jump though all of [[color="#000fff"]these hoops[/COLOR]]("http://www.bitpim.org/help/howto-linuxusb.htm") to make things work on computers that aren't set up for bitpim.

The bitpim site does not [[COLOR="#0000ff"]specifically mention[/COLOR]]("http://www.bitpim.org/help/phones-samsung.htm") your phone as being supported, but it might be worth tinkering with. Just be sure to note the link above for the process that may be required to let your system, and non-root user account access the device.


Good luck!

---

### Post by knurledflanges on 2010-02-16
Thanks for the replies.

The phone does have 3 different "USB modes": "Media Player" (which was on by default), "PC Studio," and "Mass Storage." Only with "Media Player" selected can I get any apps I've tried to see it, and I haven't actually found any that will see the various image and data files on it. It seems invisible to everything with either of the other 2 selected.

I got Bitpim and experimented a bit but didn't have any luck getting it to see the phone.

I know the USB adaptor is the simple solution, and the only good one if you want to be able to plug it into any computer you come across without having to mess with stuff. I had one but lost it, need to get a new one :P. It would be nice if this "just worked" though, seems like the file managers should be able to do it since some applications can.

---

