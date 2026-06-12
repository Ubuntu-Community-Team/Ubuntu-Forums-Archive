---
title: "Knetworkmanager starts then disappears"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by oliwally on 2006-12-01
I'm using Knetworkmanager (and KDE Wallet) on my Dell D820 to connect to my wireless router. I have put a link in .kde/Autostart to make Knetworkmanager run as I log in. It has always worked beautifully, connecting as I log on and showing an icon in the system tray that it's connected.

However, for the last week Knetworkmanager has started as normal, then disappeared without connecting to the network with no icon in the system tray. To fix it I have been killing the Knetworkmanager process through KDE System Guard, then restarting Knetworkmanager through the Kmenu. This works, but it's inconvenient.

Why is Knetworkmanager being pushed into the background without running properly? Is there a better way of making Knetworkmanager start at login? Is there a way of giving priority to the program so it doesn't get pushed into the background (if that's what's happening..)?

It doesn't always behave like this. Sometimes it works as it should.

---

### Post by oliwally on 2006-12-04
bump ;)

---

### Post by oliwally on 2006-12-07
> **oliwally said:**
> I'm using Knetworkmanager (and KDE Wallet) on my Dell D820 to connect to my wireless router. I have put a link in .kde/Autostart to make Knetworkmanager run as I log in. It has always worked beautifully, connecting as I log on and showing an icon in the system tray that it's connected.

However, for the last week Knetworkmanager has started as normal, then disappeared without connecting to the network with no icon in the system tray. To fix it I have been killing the Knetworkmanager process through KDE System Guard, then restarting Knetworkmanager through the Kmenu. This works, but it's inconvenient.

Why is Knetworkmanager being pushed into the background without running properly? Is there a better way of making Knetworkmanager start at login? Is there a way of giving priority to the program so it doesn't get pushed into the background (if that's what's happening..)?

It doesn't always behave like this. Sometimes it works as it should.

Any ideas anyone?

---

### Post by K0LO on 2006-12-11
Oliwally:

I'm having a similar problem as described [in this thread.](http://www.ubuntuforums.org/showthread.php?t=287095)

I think it's a bug caused by some kind of timing issue. I've been able to work around it by hibernating the machine instead of shutting down. When resuming from hibernation it always connects 100% of the time.

---

### Post by dearephesus64 on 2006-12-12
I had a similar problem with spotty performance from knetworkmanager.  I made a shortcut in .kde/Autostart, and it seems to be working so far.  

When it was non-functional, I checked in KSysGuard and there were *three* instances of it running.  My guess is that there was one restored from a previous session, one started at the the session start, and one from me trying to run the program from menu because I didn't see my network icon in the tray.  Just a guess.  

Killing all instances and running it again works, but like oliwally said, it's inconvenient.



Does anyone know how to have *buntu automatically kill a process, no matter whether the computer is shut down, suspended, or hibernated?  All the problems with knetworkmanager I've heard of might be addressed by that.

---

### Post by k3nt1 on 2006-12-13
Hi all,

I have exactly the same problem. It starts normally, then KDE wallet pops up for my master password while the icon of knetworkmanager disappear. However, the space needed to store the icon keeps being there (i.e. there is a blank space between the surrounding icons). I must then kill the application and restart it before being able to connect.

Any idea to solve that ? A workaround may be fully satisfying.. :-)

Thanks in advance.

Cheers.

---

### Post by dearephesus64 on 2006-12-14
I can address the wallet problem with what worked for me, at least.  If you don't have any other sensitive information in your wallet (e-mail passwords, etc.) and you don't mind the security risk, I just set up my wallet with no password.  I left the password field blank when kwallet asked for one, then the wallet manager only asked me once if I wanted to always allow knetworkmanager access to the wallet.  Since I added the shortcut in .kde/Autostart, It's been working fine for a few days now.

I don't consider my network key particularly sensitive information-- my elderly neighbor probably isn't pirating my internets, so I'm not worried.  I don't know of a more elegant solution than that, though.  Perhaps there is provision in kwallet for multiple wallets with different kinds of information?  Cheers, k3nt1.  I hope this is fun for you and not just frustrating. :D

---

### Post by K0LO on 2006-12-14
I have always used a blank password for kwallet and still have the same problem as described above.

---

### Post by oliwally on 2006-12-15
Thanks for the replies folks. I'm glad, but sad, that I'm not the only one with this problem. Everything described here sounds very much like what's happening on my 'puter.

I also use the blank password method for Kwallet. And still, the same problems. Sometimes it works well, sometimes I have to kill Knetworkmanager through Ksystemguard and then restart it in order for it to kick in. Haven't yet tried to move between networks.

Looks like someone with an in-depth knowledge of knetworkmanager etc. needs to join our discussion. 

Any takers? (please)

---

### Post by K0LO on 2006-12-15
Keep in my the workaround mentioned in my previous post. If you are running knetworkmanager on your laptop then just hibernate your machine instead of shutting down.

When doing this I find that knetworkmanager connects automatically 100% of the time.

---

### Post by oliwally on 2006-12-18
> **K0LO said:**
> Keep in my the workaround mentioned in my previous post. If you are running knetworkmanager on your laptop then just hibernate your machine instead of shutting down.

When doing this I find that knetworkmanager connects automatically 100% of the time.

I found that I don't have to shut down or hibernate, I just simply kill the knetworkmanager process using ksystemguard, then start it again through kmenu and connect to the network.

But still, no permanent or good solutions.

---

### Post by K0LO on 2006-12-18
That's not what I was trying to say. My point is that the problem goes away if you always hibernate your machine. You can go into and out of hibernation all you want and knetworkmanager will always connect flawlessly.

If instead you shut down your machine, the problem re-appears.

So if you're running a laptop and you get in the habit of hibernating the machine instead of shutting it down then you will no longer have this problem with knetworkmanager. At least that's how it's been working for me. End of problem.

---

### Post by oliwally on 2006-12-24
> **K0LO said:**
> That's not what I was trying to say. My point is that the problem goes away if you always hibernate your machine. You can go into and out of hibernation all you want and knetworkmanager will always connect flawlessly.

If instead you shut down your machine, the problem re-appears.

So if you're running a laptop and you get in the habit of hibernating the machine instead of shutting it down then you will no longer have this problem with knetworkmanager. At least that's how it's been working for me. End of problem.

Oh, I see. I may give that a go. Haven't really tried hybernating yet. Thanks for the hint.

---

