---
title: "NetworkManager..."
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by geminias on 2007-08-02
Hi, I like Ubuntu 7.04 Fiesty, but the wireless networking is getting out of hand...  It randomly disconnects on occasion, and that wouldn't be so bad, except it doesn't reconnect too well.  Shutting down and restarting allows it to reconnect again.  But I mean, it's just so frustrating.  

I've tried semi-randomly punching these commands in to get a connection: 

ifdown eth1
ifup eth1
iwconfig eth1 mode managed  || mode monitor  #the reason I sometimes use this is cause I switch to monitor mode while running kismet and such.

Sometimes a combination of these will get it to reconnect.  The one that works best is killing NetworkManager and starting it back up again, but even that sometimes fails. 

Is there like a log file or something I can check to see what's going on?

P.S. My driver is ipw3945

---

### Post by geminias on 2007-08-02
Or what are the commands to connect to a specific network?  So I can get feedback on the process from the terminal window...

---

### Post by Sand Lee on 2007-08-03
Is this a Ubuntu only problem or does this happen on other distros/windows?

---

### Post by sekazi on 2007-08-03
I am having the same issue but never thought to do any of those commands. I would be listening to a music stream then all the sudden the connection is gone and I am less then 3 feet from the wireless router. It would never reconnect after that and if it does it takes several minutes. I have also found restarting the process or just restarting the system helps the most. 

I have no issues with Windows XP. I have found I cannot even connect to a unsecured wireless network at school.

I have a Dell Wireless 1370 Card using Broadcom 4318 Wireless drivers.

---

### Post by splintercellguy on 2007-08-03
To the OP, try the System Log app?

---

### Post by damir_1105 on 2007-08-03
Why don't you try 

```
sudo /etc/init.d/networking restart
```

when hang up

---

### Post by ugm6hr on 2007-08-04
@geminias:
It sounds like Network Manager is the culprit - I know it misbehaves with multiple chipsets (including yours) when used with WPA.

Try removing Network Manager (uninstall from Synaptic network-manager and network-manager-gnome)

Install Wicd (see my signature link).

Hopefully it will be more stable.

---

### Post by shoofy on 2007-08-07
I have exactly the same problem. It started about 2 weeks ago and I was usually able to reconnect using various different configuration changes or occasionally restarting services or rebooting. As of 2 days ago, all o fthese methods stopped working and I now can no longer connect wirelessly at all. The wired connection works fine.

Someone else with this problem in a different thread says that wicd didn't solve his problem, but I haven't tried it yet.

---

### Post by davycork on 2007-08-07
Hi all,

First post. I got so sick of re-installing Windows XP on my laptop. It seemed that each time I did, I was getting strange crashes by the time I had finished downloading updates!

Anyway, I gave Ubuntu a go and am very happy so far. Two gripes:

- Network Manager seemed unreliable. Wireless disconnecting, especially after hibernation. I replaced it with Wicd and so far it is perfectly reliable. The wireless connects seamlessly on its own on startup with no intervention.

- The touchpad is super-sensitive and causes spurious clicks. I'm off now to try to fix that.

Davycork.

> **ugm6hr said:**
> @geminias:
It sounds like Network Manager is the culprit - I know it misbehaves with multiple chipsets (including yours) when used with WPA.

Try removing Network Manager (uninstall from Synaptic network-manager and network-manager-gnome)

Install Wicd (see my signature link)

Hopefully it will be more stable.

---

### Post by shoofy on 2007-08-07
Wicd does seem to have made the wireless work. It's only been going for a few minutes now, but so far so good. I'll post back if anything changes.

---

### Post by shoofy on 2007-08-08
It just dropped the connection and wouldn't let me reconnect until I toggled the kill switch. Still doing better than NetworkManager did, but it's not a good sign.

---

