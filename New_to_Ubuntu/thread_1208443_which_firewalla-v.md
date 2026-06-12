---
title: "which firewall/a-v?"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by bodyharvester on 2009-07-09
just curious, i know that linux distros can still get worms and such but which firewall/a-v stuff should i use?

[www.pctools.com]("http://www.pctools.com") has a free firewall/a-v/behavioural protection

but would they work with ubuntu? what about clamav which i read about?

what do you guys recommend?

also i liked the look of the latest msn messenger, is there any messenger app which gets close that i can download?

thanks again :)

---

### Post by Zzl1xndd on 2009-07-09
IMHO an anti-virus isnt really needed.

There is a built in Firewall with Ubuntu and nothing beats a good router.

AMSN is probably the closest.

---

### Post by MrWES on 2009-07-09
> **bodyharvester said:**
> just curious, i know that linux distros can still get worms and such but which firewall/a-v stuff should i use?

[www.pctools.com]("http://www.pctools.com") has a free firewall/a-v/behavioural protection

but would they work with ubuntu? what about clamav which i read about?

what do you guys recommend?

also i liked the look of the latest msn messenger, is there any messenger app which gets close that i can download?

thanks again :)

The standard firewall is ufw (uncomplicated firewall) and the gui is gufw -- pretty easy to use and setup if needed.

[http://packages.ubuntu.com/intrepid/gufw]("http://packages.ubuntu.com/intrepid/gufw")

~Bill

---

### Post by bodyharvester on 2009-07-09
thanks, i searched ubuntus help thing and saw firestarter, i think thats the one thats active now but using "shieldsup" as suggested in the help files my computer has perfect security :)

---

### Post by alexlafreniere on 2009-07-09
An antivirus is generally not needed on Linux. The default firewall is sufficient for home users, and as long your computer is behind a hardware router as one poster mentioned, you're covered.

---

### Post by winjeel on 2009-07-09
whilst browsing through the Synaptic Package Manager I wouldn't have known that gufw was a firewall program. Glad I stumbled on this thread, and glad that there is a Synaptic Package Manager to get it in seconds!

---

### Post by Paddy Landau on 2009-07-09
> **bodyharvester said:**
> just curious, i know that linux distros can still get worms and such but which firewall/a-v stuff should i use?
You don't need antivirus on Linux. The built-in firewall is already perfect IMO.

See [post 20 in this thread]("http://ubuntuforums.org/showthread.php?p=7587142#post7587142").

Antivirus products in Linux tend to test for Windows-based viruses, since that's all that's really out there.

> **bodyharvester said:**
> i liked the look of the latest msn messenger, is there any messenger app which gets close that i can download?
My daughter is an MSN addict, and she likes emesene (download it with Synaptic Package Manager). It's not an exact look-alike, of course, but it has all the required functionality.

---

### Post by Ascenti0n on 2009-07-09
I have Gufw installed but as others have stated, Linux comes with great protection built in called 'IPTABLES'. Programs like UFW/gUFW (by Ubuntu) and Firestarter, all use IPTABLES.

IF you have a router, these normally come with firewalls, sometimes referred to as 'hardware firewalls'. This would be like a first line of protection.

Linux and IPtables, would be like a second line of protection, and although you could have additional firewalls, I don't see any benefit.

You are already well protected.

---

### Post by 3rdalbum on 2009-07-09
> **bodyharvester said:**
> thanks, i searched ubuntus help thing and saw firestarter, i think thats the one thats active now but using "shieldsup" as suggested in the help files my computer has perfect security :)

Just in case you want to know a little more about your system:

Firestarter isn't a firewall, and neither is UFW. They just provide a way to tell the inbuilt Linux firewall (IPtables) what to do. UFW and its graphical counterpart, gUFW, are much easier to use than Firestarter. Not as powerful, but much less complicated.

A default installation of Ubuntu will not listen to any incoming connections anyway, so you'd likely get the same result in Shields Up! as if you didn't install a personal firewall. That is, unless you had installed any server software.

Finally, many broadband routers already contain firewalls that protect your whole network. In that case, you don't need a personal firewall unless you don't trust your own network traffic - and if you don't trust your own network traffic you've got bigger problems! :-)

---

### Post by lovinglinux on 2009-07-09
I recommend that you read the [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial, to understand how things work in the Linux world.

A few tips:

- You don't need to run Firestarter all the time to be protected, because it is, like ufw/gufw, just a tool for configuring the real firewall (iptables). Additionally, running Firestarter all the time might be a security risk, due to administrative privileges requirements.

- [www.pctools.com](www.pctools.com) produces Windows programs, which do not run on Linux. Although, there is a Linux program, called Wine, that creates a Windows compatibility layer, allowing to run some programs. Nevertheless, you shouldn't, imo, run security tools through Wine. There are plenty of security programs already installed on Ubuntu and you can install several others through the official repositories.

---

### Post by MrWES on 2009-07-09
> **Ascenti0n said:**
> I have Gufw installed but as others have stated, Linux comes with great protection built in called 'IPTABLES'. Programs like UFW/gUFW (by Ubuntu) and Firestarter, all use IPTABLES.

IF you have a router, these normally come with firewalls, sometimes referred to as 'hardware firewalls'. This would be like a first line of protection.

Linux and IPtables, would be like a second line of protection, and although you could have additional firewalls, I don't see any benefit.

You are already well protected.

Correct iptables is installed by default, but have you ever attempted to write iptable rules from the command line:
```
sudo iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
```

Using Gufw is much much easier for the average user, and that's what it's designed for -- Uncomplicated FireWall -- ufw.

Bill

---

