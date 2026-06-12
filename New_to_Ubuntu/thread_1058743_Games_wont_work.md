---
title: "Games wont work"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by rjg117 on 2009-02-03
Hey I just downloaded some games from add/remove applications, and none of them are working. I click on one, and nothing happens. The games I downloaded are:

freeciv
glest
supertuxcart
TORCS
Warzone 2100
xmoto

When I click on a game in the menu, nothing happens at all. All of the other games I have work just fine.

One of the games, (glest) begins to open, but then it closes again and doesnt work.

Any help would be greatly appreciated. Thanks

---

### Post by johnjohn2 on 2009-02-03
What graphics card are your unning and what are your system specs

---

### Post by ajcham on 2009-02-03
Have you tried launching the games from a terminal?  This will allow you to see any error messages which may help to diagnose the problem.

---

### Post by rjg117 on 2009-02-03
Graphics: Nvidia GeForce 8600GT 512m
Ram: 3.5 gig
CPU: intel core duo CPU 3.00GHz, intel core duo CPU 3.00GHz
Running intrepid

Also, I'm pretty new to Ubuntu, I'm not really sure how to run the games using terminal..

Thanks

---

### Post by cmay on 2009-02-03
i almost never use the restricted drivers so i never have the advanced visual effects enabled other than on my media-center which can not work with out the restricted drivers. on my computers wiht out desktop effects enabled all games other than supertux will behave like you describe so i think it has something to do with either you have not enabled the desktops effect or maybe as others are trying to figure out your card just does not work right in this context.

---

### Post by rjg117 on 2009-02-03
Ah. I figured it out. I went to system, hardware drivers, and enabled accelerated graphics driver. Thanks for the help. I feel kindof stupid now >.>

---

### Post by ajcham on 2009-02-03
> **rjg117 said:**
> Also, I'm pretty new to Ubuntu, I'm not really sure how to run the games using terminal..
Simply open the terminal: Applications » Accessories » Terminal.

In the terminal window type the appropriate command for each game then press enter, for example:
```

glest
torcs
warzone2100
xmoto
```
I'm not certain of the commands for Super Tux Cart or FreeCiv, but a couple of the above should be sufficient to get an idea of the problem.  Copy and paste the output that the terminal gives you when the game fails to load.

---

### Post by computermacgyver on 2009-02-03
> **rjg117 said:**
> I feel kindof stupid now >.>

Not at all. We're glad its working for you now, and doubtless this thread will help someone in the same situation in the future. Cheers!

---

### Post by rjg117 on 2009-02-03
thanks :)

---

