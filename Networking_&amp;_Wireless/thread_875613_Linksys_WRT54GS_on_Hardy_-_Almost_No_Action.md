---
title: "Linksys WRT54GS on Hardy - Almost No Action"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by raywood on 2008-07-31
Linksys setup instructions for a WinXP installation advise going to the router at 192.168.1.1 and changing that to 192.168.2.1.  I did that in Firefox on Ubuntu and got an indication that the process was successful.  But the screen seemed to freeze at that point, and refreshing gave me an "Unable to connect."  Another computer running Ubuntu has the same experience.  I can connect directly to the Internet using either machine, but nothing happens with connections through the router.  It's a new router.  I bought it because the previous one, a WRT54GL, was suddenly having this same problem, after weeks of successful connections.

---

### Post by tamoneya on 2008-07-31
there is really no need to go to 192.168.2.1 unless you have some weird network.  Anyways try reseting it to defaults so you can get back into the configuration screen.  Hold the reset button in for 15 seconds or so.  I actually pull the power out while holding it and plug it back in while I am still holding it down.  That should clear out any problems in the router.

---

### Post by raywood on 2008-07-31
For some reason, they have you reset it to 192.168.2.1 when you go through the automated tech support guide at Linksys (800-326-7114).  Your reset instructions and/or their guide enabled me to go online through my secondary computer.  I can't say which did it exactly; I was focused on the primary computer at the time.  The primary computer still can't go online through the router, but is able to do so when I connect the computer directly to the modem.

Using Ubuntu's Network Tools, Ping is successful to 192.168.2.1, but nowhere else.  Using Netstat, I see interfaces with vmnet8, eth0, and lo.  I remember seeing a report, somewhere along the way, to the effect that vmnet8 doesn't exist.  I think I created it in the configuration process by mistake.  Could that be interfering somehow?

<a couple of hours pass>

I have now rebooted into Windows XP, on the dual-booting primary computer, and have finished installing its drivers.  WinXP is able to go online through the router.  I reboot into Ubuntu and it, too, is now online.  A mystery.  Did rebooting do it?  Did it help to have Windows lead the way?

---

### Post by tamoneya on 2008-07-31
im pretty certain that windows wouldnt have fixed anything.  It was more likely the restart of the router or the restart of the computer/network module.

---

### Post by raywood on 2008-08-04
You're right.  The problem is back, and a reboot into Windows and back into Ubuntu has solved nothing.

It doesn't seem to be the router.  I have two computers connected to it, and the one on which I'm typing these words is connecting without a problem -- except that I just got "The page isn't redirecting properly" when I tried to connect to a VMware forum.

On the other computer, I was able to go online when I booted into Windows.  I just can't go online when I'm in Ubuntu.

I was trying to get to a VMware forum because there is something I don't understand.  When I go into Ubuntu's System > Administration > Network Tools > Devices, I see four network devices:  Loopback Interface (lo), Ethernet Interface (eth0), Unknown Interface (vmnet1), and Unknown Interface (vmnet8).  Could the problem be in those two unknown interfaces?

---

### Post by PinkFloyd102489 on 2008-08-04
I dont see why anyone changes it at all anyway, unless you've got several routers on several subnets. I just left mine at 1.1 and my computers increment from there.

---

### Post by raywood on 2008-08-04
Not sure why vmnet-eight got converted into a smiley face in the previous post.  I guess the computer thought I was funny.

But anyway, does anyone have a theory on this connection problem?

---

### Post by caljohnsmith on 2008-08-04
I'm not sure if I'm understanding correctly your problem, but if you do
```
john@TECH5321:~$ [COLOR="Blue"]route -n[/COLOR]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         [COLOR="Blue"]192.168.1.1[/COLOR]     0.0.0.0         UG    100    0        0 wlan0
```
That 192.168.1.1 should be 192.168.2.1 for you, if that is the address of your router now. If it isn't, then you need to set up your gateway correctly; one way you can do this is just by setting up a static IP in Network Manager (vs DHCP), and then you can manually set your gateway address. 

Or maybe I'm totally off-base here and have misunderstood your problem. ;)

---

### Post by raywood on 2008-08-04
Thanks for that.  Here's what I get:

192.168.2.0   0.0.0.0   255.255.255.0  . . . vmnet8
192.168.2.0   0.0.0.0   255.255.255.0  . . . eth0
172.16.237.0  0.0.0.0   255.255.255.0  . . . vmnet1
169.254.0.0   0.0.0.0   255.255.0.0    . . . eth0

The ellipses (. . .) replace Flags (all U), Metric (all 0 except the last is 1000), Ref (all 0), and Use (all 0) columns.

---

### Post by caljohnsmith on 2008-08-04
So which is your wireless interface? If I understood you correctly from before, you had your wireless working, but then you changed your router's address to 192.168.2.1 and now its not working? Is that right? 

Please copy and paste the output of the following commands:
```
ifconfig
iwconfig
route -n
```

---

### Post by raywood on 2008-08-04
OK, here it is:

ray@P4-VM:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:9a:ff:5f  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe9a:ff5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1010 (1010.0 B)  TX bytes:3483 (3.4 KB)
          Interrupt:254 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1910 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80220 (78.3 KB)  TX bytes:80220 (78.3 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.237.1  Bcast:172.16.237.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2875 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ray@P4-VM:~$ 
ray@P4-VM:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

ray@P4-VM:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
172.16.237.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
ray@P4-VM:~$ 

Both computers are connected to the router via Ethernet cable.  I'm not using any wireless connections.

---

### Post by caljohnsmith on 2008-08-04
Do you have Ubuntu installed under VMware? Or is Ubuntu installed to its own partition? 

If you have a normal Ubuntu install (partition), then I think your routing table is really messed up at this point. It doesn't even show a gateway for your eth0 interface (just 0.0.0.0). But if you are using VMware, then I don't think I can help you, because I'm not sure what your routing table should look like under VMware. :)

Just to clarify, were you able to use the internet fine in Ubuntu until you changed the router's address? Or were you only able to communicate with the router?

---

### Post by raywood on 2008-08-04
Wow.  Fast replies.  I appreciate that.

I have 64-bit Ubuntu installed on a dual-boot system with WinXP.  What we're talking about here is the Ubuntu installation with VMware installed on top of it.  I'm running WinXP in a virtual machine in VMware.

Each operating system is on its own physical drive.  I have drive C and other Windows partitions on one hard drive, and I have / and swap for Ubuntu on another hard drive.

I had previously had some of the same problems, but then it had magically started working.  I was able to go online with all installations:  with dual-booted WinXP, with WinXP in the virtual machine, and with dual-booted Ubuntu.  Then it just stopped.  Now it has magically stopped.  But only in Ubuntu and in the WinXP virtual machine.  I can still go online in the WinXP dual boot.

---

### Post by caljohnsmith on 2008-08-04
Ok, how about going into network manager, make sure *only* your eth0 interface is enabled, set eth0 up with a static IP address (instead of DHCP), and then also specify your gateway as 192.168.2.1. That might give us a clue what is going on. Try pinging your router and checking the routing table to make sure you really are using 192.168.2.1 as your gateway after setting things up in network manager. 

Also, are you running VMware while trying these things in Ubuntu? It would help to keep VMware closed down to make sure it is not interfering at this point.

---

### Post by raywood on 2008-08-04
I went into Ubuntu's System > Administration > Network.  This opened a Network Settings dialog.  On the Connections tab, I clicked Unlock and then Wired Connection and then properties.  "Enable roaming mode" was selected and everything else there was grayed out.

I unselected "Enable roaming mode" and set Configuration to DHCP.  That gave me a "Changing interface connection" box.  When that box was gone, I tried but failed to go online, using Firefox in Ubuntu (i.e., not inside VMware).  I went back and changed it from DHCP to Static IP Address, and typed in 192.168.2.1 for IP address.  I clicked on the Subnet Mask box, and it defaulted to 255.255.255.0.  I typed 192.168.2.1 in the Gateway Address box.  I realized the IP address probably had to be something different, so I went back and changed that to 192.168.2.100, since that was what I was seeing for Ethernet Interface (eth0) in Ubuntu's System > Administration > Network Tools > Devices > Network Device.  I clicked OK.  Again I got the "Changing interface connection" box.  I tried again to go online.  Still no luck.

I took all these steps with VMware still running, because unfortunately I have a process underway there that I can't interrupt.  I will try again with VMware shut down, later tonight or tomorrow.  In the meantime, if I have gone astray on any of the foregoing steps, kindly set me straight.  Thanks again for your help.

---

### Post by raywood on 2008-08-05
I left the settings on Static, as described above, and closed down VMware.  I let the machine sit overnight, turned on, and tried going online again this morning.  No problem!

Network Tools, at this point, shows three of the four devices listed previously:

Loopback Interface (lo)
Ethernet Interface (eth0)
Unknown Interface (vmnet1)

My vague impression is that the vmnet8 device was the result of a mistake I made during installation.  

If I start up VMware, and do nothing more, there are still only the three items listed above, and I am still able to browse online.  If I power on a virtual machine in VMware, same thing:  still good.  If I start up Internet Explorer in that WinXP virtual machine, I am able to go line that way too, and there are still just those same three items listed in Network Tools.

If I change Network Settings to DHCP, Network Tools still shows those three items.  I am still able to browse online using Internet Explorer within the virtual machine, and likewise in Firefox in Ubuntu.

It seems the problem may arise when something causes that fourth item, vmnet8, to come to life.  I may be happier without it.  Is it possible to locate and eliminate it?

---

### Post by caljohnsmith on 2008-08-05
That's great news you have it working. I was definitely suspicious that VMware was involved. :)
> **raywood said:**
> It seems the problem may arise when something causes that fourth item, vmnet8, to come to life.  I may be happier without it.  Is it possible to locate and eliminate it?
As I mentioned before, unfortunately I can't help you with your VMware problem of creating new network interfaces because I don't use VMware. I'm sure there is a manual way of deleting that network interface within the right configuration file(s) in Ubuntu, but that probably won't prevent VMware from creating it again. Really you should try to figure out under what conditions VMware creates that additional interface.

But at least you have the problem narrowed down now, so if you have any similar problems in the future, you will know the likely culprit (VMware) and have a good idea how to troubleshoot it. :)

---

### Post by Scubamom on 2010-11-30
:confused:
I hope you all don't mind I read what every one said but I need the ABC's of it all. At this point I figure that I don't need the CD that comes with the router. Right?
So how do I install it? I am not using windows at all. SO do I just install the device and pray? Can some one tell me where to find this info?
Thank you

---

