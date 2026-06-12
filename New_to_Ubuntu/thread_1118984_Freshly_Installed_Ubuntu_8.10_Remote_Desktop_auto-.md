---
title: "Freshly Installed Ubuntu 8.10: Remote Desktop auto-recognition not active"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by swarup on 2009-04-07
I've just installed Ubuntu 8.10 on one of three computers connected to a local network via a router in our home office. All three run Ubuntu, and the other two see each other automatically via Remote Desktop. This third one, on which I've just installed Ubuntu 8.10, and then run the update manager and installed all the updates, does not see the other two computers and nor do the other two see it. If I run ifconfig to get the address of either of the other two computers, then by typing that address into Remote Desktop in the third computer, that third computer (with the newly installed 8.10) will recognize the other computer and function properly in Remote Desktop with either of the other two computers. So Remote Desktop does work fine if you give it the address it needs to connect with; it is just the autorecognition which is not active. Someone has told me that the Avahi Service is the software that does the automagic *.local name resolution. So how can I make it active on this third computer? It was active automatically from the get-go with my other two computers. I do not know why it is not active by default with this one two.

---

### Post by swarup on 2009-04-08
I've been waiting anxiously for 18 hours, and trying to read about this and get a solution-- but haven't found one. I'm sure if one of the folks with Remote Desktop experience has a look at this, the solution will be easy. Please kindly, if someone can help it would be wonderful. Thanks :p

---

### Post by billfreeboy on 2009-04-08
I've installed it too! XP is formatted off the hard drive! (Sorry Mr. Gates but Linux Wins!)

---

### Post by theozzlives on 2009-04-08
Did you go to System > Preferences > Remote Desktop and set it up?

---

### Post by swarup on 2009-04-08
> **theozzlives said:**
> Did you go to System > Preferences > Remote Desktop and set it up?

Yes, I did. 

But even then, it seems to me that that "set-up" window is really for the host computer. It "allows other users to view your desktop", and to "control your desktop", and sets up a password for security when others want to visit your desktop. So this setup it seems is to allow other computers to visit your computer. --And I did do this setup in all my three computers. But it looks like even without this setup, the non-host computer ought to be able to see the other computers which are in the local network. Or is there something I am missing in the set-up?

When one does Internet -> Remote Desktop Viewer -> Connect -> Find, then there should appear a list of the other computers online in the local network. That is not happening with my third computer, in which Ubuntu 8.10 has been freshly installed.

---

### Post by AFarris01 on 2009-04-09
im having a similar issue, but on 2 older 8.10 installs...however, I can't connect at all, even with remote viewing setup on both of them.

on my desktop, i cant see anythign else on the network, and on the computer i can see my computer registered, but when i try to connect, the viewer just silently crashes...

:(

hope you get a solution to your prob tho! I'll post any info i find that may be useful to u!

---

### Post by swarup on 2009-04-09
I think I have found out what the problem is. Remote Desktop Viewer's local auto address recognition only works when one is connected via wireless dongle. If one is connected via hard wire (i.e. RJ45), then the autorecognition of others on the local network, does not work.

I do not know why this is the case, but it is. The same computer when connected to the router via wireless, recognizes flawlessly all those present in the local network-- and the other computers can also see that computer. When the computer is connected to the router via hard wiring, then it cannot see anyone else in the local network, and no one else can see it.

Note: In the hard wired connection, if you manually type in the address of the other computer into Remote Desktop Viewer, then it connects just fine. But the autorecognition feature does not work.

---

### Post by asmoore82 on 2009-04-09
mDNS is limited to the local subnet by design,
does your router separate wired/wireless into different subnets?

---

### Post by swarup on 2009-04-09
> **asmoore82 said:**
> mDNS is limited to the local subnet by design,
does your router separate wired/wireless into different subnets?

I do not know. 
(1) How could I find this out?
(2) If indeed my router separates wired/wireless into different subnets, then is there a way around this so that wired and wireless connections will be able to see each other?

---

