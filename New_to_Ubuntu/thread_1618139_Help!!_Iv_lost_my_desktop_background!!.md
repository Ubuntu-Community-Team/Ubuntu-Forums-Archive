---
title: "Help!! Iv lost my desktop background!!"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by mikibish on 2010-11-10
Right first off I'm running Ubuntu 10.10 on an Acer Aspire one D260.

The problem is that iv managed to loose my desktop background...
I think it might have something to do with Gnome color chooser as it was the last thing I was using before it happend... I was messing about in the engiens tab with global, trying to follow some thread to with transparency... to be honest im not even sure why i had to go in there... but i did...

When I restarted my background was gone, every time i try and change the background it crashes... iv tried the "killall nautilus" command and gone into the "gconf-editor" to check "draw_backgroun" is enabled. Oh and before anyone asks, yes i can still have icons on the desktop

I'm really hoping for an easy fix if anyone know what the hell iv done??

P.s. i can see some of the background behind the panel if i set it to transparent, i don't know if thats any help?

---

### Post by mikibish on 2010-11-11
I'm now thinking it has something to do with my windows manager as im able to see it for a split second if i switch it from compiz to metacity nd vice versa.

---

### Post by moody_mark on 2010-11-11
Hi, Your backgrounds should be in /usr/share/backgrounds/ do you have files there? Under your home directory theres a directory called .gnome2 try cd to that and then you should see a file called backgrounds.xml. In this file you should have entries like this

  <wallpaper deleted="false">
    <name>Maraetai before sunrise</name>
    <filename>/usr/share/backgrounds/Maraetaibeforesunrise.jpg</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#09091d1d5c5c</pcolor>
    <scolor>#09091d1d5c5c</scolor>
  </wallpaper>

Do you have these ok? Ive not dabdled with this file, but it looks like pretty plain xml perhaps this file is missing or screwed up. Ive attached my file for you to compare. It might help hopefully

[ATTACH]175305[/ATTACH]

---

### Post by mikibish on 2010-11-11
yeah iv got files in usr/share/backgrounds
and also i have the background.xml and it appears to be correct. so no luck there...

iv been trying to think of a better why of describing whats going on and it seems like there is a separate background pasted over the top if thats even possible?

Iv attached a screen shot if thats any help at all? the panel is transparent so you can see the background behind it

---

### Post by mikibish on 2010-11-25
Anyone?? help please :)

---

### Post by bvpainter on 2010-12-03
I've got exactly the same problem.

---

### Post by mikibish on 2010-12-08
I no longer have this problem had to do a reinstall.
I don't believe there is no fix for this problem but I'll be damned if I could figure it out...

---

### Post by bvpainter on 2010-12-08
I re-installed all my backgrounds and lo and behold things are back to normal.

---

