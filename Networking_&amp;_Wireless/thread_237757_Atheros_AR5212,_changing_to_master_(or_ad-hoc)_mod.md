---
title: "Atheros AR5212, changing to master (or ad-hoc) mode, error, no wlanconfig"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by killfire on 2006-08-16
I just did a fresh install of dapper, and xubuntu dapper on my laptop. both detect the wireless cards (new) that are in them- for the laptop it is a Netgear WG511T, and for the desktop it is a D-Link DWL-AG530. So all seems to be well.

However, my intent is to have the desktop asking as an access point for the laptop- and thus I need to set its card to master mode. I tried what you are supposed to use: ```
iwconfig ath0 mode master
``` (ath0 is the interface), and it results in an error which I have found referenced around online, but with no definitive answer aside from use wlanconfig instead. the error is:
```
Error for wireless request "Set Mode" (8B06)   :
    SET failed on device ath0 ; Invalid argument.

```
So I went ahead and tried the various wlanconfig commands, with one problem: wlanconfig is not a program shipped with ubuntu. well isn't that nice. So I start looking around for where this executable could be found. Most references point to madwifi-ng, but the tarball for that only seems to have the kernel module. Other references to something called madwifi-tools, but the only repos listed all turn up server not found. So really, I need to know A. why the iwconfig command did not work and B. where I can find wlanconfig.

Thanks,
Daniel

---

### Post by tturrisi on 2006-08-16
What you want to do is create an Ad-Hoc setup.
[http://madwifi.org/wiki/UserDocs/AdHocInterface](http://madwifi.org/wiki/UserDocs/AdHocInterface)

---

### Post by killfire on 2006-08-16
> **tturrisi said:**
> What you want to do is create an Ad-Hoc setup.
[http://madwifi.org/wiki/UserDocs/AdHocInterface](http://madwifi.org/wiki/UserDocs/AdHocInterface)

Seriously, you did not read half of my message. It completely ignored one of my problems- I DO NOT HAVE WLANCONFIG. Even in the title I pose the option of ad-hoc mode, I am fully aware of it. It is that I cannot do either that OR master mode.

---

### Post by mfeif on 2006-08-16
I am having the exact same problem; I can't find wlanconfig anywhere.

This page:
[http://madwifi.org/wiki/UserDocs/Distro/Debian/MadWifi](http://madwifi.org/wiki/UserDocs/Distro/Debian/MadWifi)
claims that one needs to compile against Ubuntu, but it smells like they are talking about Breezy.

I can't execute the apt-get command because my apt cache is too small, but I'll work that out and give it a try.

It's odd that Dapper includes the driver, but not the tools that are necessary to configure the driver. Though, I suppose they want us to use Gnome tools to configure the driver rather than command line. Did you try that? Clearly NetworkManager isn't appropriate for an AP, but maybe it will give you some clues.

It seems that the absence of madwifi-tools is a bug; perhaps one of us should file it.

Update:
The files in here:
[http://debian.tu-bs.de/project/kanotix/unstable](http://debian.tu-bs.de/project/kanotix/unstable)
say that they're compiled against libc6 2.3.6-6 whereas Dapper has libc6 2.3.6-0ubuntu20.

The same directions on the first link note that the current version of debhelper in Dapper won't allow the madwifi-tools command to run.

Bummer.

I'm going to try and get the source and modify the dependencies for the current Dapper debhelper.

---

### Post by killfire on 2006-08-16
yeah, the other complication is that the machine I am trying to set up as an AP has no current access to internet. so it cannot get a listing from the world respository etc, all that it can get is usbkey copied individual files downloaded from a machine that does have access to internet.

if you figure out where wlanconfig is, please let me know.

it's funny, before switching to ubuntu on my main machine I was bouncing between slackware and gentoo, with most of my time on my main machine being in gentoo, and then I switched to ubuntu because it seemed to be so much less hassle, things seemed to just work, and now I have a problem where in gentoo it is brain numbingly easy to solve (one emerge and you have the tools...), and I've spent hours searching around for a solution for ubuntu. and nothing. I think as soon as I am back on a broadband connection I will switch back to gentoo. still leave ubuntu on my laptop (it is a litle light weight for compiling... 6.5 years old... plus I havent run into trouble with ubuntu on it... yet) 

and I think I'll make my server openbsd, and perhaps use it as an AP.. but I dont have access to that box either. Damn summer vacations..... found a nice tutorial and I like openbsd anyway.

---

### Post by nightybeta on 2006-08-17
sadly i have the very same problem. I will try to build madwifi myself and see if it helps but if anyone has any ideas please do share.

---

### Post by tturrisi on 2006-08-17
Wlanconf comes with the newest (newer) madwifi package, so you will need to download the latest madwifi_ng package, make & install it against your existing kernel.  You will also need the dev tools necessary to make & compile it.

found this:
[http://madwifi.org/wiki/UserDocs/AdHoc](http://madwifi.org/wiki/UserDocs/AdHoc)

Since the ubuntu madwifi are the older modules, you may be able to set adhoc mode using wireless tools (iwxxxx).

iwconfig ath0 mode ad-hoc

---

### Post by mfeif on 2006-08-25
I have this working now. It's not a very Debian way to do it, but it finally works! Here's what I did:

I followed their "Newbie Guide" **MOSTLY**
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

I did the install steps verbatim.

BUT!
Under the "Creating an Interface" there is a note:
[INDENT][FONT="Courier New"][COLOR="DarkGreen"]If your svn snapshot is more recent than the 23rd January 2006, (r1407) than you can skip the following step:

If not, then follow these instructions to make a normal station mode interface. Type (as root):

wlanconfig ath0 create wlandev wifi0 wlanmode sta[/COLOR][/FONT]
[/INDENT]

So, I **skipped** that step. [COLOR="DarkRed"]THIS SEEMS TO BE THE KEY!!![/COLOR]

Then there is the matter of "autocreating" interfaces. I want mine autocreated as "ap" since I wanted to use this card as an AP for other computers, so I made a file in /etc/modprobe.d called 'madwifi' that has the following contents:
options ath_pci autocreate=ap

And just to be sure, I put this at the end of /etc/modules:
ath_pci autocreate=ap

If you don't want autocreate to work, there are directions about how to turn it off, or how to set it into other modes here [http://madwifi.org/wiki/UserDocs/autocreate](http://madwifi.org/wiki/UserDocs/autocreate)

Now, I was able to configure the interface:
iwconfig ath0 essid MyESSID
iwconfig ath0 channel 11
ifconfig ath0 10.0.0.50 netmask 255.255.255.0 up

I did something similar on my laptop, and was able to ping! Glory glory. Ping however isn't very interesting... routing and NAT is.

In order to get it to route, I installed the excellent firewall "Shorewall" and set it up for three interfaces. Previously, I had been using Firestarter, which is cute, but doesn't handle three interfaces. After setting up Shorewall, tuning dhcpd to broadcast on the new interface, I can see my "access point" with my laptop's Network Manager.

Also, Shorewall seems a lot faster, which seems odd. Maybe because it blocks IPv6 by default.

I may tackle encryption, but for now I'm just happy to have wifi back here at home.

I hope that this helps.

---

### Post by xlyz on 2006-12-02
thanks for the guide. master mode working again :)

---

