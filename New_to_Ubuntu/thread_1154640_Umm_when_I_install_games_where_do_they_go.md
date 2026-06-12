---
title: "Umm when I install games where do they go?"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by xeticus on 2009-05-10
I opened up synaptic package manager and installed a open source FPS game Sauerbraten. I'd read good things and wanted to try it. Synaptic installed it but after that I couldn't find it. It wasn't installed in the applications menu and I have no idea where it is. I'm using 9.04 and there doesn't appear to be a category for games. This happened with another game I installed the same way. Rise of the Triad. Some programs like VLC and Kaffeine install and are easy to use. Some I'm clueless on how to get them started. How do I find my games and get them to work?

---

### Post by ad_267 on 2009-05-10
Sometimes the applications don't add a launcher to your menu. Try pressing alt-f2 and running "sauerbraten". If that works you can edit your menu and add an entry for sauerbraten by right clicking on the menu and selecting "Edit Menus".

---

### Post by xeticus on 2009-05-10
> **ad_267 said:**
> Sometimes the applications don't add a launcher to your menu. Try pressing alt-f2 and running "sauerbraten". If that works you can edit your menu and add an entry for sauerbraten by right clicking on the menu and selecting "Edit Menus".Ubuntu Forums


I'm a real noob so don't be surprised by what happens next. I press alt+f2 and the search bar comes up. I type in Sauerbraten. I press enter. Nothing happens. I know the package installed but I'm at a loss.

---

### Post by jojo1224 on 2009-05-10
I noticed on Ubuntu 9.04 that the menu won't always update until you logout and log back in.

---

### Post by xeticus on 2009-05-10
Yeah i tried that also. That's how I got Kaffeine to work. I logged out and in a couple of times. Nada.

---

### Post by ad_267 on 2009-05-10
Did you type Sauerbraten or sauerbraten? You need to type it all in lowercase.

---

### Post by xeticus on 2009-05-10
> **ad_267 said:**
> Did you type Sauerbraten or sauerbraten? You need to type it all in lowercase.
Yup all lower case. I can see in Synaptic that the package is installed. I'm just kinda lost from there.

---

### Post by 3rdalbum on 2009-05-10
Hmm, that program should create a menu item. Maybe you should try reinstalling just the "sauerbraten" package? (no need to reinstall the sauerbraten-data package).

If that doesn't work, in Synaptic find the sauerbraten package, right-click and go to Properties, and then look in the Installed Files tab. That will tell you the exact path of the Sauerbraten executable, and you can create your own launcher.

---

### Post by xeticus on 2009-05-10
I got it working. It seems under systems I have 2 package managers. One says Synaptic and one just says Add/Remove Applications. I used the latter one and it installed easy as pie. Thanks for bearing with me.

---

