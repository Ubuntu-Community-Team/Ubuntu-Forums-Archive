---
title: "Wifi doesn't work at certain hotspots"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by Chriswaterguy on 2007-12-15
I have a Lenovo Thinkpad R60 and I've been traveling a lot, connecting (or trying to connect) wherever there's wifi. 

Most of the time I can connect successfully, though sometimes I need to go through the "Wireless security" and "Authentication" options, by trial and error. Other times I cannot connect, in spite of entering the password carefully, trying every option, rebooting, and getting help from the person on the spot (e.g. net cafe worker) and that person telling me that connecting Windows and Apple computers is very straightforward. 

I'd really appreciate any help - where I'm staying at present I'm forced to use the desktop PC machine, rather than my own machine which has my data, bookmarks and programs. 

Other info which might be relevant: 

1. Wifi Radar never works, even in locations where Network Manager is able to connect. 

2. At one hotspot where I was last month (no password) it was simple to connect initially, but I would often lose connection and then Network Manager (nm-applet 0.6.5) would refuse to do anything when I tried to select the signal I wanted to connect to. I tried ending nm-applet and restarting it, but no available connections would show. I had to restart the computer, which is a major time-waster on a very slow connection in Indonesia, when Firefox has to reload every tab.

Thanks!

---

### Post by Chriswaterguy on 2007-12-15
Pity, I'd hoped someone might have an idea on this. 

I think it's time to look for a different distro.This is only one of many bugs and lack-of-documentation problems I constantly experience with Ubuntu. I'm in danger of feeling nostalgic for the stability of Windows XP - and at least I can make XP mostly secure, with a couple of hours effort - whereas my installations of Ubuntu and Xubuntu have been persistently unstable and time-consuming. 

I do like the idea of Ubuntu, and the active community, and I know it works and is stable for a lot of people, but at sure as heck isn't for others, including me. 

One thing that might help improve the documentation (to develop proper help pages that are easier to navigate, rather than having to search the forums for advice that may be good or may be harmful) would be to license all posts to be compatible with the help wiki, so that when there's a good bit of advice here, another user can put it straight into the wiki.

---

### Post by Chriswaterguy on 2007-12-16
I've just double checked with the local expert (my friend's son) and I'm definitely using the correct password, but still can't connect at all. Looks to me like a major problem when a user can't rely on wifi being able to connect - does no one have any suggestions? 

I'm off to catch a train to another kind friend's place who is letting me use their (wired) connection. This is not the experience I was hoping for when I switched to Linux. ](*,)

---

### Post by Chriswaterguy on 2007-12-19
I just ran an OpenSUSE (Gnome) LIVECD, which connected with only a small hiccup. 

As I've found at other times with Network Manager in Ubuntu, it gives me options (WEP 128 bit, 64 bit HEX...) and I had to find it by trial and error. It turns out it was the second one - 64 bit HEX. When I had tried that option in Ubuntu and entered the password, the "OK" button remained greyed out. I thought that meant it had detected what kind of WEP it was and wouldn't let me choose a different one, but apparently not. 

I'll try again, and if I still can't get it to work I'll try reinstalling Network Manager. 

Hoping it works - I'd rather be able to keep using Ubuntu for the next week or two, to give myself time to decide on which distro to move to (PCLinuxOS sounds interesting but I need to try the LiveCDs for a few distros.)

---

### Post by Giradman on 2007-12-19
Sorry that you're answering your own thread - frustrating when you're trying to solve a problem - not sure that I can help you much; I'm new to Ubuntu 7.10 - put it on an old IBM laptop w/ a 'dead' HD - replaced the HD & upped the RAM - really enjoying the experience (all my other computers are running Windows XP or VISTA) - after installation the laptop connected immediately to my Linksys wireless router (I was astounded!); I've taken it on the road now 3 times, and w/ some effort have been able to connect 'wirelessly' - I have a number of 'network managers' that appear in the top bar - not sure that I yet understand them completely, but have w/ some minor effort been able to get them to work (not as easy as w/ my Windows traveling laptops) - yes, this could be improved; but, please keep posting your experiences - may help others, like me! :)

---

### Post by Chriswaterguy on 2007-12-19
Yes very frustrating. My experience has been that when I tell Linux people some of the many problems I'm experiencing, I'm sometimes met with helpful answers, but sometimes just with surprise and a complete lack of answers. 

I just reinstalled network-manager with synaptic, and it made no difference. 

You said you have 3 managers - what are they? I installed wifi radar but it doesn't work (clashes with network manager perhaps)

---

### Post by Skidpad on 2007-12-19
Glad to hear you sticking with this - even today, wireless networking in Linux can be a pain in the butt for many of us.  I don't know what I can contribute to help your situation, but I will tell you that I have found a wide degree of usability among distros within the same family, meaning I can connect no problem with Kubuntu, but not Ubuntu.

Even last night, my desktop computer would not connect with Sabayon 3.4, but would with Gutsy - both LiveCd's.  I haven't found consistent rhymn or reason with much of it, just that hardware and different OS' get along differently - as you have found out.  

Another possible problem is having too many wireless managers present and running.  I originally tried Network Manager, and had little success.  Wifi Radar was much better in my application, but I've found something better - for me anyway.  I'm running Edgy and connecting via Ralink 2500 chipset in PCMCIA format.  I've learned to manipulate it quite well via the "RutilT WLAN Manager", but I did have an instance at a hotel last spring where I could see the network, but could not connect. to it.  I am not convinced it was entirely my laptop's (or my own) fault though.

Nevertheless, persevere, continue to try other distros, and post your results back here.  It can be frustrating when your posts aren't creating the type of response you'd like to see, but don't give up - this place is often far more helpful to those who have shown they are willing to listen and help themselves.

Good luck and keep posting so you can be helped.

---

### Post by Giradman on 2007-12-21
> **Chriswaterguy said:**
> Yes very frustrating...........

I just reinstalled network-manager with synaptic, and it made no difference. 

You said you have 3 managers - what are they?

Please find attached a couple of 'screenshots' of the 2 network managers that I have installed (again, not sure that I should be running both but each seems to have slightly different features & options?) - usually, I've been able to get connected on the road (which is the 3 times mentioned + at home).

Currently, I'm away at a hotel in Charlotte, NC for a few days - have the IBM laptop w/ me - the room had a 'wired' internet option (have not tried that before), so plugged in the adapter & booted-up, just had to sign into the hotel's login page and I was connected - did nothing w/ the network managers; and don't plan to as long as it's working! :)

As mentioned in the previous post, there does seem to be a lot of varied experiences w/ this internet connectivity - good luck!

---

### Post by Chriswaterguy on 2008-02-09
The solution for me unfortunately appears to be: don't use Ubuntu. 

I've been using Mandriva 2008 One (with Gnome) and having far fewer headaches in general than with Ubuntu, and no significant trouble connecting to wifi at my friend's place (where Ubuntu wasn't working). Not perfect, but bottom line: it works. 

Just my experience.

---

### Post by jufri001 on 2008-03-23
... I have been having the exact same problem. Has nobody turned up any hints yet?

---

### Post by cnich23 on 2008-07-13
Posted several times about this... and no one knows anything. It's very frustrating

---

### Post by mutzinet on 2008-07-14
Same problem here. This is my only reason for wasting 12Gb of disk space with a windows partition, to be able to connect when I'm travelling. No problem at home with Wep, no problem at work with WPA-entreprise, but I can't connect (or most of the time not, because it sometimes works...) at my university, where luckily I have ethernet access in my office.
And I can only seldomely connect in hotels. I am using Kubuntu, but currently with gnome and network-manager. Problem is similar in KDE. Machine is an old T40p.

---

### Post by zipperback on 2008-07-14
I've been using Ubuntu 7.04 with wicd to manage my wifi connections and I've been really happy with the results.

wicd homepage is [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Perhaps this might help you manage your connections a little easier.

Hope this helps you,

- zipperback
:popcorn:

---

### Post by cnich23 on 2008-07-14
wicd did not work for me unfort

---

### Post by mutzinet on 2008-07-15
Thanks Zipperback,

I've tried wicd before, but I need Wap-enterprise at my work, which wicd doesn't support natively. And since nm and wicd cannot coexist on the system, I makes things slightly complicated when travelling. ;)

---

