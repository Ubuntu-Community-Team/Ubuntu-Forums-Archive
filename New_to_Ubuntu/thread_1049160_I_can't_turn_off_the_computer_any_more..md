---
title: "I can't turn off the computer any more."
date: 2009-01-24
forum: New to Ubuntu
---

### Post by jorge ortega on 2009-01-24
Hi there, I hope someone will know what the problem is. Out of the blue the shut down window does not give me the option to turn off the computer anymore, it just isn't there. I've got the option to hibernate or supend, that's all. Now the computer doesn't boot properly although in the end it does start. And then my desktop shows open programs which I had closed before putting the computer to hibernate (as I can't just switch it off). Could anyone help, please?

---

### Post by Eisenwinter on 2009-01-24
Well, you can shut it off with a terminal command.

Open terminal, and type "sudo shutdown -Ph now"

This will shut down the computer (turn it off completely).

As far as the "shut down window" not giving you the turn off option, I'm stumped. I don't use GNOME or Ubuntu, so I can't help you with that one.

---

### Post by feelshift on 2009-01-24
```
sudo halt
``` or ```
sudo shutdown -h now
``` I remember having the same problem with 7.04, and I used this commands as work-rounds.

---

### Post by 3rdalbum on 2009-01-24
Quicker to type and easier to remember:

```
sudo halt
```

You might want to look at the settings in System > Preferences > Sessions.

---

### Post by jorge ortega on 2009-01-24
High, thanks to all for the quick replays. I thought there might be some command prompt i could use, but still wonder what the problem might be and if there is anything I could. I'm not the only one using the computer and the others would cry at the thought of having to use the command line.

---

### Post by SOULRiDER on 2009-01-24
My guess it that the user doesnt have permissions, and thats why it isnt giving you the option.. is a very wild guess though. Did you change any system settings or anything?

---

### Post by jorge ortega on 2009-01-24
As far as i know i've not changed any configuration. Yesterday I installed some updates, and also installed some more softaware from synaptic and althogh i can't relate to anything in particular it must've been some of the installed stuff (as i said, nothing dodgy all from synaptic).

---

### Post by mister_pink on 2009-01-24
gnome-power-manager has to be running. Check it's still ticked in your startup session in System > Preferences > Sessions.

---

### Post by linux_tech on 2009-01-24
Try turning off your network connection before you turn off your PC. The icon is in right corner of your screen, right click and uncheck the “Enable Networking” option

---

### Post by jorge ortega on 2009-01-24
> **linux_tech said:**
> Try turning off your network connection before you turn off your PC. The icon is in right corner of your screen, right click and uncheck the “Enable Networking” option

I tried this and restarted the computer. Is starts OK now but still no graphical option to turn off computer
I also checked for the Power Manager and is on.

---

### Post by philinux on 2009-01-24
Simple to sort out.

System Admin>login window.

Click the local tab.

Then tick the option "Show actions Menu".

---

### Post by jorge ortega on 2009-01-24
> **linux_tech said:**
> Try turning off your network connection before you turn off your PC. The icon is in right corner of your screen, right click and uncheck the “Enable Networking” option

> **philinux said:**
> Simple to sort out.

System Admin>login window.

Click the local tab.

Then tick the option "Show actions Menu".

Magick! It is sorted now. Thank you all

---

### Post by jorge ortega on 2009-01-24
I can't fined "solved" and "thank" bottoms?!

---

### Post by PocketDog on 2009-01-24
They've been temporarily removed due to forum database issues.

---

