---
title: "sudo what?"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by Alex-H on 2009-05-24
Hello all. New to this linux game, since xp outgrew the meagre specs of an old and trusted laptop - pleased to say ubuntu is a vast improvement in terms of disk-thrashiness on this machine. I was stunned to see out-of-the-box support for almost everything on this victor/jvc xp7210, despite it having lots of proprietary stuff in.

Few questions though, if I may?
- Coming as I do, and I expect most in this forum, from a windows background, - I'm used to needing numerous additional security related software packages - I've been using Zonealarm, Avast and adaware under windows. What do I need in an ubuntu environment?
- From time to time the usb wireless connection ***** itself - using a dlink dwl-122 dongle - which is stable under windows. Is there a way I could look to reset it under ubuntu? I have of course tried physically removing it, but the only fix I've found currently is to reboot.
- Also on the wireless thing, I don't seem to have any wpa support? Had to switch the router back to wep to get a connection up unfortunately. Is this telling me I need a better/later/different driver for the dongle?
- The constant requests for password every time I try to install something is getting old already - admin this, keyring that yada yada - is it turn off-able?

My apologies if, as is almost certain, I've missed the answers to the beginner questions, I'm at the bottom of what I suspect will be a steep learning curve!

Cheers,
Alex

---

### Post by Kareeser on 2009-05-24
1. You don't need anything. Ubuntu comes pre-configured with all of its ports closed, so nothing gets by unless you initiate a connection first. Furthermore, virus and malware writers don't often target Linux because of its low market share, which means we are safe for now. Furthermore, user privleges in Ubuntu (your question 4) keep us safe from malware as well.

2. N/A

3. Ubuntu has WPA and WPA2 support. You wouldn't expect anything less from an operating system that's one month old! :) If your dongle can't support it, then yes, it may be time to buy a new one. However, to keep the casual snooping neighbour out, WEP works fine.

4. Yes, you can log into the root account directly with "sudo su" in the terminal and do your business there. There are ways around it, and there are ways to re-enable the root account directly, but _nobody in their right mind would tell you how_, since it's there to protect you from yourself.... It's also against the forum rules. As tough as it sounds, "just get used to it", because this feature prevents less privileged users (or viruses) from wreaking havoc on your computer. It also protects you from yourself, if you are tricked into downloading and executing a seemingly harmless program.

You may ask yourself "Why do I have to type in my password to look at pictures of me from last night's party?"... and that's your warning, because you don't need to type in your password. It's probably a virus, or a piece of malware!

---

### Post by michy99 on 2009-05-24
To restart your wireless, enter this in a terminal```
sudo /etc/init.d/networking restart
```And yes, you will have to enter your password. :P

---

### Post by ugm6hr on 2009-05-24
The password thing is something you should get used to.  I would recommend you disable auto-login / timed login, that way, the Gnome Keyring will allow you to auto-allow each time after the first.  As explained, the sudo security model is deliberate: [http://www.psychocats.net/ubuntu/security#sudomakessense](http://www.psychocats.net/ubuntu/security#sudomakessense)

As for your wifi problem, if you copy and paste the output from the following commands in Terminal (with the device plugged in), we can at least see what chipset / driver you are currently using:

```
lshw -class network
lsusb
```

---

### Post by oldos2er on 2009-05-24
"The constant requests for password every time I try to install something is getting old already - admin this, keyring that yada yada - is it turn off-able?"

 See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for some suggestions on how to use sudo effectively.

---

### Post by Alex-H on 2009-05-24
Thanks very much all. Will try it out this eve, and post back with the usb wifi dongle info. It does support wpa in windows, so I suspect I need a better driver.

Cheers,
Alex

---

### Post by bagle on 2009-05-24
personaly if i were you i would install an anti-virus on your machine since you never can be too careful. plus rarely virus arewritten for linux so you should just stay safe.  i recomend clam-av or avast as an anti virus.;-);-)

---

### Post by chrisod on 2009-05-24
The virus scanners keep you from accidentally forwarding a windows virus along in an email, or they help protect windows users if you are sharing a drive or directory. I've been using Ubuntu sans AV software for 2+ years without issue.

---

### Post by Alex-H on 2009-05-30
> **ugm6hr said:**
> As for your wifi problem, if you copy and paste the output from the following commands in Terminal (with the device plugged in), we can at least see what chipset / driver you are currently using:

```
lshw -class network
lsusb
```

Thanks. This is what I got:
```
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: *macID removed*
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.5 multicast=yes wireless=IEEE 802.11-b
```
and
```
Bus 001 Device 002: ID 2001:3700 D-Link Corp. [hex] DWL-122 802.11b

```
Cheers,
Alex

---

### Post by Paqman on 2009-05-30
> **bagle said:**
> personaly if i were you i would install an anti-virus on your machine since you never can be too careful. plus rarely virus arewritten for linux so you should just stay safe.  i recomend clam-av or avast as an anti virus.;-);-)

Those products protect against Windows viruses, which you aren't vulnerable to anyway. Protection against Linux threats is taken care of through your normal updates.

---

### Post by Sef on 2009-05-30
> Quote:
 	 	 		 			 				 					Originally Posted by **bagle** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7340609#post7340609") 				
 				*personaly if i were you i would install an anti-virus on your machine since you never can be too careful. plus rarely virus arewritten for linux so you should just stay safe. i recomend clam-av or avast as an anti virus.:wink::wink:*
 			 		 	 	 
Those products protect against Windows viruses, which you aren't vulnerable to anyway. Protection against Linux threats is taken care of through your normal updates

The only time you need an anti-virus is if you use an email client, e.g., thunderbird, or evolution.   That is so you don't pass on a virus or other malware to your Window using friends.  A virus won't infect GNU/Linux, but it can ride on top of it and send itself to other computers.

---

