---
title: "Directory taking up most of HDD space"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by k33bz on 2010-07-28
Today I was cleaning out files and apps that I no longer needed. I decided to see how much disk space I had left. To my shock I noticed that i have 260GBs of space taken out of a 300GB HDD. So I started clearing my logs, lost and found, tmp directories. And still have a large sum. So I started going through each directory to see where my problem was. And I found it. The Encryption Directory:
```
/home/user/.Private
```
That folder alone takes up 135GB space.

Can I just delete this folder (I really dont care to keep the encryption on my HDD).
Or will deleting it screw my laptop up?

Please help!

---

### Post by gordintoronto on 2010-07-28
My assumption would be that the folder contains encrypted files, so you don't want to just delete it.

Have a look at the man pages for encryption.

---

### Post by JustinR on 2010-07-28
Is you Home Directory encrypted? If so everything in .Private is actually your home folder. When Ubuntu boots, it mounts .Private to /home/USERNAME and decrypts everything you click in the folder in RAM.

Got this from the Ubuntu documentation but this was from memory so I could be wrong.

---

### Post by k33bz on 2010-07-28
lol, well too late, :( I just got back online from re-installing, I deleted my whole Home Folder, and didnt have a backup, so now I am doing everything from scratch. :(

---

### Post by JustinR on 2010-07-28
> **k33bz said:**
> lol, well too late, :( I just got back online from re-installing, I deleted my whole Home Folder, and didnt have a backup, so now I am doing everything from scratch. :(

Ohhhhhhh Wow. :!: Oops. Well Good luck!

---

### Post by k33bz on 2010-07-28
I sort of knew that I should of made a backup, now I am kicking myself for not doing so, oh well better this way, had to many un-needed apps, plus now I can easily do away with encrypting my HDD, lol

Another lesson learned, feel like a noob again, lol

---

