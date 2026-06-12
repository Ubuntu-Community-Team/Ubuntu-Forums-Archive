---
title: "Unbelievably frustrated -- Acer 3680-2472 + Broadcom"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by clueless11 on 2008-04-12
I have been trying to get my broadcom wifi working with ubuntu.  I DO NOT HAVE WIRED ACCESS IN UBUNTU!!!  I cannot follow ndiswrapper instructions ... everyone seems to give different instructions.  Regardless, I have utterly no clue how to get linux headers.  I cannot connect to the internet in ubuntu.   I can still connect and download in Vista.

I have a dual boot vista system.  Wifi works in vista.  The light does not come on in ubuntu.  There is a wifi switch on the front of my acer that does not function in ubuntu.  I have bcmwl5 and bcmwl6 inf and sys files.  I have ndiswrapper 1.51

---

### Post by dstew on 2008-04-12
> I have utterly no clue how to get linux headers.The way to install and do updates off-line is to use the [nonetdebs service]("http://nonetdebs.homeip.net/"). You make a text file of your current system status, copy it over to your internet computer, upload it to the nonetdebs site, and they create a bunch of links for you to download the packages you need. Then, you copy the packages over to your no-internet computer and install them. You can get the linux-headers package that way too.

---

### Post by clueless11 on 2008-04-12
Um, what packages do I want to install and what repositories do I use.

I can't believe this is all necessary to get a driver to work with my wifi card in ubuntu.  Actually, with no guarantee of same.

Any suggestions for what ndiswraper instructions I should use?  Or is there a better/easier way to get my wifi working in ubuntu 8.04?

---

### Post by clueless11 on 2008-04-12
installed ndiswraper without recourse to nonetdebs.

installed drivers bcmwl5 and bcmwl6.

In the windows driver gui (installed from ubuntu cd) it shows that bcmwl5 has no device attached.  bcmwl6 does have a device attached.

wifi still does not work (and light does not come on, switch does not work).

lots of b43 firmware not found messages on exit.

---

### Post by zackf on 2008-04-12
Just FYI, I wouldn't use the bcmwl6.inf, that's a Vista driiver which ndiswrapper doesn't support (at least when I tried it last) However bcmwl5.inf is what I'm using now.

(Now if the hotel I was staying at had a good wifi singal.... :-)

---

### Post by zackf on 2008-04-12
Don't forget to blacklist the native bcm drivers in Ubuntu by adding "blacklist bcm43xx" (no quotes) to /etc/modprobe.d/blacklist. I would remove the bcm6.inf driver by doing "sudo ndiswrapper -r bcmwl6.inf" and try "sudo nidswrapper -m"

---

### Post by mathenge on 2008-04-12
Hi, 

My Dell Latitude has the same chipset (broadcom). I had to first blacklist the one that was being installed by Ubuntu. To do this type

sudo gedit /etc/modprobe.d/blacklist

In my case, the offending driver was bcm43xx, so I added the following line to the end of the file:

blacklist bcm43xx

Then I installed ndiswrapper. The package that I downloaded was: ndiswrapper-1.48
Once extracted, I installed in the typical Linux way. Compile and install by typing
make
sudo make install

The driver (Windows XP) that I had was bcmwl5.inf and bcmwl5.sys.

The steps that I used to get the card working were:

First change to the directory where I extracted the drivers
cd /home/me/XPdrivers
sudo ndiswrapper -i bcmwl5.inf

Now check if the driver is installed
sudo ndiswrapper -l

Now load the ndiswrapper module
sudo modprobe ndiswrapper

Now make sure that the ndiswrapper module is loaded at boot time
sudo ndiswrapper -m

After that you need to configure the wireless connection. If you're using Ubuntu/GNOME, you can use NetworkManager by typing:
sudo NetworkManager.

Normally there will be an icon for the network on the top right, but if you don't have a wired connection at all, it may not be there. Alternatively, to get to NetworkManager, click on System -> Administration -> Network.

Hope this helps. It worked for my machine. I have an Acer but it has a completely different chipset (Atheros) with entirely different problems. Why Acer does this... I don't know.

---

### Post by clueless11 on 2008-04-13
tried to blacklist bcm43xx ... but it was *already* blacklisted in hardy.
So I blacklist b43 and ssb (and ohci_hcd, based on another thread) instead.  No change.  Except now my wireless connection (wlan0) has disappeared from NetworkManager.

NetworkManager now crashes whenever I try to open it.

I tried to remove bcmwl6.inf and got a file not found message.  Then I tried to remove bcmwl (without the inf extension) and got a bunch of "cannot remove links" messages.  The driver is not removed.  It shows up in the windows wireless gui as still present (with a device attached).  I cannot remove bcmwl5 either. It shows up also, but with no device attached.

---

### Post by clueless11 on 2008-04-14
what a waste of a weekend.

i have reinstalled ubuntu.

i have installed ndiswrapper.

i have installed the driver (bcmwl5)

ndiswrapper -l shows the driver and the device (14E4:4311).

But when I run iwconfig I have NO WLAN0!!!!

There IS a wlan0 in my 70-persistent-net.rules file.

Ugh.  what do i do now?????

---

### Post by dmizer on 2008-04-14
you should take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=740632](http://ubuntuforums.org/showthread.php?t=740632) it's how i helped someone else get their broadcomm card working in hardy.

keep in mind, hardy is beta (still testing), and not everyone knows how to support it yet.

---

### Post by kevdog on 2008-04-14
Here is how to get the linux header files.  They are contained on the ubuntu install disk -- no internet connection needed:
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by zackf on 2008-04-14
Clueless, 

Just out of curiosity can you post the results of

```
lspci
```

---

### Post by mikeymo1741 on 2008-04-14
I used this thread: 

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

and the driver was bcm4318.all.gar.tz.      Worked like a charm.

---

### Post by KB3MKD on 2008-04-14
I'm using the native b43legacy driver on my laptop and it works just fine, except that it's not persistent.if i suspend my laptop, the network goes down and doesn't come back up antil i rerun the configuration.  also eth0 seems to conflict with wlan0

---

### Post by clueless11 on 2008-04-14
WOW!

What ***INSANELY*** great help.

I followed kevdog's instructions to the tee. 
Did not work.

I followed dmizer's thread to the tee.  It was spooky.  The person he was helping could have been me.  It was identical.

I am now posting from a working ubuntu wifi connection.

The secret sauce was (i think)

 #1 editing the etc/modprobe.d/blacklist to add the blacklist from dmizer
[B]blacklist b43
blacklist rfkill_input
blacklist mac80211[/B]

 #2 editing the etc/rc.local with a (presumed) b44 bug workaround dmizer figured out by adding these lines before exit 0:
[B]modprobe -r ndiswrapper
modprobe -r b44
modprobe ndiswrapper
modprobe b44[/B]
exit 0

[both #1 and #2 are explained in thread he linked to].

Now that my wifi is working I will post a bug report against the native b44 module.

Huge thumbs up.  Thanks so much folks!

---

