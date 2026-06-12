---
title: "help, net almost down"
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by donkey42 on 2007-11-22
help pwease

only a few sites load & email works (both send & receive)[ot]luckily Ubuntuforums has loaded this time[/ot]

i think i need to clear Swiftweasel cache, however, i cleared it graphically & still nothing, how can i cler cache from console ?

this may be connected to me increasing my APT cache by adding```
APT::Cache-Limit "16777216";
```to my 70debconf in /etc/apt/apt.conf.d because i had a few sources & couldn't get GNU Radio to work (i've attached my sources)

BTW: using Feisty & i'm very :swear:ed off, any ideas as to what the problem could be, i also booted a LiveCD of Edgy & still having problems, thought it could be filter but mail works, may also be DNS as i use OpenDNS's primary as my primary & my ISPs primary as my secondary, could this be a problem ?

FYI: i'm disabled & brain damaged which makes it very difficult to swap ADSL filters

---

### Post by xeth_delta on 2007-11-22
From what you wrote I understand that you are having the same network problems on both, your system installation and a live cd. If that is the case I would guess it is an ISP or DNS problem.

By the way, **/etc/apt/sources.list** should not affect your network performance. It is a configuration file where information on ubuntu repositories is kept. You don't need to edit this file to change your network configuration. Repositories in turn are servers from which you can download and install software on your Ubuntu machine.

Xeth

---

### Post by donkey42 on 2007-11-22
[quote=Xeth]I understand that you are having the same network problems on both, your system installation and a live cd.[/quote]yeah[quote=Xeth]If that is the case I would guess it is an ISP or DNS problem[/quote]thank you Xeth, i'll try using both OpenDNSs DNS, failing that, i'll ring my dad & ask him to throw this :swear:ing thing through the window, but it's cold, so i'll think about that

BTW: if sites don't timeout they sometimes load eventually, thank you

---

### Post by xeth_delta on 2007-11-22
As I said, it might be an ISP problem, and in that case they will probably fix it soon, just be a bit patient. It happens sometimes.

If not, write here again, and we'll try to find out what's wrong.

Xeth

---

### Post by donkey42 on 2007-11-22
[quote=Xeth]As I said, it might be an ISP problem, and in that case they will probably fix it soon, just be a bit patient. It happens sometimes.[/quote]yeah, thankies[quote=Xeth]If not, write here again, and we'll try to find out what's wrong.[/quote]thank you

FYI: i'm good at being bored, thank you again ](*,)

---

### Post by donkey42 on 2007-11-22
fixed, as i was bored i removed over 650 Mb of stuff i don't use and it works, so, you can install too much on *nix

BTW: i've only got just over 1500 packages installed :roll:, i know this fixed it because i didn't reboot or restart networking, i just removed the packages & it worked

Edit: thankies Xeth

---

### Post by xeth_delta on 2007-11-22
You are welcome.

[QUOTEfixed, as i was bored i removed over 650 Mb of stuff i don't use and it works][/QUOTE]
Could it have been that your hard-disk was full?

You can check how much free space you have on your partitions by typing in a terminal:
```
df -h
```

Xeth

---

