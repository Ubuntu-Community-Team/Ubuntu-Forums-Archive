---
title: "Missing Options in Network Manager 0.70"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by Vandel on 2008-10-04
As an initial declaration, I'd like to say that I do not claim to know very much about linux.

I recently upgraded my laptop's OS from Ubuntu 8.04 to Ubuntu 8.10 Beta.  The transition was far from painless and I ran into absolutely no problems.  I even received the added bonus of my wireless card being supported.  The problem that I am having now, though, involves the updated Network Manager (in Hardy, it was 0.6.6.  Now it is 0.7.0.)  I am attempting to connect to the campus wireless at my university to no avail.  

Security: WPA Enterprise
EAP Method: PEAP
Key Type: TKIP
Phase2 Type: None

Network Manager will not allow me to choose a key type (It doesn't even give me the option.)  It also won't allow me to choose 'None' as a Phase2 Type.

I do not know much about networking, so any help will be appreciated.  By the way, I am running Ubuntu 8.04 on my desktop, which is where I looked up the wireless settings.

Thank you.

---

### Post by hackerseraph on 2008-10-18
BUMP

I am also having these same issues; I need to be able to select between either aes or tkip; I dont beleive the auto is working

---

### Post by omega_drh on 2008-10-24
I just upgraded my T61 to Intrepid today, and can no longer connect to my corporate network, either. It uses WPA(1) with PEAP, TKIP, and EAP-MSCHAP-v2. This used to work fine in Hardy. Sorry I don't have any more information at the moment, but I at least want to at least say "me too."

---

### Post by bobaab on 2008-10-27
I'm also having the same problem.  Updated from Hardy to Intrepid last night and the option for TKIP has disappeared.  My connection was fine in Hardy, but now I can't connect anymore.

I also just wanted to say "me too".

---

### Post by wheresthesnow on 2008-11-02
I am having the same problem on my college campus,  I never used 8.04 but I know people who have and had our campus wireless work but now with 8.10 the lack of tkip support keeps the wireless from working.  If anyone finds a fix for this please let me know.

---

### Post by aero528 on 2008-11-02
This is my one of my two problems with 8.10, otherwise I love it.  My college uses tkip, and I can't connect.  I had to connect and enter all of the info for the network with 8.04, but it would at least connect.  If anyone has any ideas on this, please help!

---

### Post by Dakani on 2008-11-03
Can someone explain to me why they removed the options altogether?
I mean, I can understand why they might be hidden, but they really should keep it in there for advanced users or complex networks.
Plus, it is quite obvious that the automatic settings isn't working out for everybody...

---

### Post by spooner on 2008-11-06
I would also like to know as I am in the same situation... when I am at my desk I can connect via the eth net but if I want to go to a lecture/demeonstation I have to either leave my laptop on my desk and remote desktop or switch to windows and putty+X into a linux server... rubbish... yet again I souldn't have upgraded from LTS...

---

### Post by Forlornity on 2008-11-13
Same problem here, college wireless network: WPA2 Enterprise + PEAP + TKIP + MsCHAPv2

Auto fails, no luck at all.

---

### Post by whatsinaname on 2008-11-13
Wow we are all in the same boat.  I have Acer Aspire One, dual boot with xp and Ubuntu 8.10.  Networkmanager won't let me wpa-tkip.  Hope this gets fixed somehow.

I am going to try WICD.  Not sure what I am doing, but that's half the fun of messing with computers.

---

### Post by deltateam2 on 2008-11-20
A buddy has the same problem.  Why is this?

---

### Post by addiebk on 2008-11-21
It seems that the last thing that this post needs is another "me too!", but alack, it is so!  I know that there's a way to downgrade certain packages, and downgrading to Hardy's Network Manager would be a great solution-- I just have no idea how one would go about doing such a thing.  Anyway-- good luck to us all!

---

### Post by addiebk on 2009-01-12
I have managed to connect to my university's wireless (they do use tkip encryption) and without messing with the network manager.

Right click on the networking icon in the upper right hand connection and click 'edit connections'.  Find the wireless network that you have that uses tkip and click on the 'edit' button.  Under the tab 'Wireless Security', there is a drop-down menu for 'PEAP version'.  Make sure that this is set to Version 0, and then see if it connects!

It has worked for both me and a friend of mine who also uses Ubuntu, so hopefully it'll help some others with the problem.

---

### Post by shazbut on 2009-01-12
The missing authentication methods is a known problem in NM 0.7, see here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/284211]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/284211")

I'm using wicd [http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php") as a replacement while I wait for the NM issue to be sorted and can connect fine with PEAP/GTC authentication.

---

### Post by Favux on 2009-01-14
Hi everybody,

Also consider the method a bunch of us have used.  It involves editing the keys with Gconf editor.  See:

[http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

Hope this is helpful.

---

