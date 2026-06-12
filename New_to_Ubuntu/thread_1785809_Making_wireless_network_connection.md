---
title: "Making wireless network connection"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by redoak on 2011-06-18
I believe U 11.04 knows there is a wireless setup available when I boot. A message appears to go to --------. But I don't know how to reach the spot. I noticed in a previous Thread: "Oh, did you click the little network icon to see if there are any wireless access points?" Where is this "little -- icon" located? I think clicking it will lead me to connecting to my network.

---

### Post by Talon2 on 2011-06-18
It is located on the right side of the top panel.  It is usually located just to the left of the speaker.

---

### Post by wildmanne39 on 2011-06-18
> **redoak said:**
> I believe U 11.04 knows there is a wireless setup available when I boot. A message appears to go to --------. But I don't know how to reach the spot. I noticed in a previous Thread: "Oh, did you click the little network icon to see if there are any wireless access points?" Where is this "little -- icon" located? I think clicking it will lead me to connecting to my network.
Hi, if that does not work post the outcome of these command from your terminal.
```
sudo lshw -C network 
```
```
lspci
```
```
lsmod
```

---

### Post by redoak on 2011-06-19
"Talon2": Thanks! My network was indeed available. 

I am almost 82 years of age. I take one computer challenge after the other to keep my brain occupied!

I never did anything with Ubuntu back in 2008. My true "join date" is June 2011.

---

