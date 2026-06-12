---
title: "updating, ´linux-generic meta-packages´"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by cannonballsimp on 2010-08-21
[FONT=Verdana]Hi

I´m an Ubuntu beginner, using Lucid Lynx LTS, which automatically downloaded some updates yesterday. The Update process crashed when I clicked ´Install Updates.´ This morning, it downloaded the updates again, and I noticed the following text in the ´description´ tab:[/FONT]

[INDENT][FONT=Microsoft Sans Serif]You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed.[/FONT]

[/INDENT][FONT=Verdana]Is this perhaps the problem? If so, How do I install the linux-generic meta-package?[/FONT]
[FONT=Verdana]

Thanks
Simon[/FONT]

---

### Post by jmfal on 2010-08-21
Welcome to Ubuntu

OK, open software sources: system>administration>software sources
put a check in the boxes except for source unless you added a ppa(source code)repo
uncheck the cd box

click other software put checkin all boxes, close, may say not up to date, reload, will close

open synaptic: scroll down to meta packages, its probably already installed.

are you having some problem or do you just want to install this package?

---

### Post by jtarin on 2010-08-21
This WILL solve the problem. Go to Synaptic, on the left at the window that says ALL at the top scroll down to Meta Packages click it, then on the right scroll down to linux-image-generic that is what you need. But the easy way is to click the box Mark all upgrades near the top then click apply let it do its thing and you are done.

---

### Post by L Campbell on 2010-08-21
> **jtarin said:**
> This WILL solve the problem. Go to Synaptic, on the left at the window that says ALL at the top scroll down to Meta Packages click it, then on the right scroll down to linux-image-generic that is what you need. But the easy way is to click the box Mark all upgrades near the top then click apply let it do its thing and you are done.

Hi, I followed your instructions here and all went well until I came to 'Apply'.

Apply is not a 'hot key', (or whatever the technical term is) so nothing happens when I click on it.

Is there something else I should do?

TIA

---

### Post by jtarin on 2010-08-21
Close Synaptic and open it from the terminal with ```
gksudo synaptic
```then follow the instructions

---

### Post by jmfal on 2010-08-21
when you clicked mark all upgrades did a window popup stating what is going to be done, if there is click ok then apply will be highlighted, click apply. 

if a window did not popup your system is up to dateif you think you need to update/upgrade try in a terminal: applications>accessories>terminal>

        ```
  sudo apt-get update
```

and

           ```
 sudo apt-get upgrade
```

---

### Post by cannonballsimp on 2010-08-21
Thanks, this worked

---

