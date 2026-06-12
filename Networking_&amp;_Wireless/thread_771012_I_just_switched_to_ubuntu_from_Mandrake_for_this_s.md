---
title: "I just switched to ubuntu from Mandrake for this same problem."
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by Brian Newman on 2008-04-27
I was unable to get my wireless connection working with my old OS, so I thought it might work with a different one.

Linksys 2.4 GHz "wireless-G" card and router.

I did look at the threads stickied at the top, but I am not adept at the command line level.

---

### Post by Brian Newman on 2008-04-27
WEP encryption.

---

### Post by Brian Newman on 2008-04-28
bump

---

### Post by Brian Newman on 2008-04-28
Any guidance?

---

### Post by wireddad on 2008-04-28
[http://ubuntuforums.org/showthread.php?t=409914](http://ubuntuforums.org/showthread.php?t=409914)

Hope this helps.

---

### Post by mmilitia9 on 2008-04-28
I know this isn't the post you were hoping for, but I thought you should know.. Even using a Simple Linux Distro such as Ubuntu, you will have a time where a problem will occur and the only way to directly fix it is through the command console.  
I can understand if they wanted you to make magic happen with the command console because that would suck..but normally they paste code on the page and just want you to follow simple instructions to get your stuff working.

Anyway.. I guess I should start with questions such as...

What type of laptop is it?(Stats)

Did the Wireless card work in any prior OS's?  Which ones?


My guess is... if it didn't work with Mandrake and Ubuntu.. it's definitely something with the wireless card that needs some kind of run around.  Other people HAVE to have the same hardware then you somewhere.. Your problem should be solved shortly.. =)

Good luck!

---

### Post by Brian Newman on 2008-04-29
It is a desktop, and the lady I am renting from has a wireless card and router for me to use. I have always connected through the ethernet in the past, and this is my first attempt at wireless. She told me she had it running with another computer at one point, and I have to assume it was windows(everyone spits:lolflag:).

I know it is a pentium four, but little beyond that. My feild now is glassblowing. I gave up programming when I was fifteen or so, and DOS was boss.

I will call up a terminal, type iwconfig, and post back shortly.

---

### Post by Brian Newman on 2008-04-29
This is not cut and paste, it is from notes I made downstairs. First it lists some other devices like ethernet as not connected (they aren't), and then it gets to:

wlan0    IEEE:802.116   ESSID:"SSID"
         Mode:Managed   Frequency:2.412GHz Access Point:Not-Associated
         Tx-Power=27 dBm
         Retry min limit:7  RTS thr:off thr=2346 B

Followed by some more items with a value of zero.

Edit: the bullatin board code seems to display an "o" in "off" as a smileyface in this post.

---

### Post by wireddad on 2008-04-29
I think you need to input the SSID.

---

### Post by Brian Newman on 2008-04-30
> **wireddad said:**
> I think you need to input the SSID.

I was told the network name was "SSID", so that is what I entered. I am assuming that is how it was set up, but it would be nice to be able to check. The lady I am renting from is running windows (the computer I am on now). Can I check the router settings from this machine, just to be sure? Any other ideas on what might be wrong, or how to go about diagnosing it?

---

### Post by Brian Newman on 2008-05-01
Bump.

---

### Post by wireddad on 2008-05-01
> **Brian Newman said:**
> I was told the network name was "SSID", so that is what I entered. I am assuming that is how it was set up, but it would be nice to be able to check. The lady I am renting from is running windows (the computer I am on now). Can I check the router settings from this machine, just to be sure? Any other ideas on what might be wrong, or how to go about diagnosing it?

You will need the admin username and password to check the router settings.  I would check to see if their are any security settings that is disallowing you to connect...like MAC only or you may ave to expand the DHCP IP's.

---

### Post by Brian Newman on 2008-05-01
So how do I check the router settings? This machine I am on now is running windows, and is connected to the modem by ethernet. I tried putting 192.168.2.1 into I.E., but it shows a search result.

---

### Post by Brian Newman on 2008-05-02
Bump.

---

