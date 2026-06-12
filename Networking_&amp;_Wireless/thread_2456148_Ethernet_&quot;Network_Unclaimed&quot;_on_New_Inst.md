---
title: "Ethernet &quot;Network Unclaimed&quot; on New Install of Ubuntu 16.04.6 LTS"
date: 2021-01-05
forum: Networking &amp; Wireless
---

### Post by theexpert1234 on 2021-01-05
[INDENT]                     Hello all,

I am a new Ubuntu user who recently installed Ubuntu 16.04.6 LTS to dual boot  with Windows 10. My issue is that Ethernet  menu is  not showing up so I cannot establish an internet connection (also I have no wifi card installed on my system). This  is essential to doing anything so it's the first thing I'd like to take  care of.The Ethernet network is working fine in windows so I know the  router isn't the problem. I've done a bit of searching and it seems like  this is due to me not having the right drivers installed but I don't  know where to get them. I've seen people with similar issues get their  problems solved so I've copied some of the outputs some people have  asked them to post on their threads. Hopefully this will expedite my  debugging process.

Please note that I'm as new as a user as possible so detailed  instructions would be greatly appreciated. Also, keep in mind that I DO  NOT HAVE INTERNET. Most of the solutions I've seen online ask you to  "download" this or "apt-get" that. I can download something in Windows  and access it from Ubuntu but please don't suggest things that require  me to have internet within Ubuntu.

Below, I have the output to certain commands (in bold) that I've seen other people ask for:
**ifconfig**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:20336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1505136 (1.5 MB)  TX bytes:1505136 (1.5 MB)

**sudo lshw -C network**
*-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:51100000-5111ffff

**uname -r**
4.4.0-142-generic

**lspci**
00:00.0 Host bridge: Intel Corporation Device 9b43 (rev 05)
00:02.0 VGA compatible controller: Intel Corporation Device 9bc5 (rev 05)
00:12.0 Signal processing controller: Intel Corporation Device 06f9 
00:14.0 USB controller: Intel Corporation Device 06ed
00:14.2 RAM memory: Intel Corporation Device 06ef
00:16.0 Communication controller: Intel Corporation Device 06e0
00:17.0 SATA controller: Intel Corporation Device 06d2
00:1b.0 PCI bridge: Intel Corporation Device 06c0 (rev f0)
00:1b.4 PCI bridge: Intel Corporation Device 06ac (rev f0)
00:1c.0 PCI bridge: Intel Corporation Device 06b8 (rev f0)
00:1c.4 PCI bridge: Intel Corporation Device 06bc (rev f0)
00:1d.0 PCI bridge: Intel Corporation Device 06b0 (rev f0)
00:1d.4 PCI bridge: Intel Corporation Device 06b4 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device 0685 
00:1f.3 Audio device: Intel Corporation Device 06c8
00:1f.4 SMBus: Intel Corporation Device 06a3
00:1f.5 Serial bus controller [0c80]: Intel Corporation Device 06a4 
00:1f.6 Ethernet controller: Intel Corporation Device 0d4d 

**arch**
x86_64

Any help would be greatly appreciated! Thanks in advance                 
[/INDENT]

---

### Post by TheFu on 2021-01-05
Support for 16.04 ends in 3 months. 
First thing you should do is stop and load 20.04 instead.

The output doesn't tell us which card the system has. Without that, nobody can help.  Use Windows to get the model, if necessary.

It doesn't work post-install, but does it work in a "try ubuntu" flash drive environment? Get 20.04, create a boot flash drive and see if 4 yrs newer fixed it.

Almost always, the correct drivers are included with the Linux kernel. The exceptions are usually due to bleeding edge hardware or odd versions like the entire "Killer" line of ethernet stuff.

---

### Post by theexpert1234 on 2021-01-05
Hi Thanks for your response,

I managed to check from  windows 10 , My Ethernet card has following name:

Name:  Intel(R) Ethernet Connection(11) 1219-V
Adaptor type:  Ethernet 802.3
Product Type: Intel(R) Ethernet Connection(11) 1219-V

> **TheFu said:**
> Support for 16.04 ends in 3 months. 
First thing you should do is stop and load 20.04 instead.

The output doesn't tell us which card the system has. Without that, nobody can help.  Use Windows to get the model, if necessary.

It doesn't work post-install, but does it work in a "try ubuntu" flash drive environment? Get 20.04, create a boot flash drive and see if 4 yrs newer fixed it.

Almost always, the correct drivers are included with the Linux kernel. The exceptions are usually due to bleeding edge hardware or odd versions like the entire "Killer" line of ethernet stuff.

---

### Post by chili555 on 2021-01-05
> Get 20.04, create a boot flash drive and see if 4 yrs newer fixed it.Plus One Thousand.

The aliases for the device appear in my 20.10 machine.

```

chili@T440p:~$ modinfo e1000e | grep 0D4D
alias:          pci:v00008086d0000[COLOR="#FF0000"]0D4D[/COLOR]sv*sd*bc*sc*i*
```I also recommend that you install, at least, Ubuntu 20.04 LTS and enjoy your ethernet connection.

---

### Post by grahammechanical on 2021-01-05
According to Intel.com the 1219-V was launched 2nd quarter 2015. I would hope that the Linux firmware (drivers) in Ubuntu 16.04.6 (Released February 2019) would include drivers for the 1219-V. In case it does not, I suggest using Windows to download and burn the Ubuntu 20.04 ISO image and run it as a live session and test to see if you get internet access through Ethernet.

It is possible to install Ubuntu without having an internet connection but it is much better to install with an internet connection. In that way the installer can download the latest system libraries (packages).

As pointed out above, 16.04 is soon to reach the end of its support life. You will need internet to upgrade to 18.04. The latest release of Ubuntu with Long Term Support (April 2025) is 20.04. If that has drivers for your ethernet it may be best to install 20.04.

Is there a particular reason you decided to install 16.04?

Regards

---

### Post by theexpert1234 on 2021-01-06
Thanks for your advice, Here I have a limitation of my software, that  require the libraries which are only available in ubuntu 16.04, plus I was recommended by software, to use the server edition. so I cannot go beyond that 16.04. from one of your recommendation I have used the live usb and found that somehow server editions are missing ether drivers ,while desktop edition of 16.04 can detect the network adaptor(thanks to the live usb option , saving time) . Now I am looking to use the desktop edition instead of server of 16.04, and if i am able to build , I will update it accordingly.Thanks.

---

### Post by TheFu on 2021-01-06
That doesn't change the fact that 16.04 support ends in a few months after 5 years.  If you must keep using it, don't put it on a network after April. There are likely to be existing remote access bugs, some don't need even a running listener, if history is any guide.

Get everyone using that software to work with the vendor/team to move to a supported release ASAP.  A few months for small projects isn't bad, but for large projects, it can take years.  But they will never know until all the dependencies are checked.  I ported software across platforms and OS versions for about a decade.  It can be pretty easy or very hard. Just depends on the software involved.

---

### Post by theexpert1234 on 2021-01-06
I have tested the ubuntu desktop version , but somehow its not booting up with the required software.

 Regarding ubuntu server 16.04.6 , I also tried to manually download and install the Ethernet drivers, but I got that error when I tried to compile the src folder of the driver it said, "make package is not installed " , and I have no idea how to install the make package without the internet connectivity . 

the commad "sudo make install"  is needed to execute the driver manually , if any idea how to install the make package offline?,  that  solution was given by this link.  

[https://askubuntu.com/questions/650953/intel-e1000e-ethernet-not-working](https://askubuntu.com/questions/650953/intel-e1000e-ethernet-not-working)

---

### Post by TheFu on 2021-01-06
The "Server" installer has limited drivers and usually doesn't include Bluetooth or wifi stuff. That's to be expected.
I'm always confused when the Desktop versions of any Ubuntu installation media has more network drivers than the installed Desktop does. That doesn't make sense, but still it seems to happen.

The difference between the "Server" and "Desktop" versions of Ubuntu are just in the pre-installed software packages. It is fine to add server packages to any Ubuntu desktop install. That is usually the way most people go.  Some people will install the "Server" version, then add a light desktop as well, but in doing that, all those little GUI tools expected as part of a desktop don't get installed.  Network configuration is handled by text config files, not a pretty GUI.

That's just the first of the dependency issues you will run into.  

There are likely many. 'make' is the software build controller, so it is likely you'll need a compiler, linker, perhaps object archive management, but any other 3rd party libraries. Without a network, I don't know how to get the stuff you need.

Google found these: [LIST]
[*][https://ostechnix.com/fully-update-upgrade-offline-debian-based-systems/](https://ostechnix.com/fully-update-upgrade-offline-debian-based-systems/)
[*][http://manpages.ubuntu.com/manpages/bionic/man8/apt-offline.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/apt-offline.8.html)
[/LIST]

Seems like what you need. I've never used it.

---

### Post by chili555 on 2021-01-06
> so it is likely you'll need a compiler, linker, perhaps object archive management, In other words, the package *build-essential* and its many dependencies, some 25 or so packages.

I have tried several times to compile Intel's source code but I havent succeeded for several years.

---

### Post by theexpert1234 on 2021-01-07
These are  good detailed tutorials regarding   apt-offline and other python scripts, I tried it, but being a beginner, I got stuck in the dependency issues.
Aas another attempt to get some sort of internet connectivity , I thought to use mobile tethering, while it automatically detects the usb interface in live usb, but on the offline system , the   "ifconfig -a" command only shows loopback interface , but no usb interface ,

my question would be that , can I use the same method like apt-offline or below method2  to make visible usb interface like ( enp0s29u1u3c4i2 ) in my ubuntu 16.04 " ifconfig -a " output ? 
then which package should I be looking for to install offline this usb interface?


Method 2 (example)

$ sudo apt-cache depends python
[I]**Sample output:**
 python
PreDepends: python-minimal
Depends: python2.7
Depends: libpython-stdlib
Conflicts: <python-central>
Breaks: update-manager-core
Suggests: python-doc
Suggests: python-tk
Replaces: python-dev


And then run:

$ for i in $(apt-cache depends python | grep -E 'Depends|Recommends|Suggests' | cut -d ':' -f 2,3 | sed -e s/'<'/''/ -e s/'>'/''/); do sudo apt-get download $i 2>>errors.txt; done



[/I]





> **TheFu said:**
> The "Server" installer has limited drivers and usually doesn't include Bluetooth or wifi stuff. That's to be expected.
I'm always confused when the Desktop versions of any Ubuntu installation media has more network drivers than the installed Desktop does. That doesn't make sense, but still it seems to happen.

The difference between the "Server" and "Desktop" versions of Ubuntu are just in the pre-installed software packages. It is fine to add server packages to any Ubuntu desktop install. That is usually the way most people go.  Some people will install the "Server" version, then add a light desktop as well, but in doing that, all those little GUI tools expected as part of a desktop don't get installed.  Network configuration is handled by text config files, not a pretty GUI.

That's just the first of the dependency issues you will run into.  

There are likely many. 'make' is the software build controller, so it is likely you'll need a compiler, linker, perhaps object archive management, but any other 3rd party libraries. Without a network, I don't know how to get the stuff you need.

Google found these:
[LIST]
[*][https://ostechnix.com/fully-update-upgrade-offline-debian-based-systems/](https://ostechnix.com/fully-update-upgrade-offline-debian-based-systems/) 
[*][http://manpages.ubuntu.com/manpages/bionic/man8/apt-offline.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/apt-offline.8.html) 
[/LIST]

Seems like what you need. I've never used it.

---

