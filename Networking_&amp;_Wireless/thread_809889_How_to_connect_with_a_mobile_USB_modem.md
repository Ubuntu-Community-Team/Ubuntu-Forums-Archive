---
title: "How to connect with a mobile USB modem?"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by rbarra on 2008-05-27
Hi,

I have a Sony Ericsson MD300 mobile broadband USB modem and need to connect to the Internet. I plug the device in the USB port but nothing happens.

I did a little research and was told that I could use [WvDial]("http://freshmeat.net/projects/wvdial/") software in order to configure it. But in [the official web site]("http://alumnit.ca/wiki/index.php?page=WvDial") they say I must install the WvStreams library first.

I don't want to mess it up. Can someone help me?

Thanks in advance.

---

### Post by a2gs' on 2008-05-31
Hi rbarra,
I bought the same modem (Claro 3g Brazil) and I'm looking for information too. Nothing until now.
I installed Dell's patches ([http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Known_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Known_Issues)) to create /dev/ttyS0 as 'dialout' device, but wvdial not recognize it as a USB modem. Only as a storage device.

Some new information, I post here. cya!

---

### Post by rbarra on 2008-06-02
Hi again,

When I first posted, I said that my notebook didn't "realize" that there was something connected in the USB port. Now when I plug the mobile usb modem, I get a window listing everything that's inside the MD300 modem, and I can also see the MD300 icon in the desktop.

So, in the location /media/MD300 I have an "Install" folder and 4 files:

- Autorun.inf
- catalog.txt
- F.bat.Ink
- readme.txt

Inside the Install folder I have 4 more folders (with subfolders):

- Application Data
- ISSetupPrerequisites
- program files
- Temp

... and 56 files (.ini, .mst, .exe, .msi, .ico, .inx, etc., and the setup.exe file)

Does anyone have an idea of how to configure the modem? Should I install additional libraries such as the WvStreams?

Thanks again.

---

### Post by rbarra on 2008-07-03
Hi, has anyone by any chance figured out how to solve this?

Thanks again.

---

### Post by mosm on 2008-07-09
Use de udev rules, I tried install in my Notebook Dell with Ubuntu Hardy and nops! but i guess that modem isnt compatible with usbserial.

Anybody help us? :confused:

---

