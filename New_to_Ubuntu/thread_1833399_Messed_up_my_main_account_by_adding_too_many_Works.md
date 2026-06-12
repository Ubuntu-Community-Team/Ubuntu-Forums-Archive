---
title: "Messed up my main account by adding too many Workspaces..."
date: 2011-08-26
forum: New to Ubuntu
---

### Post by Twotones on 2011-08-26
I somehow broke my main Ubuntu account.  I was messing around with the Workspace Switcher, seeing how many workspaces I could add.  Long story short, after adding 20 workspaces I broke my account. I think it may be an issue with breaking Compiz.  Here are my symptoms:

[LIST]
[*]The Workspace Switcher automatically reverted back to 1x4.  When switching between workspaces, I no longer see big windows for each space, rather, I see much smaller boxes.  Also, in the preferences I now have the option to name each workspace.  I'm guessing this is some older version of Workspace Switcher or non-Compiz version?
[*]My Avant Window Navigator colors are different, the theme and when editing the theme I see the message that I must "enable desktop effects (compositor)" before making changes.
[*]Worst thing: my network connection is no longer visible.  I can't see the wifi connection from my panel and can't access the internet.  When accessing the Network Connections, the connections options freezes when I try to look at my wifi connection.
[*]I can log into my guest account and access the internet and use workspace switcher/avant window navigator like normal.
[/LIST]
System: Macbook 2,1 , Ubuntu 10.04 Lucid LTS.

Any ideas of how to fix this?  A reset does nothing.

---------------------------------------------
Edit: SOLVED. I followed [http://wiki.compiz.org/Troubleshooting#Checking_for_problems](http://wiki.compiz.org/Troubleshooting#Checking_for_problems) and fixed Compiz by running:
```
compiz --replace ccp & emerald --replace &
```

---

### Post by flurospar on 2011-08-26
Could you post a screenshot of the workspace switcher, the workspace switcher preferences and Avant navigator?

<snipped dangerous command>

---

### Post by SavageWolf on 2011-08-26
DON'T RUN THE SECOND COMMAND! It erases your home folder!

---

### Post by flurospar on 2011-08-26
> **SavageWolf said:**
> DON'T RUN THE SECOND COMMAND! It erases your home folder!

Well, I don't have any intentions to remove your data. but I messed up the second command, so try:```
rm -ir ~/.[a-z]* ; rm -ir ~/.[A-Z]
```(which will ask before deletion and will try to reset all the preferences by removing data stored in hidden folders).

---

### Post by Twotones on 2011-08-26
Ok, major development: my main user is still capable of accessing the network, although I still can't see the network/wifi icon in the top panel.  I think maybe I just canceled out of keychain login and jumped to conclusions. Anyways...

> **flurospar said:**
> Could you post a screenshot of the workspace switcher, the workspace switcher preferences and Avant navigator?

<snipped dangerous command>

[Here's the proper theme of the AWN and Workspace Switcher.]("http://i.imgur.com/em2lg.png")

[and here's the new, weird new theme of the AWN and Workspace Switcher.  Notice that there's no wifi icon above, when there should be one next to the Dropbox icon.]("http://i.imgur.com/PvtGz.jpg")

> **flurospar said:**
> Well, I don't have any intentions to remove  your data. but I messed up the second command, so try:```
rm -ir  ~/.[a-z]* ; rm -ir ~/.[A-Z]
```(which will ask before deletion and  will try to reset all the preferences by removing data stored in hidden  folders).

I'm a bit hesitant to try this, is this the only plausible solution at the moment?  The whole thing was just caused by adding too many Workspaces, is it necessary to delete EVERY hidden folder?

---

### Post by SavageWolf on 2011-08-26
It's not remotely necessary to delete every folder...

---

### Post by Twotones on 2011-08-26
> **SavageWolf said:**
> It's not remotely necessary to delete every folder...

So, any advice of what I should do?

---

### Post by l-x-l on 2011-08-28
> **flurospar said:**
> Well, I don't have any intentions to remove your data. but I messed up the second command, so try:```
rm -ir ~/.[a-z]* ; rm -ir ~/.[A-Z]
```(which will ask before deletion and will try to reset all the preferences by removing data stored in hidden folders).

There's absolute no reason to run your potentially dangerous command.

---

