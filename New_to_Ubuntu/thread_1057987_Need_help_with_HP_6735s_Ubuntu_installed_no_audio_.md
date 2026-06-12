---
title: "Need help with HP 6735s Ubuntu installed no audio working"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by stephen376 on 2009-02-02
Only been using ubuntu for a few days, i really like it. My problem is i installed Ubuntu on my XP laptop the HP 6735s. I can't seem to get the audio working. in the volume control preferences I have it set to HDA ATI SB (alsa mix) and track PCM. I have tried the others but with no luck. I have been playing the smiths at the same time to try to test the different sound settings. Any help would be much appreciated. Thank you.

---

### Post by kestrel1 on 2009-02-02
Lets bump this one for you.
Something I should have asked. Have you installed all the latest updates?

---

### Post by stephen376 on 2009-02-03
Sure did.

---

### Post by kestrel1 on 2009-02-03
OK, as I just said in the earlier email, we can work on that one.

---

### Post by kestrel1 on 2009-04-29
As requested here is the solution that worked for Stephen376.
Run the following commands first```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.bak
```
```
sudo cp /etc/modprobe.d/options /etc/modprobe.d/options.bak
```
Copy the attached files to your desktop & do the following:```
cd Desktop
```
```
sudo cp alsa-base /etc/modprobe.d/
```
```
sudo cp options /etc/modprobe.d/
```
You may need to rename the attached files by removing the .txt extension.
Hopefully this will work.

---

### Post by radojesrb on 2009-04-29
HUGE thanks!!!!!

This works for me too.

Now I can fully enjoy UI just need to learn much more 

:popcorn:

---

### Post by kestrel1 on 2009-04-29
Good result then. Glad about that. :lolflag:

---

### Post by Devlin67 on 2009-04-29
Thanks a million. PERFECT:guitar:

---

### Post by /etc on 2009-05-11
Thanks m8, finally solved this ;)

---

### Post by kestrel1 on 2009-05-12
Glad to hear it. :-)

---

### Post by Slavko.M on 2009-07-13
Hello everyone. I'm new with Linux and after I installed ubuntu 9.04 I had the same problem with sound. I followd these instructions, but when I type the first command the computer is asking for a password and further typing seems to be blocked until I press "ente". After I press "enter" the computer tells me it's a wrong password. Any idea how to overcome this problem? Thanks in advance.

---

### Post by kestrel1 on 2009-07-13
> **Slavko.M said:**
> Hello everyone. I'm new with Linux and after I installed ubuntu 9.04 I had the same problem with sound. I followd these instructions, but when I type the first command the computer is asking for a password and further typing seems to be blocked until I press "ente". After I press "enter" the computer tells me it's a wrong password. Any idea how to overcome this problem? Thanks in advance.
The password you should use is your login password.
You won't see anything as you type, as this is a security measure. But once you use 'sudo' you will be asked for your password, if you do not close the terminal you will not need to retype the password.
If you need any detailed info PM me.

---

### Post by plattr on 2009-10-05
Great solution, kestrel1! This fixed the problem on Linux Mint 7 by the way. :)

---

### Post by kestrel1 on 2009-10-05
> **plattr said:**
> Great solution, kestrel1! This fixed the problem on Linux Mint 7 by the way. :)
We aim to please :-)

---

