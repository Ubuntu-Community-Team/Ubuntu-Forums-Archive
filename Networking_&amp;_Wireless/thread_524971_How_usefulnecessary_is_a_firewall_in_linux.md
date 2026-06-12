---
title: "How useful/necessary is a firewall in linux?"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by fizikz on 2007-08-13
In Windows, I would not do anything online without a firewall like ZoneAlarm, but I'm not sure if a firewall is necessary in linux. Many linux users I've talked to seem to think that a software firewall is all but useless. I know there is Firestarter available as a firewall for Ubuntu, but I'm not looking for something just to give me a false sense of security, if that is in fact the case. I did all the tests at ShieldsUp! and my Ubuntu system gets a perfect score without any firewall installed (to my knowledge). Admittedly, those tests seem to be targeted for Windows machines, but the question remains: is there any merit to a firewall in linux?

---

### Post by misfitpierce on 2007-08-13
Well it's not really needed to be honest as the chances you get hacked are 1 in a billion unless playing in bad IRC rooms or something of the sort. A firewall can be good on any OS though and ubuntu comes with one built in known as IPtables... Download firestarter to have a GUI to edit rules of the firewall. It's leightweight and barely touches ram and runs great.

 I personally do not use one... I just use the built in firewall on router and it blocks out everything I dont need.

---

### Post by fizikz on 2007-08-13
Well, my laptop is connected wirelessly through the modem/router at home, so I do have some sort of hardware firewall when I'm at home. In public areas, I'm not sure how secure my setup will be. But judging from the information I've found so far, installing a firewall seems to be a very optional thing in linux, as opposed to a necessity in Windows. So I suppose I'll hold off on the firewall for now.

---

### Post by Darkhack on 2007-08-13
I use Firestarter to edit the permissions however the Linux firewall (iptables) is constantly running all the time.  It isn't necessary to run Firestarter in the system tray in order to have the firewall turned on.  This seems to be a misconception by some people.  A firewall is always necessary.  Thankfully with Linux you don't have to worry as much about it since it is built into the kernel and programs like GuardDog and Firestarter are just GUI tools to help edit the permissions instead of the complicated "iptables" command.

---

### Post by fizikz on 2007-08-15
That makes sense. Thanks for clarifying, Darkhack.

---

