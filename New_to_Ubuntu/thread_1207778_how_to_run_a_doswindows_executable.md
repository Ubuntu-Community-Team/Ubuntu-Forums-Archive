---
title: "how to run a dos/windows executable?"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by bodyharvester on 2009-07-08
i will install ubuntu (netbook remix 9.04) as soon as i can figure this out, i have a built in mobile broadband card, a dell5530broadband modem something-or-other. it connects through vodafone UK. (DELL mini 9)

but it doesnt seem to ever get a signal or be able to connect, it was like this some time ago on windows xp before i re-installed the VMC (Vodafone Mobile Connect) software.

now it does work (on windows), i have run ubuntu form the cd and copied the VMC setup onto ubuntu desktop and double-clicked expecting it to run but it opened in archive manager instead with the following message:


[/home/ubuntu/Desktop/setup_vmc10523RP11.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/ubuntu/Desktop/setup_vmc10523RP11.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/ubuntu/Desktop/setup_vmc10523RP11.exe or
          /home/ubuntu/Desktop/setup_vmc10523RP11.exe.zip, and cannot find /home/ubuntu/Desktop/setup_vmc10523RP11.exe.ZIP, period.


when i removed the archive from the apps list to use for opening files and double-clicked it said that there was nothing installed to run a DOS/Windows executable.

is there something i can install or is this software just not compatible with a live cd of desktop edition 9.04?

---

### Post by IHeequ5i on 2009-07-08
Wine works under Ubuntu, from what I've been told.  I've only used it under Fedora however, so I have no personal experience.

There's a lot of documentation and help at [WineHQ]("http://www.winehq.org/")

Wine will allow you to run a fair number of Windows programs on Linux.  Dosbox will allow you to run many DOS programs.

---

### Post by bodyharvester on 2009-07-08
WINE?

huh, i thought that was just for games,

cheers, ill run the cd again get it and see if that sorts it out, then ill install ubuntu

:)

---

### Post by ivanvajar on 2009-07-08
Linux doesn't know about .exe. There is a program called Wine for installing Win software, but it's not what you need. What you need is ndiswraper. It's a program that you provide with .inf file of your Win wireless driver.

---

### Post by bodyharvester on 2009-07-08
> **ivanvajar said:**
> There is a program called Wine for installing Win software, but it's not what you need. What you need is ndiswraper. It's a program that you provide with .inf file of your Win wireless driver.

okay, i get ndis, wrap the inf, then what? use wine to install software still then wrap?

could you walk me throuhg its use?

thanks

---

### Post by ivanvajar on 2009-07-08
When you provide .inf, ndis will install Win driver. No further action needed but restart. Also, check if your WiFi is ON.

---

### Post by bodyharvester on 2009-07-08
aah, cheers

ill get that done now

thanks

---

### Post by ivanvajar on 2009-07-08
If you don't have this program installed, open Terminal (Applications/Accessories/Terminal and type:
> sudo apt-cdrom add
then
> sudo apt-get install ndisgtk

---

### Post by ivanvajar on 2009-07-08
After installation, System/Administration/Windows Wireless Drivers

<install new driver> and find *.inf of driver

---

### Post by bodyharvester on 2009-07-08
thanks, ive got the cd of ubuntu desktop 9.04, ill install that tonight and install netbook remix later

:)

got the cd from shipit.ubuntu

---

### Post by bodyharvester on 2009-07-08
done :)

im on ubuntu now, im going to install it soon too, until i get the netbook remix .img from my friends computer :P

---

### Post by frenzyface on 2009-09-24
Is there a package like ndiswrapper for a simple Windows executable? I'm trying to download a Windows 7 iso to use in VMWare, but wouldn't you know it? Microsoft can't just let me download; I have to download an executable that will download the iso. So unless there is a way to execute this Windows executable, I'll have to buy a blank DVD and find somewhere to download this for five hours. Maybe I'll have to install Wine.

---

### Post by lkraemer on 2009-09-24
You stated it does work on windows.....So, go find the proper drivers
for Windows.  You can search for them on the internet, or get them from
the manufacturer.

Forget about trying to install something to run a setup file for Windows
on Ubuntu.

Open a Terminal window, Copy and paste these commands (one at a
time), then post the output of the following commands:
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist 
               OR for >= 9.04 use cat /etc/modprobe.d/blacklist.conf

iwconfig

```
Then post the output.

Once you know what is already installed, and what the device is, you
might have to blacklist some drivers, then use ndiswrapper to install
the Windows drivers.  You should be able to make it work.

Ref:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Good Example - once you get the *.inf file:
[http://ubuntuforums.org/showthread.php?t=859481](http://ubuntuforums.org/showthread.php?t=859481)
Posting #8

lk

---

### Post by 3rdalbum on 2009-09-24
I hate to say that you've been wasting your time, but the person helping you has misunderstood.

Ndiswrapper is for wireless network cards that don't have Linux drivers. It is NOT for mobile broadband.

I can't help you with mobile broadband; all the mobile broadband devices I've tried work out-of-the-box. All I can suggest is, try and set up the connection with the Network Manager applet.

---

### Post by ddrichardson on 2009-09-24
[https://help.ubuntu.com/community/DellMini9#Connecting%20via%20Broadband%20mobile%20services](https://help.ubuntu.com/community/DellMini9#Connecting%20via%20Broadband%20mobile%20services)

It's for Sprint but should be much the same.

---

