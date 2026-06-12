---
title: "USB Drives not recognized"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by Lynnlake1 on 2009-11-24
A friend installed Ubuntu on my computer but I am completely illiterate to it's language.  I was trying to use my card reader to upload pictures and it doesn't recognize that there is a drive.  I also placed a game controller in the usb drive but it never recognized that either.  I have no idea how to fix this at all or where to even begin seeing if the computer detects the usb drive.  I really need to upload pics for some Xmas gifts and I'm literally stuck until I get this problem fixed.  Please please...any help would be greatly appreciated.

---

### Post by dca on 2009-11-24
What version of Ubuntu did they install?  The latest 9.10 Desktop Edition recognized everything I throw at it.  The Ricoh Media Card reader and USB bus on my laptop have been recognized since at least 8.04???

---

### Post by kansasnoob on 2009-11-24
I'm also curious about the version. Please go to Applications > Accessories > Terminal and post the output of:

```
cat /etc/issue
```

Unlike dca I had nothing but trouble with 9.10, will explain more after I see that output.

---

### Post by kansasnoob on 2009-11-24
I'll be unavailable for a while so remove the external media and try:

```
sudo apt-get install pmount usbmount
```

Then restart and see if that helps.

---

### Post by Lynnlake1 on 2009-11-24
This is what it says:

Ubuntu 8.10 \n \l

skashani@dimension-2400:~$ 

Does that help you out at all?  Thk u agai for your help.

---

### Post by Lynnlake1 on 2009-11-24
I put in the code you suggested by going to applications/accessories/terminal.  I entered after your code and it did a few things.  Then I restarted but I still don't get an autoprompt that my card reader is in.  I also open up Gimp and choose to locate pictures but it doesn't pick up the external drive either.

---

### Post by Lynnlake1 on 2009-11-24
Let me clarify that I've had Ubuntu for about 6 months now with no trouble.  Am really enjoying it but this is the first real problem I've had that I cannot fix.  The drivers were obv. working until 2 days ago when I plugged in my card reader.  I'm truly lost in Ubuntu and given the timelines of getting pics uploaded and Christmas around the corner..I'm hoping for a relatively easy painless fix.

---

### Post by dca on 2009-11-24
The only thing I can think of is have your friend (back-up your data) do a clean install of the latest vers of Ubuntu (9.10 Desktop Edition).  
 
Other than plugging in the media cards or USB devices, clicking on 'Places' in your menu bar, selecting 'Computer' and seeing if it lists the devices in that nautilus screen.  You should see 'CD/DVD drive', 'Filesystem' (hard drive), and hopefully something listed as Media card or USB device.  Hopefully it's there and something is not set in your OS to display the device on your desktop. 
 
Generically, to see if your system even recognizes these as mass storage devices, you can plug them into computer, open the 'Terminal' from Applications -> Accessories menu and type in:
 
*sudo lsusb* 
 (lower-case L) after the sudo
 
...then copy/paste results here...

---

### Post by Lynnlake1 on 2009-11-24
Unfortunately the media card is not detected in the computer folder.  I have file system and cd-rw drive.  I am not sure what you want me to type in at the terminal location under accessories.  The prompt I have when opening terminal is:

skashani@dimension-2400:~$ 

Do you want me to put in sudo lsusb there?  If so, it then asks me for a sudo password.

I'm so sorry but none of this makes sense to me...this is probably pretty basic info I should know about my OS.  Sorry.

---

### Post by dca on 2009-11-24
Your sudo password is same one that you use to login, (yes, at that command line is where you type it) if your friend disabled that feature and your computer simply boots to desktop than your friend should have that info.  I only run the latest desktop ed on my PCs/laptops and latest LTS on servers so it's tough for me to say if an update killed the ability to mount your usb devices or if it's a permissions thing...

---

### Post by Lynnlake1 on 2009-11-24
This is what I got...is this right?

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:1d04 Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0ace:1215 ZyDAS WLA-54L WiFi
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by 0nelove on 2009-11-25
I'm following this thread also.  having same issues recognizing USB drive in Ubuntu 9.04.  output of lsusb is same as above (not listing the drive, but does list the 2.0 and 1.1 hubs and other usb devices (mouse, bluetooth, etc).  lynnlake1, see these instructions to get additional debugging info that these folks can use to help you: 
[https://wiki.ubuntu.com/DebuggingRemovableDevices](https://wiki.ubuntu.com/DebuggingRemovableDevices)
 I'm stuck at the same spot you and and it looks like I might have another dead USB stick.  Hope not tho...

```
:~$ ck-list-sessions
Session1:
	unix-user = '1000'
	realname = 'uzer,,,,'
	seat = 'Seat1'
	session-type = ''
	active = TRUE
	x11-display = ':0'
	x11-display-device = '/dev/tty7'
	display-device = ''
	remote-host-name = ''
	is-local = TRUE
	on-since = '2009-11-25T15:16:26.109038Z'
	login-session-id = '4294967295'

:~$ id haldaemon
uid=111(haldaemon) gid=120(haldaemon) groups=120(haldaemon)

:~$ uname -a
Linux uzux 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009 x86_64 GNU/Linux

```

also, sudo tail -f /var/log/messages:
```
usb 6-1: new full speed USB device using uhci_hcd and address 9
```

---

