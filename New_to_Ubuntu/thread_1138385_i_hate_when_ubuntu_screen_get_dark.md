---
title: "i hate when ubuntu screen get dark"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by evertsfnic on 2009-04-26
i know this question is just for the look, but i don't know you guys,
when a program works nice the screen looks bright, but when start to crash or the program it's too busy, the screen of the monitor get dark, or a less bright, i hate this, (it's the same thing with vista, but at least in vista i can take off the UAC), why you have to choose these idea, i think maybe another color, or a better idea. i am telling what i feel, ubuntu in every release it's getting better, but still it's kind of hard, i think ubuntu should made things easy like linux mint, when you install a program in linux mint you just have to make one click, and it's much, much better on the web site, that  in a box.

---

### Post by Sidewinder1 on 2009-04-26
Is it, perhaps, a RAM issue? Increasing RAM may totally eliminate the "gray-out".
Then you won't care what color it is 'cause you'll never see it.

:-)

---

### Post by steve101101 on 2009-04-26
yes. what are your specs. also install programs in synaptic or add/remove programs is just about down to a single click and entering the su password.

---

### Post by ubuntu27 on 2009-04-26
Windows or prgrams becoming dark is not caused by Ubuntu but by an third party visual effects program called Compiz-fusion.

Install [compizconfig-settings-manager]("apt://compizconfig-settings-manager") if you don't have it installed.

Open it by going to System menu---->Preferences --->>>CompizConfig Settings Manager

Look for **"Negative"** effect and uncheck the box next to it. 
And click on Apply button if there is one. 


That is all :)


You can now close it or experiment with CompizConfig Settings Manager.

---

### Post by fooman on 2009-04-26
if your referring to the grayish, faded out windows when the system is busy....then yeah,  i hate it also.

thats why i turn that feature off.

i am not sure if it available by default in intrepid or previous versions,  but in jaunty just install the compizconfig-settings-manager package from synaptic, or type/copy/paste the following in a terminal:

```
sudo apt-get install compizconfig-settings-manager
```after it installs,  open it in system > preferences > compizconfig settings manager.

then look under effects > fading windows and uncheck "dim unresponsive windows".

hope that helps.

edit:  in intrepid and earlier,  i first had to update to the latest compiz packages using their repos in order to have access to that plugin from ccsm.  if you need more info,  post back and i'll dig something up.  
using jaunty...it seems to be in the default version of ccsm.

---

### Post by evertsfnic on 2009-04-26
thank, i will try it, but what i am trying to say it's why get gray-dark by default, there's a lot of think that could be better, ubuntu it's great, but linux mint it's better, even that linux mint is a song of ubuntu, like the wallpaper it's horrible, the theme it's not so good, (i like opensolaris theme better for default), so what i am tring to say it's that you can make better icon, better theme, more color. i know it's better but it need more make up.......

---

### Post by nandemonai on 2009-04-26
> **evertsfnic said:**
> thank, i will try it, but what i am trying to say it's why get gray-dark by default, there's a lot of think that could be better, ubuntu it's great, but linux mint it's better, even that linux mint is a song of ubuntu, like the wallpaper it's horrible, the theme it's not so good, (i like opensolaris theme better for default), so what i am tring to say it's that you can make better icon, better theme, more color. i know it's better but it need more make up.......

This is where themes come in.

---

### Post by evertsfnic on 2009-04-26
i have a computer with 1 giga of ram, 2 gigahertz of procesor, 256 of video card, so i think that should be good. sorry for me english.

---

### Post by Sidewinder1 on 2009-04-26
Certainly not a RAM or clock-speed issue. 
No need to apologize for your English; you get your thought/point across and communicate very well. 
Now, if I tried to communicate in any language other than English, **that** would require an apology
And, my wife is constantly telling me to "watch my language". 
:-)

---

