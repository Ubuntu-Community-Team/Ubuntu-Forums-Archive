---
title: "Nvidia GTX260 + Jaunty == !openGL for savage2"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by piousp on 2009-04-24
SO, here is my problem:

Yesterday i upgraded to Kubuntu Jaunty 64bits (fresh install actually).
Well, everything went really fine, and jockey detected my gtx260 without a problem. So, i installed the nvidia propietary driver (180.44 i think) its working like a charm except for Savage2.
Actually, i havent played it before, so i got the lastest version for linux 64bits in their site. Well, whenever i run the game, i get an error message saying something like: "No openGL detected" (Or something really close to that). Then the game exits. Now, i get that in the terminal, because if i run the game withing the kde menu, it just exits without saying why.

Any ideas?

---

### Post by crjackson on 2009-04-24
> **piousp said:**
> SO, here is my problem:

Yesterday i upgraded to Kubuntu Jaunty 64bits (fresh install actually).
Well, everything went really fine, and jockey detected my gtx260 without a problem. So, i installed the nvidia propietary driver (180.44 i think) its working like a charm except for Savage2.
Actually, i havent played it before, so i got the lastest version for linux 64bits in their site. Well, whenever i run the game, i get an error message saying something like: "No openGL detected" (Or something really close to that). Then the game exits. Now, i get that in the terminal, because if i run the game withing the kde menu, it just exits without saying why.

Any ideas?

That's strange. Check your nvidia-settings applet and make sure it's reporting correctly. Pay close attention to the GL section. Also, you may want to get the newest driver from nvidia and install that. I'm using 180.53 with very good results. The current OFFICIAL stable release in the 180.xx series it 180.51

You may need the 185.xx series drivers to properly support that card, I'm not really sure on that.

I have a 7900GTO card and the 180.44's worked fine for me. I haven't tried Savage2 since Intrepid, but I'll give it a go and see if I have any luck this weekend.

---

### Post by piousp on 2009-04-24
> **crjackson said:**
> That's strange. Check your nvidia-settings applet and make sure it's reporting correctly. Pay close attention to the GL section. Also, you may want to get the newest driver from nvidia and install that. I'm using 180.53 with very good results. The current OFFICIAL stable release in the 180.xx series it 180.51

You may need the 185.xx series drivers to properly support that card, I'm not really sure on that.

I have a 7900GTO card and the 180.44's worked fine for me. I haven't tried Savage2 since Intrepid, but I'll give it a go and see if I have any luck this weekend.

I know its weird! I'm the the 180.44 cuz thats the one the drivermanager installed. I guess i'll have to manually install those new drivers. But before that, i'll check those GL values.

---

### Post by crjackson on 2009-04-24
> **piousp said:**
> I know its weird! I'm the the 180.44 cuz thats the one the drivermanager installed. I guess i'll have to manually install those new drivers. But before that, i'll check those GL values.

The newer drivers are very easy to install.  Check this link...

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by piousp on 2009-04-24
Ok, i just got home, so i can paste any info you may want:

When i try to run the game, this happens:

```
piousp@QVANTVM:~/Savage2$ ./savage2.bin
Savage2 - Fatal Error: OpenGL 2.1 not available.
```

In the picture you can see the basic info that the nvidia driver gives me

Any ideas???? 

@crjackson:

Thanks! I'm gonna check out those new drivers ;)

---

### Post by piousp on 2009-04-24
I got thinking, is this really an issue with the driver??? My guess is that it isnt, but i just dont know

---

### Post by aktiwers on 2009-04-24
Hey thats a bug! Run the dedicated_server.sh file in the savage folder and let it update (this can take more than 10-20 mins). That should fix it. I even think I had to reboot when the dedicated_server.sh completed.

---

### Post by piousp on 2009-04-25
:O :O :O :O
Thanks! I'm gonna run it right now!!! Yay! I can't wait!

---

### Post by Perfect Storm on 2009-04-25
I just run the ./savage2_update.bin instead, same effect I guess.

[http://gaming.gwos.org/doku.php/guides:64bit:savage_2](http://gaming.gwos.org/doku.php/guides:64bit:savage_2)

---

### Post by aktiwers on 2009-04-25
I got the same error with the savage2_update.bin but  dedicated_server.sh didn't make that error.
Well hope it works out, let us know :)

---

### Post by piousp on 2009-04-26
HEY!!!! THANKS!!!! Its working now!!!
I'm not really sure what did it, 'cuz i ran the dedicated_server.sh first, and then i tried the savage2_update.bin and it worked. So i can play now!!! Nice!!! Thanks guys! :popcorn::popcorn:

Can i still mark this thread as solved???

---

### Post by aktiwers on 2009-04-26
> **piousp said:**
> HEY!!!! THANKS!!!! Its working now!!!
I'm not really sure what did it, 'cuz i ran the dedicated_server.sh first, and then i tried the savage2_update.bin and it worked. So i can play now!!! Nice!!! Thanks guys! :popcorn::popcorn:

Can i still mark this thread as solved???

Great - and yeah mark it solved :)

Glad it worked out, Savage2 is a great game

---

