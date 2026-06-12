---
title: "Problem running firefox or IE from wine"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by hsraghu on 2011-08-01
Problem running firefox or IE from wine
Pardon my linux knowledge
I have installed latest wine and firefox and ie7 tru wine.
The IE acts funny , firefox also looks not right.
example - i cannot get this link working , [http://www.cartoonnetwork.com/games/exonaut/game.html](http://www.cartoonnetwork.com/games/exonaut/game.html)

I think this uses unity web player and have installed the plugin also. still not able to run. Need this and few other sites like this for my kids to play games else I need to go back to windows which i hate to.
Also I want the dynamic fonts to work ex - [www.kannadaprabha.com]("http://www.kannadaprabha.com") , where kannada fonts does not load.
any help appreciated.

---

### Post by bodhi.zazen on 2011-08-01
Well, Linux is not a drop in replacement for Windows and Wine is not always so easy to use.

If all you want to do is run that web site, perhaps you are better off with Windows, or at least dual booting for a while until you get it sorted out.

Your best support for wine applications is winehq:

[http://www.winehq.org/](http://www.winehq.org/)

We can possibly help, but, do you have any idea what that site needs to run ? flash ? Silverlight ?

---

### Post by hsraghu on 2011-08-01
Hello this cartoonnetwork.com some games  runs unity webplayer. which I installed  as a plugin in IE and firefox from wine.
Still it displays blank. 
Other problem is kannada fonts does not load ex kannadaprabha.com

---

### Post by computerandu on 2011-08-02
> **hsraghu said:**
> Hello this cartoonnetwork.com some games  runs unity webplayer. which I installed  as a plugin in IE and firefox from wine.
Still it displays blank. 
Other problem is kannada fonts does not load ex kannadaprabha.com

Are there no suitable plugin in firefox (which is the default browser in ubuntu)?

If you want Kannada fonts then go to preference in firefox and add language there...

---

### Post by Jouke S on 2011-08-02
You don't need to run firefox through wine. Ubuntu offers many web browsers that work fine without wine (firefox, chromium, opera to name a few)

enter the command 'sudo apt-get install ubuntu-restricted-extras' in a Terminal and you should be able to run your game without any issues.

---

### Post by hsraghu on 2011-08-02
Thanks for the tips guys , but unfortunately , damn this  cartoonnetwork.com and some few other sites uses unitywebplayer     [http://unity3d.com/webplayer/](http://unity3d.com/webplayer/) 
I cant find any alternative plugin in linux . 
I will try chrome from wine which I have not tried yet.

Regarding the kannada fonts , I have installed all the avl from the  preferences in firefox. Still no luck for some sites uses dynamic fonts for other languages.

---

### Post by bodhi.zazen on 2011-08-02
Well, unless they make a linux version, it is unlikely you will get it working in wine.

I suggest you contact them directly as it is a third party and support here is going to be limited.

---

