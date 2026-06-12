---
title: "why is there no real time firewall gui?"
date: 2014-05-24
forum: Networking &amp; Wireless
---

### Post by thinking on 2014-05-24
Hi all,

maybe i miss something, but i cant find a firewall which allows me to allow/deny network traffic decisions in real time
using some kind of popup/gui.
i'm searching for something like zonealarm on windows. If a programm wants to use eth0 i want to be notified and
i can decide if its allowed or not.

the only linux-like variant of this is androids firewall without root
which, afaik, uses tun/tap interfaces to route the traffic to the app.
this would be a very valid approach so

is there really no gui which solves this problem on *nix?
if the answer is truly no, maybe anyone point me to resources on how to develop this gui on my own?
programming is not the problem but
i dont really know much about tun/tap and i have no idea how it should work - anyone can give the big picture here?
and what may be the differences between the android app and an ubuntu solution?

thx

---

### Post by TheFu on 2014-05-24
Looking for Windows-like solutions on Linux/UNIX will lead to frustration. It is a VERY DIFFERENT OS with extremely different philosophies.

UNIX is multi-user from the ground up, for the last 30+ yrs. Network controls are designed to be managed by "root", not end users. UNIX admins routinely manage hundreds of servers, so having a GUI is considered highly inefficient. Log files and log file analysis tools are what most professional Linux/UNIX administrators use.

There is only 1 real firewall on Linux - it is built into the kernel and called iptables.  EVERYTHING ELSE is just a different UI/GUI over that kernel module.  The UI/GUIs send requests to iptables.  The kernel either accepts and implements the requests or rejects them. The primary mode of feedback is to a log file in /var/log ... often, for security reasons, it is not allowed for those log files to be read by non-root users. 

I'm not saying that there isn't a place to do what you are asking - especially as more and more end-user-types start running Linux desktops.  It is just not part of the normal use methods until relatively recently.

Big enough picture?   Oh - and I wouldn't touch tun/tap methods in a firewall unless it was required for some other reason.  Linux bridging is very efficient, unless you load it in user-mode.  Then it sucks.

So ... how can you make a GUI?  Pick a language, pick a GUI library, then get to work.  Qt or GTK are the most likely for Linux desktop needs. These are cross platform GUI libraries, so if your back end is also cross platform, then managing Windows and OSX and other OS firewalls might be possible - though Microsoft and BSD firewalls are different from iptables.  Might want to include a test mode or a 5 min time-out mode, so when noobs lock themselves out, they can get back in. This happens A-LOT.

Anyway - hope that is helpful and provides a few ideas.

---

