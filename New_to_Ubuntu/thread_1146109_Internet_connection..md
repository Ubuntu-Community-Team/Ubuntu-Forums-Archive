---
title: "Internet connection."
date: 2009-05-02
forum: New to Ubuntu
---

### Post by stoat09 on 2009-05-02
Hi, I've loaded Ubuntu 8.10 onto a new PC as the sole O/S but cannot connect to my cable broadband, via the ethernet connection, which works fine on my old (Wind**s) machine. The socket seems 'live' as it lights up when connected - steady green on right but no orange on left. Tried to 'ping' my other PC, but nothing. Any ideas for a relative PC simpleton? Thanks.
Chris.

---

### Post by mikewhatever on 2009-05-02
Please post the outputs of the following commands:
ifconfig
cat /etc/network/interfaces

Can you go to google.com by entering 74.125.45.100 in the address bar?

---

### Post by stoat09 on 2009-05-02
cat/etc/network/interfaces:- "no such file or  directory"
74.125.45.100:- "connection refused", "unable to establish a contact"
'ifconfig' gives me a result but I am at a loss as how to post it here without typing it in full. Are there any 'important' bits I could type here for you? Many thanks.
Chris.

---

### Post by unutbu on 2009-05-02
Do you have a USB flash drive? If so, we could show you some commands to save the output on to the flash drive. Then you could tote the flash drive to a computer with internet...

---

### Post by cariboo on 2009-05-02
If you have a usb thumb drive, you can save yourself a lot of typing by piping the output of a command to a text file eg:

```
cat /etc/network/interfaces > interfaces.txt
```

You can then transfer the text file to your computer with an internet connection and post the results.

You made a typing error when runnung the first command that mikewhatever asked for, there should be a space between cat and /etc.

---

### Post by Butthead on 2009-05-02
Face it gentlemen, something is screwy lately with networkmanager. :( 

Was there an upgrade to it recently that I don't remember installing? :confused:

---

### Post by SnaveDogg on 2009-05-02
I had the same problem for about a week, until I took the computer to a guy who was very knowledgeable about BIOS settings, and Ubuntu in general. He found that in the BIOS settings of my computer, it Operating System was set to: WIN98. He changed that setting to "OTHER" and everything started working. Before that, nothing on the PCI bus was enabled. My ethernet card was connected to the PCI bus, and was being recognized as installed, but couldn't be used by the system, until the OS setting was changed to OTHER.

Ya might want to see if your ethernet card (if that is what you are using for internet) is on, being recognized by the OS and is enabled.

After that was done, we made sure in the Network settings that it was set to DCHP so it would automatically search for the IP address from the DSL modem we are using.

It all works now.

Keep in mind, my distribution of the OS is Xubuntu, not Ubuntu.

Hope this helps.

---

### Post by stoat09 on 2009-05-02
cat /etc now gives me:-
auto lo
iface lo inet loopback

I now have the results of "ifconfig" as a .txt file on this PC with internet access but  cannot manage to insert it into a posting. Can someone help with this please? Thanks.
Chris.

---

### Post by unutbu on 2009-05-02
When you click replay, look below the "Submit Reply" button. You'll see a "Manage Attachments" button. Click it, and attach the .txt file.

---

### Post by stoat09 on 2009-05-02
Here's hoping:-

---

### Post by stoat09 on 2009-05-02
Try again:-

---

### Post by stoat09 on 2009-05-02
eth0   link encap:Ethernet  HWaddr  00:24:21:1f:d8:fe
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
         Interrupt:219
 
lo       link encap:Local Loopback
         inet addr:127:0:0:1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:598 errors:0 dropped:0 overruns:0 frame:0
         TX packets:598 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:39880 (39.8 KB)  TX bytes:39880 (39.8 KB)
 
Phew. 
Chris.

---

### Post by stoat09 on 2009-05-03
[IMG]http://ubuntuforums.org/images/attach/txt.gif[/IMG]
 
Can anyone interpret these files please?
Chris

---

### Post by stoat09 on 2009-05-03
[attach]112304[/attach]

---

### Post by mikewhatever on 2009-05-04
According to ifconfig, you don't get an IP address. Right click on the network manager icon, select Edit Connections, and edit your wired connection according to your settings. If you don't have any special settings, choose DHCP.

---

### Post by stoat09 on 2009-05-04
Ok, so now I've re-installed Ubuntu 8.10 with the cable modem connected, and ifconfig now shows an IP address as a second line: 
   inet6 addr: fe80::224:21ff:felf:d8fe:/64 Scope:Link
I've input my settings manually via Edit Settings (the values change when the window is closed and re-opened), and  the network manager icon tells me that I'm connected, but I still cannot get online. Is this some kind of firewall problem? I can't find Firestarter or Lokkit in Add/Remove Applications. Thanks for your time.
Chris

---

### Post by unutbu on 2009-05-04
Please post the output of 

```
ifconfig
route
cat /etc/resolv.conf
ping -c1 google.com
ping -c1 74.125.45.100
```

If the ping commands do not return output within a short amount of time, you can use Ctrl-c to break out of the command.

---

### Post by morphodone on 2009-05-04
> **stoat09 said:**
> Ok, so now I've re-installed Ubuntu 8.10 with the cable modem connected, and ifconfig now shows an IP address as a second line: 
   inet6 addr: fe80::224:21ff:felf:d8fe:/64 Scope:Link

That doesn't look like an ip address to me.  Do you use dhcp or static ip addresses on your network?

```
eth1      Link encap:Ethernet  HWaddr 00:0a:cd:15:43:df  
          **inet addr:192.168.0.197**  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:cdff:fe15:43df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:297193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:153919 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:347534593 (347.5 MB)  TX bytes:14855491 (14.8 MB)
          Interrupt:16 Base address:0x8000 

```

Look for the bolded part above.

Is your router set to assign dhcp?

---

### Post by Toshubu on 2009-05-04
> **stoat09 said:**
> cat /etc now gives me:-
auto lo
iface lo inet loopback

I now have the results of "ifconfig" as a .txt file on this PC with internet access but  cannot manage to insert it into a posting. Can someone help with this please? Thanks.
Chris.

Looking at (what I assume to be) Stoat09's "cat /etc/network/interfaces" command output, I do not even see an ethernet interface.This is what mine looks like:

root@Tosh:/etc/network# cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

I would think that might be a problem.

---

### Post by stoat09 on 2009-05-08
Many thanks to all who provided useful assistance for my recent internet connection problem. The problem seems to have been that I had swapped the rj45 cable between two PC's after both had been booted up. The connection is DHCP. Linux PC has functioned well with no problems, since Tuesday last,  with the connections secure and settings correct before attempting to boot up. (We live and learn eh?)
Thanks again and keep up the good work.
Chris.

---

### Post by KevHed on 2009-05-08
under System/Administration/Network (you will have to unlock the module) is the wired connection box checked?  If not you may need to create a new wired connection and have if use DHCP.  Most likely a restart of services will be required before connectivity is established.  Hope this leads you in the right direction.  My Wlan card is detected as eth0 and my eth1 is my hardwired connection.

---

