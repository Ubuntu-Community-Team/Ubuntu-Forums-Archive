---
title: "sync. out of range after upgrading to 9.06?"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by jeordieg on 2009-05-21
Hi, I just upgraded my ubuntu to the latest release and now I have a black screen with sync. out of range message that pops on for a few seconds before it goes black.  Can someone point me to the right place to learn how to fix this? 

I usually can find these solutions myself but this time I'm feeling a little boondoggled... 

thank -you, geordieg

---

### Post by overdrank on 2009-05-21
> **jeordieg said:**
> Hi, I just upgraded my ubuntu to the latest release and now I have a black screen with sync. out of range message that pops on for a few seconds before it goes black.  Can someone point me to the right place to learn how to fix this? 

I usually can find these solutions myself but this time I'm feeling a little boondoggled... 

thank -you, geordieg

Hi and welcome, what is the model of the graphics card? Have you tried booting into recovery mode and using the xfix option to correct the graphics?

---

### Post by jeordieg on 2009-05-21
Hi, yes I did try the xfix option in recovery mode with no success. I am not sure how to find my graphics card model without being able to use the desktop. 

Also, I the version of ubuntu is 9.04 not 9.06 as I had previously thought.

---

### Post by clhsharky on 2009-05-21
Do you have the Ubuntu 9.04 desktop cd and can you boot off it

---

### Post by overdrank on 2009-05-21
> **jeordieg said:**
> Hi, yes I did try the xfix option in recovery mode with no success. I am not sure how to find my graphics card model without being able to use the desktop. 

Also, I the version of ubuntu is 9.04 not 9.06 as I had previously thought.

Hi and if you are able to reach the command line, using the alt, F1 keys or booting into recovery mode you may use the command lspci and look for VGA. That will be the graphics card and I have seen many threads with this issue as intel or ATI graphics card.

---

### Post by Penguin Guy on 2009-05-21
I believe this is something to do with xorg - so if you're quite an experienced user you might want to look into that.

> **overdrank said:**
> Hi and if you are able to reach the command line, using the alt, F1 keys or booting into recovery mode you may **use the command lspci and look for VGA**. That will be the graphics card and I have seen many threads with this issue as intel or ATI graphics card.
Forgive me if you are more experienced than I think you are but you might want to use grep for this:
[COLOR="Green"]lspci | grep VGA[/COLOR]

---

### Post by jeordieg on 2009-05-21
sorry for the delay, I found the VGA info: S3 Inc. VT8375 (Prosavage8) KM266/KL266

now would that mean Intel or ATI ?

and yes I am an absolute noob for ubuntu stuff. Just heard it would make my old dinosaur run faster and smoother so figured I'ld give it a whirl...

---

### Post by clhsharky on 2009-05-21
No that's a VIA chip, that Prosavage is probable legacy now. Might have to go back to 8.10. This is not the first VIA video problem I've seen in 9.04.

---

