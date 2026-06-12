---
title: "Ping problem"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by MaZZly on 2006-11-15
Hi

i play warcraft 3 on my free time, and i only play custom games, but there are often laggers who will leave after a while couse of bad ms. To prevent leaving i ping them in "pre-game" with a program called "wc3banlist" to filter out the "laggers"
i play and ping from my xp-machine

the problem:
always it only gets respond (pong)from the 3-4 first people (out of 12), may it be that my ubuntu machine blocks the ping/pongs out?, in firestarter i have allowed ping & pongs under preferences/icmp-filtering

are there any ports that may need to be forwarded to my computer to get the pongs?

setup:
internet->modem->unbuntu->my xp machine

thanks in regards
//MaZZly

---

### Post by MaZZly on 2006-11-16
it seems to be like this:
1-3:d i recieve pong from 
4:th t/o (timeout)
5-12:th t/o (timeout)

---

### Post by FrodoB on 2006-11-16
Maybe those other people's machine are set to ignore pings, most are.

Can you ping them manually?

---

### Post by MaZZly on 2006-11-19
well it cant be that always the 4:th and the 6 last player have it blocked

when my friend tries to ping he gets response from almost all the players..

its always the same people that are t/o

---

### Post by FrodoB on 2006-11-19
I see. Is wc3banlist a script or program that you made or a closed source program, or do you already know that it, is not the issue?

---

### Post by MaZZly on 2006-11-25
[www.wc3banlist.de](www.wc3banlist.de)
The Wc3banlist program uses ICMP(normal ping) and i have selected firestareter to allow ICMP.. but maybe my server doesnt understand to route the ICMp to my Comp..

under "ICMP-flitring" in firestarter is there anything other than "echo request" & "echo reply" i need to have allowed for pings to work?


PS. it is always the same players(slots) that are "t/o", though i play with different persons each time, before i got the server there was only 1 or 2 that had t/o and those were in random slots.

---

### Post by MaZZly on 2006-11-27
is there anyway i can try to ping several sites in a row like google to see if it responds the same way (like when pinging in Warcraft)

---

### Post by koenn on 2006-11-28
```

for SITE in www.google.com www.playboy.com www.ubuntu.com ; do 
ping -c 2 $SITE; 
done;

```

pings several sites in a list. You can add more sites. site names can be replaced with IP adddresses
pings every site 2 times ( '-c 2'). Replace '2' with any other number if needed

---

### Post by MaZZly on 2006-11-28
was that script made for the ubuntu or the xp machine?
tried it on my xp machine but it returned me an error: "unexpected SITE"

how to get that working from the winxp machine?

i believe that the server doesnt route all the pongs to my xp machine(to the program).. couse its always the same slots(gameslots in wc3) that "doesnt respond" on my pings

---

### Post by MaZZly on 2006-12-01
any ideas someone?

P.S i havent got any router.. it worked nice pinging before i put the server as firewall :/

---

### Post by MaZZly on 2006-12-23
does ubuntu have some built-in protection for ping/pong attacks? since it always blocks after 4-5 pings..

---

### Post by hansoffate on 2007-04-17
Sorry to bring an old post back up, but does wc3banlist work on ubuntu?  I really don't care that much about pinging.  I just want to be able to determine origin and be able to ban people.   IF that works, there is no reason to stay on windows anymore.

Thanks for the help,
Hans

---

### Post by jonallport on 2007-04-18
Sounds like IDS shutting you down.

That behavior is typical if there is Intrusion Detection on your gateway.  This utility of yours will look v.suspicious to it as you are pinging multiple hosts as an intruder may do to 'feel' round the network, hence it will respond to this behavior and deny any further pings.

---

