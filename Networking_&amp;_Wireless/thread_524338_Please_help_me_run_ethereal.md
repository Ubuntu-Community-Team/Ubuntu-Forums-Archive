---
title: "Please help me run ethereal"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by dudi.dalal on 2007-08-13
I'm very new user of Ubuntu I might ask a silly question.

I want to install ethereal at my ubuntu 7.01 (running under dual core intel)

according to the forum I did:

$sudo apt-get install ethereal
$sudo apt-get install ethereal-common

but when I run:

$ethereal

it write:
bash ethereal: comand not found

when i run:

$gksudo ethereal

It dose nothing

When I'm doing:
$which ethereal 

it writes nothing

Please help me 
Thanks

---

### Post by eentonig on 2007-08-13
wasn't ethereal chaged into Wireshark?

If I check the repo.
>  apt-cache search ethereal
ethereal - dummy upgrade package for ethereal [COLOR="Red"]**-> wireshark**[/COLOR]
ethereal-common - dummy upgrade package for ethereal **[COLOR="Red"][COLOR="Red"][COLOR="Red"]-> wireshark[/COLOR][/COLOR][/COLOR]**
ethereal-dev - dummy upgrade package for ethereal -> [COLOR="Red"]**wireshark**[/COLOR]


So, yes. The new projectname is wireshark. Can you try this as a command?


Damn, I just realized that it's been ages since I used a Sniffer.

---

### Post by heimo on 2007-08-13
It should add itself to your application menu - probably as a wireshark, which is what ethereal is called nowadays. You can also try to run gksudo wireshark on command line.

---

