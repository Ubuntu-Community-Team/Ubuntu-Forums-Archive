---
title: "on-board LAN port is not working"
date: 2013-12-20
forum: Networking &amp; Wireless
---

### Post by luge86 on 2013-12-20
Hi folks,

i've got a new PC with the following hardware setup:
> Gigabyte GA970-U3
AMD FX6300
ADATA 2*4Gb RAM @ 1600 MHz
Kingston 120 Gb SSD

I'm running Kubuntu 13.10 and my system is up-to-date.

The Board contains an on-board LAN port with a Realtek chipset.
According to lspci, the kernel recognize this:
> lugge@lugge-desktop:~$ lspci -nnk | grep -i net -A2   
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
        Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
        Kernel driver in use: r8169

However, i do not get an IP from my Router (AVM Fritzbox). Windows 7 on the same machine does.
The "Notification Service" from Kubuntu keeps telling me that
> "Connection 'Wired connection 1' deactivated"

Reading the output from ifconfig, i wonder why all TX packets are being dropped?!
> lugge@lugge-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 94:de:80:bf:d6:b8  
          inet6 addr: fe80::96de:80ff:febf:d6b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:235 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23699 (23.6 KB)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:613 errors:0 dropped:0 overruns:0 frame:0
          TX packets:613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49359 (49.3 KB)  TX bytes:49359 (49.3 KB)

usb0      Link encap:Ethernet  HWaddr 1a:2b:81:38:ac:5f  
          inet addr:192.168.42.197  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::182b:81ff:fe38:ac5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:786 errors:1 dropped:0 overruns:0 frame:1
          TX packets:1030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:536675 (536.6 KB)  TX bytes:213444 (213.4 KB)

usb0 is my Android Smartphone via USB with shared internet.

Can anyone help me with that? According to some forums, my Mainboard should just work fine with Linux :-/
If you need more information, please tell me, and i will provide it.

Greetings,
lugge

---

### Post by tfrue on 2013-12-20
Here are some things to try.

Disconnect your Android device so there won't be any conflicts, which there may not be but Momma always said, "Better safe than sorry," and type:
```
sudo ifconfig usb0 down
```

Then take down the eth0 interface:
```
sudo ifconfig eth0 down
```
then bring it back up
```
sudo ifconfig eth0 up
```
I would also try and restart the network service just to see if it will try and connect to eth0. Type:
```
 sudo service /etc/init.d/networking restart
```

I'm curious as to what you interfaces config file looks like. So if you would kind friend, type:
```
cat etc/network/interfaces
```
and maybe give this article a read:
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

---

### Post by luge86 on 2013-12-20
Thank you for your fast reply!

Here's my interfaces file:
> lugge@lugge-desktop:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

Unfortunately i'm not at home, so i will give your other solutions a try when i am.
But as the LAN port wasn't even working during/after Kubuntu Setup (without my Smartphone ever being plugged in) i don't think there are problems related to my phone.
But yeah, as Momma said... :-)

---

### Post by tfrue on 2013-12-20
It seems as though your eth0 isn't being configured. So you will have to manually add an entry to the /etc/network/interfaces config file, which isn't hard it's just deciding whether you want DHCP or a Static IP. Give this article a read, and pay attention to the first two headings as they will probably provide the most help. 
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

---

### Post by tfrue on 2013-12-20
> Thank you for your fast reply!


No problem!

---

### Post by luge86 on 2013-12-20
Hello again,

i followed your instructions and the instructions on the link, unfortunately, it's still not working.

I added eth0 to my interface file, trying both, dhcp and static configuration.
At the moment, it looks like:
> lugge@lugge-desktop:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
  address 192.168.178.26
  netmask 255.255.255.0
  gateway 192.168.178.1


> lugge@lugge-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 94:de:80:bf:d6:b8  
          inet addr:192.168.178.26  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::96de:80ff:febf:d6b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:94 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5677 (5.6 KB)  TX bytes:0 (0.0 B)


According to ifconfig, my TX packets are still being dropped :-(

Any further suggestions?

Greetings,
lugge

---

### Post by tfrue on 2013-12-20
For the eht0 part, try and do just
```
auto eth0
iface eth0 inet dhcp
```
If that doesn't work, then remove it all the eth0 text we just added, and type:
```
iface eth0 inet static
  address 192.168.178.26
  netmask 255.255.255.0
  gateway 192.168.178.1
```
Be sure to restart the networking service, and I think doing them one at a time might make a difference.

Also, you may want to check your router and make sure that you're assigning IP addresses out of the right subnet. Usually private IP addresses are '192.168.2.1-100' or so or '192.168.1.0-100' or so. But looking at your gateway IP being 192.168.178.1 makes me wonder. My IP is from the pool '192.168.2.x with the gateway at '192.168.2.1'...So double check your router's settings.

Could you tell me the make and model of your router, please and thank you! I also want to apologize for giving you the same link twice, it was way too late for me lol.

---

### Post by luge86 on 2013-12-20
Hi chris_johnson2

this is exactly what i already did, as i stated in my previous post.
First i tried with "dhcp", then with static IP.
Or do I get you wrong and you want me to remove the loopback device? Otherwise, there's is no difference in your post and what i already did.

The static network settings are taken from Windows7 on the same machine. Under Windows, i use DHCP and 192.168.178.26 is the IP my router (AVM Fritzbox 6360) assigned me. Also, 192.168.178.1 is my router (checked with windows).

Greetings,
lugge

One more point:
sudo service /etc/init.d/networking restart
Is not working for me: /etc/init.d/networking: unrecognized service
Was this script maybe renamed for Kubuntu 13.10?
I simply restarted my PC after editing the interface file :-)

---

### Post by tfrue on 2013-12-20
Ok, the reason I restated doing them separate is because you have auto eth0 then telling it to use static in the interfaces file and no you didn't get me wrong, I was mistaken lol. Alas, we shall try a different route. I'm going to say this and it may sound deeming and mainstreamed so don't take it that way, but have you reset your computer and router recently? 

Also, I was over looking your very first post and I think that it's strange that you computer loaded a driver that your PCI card doesn't use. These are the drivers that your card supports, RTL8111/8168/8411, but the kernel is using 8169. So I went to Realtek's website and found your driver for Linux that supports the right kernel. I was reading through the README file, and I want to note that it tells you to look to see if your computer has loaded the right driver, and it may return that you have, but I suggest loading the 8168 driver since that is supported by your card. I'm going to link the folder from my dropbox and let me know when you get it, so I can delete the link.

Good Luck,
Chris

---

### Post by tfrue on 2013-12-20
Here is the link to the page I was browsing if you would rather download it from their. [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

---

### Post by Iowan on 2013-12-20
> **luge86 said:**
> 

One more point:
sudo service /etc/init.d/networking restart
Is not working for me: /etc/init.d/networking: unrecognized service
Was this script maybe renamed for Kubuntu 13.10?
I simply restarted my PC after editing the interface file :-)
That should be just **sudo service networking restart**... although I've seen a [bug report]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/1102507") that it crashes. 
**sudo service network-manager restart** is offered as an alternative.

---

### Post by luge86 on 2013-12-20
Ok, I now have the 8168 driver installed and loaded.

Still exactly the same behaviour :-(

Greetings,
lugge

---

### Post by tfrue on 2013-12-20
Bummer! Ok, I did a little Google searching and I will link the pages here so you can read them instead of me trying to explain them. All though, one did say try and disable dhcpd before activating a service like networkmanager, check the output of 'systemctl'. It doesn't really elaborate, but I did read on one of the articles that the networkmanger service tries to start dhcp, so if dhcpd is started before the networkmanager service it might cause conflicts. But yet again, I will link the articles here.

[http://www.linuxquestions.org/questions/slackware-14/networkmanager-cannot-connect-to-wired-connection-in-slackware-14-1-a-4175484525/](http://www.linuxquestions.org/questions/slackware-14/networkmanager-cannot-connect-to-wired-connection-in-slackware-14-1-a-4175484525/)

[http://www.linuxquestions.org/questions/slackware-14/no-networking-after-upgrade-to-14-1-a-4175484128/](http://www.linuxquestions.org/questions/slackware-14/no-networking-after-upgrade-to-14-1-a-4175484128/)

and here is the one with systemctl command [https://bbs.archlinux.org/viewtopic.php?id=172678](https://bbs.archlinux.org/viewtopic.php?id=172678)

Best of Luck,
Chris

---

### Post by tfrue on 2013-12-20
If you wanted, try and Live boot a different distro and see what luck you have with it. Maybe even try and reinstall Kubuntu.

---

### Post by luge86 on 2013-12-20
dhcpd is not installed on my machine (im not running a server, so this seems to be OK).

However, syslog tells me that:

lugge@lugge-desktop:~$ grep -i eth /var/log/syslog | grep NetworkManager | tail
Dec 20 19:34:39 lugge-desktop NetworkManager[905]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Dec 20 19:34:39 lugge-desktop NetworkManager[905]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 20 19:34:39 lugge-desktop NetworkManager[905]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Dec 20 19:34:39 lugge-desktop NetworkManager[905]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 20 19:34:39 lugge-desktop NetworkManager[905]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Dec 20 19:34:39 lugge-desktop NetworkManager[905]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec 20 19:34:39 lugge-desktop NetworkManager[905]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 20 19:34:39 lugge-desktop NetworkManager[905]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 20 19:34:39 lugge-desktop NetworkManager[905]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec 20 19:34:39 lugge-desktop NetworkManager[905]: <info> (eth0): DHCPv4 state changed nbi -> preinit
lugge@lugge-desktop:~$ grep -i eth /var/log/syslog | grep NetworkManager | tail
Dec 20 19:34:39 lugge-desktop NetworkManager[905]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Dec 20 19:35:24 lugge-desktop NetworkManager[905]: <warn> (eth0): DHCPv4 request timed out.
Dec 20 19:35:24 lugge-desktop NetworkManager[905]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2984
Dec 20 19:35:24 lugge-desktop NetworkManager[905]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Dec 20 19:35:24 lugge-desktop NetworkManager[905]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Dec 20 19:35:24 lugge-desktop NetworkManager[905]: <info> (eth0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Dec 20 19:35:24 lugge-desktop NetworkManager[905]: <warn> Activation (eth0) failed for connection 'Wired connection 1'
Dec 20 19:35:24 lugge-desktop NetworkManager[905]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Dec 20 19:35:24 lugge-desktop NetworkManager[905]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Dec 20 19:35:24 lugge-desktop NetworkManager[905]: <info> (eth0): deactivating device (reason 'none') [0]


Makes sense. According to ifconfig, i receive broadcast messages on eth0 (must be DHCP Discovery announcements from my router).
NetworkManager recognizes that, but stage4 fails because the TX packets are not transmitted. Instead, they are "dropped", whatever that means.

However, i think the DHCP thing is the wrong thing to think of.
Because, if i try a static IP (with interfaces file), i have no working connection as well. There are still the TX packets being dropped.
So, i guess this is the real problem. Someone in the network stack drops my TX messages :-)
And because the answers to DHCP announcements are the first packets being sent, this makes us think the problem is related to DHCP...

---

### Post by tfrue on 2013-12-20
Well my friend, I haven't given up yet. I shall help you battle the someone in the network stack that keeps dropping your TX messages. In the meantime thou, this article might help(I know how excited you are to read another article, but this one seems to go more in depth than the others.):
[http://ubuntuforums.org/showthread.php?t=1816095](http://ubuntuforums.org/showthread.php?t=1816095)

---

### Post by sanderj on 2013-12-20
> **chris_johnson2 said:**
> If you wanted, try and Live boot a different distro and see what luck you have with it. Maybe even try and reinstall Kubuntu.

+1 ... I would just live-boot Kubuntu 13.10 from USB/CD and see if your eth0 works.

---

### Post by PaulBx on 2013-12-22
> $ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

For what it's worth, I get exactly the same result from this command, and my eth0 works fine (lubuntu).

When I use static addressing I always ensure it is outside the range that dhcp is handing out leases in. I don't know if that is a requirement, but it can't help but simplify things. Can you turn off the dhcp server and see if your static addressing works then? Seems to me, starting at the most basic, get static addressing working first without any dhcp in the picture. Take baby steps...

---

### Post by luge86 on 2013-12-22
First of all, Sorry for not replying here for over a day :-)
Well, it's still not working...

@chris_johnson2:
Thank you for your help. I also read the linked article, but i cannot see how this is related to my problem.

@ sanderj:
before installing Kubuntu, i tried several LiveCDs. I got this problem on all of them.
However, all of them were Debian-based (like Linux Mint for exampel).
Maybe i should try a completely different distribution, which may use different network settings / tools. Can you give mea hint on that? Maybe Slackware or OpenSuse?

@ PaulBx:
Yes, my Lubuntu-runniong Notebook has a similar interfaces file and is getting a dynamic IP without any problems.
I will give your idea a try. But, as i stated in my previous post, it seems that the NetworkManager does indeed try to get a IP from my router.
However, as no TX packets leaves my computer, the router does not reply, and so the NetworkManger times out.
The packet loss is my real problem i guess.

---

### Post by sanderj on 2013-12-22
So even with running other LiveCDs you have the problem? Even before installing? 

That makes me think it is a hardware problem, but you said the LAN connection works well under Windows, right? Weird.

Wait, some weeks ago there was something with non-working onboard ethernet and USB3 ... caused by a (BIOS?) boot setting ... I'll have a look.

---

### Post by sanderj on 2013-12-22
OK, worth a try: IOMMU. Can you read [http://ubuntuforums.org/showthread.php?t=2111223&page=2](http://ubuntuforums.org/showthread.php?t=2111223&page=2) and set IOMMU to yes?

That problem is not completely the same, but worth a try.

---

### Post by luge86 on 2013-12-22
Thank you sanderj,

i'm not finished reading your article, but it sounds good :-)
The guy has a very similar problem, and my USB2.0 ports are not working either.
I'm just trying not to be too euphoric :-)

---

### Post by luge86 on 2013-12-22
Haha, it, worked for me, too :-)

I just enabled IOMMU in the BIOS and now my NIC and my USB2.0 ports are working.

I love you man, many thanks :-)
(I spend countless hours - no, days! - on this...)

---

### Post by sanderj on 2013-12-22
> **luge86 said:**
> Haha, it, worked for me, too :-)

I just enabled IOMMU in the BIOS and now my NIC and my USB2.0 ports are working.

I love you man, many thanks :-)
(I spend countless hours - no, days! - on this...)

Cool! And "IOMMU" is just a setting in your BIOS? Can you post a picture of that BIOS setting screen?

And can you check if "IOMMU" is in your dmesg (or anywhere else)? My dmesg does not reveal too much about IOMMU, but I must say my laptop's BIOS has no IOMMU setting:

```
$ dmesg | grep -i iommu
[    0.275303] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    4.698588] vboxpci: IOMMU not found (not registered)

```

Last remark: as Windows can live without the IOMMU setting, IMHO this is a bug in the Linux kernel and it might be worth registering it as a bug on [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/) ... not that I expect a resolution from launchpad, but just for the record.

---

### Post by tfrue on 2013-12-22
Wow, that simple huh. I'm sorry that I was unable to help you with that because I have never seen that before, but I guess we all learned from this right? Anyway, glad to hear that you finally got it fixed. It was great troubleshooting with you and thanks for working with me! Have a nice day, and don't forget to mark this as solved.

Chris

---

