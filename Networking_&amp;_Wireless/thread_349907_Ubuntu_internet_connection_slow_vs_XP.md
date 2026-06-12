---
title: "Ubuntu internet connection slow vs XP"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by Caen on 2007-01-30
Hi,

I just installed Ubuntu on my PC and I dual boot with XP.  I have noticed a considerable speed difference in my internet connection between XP and Ubuntu.  Is there any reason why this would be the case?

Any  help would be appreciated.  Let me know if you need some information from me to help diagnose.

Thanks

---

### Post by gamradtb on 2007-01-31
Hi there!
I just read through all the forums and with a combination of a few different posts and my own steps I have got the internet to be quick on Ubuntu 6.06 Desktop.

**System:**

**Internet Provider: **Qwest Premier DSL 7MB/896Kbps Package with ActionTec Modem
**Router:** IPCop Firewall with a few customizations on and old Intel Pentium IV 1.8GHz System.
**System:** Intel D845GLAD, Intel Pentium IV 2.4Ghz, 1GB of Ram and 60 IDE HD with Intel Pro 100 NIC
**Operation System:** Ubuntu 6.06

**Issue:** Slow Internet. Sites were really slow and ping times were too.

**RESOLUTION**

**Step one:** Disableing IVP6 in Firefox and Ubuntu
[LIST=1]
[*]Open Firefox in the address bar type about:config find the line network.dns.disableIPv6. Double click on it to change it to True
[*]Open a terminal and type sudo gedit /etc/modprobe.d/bad_list and add the line alias net-pf-10 off.
[/LIST]

**_Note:_** The above steps made my Ping response time drop to about 40ms to 80ms consistently.

**Step two:** Changing DNS from ISP to OPEN DNS.
[LIST=1]
[*]In my Qwest DSL ActionTec Modem I set the DNS manually to Primary: 208.67.222.222 and the Secondary to 208.67.220.220
[*]I also enter the above settings into my IPCop firewall.
[/LIST]
**Step three:** Reboot Ubuntu

**Step four:** ENJOY A WINDOWS FREE WORLD! :)

---

### Post by borobudur on 2007-07-30
[gamradtb]("http://ubuntuforums.org/member.php?u=230901") you saved my life. Step 1 improved my download speed so much!
Thanks!

---

### Post by ggordon on 2007-08-18
I was having the same problem and the first item fixed my problem too.  I have a Windows computer that has been very fast, but when I set up my first Ubuntu computer about a week ago, it has been very slow.  Now it's working great.

Thank you gamradtb!

---

### Post by starlightit on 2007-08-21
Ok I'm almost to the point where I believe this is a compatibility issue with my router, and Linux, although I can't imagine why that would be an issue (Read somewhere that it was possible).

I've disabled IPv6 in both firefox, and within Ubuntu.

I've installed opera

I've gone through countless threads tweaking firefox 

Changed a line in the nsswitch.conf to hosts: files dns

Tried using openDNS

Searched google and the forums tirelessly for an answer to slow connection.

Some pages load quickly others load slowly, Ubuntu update download speed never exceeds 25k

Adobe.com stops loading at wwwimages.adobe.com

Java download hangs at starting never actually begins downloading.

This is a wired ethernet connection on a hub. The other machine connected to the hub is an XP machine and it's connectivity is fine.

I've directly connected the Ubuntu machine to the data jack in the wall removing the hub, still no dice. 

The DNS server is a windows 2003 domain controller, but I have tried open dns with no luck either.

Browsing is slow both fully installed, and off the live CD.

Anyone have any other thoughts?

---

