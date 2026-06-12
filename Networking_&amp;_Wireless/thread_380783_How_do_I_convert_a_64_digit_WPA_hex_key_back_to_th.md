---
title: "How do I convert a 64 digit WPA hex key back to the passphrase"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by persept on 2007-03-10
My wireless network is set to WPA, and I had set up a passphrase for it.  After many months I forgot the passphrase, but I was able to recover the 64 charactor hex key that was stored on my computer.  The hex key does work fine if I type it in for my network, but it is very bothersome to type in, such as when a friend needs to use my wireless.  Is there a way I can turn the hex key back into the passphrase?  I think I might have to use a password cracking program to do this, such as John the Ripper.
Any help would be greatly appreciated.

---

### Post by wieman01 on 2007-03-10
That's a good question... I actually think you can't.

---

### Post by hardyn on 2007-03-10
thats the point of encryption!

---

### Post by persept on 2007-03-10
> **hardyn said:**
> thats the point of encryption!

What I believe what happens when you enter the passphase for a WPA network is that it converts it to the 64 char hex.  I have access to the network with the hex key, I just want to get back to my a much shorter key that is easier to remember.  But I don't think that you can just convert back to it.  To my knowledge, it does something with the [PBKDF2]("http://en.wikipedia.org/wiki/PBKDF2") which does something with SHA1.  I am pretty sure I need a cracking program, but I don't know what I would have to enter into it to be able to try and use a wordlist to crack it.  I know I used a couple of words, but I just don't remember it.

---

### Post by lsutiger on 2007-03-10
Why not just reset you WPA passphrase? Just wondering....

---

### Post by wj32 on 2007-03-10
john the ripper!

---

