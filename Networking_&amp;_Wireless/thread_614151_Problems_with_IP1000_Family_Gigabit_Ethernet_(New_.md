---
title: "Problems with IP1000 Family Gigabit Ethernet (New User)"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by bigunit3000 on 2007-11-15
Hi, this is my first time running Linux.  After a couple of hitches (problems with ATI display driver on Live CD) I was able to install Gutsy Gibbon onto my hard drive.  (The amd64 one, if it matters.)  I was originally dismayed when I was unable to get an internet connection going, but I accessed nm-applet and changed my wired connection to disable roaming mode, and instead Enable DHCP.  This seemed to do the trick -- I booted up Firefox and like magic, I was able to surf the web.  Similarly, I was able to connect to AIM with Pidgin.

Then, I tried downloading new programs, using Add/Remove Applications from the top menu bar.  It claimed that I had no working internet connection.  This rears its ugly head in a few other places, too.  nm-applet, even though I have enabled DHCP, claims that I have "No network connection."  Also, when trying to download MP3 codecs for Totem Movie Player, it says the list of applications is unavailable, and that I had no internet connection.

Bummer.

The solution is probably staring me right in the face, but I would appreciate it if someone could lend me a hand.  If it helps, here are some of the outputs from network related commands that other threads have suggested to run.

sudo ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:50:8D:D3:BD:41  
          inet addr:129.2.250.146  Bcast:129.2.250.255  Mask:255.255.255.128
          inet6 addr: fe80::250:8dff:fed3:bd41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:281859 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12242 errors:2538 dropped:0 overruns:0 carrier:10
          collisions:1819 txqueuelen:1000 
          RX bytes:50537265 (48.1 MB)  TX bytes:1619320 (1.5 MB)
          Interrupt:22 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14600 (14.2 KB)  TX bytes:14600 (14.2 KB)

sudo lshw -C network:
>   *-network               
       description: Ethernet controller
       product: IP1000 Family Gigabit Ethernet
       vendor: Sundance Technology Inc / IC Plus Corp
       physical id: e
       bus info: pci@0000:00:0e.0
       version: 41
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Sundance Technology IPG Triple-Speed Ethernet latency=32 maxlatency=10 mingnt=80 module=ipg
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 00:50:8d:d3:bd:41
       capabilities: ethernet physical
       configuration: broadcast=yes ip=129.2.250.146 multicast=yes

Thanks in advance for any help you might be able to give me!

---

