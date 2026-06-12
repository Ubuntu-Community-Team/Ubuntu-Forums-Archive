---
title: "[SOLVED] Help with openbox menu!"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by bhadotia on 2008-12-18
When I installed openbox last time, I automatically got a submenu in my openbox menu which listed all my apps. Now  when I reinstalled ubuntu (and openbox), I automagically don't have that menu.
After some RTFMing (the F stands for **f**ine- in case anybody wonders:D), I find that I have a submenu in my ~/.config/openbox/menu.xml file called debian as shown below:
```
<!-- This requires the presence of the 'menu' package to work -->
  <menu id="Debian" />
```
but for some reason the submenu is not showing. As far as I can recall there was a link to some file in the above line in my previous openbox install. But I can't seem to remember the file that the link pointed to. 
So, now you know what the problem is, can someone please help me figure out where I'm going wrong.
P.S.:
I have already tried:
```
sudo update-menus
```
and of course I have the menu package installed.

Many thanks in advance:KS:KS:KS

---

### Post by bhadotia on 2008-12-18
Just found this [link]("http://icculus.org/openbox/index.php/Help:Menus#The_Debian_menu") and its working now. 


Wow!, this going through manuals sure is tough but it fun when they help you solve the problem that was originally a consequence of your ignoring the manual at the first place:popcorn:

---

