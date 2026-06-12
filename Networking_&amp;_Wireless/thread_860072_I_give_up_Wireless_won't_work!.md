---
title: "I give up: Wireless won't work!"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by 00Davo on 2008-07-15
No matter WHAT I try, my Ubuntu Hardy machine will not connect to my Netgear wireless router. 

When I try to connect, I get either wlan0:avahi if I use DHCP, or simply a dysfunctioning Internet connection if I use a static IP. 

I looked up my wireless card (Netgear WG311v2) in the Ubuntu help, and, apparently, it'll work "out of the box". Of course, Ubuntu hasn't got a box, so it doesn't work.



I tried setting my domain to DCC, matching my SSID, and had to deal with that stupid glitch that makes sudo break when you change domains. After dealing with it, surprise surprise, my wireless still wouldn't connect.

I've tried replacing the Network Manager with Wicd, but it didn't work either. It couldn't retrieve an IP from the DHCP on my router. With static it said connected, but it wasn't really: I couldn't actually USE the connection for anything.

I tried reinstalling Ubuntu about seven times. My /home directory is on a separate drive and so was unaffected. After each reinstall I tried pretty much everything on this list at least twice, until Ubuntu completely froze up. :(

HELP!

---

### Post by adam_kimber on 2008-07-15
Hmmm. There is a DHCP bug which I have found but not posted as of yet as I have not nailed the problem to an specific "bug". Anyway I will share the workaround with you and then I will have a bash at helping you with your wireless problem. 

If a router is restarted with Hardy running and the DHCP server is not set up to give the same IP to the same device every time then it tries to give Hardy a new IP but Hardy wants to use the old one, hence nothing works. Just click on the network manager icon and click disconnect and then reconnect. Silly I know. But it works. Make sure the router is fully up and running before doing this. This problem is more apparent with speedtouches than Netgears.

Wireless.

1) Install Ubuntu. Or revert back to network manager. 
2) Go to restricted drivers. System --> Preferences I think. 
3) If your card is there. Click the use and see what happens.

Check out this thread it might be of some help [http://ubuntuforums.org/showthread.php?t=5141]("http://ubuntuforums.org/showthread.php?t=5141")

If that fails try [For V3 but might work for you]("https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3")

Basically you need to install ndiswrapper (a funky way to use windows wireless card drivers in Linux) and then tell it to use the windows drivers XP/2000 works most of the time. Check out the [ndiswrapper]("http://ndiswrapper.sourceforge.net/joomla/") home page for lots of info and this is the [installation]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/") page.

So. Recap

1) Check out restricted drivers.
2) Use ndiswrapper if above does not work.

Just shout if parts do not make sense.

---

### Post by 00Davo on 2008-07-15
Hooray! Your first link led me here: [http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-dapper.html](http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-dapper.html)

After switching the driver, my wireless connects *perfectly*! Thanks very much. :)

---

### Post by chalewa on 2008-07-15
> **00Davo said:**
>  Of course, Ubuntu hasn't got a box, so it doesn't work.




that made me lol

---

### Post by adam_kimber on 2008-07-16
> **00Davo said:**
>  Thanks very much. :)

Not a problem. Lol to the out of box thing :P

---

### Post by auxis on 2008-07-17
> **00Davo said:**
> Hooray! Your first link led me here: [http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-dapper.html](http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-dapper.html)

After switching the driver, my wireless connects *perfectly*! Thanks very much. :)

Are you using WEP?

I have a WG311v2 on a Hardy machine.  I get no error messages, and It's able to detect wireless routers in my area, but I cannot connect to anything at all using network manager (It just sits in a connecting loop, and sometimes crashes the kernel).  I've followed the instructions on the link provided, but it didn't work.  I also tried instructions updated for newer versions of Ubuntu, but it still didn't work (Those are located at: [http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-feisty.html](http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-feisty.html)).

I know of ndiswrapper, and I've used it on installations of Fedora, but all in all I really dislike using it when the WG311v2 should work "out-of-the-box" with Hardy.

Any help would be appreciated.

Edit:

I finally figured it out after one last try.  I followed the steps at [http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-feisty.html](http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-feisty.html) which required me to uninstall network-manager.

I then edited the interfaces, added the wlan0 information in, went to System -> Administration -> Network and the wireless device was listed in the connections tab, I clicked properties and used the drop-down and found my network that it detected, and simply entered the hex key in (without adding the prefix 0x to the key).

Hopefully in newer updates we'll be able to use Network Manager for this.

---

### Post by jkyahoo101 on 2008-07-17
I am glad someone got their wireless working. Now maybe someone will help me in my thread. I am about to give up too.

---

### Post by adam_kimber on 2008-07-17
Yo! I will have a look at your post...

---

### Post by 00Davo on 2008-07-21
Know how I said it worked perfectly? I spoke too soon. :( The wireless has gone down *again*. I've tried both [http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-dapper.html](http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-dapper.html) and [http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-feisty.html](http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-feisty.html), and neither worked. I also re-tried all those other methods above. HELP! (again!)

---

### Post by adam_kimber on 2008-07-21
What have you done! :P Afraid I am nearly out of ideas. I suggest you try looking at the ndiswrapper page for more help and have a look around for using a different network manager as there are many issues with the current version. Allegedy 0.7 of NM is better. However lots of people swear by WICD.

---

### Post by 00Davo on 2008-07-21
> **adam_kimber said:**
> What have you done! :P Afraid I am nearly out of ideas. I suggest you try looking at the ndiswrapper page for more help and have a look around for using a different network manager as there are many issues with the current version. Allegedy 0.7 of NM is better. However lots of people swear by WICD.

Oh dear. :( Will try using ndiswrapper this afternoon...

---

### Post by falcon61102 on 2008-07-21
Just a word of advice with ndiswrapper, make sure you have completely removed your old drivers and modules so you don't have any conflicts.  It's a great tool, hopefully it works for you...

---

### Post by 00Davo on 2008-07-23
Okay then.

When I got home, ready to install ndiswrapper, the wireless just worked. No changes since it previously didn't work. It just started working. :confused:

I think it must be poor reception: iwconfig says I only have 10-14 signal strength.

---

### Post by 00Davo on 2008-07-29
It's not working again. I tried ndiswrapper, to no avail. I also tried adding "pci=noacpi" to my kernel boot as suggested in the Ubuntu help file. No worky. :(

To add to the trouble, my house has moved around, and I no longer have my backup wired connection. :o Luckily, I can borrow Dad's computer while trying to fix this awful problem...

Any ideas?

---

### Post by falcon61102 on 2008-07-29
what is the output of 
```
ndiswrapper -l
```
That's a lowercase L at the end

---

### Post by 00Davo on 2008-07-30
In a blank Terminal window:
> david@dcc-david:~$ ndiswrapper -l
wg311v2 : driver installed
device (104C:9066) present (alternate driver: acx)

Looks like it should be working.

---

### Post by falcon61102 on 2008-07-30
Did you add ndiswrapper to your modules list to be loaded at startup?  If not, then Ubuntu wouldn't know to load ndiswrapper and that could cause your problems.

Run:
```
sudo gedit /etc/modules
```

And if ndiswrapper isn't listed in the file, then add it to the end of the file, save and close.  Reboot and see if that helps.

---

### Post by 00Davo on 2008-07-31
Turns out I *hadn't* put ndiswrapper into my /etc/modules. So, I just did. Now it looks like this:
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
ndiswrapper


I also added "blacklist acx" to my /etc/modprobe.d/blacklist file, to stop the acx driver from taking over.

BUT! It still doesn't work! wlan0 simply will not connect! HELP!

---

### Post by 00Davo on 2008-08-01
Problem solved! I switched my wireless card for another WG311v2, and it works fine. Thanks, everyone.

---

### Post by falcon61102 on 2008-08-01
Lol... that's one way to get things working.  Well, glad something worked out for you.

---

