---
title: "Java problems"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2011-07-07
In my spare time i play on pogo.com
I am running 11.04 and all has been great since the upgrade, apart from a few problems i had with Sun Java. I post here about the problems, and got help on installing IcedTea. All was well for a coupe of weeks, but now IcedTea is getting terrible.
I click on a game, and the popup window will open and start to load the game. Very rarely it will load the game, and then Firefox will crash, but more often than not the window will just sit there doing nothing, then after a while, crash Firefox totally. Its getting ridiculous . I searched the web yesterday and tried a few things that have been suggested in Forums, but no good.
What is worse, is that on my Wiindows XP pc, all is ok (get the odd problem, but it is and acsient pc)
Can anyone help please ?
Should i get rid of IcedTea (and anything else) & re-install Sun Java. Maybe its getting clogged up somewhere and needs a clear out.
Please dont make me go back to XP......love using Ubuntu


img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by MadMonkey1966 on 2011-07-07
hmmm what is that rubbish at the bottom, it wont let me delete it ?

---

### Post by MadMonkey1966 on 2011-07-08
Bump, still no good :(

Could someone please tell me how to un-install IcedTea(well , that is in Firefox) and re-install everything fresh.

I have the same problem with chromium, i guess that must use IcedTea as well.

Then what is best to install ? As i said i have very few hassles when using my XP backup PC :confused:

---

### Post by cavh on 2011-07-08
See [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")


If your system has more than one version of Java, type the following command in a terminal window:

```
sudo update-alternatives --config java
```

---

### Post by gandaran on 2011-07-08
> **MadMonkey1966 said:**
> Bump, still no good :(

Could someone please tell me how to un-install IcedTea(well , that is in Firefox) and re-install everything fresh.

I have the same problem with chromium, i guess that must use IcedTea as well.

Then what is best to install ? As i said i have very few hassles when using my XP backup PC :confused:
open synaptic package manager and scroll down to icedtea6-plugin, mark for complete removal and click apply, you may remove all openjdk-java packages if you wish too, I would recommend to install and use sun-java only, if you already have the canonical partner repository enabled (and updated packages) then in synaptic mark the sun-java6-plugin for install.

---

### Post by MadMonkey1966 on 2011-07-08
Followed your instructions gandaran and all went well :)

I tried a couple of games, and Firefox did not crash, so i think its a success.

Many thanks for your help, lets hope it keeps working ;)

---

