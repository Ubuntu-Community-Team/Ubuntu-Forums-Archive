---
title: "no sound"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by idrinkwhisky on 2010-07-01
My lucid lynx always played sound but after starting up today it s not playing sound anymore.

when i go to "sound preferences" and then "hardware" it shows no devices at all. 

in the terminal i typed in:

sudo aplay -l
(and it returned a list with sound devices)

though when i type in
alsamixer 
(in the terminal, nothing happens)

does that mean i need to reinstall alsamixer? if so how?
other suggestions? Thanks.

---

### Post by ubudog on 2010-07-01
What did you do before this happened?

---

### Post by lkjoel on 2010-07-01
Click on Fix your sound! in my sig.
That should fix it.
Also check if OSS supports your soundcard.
Check if your soundcard even works!

---

### Post by idrinkwhisky on 2010-07-02
Hi, thanks for the replies.

I found the solution in this link
[http://ubuntuforums.org/showthread.php?t=1475312&highlight=alsamixer](http://ubuntuforums.org/showthread.php?t=1475312&highlight=alsamixer)

by novellahub. I had to add my username to the audio group.

---

