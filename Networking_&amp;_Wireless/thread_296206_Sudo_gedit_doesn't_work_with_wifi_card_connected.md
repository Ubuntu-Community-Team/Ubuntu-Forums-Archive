---
title: "Sudo gedit doesn't work with wifi card connected"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by fdenes on 2006-11-09
Hi everyone. I've a problem with my wifi pcmcia card: I tried to install (and did it) the network administrator package with the result that the graphic interface freezed after login. Of course the command line was working, so I decided to remove the package. Ok...rebooted...same problem, but if I unplug the pcmcia card it logs without any problem.
Then I can plug my card and it goes fine, but when I type "sudo gedit /etc/fstab" the process cant continue and it goes in some kind of "loop" without asking for the password (and for anithing else).
Well...before installing network administrator everything was working fine, so...how can I roll back correctly the installation?

---

### Post by FrodoB on 2006-11-09
apt-get remove package_name

---

### Post by fdenes on 2006-11-10
yep...I know how to remove a package and I did remove network manager, but now I have the problem I described before

---

### Post by stream303 on 2006-11-12
Does gksudo gedit work instead?

---

