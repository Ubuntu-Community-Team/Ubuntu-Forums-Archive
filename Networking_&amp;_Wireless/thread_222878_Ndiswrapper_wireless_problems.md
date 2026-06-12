---
title: "Ndiswrapper wireless problems?"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by BetaMaster on 2006-07-25
I have a Linksys WRT54G wireless PCI card. I followed the instructions on the wiki, and it seemed to work...But under Networking, rather than Wireless Connection showing wlan0 like it should, I'm seeing eth1. Obviously, it doesn't work. What did I do wrong? Should I write down what I did for you all? I honestly don't know what I did wrong, ndiswrapper seems to be working, bcmw54 (that's what it's called, right? I'm not at Ubuntu right now)...Anyways, bcmw54 seems to be present. So I don't know what else I could have done.

Thanks in advance.

---

### Post by BetaMaster on 2006-07-25
Is there a file I can edit to change the name? Stop Ubuntu for looking for eth1 for wireless, and instead look for wlan0?

---

### Post by BetaMaster on 2006-07-25
Does nobody have any tips or advice for me?

---

### Post by Max Velocity on 2006-07-25
I did come across something like that a while ago, if you check out the wireless guides you should be able to find it, sorry I could not be much of help.

---

### Post by mpvano on 2006-07-26
Why do you need to change it? I believe what you describe is the way it's intended to work in Dapper.

The names of interfaces are controlled in several different places (usually by the program or script that loads them). There are several conflicting viewpoints of what the names should be. Dapper seems to try to consistently rename the first wireless adapter as eth1 (but some startup scripts, drivers, networking control panels and tools override this).

Is this actually causing a problem for you? If so perhaps explaining what the problem is might allow someone to suggest a solution.

If you're not SURE which interface is your wireless interface, I suggest looking at the description in the System:Administration:Networking control panel.

If you're doing something more complicated, try looking at the output of the iwconfig command by opening a terminal window and typing "sudo iwconfig". After entering your password, it will list the adapters in your system and tell you which have wireless support.

If you REALLY understand the network startup system and are trying to do something more complicated, then read the various system documents and man pages about ifrename, iftab, the module loading system, and the device system (it's not the old static UNIX device naming system any more).

Remember that there's no way to tell if an online FAQ you are reading is up-to-date, true for anyone but the writer's local installation's peculiarities, or ever was correct in the first place. Much information here and elsewhere about wireless networking is misleading, incomplete or just plain wrong.

hope this helps....

Mario

---

