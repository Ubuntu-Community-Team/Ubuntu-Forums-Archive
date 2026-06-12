---
title: "Ubuntu 16.10  wireless not working"
date: 2017-06-15
forum: Networking &amp; Wireless
---

### Post by pid1 on 2017-06-15
Ubuntu 16.10 / Grub2 bootloader issue:

I was given a nice older custom desktop pc with Windows 7 installed.

I added Ubuntu 16.10 from a usb optical drive.

It can now boot to either operating system.

Windows can access the internet, and Ubuntu cannot, while running on the same hardware.

In troubleshooting that problem, the wifi card vendor asked me to reinstall Ubuntu, and I find that I am unable to do that.

Grub2 will let me get to Windows or Ubuntu, but will not let me boot from a cd, or usb stick, as I get to the grub menu first.

I have tried (probably) every setting of boot order available in bios to no avail:

I can&#8217;t seem to get around the bootloader.

There is a grub config utility under Windows, but I have not been successful in getting that to help.

Again; I can not get the Ubuntu side of the machine online to update, or to add a boot repair utility.

Possible fixes to the problem found on the web all assume that I can boot from removable media, or that I can access the web from the problem computer, so don&#8217;t seem to get me any help.

Thanks for any help with this.

---

### Post by oldfred on 2017-06-16
Moved to networking & Wireless sub-forum so those that know those issues can help.

Can you connect using hardwire connection. There are so many wireless that live installer often does not have everyone, and can download correct one if using Ethernet hardwired connection which in most cases does work.

See also sticky threads at top of networking & Wireless sub-forum.
You should still be able to run the wireless script as suggested, but then copy to flash drive and upload from another system.
What brand/model Wireless chip do you have.

After you get wireless or Internet working post a new thread on grub or boot issues.

---

### Post by pid1 on 2017-06-16
OK, just remember that I'm new.

So I didn't think to add to the first post that a hard wired network is not available.

I would use that in preference to wireless, if it was an option.

Also, there is no unsecured wifi within range of the adapter.

Note that my wireless adapter was not present when Ubuntu 16.10 was installed.

After installing Ubuntu, I tried another adapter with no success. When it became obvious that they had zero tech support, I replaced it with the current one:

Panda Wireless N600 (nothing included with it specifies a chipset)

The Panda adapter works when I boot the computer to Windows 7. That is, I can connect to the internet using the same hardware if I boot Windows.

So, again, I had another adapter in the machine before this one, but after the original Ubuntu 16.10 install.

I can imagine that that might be at least partly to blame.

When I go to the wifi networks icon on the upper right of my screen, it shows that the Panda adapter is connected to my wifi hotspot.

I can not, however, connect to the internet.

Firefox says, "Server not found."

Ping Google.com says, "ping: google.com: Name or service not known."

Ping 8.8.8.8 says, "connect: Network is unreachable."

If there is no other solution, I could possibly carry the computer to work and hardwire it there, but I would rather avoid that option for a variety of reasons.

I will look through the sticky threads and see if they offer an answer.

lsusb tells us that the adapter is a Ralink Technology Corp. RT5572 wireless adapter

Thanks

---

### Post by Hadaka on 2017-06-16
Hi, Ubuntu 16.10 end of life is July 2017..next month.
Ubuntu 16.04 LTS would be a better choice end of life is April 2021.
Meantime please post the output of..
```
 lspci -n | awk '/0280/{print$3}'
```
Thanks.

---

### Post by oldfred on 2017-06-16
I have mostly wired connections and have not followed issues on wireless.
Until someone who knows a bit more comes along you can look at this thread which may have some more info.
[https://ubuntuforums.org/showthread.php?t=2137428](https://ubuntuforums.org/showthread.php?t=2137428)

---

### Post by pid1 on 2017-06-16
Hadaka, is this what you are after?

:~$ lspci -n 
00:00.0 0600: 8086:2e20 (rev 03)
00:01.0 0604: 8086:2e21 (rev 03)
00:1a.0 0c03: 8086:3a37
00:1a.1 0c03: 8086:3a38
00:1a.2 0c03: 8086:3a39
00:1a.7 0c03: 8086:3a3c
00:1b.0 0403: 8086:3a3e
00:1c.0 0604: 8086:3a40
00:1c.3 0604: 8086:3a46
00:1d.0 0c03: 8086:3a34
00:1d.1 0c03: 8086:3a35
00:1d.2 0c03: 8086:3a36
00:1d.7 0c03: 8086:3a3a
00:1e.0 0604: 8086:244e (rev 90)
00:1f.0 0601: 8086:3a16
00:1f.2 0101: 8086:3a20
00:1f.3 0c05: 8086:3a30
00:1f.5 0101: 8086:3a26
01:00.0 0300: 10de:05e6 (rev a1)
03:00.0 0106: 197b:2363 (rev 02)
03:00.1 0101: 197b:2363 (rev 02)
04:07.0 0c00: 104c:8024

I originally posted in the newbie section, because, well, I am one, so forgive me if I don't understand your request.

lspci -n gives the above output on the terminal screen.

If I type your command exactly, terminal shows me nothing, which is possible if awk is quietly creating a file somewhere, but I don't find anything with the string "0280" (which I would assume would be a directory) and I can't guess what the filename might be.

Simply typing "lspci" in terminal shows me a bunch of stuff, none of which appears to me to be related to my previously installed (& now gone) Broadcom pci adapter.

The current adapter is a Panda N600 usb adapter.

Thanks, and thanks for the heads up on Ubuntu version. I'll certainly update when I am able to do so.

---

### Post by pid1 on 2017-06-16
oldfred,

In the link you posted, the op eventually gives up on Ubuntu and goes back to Windows!

I hope with your collective help I won't have to do that.

---

### Post by Hadaka on 2017-06-16
Hi, the command..
```
lspci -n | awk '/0280/{print$3}'
```
means display the output of  lspci -n and then search for line that
has 0280 and print the 3rd field of the output.  Obviously you have
no internal wifi card ...line 0280. The panda is a usb so lets see the output of
```
lsusb
rfkill list all
```
thanks.

---

### Post by pid1 on 2017-06-17
Hadaka,

vincent@Vincent:~$ lsusb
Bus 002 Device 004: ID 148f:5572 Ralink Technology, Corp. RT5572 Wireless Adapter
Bus 002 Device 002: ID 18a5:0302 Verbatim, Ltd Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 045e:07b2 Microsoft Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
vincent@Vincent:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
vincent@Vincent:~$

---

### Post by Hadaka on 2017-06-17
Hi, Please open a terminal and do..
Enter one line at a time EXACTLY as written.
*Ignore any error or file not found..do every line.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -rf rt2800usb
sudo modprobe -v rt2800usb
```
boot and test wireless
Did that make a difference ?

---

### Post by pid1 on 2017-06-17
Hadaka,

```
vincent@Vincent:~$ sudo apt-get remove --purge bcmwl-kernel-source 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  guile-2.0-libs libgc1c2
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
vincent@Vincent:~$ sudo modprobe -rf rt2800usb
vincent@Vincent:~$ sudo modprobe -v rt2800usb
insmod /lib/modules/4.8.0-22-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.8.0-22-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko 
insmod /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko 
insmod /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00usb.ko 
insmod /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800usb.ko 
vincent@Vincent:~$ 

```

Did a reboot here with results as reported before: Firefox can't see internet, & ping doesn't work.

Thank you for your patience.

---

### Post by Hadaka on 2017-06-17
Hi, please do..

```
sudo apt autoremove
cat /etc/resolv.conf
cat /etc/network/interfaces
```
Then do..
```
ping -c2 $(route -n | awk 'FNR==3{print$2}')
ping -c2 localhost
ping -c2 google.com
ping -c2 8.8.8.8
```
Thanks.

---

### Post by pid1 on 2017-06-17
Hadaka,

```
~$ sudo apt autoremove
[sudo] password for vincent: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  guile-2.0-libs libgc1c2
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 12.1 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 164659 files and directories currently installed.)
Removing guile-2.0-libs:amd64 (2.0.11+1-12build2) ...
Removing libgc1c2:amd64 (1:7.4.2-8) ...
Processing triggers for libc-bin (2.24-3ubuntu1) ...
vincent@Vincent:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.53
vincent@Vincent:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
vincent@Vincent:~$ 
vincent@Vincent:~$ ping -c2 $(route -n | awk 'FNR==3{print$2}')
PING 0.0.0.0 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.032 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.015 ms


--- 0.0.0.0 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1027ms
rtt min/avg/max/mdev = 0.015/0.023/0.032/0.009 ms
vincent@Vincent:~$ ping -c2 localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.040 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.024 ms


--- localhost ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1017ms
rtt min/avg/max/mdev = 0.024/0.032/0.040/0.008 ms
vincent@Vincent:~$ ping -c2 google.com
ping: google.com: Name or service not known
vincent@Vincent:~$ ping -c2 8.8.8.8
connect: Network is unreachable

```

I can ping the namserver's ip address successfully. 
I had suspected that I didn't have a namserver. 
(I'm assuming that it's not local to my machine.)

---

### Post by Hadaka on 2017-06-17
Please post the output of..
```
route -n
ifconfig
iwconfig
```
Thanks

---

### Post by pid1 on 2017-06-17
```
vincent@Vincent:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.0.0       0.0.0.0         255.255.255.0   U     600    0        0 wlx9cefd5ffc952
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlx9cefd5ffc952
vincent@Vincent:~$ ifconfig
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 27630  bytes 1658334 (1.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 27630  bytes 1658334 (1.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlx9cefd5ffc952: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.42.0.1  netmask 255.255.255.0  broadcast 10.42.0.255
        inet6 fe80::9eef:d5ff:feff:c952  prefixlen 64  scopeid 0x20<link>
        ether 9c:ef:d5:ff:c9:52  txqueuelen 1000  (Ethernet)
        RX packets 71  bytes 19456 (19.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 180  bytes 27833 (27.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


vincent@Vincent:~$ iwconfig
wlx9cefd5ffc952  IEEE 802.11  ESSID:"viral"  
          Mode:Managed  Frequency:5.825 GHz  Access Point: 64:BC:0C:4A:F8:02   
          Bit Rate=39 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:102   Missed beacon:0


lo        no wireless extensions.


vincent@Vincent:~$ 

```

---

### Post by Hadaka on 2017-06-17
Hi, without having any kind of internet access, there are just too many
possibilities to determine exactly what is contributing to the failure and
ability to access the internet. the routing and nameserver dont make any sense.
add to that the Ubuntu 16.10 you loaded, is no longer supported in 2 weeks. I am
out of ideas as to what can be done, with the exception of suggesting you get access
to a valid router,delete the partition that ubuntu 16.10 is on and install Ubuntu 16.04 LTS
from a working wired connection. Good luck to you, sorry i was not able to help you.

---

### Post by pid1 on 2017-06-17
No, this was a help.

I know for a reasonable certainty that I haven't missed something obvious in setting this up.

You've gone way out of your way to help, and I appreciate that a lot.

Thanks.

Let me know where to send the pizza...

---

### Post by oldfred on 2017-06-17
Have not had to manually configure Internet for years. And mostly use wired.

What brand router?
But gateway is usually .1? Various routers have started DHCP at 100 and others at 2.
Are you using DHCP?


Have you compared ipconfig in Windows to ifconfig in Ubuntu?
Not sure anymore what parameters may be needed, if any.

---

### Post by wildmanne39 on 2017-06-18
Please do"
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Then:
```
echo "options rt2800pci nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
Posts any errors, if none reboot.

---

### Post by pid1 on 2017-06-18
```
vincent@Vincent:~$ sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
vincent@Vincent:~$ echo "options rt2800pci nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
options rt2800pci nohwcrypt=y
vincent@Vincent:~$ sudo modprobe -rfv rt2800pci
vincent@Vincent:~$ sudo modprobe -v rt2800pci
insmod /lib/modules/4.8.0-22-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko 
insmod /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko 
insmod /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko 
insmod /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko nohwcrypt=y 
vincent@Vincent:~$

```

So internet still doesn't work, with symptoms the same as above: Firefox can't find anything, can't ping Google, etc.

---

### Post by wildmanne39 on 2017-06-18
To be able to help you we need to see the output of the wireless script in my signature, just click on it and follow the directions for running it without internet connection unless you can use your cell phone as a tether and access the internet that way.

I do agree with Hadaka that you should switch to a supported version of Ubuntu since the support on 16.10 is ending.

Thanks

---

### Post by pid1 on 2017-06-18
```


########## wireless info START ##########



```

[COLOR=#000000]wildmanne39, [/COLOR]I assume that the above is not what your were looking to get as a result of running your wireless script.

I will be happy to move to a supported version of Ubuntu once this (and my bootloader problem) get ironed out.

I will ask my employer tomorrow if he will let me carry the whole kit and caboodle to work, and connect it to his network to (hopefully) fix the various problems. Note that I have a bootloader problem as well, or I would just wipe this install out and start over.

Thanks

---

### Post by Hadaka on 2017-06-18
Let's try something from a different angle.
Boot to windows...click start >>run   Type   cmd  and press return
you should now have a command prompt and window.
enter....ipconfig   in that window and post the results.
Type exit to leave the command window and prompt.
Thanks.

---

### Post by pid1 on 2017-06-18
Yes, oldfred suggested that earlier as well.

I'll give it a go tomorrow (Monday).

---

### Post by wildmanne39 on 2017-06-18
> **pid1 said:**
> ```


########## wireless info START ##########



```

[COLOR=#000000]wildmanne39, [/COLOR]I assume that the above is not what your were looking to get as a result of running your wireless script.

I will be happy to move to a supported version of Ubuntu once this (and my bootloader problem) get ironed out.

I will ask my employer tomorrow if he will let me carry the whole kit and caboodle to work, and connect it to his network to (hopefully) fix the various problems. Note that I have a bootloader problem as well, or I would just wipe this install out and start over.

ThanksThat is the top of the script output there should have been a lot more, but I will back out and let Hadaka continue with is train of thought.

---

### Post by pid1 on 2017-06-18
I realize there should be more, but that's what I got.

Will try ipconfig from Windows tomorrow.

If it's not clear, the computer in question is not at my home, hence the delay in trying your suggestions.

---

### Post by pid1 on 2017-06-19
```


C:\Users>ipconfig


Windows IP Configuration




Wireless LAN adapter Wireless Network Connection 3:


   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::d0e7:43f7:9210:c60%18
   IPv4 Address. . . . . . . . . . . : 192.168.43.226
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.43.1


Tunnel adapter isatap.hvc.rr.com:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :


Tunnel adapter isatap.{E9236E39-3083-444B-B2FA-0E9D287A4B6F}:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :


Tunnel adapter Teredo Tunneling Pseudo-Interface:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :


C:\Users>ping google.com


Pinging google.com [172.217.10.238] with 32 bytes of data:
Reply from 172.217.10.238: bytes=32 time=121ms TTL=53
Reply from 172.217.10.238: bytes=32 time=126ms TTL=53
Reply from 172.217.10.238: bytes=32 time=61ms TTL=53
Reply from 172.217.10.238: bytes=32 time=88ms TTL=53


Ping statistics for 172.217.10.238:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 61ms, Maximum = 126ms, Average = 99ms


C:\Users>

```

If you need to see this as a screen grab, I can upload a picture of it.

---

### Post by Hadaka on 2017-06-19
Hi, this windows output is the EXACT same router that you are attempting to
make a Ubuntu connection with ?????   CORRECT ???
Thanks.

---

### Post by pid1 on 2017-06-19
Yes.

I'm using a Google / LG Nexus phone as a hotspot.

The same phone is used for both Windows 7 and Ubuntu 16.10 (with no changes to the phone in between).

(And I'm at work already, so I can't check anything else on that computer until tonight.)

---

### Post by Hadaka on 2017-06-19
Hi, I did not know 100% that you were using a "hot spot" although the 10.x.x.x address
made that a possibility. This statement. "I'm using a Google / LG Nexus phone as a hotspot."
verifies that. I know nothing about "hot spot" and will be unable to help you further.

Your MBR..master boot record with windows likely got corrupted when you attempted to load Ubuntu 16.10
and were unable to  do updates due to the failed connection and configuration, along with failed user implementation
of correct dual boot installation. Perhaps getting assistance in correcting the Windows MBR or inability to specify the selected
device for booting would be of benefit to you.
Hadaka.

---

### Post by pid1 on 2017-06-19
Thanks.

What might be easiest to do would be to remove Ubuntu from Windows side, then install 16.04.

---

### Post by jeremy31 on 2017-06-20
Can you tether to the phone using the USB cable in Ubuntu?
You may be able to install 16.04 over 16.10 in the same partition, is there an option for replace Ubuntu with Ubuntu during an install attempt?

---

