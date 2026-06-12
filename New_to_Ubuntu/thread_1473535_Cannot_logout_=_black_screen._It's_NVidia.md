---
title: "Cannot logout = black screen. It's NVidia"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by tonsil on 2010-05-05
I've just installed a fresh copy of kubuntu 10.04. When I activate the nvidia drivers I cannot logout. When I logout I get a black screen waiting forever. When I disable the nvidia driver I can logout and I am brought back to the login screen.

Any suggestions?

---

### Post by GSF1200S on 2010-05-05
Do you have 2 video cards in your computer? While I dont have the same issue, I had an issue with 10.04 where my monitor would shut off if I killed X or switched tty's. I solved it by adding this ppa to my System>Administration>Software Sources and updating my nvidia drivers to the latest version- see this page:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

After you add that ppa to update sources, allow it to reload, and your update manager should advise you that you have updates. After doing this, I would suggest disabling the ppa unless you really want to push your luck with bleeding edge updates ;) You might give the driver a shot even if you dont have two video cards.

Also, can you tell us what video card youre using?

---

### Post by tonsil on 2010-05-05
I'm using Nvidia Geforce 2 MX 400 and it's the only card in my system. I'll try what you suggested and see what happens. Thanks.

---

### Post by tonsil on 2010-05-05
I added the PPA and it downloaded 2 updates; they seemed to add some extra options like refresh rates, however still when I logged out my screen went black and never came out. I removed the nvidia driver now and I can log out. Are there alternatives to nvidia drivers? Currently I'm running a 1024x768 resolution and it looks ugly. When I switch to 1280x1024 I get the wrong refresh rate.

---

### Post by -humanaut- on 2010-05-05
There's a fix in the proposed updates. You can either activate it now or wait till its pushed in to the official updates which shouldn't be long.

---

### Post by cojoco on 2010-06-02
It happens on both of my computers.

One is an NVidia, one has ATI.

Nothing from the keyboard works, but I can ssh in from my laptop and kill the X server, which seems to be running at 100%

---

