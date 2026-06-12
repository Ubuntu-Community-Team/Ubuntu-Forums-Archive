---
title: "Getting my wireless connection to cooperate."
date: 2009-06-16
forum: New to Ubuntu
---

### Post by thesilentfool on 2009-06-16
I installed Ubuntu 9.04 a few days ago, and I am having a lot of trouble getting my wireless hardware to work with it in order for me to connect to the internet. The online guide says to go and see that my wireless card is turned on in windows.
I go to windows, I turn on my card, restart, go to Ubuntu only to find that when I plug "sudo lshw -C network" in to the terminal, I get an output that says something along the lines of:
Broadcom Wireless Device
(jumble of confusing information here)
Network 0: DISABLED
(more confusing jumble)
Network 1: DISABLED
(more confusing jumble)

Any help as far as getting my hardware to play nice with 9.04?

P.S. I didn't know whether this classified as [ubuntu] or [gnome]. The desktop I'm running is gnome if that helps any.

---

### Post by pytheas22 on 2009-06-16
Broadcom wireless cards need proprietary firmware to be installed before they will work; this is probably the source of your problem.  You can install the firmware by plugging into the Internet and typing:
```

sudo apt-get install b43-fwcutter
```

(If you have no way to plug into the Internet temporarily, let me know and we can get the firmware installed without being online.)

After installing the firmware, reboot your computer and the wireless should work.  If it still doesn't, please post the output of these commands:
```

dmesg | grep -e wlan -e b43 -e eth1 -e wl
lshw -C Network
lspci -nn | grep -i broadcom
```

---

### Post by thesilentfool on 2009-06-16
Yeah, I don't have a way to get on to the internet temporarily, unless I'm in windows.

---

### Post by unutbu on 2009-06-16
You can use Keryx to download Ubuntu packages (with all necessary dependencies resolved for you) while in Windows. Then you can copy the .deb files over to a place where Ubuntu can read and instal them.

See [http://crashsystems.net/2009/01/keryx-tutorial/](http://crashsystems.net/2009/01/keryx-tutorial/) for a tutorial on how to use Keryx. And go to [http://keryxproject.org/](http://keryxproject.org/) to download the program (from a Windows, OSX or Linux machine with an internet connection).

---

### Post by thesilentfool on 2009-06-16
Would putting them on a usb storage stick work?

Edit: Okay, Keryx really has me confused. I don't get the whole premise of the program, what is the "project"? Is it the program I wish to install on my ubuntu machine?

---

### Post by pytheas22 on 2009-06-16
Don't download the b43-fwcutter package, as it won't be able to fetch the firmware unless you have an Internet connection (the package doesn't contain the firmware itself, only a script to fetch it from a website).

To get the firmware installed without a wired connection available, download [this file]("http://burnthesorbonne.com/files/b43_firmware.tar.gz"), then transfer it to Ubuntu (using a CD, USB stick or whatever you have available) and save it on the desktop there.  Then run these commands in the terminal:
```

cd ~/Desktop
tar -xzvf b43_firmware*
sudo cp b43 /lib/firmware
sudo cp b43legacy /lib/firmware
```

Then reboot.  Does this solve it?

---

### Post by thesilentfool on 2009-06-17
It didn't, I put the commands in and I get:
```

                   mike@mothership:~$ cd ~/Desktop
mike@mothership:~/Desktop$ tar -xzvf b43_firmware*
b43/
b43legacy/
b43/b0g0initvals4.fw
b43/b0g0bsinitvals4.fw
b43/a0g0initvals4.fw
b43/a0g0bsinitvals4.fw
b43/b0g0initvals5.fw
b43/b0g0bsinitvals5.fw
b43/a0g0initvals5.fw
b43/a0g1initvals5.fw
b43/a0g0bsinitvals5.fw
b43/a0g1bsinitvals5.fw
b43/b0g0initvals9.fw
b43/b0g0bsinitvals9.fw
b43/a0g0initvals9.fw
b43/a0g1initvals9.fw
b43/a0g0bsinitvals9.fw
b43/a0g1bsinitvals9.fw
b43/n0initvals11.fw
b43/n0bsinitvals11.fw
b43/n0absinitvals11.fw
b43/lp0initvals13.fw
b43/lp0bsinitvals13.fw
b43/b0g0initvals13.fw
b43/b0g0bsinitvals13.fw
b43/a0g1initvals13.fw
b43/a0g1bsinitvals13.fw
b43/lp0initvals14.fw
b43/lp0bsinitvals14.fw
b43/lp0initvals15.fw
b43/lp0bsinitvals15.fw
b43/ucode4.fw
b43/ucode5.fw
b43/ucode9.fw
b43/ucode11.fw
b43/ucode13.fw
b43/ucode14.fw
b43/ucode15.fw
b43/pcm4.fw
b43/pcm5.fw
b43legacy/a0g0bsinitvals5.fw
b43legacy/b0g0initvals2.fw
b43legacy/b0g0initvals5.fw
b43legacy/b0g0bsinitvals2.fw
b43legacy/a0g1initvals5.fw
b43legacy/a0g0initvals2.fw
b43legacy/a0g1bsinitvals5.fw
b43legacy/a0g0initvals5.fw
b43legacy/b0g0bsinitvals5.fw
b43legacy/a0g0bsinitvals2.fw
b43legacy/pcm5.fw
b43legacy/pcm4.fw
b43legacy/ucode11.fw
b43legacy/ucode5.fw
b43legacy/ucode4.fw
b43legacy/ucode2.fw
mike@mothership:~/Desktop$ sudo cp b43 /lib/firmware
[sudo] password for mike: 
cp: omitting directory `b43'

 

   
```   what am I doing wrong?

---

### Post by unutbu on 2009-06-17
thesilentfool, try
```

cd ~/Desktop
sudo cp -r b43 /lib/firmware
sudo cp -r b43legacy /lib/firmware
```

This will copy the b43 and b43legacy directories into /lib/firmware.

---

### Post by thesilentfool on 2009-06-17
That didn't do anything either.

---

### Post by pytheas22 on 2009-06-17
> That didn't do anything either. 

Sorry it's still not working.  What is the output of these commands:
```

ls /lib/firmware
dmesg | grep -ie firmware -e wlan -e eth1 -e b43 -e wl
```

unutbu, thanks for correcting my mistake in omitting the -r flag before.

---

### Post by thesilentfool on 2009-06-20
Alright, I just went out and got a different wireless card, thanks for the help though.

---

### Post by pytheas22 on 2009-06-20
Sorry you ended up having to spend extra money to get wireless working.  If you ever want to come back and work on the internal wireless card, I'd be happy to help--Broadcom chips have good Linux support these days, so the device really should work once the right firmware is installed.

---

### Post by Xorlan on 2009-06-20
Here's another "possible" solution.  May or may not work.  

For the longest time when I installed Ubuntu a couple weeks ago, I simply could get not connection to my router.  It was a Linksys WRT54g. 

Anyhow, after reading and reading on possible issues (namely IPv6, or incorrect drivers or something), I finally turned off the security on my router.  While the router was just in plain jane mode, I still couldn't connect.  I then accessed my router through my windows desktop, set WPA personal back on, created my key, named SSID, etc. etc.  Low and behold, it connected and worked instantly.  

Maybe someone could explain why resetting your security when you first try to connect works, but to be honest I have no clue.

I drove back home today to visit my folks, and encountered the same problem with their router.  Wouldn't connect.  Immediately I reset it, entered their same PW/SSID info so nothing was really changed, and it worked like a charm.  So far it's magic to me. :D

---

### Post by pytheas22 on 2009-06-21
Xorlan: I don't know why that would work; it actually doesn't make much sense to me.  But it's nice that it does.

Sometimes when you have trouble connecting to networks, particularly WPA-protected ones, [wicd]("http://wicd.sourceforge.net") does a better job than Ubuntu's default connection manager.

---

