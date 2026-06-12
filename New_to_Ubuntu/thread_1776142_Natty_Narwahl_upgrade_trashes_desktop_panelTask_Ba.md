---
title: "Natty Narwahl: upgrade trashes desktop panel/Task Bar"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by Arikaree105 on 2011-06-05
I ran the Natty Narwahl upgrade, it did not go well on my old PE800 dell server... upgrade stalled after 5 hours (probably earlier, I pulled the plug at 5 hrs).

Rebooted and ran recovery option, boot presented "You are in Low Graphics" (or some such alert box), but upon continuing the sucker booted. 

All seemed normal, Except: this odd UNITY task bar appeared on the left margin, full of interesting but odd icons (lots of duplicates), so I went into COMPIZ settings and removed it. 

I now have NO desktop panel, aka Task Bar, on the upper border of my display. I can do nothing without it, even shutdown. Running Gnome display manager, not KDE or others.

How do I restore my traditional task bar? (Status bar on bottom border is gone as well, presume fixing task bar also fixes this.)

Sorry for the Noob question, this one is not in any of my several Ubuntu books.  [IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by TeoBigusGeekus on 2011-06-05
Alt+f2 and then
```
gnome-terminal
```
Give
```
sudo reboot
```
to reboot and when you log in choose ubuntu classic (I hope you don't have automatic login enabled).

---

### Post by Arikaree105 on 2011-06-05
Yes, I have auto login enabled. :frown:

possible solution: I did make /home it's own partition. So what's the worry if I reinstall 10.10?, besides being a little dramatic? I'm presuming that a reinstall leaves my /home... oh, wait, the new install won't have my old account, will it.  ](*,) I tried running my 10.10 install DVD, and selected Rescue a broken system, but that seemed ineffective. 

Well, shot myself in the foot. What's this UNITY thing anyway? The upgrade never asked if I wanted this.

---

### Post by garvinrick4 on 2011-06-05
ctrl/alt/f1
login:
sudo dpkg --configure -a
sudo apt-get update
If updates fine; (internet working)
sudo apt-get upgrade
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get dist-upgrade
sudo dpkg --configure -a
ctrl/alt/f7

## Let us know how it went: Just trying to get your upgrade to complete:
IN Natty can choose either Unity or Gnome Classic at login (button on bottom panel after clicking on user name)
Gnome Classic is what you are used to. (gnome2)

---

### Post by TeoBigusGeekus on 2011-06-05
If you can reach the terminal, give
```
sudo nano /etc/gdm/custom.conf
```
Find the line that says
```
automaticloginenable=true
```
and change it to false. 
Save, reboot, choose ubuntu-classic at login and post back with the outcome.

---

### Post by garvinrick4 on 2011-06-05
> I'm presuming that a reinstall leaves my /home... oh, wait, the new install won't have my old account, will itIF you had /home in a seperate partition at install put /home back in same partition if you
reinstall and do not FORMAT /home so as to leave it the way it is.
sudo blkid  (lower case L second letter)
sudo fdisk -l (lower case L)
##These will tell you partitions by uuid's with labels and sda#'s
## Can complete upgrade though live Cd also.

---

### Post by Arikaree105 on 2011-06-05
> **garvinrick4 said:**
> ctrl/alt/f1
login:
sudo dpkg --configure -a
sudo apt-get update
If updates fine; (internet working)
sudo apt-get upgrade
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get dist-upgrade
sudo dpkg --configure -a
ctrl/alt/f7

## Let us know how it went: Just trying to get your upgrade to complete:
IN Natty can choose either Unity or Gnome Classic at login (button on bottom panel after clicking on user name)
Gnome Classic is what you are used to. (gnome2)


Thank you!, will give it a try.... need to reboot and reload Narwhal. Will post results. I have auto login enabled, might give a bit of grief.

Here's hoping.... [-o<

---

### Post by Arikaree105 on 2011-06-05
SUCCESSFUL REPAIR :p, my many thanks to the many who guided me along.

the dpkg --configure -a reported 454 packages available for update, but when
I applied the various dpkg and apt-get commands, the results from each said quantity 0 to upgrades, changes, and even dist-upgrade. This tells me that on the one hand, the system thinks it has changes, but there's really nothing to do. Unless I interpret all this wrong, which is also likely.

The nano /etc/gdm/custom.conf was crucial to getting me into Gnome classic

Anyway, this message of thanks comes from my new Narwhal upgrade, and all seems well. (fwiw: I will keep my spare and seldom used Ubuntu distro close by, just in case I shoot myself again.)

Thanks, all, for your help and advice, and very cool expertise.

---

### Post by garvinrick4 on 2011-06-05
> This tells me that on the one hand, the system thinks it has changes,  but there's really nothing to do. Unless I interpret all this wrong,  which is also likely.
It just means the system is up to date and nothing left to do. It was according to what
part of the upgrade your system was in if that was going to work. It does not work all
the time but you were far enough along in upgrade process that she finished with a few
commands. The apt-gets on the end were just to make sure the dist-upgrade had completed. Enjoy.

---

