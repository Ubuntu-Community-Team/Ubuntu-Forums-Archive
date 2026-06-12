---
title: "Can not find wireless networks"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by shiznatix on 2007-03-04
I just upgraded to Edgy from Dapper. IN Dapper my wireless was working just fine but now that I upgraded I am having problems.

I have my wireless card installed and it seams to be setup no problem. The problem comes when I try to find a wireless network. I go to the network configuration stuff and there are no networks under the essid drop down even though I know there are some around. Then when I try to put in an essid that I know is around it won't connect.

So I was wondering if there was something special I have to do to get my wireless card to actually detect wireless networks in range.

This is not an isolated problem as it happened on 2 laptops that I was putting edgy on, one of them I upgraded from dapper and the other I did a fresh install of ubuntu on.

Any help would be awesome. Thanks.

---

### Post by Metaljaz on 2007-03-04
Try this wiki. Post the type of card that you are using.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by toasterofirony on 2007-03-04
I had a similar problem and fixed it by installing network-manager in Dapper before upgrading to Edgy.

It was a bit of a ham-fisted fix, but it worked for me.

---

### Post by shiznatix on 2007-03-04
when I do lspci I get this for my wireless card:

> 
06:00.0 Network Controller: Broadcom Corporation Unknown device 4311 (rev 91)


in ndiswrapper I installed the driver from compaq's website and it says:

> 
bcmwl5 driver installed, hardware present


The wiki did not really help me much sadly. Any ideas?

---

### Post by gradedcheese on 2007-03-04
So, what happens when you do:

```

iwlist wlan0 scan

```

(substitute wlan0 with whatever your interface is named, or run iwconfig to see which one it is).  If the card won't even scan, you probably need a different driver.

---

### Post by shiznatix on 2007-03-04
Ok after reading some tutorials it sounds like i need to blacklist bcm43xx in the file /etc/modprobe.d/blacklist

I tried this but when I restarted my computer the light on my wireless card still lights up but the card is not recognized. ndiswrapper still says the 'driver installed hardware present' but its  not working.

hopefully that can give some more information.

---

### Post by gradedcheese on 2007-03-04
> 
ndiswrapper still says the 'driver installed hardware present' but its not working.


It would help to be more specific:
- interface doesn't show up in "ifconfig -a" at all?
- shows up but iwlist scan doesn't work?
- scan works but won't associate?

---

### Post by shiznatix on 2007-03-04
> **gradedcheese said:**
> So, what happens when you do:

```

iwlist wlan0 scan

```

(substitute wlan0 with whatever your interface is named, or run iwconfig to see which one it is).  If the card won't even scan, you probably need a different driver.

what I got was:

> 
iwlist eth1 scan
eth1 No scan results


does that mean I need a different driver?

Edit: this was after I removed bcm43xx from the blacklist
Edit2: I hope this post cleared up the confusion

---

### Post by shiznatix on 2007-03-04
> **gradedcheese said:**
> 
- interface doesn't show up in "ifconfig -a" at all?


when I do ifconfig -a the record that shows up for the wireless looks like this:

> 
eth1

Link encap:Ethernet HWaddr 00:14:A5:B6:55:49
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:244 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:9856 (9.6 KiB)
Interrupt: 3


---

### Post by gradedcheese on 2007-03-04
well then you want to scan with eth1, right?  Run "iwconfig" to be sure that eth1 is a wireless interface though, the MAC prefix for your eth1 is "Gemtek Technology Co., Ltd." which is some Chinese company, but they could have used that in place of Broadcom's.

```

iwlist eth1 scan

```

---

### Post by shiznatix on 2007-03-04
When I run that I get this:

> 
shiznatix@shiznatix-laptop:~$ iwlist eth1 scan
eth1 No scan results


but i know for sure that there are wireless networks around, my computer is still right next to my wireless router.

---

### Post by chili555 on 2007-03-04
See if this helps: [http://ubuntuforums.org/archive/index.php/t-206492.html](http://ubuntuforums.org/archive/index.php/t-206492.html)

> iwpriv wlan0 network_type g
iwconfig wlan0 essid "any"
ifconfig wlan0 up
iwlist wlan0 scan

Of course, substitute your interface for wlan0 and network_type b if you have an 802.11b card.

---

### Post by shiznatix on 2007-03-04
when I run the line

iwpriv eth1 network_type g

it outputs:
> 
Invalid command: network_type


so I looked and did this command:

iwpriv eth1

and got:
> 
eth1 Available private ioctls:
set_interfmode (8BE0) : set 1 int & get 0
get_interfmode (8BE1) : set 0 & get 80 char
set_shortpreamb (8BE2) : set 1 int & get 0
get_shortpreamb (8BE3) : set 0 & get 80 char
set_swencrypt (8BE4) : set 1 int & get 0
get_swencrypt (8BE5) : set 0 & get 80 char
write_sprom (8BE6) : set 512 char & get 0
read_sprom (8BE7) : set 0 & get 512 char


the rest of the commands 'work' but of course without the first step they don't do anything.

---

### Post by gradedcheese on 2007-03-04
eth1 doesn't sound like a wifi card... can you just run "iwconfig" and post all of the output?

---

### Post by shiznatix on 2007-03-04
> **gradedcheese said:**
> eth1 doesn't sound like a wifi card... can you just run "iwconfig" and post all of the output?

certainly. heres the output:

> 
lo         no wireless extensions 

eth0     no wireless extensions

eth1     IEE 802.11b/g ESSID:"" Nickname:"Broadcom 4311"
           Mode:Managed Frequency=2.484 GHz Access Point: Invalid
           Bit Rate=1 Mb/s
           RTS thr:off Fragment thr:off
           Encryption key:off
           Link Quality:0 Signal level:0 Noise level:0
           Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
           Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0      no wireless extensions


I don't know where the sit0 is coming from. Thats the entire ouput of iwconfig.

---

### Post by gradedcheese on 2007-03-04
Oh, ok so eth1 is correct.  'sit0' as I understand it is an IPv4 to IPv6 bridge and you can just ignore it (it's not a real interface).  It may be that you don't have the correct driver installed for this exactly Broadcom chipset, perhaps?  I don't have much experience with ndiswrapper because I only buy Linux-supported cards, but someone else should be able to help you.  I just wanted to make sure you're working with the right interface at least.

---

### Post by shiznatix on 2007-03-04
I uninstalled it from ndiswrapper and the device shows up in iwconfig correct but in network-admin it says that the device is not configured.

The same things is happening even thought I reinstalled the driver so maybe it is a driver problem. ndiswrapper says "driver installed, hardware present" but when I do

"iwconfig eth1 scan" it says "Error: unrecognised wireless request 'scan'"

so maybe this is a driver problem?

---

### Post by fdrake on 2007-03-04
you should type:
iwlist eth1 scan
to scan the present networks aroud you

---

### Post by shiznatix on 2007-03-04
> **fdrake said:**
> you should type:
iwlist eth1 scan
to scan the present networks aroud you

haha my bad. when I do:

"iwlist eth1 scan" i still get "eth1 No scan results"

---

### Post by fdrake on 2007-03-04
try this:
sudo ifconfig eth1 up
(write the password)
ifconfig
(copy the results)
iwlist eth1 scan
if you still don't see any result past here the output of ifconfig

---

### Post by chili555 on 2007-03-05
You seem to have a conundrum and a more serious issue. 

First the easy one: You can't readily associate to an access point or router unless you can set the bit-rate or the ESSID. This comes from Ndiswrapper's FAQ: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ](http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ) The iwpriv of your particular card does not permit setting the bit-rate. As well, you don't know the ESSID, precisely, unless you can scan, which you cannot. 

Can you get into the configuration page of the router and tell the ESSID? If so, sudo iwconfig eth1 essid <router's_essid> might kick your interface to life.

Next, the hard one: I notice your interface is eth1. Here: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29) it says your interface must be wlan0.> If your wireless device initially shows up as eth1, go back to step 2 and comment out the eth1 line in /etc/iftab. Then resume the rest of the instructions. If you don't comment out the eth1 entry, ndiswrapper won't be able to alias the device as wlan0.

I think I would consider bringing down eth1: sudo ifdown eth1; duplicating all my eth1 entries as wlan0 in /etc/network/interfaces; commenting out all eth1 entries; then commenting out eth1 in /etc/iftab. Then, after saying my prayers carefully, I would reboot.

If it doesn't work, you can always reverse the above since items are commented out and not deleted.

DISCLAIMER: I've never actually done this myself, my ndiswrapper card worked fine from the gitgo.

---

### Post by shiznatix on 2007-03-05
Ok I changed some things but still can not get eth1 to become wlan0. Here is what all of my config files look like and what the commands produce:

sudo ifdown eth1:

> 
ifdown: interface eth1 not configured


/etc/network/interfaces:

> 
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0


I dont know what eth2 is in that one.


/etc/iftab:

> 
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:16:d4:39:2d:00 arp 1
#eth1 mac 00:14:a5:b6:55:49 arp 1


I commented out the eth1 there.

Sadly when I commented it out, nothing changed.

---

### Post by shiznatix on 2007-03-05
also, the biggest thing to me is that this is happening on 2 completly different laptops. 1 with integrated wireless the other with a pcmci card that was working 100% perfect in dapper. I did a fresh install of edgy on the one with integrated wireless and I did an upgrade on the one with the pcmci card.

The one I have been giving all of the information and output on is the one with integrated wireless but since it is the exact same problem I am starting to think there is some underlining problem not associated with the cards themselves (it worked fine in dapper!)

is there no way that I can get the wireless support dapper offered while still staying with edgy?

---

### Post by Metaljaz on 2007-03-05
Have you tried reading through the below thread to see if you maybe missed something. After the initial steps you have to select the version of Ubuntu that you are using, then proceed.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by shiznatix on 2007-03-05
I just tried that with the bcm43xx part but still whenever I try to scan or connect to a network it wont even get a signal.

I find it suspicious though that it keeps coming up as an "Unknown Device" in lspci:

> 06:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)


---

### Post by liljoe76 on 2007-03-05
> I find it suspicious though that it keeps coming up as an "Unknown Device" in lspci:
i hear ya on that, infact if i was shmarter i woulda bought a different laptop not so long ago that had a different wireless vendor. the unknown device is 'normal' and the wiki that you've been referred to is the only things thats every gotten my broadcom up and running. [Wicd Manager]("http://compwiz18.blackhole.cx/wicd/wb/")
i like it more than any other wifi managers.

---

### Post by shiznatix on 2007-03-05
> **liljoe76 said:**
> i hear ya on that, infact if i was shmarter i woulda bought a different laptop not so long ago that had a different wireless vendor. the unknown device is 'normal' and the wiki that you've been referred to is the only things thats every gotten my broadcom up and running. [Wicd Manager]("http://compwiz18.blackhole.cx/wicd/wb/")
i like it more than any other wifi managers.

I just installed that but it did not work. I am half tempted to just format and install dapper and see if that works. otherwise I might have to bite the bullet and buy another wireless card.

---

