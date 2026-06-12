---
title: "Wifi Not detected on &quot;Try It&quot; install of 14.04.1"
date: 2014-08-07
forum: Networking &amp; Wireless
---

### Post by Tony_Bennett on 2014-08-07
I am considering installing Xubuntu 14.04.1 LTS on a friend's old Compaq Presario C503WM laptop.

Before doing so, I wanted to ensure all of the hardware would be detected and work, thus 
I booted off of the Install Disk, and chose "Try It" instead of an install.

It was able to boot, and detect the Ethernet, but not WIFI.

I have attached the output of "wireless_script"...

Any help would be appreciated.

-tony

---

### Post by weatherman2 on 2014-08-07
According to your wireless info file, you have a Broadcom BCM4311 wireless card.  Check out the first answer (with 6 votes) in the link below for a solution.  This may not work in a live session but will work after a full install:

[http://askubuntu.com/questions/450631/broadcom-b43-wifi-not-working-in-ubuntu-14-04-lts](http://askubuntu.com/questions/450631/broadcom-b43-wifi-not-working-in-ubuntu-14-04-lts)

---

### Post by Hadaka on 2014-08-07
Hi, you are missing your firmware. Please open a terminal
click the dash then type in TERM it will bring one up.
  From a wired connection please enter..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
thanks.

---

### Post by Tony_Bennett on 2014-08-08
Thank you both for the suggestions.

For the record, neither worked on the LIVE CD...(a reboot was required)...

After installing, I ran this link and everything worked following another reboot:

[URL="http://askubuntu.com/questions/45063...untu-14-04-lts"]http://askubuntu.com/questions/45063...untu-14-04-lts

[/URL]
Again, thank you...

---

### Post by Hadaka on 2014-08-08
GREAT ! glad you got it working.

the link you provied for the fix is comming
up blank.

---

### Post by Tony_Bennett on 2014-08-08
Sorry link is coming up blank...
... I followed the instructions in the second posting of this thread...

I'll try a link again:

[http://ubuntuforums.org/showthread.php?t=2238441&p=13093064#post13093064](http://ubuntuforums.org/showthread.php?t=2238441&p=13093064#post13093064)

---

