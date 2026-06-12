---
title: "need help on getting connected to the internet"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by jenna28jj on 2011-03-04
I am an IT student and taking the ubuntu linux class. I bought a crappy laptop and did a clean intsall of lucid lynx on a dell laptop running windows vista. every thing installed i think, although i cannot get connected to my wifi as the windows did. it says in the network manager that device is not ready although i am connected on this asus laptop and 2 desktops? I saw what i thought was a related post to this and i cant read it, its in another language. If anyone could help me i would appreciate it...my instructor has no time..lol P.S. I did everything in the help section to try and get it working..

---

### Post by Drate on 2011-03-05
If you would be so kind as to post the output of of "lspci" it would help in identifying what the problem could be.  To do this goto:

Applications > Accessories > Terminal

(you might want to maximize the terminal window as the output will be big)

Then type:

lspci

Then press enter... it will have a rather large output.

You can highlight the text and right-click > Copy OR
You can highlight the text and press ctrl+shift+c

Then paste it in here as normal.

---

### Post by jenna28jj on 2011-03-05
Well thank you for replying, I got this working. but thank you very much! SOLVED

---

### Post by lisati on 2011-03-05
> **jenna28jj said:**
> Well thank you for replying, I got this working. but thank you very much! SOLVED

Just a suggestion: are you able to post the solution here (a link will do fine) so others with a similar problem might be helped?

---

### Post by jenna28jj on 2011-03-05
well I clicked on system-administration-windows wireless drivers, then a box came up about proprietary drivers..which said there were none. I was frustrated and closed the laptop, opened it this morning and there was an icon near the network manager for hardware drivers. I clicked on it, it stated one had been found, broad-com something or other and it wanted me to click it and install said driver. Now at this point I had no wireless connection so I plugged in the Ethernet and clicked install and it did. Then a box came up about security updates to download, which I did and now everything works perfectly, I also have Avast! for Linux up and running. Pretty exciting stuff.

---

### Post by jbiggs12 on 2011-03-05
Congrats! Would you mind marking this thread as "Solved" in the Thread Tools menu?

---

