---
title: "Firestarter to be automatically started without a password on Kubu Edgy boot"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by rautamiekka on 2007-06-06
At ubuntuguide.org you see how to make Firestarter start at **Ubu**'s boot, but you can find nowhere how to make it start at Kubu's boot so does anybody got an idea how to make it start without asking a password ?

---

### Post by bapoumba on 2007-06-06
[https://help.ubuntu.com/community/Firestarter]("https://help.ubuntu.com/community/Firestarter")
Is that the doc you are talking about?

Firestarter runs in background and is used only to configure the firewall rules. Why would you want it to open at boot ?

---

### Post by rautamiekka on 2007-06-06
Because without having Firestarter on I can't use Thunderbird to connect to my gmails

---

### Post by bapoumba on 2007-06-06
> **rautamiekka said:**
> Because without having Firestarter on I can't use Thunderbird to connect to my gmails
You should be. What is the problem ?

---

### Post by rautamiekka on 2007-06-06
Hmm, I already have myself added to sudoers so that I don't need password to open Firestarter, well, I do happen not need, but still Firestarter is not opening at boot.

---

### Post by kevdog on 2007-06-06
Firestarter is simply a program that modifies the iptables.  Once you are done using it, and close the program, it doesnt run in the background.  It never runs at startup.

---

### Post by rautamiekka on 2007-06-06
But still in any way without having Firestarter GUI running I can't connect to some places.

---

### Post by kevdog on 2007-06-06
Its likely you havent configured Firestarter correctly.  It simply allows incoming/outgoing ports to be open or shut.  These ports are static (meaning they are always open or closed and dont change their assignment dynamically).  I use guardog instead of firestarter, but it doesnt matter -- they both simply set the iptables file.  I would suggest that you need to do just a little bit more research (possibly as little as 20 minutes) on how to correctly use firestarter -- I know I had a lot of problems at first because I was stubborn and didnt read the documentation -- once I actually took the time to read it -- I mean really read it -- all my problems went away!

---

### Post by rautamiekka on 2007-06-06
I hope you're right

---

