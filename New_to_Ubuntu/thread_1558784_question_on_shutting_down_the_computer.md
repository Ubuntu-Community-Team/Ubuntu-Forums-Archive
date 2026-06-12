---
title: "question on shutting down the computer"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by gaurish108 on 2010-08-22
This is probably a sill question......I notice that when I try to shut down/ restart the computer through the terminal with sudo restart and sudo reboot my laptop makes a strange 1 second sound blip as if sth is being dragged on a metallic surface. 

If I shut it down the 'normal' way by using the system menu, I dont hear the same sound......Why could this be happening? Is it safe for the computer to be shut down from the terminal?

---

### Post by gaurish108 on 2010-08-22
Sorry I shut down the computer with sudo poweroff :lolflag:

---

### Post by Chris1274 on 2010-08-22
Try muting the computer beep. You can do so using the Alsa mixer, which can be downloaded via synaptic.

It's perfectly safe to shutdown through the terminal. I do it all the time, using the commands:
```
sudo shutdown -r now
sudo shutdown -h now
```
to restart and powerdown, respectively.

---

### Post by 0004tom on 2010-08-22
I do the same altho I use different commands.

```
sudo reboot
sudo halt
```

---

### Post by Chris1274 on 2010-08-24
I wasn't aware of those commands. Less typing is always a good thing :)

---

