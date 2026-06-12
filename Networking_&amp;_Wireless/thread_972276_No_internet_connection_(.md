---
title: "No internet connection :("
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by tinnguyen123 on 2008-11-05
Hi im completely new to linux can anyone out there show me how to work my internet on linux..? im currently using my Window OS to surf the net for answer...

i have 2Wire SW1000 modem.. with DSL

When i start logging into ubuntu, the modem broadband link light turns off, and my local Networking Light turns off, and once inawhile the modem try to connect to its broadband thing...






also i cannot run anything on my CD/DVD driver, once i log into Ubuntu OS..

i try installing Warcraft and the system pop up "cannot find autorun program" as an error message..

---

### Post by Quarg on 2008-11-05
WoW wont work because ubuntu won't run .exe programs, it runs on a completely different kernel, so you can't install any windows apps straight to linux. however, if you emerge Wine from the ubuntu repository (System>Administration>synaptic package manager) I have heard that people have gotten WoW to work with Wine. as for your internet, I would guess that your modem driver isn't supported, make sure your using ubuntu 8.10. To help you any more, it would help a lot to have the manufaturer and model number of your modem, as well as the model of the P.C.

---

### Post by tinnguyen123 on 2008-11-05
oh i thought i provided the model number already..

uh.. its a [COLOR="Black"]**2wire**[/COLOR] kinda modem.. it is a 1000SW model..

my computer is a HP pavilion media center: a1657c...


oh not only warcraft 3.. its every kinda CD i try to put in my CD/dvd drive...

and it all say "Cannot Find AutoRun Program"

well when i put it in all Linux does is show the Icon of the CD i just put in and doesnt do anything else.. then when i right click and choose auto run or select something from the cd that's what it says..

oh if my modem have no way to use linux what modem model out there can i buy to use..?


hey thanks for replying btw..:)

---

### Post by Iowan on 2008-11-05
For what it's worth, [this]("http://ubuntuforums.org/showthread.php?t=961942") thread proclaims that the 2Wire SW1000 works on Intrepid.

I'd have you check */etc/network/interfaces* file, but I'm not sure what might have changed in Intrepid, and I don't have a machine running it - yet.

---

### Post by tinnguyen123 on 2008-11-05
dang it i feel so freaken dumb!! i dont know any of these new terms.. ubuntu, conical, wine, ahh!! >.<


sorry im trying to read and learn but there's so much.. i just needed a new OS cuz stupid microsoft keep restarting on me.. "BSOD" problem.. :(

---

### Post by Iowan on 2008-11-06
No one was born an expert.  Unfortunately, after you've been around awhile, you start throwing around terms like they're common knowledge. Ubuntu would be this Linux distro (distribution - AKA "flavor"), Canonical would be the "commercial sponsor of Ubuntu". WINE (Wine Is Not an Emulator) is a program that allows you to run Windows software on a "Unix-like" system.
 Feel free to ask about other terms - most folks here will either (try to) answer your question or provide a link to an answer. "RTFM" is not considered an appropriate response - and is a violation of the Forum Code of Conduct.

---

