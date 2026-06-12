---
title: "Japanese on WINE"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by darkfeline on 2009-05-10
I can't get Japanese characters to display properly on Wine.  I'm using Ubuntu Intrepid.  I've tried Googling it, but the only solutions I've found (there were only a few), involved using a font called Vera Sans Yuanti, and the fixes were both from a few years back.  I tried looking for this font, but couldn't find it anywhere. Can someone help?

---

### Post by ashmew2 on 2009-05-11
Hi , I looked around a bit myself and im pretty sure that this is what you should be looking for : [http://warrence.com/tech/?p=26](http://warrence.com/tech/?p=26)

And nice thing you mentioned the font's name otherwise it would be a pain to find you that link. That should fix you right up.

---

### Post by darkfeline on 2009-05-11
Cool, I'll go look at that.

---

### Post by KagetsukiZero on 2009-05-11
As a Japanese Linux user I really wanted to get WinE to display Shift-JIS. At that point in time I looked it up and went so far as to ask about it on the Wine mailing list etc.

Basically, there are hacks such as the link provided above... but weather or not they will work will depend on the application. Unfortunately the circuit board layout programs I wanted to run did not conform and did not work with the hacks I tried, but some other software did (photoshop 7 for example). At this point in time I've got windows XP running in virtual box and that seems to work great, and the seamless mode integration works quite well. My only quarrel with it is virtualbox doesn't like my Japanese keyboard and the keyboard layout acts like an American keyboard... and I don't know where most of the symbols are. Luckily I don't do much typing in the virtual machine (when I write code for windows I put the project in a shared folder, code in gvim and just hit the compile/run/debug button when I need to). I should note MS Visual Studio did not run in Wine, and IME input would take down (crash) most applications in WinE as well. 

So, if you can't get WinE working I would try putting a virtualbox installation on. It's unfortunately bulky and certainly slower, but WinE just doesn't handle certain things well and Japanese was most definitely one of those things.

---

### Post by ashmew2 on 2009-05-11
> **KagetsukiZero said:**
> As a Japanese Linux user I really wanted to get WinE to display Shift-JIS. At that point in time I looked it up and went so far as to ask about it on the Wine mailing list etc.

Basically, there are hacks such as the link provided above... but weather or not they will work will depend on the application. Unfortunately the circuit board layout programs I wanted to run did not conform and did not work with the hacks I tried, but some other software did (photoshop 7 for example). At this point in time I've got windows XP running in virtual box and that seems to work great, and the seamless mode integration works quite well. My only quarrel with it is virtualbox doesn't like my Japanese keyboard and the keyboard layout acts like an American keyboard... and I don't know where most of the symbols are. Luckily I don't do much typing in the virtual machine (when I write code for windows I put the project in a shared folder, code in gvim and just hit the compile/run/debug button when I need to). I should note MS Visual Studio did not run in Wine, and IME input would take down (crash) most applications in WinE as well. 

So, if you can't get WinE working I would try putting a virtualbox installation on. It's unfortunately bulky and certainly slower, but WinE just doesn't handle certain things well and Japanese was most definitely one of those things.

Why not install Win98/2000 instead of XP , theyll be much faster than XP inside a VM IMO..

---

