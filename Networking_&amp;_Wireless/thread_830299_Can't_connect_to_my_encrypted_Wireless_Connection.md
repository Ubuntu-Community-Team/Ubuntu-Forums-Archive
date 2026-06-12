---
title: "Can't connect to my encrypted Wireless Connection"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by EverettGMartin on 2008-06-15
I've have connected to a wireless connection before, but it was unencrypted, I soon got tired of people stealing my wifi and slowing down my connection, so I secured it with WEP, after that Ubuntu will not connect, in the linksys router I use, I chose to use 64 bit enc. 10 hex, and here is the problem, i choose Key 4, and in Ubuntu, it doesnt give me the option to choose which key i'm encrypting my signal on???? Do i have to modify one of the lists or something? I'm tired of using microsoft windows, they change their stuff to much and it is to demanding, I love using Ubuntu and it is way faster than Microsoft

---

### Post by fwre01 on 2008-06-15
i dont think ubuntu offers you a list to select a key from, you just need to enter it in manually. or have u tried that?

---

### Post by EverettGMartin on 2008-06-15
yes i have tried that and it doesnt work, I even tried the passphrase but i got the same luck


could you name or give me instructions on how to do this, maybe i did something wrong?

---

### Post by fwre01 on 2008-06-15
have u tried using a different key? or a higher level bit encryption?

---

### Post by EverettGMartin on 2008-06-15
I've tried using a different key, but it didnt work, I haven't tried higher encryption, didn't feel like typin the longer codes on 7 computers, it gets really tireding. Could it be a bad disc I got in the mail, because I have installed it numerous times, but it still connects without encryption so.... I don't know.

---

### Post by fwre01 on 2008-06-15
a bad disc? howcome theres a disc involved?

you know u can generally copy and paste the WEP key

---

### Post by EverettGMartin on 2008-06-15
Oh sorry, as in bad disc I meant the OS Disc, you know, the one to install Ubuntu. i never really copy the key to a floppy or disc or flash drive, i jus write it down on paper then shred the paper after i use it, so copy and paste is kinda out of the question

---

### Post by fwre01 on 2008-06-15
i guess theres a chance it could be a bad disk, allthough im sure it would have complained during the install. do u have other computers connecting to the wireless with the WEP key switched on?

---

### Post by EverettGMartin on 2008-06-15
No it never complianed during install. yes, I have 4 desktops running Microsoft Windows and 3 laptops running microsoft windows, my desktop counts as one of those 4 because i cant connect with linux so i had to convert back. not a single MS computer is having difficulties. do you have an idea of what it could be?

---

### Post by jerome1232 on 2008-06-15
Problem wouldn't lie with the disc, you say you have 7 computers, are any of them able to connect? Are they all the same OS or diff? I would probably not select key 4, just use Key 1 usually Client mangers default to Key 1 and I'm not sure how to change that in ubuntu's network manager.

Try WPA - PSK, or WPA2, much better forms of encryption anyways (wep can be cracked in about 10 secs, shorter even). WPA actually lets you use a shorter password, 8 characters (any characters) as opposed to weps 10 hexadecimal characters (1-0, a-f)

check this out to figure out what card you are using and if there are any known problems with it.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by EverettGMartin on 2008-06-15
all computers are able to connect, one is windows 98 SE, two are 2000, 3 are xp home and mine is xp pro, it would be ubuntu 7.10 but yea..... all computers connect fine to any key, i change it often, i jus got tired of ubuntu not wanting to connect so i jus gave up like 3 months ago, but i want it back so now im asking if anyone else has had this problem and if it can be solved. yea i kno wep can be cracked easily, but i jus chose the first think on the list because all the wifi stealers, i'm bout to do WPA-PSK tho, jus never got around to it. i have a d-link 1320 and it works fine. I'm going to try Key 1 and i'll let ya kno thanx man

---

### Post by EverettGMartin on 2008-06-15
[COLOR="Red"]Thanx so much man, that was the problem, it had to be key 1. keep up the good work
[/COLOR]

---

