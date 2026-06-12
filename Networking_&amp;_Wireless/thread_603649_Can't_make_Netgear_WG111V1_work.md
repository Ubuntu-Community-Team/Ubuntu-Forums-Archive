---
title: "Can't make Netgear WG111V1 work"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by gaston9x19 on 2007-11-05
Originally Posted by AAM  
> 
the commands that you should invoke (don't forget the dead chickens!) with ndiswrapper installation are:

take the dongle OUT....

install the ndiswrapper package
sudo gedit /etc/modules (add ndiswrapper)
sudo gedit /etc/iftab (add wlan0 mac xx: xx: xx: xx: xx apt 1)
sudo gedit /etc/modprobe.d/blacklist (add 4 lines that blacklist islsm, islsm_pci, islsm_usb and prism2_usb)
cd /folder/WG111 (substitute the directory name here)
sudo ndiswrapper -i netwg111.inf (substitute name if different)
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m (this may be what you are missing)

.... insert the dongle
go to System | Administration | Networking
select the wlan0 and edit properties to include your ESSID. 



I get a bunch of errors immediately after trying to do the sudo modprobe ndiswrapper line. Here's what my terminal console looks like so far:


Code:
```

bensauve@ubuntu:~$ sudo -s
root@ubuntu:~# ndiswrapper -l
No drivers installed
root@ubuntu:~# sudo gedit /etc/modprobe.d/blacklist
root@ubuntu:~# sudo gedit /etc/modules/
root@ubuntu:~# sudo gedit /etc/iftab/
root@ubuntu:~# cd /home/bensauve/
root@ubuntu:~# dir
Desktop   net111v2.cat   net111v2.inf   wg111v2.sys
root@ubuntu:~# sudo ndiswrapper -i net111v2.inf
Installing net111v2
root@ubuntu:~# sudo depmod -a
root@ubuntu:~# sudo modprobe ndiswrapper
WARNING: /etc/modprobe.d/blacklist Line 1: ignoring bad line starting with 'blacklist'
WARNING: /etc/modprobe.d/blacklist Line 2: ignoring bad line starting with 'blacklist'
WARNING: /etc/modprobe.d/blacklist Line 3: ignoring bad line starting with 'blacklist'
WARNING: /etc/modprobe.d/blacklist Line 4: ignoring bad line starting with 'blacklist'
root@ubuntu:~#

```

Here's what I have when I open up /etc/modprobe.d/blacklist with gedit:


Code:
```

blacklist islsm
blacklist islsm_pci
blacklist islsm_usb
blacklist prism2_usb

```

Now I'm brand new to Linux, and I thought maybe you're not supposed to have to include the term 'blacklist' when the file you appear to be opening is also called '.../blacklist'. I tried taking out those terms and just putting in the islsm stuff, and it still gave me the error, just with a different 'starting with....' line.

How do I make this work in Ubuntu 5.04? None of the other threads seemed to say to do anything very different than what I am doing, which isn't working...

---

### Post by sennep on 2007-11-05
I really have no clue why you get that error..
What happens if don't blacklist those drivers? when you type ```
lsmod
``` do any of them show up?
If they do, you could try to unload them by typing ```
sudo rmmod drivername
``` where drivername is the name of the driver (such as islsm_pci), and then, see if you can establish a wireless connection using ndiswrapper. (also make sure ndiswrapper is running by typing lsmod)

Oh and btw, I noticed your topic says WG111v1, but it seems like you're installing the net111v2 driver.

I'm not actually sure if the things I've written here work in 5.04, I've only used ubuntu since 7.04.. Just out of curiosity, why did you install 5.04 instead of 7.04 or 7.10?

---

### Post by HokeyFry on 2007-11-05
follow the wireless howto in my sig, ive used this method since hoary back in the day

and just as it happens, it was the WG111 i began with xD

---

### Post by HokeyFry on 2007-11-05
also, run 

sudo ndiswrapper -m

before the modprobe line

---

### Post by wieman01 on 2007-11-05
> **gaston9x19 said:**
> How do I make this work in Ubuntu 5.04? None of the other threads seemed to say to do anything very different than what I am doing, which isn't working...
You got to be joking... 5.04?

---

### Post by HokeyFry on 2007-11-05
okay, that was unnecessary

---

### Post by wieman01 on 2007-11-05
> **HokeyFry said:**
> okay, that was unnecessary
No, I think that's a typo. I guess we'll certainly be able to help if we were talking about a recent version, but somebody who is new to Linux should by no means go for 5.04. This is not an old post.

Are you sure it's 5.04 and not Gutsy (7.10)?

---

### Post by gaston9x19 on 2007-11-06
I am positive I have an older version of Ubuntu, I got the CD free from someone in the web design business a couple of years ago and never installed it since I only had one computer. It says "version 5.04" right on the paper CD cover. I have a couple of towers now, and set up a linux partition on one of them to try to learn how to unlock the great mystery of the open-source operating system.

I can't get 7.10 to boot from CD when I burned the files in the ISO to a CD lol. Um, any help on that topic?? :) Or know where I can get a bootable 7.10 disc?

I think even though it says V2 on the dongle, the line I got when I ran **lsusb | grep NetGear** came back with something other than 0846:4240, so I think it's really V1?? I have no clue, every article and how to on setting up these contraptions says something different.

I ran lsmod and ndiswrapper is there but none of the other things that you're "supposed" to blacklist aren't there. I'll try removing them from the blacklist and see if that changes.

Is there a program you can load and just install the drivers and graphically set up the WEP key and stuff, like Windows, by any chance? lol Linux is so not my thing yet. :)

---

### Post by wieman01 on 2007-11-06
I recommend that you burn the ISO (using a Windows program) on to a CD, then install Gutsy (7.10) and start all over again. There is no point in installing 5.04. You'll only run into problems with hardware detection, etc. so I really think you ought to go for 7.10.

Perhaps your adapter even works out of the box? There is a pretty good chance as Ubuntu has made great progress in the meantime. Should we simply continue once you have Gutsy up & running (= 7.10)?

Yes, there is a graphical program for wireless networking, etc. called the Network Manager. It is included in Gutsy by default.

---

### Post by sennep on 2007-11-07
I agree with wieman01, get 7.10 up and running!

I just wanted to add a couple things:
-After you have downloaded the ISO, in Windows, make sure the md5 checksum is correct, you can use a small program like MD5 Checker to do that (see [www.download.com](www.download.com)). The MD5 checksums are listed on this page: [http://releases.ubuntu.com/7.10/MD5SUMS](http://releases.ubuntu.com/7.10/MD5SUMS)
Only burn it if the checksums match, and make sure you burn it with software that can handle ISO's. I used DeepBurner Free 1.8 (it's on [www.download.com](www.download.com)).

-The Netgear Wg111 is supposed to work out of the box in 7.10, but it didn't in my case, but I use WPA, it might work out of the box with WEP, but I haven't tested that.

-There is a graphical program for ndiswrapper too, it's called ndisgtk, but some people say it's buggy, but I've never had any problems with it. If your computer has no internet connection at all, you can use a different computer to download a .deb from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and then use a floppy or something to get it to the linux box.

---

