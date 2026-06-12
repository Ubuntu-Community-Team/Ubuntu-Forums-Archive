---
title: "Wireless woes... SO FRUSTRATED... now WIRED internet not even working, please help"
date: 2006-08-31
forum: Networking &amp; Wireless
---

### Post by littlec on 2006-08-31
Hello,
So i recently purchased a DWL-G132 usb card (D-Link) and am trying to get it working while I still have a wired connection available to me.

I am basically a blind man stabbing in the dark installing this thing.  I've read countless threads/tutorials/how-to's on installing and here's what I've been able to do.

network manager is installed

Card is automatically detected when plugged in as wlan0
installed ndwiswrapper (used my windows drivers the ath*.inf and the other A5*.inf).
card works fine, can SCAN networks, but not connect

tried installing linuxant's driverloader, it does not detect my device even when both drivers are loaded.

wifi radar i even tried, along with gtkwifi.

Now, not only does the D-link card still not work,
my WIRED connection doesn't even work.  (even if it's 'active' in the network manager settings').

With the usb key plugged in, i also have occasional hard locks (mouse/cpu/kbd freeze) that I've also read about in the threads with no solution.  --> hoping this will be solved once everything works. 

Can someone please help me with setting up my wireless and/or my wired internet?  I'm stuck in windows until then and need my computer for school.

Thanks.

---

### Post by littlec on 2006-08-31
hmmmmm....

i rebooted in ubuntu and ran dhclient.  WIRED is now working again (for now...?).  But it's still doesn't detect it connect in the nm-applet.  Just want to get wireless internet working with ubuntu or else I have to go back to windows.

Extremely frustrated and ready to throw my machine out the window. .. someone save me:)

*edit:

while i have the net i can paste this. so let me paste my iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:108 Mb/s
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


|| even with setting the essid, keys etc. it wouldn't connect...
--------------------

ifconfig returns this:

eth0      Link encap:Ethernet  HWaddr 00:E0:18:94:E5:CB
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fe94:e5cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:3790 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3770 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2434801 (2.3 MiB)  TX bytes:654633 (639.2 KiB)
          Interrupt:193 Base address:0xb000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5668 (5.5 KiB)  TX bytes:5668 (5.5 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.178.128  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.72.129  Bcast:192.168.72.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


not sure why it'snot showing wlan0. it was before, but also not working.
------------

and ndiswrapper -l

~$ ndiswrapper -l
Installed ndis drivers:
athfmwdl                driver present, hardware present
neta5agu                driver present, hardware present

-------------
my /etc/modules:
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
ndiswrapper
----------------

---

### Post by alanmzifa on 2006-08-31
Let me say I'm no wireless expert. We all seem to be fumbling around in the dark.

One thing perhaps might be worth a try (and it's a personal hunch rather than clever logic) is uninstalling network manager completely, re-booting and try to pick up the connection with wifi-radar. Initailly try to set up the connection without security and go from there. 

[click here]("http://www.ubuntuforums.org/showthread.php?t=246403")

---

### Post by littlec on 2006-08-31
Alanmzifa, thank you for your reply.
Actually came across several of yoru posts in my searches.

I Uninstalled network-manager (thoguht of that before but was worried it would disable net access, which means it would be a lot trickier to reinstall the package witout the net).  Still no luck.

I did however unsecure my router (no WEP) and the usbcard connects without problem.  

The problem somewhere is in the WEP.

My router is set on 64bit encryption right now.  Even entering the correct keycode in ascii form hasn't been working.  

At least we've narrowed it down to WEP/key problem I am assuming.

Any suggestions?

---

### Post by littlec on 2006-08-31
Does this solution [http://www.ubuntuforums.org/showthread.php?t=190703&page=2&highlight=D-Link+G120](http://www.ubuntuforums.org/showthread.php?t=190703&page=2&highlight=D-Link+G120)

address the wireless usbkey giving hardcrashes in i686 and amd distros?

---

### Post by alanmzifa on 2006-08-31
Not sure, it seems to be for adifferent adapter than yours. Do they use Identical chipsets?

The writer is suggesting you blacklist some native linux drivers (for prism chipped devices I think). 

I had some luck when I blacklisted islsm. If you think it's the same chipset it's certainly worth a try, there could be a driver clash occuring.

Keep a note of the original file before edit (or copy it to somewhere) so that you can put it back to how it was if necessary.

---

### Post by littlec on 2006-09-01
going to try i386 kernel and see how that goes. so far no crashing.

But also no luck with wireless still... I don't understand, i believe i've properly config'd the network with iwconfig.  It's still not able to connect.

---

### Post by littlec on 2006-09-01
PROGRESS! or at least i think it is.

Ok, still using i386, NO crashing at all.  I'm going to stick with this for now until I get the i386 working then try to blacklist possible conflicting drivers in i686 once i get wlan resolved.

I changed the iwconfig key to an open key:  iwconfig key s:keynamehere open

The activity light on my wireless usbkey now blinks and appears to be communicating with the router.  Still cant get onto the net or ping. Even with a dhclient, but it now finds an Access Point.
Able to connect to router now, now It just needs to be able to connect to the net?  

wlan0     IEEE 802.11g  ESSID:"ssid"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:C0:02:F9:EE:D0
          Bit Rate:54 Mb/s
          Link Quality:0/100  Signal level:-54 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by littlec on 2006-09-01
Problem resolved, my 'solution' is here:

[http://www.linuxquestions.org/questions/showthread.php?p=2405219&posted=1#post2405219](http://www.linuxquestions.org/questions/showthread.php?p=2405219&posted=1#post2405219)

Will keep working at the other issues.

*edit: i am the dork that entered a hexidecimal key as a string
ALL other settings have to be in check as well at the same time for everything to work.  It's like a game of combinations.

---

