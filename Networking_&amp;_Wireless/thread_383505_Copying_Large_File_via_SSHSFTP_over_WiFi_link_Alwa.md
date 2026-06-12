---
title: "Copying Large File via SSH/SFTP over WiFi link Always Stalls and Freezes Host"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by haz2a on 2007-03-13
SSH Host 'PC-A' runs Xubuntu 6.10 (2.6.17-11-generic) with gnome-core v1:2.14.2, openssh-server v1:4.3p2, and connects via WiFi with WPA-PSK (no rekeying). 
It has a 1.4GB image file on it that I want to copy to PC-B.
'PC-B' runs Ubuntu 6.06 LTS and has a cable LAN connection.

How ever I try to download this file from PC-A to PC-B the download always stalls:-
a) via Gnome > Places > Connect to Server > SSH etc - usually after about 200MB
b) via SFTP from Gnome Terminal - usually after abt 1000MB
c) via SFTP from console - usually after abt 900MB  
Every time, it causes Gnome to freeze on the ssh host PC-A, both keyboard and mouse, and it is then unreachable on the network so I have to reset the PC.

BUT CABLE IS OK. If I switch PC-A to cable, I can download the whole file without problem.

PC-A uses a Buffalo WLI2-PCI-G54S adapter with ndiswrapper and the bcmwl5 driver. It seems to work fine otherwise eg: Firefox, Thunderbird, Gnome Terminal via SSH (other than this download). iwconfig shows 100% link quality.

Any ideas anyone?
TIA Haz

---

### Post by Matt Yun on 2007-03-13
Have you tried scp from the console? ie:

scp filename-on-PC-A user@PC-B:/path/

---

### Post by dannyboy79 on 2007-03-13
have you tried to set the computers up into ad hoc mode instead of infrastructure? I believe this will then not involve the router (i think, someone correct me if I am wrong) this may help or may not, not sure.

---

### Post by haz2a on 2007-03-14
Thanks for your suggestions.

I forgot about SCP but it did the job, thanks Matt.

Any idea why SCP should be better than SFTP for large files over WiFi?

Thanks again
Haz

---

### Post by cookfromfrozen on 2007-03-14
The only way network activity can make the system hang is if there is a problem in the network driver that is causing the system to stop.  Since you are using ndiswrapper, there is probably some sort of bug in the driver that hangs the system under load.

Using a native Linux driver would be much more stable than using ndiswrapper.  As far as I'm aware, bcmwl5 is for Broadcom chipsets and these chipsets do in fact have their own native driver.  You should probably try and get that working rather than falling back on ndiswrapper because it is not the optimal way.

If you are having trouble getting Broadcom to work, consider gathering as much information as you can (card name, chipset, output of lspci, logs etc) so we can help you get that working rather than having to rely on the imperfect ndiswrapper.

On my own system I use an Atheros wireless chipset, which is well-supported natively by Ubuntu.  A friend of mine however does use Broadcom and has found this tutorial works well for him:

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

I am confident that switching from ndiswrapper to the native Broadcom driver would  fix this problem, but seeing as it works through scp it may just be that gnome is being a little funky.

---

### Post by haz2a on 2007-03-14
SCP was the first transfer to work, but I've tried it three times since and it stalled each time - at 240MB, 670MB, and 35MB.

I tried it with ```
-l4000
``` which limited the bandwidth to about 440KB/s - about half normal speed, but thats when it stalled after just 35MB.

Seems to me the problem is independant of the front-end app, and most likely related to the quality of the wirelss link.

Is there some way to monitor the connection for any problems that might be causing this?

Any other ideas?

Haz

---

### Post by dannyboy79 on 2007-03-14
make sure you don't have other 2.4 ghz stuff on, like cordless phones, and other stuff like that. see if you can use a different channel for your connection. if there are a lot of other wireless networks next to you than this is what degrades your connection and causes "interference". what is the strength of your connection? I think you can use iwlist scan should show you all wireless access points that your card can see and possible have interference with. see what channels each one is using and try to use a different one. that's about all I can suggest.

also, according to the man page:
  -l limit
	     Limits the used bandwidth, specified in Kbit/s.

so you would need to use it with -l 3520
and that would limit it to 440 kilobytes. 

14000 kilobits is 1750 kilobytes.

---

### Post by haz2a on 2007-03-14
cookfromfrozen many thanks for your suggestion - it seems the most likely explanation!

I'll try the Broadcom howto first - it looks promising, but failing that I'll try to get a new adapter supported by the native drivers.

Thanks again
Haz

---

### Post by dannyboy79 on 2007-03-14
do you dual-boot? if you do and windows has this problem as well than you could make a storng case for that fact that  it's an interference as well as poor connection quality that is causing this and then it may be a waste of money to buy a new adapter, unless you get an amplified antenna or something like that. what does iwlist scan show for your signal strength? good luck

---

### Post by Matt Yun on 2007-03-14
> **haz2a said:**
> Thanks for your suggestions.

I forgot about SCP but it did the job, thanks Matt.

Any idea why SCP should be better than SFTP for large files over WiFi?

Thanks again
Haz

I'm not sure why SCP just seems to work when all else fails, but I suspect that it is simpler than SFTP.

However, from your later posts, this didn't seem to work for you either.  I echo the other contributors; you probably have 2.4GHz interference from somewhere (cordless phone, microwave) or your Broadcom card is flaky.  If you want to try a different WiFi card, I suggest something based off of the RaLink chipset (module rt25xx).  

I use a C-NET CWP-854 (RaLink rt25xx), and generally it works fine except when my neighbour uses the microwave or something; I live in a condo, and his kitchen wall is proximate to my desktop computer.

---

### Post by benteveo on 2007-11-13
**Solution**

I have had this problem exactly: *rsync* stalls after transferrng a small part of a large file.
I narrowed it down to *scp,* then to the network and found a solution:

I lowered the MTU (Max Transfer Unit) on the wireless interface and since then, everything works perfectly including multi GB file transfers.  Throughput is slighty down, but reliability is perfect.

Here are the details of the solution, your values may differ:

edit [FONT="Lucida Sans Unicode"]/etc/network/interfaces[/FONT] on the machine with the wireless card:

```

# note: your interface name may be different, mine is 'wlan0' just because I like that name
iface wlan0 inet dhcp
        # leave all values intact... then add or change your MTU value:
        mtu 830

```

Now in a konsole/shell, restart the network so it picks up the change:
```

sudo /etc/init.d/networking restart

```

The optimal MTU value may differ in your case.  The way I determined mine is by repeatedly doing:

```

sudo ping -f -v -c 10 -s 1492 other.host.name

```

(the 1492 in the example above is the data-portion size of the packet.)

Note how quickly the 10-packet ping finishes _without any packet loss_.
At first the ping would often hang and lose packets (which is what is apparently what's causing file copying to stall).
Then, repeat  the test with lower and lower MTU sizes (1482, 1472, 1462, ...) until you get:

   * no packet loss
   * a fast completion of the command
   * repeatably

Note: in some cases you may be lucky and get 0% loss, only to get 30% loss in an identical subsequent attempt.  Make sure your 0% loss is repeatable before settling on the MTU value.

Note that the value you have to put as MTU in the */etc/network/interfaces* file is 28 bytes bigger than the packet size you pass to ping, since there's a 28 byte header around your ping ICMP data.  Ping output should make this clear by its output (it adds the total size including headers in parentheses after the size you supply) as follows:

```

PING other.host.name (10.9.9.7) 802(830) bytes of data.

```

Showing that a 802 byte datasize is actually a 830 byte total packet size, including headers.

Note: I realize that 830 is a very small MTU but this is the biggest that actually had 100% reliability in my specific case. If you can make it bigger, you should definitely do so.

HTH

---

