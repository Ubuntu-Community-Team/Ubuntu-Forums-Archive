---
title: "Keeping Firestarter running (inittab)"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by Dave232 on 2007-09-16
I'm new to Ubuntu/linux, but have used Unix for years (user, not admin).  I've installed "firestarter".  (Yes, I've read the various debates on it being necessary, or not.)  

I'm going to stay in the "yes, it *is* doing something camp".  When running the system monitor (before firestarter) there is clearly a bunch of inbound network traffic (that I'm not consciously requesting).  After starting firestarter, the inbound traffic drops close to zero.

So, running it seems to be a productive thing...?

However, after a fresh reboot, it doesn't look like "firestarter" is running.  I can launch the GUI via "System > Adminstration > Firestarter".  Afterwards, the "play button" icon in the the taskbar for the remainder of the session.  Prior to running the GUI, there's no such icon.

Yeah, I know that a simple icon probably isn't the best indicator of what's really going on.  So...

I found multiple references to "firestarter" being a service that would be listed and managed in the services program.  However, when I look in: System > Administration > Services, nothing that looks like "firestarter" is even listed.  Obviously, there's no corresponding checkbox to have it enabled.

Looking at "ps" (ps -ef | grep -i fire), I don't see anything that looks like a running process.  However, after running the GUI, "ps" shows the running process from that point forward.

There is a "firestarter" script in  /etc/init.d.  The script is complex enough to keep me from knowing what's really supposed to happen.

Any thoughts or help would be appreciated.

Thanks,

Dave.

---

### Post by ruibernardo on 2007-09-17
Hi Dave,

Firestarter is just a frontend of iptables (the real firewall). Basically it's just a script that sets up iptables as you defined when you ran Firestarter the first time (run the "Firewall Wizzard" on the Firewall menu in Firestarter if you didn't) and the other settings you set after on the GUI. It runs when you boot, and you don't see on the process list it because it already setup iptables and ended its job (it's the script in /etc/init.d/firestarter).

You shouldn't need the GUI on the gnome panel unless you want to change some setting (open/close ports). If you run the GUI, then yes, you will see a process of the GUI of Firestarter, which is a program that is in /usr/sbin/firestarter.

To verify if Firestarter did setup iptables, run on a console/terminal:

sudo iptables -L

If it didn't, then the output should be:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```If iptables did give you the this output, then run the "Firewall Wizzard" again, on the "Firewall" menu in Firestarter. If the output was a bunch of lines, then it is working. Search for "security scan" on Google and confirm it.

To set up Firestarter the right way take a look at -->[this page]("http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html")<--.

I hope that this isn't too much confusing :-? because it isn't that complicated once you understand it.

---

### Post by Caffeine_Junky on 2007-09-18
[ [COLOR="Navy"]_How-To: Firestarter on startup (better & safer way)_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=542756&highlight=firestarter")

This Link may be of interest aswell

cheers

---

