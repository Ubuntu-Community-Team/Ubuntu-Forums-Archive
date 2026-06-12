---
title: "Ethernet card won't connect"
date: 2005-12-01
forum: Networking &amp; Wireless
---

### Post by Zooropa on 2005-12-01
Hi,

I've installed 5.10 tonight, and it's my first installation of Linux ever.

My network card is connected, and it's listed in device manager.
"SMC2-1211TX Accton Technology Corporation"
It's Hewlett-Packard card, as it rightly says in the OEM Vendor.

I go into Networking, it has the Ethernet card listed, I go to set it up, I choose DHCP, the icon spins for a second, a progress bar pops up for 20 or so seconds, and then all seems well.
it says the connection is active.

I Load up Firefox, but get an error saying it can't connect.
Same with my email.

Does anyone have any ideas?
I'm totally new to this.
The people who I've mentioned it to seem to think that it should have connected right away with no problems.

---

### Post by janz84 on 2005-12-01
how is your network card connected? PCI? Cardbus?

---

### Post by Zooropa on 2005-12-01
[QUOTE=janz84]how is your network card connected? PCI? Cardbus?[/QUOTE]
It's PCI.
Sorry, I should have mentioned.

---

### Post by janz84 on 2005-12-01
maybe your isp has specific settings you need to input... did your previous operating system networking run off DHCP?

---

### Post by Zooropa on 2005-12-01
Yes, as far as I know.

Here is the output of an IPconfig /all (different network card - I'm just moving the cable between machines as I try)



Windows IP Configuration
        Host Name . . . . . . . . . . . . : zoostation
        Primary Dns Suffix  . . . . . . . : 
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection 4:

        Connection-specific DNS Suffix  . : 
        Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connection
        Physical Address. . . . . . . . . : 00-07-E9-44-D6-6B
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 81.104.105.112
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 81.104.105.254
        DHCP Server . . . . . . . . . . . : 62.252.128.20
        DNS Servers . . . . . . . . . . . : 194.168.8.100
                                           194.168.4.100

        NetBIOS over Tcpip. . . . . . . . : Disabled
        Lease Obtained. . . . . . . . . . : 01 December 2005 21:39:59
        Lease Expires . . . . . . . . . . : 03 December 2005 07:31:19

---

### Post by janz84 on 2005-12-01
try reseting your modem/router and turning on dhcp on ubuntu again

---

### Post by Zooropa on 2005-12-01
I had to re-install to get it to work.
This time round it automatically detected my hostname etc and I was online as soon as I logged in.

Is it always this difficult to install a network card and connection after the intitial installation? :S

I'm going to get some books and read up.

---

### Post by aleks on 2005-12-02
hi there
Last night I install ubuntu for  the first time in my computer and i am totaly new to this...I was reading ur problem that u experienced and it seems similiar to minde. Please let me know what do you mean by re-installing it. What did u actually do

---

### Post by KermitJr on 2005-12-02
Hmm,

Looks like your ipconfig /all  doesn't show a proper ip address.  You would normally expect 192.168.*.*

So I would think that a simple reboot of the router and computer would have worked.

Actually, reboot the router, and then do the following in a  terminal:

```
ifdown -a && ifup -a
```

That tells the computer to bring down all ethernet connections (ifdown -a) and then back up.  If you want to be precise:

```
ifdown eth0 && ifup eth0
```

Also, I've noticed that some ethernet cards need a reset if you are rebooting from windows previous.  I had one once that after a windows boot (or installing after having run windows last) would hang for 2-3 minutes and then still need the ifdown ifup command to work in linux.

Hope this helps,
KermitJr

---

### Post by Zooropa on 2005-12-05
KermitJr - That's, I have this page bookmarked on my Windows PC in the event of this ever happening again :)


aleks - I unplugged my modem's power for a minute, and reconnected it, rebooted the PC, and installed ubuntu again from the start.

---

