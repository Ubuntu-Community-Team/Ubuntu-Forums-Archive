---
title: "airodump not in aircrack?"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by mrchrisblau on 2007-05-03
So I've decided to mess around a bit with kismet, airodump, aircrack, and the like. I'm fairly new to linux, but not a total noob (but still, speak slowly and clearly).

I've downloaded/installed aircrack, aircrack-ng, and kismet from the repositories.

Heres my problem:

I've run kismet and found a network that I want to try to crack (its my own home network, calm down).

I then try to run airodump, but i get this:
```
bash: airodump: command not found
```

I went looking on Google and these forums and found somebody who had the same problem, but the only response to his thread was "airodump is included in aircrack". Seeing as I have aircrack (and aircrack-ng), I would think that airodump would work, but it does't.

Please help!

---

### Post by ttakun on 2007-05-03
I haven't tried those programs. I don't know what version of those programs is on the repos. But maybe you could install the latest stable version from its main page, and see what happens:
[Aircrack-ng Main Page]("http://www.wirelessdefence.org/Contents/Aircrack-ng_Main.htm")
Get the tar file, unzip it, and make it.

---

### Post by mrchrisblau on 2007-05-03
I have the most recent aircrack and aircrack-ng versions now.. but still now airodump. Any other suggestions?

---

### Post by ttakun on 2007-05-03
If you open a terminal window and type "air" and then press twice the TAB key (to the left of Q key), what do you get?
You should get all the commands that can be executed from bash and start with "air". So you should get a list of commands including: aircrack aircrack-ng airodump airodump-ng aireplay aireplay-ng ... If you only get aircrack and aircrack-ng, or you don't get any command at all, maybe there is a problem with the repository of aircrack in Feisty. Then, I advice you to install aircrack or aircrack-ng from its web site, ... download the tar file, unzip, make, ...

P.D. I can't help you more, because I am writing you from my computer at work, that is running on Windows. No Linux available nearby .When I get home at night I will put my hands on my linux laptop and I could be more helpful.

---

### Post by mrchrisblau on 2007-05-03
```
chris@greyhat:~$ air
aircrack-ng  airdecap-ng  aireplay-ng  airmon-ng    airodump-ng  
```

Ha! There's airodump-ng! Alright, I'm going to go play with it, hopefully that works.

Thanks so much!

---

