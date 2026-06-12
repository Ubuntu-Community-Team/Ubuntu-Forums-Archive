---
title: "Firestarter and firewall launch at startup"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by Razmear on 2009-03-18
Does Ubuntu's firewall start automatically at system start or does it have to be started manually? 
I have FireStarter installed and manually launch it when starting the system, but I'm not sure if it's just reporting the status of the firewall or if my action is needed to start the firewall program. 
If FireStarter does have to be launched, is there a way for me to add it to the equivilent of the Windows Startup Group so it launches automatically, and without my needed to enter a password. 

Thanks
eb

8.10

---

### Post by BOZG on 2009-03-18
Firestarter is not actually a firewall, it's a graphical front-end for Ubuntu's built in firewall iptables, that allows you to change settings.  iptables itself should boot automatically at start-up.  It's not necessary to have Firestarter start-up automatically unless you want to look at network activity.

If you do want it to run at start-up, go to System->Preferences->Sessions and click Add.  Set Firestarter as the name and the command as "gksudo firestarter".  Because it needs to be run as root, you'll have to enter your password each time.

---

