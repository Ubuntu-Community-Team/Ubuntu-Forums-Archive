---
title: "Problem with Sound"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by pmla_dailha on 2009-04-23
Hello everybody!
I hope someone can help me.
As absolute beginner I'm trying to use Ubuntu mainly to surf the Internet and to listen to my music collection. I use every now and again OpenOffice.
But Jaunty does not want me to have a peaceful life.
Mainly when I'm listening mp3, lastfm or watching a movie, the sound becomes very slow until I restart my system. I've tried everything, from reinstalling all packages that I found searching for mp3 or codecs in the Synaptic Package Manager, to using different mp3-players (Amarok, Rhytmbox, Songbird) and movie-players (Mplayer, Movie Player, Totem)...
The beta version of Jaunty was already problematic, therefore I was using till today Intrepid. But I wanted to try again and upgraded my system. Result: I cannot listen my music or watch a movie.
But the worst is that I cannot boot with my LiveCD (Intrepid). I have no idea why, but when I configure my laptop to boot from CD, it springs directly in grub and I have to use Jaunty.
So, I believe nobody has such a problem with his machine and because of that I'm writing.
Can anyone help me and recommend what I should do either to get Jaunty working or to downgrade (or fresh install) Intrepid?

Appendices:

$ cat /proc/asound/cards 
 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 2 with ALC250 at 0xc0003400, irq 17
 1 [Modem          ]: ATIIXP-MODEM - ATI IXP Modem
                      ATI IXP Modem rev 2 at 0xc0003800, irq 17

$ lspci | grep -i audio 
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)

$ lsusb 
Bus 001 Device 003: ID 1267:0210 Logic3 / SpectraVideo plc 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 03f0:5c11 Hewlett-Packard Photosmart C4200 Printer series
Bus 003 Device 004: ID 0dda:6010 Integrated Circuit Solution, Inc. 
Bus 003 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
$ aplay /usr/share/sounds/alsa/Front_Center.wav 
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mon                 **(I can hear)**

---

### Post by markharding557 on 2009-04-23
hi there you should be able to disable hard drive booting in your bios so there will be nothing else but the cd to boot from.
it appears jaunty has problems with certain sound chips so you will be best using intrepid as i do,i have a simular problem on my sigmatel sound chip.
if you want updated packages you can look on getdeb in my sig and in there is ubuntu tweak which can add repos for open office3 and many other things on intrepid.

---

### Post by pmla_dailha on 2009-04-24
Thanks for your reply (and sorry for my english ;-) )
I'll try to  disable hard drive booting and post what happened.
Do you mean I should submit both bugs (with sound chip and with booting from LiveCD) to launchpad?

---

### Post by pmla_dailha on 2009-04-24
Hello everybody,
I'm not able to boot from my LiveCD (8.10). I tried to boot from an USB-device, and that didn't work. Please I NEED YOUR HELP!
How can I do my mainboard booting from a device else the hard disk?

---

### Post by RichardLinx on 2009-04-24
Before trying to downgrade from Jaunty straight away you could check if it's Pulse Audio stuffing up your sound.

Type in terminal:
```
sudo apt-get remove pulseaudio
```
```
sudo apt-get install esound
```

Then run:
```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```

It's not the first time Pulse Audio's been responcible for these kinds of issues.

EDIT: I forgot to mention that you should probably reboot after doing all this.

---

### Post by pmla_dailha on 2009-04-24
Hi [RichardLinx]("http://ubuntuforums.org/member.php?u=736965"),
thanks for your help. It seems to have worked. I'll test my sound for this weekend and post on Monday if it stays good.
But I still have the problem with booting from LiveCD or USB. Do you know what I could do to solve it?
PS: I've just burned openSUSE to a CD and tried to boot from it. Unfortunately it is not working... :-x

EDIT: Today is Monday and my sound is WORKING!!! THANKS [RichardLinx]("http://ubuntuforums.org/member.php?u=736965")! I believe, this topic should be added to [SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")!

---

### Post by nikef on 2009-04-24
> **RichardLinx said:**
> Before trying to downgrade from Jaunty straight away you could check if it's Pulse Audio stuffing up your sound.

Type in terminal:
```
sudo apt-get remove pulseaudio
```
```
sudo apt-get install esound
```

Then run:
```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```

It's not the first time Pulse Audio's been responcible for these kinds of issues.

EDIT: I forgot to mention that you should probably reboot after doing all this.


Just like to say a big thank you to Richardlinx :) for giving out this tip
my sound is working again ,i am not sure what has happened to the thanks button ,but i can not find it.

---

