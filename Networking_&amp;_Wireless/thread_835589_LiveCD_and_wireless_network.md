---
title: "LiveCD and wireless network"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by frankhovin on 2008-06-20
First of all - I'm new to Ubuntu. I've been using Debian for quite a while, but since that's a huge pain when it comes to getting hardware newer than 5 years to work, I thought I'd give Ubuntu a try, since people say it's got the best hardware support.

My machine is a Lenovo T60 laptop, with an Intel PRO/Wireless 3945ABG Mini-PCI Express Adapter wlan card. I booted up Ubuntu (latest version) from the "LiveCD", without installing it, to test it. To my surprise, it found neither my wireless card NOR my network card. And when I tried to configure a wireless network connection anyway, it wouldn't even let me type in the SSID of the nework (just kept beeping). No available tools listed any network devices.

Is this a problem, or an impossibility, with the LiveCD, or must I conclude that Ubuntu, like most other Linux distros, are not to be trusted entirely when it comes to getting wlan to work? I checked on the list of compatible cards, and the 3945 adapter should be tested and working with older versions of Ubuntu. I got a mulitiboot with WinXP on the machine, just to be able to work from home, since wireless works with Windows. I cannot install ubuntu over any of the existing partitions unless I know for sure that wireless networking will work.

All input, answers and suggestions are appreciated.

---

### Post by gradedcheese on 2008-06-20
I have the same laptop and WLAN card, and it all works fine, including on the Live CD.

Do you have the RF kill switch set by accident?  That's the slider switch on the front left of the laptop.  

The Ethernet card sometimes won't work due to a bug related to checking an EEPROM checksum.  Newer versions of the driver work around this, you can also load and unload the driver to work around it. This is a pretty rare bug and I haven't seen it in a long time.

---

### Post by frankhovin on 2008-06-20
No, I'm using the Windows partition on the machine right now, so it's not the switch :-)

What's strange is that there doesn't seem to be any network drivers loaded when the LiveCD start.

---

### Post by frankhovin on 2008-06-20
I just tested the LiveCD again now. After it starts up the system, ifconfig and iwconfig shows no wlan or lan interface at all. There is a line about e1000 in dmesg, with a comment about loading failed on line 5. A modprobe of e1000 however, returns no error. I know the card is an Intel 3945, but there are no drivers loaded with a name resembling that.

So, no network drivers are loaded, and the machine works problem free with lan and wlan in Windows, and win lan in Debian. Ubuntu, however, fails to get either up.

Anything else I could/should try? Any other CD's, troubleshooting etc.?

---

### Post by frankhovin on 2008-06-20
Also, my WLAN here at home is WPA protected, but visible (SSID broadcast). It doesn't show when clicking the wlan icon in the top right corner, and (as mentioned) when trying to type something in the (b?)ssid field, it won't let me.

---

### Post by gradedcheese on 2008-06-21
That's strange.  To load the driver manually:

```

sudo modprobe iwl3945

```

Use 'ifconfig -a' to see all interfaces.  On my T60, this all works fine from the beginning, so I wonder what's different on yours.

---

### Post by frankhovin on 2008-06-21
This is getting both weird and downright silly.

When I load the wlan driver manually, with modprobe iwl3945, something happens allright. It loads the eth0 driver. So now I get access to the network card, and wired connection. The wireless card is still lost, however.

---

### Post by chili555 on 2008-06-21
> **frankhovin said:**
> This is getting both weird and downright silly.

When I load the wlan driver manually, with modprobe iwl3945, something happens allright. It loads the eth0 driver. So now I get access to the network card, and wired connection. The wireless card is still lost, however.Network Manager will not allow a wireless connection, if you have an active wired connection: [https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager](https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager) Especially see this:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managedSo, I'd boot up without the wire and:```
sudo modprobe iwl3945
```See if you can configure and connect your wireless.

I am answering this on my T60 using an Intel 3945ABG card. It works very well.

---

### Post by frankhovin on 2008-06-21
There is no cable plugged into the network card. What happens when I modprobe iwl3945 is that eth0 suddenly appears under ifconfig. The only wireless "card" visible under iwconfig is ir0. So, the problem is not that the network card "overrides" the wireless card.

---

### Post by frankhovin on 2008-06-21
Last update and most likely my goodbye to Ubuntu:

I put in an old pcmcia card, and booted up the LiveCD. This time the card was detected, and I was able to enter the configuration (SSID, WPA-key etc.). However, no matter how I configured it - DHCP or static (my router is set up with both), there was no way to get a connection to the internet (no route to host). I used the exact same configuration(s) as I use on my Debian laptop (not the one with the troubles), which works fine both with a wired network and wireless.

This is the kind of trouble I'd expect from a Gentoo installation, where you have to research every topic manually, and I'd be perfectly happy to spend the weekend getting something like that to work. But not in Ubuntu, which is said to be user-friendly and very easy to get working. Ubuntu has so far proved to be exactly the same kind of hassle as its parent, Debian.

---

### Post by gradedcheese on 2008-06-21
Are you sure that eth0 is the LAN and not the WLAN interface?  iwconfig will tell you.  I'd really love to see this laptop in person as I own two T60's with the same hardware and I know of three others using Hardy without a problem.  Everything works, Live CD and all.

Instead of giving up, let's troubleshoot this systematically.  Put the CD in, boot it up all the way, and let's see what gets modprobe'd.  Please open a terminal, before doing anything, and run:

```

lsmod | grep e1000
lsmod | grep iwl
ifconfig -a

```

...and post the results (or a summary) here.

---

### Post by frankhovin on 2008-06-22
lsmod |grep e1000:
```

e1000            125760        0

```
lsmod |grep iwl:
```

nothing

```
ifconfig -a:
```

eth0      Link encap:Ethernet  HWaddr 00:15:58:c5:46:f6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x3000 Memory:ee000000-ee020000 

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10044 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10044 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:502200 (490.4 KB)  TX bytes:502200 (490.4 KB)



```

---

