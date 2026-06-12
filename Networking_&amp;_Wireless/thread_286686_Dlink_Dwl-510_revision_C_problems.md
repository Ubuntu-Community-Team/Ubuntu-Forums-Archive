---
title: "Dlink Dwl-510 revision C problems"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by birdie101 on 2006-10-28
Hi everyone.

I'm a new convert from Micro$oft land and am really enjoying the learning curve for Ubuntu.

However, I'm having heaps of problems getting my wirelss card to work.  The initial setup found a wireless card and called it "ra0".  I tried to enter my SSID and key and thought that everything would work out of the box, but to no avail.  

I have tried following various instructions on the net to get ndiswrapper to use the windows drivers for the card to work in Ubuntu and I'm now stuck.

if I run iwlist ra0 scan I get the following:
ra0       Scan completed :
          Cell 01 - Address: 00:15:E9:0B:6C:84
                    Mode:Managed
                    ESSID:"birdnest2"
                    Encryption key:on
                    Channel:6


I thought that would mean that I would have set thing up correctly, but nothing works via the wireless.

Can anyone please help me?  Ask for more information if I've left out the usefull stuff.

Many thanks,
Luke

---

### Post by ihavenoname on 2006-10-31
> **birdie101 said:**
> Hi everyone.

I'm a new convert from Micro$oft land and am really enjoying the learning curve for Ubuntu.

However, I'm having heaps of problems getting my wirelss card to work.  The initial setup found a wireless card and called it "ra0".  I tried to enter my SSID and key and thought that everything would work out of the box, but to no avail.  

I have tried following various instructions on the net to get ndiswrapper to use the windows drivers for the card to work in Ubuntu and I'm now stuck.

if I run iwlist ra0 scan I get the following:
ra0       Scan completed :
          Cell 01 - Address: 00:15:E9:0B:6C:84
                    Mode:Managed
                    ESSID:"birdnest2"
                    Encryption key:on
                    Channel:6


I thought that would mean that I would have set thing up correctly, but nothing works via the wireless.

Can anyone please help me?  Ask for more information if I've left out the usefull stuff.

Many thanks,
Luke
umm did you try the gui under System--->Administration----> Networking? Also you could try iwconfig ra0 channel (ur channel #> mode managed essid "<ur essid inside the quotes>"

---

### Post by -Chi.0 on 2006-10-31
Check this link for help w/ NdisWrapper on Edgy](*,) 
[http://ubuntuforums.org/showthread.php?p=1692550#post1692550]("http://ubuntuforums.org/showthread.php?p=1692550#post1692550")
I hope this helps:-k

---

