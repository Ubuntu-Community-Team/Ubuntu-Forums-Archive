---
title: "Some 9.10 problems."
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Rave Gloves on 2009-10-29
Im not getting any drivers on my hardware list any reason why?

i have updated to see if it would cure it but still nothing.
Anyone else having this problem?

---

### Post by Rave Gloves on 2009-10-29
Also the new add/remove is very slow. is this a server problem maybe?

---

### Post by twright on 2009-10-29
> **Rave Gloves said:**
> Also the new add/remove is very slow. is this a server problem maybe?
It might be, the servers are usually quite clogged up in the wake of a release.

This might also be related to your other problem - running updates might help.

---

### Post by Rave Gloves on 2009-10-29
> **twright said:**
> It might be, the servers are usually quite clogged up in the wake of a release.

This might also be related to your other problem - running updates might help.

I have been updating for a while and still nothing. Is anyone else having the same problem?

---

### Post by twright on 2009-10-29
> **Rave Gloves said:**
> I have been updating for a while and still nothing. Is anyone else having the same problem?
What are you expecting to see?

---

### Post by dearingj on 2009-10-29
> **Rave Gloves said:**
> Im not getting any drivers on my hardware list any reason why?

i have updated to see if it would cure it but still nothing.
Anyone else having this problem?

I assume you're talking about the "Hardware Drives" program (System->Administration->Hardware Drivers). This isn't usually a problem; it just means there aren't any closed-source drivers available for your hardware. Open-source drivers are installed by default in Ubuntu, but they're not listed by this program.

---

### Post by Rave Gloves on 2009-10-29
> **dearingj said:**
> I assume you're talking about the "Hardware Drives" program (System->Administration->Hardware Drivers). This isn't usually a problem; it just means there aren't any closed-source drivers available for your hardware. Open-source drivers are installed by default in Ubuntu, but they're not listed by this program.

On 9.04 it would atleast have my graphics card driver. Without it everything is running generaly quite slow. which might not be a graphic problem but from my experiance it dose speed everything up. Menus and such.

compiz wont work ether im sure.

---

### Post by Rave Gloves on 2009-10-29
I checked my drivers list there and it seems i have got my graphics card drivers there now. im getting this error though.

SystemError: Failed to lock /var/cache/apt/archives/lock

---

### Post by djyoung4 on 2009-10-29
i have sort of the same problem.  there are no drivers in the proprietary drivers list and i need one to get my wireless card working.  any ideas anybody.

---

### Post by Rave Gloves on 2009-10-29
Im having a problem also with flash player.

ussualy i would just get it from the add/remove but that dosent seem to be working ether.

---

### Post by Hankers on 2009-10-29
Having issues with sound in 9.10. Using 9.10 in Parallels on a mac and the sound seems to be not in sync with a video or when listening to audio in an audio player such as VLC media player the sound continues for a few seconds after quitting the program.

---

### Post by dearingj on 2009-10-29
> **Rave Gloves said:**
> I checked my drivers list there and it seems i have got my graphics card drivers there now. im getting this error though.

Strange that it would just appear there. Glad it did, though, since you say it speeds things up.

> **Rave Gloves said:**
> SystemError: Failed to lock /var/cache/apt/archives/lock

That file can be safely deleted if you're sure there isn't anything currently being installed or updated. It's used to ensure that you never run two installers at once, which otherwise could mess up your system. You can remove it by entering this command in the terminal:
sudo rm /var/cache/apt/archives/lock

---

### Post by Rave Gloves on 2009-10-29
> **dearingj said:**
> Strange that it would just appear there. Glad it did, though, since you say it speeds things up.



That file can be safely deleted if you're sure there isn't anything currently being installed or updated. It's used to ensure that you never run two installers at once, which otherwise could mess up your system. You can remove it by entering this command in the terminal:
sudo rm /var/cache/apt/archives/lock


it appears that it has decided to work, took about 15mins to get the drivers to install but they are working and everything is working alot smoother now.

---

### Post by danastasio on 2009-10-29
for your hardware problem,

I had the same issue, install all updates 

```
sudo apt-get update && sudo apt-get upgrade -y
```

Then restart your computer, and run the hardware drivers app again. should solve your problem

---

