---
title: "[SOLVED] adsl ethernet alcatel speedtouch no connection"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by ubu-lemon on 2007-10-23
hi,

i'm completely new to linux -ubuntu 7.04-
(yeah chose a wrong usersname, but it's so cute, can't help it :roll:)

Instalation worked out, but there are still problems (ATI for example, no sound, no movies playing, no printer, etc)
first step to solve them is the internet connection ...

I followed the advise on a page I found here "internetHowTO" which directs me to a page about "ADSLPPPoE". everything worked out as it says,

except that I cannot access the internet.There seems to be a connection though. In the 'network settings', 'wired connection' is ticked.

(there should be nothing wrong with the cable/provider/etc cause it works on my other XP-laptop right now)

An online friend adviced me to take a look in the system log, I find "CHAP authentification failed: login failed", he advises me ""/etc/ppp/chap-secrets" to check the password, I get the correct password and correct username.

Please be aware that i'm completely new to linux ( i have read the absolute beginner's guide, but it will take some time before this is all really clear)
so maybe it's some minor problem,
webpage links are also welcome (but i've read already ten or so on simular problems)


thanks in advance :-)

---

### Post by Stemp on 2007-10-23
> **ubu-lemon said:**
> 
An online friend adviced me to take a look in the system log, I find "CHAP authentification failed: login failed", he advises me ""/etc/ppp/chap-secrets" to check the password, I get the correct password and correct username.

Check again, you have a login/password problem ;)

But to be really sure of what is going on, close pppoe connection :

```
sudo poff -a
```

start a new one :

```
pon dsl-provider
```

and check the pppoe log :

```
plog
```

You'll have to check plog multiple times to look at all the messages

---

### Post by ubu-lemon on 2007-10-23
> **Stemp said:**
> 
You'll have to check plog multiple times to look at all the messages

i've done this several times now, as you suggested, but to no avail,
same error message, have multiple-checked whether the password and usersname are correct.
but when trying to connect, i don't get asked to insert any password nor usersname, is that ok?

maybe the browser itself needs some configuration?




(pour les framboises, p-ê en ville c'est autre, mais la saison c'est en été, faudrait attendre l'année prochaîne ;-))

---

### Post by Stemp on 2007-10-23
> **ubu-lemon said:**
> i've done this several times now, as you suggested, but to no avail,
same error message, have multiple-checked whether the password and usersname are correct.
but when trying to connect, i don't get asked to insert any password nor usersname, is that ok?
You don't need to give a password at login, you gave it in pppoeconf.

> **ubu-lemon said:**
> maybe the browser itself needs some configuration?
No not needed but may be your network configuration is not good.
Menu, System, Administration, Network....
Are you in fixed IP ? 

> **ubu-lemon said:**
> (pour les framboises, p-ê en ville c'est autre, mais la saison c'est en été, faudrait attendre l'année prochaîne ;-))
Les frambroises se congèlent très bien :p

---

### Post by ubu-lemon on 2007-10-23
> **Stemp said:**
> You don't need to give a password at login, you gave it in pppoeconf.


No not needed but may be your network configuration is not good.
Menu, System, Administration, Network....
Are you in fixed IP ? 

Fixed IP? you mean like a university or company or so? don't think so, how can I know? I see some IP-adress in these network settings with the name of my computer next to it. 
(sorry i'm not an internet wizard, not a wizard at all actually, otherwise it would have been fixed just by wishing it :-) )







> **Stemp said:**
> Les frambroises se congèlent très bien :p
évidamment :-) bah, moi je préfère les citrons, pas besoin de congeler :-)

---

### Post by Stemp on 2007-10-23
You have an ethernet modem ? 
So you need to set up your wired connection to fixed IP : something like 196.168.1.2
Check : 
```
ifconfig -a
```
to look at the inet adr of eth0

---

### Post by ubu-lemon on 2007-10-23
> **Stemp said:**
> You have an ethernet modem ? 
So you need to set up your wired connection to fixed IP : something like 196.168.1.2
Check : 
```
ifconfig -a
```
to look at the inet adr of eth0

yeah, it's an ethernet modem.

What do I do there in this config-stuff?(I'm completely new remember, it's my first week of the linux-trip, except for the burning of the CD, that i did last summer)

I got a whole list now (ath0, atg0:avah, eth0, lo, wifi0-00)
It's the 'lo' that has the same figures as in the network settings,
the 'eth0' does not have a ' inet adr'

(also the IP there is not *three figures.three figures.one figure.one figure* (but the ath0 has a 'inet adrr' like that), it's *three figures.one figure.one figure.one figure*)

---

### Post by Stemp on 2007-10-23
Ok, Menu System, Administration, Network......
Click on Wired Connection and then properties...
Choose 
Confiiguration :static IP
IP adress : 192.168.1.2
Mask : 255.255.255.0

It's probably better to restart your network in a terminal :
```
sudo /etc/init.d/networking restart
```

check if there is an error with dmesg and plog

---

### Post by ubu-lemon on 2007-10-23
> **Stemp said:**
> Ok, Menu System, Administration, Network......
Click on Wired Connection and then properties...
Choose 
Confiiguration :static IP
IP adress : 192.168.1.2
Mask : 255.255.255.0

It's probably better to restart your network in a terminal :
```
sudo /etc/init.d/networking restart
```

check if there is an error with dmesg and plog


you do mean the IP that you write here (the '192.168.1.2'? or some i have to find myself?)

it's a whole list, i wrote a whole résume but erased it by accident :-(
i have it copied in a file now, if i attach it can i still remove it later then? 

can still not open webpages

the log says still the same
although at one point it says
-eth0: liink up, 10Mbps, half-duplex, lpa 0x0000
after that
-Plugin rp-pppoe.so loaded
-pppd 2.4.4 started by root, uid 0
-Timeout waiting for PADS packets
-PPP session is some figure
-Connect: ppp0 <---> eht0
-CHAP autentication failed: login failed
-Connection terminated
-Modem hangup

---

### Post by Stemp on 2007-10-23
> **ubu-lemon said:**
> 
-CHAP autentication failed: login failed

ok so basically it's still the same :D

You do have a problem with your login/password, something is wrong.
So it could be an Uppercase problem (x and not X) or maybe you need the full username (user@internetprovider.be  and not only user).

---

### Post by ubu-lemon on 2007-10-23
i do need the full name when i connect with my XP,
(i mean when i give my password, something i always did manually the username with it, is indeed a full name with the [email]abcdefg@provider.com[/email])

should i change that it  and how?

---

### Post by Stemp on 2007-10-23
I think the user name is in : 
/etc/ppp/pap-secrets
and
/etc/ppp/peers/dsl-provider

So I think it's better to run pppoeconf again :
```
sudo pppoeconf
```

---

### Post by ubu-lemon on 2007-10-23
> **Stemp said:**
> I think the user name is in : 
/etc/ppp/pap-secrets
and
/etc/ppp/peers/dsl-provider

So I think it's better to run pppoeconf again :
```
sudo pppoeconf
```


yeah !!! yipie !!!! great !!!
youhouuuuuuuuuuu !!!!

:guitar:


have i really arrived in linux-land now? 

that was it,
funny enough the config-stuff itself told me to ***not*** add the @provider.com...
i'm so greatful,
i hope my linux adventure can begin now...
even if it was kind of hard to have such a difficult start, it was never really frustrating,
not in the windows-way. i think linux and me are going to be friends :-)

thanks very much !!!

tu auras une farandole de framboise !!!!!

(ça fait trois jours que je cherche à résoudre ce truc !!!)

---

### Post by Stemp on 2007-10-23
> **ubu-lemon said:**
> have i really arrived in linux-land now?
Yep, Welcome and have fun :popcorn:


> **ubu-lemon said:**
> tu auras une farandole de framboise !!!!!
Super ! mais j'attendrai cet été pour en avoir des fraîches ;)

---

### Post by ubu-lemon on 2007-10-23
> **Stemp said:**
> Yep, Welcome and have fun :popcorn:

thanks!



> **Stemp said:**
> Super ! mais j'attendrai cet été pour en avoir des fraîches ;)

ok; d'accord! :-)
bye bye

---

### Post by bapoumba on 2007-10-23
> **ubu-lemon said:**
> 

tu auras une farandole de framboise !!!!!


Je suis jalouse, maintenant :D
(I'm jealous now)

---

### Post by ubu-lemon on 2007-10-25
> **bapoumba said:**
> Je suis jalouse, maintenant :D
(I'm jealous now)

:-)  t'en fais pas...

don't worry...

i've got plenty of problems to solve... ;-)

---

