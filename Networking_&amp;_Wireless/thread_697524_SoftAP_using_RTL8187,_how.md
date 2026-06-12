---
title: "SoftAP using RTL8187, how?"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by pink_fone on 2008-02-15
Hi guys!  I've been searching the forum and tried a couple of how tos but to no avail.  Basically I would like to setup my ubuntu box as SoftAP using my RTL8187.  I think I've got the drivers installed properly as shown below:

wlan0     IEEE 802.11g  ESSID:"testing"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Which leads me to the question, how do I exactly configure ubuntu to act as SoftAP?  My card does support SoftAP as I was able to do this using xp.  Many thanks in advance!!

---

### Post by mrsteveman1 on 2008-02-15
The mode you want is master, managed is a client mode (station).

---

### Post by pink_fone on 2008-02-15
how do I actually do that?  I tried this: 

sudo iwconfig wlan0 mode master

and got this:

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

Any ideas?  

Thank you very much for the help! :)

---

### Post by mrsteveman1 on 2008-02-15
Which driver are you using? Did it come with the system or did you install the one from realtek?

I ask because the driver you are using right now might not support master mode at all.

From looking over the source for the driver realtek publishes on their site (might be old), it does appear to support master mode.

---

### Post by pink_fone on 2008-02-16
Hi yah Steve! :)  thank you so much for taking time to help me.  Anyway, I used the windows xp/2k driver and used "Windows Wireless Driver" app but since that didn't work, I'm downloading the linux version and will give it a try.  Will let you know in a bit if it works or not.

---

### Post by mrsteveman1 on 2008-02-16
Windows drivers never support monitor or master mode.

Some windows drivers may be able to do softap but for that to work in linux you need the native driver.

---

### Post by pink_fone on 2008-02-16
That explains it.  I'm now trying the linux driver.  will update in a bit..

---

### Post by pink_fone on 2008-02-16
I downloaded this: debian31-8187(110).zip and extracted the files.  Went inside the "module" folder and run: 

sudo ./load

and got this:

insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 Invalid module format
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 Invalid module format
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 Invalid module format
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 Invalid module format
insmod: error inserting 'ieee80211-rtl.ko': -1 Invalid module format
insmod: error inserting 'r8187.ko': -1 Invalid module format

any ideas?

---

### Post by mrsteveman1 on 2008-02-16
Those modules probably aren't compiled for your specific kernel.

Realteks source driver is [here]("ftp://66.104.77.130/cn/wlan/rtl8187_linux_26.1025.0328.2007.tar.gz")

Are you sure that the driver isn't available from ubuntu directly? It might be in the repos which would make things much more simple here. I believe they used to package these drivers up for users, I'll check.

If they don't have a package for this chip in ubuntu i'll post how to compile the source, since its fairly complicated in this case.

---

### Post by pink_fone on 2008-02-16
By repos, you mean the add/remove and synaptic?  I already tried and sadly failed. :(  for the add/remove, no hits at all.  for synaptic, only has the one for Ethernet and not for usb wifi.  Thanks again in advance for the help! :)  I'll wait for your instructions on how to compile. :)

---

### Post by mrsteveman1 on 2008-02-16
first setup the system for compiling:

```
sudo apt-get install build-essential linux-headers-generic unzip
 
```

The basic instructions are [here]("http://aircrack-ng.org/doku.php?id=r8187")

If you get any errors let me know. I get some symbol errors when i load the module but you might not.

This driver is from the aircrack website because the one on realteks site both doesn't compile on ubuntu 7.10 for some reason, and because it seems to have bugs.

---

### Post by pink_fone on 2008-02-18
Apologies for the late reply, was caught up with work.  Anyway, I'll give it a try later once I get home.  :)  Again, many thanks for the help! :guitar:

---

### Post by pink_fone on 2008-02-18
I was able to install!!! :guitar: thank you very much!  will try it tomorrow as my sister borrowed my wifi usb.  thanks thanks!! :guitar: rep for you! :)

---

### Post by pink_fone on 2008-02-19
Steve pls. help, I'm still getting this: 

sudo iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

any thoughts? :(

---

### Post by mrsteveman1 on 2008-02-19
Are there any errors in dmesg with the new driver?

It might be a good idea for you to post a bugreport about this with ubuntus kernel developers.

Is wlan0 the only network interface listed with ifconfig -a ? (other than the wired interface)

---

### Post by pink_fone on 2008-02-20
Nope, no errors at dmesg output.  For ifconfig -a:

eth0      Link encap:Ethernet  HWaddr 00:E0:5F:10:9B:54  
          inet addr:192.168.250.251  Bcast:192.168.255.255  Mask:255.255.224.0
          inet6 addr: fe80::2e0:5fff:fe10:9b54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4684 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1044334 (1019.8 KB)  TX bytes:2172490 (2.0 MB)
          Interrupt:16 Base address:0x8f00 

eth1      Link encap:Ethernet  HWaddr 00:11:09:5E:34:6B  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6160 (6.0 KB)  TX bytes:6160 (6.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1A:EF:00:D8:D7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-EF-00-D8-D7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I only have one wifi usb device.  now I'm wondering what wmaster0 is.  Also, how can I check that I'm using the driver that you taught me to install?  I'm thinking that I'm still using the old driver.

---

### Post by mrsteveman1 on 2008-02-20
What does iwconfig tell you right now?

Since there are actually 3 interfaces there, its hard to say which one you set modes on.

If you installed the new driver it wrote over the old one im sure, so that shouldn't be a problem.

BTW: what is lshw -C network telling you now?

---

### Post by pink_fone on 2008-02-21
for iwconfig:

sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


for lshw -C network:

WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: 10
       serial: 00:e0:5f:10:9b:54
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.250.251 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth1
       version: 78
       serial: 00:11:09:5e:34:6b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.0.1 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:ef:00:d8:d7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


I hope this gives us clue on my problem. :(  Also, how do I change from 802.11g to 802.11b?

Many thanks for the patience!

---

### Post by cowboytuna on 2008-02-21
?

---

### Post by pink_fone on 2008-02-21
Ok, I think I really did something super stupid.  Now, whenever I'm trying to run this command: iwconfig, I get this result:

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

I think this is because of this step in aircrack-ng.org:

Move /lib/modules/k#/kernel/drivers/net/wireless/mac80211/rtl818x/rtl8187.ko to a safe place. The “k#” and/or other parts of the path will be different for your distribution/system. Use “locate 8187.ko” or “find /lib/modules -name *8187*” to find the full path.

How do I get things back to order?  :( I'm really confused now.. Pls. help :(

---

### Post by mrsteveman1 on 2008-02-21
On gutsy, this module is part of the ubuntu supplied modules so you can reinstall it like this:

```
sudo aptitude reinstall linux-ubuntu-modules-2.6.22-14-generic
```

You can also reinstall the kernel image to make sure the other modules are still present:
```

sudo aptitude reinstall linux-image-generic
```

These will put back all the stock modules that came with the system in case something goes wrong.

---

### Post by shiver on 2008-03-24
@ pink_fone: Did you ever get this to work? I'm getting a laptop but I don't have an access point so I thought I could use the onboard rtl8187 on my desktop machine. I haven't found any conclusive answer to whether the master mode works or not.

---

### Post by pink_fone on 2008-04-05
Hi Shiver! Sadly, I wasn't able to. :(  I again tried doing the steps which Steve posted before: [http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187)  and I was able to set it to master mode.  However, when I use my P1i to search for wifi signals, I couldn't find any.  

Here's the output of iwconfig:
wlan0     802.11b/g linked  ESSID:"Penguin"  
          Mode:Master  Channel=5  Access Point: 00:1A:EF:00:D8:D7   
          Bit Rate=11 Mb/s   Tx-Power=11 dBm   
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

any ideas?  It's working properly in my XP but I dont want to use that OS :(
BTW, apologies for the late reply; I was caught up with work..

---

### Post by pink_fone on 2008-04-08
Hi Shiver! In case your still wondering how I was able to go around this, I just installed an XP copy at virtualbox. :)  works like a charm ;)  Now I can still use my computer at AP mode while using ubuntu. :guitar:

---

### Post by AVT- on 2008-06-14
I'm trying to do the same thing, however, even after installing new drivers, I still can't set to master.

---

