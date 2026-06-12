---
title: "&quot;it just doesnt work&quot;"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by hayim on 2006-08-03
this is really weird. 

Im connected wirelessly. It's all good, but i have to do it manually, with iwconfig, ifconfig and dhclient.

But the network-admin GUI simply does not work. It sees my card, but any changed i apply do nothing. I set it to a profile, and it immediately forgets! (this is really annoying coz my Ad Hoc network doesnt give DNS, so i needed to edit dhclient.conf for that).

Network Manager is similarly useless. It dosnt even see my card, says 'no network devices have been found'! And it loads on boot - could someone tell me how to stop that? Do i blacklist?

Has anyone else found the gnome apps totally usless? 

Also, where would i automate all these commands, so that dhclient runs on boot? 

Thx for the help.
Hayim

---

### Post by Buffalo Soldier on 2006-08-03
What helping these excellent people here some help in helping you. A detail description of your hardware is a good way to start. Try typing **lspci** at the commandline/terminal. It will usually list your hardware.

---

### Post by wylfing on 2006-08-03
@Buffalo Soldier - Um...that was incoherent :) . I think the jist of it was that we need more information.

@hayim - You pose many vague questions. Start with telling us which wireless card you've got -- or, even better, which chipset it's using. Your issues may be well addressed by simply shelling out $25 for a different wireless card. Not every card is equally supported under Linux.

---

### Post by Buffalo Soldier on 2006-08-03
> **wylfing said:**
> @Buffalo Soldier - Um...that was incoherent :) . I think the jist of it was that we need more information.Just woke up from my afternoon sleep :)

---

