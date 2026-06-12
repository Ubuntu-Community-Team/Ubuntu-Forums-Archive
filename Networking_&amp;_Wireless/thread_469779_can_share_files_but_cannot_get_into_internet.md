---
title: "can share files but cannot get into internet"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by the ber on 2007-06-10
using ubuntu 7.04 and w2k on two pc's. one is cable connected via modem to a d-link router, and everything works as expected, both in windows and in linux. the other pc is connected via netgear wg111v2 wlan usb stick. this second pc works fine with windows. the wlan-stick would not work with ubuntu 6, but as soon as i upgraded to ubuntu 7.04 it worked right off the bat. i can use the shared folders in the first pc, i can print on the printer which is usb-connected to the first pc, but i cannot connect to the internet with the wlan-stick. i can ping the d-link router, i can see which ports are open on the router, etc.  i tried changing the preferences in firefox to no avail. i must be missing something very basic. can anyone point me in the right direction?

---

### Post by conjur3r on 2007-06-10
Can you ping any ip address from the internet?  For example, try to ping google.com using 64.233.167.99.  If you can, you need to look at your DNS configuration in the /etc/resolv.conf file.  Some dlink models are known to have problematic DNS support.

---

### Post by the ber on 2007-06-10
thanks for the quick reply.
when i try to ping an internet adress i get the message "network is unreachable". i looked at the resolvconf folder, and it had a file named "avahi-daemon" but i can't figure out what it means. there is no mention of the d-link router there. as near as i can tell there is no firewall set up in ubuntu, and i know that there is no firewall set up in the d-link router. maybe i need to sleep on it; i've spent hours today to just be able to see the network.

---

### Post by conjur3r on 2007-06-10
Copy/paste this file (rather than a folder): **/etc/resolv.conf**

Also copy/paste your routing tables by entering the rollowing in a terminal:
# route

Does your laptop automatically obtain networking settings from your dlink router?  Ie, is it setup in dhcp mode?

---

### Post by the ber on 2007-06-10
the second pc is not a laptop, but that probably makes no difference. yes the setting is dhcp.
i'll just reboot to linux to copy/paste the files you asked for and get back.

---

### Post by the ber on 2007-06-10
here are the files. i hope you can read them. i saved them to a windows fat32 partition.

---

### Post by the ber on 2007-06-10
just looking at my post, it doesn't seem that the file got through. if i open the file in explorer with notepad it's pretty garbled. how do i copy text into a post?

---

### Post by conjur3r on 2007-06-10
/etc/resolv.conf is a text file and not a binary.  I'm unsure why you can't open it up in notepad and read it?  Did you copy the right file?

Don't forget to copy what **# route** spits out.

---

### Post by Mr. C. on 2007-06-10
"network is unreachable" indicates a route problem.

What is the output of :

[B]ifconfig -a
netstat -rn
[/B]

MrC

---

### Post by the ber on 2007-06-10
thanks for the replies.
first: i don't have a file named resolv.conf.  i have a folder named resolvconf, and in that folder is another folder etc. see the screen shot.
i have also included screen shots of route, ifconfig, and netstat.
i really appreciate your assistance, and i hope it doesn't seem like i'm slow to answer. i have to reboot to linux every time i try something new, and then back to windows to reply.

---

### Post by dbott67 on 2007-06-10
You're definitely missing the default route from your system.  On your Windows system, can you post the output from the following command (I'm looking for the "Default Gateway" address):

```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\WINDOWS>[COLOR=Red]**ipconfig /all**[/COLOR]

Windows IP Configuration

        Host Name . . . . . . . . . . . . : omega-xp
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Cont
roller
        Physical Address. . . . . . . . . : 00-15-C5-0C-AD-05

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Dell Wireless 1390 WLAN Mini-Card
        Physical Address. . . . . . . . . : 00-16-CE-31-88-6F
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.105
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        [COLOR=Red]Default Gateway . . . . . . . . . : 192.168.1.1[/COLOR]
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
        Lease Obtained. . . . . . . . . . : Saturday, December 02, 2006 3:25:06
PM
        Lease Expires . . . . . . . . . . : Saturday, December 09, 2006 3:25:06
PM

C:\WINDOWS>
```

Notice in my output that it's [COLOR=Red]192.168.1.1[/COLOR]; yours will be something like 192.168.[COLOR=Red]0[/COLOR].xxx.  When you boot back into Ubuntu, you need to set the gateway address to the same one that Windows uses (probably 192.168.0.1) and device (wlan0) to suit your particular configuration:
```
route add -net default gw [COLOR=Red]192.168.0.1[/COLOR] dev [COLOR=Red]wlan0[/COLOR]
```

Note: you might need a 'sudo' in front:
```
**sudo** route add -net default gw [COLOR=Red]192.168.0.1[/COLOR] dev [COLOR=Red]wlan0[/COLOR]
```

-Dave

---

### Post by the ber on 2007-06-10
you were right about the missing entry, so i followed your directions and added the default entry. see the screenshot for the route, netstat, and ifconfig entries.
now i can ping the google website, as conjur3r suggested. only thing is, i still can't get into the internet with firefox, and i also now can't get into the windows shares, printer, etc.
??

---

### Post by the ber on 2007-06-10
dbott67, i took another look at your post to see what could be wrong with my configuration. in my network configuration window, in ubuntu, there was no entry under "DNS", but in the windows ipconfig there was an entry. so i added the same adress as the default gateway to the ubuntu window, and now i am writing this message using ubuntu!
thanks a bunch you guys.

---

### Post by conjur3r on 2007-06-10
It seems like your machine is not completing the DHCP process.  You will almost always obtain the default route and DNS details with an automatically configured network device.  If this is the case, you may experience periodic *resets* of the DNS/route.  You can thank the dlink router for that.  We've got a dlink router at work and it has similar issues too.

To overcome this, you may want to apply a static network configuration.

---

