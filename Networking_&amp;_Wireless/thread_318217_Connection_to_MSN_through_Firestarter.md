---
title: "Connection to MSN through Firestarter"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by buckethead on 2006-12-13
Hi everyone

Yup you guessed it, i'm a Converted Windows User and have been trying to learn Ubuntu.

Anyway i have a problem with Firestarter in that when it is switched on, i cannot connect to MSN, nor can i connect to Gmail.  When Firestarter is off, everything works.

Please can someone advice me on which ports i should active.

I currently have msnp 1863 active on both inboard and outboard, but no luck.  
Everytime i try to connect via msn, i get disconnected. when i try to access gmail it says page cannot be found.

Many Thanks for any advice.

---

### Post by ibanez on 2006-12-13
port 1863 is indeed the correct port, Its exactly what I allow both inbound & outbound  I dont understand why yours isn't working.

You have applied the setting havn't you.

---

### Post by buckethead on 2006-12-13
yeah i have applied the settings

I have the followimg

inbound traffic policy

Allow service   port    for
msnp            1863     everyone

outbound policy - the same

Do i need to allow another port?

---

### Post by buckethead on 2006-12-13
Hi All

i figured it out, in order to get msn working, you need to have port 443 (outbound) enabled.

Cheers ibanez for the help!

---

### Post by ibanez on 2006-12-13
> **buckethead said:**
> Hi All

i figured it out, in order to get msn working, you need to have port 443 (outbound) enabled.

Cheers ibanez for the help!

haha  of course you do (Beats myself on the head with a wet fish!)I have that enabled for something else, so never ran into that one  .
glad you got it sorted :)

---

