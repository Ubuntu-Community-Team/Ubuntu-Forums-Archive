---
title: "reducing the  boot time"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by konsolelover on 2011-07-12
hey,
i just wanna know how can i make my system boot faster...i have removed many programs from startup using System->pref->startup applications. there is only few items like certificate and key storage,ssh key agent, print queue applet (i didn't uncheck it because idk what they actually do)...but it still takes 50-60 seconds to boot.I'm running Ubuntu 11.04 32 bit on my hp laptop with AMD Turion 64 bit 2.0 GHz and 3 GB RAM....ne help wud b appreciated ....

---

### Post by CVGH on 2011-07-12
Try this:


[http://www.ubuntugeek.com/boot-up-manager-bum-graphical-runlevel-editor.html](http://www.ubuntugeek.com/boot-up-manager-bum-graphical-runlevel-editor.html)

It is in the software repo's I believe....

---

### Post by konsolelover on 2011-07-13
tried but bum didn't help much.........still it takes 55 seconds to boot :(

---

### Post by Peter09 on 2011-07-13
Are you timing from start to login screen or login screen to desktop. Remember that your default startup programs will not be run until you login. Some things to check - is your bios saying you have a floppy drive, when you do not -  this means that you may have delays waiting for non-existant equipment to come available.

---

### Post by konsolelover on 2011-07-13
start to desktop.....I've selected automatic login to save time lol........n checked BIOS as well my first priority is my hard disk

---

### Post by matt_symes on 2011-07-13
Hi

Produce a bootchart using bootchart (funnily enough) to see where time is being taken.

```

matthew@matthew-laptop:~/my_documents/my_logons$ apt-cache search bootchart
pybootchartgui - boot sequence visualisation
bootchart - boot sequence auditing
matthew@matthew-laptop:~/my_documents/my_logons$
```

Post it on here if you want someone to have a look at it.

Kind regards

---

### Post by konsolelover on 2011-07-13
sorry but i couldn't get what you said....
i tried to run
> apt-cache search bootchart
and got the same result as yours
> bootchart - boot sequence auditing
pybootchartgui - boot sequence visualisation

did i have to do something else like installing bootchart??if yes then plz guide me to enough explanation as i'm nooobie to linux....

---

### Post by CVGH on 2011-07-13
Try installing using synaptic. That is where I found it...
This is what the output looks like:

---

### Post by psusi on 2011-07-13
Note that uploading the bootchart to the forums like that renders it useless since the forum shrinks it down to an unreadable resolution.  You need to post them at some third party image hosting site.

---

### Post by ian dobson on 2011-07-13
Hi,

Maybe try installing ureadahead. It builds a compressed file with all files needed to boot, which it loads on boot.

If your boot sequence in IO bound ureadahead can help alot.

Regards
Ian Dobson

---

### Post by psusi on 2011-07-13
> **ian dobson said:**
> Hi,

Maybe try installing ureadahead. It builds a compressed file with all files needed to boot, which it loads on boot.

If your boot sequence in IO bound ureadahead can help alot.

Regards
Ian Dobson

It is installed by default.  It likely isn't working though.  The bootchart can confirm that.

---

### Post by CVGH on 2011-07-13
> **psusi said:**
> Note that uploading the bootchart to the forums like that renders it useless since the forum shrinks it down to an unreadable resolution.  You need to post them at some third party image hosting site.

D'oh!!

---

### Post by matt_symes on 2011-07-13
Hi

> **konsolelover said:**
> sorry but i couldn't get what you said....
i tried to run

and got the same result as yours


did i have to do something else like installing bootchart??if yes then plz guide me to enough explanation as i'm nooobie to linux....

Sorry, I think i got a bit beyond myself.

```

matthew@matthew-laptop:~/my_documents/my_logons$ apt-cache search
bootchart pybootchartgui - boot sequence visualisation 
bootchart - boot sequence auditing 
matthew@matthew-laptop:~/my_documents/my_logons$
```The above command was meant to show you the name of the files not how to install them. I did not expect you to type it in and i should have made that clearer. Sorry about that.

It's a bit late now as you have used Synaptic but the command to install it via the command line would have been

```
sudo apt-get install bootchart
```The bootchart should give us an idea as to what is happening on your system and then, hopefully, we can help find a fix. :P

Kind regards

---

