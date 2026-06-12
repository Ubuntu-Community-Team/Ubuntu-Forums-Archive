---
title: "Another user is trying to view desktop"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by Wheel on 2010-01-22
Hi all,

I'm brand new to Ubuntu.  (Installed 10 days ago.)  
Using Karmic Koala 9.10
Dual boot w/ Vista H.B.
So far, I'm mostly reading to learn my way.

Question(s):  Shortly after boot-up today, this message popped onto my desktop:

"Another user is trying to view your desktop.  A user on the computer 95-181-13-208.goodline.info is trying to remotely view or control the desktop.
Allow?  Deny?"

This message repeated 3 more times over the following 45 minutes or so, with a different number in each case.

In each case I selected "Deny" since I didn't understand what it meant.

What exactly does this mean?
Should I be concerned about this?
Ignore it?
Allow it the next time?

As to "users":  The only users are root and my own account.  I have only one PC so there are no other users on my "home network".

Thanks for any help offered,

Wheel

---

### Post by nothingspecial on 2010-01-22
I don`t know how or why that happened but I would immediately change your wireless router key and your accounts password.

---

### Post by Hospadar on 2010-01-22
Edit: I would also do as above, furthermore, if your router allows remote configuration, be sure that is disabled.  Also make sure there is no port forwarding (if you don't know what that is, you don't want it) set up on your router.

sounds like someone is trying to view your desktop

The deal is, many remote protocols (in fact almost all network protocols including http, ftp), ssh, vnc (which is the protocol in your case), and others use standard ports (which is an important feature of such protocols).

many individuals in the business of illegally gaining control of computers for the serving of spam and malware, along with the collection of private information attempt to connect to these services using random passwords and usernames, or on the hope that they will not be protected, in order to gain access to machines.

Unless you use a remote desktop, the best thing to do would be to go to System->Preferences->Remote Desktop and just disable it.  If you do use remote desktop, add a good password in the same place.

---

### Post by JiuJitsu500 on 2010-01-22
Concerned? I don't know, probably not, but you can try totally turning off all remote desktop apps (system > preferences) and removing them from startup (system > preferences > startup apps) should they be there...

Install BUM (boot up manager) too and see if you put something there on accident, but beware of using this... I got rid of my re-boot script somehow a while back and the computer only turned off, never restarted... I had to manually turn it back on... as well as a plethora of things you don't want to happen. But, check to see if any remote viewing things are on there. You can get it form the software center, or the easier command line:

sudo apt-get install bum

And I can see the annoyance, but it might be from somewhere well outside your home group, or a bug.... or a ghost in the machine (random seemingly generated from no where bits of code that come and go sometimes)... Crazy talk :)

EDIT* and two other people already posted before me... sweet.... definately change the passwords to everything internet related... good point :)

---

### Post by thatguruguy on 2010-01-22
You may have gotten a trojan on Vista.  Do you have a fixed ip address? Do you have the same username and password on both Vista and ubuntu?  Have you checked to see if anyone is logging onto your computer remotely when you're using Vista?

---

### Post by Wheel on 2010-01-25
Thanks to nothingspecial, Hospadar, JiuJitsu500 and thatguruguy for all of your helpful suggestions.

I have disabled remote access (on both Ubuntu and Vista).
I have also disabled remote access via startup programs in System-Prefs.
I have changed all system related passwords.  Just for good measure, I even changed passwords to financial sites.
Comodo reports no intrusions on my Vista partition.
And AV and several anti-spyware scans all show Vista as clean.

Looks like I'm in the clear...:)

Wheel

---

### Post by nothingspecial on 2010-01-25
If you notice any related, strange behaviour, keep us posted.

Cheers.

---

### Post by tom.swartz07 on 2010-01-25
> **Wheel said:**
> Thanks to nothingspecial, Hospadar, JiuJitsu500 and thatguruguy for all of your helpful suggestions.

I have disabled remote access (on both Ubuntu and Vista).
I have also disabled remote access via startup programs in System-Prefs.
I have changed all system related passwords.  Just for good measure, I even changed passwords to financial sites.
Comodo reports no intrusions on my Vista partition.
And AV and several anti-spyware scans all show Vista as clean.

Looks like I'm in the clear...:)

Wheel

From what you described, it looks like you just had someone else on the network trying to VNC on to your computer.

In Ubuntu, if you go to system>preferences>remote desktop, you could edit those settings. You have 'user must confirm each connection' checked. Just change it to 'password protected', and use a strong passoword (upper and lowercase, and numbers)

That should stop the problems. Either that, or find who's spooking on your network to connect and tell them to stop.


Kudos on changing all the passwords on your important things though.

---

### Post by Wheel on 2010-01-27
Thanks for chiming in tom.swartz07.

Since I have disabled both "Allow other users to view" and "Allow other users to control the desktop" all other options are greyed out. 

I had already checked the box at "You must confirm each access to this machine".
And after temporarily re-enabling "Allow others to view", I have added a password here. 
(Then disabling it once again.)

(I've gotten pretty good at using arcane passwords having ridden the Windows train for a few years.  Between my interest in writing and languages in general, I have come up with a system of apparent gibberish that I can understand.)

I suspect that having "must confirm access" checked before this attempted intrusion is what put the warning on my screen in the first place.  Otherwise, that attempt may well have been successful.

...I suspect...

This brings me to the crux of the problem: ignorance.
I know just enough about Linux to realize I know next to nothing.
If you wield ignorance like a broadsword, you may get slashed with the scalpel when you're not paying attention.

At least I know the cure.  Study and learn a little; experience and learn more.

Forums like this are invaluable.

Thanks again to everyone.

---

