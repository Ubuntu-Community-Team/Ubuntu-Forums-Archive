---
title: "Networking in new installation"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by Phil Binner on 2010-09-04
I just re-loaded my ubuntu from scratch, using a new CD. I have a choice of wired and wireless networks from the same source, a vigor DrayTek Vigor 2710 router.

Since installing I can't get onto the internet. It says I am connected over the wired connection, but I cant see the internet and I can't download updates. When I try to download updates it knows how many there are (15 updates available), however, so there must be some connection. When I query teh connection it says there is a 100 mbps connection, but this is strange as it is a gigabit router.

I tried changing the connection to wireless. I was asked for my security key, which I entered, but no joy. It just doesn't get in.

When I first installed Ubuntu on this machine a couple of years ago I had a similar problem. It turned out that Ubuntu was duplicating my password and therefore invalidating it. I fixed that temporarily by editing the file containing the password string. When I was on I downloaded WiCD, and never had a problem thereafter. Unfortunately i can't remember in detail how I did that, and I am not the kind of guy who can find out - I'm computer literate but not technically inclined.

So 2 questions.

1. Why doesn't the wired network let me connect.
2. How can I sort out the wireless connection.

My thanks go to whoever.

---

### Post by sandyd on 2010-09-04
> **Phil Binner said:**
> I just re-loaded my ubuntu from scratch, using a new CD. I have a choice of wired and wireless networks from the same source, a vigor DrayTek Vigor 2710 router.

Since installing I can't get onto the internet. It says I am connected over the wired connection, but I cant see the internet and I can't download updates. When I try to download updates it knows how many there are (15 updates available), however, so there must be some connection. When I query teh connection it says there is a 100 mbps connection, but this is strange as it is a gigabit router.

I tried changing the connection to wireless. I was asked for my security key, which I entered, but no joy. It just doesn't get in.

When I first installed Ubuntu on this machine a couple of years ago I had a similar problem. It turned out that Ubuntu was duplicating my password and therefore invalidating it. I fixed that temporarily by editing the file containing the password string. When I was on I downloaded WiCD, and never had a problem thereafter. Unfortunately i can't remember in detail how I did that, and I am not the kind of guy who can find out - I'm computer literate but not technically inclined.

So 2 questions.

1. Why doesn't the wired network let me connect.
2. How can I sort out the wireless connection.

My thanks go to whoever.
you can install wicd by downloading the wicd package on another ubuntu computer, and using apt-on-cd to transfer it over.

there is an app for windows as well, but I don't recall it atm

---

### Post by Phil Binner on 2010-09-04
Hi Carlee,

I have a couple of other windows machines, but no other linux machine. Do you have any other clues as to how I can load WiCD. Alternatively, why doesn't my wired connection get out.

---

### Post by Phil Binner on 2010-09-05
I'm having a problem getting WiCD. I have a friend with an Ubuntu machine, but how do I use the repository without installing. I went onto the WiCD website and was just told to download through the repository, but I can't do that without a connection.

Can you please tell me what apt-on-cd is and how to use it

---

### Post by Phil Binner on 2010-09-05
I found apt-on-cd using a windows computer, but when I follow the download link there's nothing to download. Since I'm using windows I was trying to download the source to load manually in ubuntu.

Help please.

---

### Post by Phil Binner on 2010-09-05
This is going on a bit. I have borrowed another Ubuntu laptop and loaded AptonCD onto it. When I try to create a CD it populates the apt list, but unfortunately WiCD is not on the list. WiCD is being used on this computer, and a search shows files all over the place, but which do I use.

It seems that the more I try to sort this problem, the more other problems I encounter. I can't say I'm feeling too positive at teh moment.

---

### Post by halitech on 2010-09-05
you don't mention what version you are using but I'm guessing 10.04 since there are only 15 updates on a new install. You can grab the deb file here

[http://mirrors.kernel.org/ubuntu/pool/universe/w/wicd/wicd_1.5.9-2_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/w/wicd/wicd_1.5.9-2_all.deb)

Once its downloaded, just right click and open with gdebi (it should be installed already). if not, open a terminal in the folder you downloaded wicd to and run
```
sudo dpkg -i wicd_1.5.9-2_all.deb
```

---

### Post by QLee on 2010-09-05
[QUOTE=Phil Binner]This is going on a bit.
...
It seems that the more I try to sort this problem, the more other problems I encounter. I can't say I'm feeling too positive at teh moment.[/QUOTE]
This is partly because of the approach you used to ask the original question (I'm not blaming you, just explaining). You mentioned wicd and so posters have concentrated on helping you install that.

However, wired interfaces almost always work with network manager so it might be useful to find out why it isn't working if you choose to use network manager.

There is nothing wrong with choosing to use wicd but if you want to troubleshoot what you now have you might post the contents of these two files:
/etc/network/interfaces
/etc/resolv.conf

and the output from the command 
ifconfig
entered into a terminal.
And, it would not hurt a bit to post what network interface card is in the computer.

Did either the wired interface or the wireless one work with the live CD previous to installing?

---

### Post by Phil Binner on 2010-09-06
I didn't try testing from the live CD before loading originally, so I have just tried it now. The problem is identical.

Strangely, this system has 2 file systems, one is 252 GB and the other 237 gb. This makes it sound as if I have a dual boot, but I re-insatlled it this morning, making sure I had not made that mistake. in both cases the requested files are as follows:

\etc\network.interfaces reads:
auto lo
iface lo inet loopback

\ect\resolve.conf reads:
# Generated by NetworkManager
nameserver 192.168.1.1

if config is as follows:

bigbin@bigbin-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d4:53:a8:39  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fe53:a839/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:181 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2920 (2.9 KB)  TX bytes:4765 (4.7 KB)
          Interrupt:19 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37228 (37.2 KB)  TX bytes:37228 (37.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:14:d7:76  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

The wired network is connected to the motherboard. It's an ASUS something, I can probably get teh details by grovelling if it is really necessary.

There is a bit more history to this problem. Originally I had a working Ubuntu system on 10.04. It was absolutely fine, but had a small disc. I wanted a MythTV system so I installed extra RAM (2gb to about 2.7gb) and a second 500gb hard drive. All still seamed fine. I loaded Mythbuntu as a dual boot, and eventually got that going. When I booted into Ubuntu all was fine with the network, but in Mythbuntu I had the problem I have now. I didn't pay much attention at that time, because I was concentrating on MythTV setup, and in any case I had quickly decided that I didn't want the dual boot, so as soon as I had ironed out the problems I was going to wipe it and start again.

While I had the dual boot both systems started to behave erratically - the sound went on and off, and the USB connections for the keyboard and mouse were erratic.

While I was re-installing the new Ubuntu load this morning I noticed the following things I hadn't noticed before - I usually walk away and come back when it has finished. The install starts by copying files, but at 79% complete it says it is Retrieving Files, which suggests it's trying to get additional stuff from the internet. It eventually completes, but is it missing something. 

When I restarted after the installation this morning there was a long list of errors while it was trying to shut down. One sample line reads:

[2943.789657] end_request: I/O error, dev sr0, sector 522968

All the lines remaining on the screen are identical except for the second and last number.

Does that mean there is a problem with the new disk. It seemed OK before I started this process. A manual restart on teh system works OK, but the new installation is clunky and obviously unwell.

If there's any other usefull information I can provide please ask.

Thanks

Phil B

---

### Post by Phil Binner on 2010-09-06
One thing I forgot to add is that the new system is 10.04.1

---

### Post by QLee on 2010-09-07
[QUOTE=Phil Binner]
Strangely, this system has 2 file systems, one is 252 GB and the other 237 gb. This makes it sound as if I have a dual boot, but I re-insatlled it this morning, making sure I had not made that mistake. [/QUOTE]

Well, the system didn't get that way except by your actions, it may have not done what you thought. Perhaps it would be better to sort this out first and avoid having to resize partitions on a working system.

[QUOTE=Phil Binner]in both cases the requested files are as follows:

\etc\network.interfaces reads:
auto lo
iface lo inet loopback

\ect\resolve.conf reads:
# Generated by NetworkManager
nameserver 192.168.1.1[/QUOTE]

Well, that looks ok. Obviously you have not installed wicd yet. What those seem to indicate is that your router has LAN IP address 192.168.1.1 and that it is being used as nameserver for your LAN, that could be normal.

[QUOTE=Phil Binner]if config is as follows:

bigbin@bigbin-ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:13:d4:53:a8:39
inet addr:192.168.1.20 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::213:d4ff:fe53:a839/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:31 errors:0 dropped:0 overruns:0 frame:0
TX packets:28 errors:0 dropped:181 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2920 (2.9 KB) TX bytes:4765 (4.7 KB)
Interrupt:19 Base address:0xe400[/Quote]

Well, something is acting as a DHCP server and handing out the IP address 192.168.1.20 to your ethernet interface. If you don't have some other DHCP server running, that's going to be coming from your router.

Sure looks like you should have a connection on eth0.

[QUOTE=Phil Binner]...

wlan0 Link encap:Ethernet HWaddr 00:11:50:14:d7:76
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)[/QUOTE]

Wireless interface didn't get an IP address but we expected that.

[QUOTE=Phil Binner]The wired network is connected to the motherboard. It's an ASUS something, I can probably get teh details by grovelling if it is really necessary.[/QUOTE]

Naw, we could query the system but that isn't necessary, we know it's up, it was assigned an address when it came up.


[QUOTE=Phil Binner]There is a bit more history to this problem. Originally I had a working Ubuntu system on 10.04. It was absolutely fine, but had a small disc. I wanted a MythTV system so I installed extra RAM (2gb to about 2.7gb) and a second 500gb hard drive. All still seamed fine. I loaded Mythbuntu as a dual boot, and eventually got that going. When I booted into Ubuntu all was fine with the network, but in Mythbuntu I had the problem I have now. I didn't pay much attention at that time, because I was concentrating on MythTV setup, and in any case I had quickly decided that I didn't want the dual boot, so as soon as I had ironed out the problems I was going to wipe it and start again.[/QUOTE]

It seems you don't have that first hard drive in the system any longer since you mentioned only those two approx. 250GB partitions

[QUOTE=Phil Binner]While I had the dual boot both systems started to behave erratically - the sound went on and off, and the USB connections for the keyboard and mouse were erratic.[/QUOTE]

Well that might be hardware failing, it's pretty unlikely you'd manage to mis-configure both systems at the same time to create the same erratic behaviour. 

[QUOTE=Phil Binner]While I was re-installing the new Ubuntu load this morning I noticed the following things I hadn't noticed before - I usually walk away and come back when it has finished. The install starts by copying files, but at 79% complete it says it is Retrieving Files, which suggests it's trying to get additional stuff from the internet. It eventually completes, but is it missing something.[/QUOTE]

Can you explain that, "it's missing something", was there an error message to that effect or some other way you know this? Did you happen to notice if the router was talking to the system during this (lights flashing, especially the led that signifies the connection talking to the Internet), sounds like the system looking for upgrades.

[QUOTE=Phil Binner]When I restarted after the installation this morning there was a long list of errors while it was trying to shut down. One sample line reads:

[2943.789657] end_request: I/O error, dev sr0, sector 522968

All the lines remaining on the screen are identical except for the second and last number.

Does that mean there is a problem with the new disk. It seemed OK before I started this process. A manual restart on teh system works OK, but the new installation is clunky and obviously unwell.[/QUOTE]

Well, maybe the disk or the drive, or some piece of hardware or cable, something caused an I/O error, presumably a failed read. Did it finish the shutdown completely or did you have to hard boot?

"Clunky"? As in didn't install correctly, or is missing something, or what?


I hesitate to suggest you try too much else until you sort out the partitioning and what you are going to do about it and verify that the system hardware is OK. That erratic behaviour from both installs in your previous configuration makes me wonder about the hardware. You might try running memtest overnight and see if the system is still running in the morning or using the live CD for a while and see if there is any erratic behaviour while you are doing normal tasks. You could, while you have the live CD up, go to System-->Administration-->Hardware Drivers, see if any are suggested. And do this with the wired connection plugged in, don't try to use the wireless yet.

Whew, this is a long one and nobody likes reading long posts.

---

### Post by jrev on 2010-09-07
In a console type :
```
ping google.com
```to check your INTERNET connection and tell us the answer
have you got a connection icon (network applet)on your main dashboard ?

---

### Post by bredman on 2010-09-07
I think your priority should be to get your wired connection working, because it looks like it is almost perfect.

Please post the result of the following command
route

This will show where your IP traffic is being routed. There is a chance that the wired connection is perfect, but the IP traffic is being sent elsewhere.

It would also be useful to know exactly what type of network hardware you have, just in case it is unusual. Therefore please enter the command
lspci

This will show the hardware connected to your PCI bus. Look for anything referring to ethernet or WiFi, and post the result to us.

---

### Post by gauravj on 2010-09-07
completely turn off the wireless, by switch(if available on your machine) and by right clicking on network-applet.
Just turn off every other mode of connection except the one you 
intend to use.
I guess the various modes of connection interfere somehow.

This solved the same problem for me, hope this helps.

---

