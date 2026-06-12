---
title: "volume resets to zero when turning on?"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by cairnzi on 2010-03-04
hi people,i am running xubuntu 9.10 and when i reboot or turn it on the volume goes to zero and i have to go to the icon and put it up again? any ideas of a fix for this rather small but annoying problem? many thanks.

---

### Post by MichealH on 2010-03-04
Audio on 9.10 AGAIN! Sorry your Sound card might not be supported on Ubuntu 9.10 that is because they have changed the audio system from GNOME to pulse audio.

---

### Post by JackRock on 2010-03-04
I have a similar issue in Ubuntu 9.10, but it works as long as I go in and unmute the sound again.  Only happens after a reboot or log off.

Sound card compatibility?

---

### Post by cairnzi on 2010-03-04
cheers for the replys,my card is listed as supported, i have sound no problem if i turn it up but it is always zero when i reboot or turn it on, is there a default setting anywhere i could try and change? thanks.

---

### Post by Sir Jasper on 2010-03-04
Hi,

I had a similar (possibly identical) problem with Xubuntu 9.04.

I read a thread with a solution which worked and was not sound card related.

At the moment I cannot recall that solution, but if there is no resolution within 24 hours I will see if I can find it again.

My regards

---

### Post by cairnzi on 2010-03-04
@ sir jasper, cheers very much,away to work,will check when i get home and see if some kind soul has found a solution, cheers again to all.

---

### Post by JackRock on 2010-03-04
FOUND IT!

[http://ubuntuforums.org/showthread.php?t=1326505&highlight=sound+reset+restart&page=2](http://ubuntuforums.org/showthread.php?t=1326505&highlight=sound+reset+restart&page=2)

Just comment out one line, and it worked just fine.  I just now tested it.

---

### Post by Jose Catre-Vandis on 2010-03-04
Also [here]("http://ubuntuforums.org/showthread.php?t=1406933")

---

### Post by cairnzi on 2010-03-05
@ Jose Catre-Vandis,JackRock, much appreciated thats it fixed and working, many thanks.

---

