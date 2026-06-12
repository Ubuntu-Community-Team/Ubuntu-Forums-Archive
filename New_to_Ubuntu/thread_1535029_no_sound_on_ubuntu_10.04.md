---
title: "no sound on ubuntu 10.04"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by paulh1974 on 2010-07-20
hi guys im not getting any sound on ubuntu 10.04. not from youtube or even movies iv downloaded. im on a desktop using google chrome. iv already checked my alsa mixer and all bars are full, and checked  my sound in preferences. any ideas what could be wrong??? please keep your answers clear and simple as im totally new to ubuntu. THANKS

---

### Post by TimEnid on 2010-07-20
try the options in this thread. i has a similar problem but was able to fix it. see post 24.
[http://ubuntuforums.org/showthread.php?t=1531958](http://ubuntuforums.org/showthread.php?t=1531958)
__[]("http://ubuntuforums.org/showthread.php?t=1531958")[]("http://ubuntuforums.org/showthread.php?t=1531958")

---

### Post by murphycc on 2010-07-20
I found the following sound troubleshooting thread in this forum to be spectacular. My problem was I did not know about alsa-mixer. Sounds like you already checked that and it's not the problem, but walk through this troubleshooter anyhow, since it starts from square one:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

-Chris

---

### Post by kozmos on 2010-07-22
> **lidex said:**
> OK. Do this.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

Now this. Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
**Reboot.**

Hi. I had the same problem but double-whammied with no sound on youtube or flash.

Coupled with the solution above, try playing around with the volume control options. (configuration tab)

I think it may be a conflict of drivers and configs between alsa and pulse. (i think)

---

