---
title: "Linux and System Maintence"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by rdmike on 2009-01-20
Hi all,

I'm a new Linux/Ubuntu user and am enjoying the transition. I am curious though whether I need to do the same things I did in Windows to keep things running smoothly? For example, I had, in Windows, an AV/Firewall, defrag program, CrapCleaner, etc to keep things running smoothly. Are all these thngs still necessary now that I'm using a Linux OS? If not, what is or isn't needed? Thanks!

---

### Post by ugm6hr on 2009-01-20
Generally speaking, nothing is needed.

If you find your self low on HD space, there is a How-to on recovering space used by previously downloaded updates etc, but I don't do anything other than empty my Trash every now and then.

---

### Post by Paddy Landau on 2009-01-20
All you need do is clear out your Deleted Items ("recycle bin") on a regular basis, and do the updates whenever prompted (usually daily, but they're fast).

All the rest is for Windows users only.

Welcome!

---

### Post by Locke_99GS on 2009-01-20
In general, no. 

You may want to sort through synaptic periodically, and remove things you no longer use. The occasional *sudo apt-get autoremove*, and *sudo apt-get autoclean*.

There are a few crapcleaners for Linux OS's, but most people would have no use for them.

Antivirus isn't really needed, and the firewall is built into the kernel (iptables) - incoming ports closed by default. Most people won't need to mess with the firewall settings, but if you need to, *ufw* and *firestarter* are good frontends.

The nature of natively linux filesystems means that defragmenting isn't required. The system will, however, check the disks periodically at boottime.

---

### Post by lykwydchykyn on 2009-01-20
Keep up with your updates, particularly if you are running any network services.

---

### Post by donkyhotay on 2009-01-20
As mentioned before, you don't need to defrag, use an anti-virus, configure your firewall, or any of those annoying things you learn to do with windows. Yes, it's a little unnerving at first thinking you're computer is wide open to attack. Just sit back though and remember linux is done *right* and doesn't need all that junk to fix flaws that shouldn't exist in the first place. Once you get used to it, it becomes annoying to go back and have to mess with all that stuff again. The most you need to do is update your software but synaptic will take care of that for you and will update all programs just not the ones from a specific company (like usually happens with windows updaters).

---

### Post by OldTimeTech on 2009-01-20
Welcome to Ubuntu.

Linux tends to do the maintenance for you.  After every 30 boots it runs a check disk before booting into the login.  When you boot ubuntu up, iptables are already running and they are your firewall, if you want a gui for this it would be firestarter.  Mostly Linux takes care of itself.

---

### Post by rdmike on 2009-01-20
That is just too awesome!

Woohoo!

In the spirit of the recent holiday, and without any negative connotations intended, may I offer a hearty "free at last?" :popcorn:

Thanks for all the great replies. This forum, and its members, have been very helpful to me during my period of transition. I appreciate it!

---

### Post by Paddy Landau on 2009-01-20
If you want to get paranoid, here are four extra things you can do occasionally (run these commands from terminal).

1. Clean up old installation files:
sudo apt-get clean

2. Remove old redundant dependencies:
sudo apt-get autoremove

3. Clear old backup files:
sudo rm /var/backups/*

4. Delete old OpenOffice backup files:
rm ~/.openoffice.org/3/user/backup/*

But, as has been pointed out, these are generally unnecessary, unless you have a small hard drive and space is at a premium.

---

### Post by perlluver on 2009-01-20
Check this out, it does a great job of explaining: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812).

---

### Post by novafluxx on 2009-01-21
Very good thread with good resources! Thank you all!

---

