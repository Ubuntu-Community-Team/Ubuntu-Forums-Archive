---
title: "Natty-Wired connection Realtek 8101E/8102E won't stay on"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by Bilou5404 on 2011-08-10
I'm deeply puzzled, and close to panic.
----
Edit
----
This post may be in the wrong place. I saw a lot of miscellaneous posts on different problems here and assumed it was the right place for new folks to do that, but, rereading a lot of stuff makes me think that I should have put it directly into networking. Sorry if that is the case.

Posted a link to this one in Networking:

[http://ubuntuforums.org/showthread.php?t=1822778]("http://ubuntuforums.org/showthread.php?t=1822778")



I have a no-name laptop which under the hood is really an N280 netbook. It has always run on on either XP or W7 and performed pefectly. 

I installed natty (11.04)on an external USB hd when the internal hd went down (terminally).

So far so good. Everything seemed to work in spite of my ignorance of up-to-date Linux (I did play with MINT when it first came out, but that was years ago).

The net connection was WIFI. That worked fine on 3 different connections I used in mini-hotels. I've been using it like that and have added basic stuff I'm used to like System Monitor, the Opera browser that does my email through IMAP, a power user text editor, Libre Office and a few games like Open Arena. Oh, and a couple of Firewall front ends, both of which I've disabled for the moment just in case they interfered. Again, everything worked without the slightest problems. Sigh of relief, as I use this little box for getting work and relaxing after the work. If it isn't broke, don't fix it.

I just moved to a new small flat which has cabled adsl using a conventional router/modem, but no WIFI. It seems to connect (looking at System Monitor shows a blip in Network activity, but drops out within a second or two. It seems to keep trying, but can't hold it

Net result is my pending bankruptcy if I can't get it fixed.

I've borrowed this old Compaq from my landlady's daughter so I can talk it through. It runs XP and is using the exact same cable. I might have to give her the laptop back pdq, so if someone can jump in and tell me what I need to do then I'll be most grateful.

The specific symptoms are that eth0 appears in the drop down network menu, the network graph in System monitor shows a blip. Then eth0 disappears from the dropdown menu and a little dialogue appears briefly saying I'm disconnected.

Yes, I think I can handle command line diagnostics, save the results in text on a usb stick, and post them here. I've tried several  from googling, but I don't understand the output. The only stuff I could find about wired internet was mostly about 10.04 and Broadcom. Since I'm on 11.04 and Realtek I didn't dare try any fixes, just some diagnostics to see if anything looked weird

If it's any help, the output of ipconfig /all on the borrowed machine is:

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\TH User>cd C:\

C:\>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : lien
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Broadcom NetXtreme Gigabit Ethernet
        Physical Address. . . . . . . . . : 00-0D-9D-8C-3B-FB
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.119
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 8.8.8.8
                                            8.8.4.4
                                            192.168.1.1
        Lease Obtained. . . . . . . . . . : Thursday, August 11, 2011 7:21:31 AM

        Lease Expires . . . . . . . . . . : Sunday, August 14, 2011 7:21:31 AM

Ethernet adapter Wireless Network Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : HP WLAN 802.11a/b/g W500
        Physical Address. . . . . . . . . : 00-11-0A-81-ED-7D

Using that, I have also tried manual configuration of eth0. Doesn't work. IPV6 is on ignore. IPV4 has been on Auto or auto address only with Google DNS, or manual. Nothing works.

help!

----------
Edited
----------
Add diagnostic results as best as I can. Had probs with Linux/other system formatting. Seems OK now. 
Includes:Output of lspci, lsmod,ifconfig,nm-tool, and
cat /var/log/syslog | grep -e r8169 -e etwork | tail -n25

See attachment.

---

### Post by Bilou5404 on 2011-08-12
Bumpety bump buimp.

There must be someone out there, even if they say "go back to Windoze, it works"

---

### Post by Bilou5404 on 2011-08-12
Bumbity bump bump

Hello, is there anyone out there without a deaf-aid?

Common chip, but no takers.

If it is terminally bad then just tell me. No sweat.

---

### Post by gordintoronto on 2011-08-12
This seems to be bad news:
[http://markmail.org/message/lfyaikqxn3igbkeq](http://markmail.org/message/lfyaikqxn3igbkeq) 

You might learn more by Googling 10ec:8136 and some other words.

---

### Post by Bilou5404 on 2011-08-13
> **gordintoronto said:**
> This seems to be bad news:
[http://markmail.org/message/lfyaikqxn3igbkeq](http://markmail.org/message/lfyaikqxn3igbkeq) 

You might learn more by Googling 10ec:8136 and some other words.

You got me Googling again. Thank you. I was just about to scout around for a very high building with a lot of concrete at the base!

I posted what I think I should attempt as a solution in Networking, but I'm really apprehensive. It's all a lot more then I will understand.

[http://ubuntuforums.org/showthread.php?t=1822778]("http://ubuntuforums.org/showthread.php?t=1822778")

Thanks again

Guillaume

---

