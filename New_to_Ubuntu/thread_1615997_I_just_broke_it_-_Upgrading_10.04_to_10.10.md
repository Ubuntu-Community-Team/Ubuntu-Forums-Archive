---
title: "I just broke it - Upgrading 10.04 to 10.10"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by Bugsy_malone 666 on 2010-11-07
Ok not your average case of failure here, basically it took me a day to go through various upgrades to get to upgrading from 10.04 to 10.10 and it took so long I had to hard power off the PC!

This is obviously a bad move, 10.10 had downloaded all the update files, it was probably 50% through upgrade when power off occured, but I had to leave and couldnt leave the PC running, there was no option to quit so I just used a linux power off button at the top of the screen.

I come back to the PC today not knowing what to expect and now it will boot up so far to the Ubuntu start screen but says there is an error with the power management not being installed properly and that I need to seek the system administrator. It wont go any further and it wont give me any options.

What do I do as I really dont know where to start looking to fix my error as I only play with linux on and off occasionally and still havent learnt the ins and outs yet.

Cheers :)

---

### Post by bioterror on 2010-11-07
Try this one in Terminal if you can Login or in TTY (ctrl+alt+f1 & log in):
```

sudo apt-get -f install

```

If that works and it continues installing software, then continue with these.

```

sudo apt-get update
sudo apt-get dist-upgrade
sudo reboot 

```

---

### Post by Bugsy_malone 666 on 2010-11-07
Ah right thanks for that!

I put in the first lot of commands and it said I had to manually type in a command to configure to repair the problem, its now happily sat going through configurations and installing stuff!

Cheers :)

---

### Post by bioterror on 2010-11-07
> **Bugsy_malone 666 said:**
> Ah right thanks for that!

I put in the first lot of commands and it said I had to manually type in a command to configure to repair the problem, its now happily sat going through configurations and installing stuff!

Cheers :)

Great, could you mark this solved then ;)

---

