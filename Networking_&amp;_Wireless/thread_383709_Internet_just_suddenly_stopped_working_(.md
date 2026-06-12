---
title: "Internet just suddenly stopped working :("
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by Metaleks on 2007-03-13
Hello there!

I just installed Ubuntu 6.10 yesterday and everything was just fine.  I was even surprised to find that even the internet was working.  I could surf the web, read email and lots of other good stuff.  I then downloaded the updates for Ubuntu restarted, and my internet still worked...

However, I turn on my computer this morning, and the internet doesn't work at all :-( I can't even connect.  I think eth0 is being recognized but I'm not sure.  I don't understand how it could just stop working when everything was just fine the day before.

Help would be appreciaited :) 

Thanks in advance

- Metaleks

---

### Post by Lord Illidan on 2007-03-13
First, it's not your internet...it is your connection to the internet :)

Can you ping sites from the terminal? Do they work?

---

### Post by Metaleks on 2007-03-13
You're going to have to forgive me ;)   I'm still learning proper terminology and getting used to Ubuntu.

I'm not a computer newbie, just a linux newbie.  Can you please describe how to ping via the terminal?  

Thanks :)

---

### Post by Lord Illidan on 2007-03-13
It isn't very different from the windows way.

Just open a terminal : Applications -> Accessories -> Terminal and type in:

ping google.com

and ping 72.14.207.99

---

### Post by Metaleks on 2007-03-13
```
ping google
ping: unknown host google.com
```

```
ping 72.14.207.99
connect: Network is unreachable
```

I am going to take a wild guess and say that I cannot ping.

---

### Post by madmaik on 2007-03-13
Hi,
my wife's got the same problem, according to the symptoms you describe but she's using kubuntu breezy.
After quite a while she installed a lot of updates, sunday (11-Mar-2007) all was fine, today the system alltogether behaves strange with the network-connection not working properly as the biggest issue.
We found so far, that the drops the default router entry from the netwerk settings when using the GUI. 
On the command line a
```
sudo route add default gw <IP_TO_ROUTER>
```
is doing the trick for us until the next reboot.

Any ideas how to solve this permanently?

rgds,
    Maik

---

### Post by Metaleks on 2007-03-13
Madmaik I tried your "solution" but that didn't work for me.  It seems that we have different issues together.  You should have created your own thread, but I don't see why we can't share one:)

---

### Post by Mr. C. on 2007-03-13
From a terminal window, enter the following and report back the results:
```

ifconfig -a
cat /etc/resolv.conf
```

MrC

---

### Post by Metaleks on 2007-03-14
I couldn't run the second command "cat /etc/resov.conf" but "ifconfig -a" worked.

**Output for ifconfig -a**

```
eth0        Link encap:Ethernet HWaddr 00:07:E9:AA:5F:92
              UP BROADCAST MULTICAST MTU:1500 Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

lo           Link encap:Local Loopback
             inet addr:127.0.0.1 Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
             UP LOOPBACK RUNNING MTU:16436 Metric:1
             RX packets:2 errors:0 dropped:0 overruns:0 frame:0
             TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:0
             RX bytes:100 (100.0 b) TX bytes:100 (100.0 b)


sit0        Link encap:IPv6-in-IPv4
            NOARP MTU:1480 Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

vmnet1 Link encap:Ethernet HWaddr 00:50:56:C0:00:01
           inet addr:172.16.78.1 Bcast:172.16.78.255 Mask:255.255.255.0
           inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)


vmnet8 Link encap:Ethernet HWaddr 00:50:56:C0:00:08
           inet addr:172.16.227.1 Bcast:172.16.227.255 Mask:255.255.255.0
           inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
```

Hmmm.

---

### Post by Mr. C. on 2007-03-14
Your eth0 interface is not up or working.

No need to do the /etc/resolv.conf (typo on my part), since your ethernet is not configured.

Try System->Administration->Networking and configure your eth0 network.  Use DHCP if you have a router to provide IP information.

If this doesn't work, look for any eth0 and related messages in output from dmesg.

See if this helps.
MrC

---

### Post by Metaleks on 2007-03-14
It's weird.  Because I could connect just fine before I rebooted my computer after the updates...  

Anyways.  I went to System > Administration > Networking and saw the Wired Connection checked, as it should be.  I then went into properties and it was enabled.  Also the configuration was already set to DHCP.  Yeah, I do have a router lol.

So I'm guessing everything looks just dandy from there.

I tried "dmesg" and got a few eth0 messages.  These were the only ones...

```
bridge-eth0: enabling the bridge
bridge-eth0: up
bridge-eth0: already up
bridge-eth0: attached

...

ADDRCONF(NETDEV_UP): eth0: link is not ready

...

e100: eth0: e100_probe: addr 0xfe1ff000, irq 209, MAC addr 00:07:E9:AA:5F:92
```

---

### Post by Mr. C. on 2007-03-14
Its not possible for me to know what order your dmesg's are in.  This ione is a sign of possible trouble, but maybe not:

ADDRCONF(NETDEV_UP): eth0: link is not ready

It looks like you have an Intel NIC: (e100_probe), but that's all I can tell from the output.

The other's are your virtual machines.  I have no idea how you have those setup.

If your eth0 config is not working, I'd start from the basics.  Shut down those VMs, and get your Ethernet working first.

With the VMs down, try disabling the network, and then re-enabling it.  Watch your dmesg output.

MrC

---

### Post by Metaleks on 2007-03-14
They appeared in that order.  The ... just represents that there are more messages in between.  But these are the only places where eth0 or eth are mentioned for that matter.

I actually have no idea what VM machines you seem to be talking about.  How do I shut down those VMs and do what you just said?  You'll have to forgive me, I'm still a linux newbie :(

---

### Post by Mr. C. on 2007-03-14
I  understand what the elipses are; however, dmesg is a ring buffer, and messages can wrap to the beginning, so order is ambiguous without the time stamps.  You can place the output of dmegs into a file, compress and attach it here:

```
dmesg > dmesg.out
gzip dmesg.out
```

These are your VMWare virtual machine interfaces:

vmnet1 Link encap:Ethernet HWaddr 00:50:56:C0:00:01
vmnet8 Link encap:Ethernet HWaddr 00:50:56:C0:00:08

You aren't aware of these?

MrC

---

### Post by Metaleks on 2007-03-14
No.  I told you...  I am a complete linux newbie.  This is my second day of ubuntu.  

But here are the time stamps:

```
[17179604.800000]bridge-eth0: enabling the bridge
[17179604.800000]bridge-eth0: up
[17179604.800000]bridge-eth0: already up
[17179604.800000]bridge-eth0: attached

...

[17179614.664000]ADDRCONF(NETDEV_UP): eth0: link is not ready

...

[17179589.724000]e100: eth0: e100_probe: addr 0xfe1ff000, irq 209, MAC addr 00:07:E9:AA:5F:92
```

EDIT:

Here is the entire dmesg output.

I really appreciate what you're doing MrC.  Thank you.  But I think I'm going to hit the haystack.  Thanks for everything you've done so far.

---

### Post by Mr. C. on 2007-03-14
Ok, well, I'm probably not going to be able to help on this one.  I don't know what type of installation this was, but there are several virtual machines running, and I'm not familiar enough with them to know how that was setup, or configured.  I believe the updates and the virtual machines are not playing nice together.  This is likely why the update cased failures.

Perhaps share with others how this installation was done.

Sorry,
MrC

---

### Post by madmaik on 2007-03-14
Hi Metaleks,
 
I do not know whether our problems might me related but I can try to help you anyway.
 
First: where and how did you install ubuntu? Where did the installation medium come from?
As MrC is confused about the virtual network devices on your system we need to know this.

Second: edit the file /etc/network/interfaces (might be called similar to this, I'm not at home currently) and type in there the following:
```

auto eth0
iface eth0 inet dhcp

```

If this won't work you may try providing a static address. 
```

auto eth0
iface eth0 inet static
        address <your computers IP address>
        netmask <your netmask>
        gateway <your routers IP address>

```

of course you will need to either re-enable the network interfaces by doing
```
/etc/init.d/networking restart
```


rgds,
   MaDMaik

---

### Post by Metaleks on 2007-03-14
I downloaded an ubuntu .iso from [here](http://www.ubuntu.com/products/GetUbuntu/download#currentrelease).

Also I installed it after opening up the install file that was located on my desktop, after I popped in the cd.  When it prompted me what kind of installation I wanted, I just chose to wipe everything and have a clean install on ubuntu on that one hard drive.  After installation the internet worked just fine.  Then, after the updates and a reboot, it just stopped working.

Also, restarting my network interfaces via

```
/etc/init.d/networking restart
```

did not work.  

I am at a complete loss.  I really don't understand what the problem could be...

---

### Post by Metaleks on 2007-03-14
Bump.

---

### Post by Mr. C. on 2007-03-14
> **Metaleks said:**
> Also I installed it after opening up the install file that was located on my desktop, after I popped in the cd.

It is this line that puzzles me.  This sounds like you installed Ubuntu, and then once booted and running Ubuntu, ran the installer again to install it into a vmware machine.  There are several releases available at the link you gave us - we don't know which version you installed, or which ISO was selected.

You DO have a virtual machine running.  You either have Ubuntu running in a virtual machine on Windows, or you have Ubuntu running on a virtual machine inside of Ubuntu.

If this is not what you desire, you will need to remove that virtual machine.  I'm can determine how your system was setup and installed.

It is very possible that kernel and core system software updates would have made one of those two installations inoperable.

I'd suggest first trying to determine how your systems are even running.

MrC

---

### Post by madmaik on 2007-03-15
> **Metaleks said:**
> 
Also, restarting my network interfaces via
```
/etc/init.d/networking restart
```
did not work.  


Sorry, my fault.
On Ubuntu you need to put the command **sudo** in front if you need to do anything that only an administrator can do. **sudo** allows you to execute a command as the superuser (-> root) and will ask you for your password.
So the complete line to restart your network interfaces is
```
sudo /etc/init.d/networking restart
```
 
By the way, I think MrC is correct in guessing that your Ubuntu runs on a virtual machine like VMWare. Question: if you reboot Ubuntu do you reboot your whole computer?
 
rgds,
   MaDMaik

---

### Post by AndyC_772 on 2007-03-15
I have a similar problem - everything was fine yesterday morning, came back in the evening to no wireless connection :(

I've tried uninstalling ndiswrapper (and ndiswrapper-utils-1.8) and wpasupplicant, temporarily disabling wireless security, and reinstalling according to the guide [here](http://www.ubuntuforums.org/showthread.php?t=340689) (but using same bcmwl5 drivers that I had before and which I know work). No joy.

Here are a few clues. dmesg output:

```
[17179599.172000] ndiswrapper version 1.34 loaded (preempt=no,smp=yes)
[17179599.284000] ndiswrapper: driver bcmwl5 (Linksys,07/17/2003, 3.30.15.0) loaded
[17179599.284000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179599.288000] ndiswrapper: using IRQ 11
[17179599.948000] wlan0: ethernet device 00:90:96:f2:52:79 using NDIS driver: bcmwl5, version: 0x50000, NDIS version: 0x500, vendor: '', 14E4:4320.5.conf
[17179599.952000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
.
.
[17179685.024000] NET: Registered protocol family 10
[17179685.024000] lo: Disabled Privacy Extensions
[17179685.024000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17179685.024000] IPv6 over IPv4 tunneling driver
[17179910.412000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179910.412000] eth1:  setting half-duplex.
[17179910.420000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179918.412000] eth1:  setting full-duplex.
[17179918.420000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17179929.300000] eth1: no IPv6 routers present

```
My /etc/network/interfaces file:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet static
address 192.168.1.203
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 192.168.1.1
wpa-driver wext
wpa-conf managed
wpa-ssid {my ssid}
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key_mgmt WPA-PSK
wpa-psk {my psk}
wireless-essid {my ssid}

iface eth1 inet static
address 192.168.1.203
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1

```

Since I don't currently have wpa_supplicant installed, I'm assuming that the wpa lines will be ignored.

Here's the output from iwconfig:
```
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:14 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

Most revealing, however, is the output from /etc/init.d/networking restart:

```
andy@andy-ubuntu-laptop:/etc/init.d$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
                                                                         [ ok ]
andy@andy-ubuntu-laptop:/etc/init.d$ 

```

...ie. no attempt to restart wlan0 (or eth1 for that matter, which is working fine).

Booting Ubuntu has also started taking a long time - a pause of a minute or so, during which the orange progress bar disappears and instead shows me the output from the fsck check on my hard discs. I presume this is simply the last thing that worked before trying to talk to the wireless LAN. I have several shares on a NAS drive which get mounted at start-up.

Any ideas please before I have to give up and reinstall from scratch? :(

---

### Post by AndyC_772 on 2007-03-15
UPD: Never mind, I rebooted my AP, set everything up again and now it seems fine. The clue was that Windows couldn't connect either.

Oddly, my Squeezebox continued to function OK despite being on the same AP, though...

---

