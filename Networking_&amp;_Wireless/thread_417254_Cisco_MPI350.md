---
title: "Cisco MPI350"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by Ichijin on 2007-04-21
Im running feisty fawn and can't get my Mini PCI wireless card to work.  I am a complete noob, but have search almost everywhere with no luck.  the problem is that it can detect APs just fine, just that it can't connect to any of them.

Kernel:  2.6.20-15
Firmware: 5.60.21

Please help

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"default"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:46:87:26:8E   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=93/100  Signal level=-49 dBm  Noise level=-96 dBm
          Rx invalid nwid:6  Rx invalid crypt:210  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:609   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"default"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:46:87:26:8E   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=93/100  Signal level=-49 dBm  Noise level=-96 dBm
          Rx invalid nwid:6  Rx invalid crypt:210  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:609   Missed beacon:0

```

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:4A:B4:EC  
          inet addr:192.168.0.116  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fe4a:b4ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1941 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1729 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1374079 (1.3 MiB)  TX bytes:273481 (267.0 KiB)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr 00:0D:65:72:C3:F8  
          inet6 addr: fe80::20d:65ff:fe72:c3f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:20 dropped:0 overruns:0 frame:20
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:10 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:5316 (5.1 KiB)
          Interrupt:17 Base address:0xa800 

eth1:avah Link encap:Ethernet  HWaddr 00:0D:65:72:C3:F8  
          inet addr:169.254.10.18  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:628 (628.0 b)  TX bytes:628 (628.0 b)

```

There is a linux driver out by cisco and its as follows:
**linux-acu-driver-v21.tar.gz  **
Published 11/Apr/2007
Linux Client Utilities and Driver. PCM, LMC, PCI, and MPI Client Adapters. Supports Radio Firmware up to and including 5.30.17. Supports Linux Kernel 2.4.18 and 2.4.20-28.
Size: 718.24 KB
Minimum Memory: DRAM:-- Flash:--



I have no idea how to install the driver and i have used lower versions of the firmware but it still doesn't work

---

### Post by alexnb185 on 2007-04-23
I have the exact same problem as you.. it knows my adapter is there .... and it can see my networks... but it won't connect.. if you find answer please let me know [email]alexnbryan@gmail.com[/email]

---

### Post by Steven_Grimes on 2007-04-25
Anyone gotten this to work? I'm having the same issue and have tried avery forum with no luck.

Thanks,
Steven

---

### Post by tp21 on 2007-07-10
hi,
i can confirm this problem. i have thinkpad T40 with cisco MPI 350. airo driver manages to check the card, and check the networks, but never managed to build a connection.
i am using Ubuntu 7.04 with Kernel 2.6.20, and cisco firmware 5.60.17.
it is frustrating because on thinkwiki.org it says that the card should work well.
did any body tries cisco driver?
thanks

---

### Post by nilsja on 2007-10-14
i have the same problem with a thinkpad x31. it connects to non encrypted wlans, but doesn't to any kind of encrypted.:confused:

dmesg | grep eth1
> [   58.600000] airo(eth1): Found an MPI350 card
[   59.556000] airo(eth1): WPA is supported.
[   59.560000] airo(eth1): MAC enabled 0:2:8a:f1:f7:92
[   96.472000] eth1: no IPv6 routers present

---

### Post by portwolf on 2008-03-13
Same here, please could someone help out??

---

### Post by enHuxley on 2008-03-20
.. same problem here .. weirdest thing, is that on my original fresh install of gutsy, I sware I got this working, then I had to re-install because I hoarked my compiz install and now I cant get it working..

---

### Post by s4nt on 2008-04-15
I found a workaround on my mandriva 2008.1 system which has the same issue:
[http://forum.mandriva.com/viewtopic.php?p=469077#469077](http://forum.mandriva.com/viewtopic.php?p=469077#469077)
perhaps it can help you solve the issue:
> 
I have an ibm T41 with the same cisco airo 350 built in.
The problem also appeared on kubuntu 8.04 beta, which uses the 2.6.24 kernel as mandriva 2008.1 spring... (in kubuntu 7.10 and previous the card worked perfectly)

I made it work disabling (on boot) some of the modules that where causing problems with the airo module

On /lib/modules/2.6.24.4-laptop-1mnb/modules.alias **(on KUBUNTU /etc/modprobe.d/aliases)** add the word **off** as seen below to the following lines:
```


alias pci:v000014B9d0000A504sv*sd*bc*sc*i* off airo
alias pci:v000014B9d00005000sv*sd*bc*sc*i* off airo
alias pci:v000014B9d00000350sv*sd*bc*sc*i* off airo
alias pci:v000014B9d00000340sv*sd*bc*sc*i* off airo
alias pci:v000014B9d00004800sv*sd*bc*sc*i* off airo
alias pci:v000014B9d00004500sv*sd*bc*sc*i* off airo
alias pci:v000014B9d00000001sv*sd*bc*sc*i* off airo
alias aes off padlock_aes
alias aes off geode_aes
alias pci:v00001022d00002082sv*sd*bc*sc*i* off geode_aes
alias sha256-padlock off padlock_sha
alias sha1-padlock off padlock_sha
alias sha256 off padlock_sha
alias sha1 off padlock_sha
alias aes off aes_generic
alias aes off aes_i586
alias usb:v08FFp2580d*dc*dsc*dp*ic*isc*ip* off aes2501

```

The airo module will be started anyway thanks to the mandriva network manager, if not,
run as root:
Code:
```

# ifconfig eth0 down
# rmmod airo
# modprobe airo
# ifconfig eth0 up

```

*replace eth0 with the one you need as appropriate.

Hope it helps (what I really hope is that someone fixes the kernel or whatever is causing this problem...)


I forgot to add that you need to reboot for these changes to take effect!

---

### Post by samie on 2008-04-17
Hi all

I manage to make my cisco mini-pci mpi350 working in gutsy, and it can connect to wpa secure network (my AP is using wpa-psk authentication) by using NDISWRAPPER..

and suprisingly it is very easy to install it...

first you have to had the windows driver, if you don't have it I attach the *.inf file below.

after that you have to blacklist the native ubuntu driver 'airo' by writing in terminal 

```
echo 'blacklist airo' | sudo tee -a /etc/modprobe.d/blacklist
```

Then install ndiswrapper. In terminal write

```
sudo apt-get install ndiswrapper-common
```

then go to **System-->administration-->windows wireless driver** , click the install new driver and select the driver (neta504.inf). it will then tell that hardware present=yes

then you go to terminal again and write

```
sudo ndiswrapper -m 
sudo ndiswrapper -ma
sudo ndiswrapper -mi 
```

then you reboot your machine and hopefully it can detect WPA encryption now

Special thanks to Elektropod because his step make this work for me.

you can see his thread on using ndiswrapper to revive his Dell 1395 wireless in [http://ubuntuforums.org/showthread.php?t=704088]("http://ubuntuforums.org/showthread.php?t=704088")

I am writing in this forum by using cisco mpi350, and so far it works great

Hope that can Help

---

### Post by petitchevalroux on 2008-04-19
Samie I try your solution on gutsy but when i load the .inf file provided in ndisGTK i get an "Invalid driver", Any idea ?

---

### Post by samie on 2008-04-19
Hmm .. that strange.. your mpi350 card maybe different from mine. btw mine is a MINI-PCI not an PCMCIA.

Maybe this one will work.. I think it's for the PCMCIA type

---

### Post by petitchevalroux on 2008-04-19
No mine is a PCI too, but ndiswrapper complain about missing file when loading the inf file. 

```

couldn't find "pcx504.51" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "pcx504b.img" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "pcx504.51" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "pcx504a.img" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete

```

Did you have this file somewhere or the complete driver not only the .inf file  ?

---

### Post by petitchevalroux on 2008-04-19
I succeed in find it in the cisco drivers and everything is ok now. Thank you for you help to manage this card :D. I just give the complete driver FOR MINI PCI CISCO card.

The way to do it work on gusty is (from samie experience and mine) 

1) Download join file to this message and extract it 
2) install ndiswrapper
```

sudo apt-get install ndiswrapper-utils-1.9

```
3) Blacklist the airo module
```

echo 'blacklist airo' | sudo tee -a /etc/modprobe.d/blacklist

```
4) Remove the airo module from kernel
```

sudo rmmod airo 

``` 
5) Load into ndiswrapper the windows driver
```

sudo ndiswrapper -i pathto/netA504.inf

```
6) store ndiswraper conf
```

sudo ndiswrapper -m 
sudo ndiswrapper -ma
sudo ndiswrapper -mi

```
7) load ndiswrapper in the kernel
```

sudo modprobe ndiswrapper

```

And it should work

---

### Post by spawnywhippet on 2008-04-25
Sorry, I'm a total noob. Where do you extract the attachment to, as I get the following error in step 1 of the process?

andy@ubuntu-laptop:~/neta504$ pwd
/home/andy/neta504
andy@ubuntu-laptop:~/neta504$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.9

---

### Post by petitchevalroux on 2008-04-25
@spawnywhippet may be try
```

sudo apt-get update
sudo apt-get install ndiswrapper-common

```

---

### Post by spawnywhippet on 2008-04-25
Thanks for all the help, I found this thread which successfully assisted to get my Wireless and WPA working

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by yukonho on 2008-04-26
You shouldn't need to bother with ndiswrapper to get the cisco 350 card to work. It's always worked reliably in Linux until this recent problem.

This is a reported bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398")

I fixed it this way, which should still work even if the kernel gets updated (I think). Add the following lines to your /etc/modprobe.d/blacklist file:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes

This fixed wireless on my Cisco Aironet 350 and eliminated the hang during boot.

---

### Post by enHuxley on 2008-05-02
*BUMP* 
  Just wanted to keep this post/thread alive 'cuz it just made my day!
:guitar:

---

### Post by ibr3ak on 2008-05-05
samie and petitchevalroux thanks to you guys I finally have this pos aironet working right on hardy with wpa (still no wpa2, but I could very well do with 1). :D

---

### Post by spawnywhippet on 2008-05-05
How do I uninstall a driver for my Cisco Aironet, in order to reinstall? I used the Windows pci504.inf driver.

---

### Post by ibr3ak on 2008-05-05
> **spawnywhippet said:**
> How do I uninstall a driver for my Cisco Aironet, in order to reinstall? I used the Windows pci504.inf driver.

Try this :)

```
sudo ndiswrapper -e pci504.inf
```

---

### Post by spawnywhippet on 2008-05-05
> **ibr3ak said:**
> Try this :)

```
sudo ndiswrapper -e pci504.inf
```

I get the error: 'Couldn't delete /etc/ndiswrapper/pci504.inf. No such file or directory'.
When I browse there, there are a few files in the directory however.

The problem occured because the driver was installed whilst it was still being unpacked, so half the files were missing. I can't seem to re-install or uninstall this.

---

### Post by ibr3ak on 2008-05-05
What's the output of:

```
sudo ndiswrapper -l
```

---

### Post by spawnywhippet on 2008-05-05
andy@ubuntu-laptop:~/driver$ sudo ndiswrapper -l 
pcx504 : driver installed
	device (14B9:A504) present (alternate driver: airo)

---

### Post by ibr3ak on 2008-05-05
Have you tried running the remove or -e command without the .inf extension? Probably won't be much of a difference but give it a try.

---

### Post by spawnywhippet on 2008-05-05
nope, just the same...:(

---

### Post by ibr3ak on 2008-05-05
Try uninstalling ndiswrapper and then either 

remove the directory inside /etc/ndiswrapper with the driver files
```
sudo rmdir /etc/ndiswrapper/<folder>
```

or remove the files if they're in /etc/ndiswrapper and not in their own folder
```
sudo rm -rf /etc/ndiswrapper/<file>
```

And then try reinstalling ndiswrapper again.

---

### Post by 4red on 2008-06-04
Hi all.

I'm stumbling and grumbling towards getting my MPI350 mini-PCI card working on my R40 Thinkpad but I'm having a few residual glitches and am finally throwing in the towel and taking advantage of this forum which has already been of enormous help in getting me this far. I'm running Hardy Heron. I've blacklisted airo and installed all available updates. I followed the HOW-TO in [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539). I'm using the ndiswrapper driver, WPA-PSK and static IP. My interfaces file is:

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 10.0.0.3
gateway 10.0.0.2
dns-nameservers 10.0.0.2
netmask 255.0.0.0
wpa-driver wext
wpa-ssid qwerty
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk xyzxyz1234xyzxyz1234xyzxyz1234xyzxyz1234

The Problem is that the card will not start up when I boot. I have to run /etc/init.d/network restart to get it working although the output of that command is this error message:

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                ioctl[SIOCSIWPMKSA]: Invalid argument              [ OK ]

When I do dmesg|grep wlan0 I get this output:

[   38.960165] wlan0: ethernet device 00:02:8a:e0:0e:62 using serialized NDIS driver: neta504, version: 0x3000c, NDIS version: 0x501, vendor: 'Cisco Systems352 series Wireless LAN Adapter.', 14B9:A504.5.conf
[   39.044299] wlan0: encryption modes supported: WEP; TKIP with WPA
[   43.582460] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  137.274235] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   75.064188] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

Forgot to add that sometimes, the PC hangs during boot.

Anybody experienced this set of symptoms?

Can anybody recommend a good reliable PCMCIA 802.11g card ??

TIA

---

