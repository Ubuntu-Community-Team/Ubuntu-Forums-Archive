---
title: "Add to Panel: Battery/Power (whatever it's called)"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by steigerjb on 2009-11-22
I feel dumb here. How do I add the battery/power icon to my panel? I don't think adding the notification area is what I want. That puts a blue battery icon (see attached). Isn't there supposed to be a way to add the battery icon to the panel where it adds a green icon (see attached)?

---

### Post by ukripper on 2009-11-22
Right click on your top panel bar-->Select Add to Panel-->Battery Charge monitor

---

### Post by steigerjb on 2009-11-22
> **ukripper said:**
> Right click on your top panel bar-->Select Add to Panel-->Battery Charge monitor

yeah, that's what I though but i don't have that listed....

---

### Post by cenzorrll on 2009-11-22
those two pictures are the same program under different themes. the green one is human, and (i think) the blue is clearlooks. it's the applet for the gnome power manger. if you right click it and chose preferences>general then click on the "always show" checkbox, it will stay up.

---

### Post by steigerjb on 2009-11-25
> **cenzorrll said:**
> those two pictures are the same program under different themes. the green one is human, and (i think) the blue is clearlooks. it's the applet for the gnome power manger. if you right click it and chose preferences>general then click on the "always show" checkbox, it will stay up.

i am using the human theme, why's it blue?

---

### Post by x C0MMAND0 x on 2009-11-25
This doesn't answer your question directly, but I use kpowersave

```
sudo apt-get install kpowersave
```

It has more features for power saving and a presentation mode settings which I really like.

---

### Post by steigerjb on 2009-11-25
i want to know how to add the Battery Charge monitor to my panel, it isn't listed

---

### Post by cenzorrll on 2009-11-27
> **steigerjb said:**
> i am using the human theme, why's it blue?

no idea, you can try poking around in system>preferences>appearance then click on the customize button and change the icons.  you may be missing the green battery icon for some reason and it reverted to something you do have.  beyond that i can't really say.  maybe try reinstalling gnome-power-manager from synaptic

---

### Post by lotharmat on 2009-11-27
I think with karmic the Battery applet was spliced into the Notification area and ditched as a standalone applet.

You may ba able to download it from the repo but I'm not too sure though.

---

### Post by mbzn on 2009-11-27
Not sure for 9.10 but in 9.04 go to system-preferences-power management then the general tab has an option to allways display the icon.

---

### Post by norbert26 on 2009-11-27
> **mbzn said:**
> Not sure for 9.10 but in 9.04 go to system-preferences-power management then the general tab has an option to allways display the icon.

yes comfirmd this works in 9.10 enter PW and make default.

---

### Post by bornagainpenguin on 2009-12-01
Anyone know how to add battstat back to Ubuntu manually?  I prefer the behavior of it to the default applet which not only is notoriously inaccurate is also not very informative.  The battstat applet (standalone battery applet) was a much better choice for inclusion as default than the POS the Ubuntu team decided to use.

What were they *thinking*?

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-12-04
Why does Synaptic still list the battstat as being a part of the panel plugins if it isn't?

--bornagainpenguin

---

### Post by steigerjb on 2009-12-05
see, the thing is. I made a Zelda theme for my brother (see attached). In Jaunty I had the heart meter as the battery icon LOL haha get it? But as you can see, in Karmic, it seems to be defaulting to clearlooks power icon or something. It does the same thing if I try and use the old human theme. I got it off my Jaunty cd and moved it to my Karmic. Why is it doing this????

---

### Post by bornagainpenguin on 2009-12-06
> **steigerjb said:**
> Why is it doing this????

Because Cannonical hates its users?

--bornagainpenguin

---

### Post by steigerjb on 2009-12-10
> **steigerjb said:**
> see, the thing is. I made a Zelda theme for my brother (see attached). In Jaunty I had the heart meter as the battery icon LOL haha get it? But as you can see, in Karmic, it seems to be defaulting to clearlooks power icon or something. It does the same thing if I try and use the old human theme. I got it off my Jaunty cd and moved it to my Karmic. Why is it doing this????

I am using this icon set [http://gnome-look.org/content/show.php/Minty+Leaf+Iconset+by+mickyz?content=107461]("http://gnome-look.org/content/show.php/Minty+Leaf+Iconset+by+mickyz?content=107461")

What should i call the attached battery icon and where should I put it so it works with Karmic Koala? There's gotta be a way. ](*,):-k:confused:

---

### Post by peterpan7191 on 2010-01-06
Im not much in2 these things but i jst referred 2 the location as mentioned by Phyxiis [http://ubuntuforums.org/showthread.php?t=1362117](http://ubuntuforums.org/showthread.php?t=1362117) and found the name 2 b 'gpm-battery*' instead of 'gpm-primary*' in the case of karmic .....
changin tat shud wrk... els replace the icons in the default location /usr/share/gnome-power-manager and try killall gnome-panel. this wrkd 4 me :)

---

### Post by peterpan7191 on 2010-01-06
[SIZE=2]Hey [/SIZE][steigerjb]("http://ubuntuforums.org/member.php?u=687872") try changin the name as mentioned abv i did notice many old themes r havin the same trble with some icons wonder y they changed the namin convention

---

### Post by bornagainpenguin on 2010-01-06
> **peterpan7191 said:**
> Im not much in2 these things but i jst referred 2 the location as mentioned by Phyxiis [http://ubuntuforums.org/showthread.php?t=1362117](http://ubuntuforums.org/showthread.php?t=1362117) and found the name 2 b 'gpm-battery*' instead of 'gpm-primary*' in the case of karmic .....
changin tat shud wrk... els replace the icons in the default location /usr/share/gnome-power-manager and try killall gnome-panel. this wrkd 4 me :)

Does this only fix the themes, or will this bring back battstat?  I don't know why Canonical decided to remove it from being an option when it still exists in pretty much every other Gnome distro...

--bornagainpenguin

---

### Post by steigerjb on 2010-01-08
> **peterpan7191 said:**
> Im not much in2 these things but i jst referred 2 the location as mentioned by Phyxiis [http://ubuntuforums.org/showthread.php?t=1362117](http://ubuntuforums.org/showthread.php?t=1362117) and found the name 2 b 'gpm-battery*' instead of 'gpm-primary*' in the case of karmic .....
changin tat shud wrk... els replace the icons in the default location /usr/share/gnome-power-manager and try killall gnome-panel. this wrkd 4 me :)

yep, worked. Thanks

---

### Post by vikingr on 2010-01-23
I was having the same problem, try right-click on the panel to open the 'panel properties', mark the box for 'show hide buttons', it brought all mine back.

---

### Post by nothingspecial on 2012-10-23
Please don't bump old threads to the top.

Closed.

---

