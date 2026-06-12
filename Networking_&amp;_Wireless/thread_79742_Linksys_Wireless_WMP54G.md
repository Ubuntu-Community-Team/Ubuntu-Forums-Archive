---
title: "Linksys Wireless WMP54G"
date: 2005-10-20
forum: Networking &amp; Wireless
---

### Post by ctcecil on 2005-10-20
After all of the time-out errors and frantic clicking, I've finally found myself at the 'Post New Thread' page of this wonderful looking forum.

So, onto my question. I am a programmer with over 4 years under my belt, and I love linux. In the beginning I used Mandrake, then migrated into RedHat and then Fedora, then ventured into Slack, and others. I was turned off to linux, though, when I spent my paycheck to turn my home network wireless. I couldn't find ANY support for the Linksys Wireless-G WMP54G card; I did find a program that worked well with the provided CD from Linksys, but it was a trial that led into payment, and one of my favorite features of linux is the FREEdom.

When I got my shipment of Ubuntu 5.04 discs in the mail a month or so back, I threw them in the cabinet remimber how much of a hassle it was not having my wireless, but it wasn't untill today that I tried to find the Ubuntu answer to my problem.

Is there an easy solution with Ubuntu? Please help me out, I've been stuck without linux for many monthes now! I hate it!

---

### Post by jhong on 2005-10-20
[QUOTE=ctcecil]After all of the time-out errors and frantic clicking, I've finally found myself at the 'Post New Thread' page of this wonderful looking forum.

So, onto my question. I am a programmer with over 4 years under my belt, and I love linux. In the beginning I used Mandrake, then migrated into RedHat and then Fedora, then ventured into Slack, and others. I was turned off to linux, though, when I spent my paycheck to turn my home network wireless. I couldn't find ANY support for the Linksys Wireless-G WMP54G card; I did find a program that worked well with the provided CD from Linksys, but it was a trial that led into payment, and one of my favorite features of linux is the FREEdom.

When I got my shipment of Ubuntu 5.04 discs in the mail a month or so back, I threw them in the cabinet remimber how much of a hassle it was not having my wireless, but it wasn't untill today that I tried to find the Ubuntu answer to my problem.

Is there an easy solution with Ubuntu? Please help me out, I've been stuck without linux for many monthes now! I hate it![/QUOTE]

Breezy should have detected your WMP54G as a rt2500 card, you just need to configure your SSID and wireless secuirty, you might find this post helpful [http://ubuntuforums.org/showthread.php?t=78250]("http://ubuntuforums.org/showthread.php?t=78250")

Good luck!

---

### Post by ctcecil on 2005-10-20
Well, it's version 5.04-- will that detect it? I can't upgrade untill I have internet access.

EDIT: I just made a new partition and tried my install, and like allways, gave me an error for no network device, did a hardware scan, nothing found. Any suggestions?

---

### Post by ctcecil on 2005-10-22
> EDIT: I just made a new partition and tried my install, and like allways, gave me an error for no network device, did a hardware scan, nothing found. Any suggestions?

bump...

please help! I'm desperatly needing linux. Can I try to install without a network card then use ndiswrapper or is there a better way? ndiswrapper didnt work  with fedora core 2...

---

### Post by bionnaki on 2005-10-22
ndiswrapper will work.

here's how...

[https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28SetupNdiswrapperHowto%29](https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28SetupNdiswrapperHowto%29)

---

### Post by bionnaki on 2005-10-22
[QUOTE=jhong]Breezy should have detected your WMP54G as a rt2500 card, you just need to configure your SSID and wireless secuirty, you might find this post helpful [http://ubuntuforums.org/showthread.php?t=78250]("http://ubuntuforums.org/showthread.php?t=78250")

Good luck![/QUOTE]

I still dont know how to do this...
can you offer any more instruction?
thanks!

---

### Post by Agent86 on 2005-10-23
Isn't the presence of a RALink chipset on a Linksys WMP54G dependent on the board version/revision? In other words, not all Linksys WMP54G's have the RALink chipset needed for the RT2500 driver.

Or am I wrong?

---

### Post by ctcecil on 2005-10-23
[QUOTE=bionnaki]ndiswrapper will work.

here's how...

[https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28SetupNdiswrapperHowto%29](https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28SetupNdiswrapperHowto%29)[/QUOTE]


it wont if i dont have the right headers, because i cannot connect to use apt-get, correct?

---

### Post by bionnaki on 2005-10-23
works fine in breezy.
just install ndiswrapper-utils
and then follow the 2nd part of the instructions
@ the site linked to.
dont worry about linuxheaders & compiling.
just install the correct drivers & modprobe, etc...

---

### Post by ctcecil on 2005-10-23
ok, so it's good to know ndiswrapper works... but I tried to install earlier, and ubuntu wont install without a network card/connection. It's saying a faulty disc or something? Ubuntu sent me these!

~~ EDIT: ~~
 I was using a bad cd, I just tried again with one of the other 10 CD's I was sent, and installation went flawlessly, then while following the WIKI directions previously posted (i burned ndiswrapper and the wiki HTML) i thought i was stuck when the I noticed I needed to use the apt-get step, I thought apt-get required a connection, but it just grabbed the needed packages from my install cd. The directions worked flawlessly, and I am posting this from my fresh ubuntu install. I was scratching my head at the fact that you never enter a root password, though.

---

### Post by youngzaphod on 2005-11-15
Hi there. I am also using the WMP54G PCI card, but it has not the ralink chipset that works with the rt2500 driver from ubuntu. This card (revision 3) uses a Broadcom BCM4306 chipset. So, I installed ndiswrapper and installed the bcmwl5.inf driver from the linksys cd. The strange thing is that the card doesn't initialize during boot time. When I type in iwconfig after booting, I see that the mac address of the Acces Point is 00:00:.... After I do a /etc/init.d/networking restart it works.
Anyone familiar with this problem?
Thanks.

---

### Post by Carbon Copy Man on 2005-11-15
I'm having a problem with this card as well. I followed the instructions at [http://wiki.ubuntu.com/Rt2500WirelessCardsHowTo](http://wiki.ubuntu.com/Rt2500WirelessCardsHowTo)
It all went fine, except that the RT2500 Configuration Utility doesn't maintain a connection (it connects, disconnects...). 

I don't know whether my card has the Ralink chipset, but I'm assuming it does because the everything went fine up until here.

I don't know what the problem actually is though.


P.S. I'm using WPA-PSK.


**Edit:**
Heh. And there's a new thread with the same problem with a different card... Must be something hidden in the network settings then.

---

### Post by ericcmi on 2006-07-25
I have Dapper 6.06 AMD64, the ISO from the main site, and a WMP54G ver4 which is thhe Ra2500 chipset.

I installed the os just fine and got the wireless working with WEP only once I was running from  the hard drives.

All I had to do was go into NetworkTool and setup the key and all was well.

However, after a series of tries at installing XGL+Compiz my X config was getting rather sloppy. So I just formatted figuring everything would go as previously.

As it tunrs out after a reinstall(with both ext and swap formatted) the same default ra2500 driver is not working.

```
root@AMD64:~# dmesg | grep ra0
[   91.385956] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
```

That is the error I get in dMesg and the ra0 device does not show up in the NetworkTools.

Could some one tell me how to fix this? I want to install the better ra2x00 driver on the wiki, but i think i need to install some packages first. But this is difficult with out working ra2500 drivers.

thanks in advance.

---

