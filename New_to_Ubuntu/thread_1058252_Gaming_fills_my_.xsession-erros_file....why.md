---
title: "Gaming fills my .xsession-erros file....why???"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by sad_iq on 2009-02-02
Ok...here goes...today I noticed that my favourite game(Urban Terror) is working really slow for me (it dropped from 125 to 30 FPS) with no aparent reason, and after my gaming session my xsession-errors file is flooded with the log from that game(who killed who, who killed me...etc). That could explain the massive FPS drops, as the HDD is working continuously and xorg eats upto 40% of my CPU, what I can't explain is WHY does this file gets flooded with the logs from that game??
 Any way to stop it from "reading" those logs??

---

### Post by Sealbhach on 2009-02-02
I play Urban Terror and I've got those messages as well:

> awnCrow.De entered the game
cancerbero was taken out by CAGUENSOS's PSG1. Plink!
remialdo was on the wrong end of Kalimah's G36.
You hit Snabben in the Legs for 11% damage.
wit joined the blue team.
wit entered the game
You hit Snabben in the Legs for 11% damage.
You hit Snabben in the Torso for 30% damage.
You hit Snabben in the Torso for 30% damage.
You hit Snabben in the Torso for 30% damage.


Maybe the slow FPS is due to problem with grpahics driver, I don't have any probs with UT.


.

---

### Post by sad_iq on 2009-02-02
Well...it wasn't slow for me till now, and the game wasn't logging anything in xsession-errors file(I check that file almost daily). I don't think it's the drivers fault...like I said I was playing with almost constant 125 FPS, but now I play with 30 FPS (not constant). The only difference in my system is that file gettin filled with useless logs causing xorg to eat almost half my CPU...and my HDD will melt if this can't be fixed, :(

---

### Post by mjheagle8 on 2009-02-02
there must be an error in the game(s) that occurs frequently and fills up the file.

---

### Post by sad_iq on 2009-02-02
I don't see why any game-related errors should end up in .xsession-errors...anyway...here's the log, after a fresh restart.I started the game, watched a demo, exited the game and started tvtime:
 [http://paste.ubuntu.com/112981/](http://paste.ubuntu.com/112981/)

---

### Post by mjheagle8 on 2009-02-02
it seems that for some unknown reason urban terror is writing its instructions/text output to that file...

---

### Post by sad_iq on 2009-02-03
bump?

---

### Post by sad_iq on 2009-02-03
I've managed to partially solve the issue by adding "> /dev/null" to the command I use to start the game (/home/username/Games/UrbanTerror/ioUrbanTerror.i386 > /dev/null), and it seems to release some stress from xorg and the HDD. Is this the right way to do it or is it another "safer" way to acomplish this?

---

### Post by change_mode on 2009-02-19
Same problem here. I discovered it by accident more or less, so I don't know for how long it's been doing that.
I'd really like to know if this is the game's or ubuntu's fault. Should be easily fixed once someone takes the time to look into it.

Is it ok to just add > /dev/null? What happens if the game needs to write to configuration files or something?

---

### Post by sad_iq on 2009-02-19
Well...I've been experimenting with no luck how to get rid of that logging. After a longer period of gaming my .xsession-errors file gets filled(there's a limit to how much errors get logged in there I think), and my system performs better. However, what really made a difference was the new nvidia driver (180.29), wich raised my FPS to a playable level.

---

### Post by sad_iq on 2009-02-23
OK...I managed too implement >/dev/null properly now and the logging has dissapeared...I've posted the workarround here: [http://forums.urbanterror.net/index.php/topic,14290.0.html](http://forums.urbanterror.net/index.php/topic,14290.0.html)

---

