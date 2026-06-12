---
title: "A couple issues for a new ubuntu user"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by keithconly on 2009-01-08
Hi everyone i have using ubuntu for about a week now and loving it. However i have run into a couple issues over the past week.

1. Steam

I have ran into about every problem when trying to get this to work. I have tried tutorials and everything. Can someone please help with the install, as if they were explaining it to a 'noob' (right now i have it installed, probably not properly and im stuck at updating steam, it wont go any further)

2. Netflix Instant Watch

Is it even possible to do this? And if so how?

3. Game issues

When playing games, even if the game is meant for linux (only fullscreen games, openarena, warzone 2100) the game runs fine for about a couple minutes, than the game freaks out, colors go all crazy and fonts are not visible, any ideas of how to fix this?

4. Uninstall and Download locations

How exactly do i remove apps that are not in my Add/Remove? Also where do my mozilla firefox downloads locate to?

5. theorangesplat.com

Trying to relive my childhood lol, i went to this site to only to find the divx videos will not play. I have mplayer plugin and have streamed other divx videos, but this site will not work, possibly the site?

Here are my specs if needed:
Dell latitude E4300
2.4 dual core processor
4GB of RAM
running 8.10 32bit


Im sorry to burden everyone with all these problems, any help would be great, thank you

---

### Post by Facetious Falcon on 2009-01-08
Not sure about your first two questions but if you want to remove a specific application the best way is to go to System->Administration->Synaptic Package Manager, press Ctrl+F and then type the app there. Click on the app in question and 'mark for complete removal' then click apply.

To check where you're downloading to go Edit->Preferences in Firefox and look at the bit at the bottom where it says 'save files to'.

I'm not too sure about running DivX through a browser but the best way to view it if you can get it on your comp is through VLC media player (on add/remove).

---

### Post by keithconly on 2009-01-08
Thank you about the Synaptic Package manager and the firefox question :)

---

### Post by dark_harmonics on 2009-01-08
> **keithconly said:**
> Hi everyone i have using ubuntu for about a week now and loving it. However i have run into a couple issues over the past week.

1. Steam

I have ran into about every problem when trying to get this to work. I have tried tutorials and everything. Can someone please help with the install, as if they were explaining it to a 'noob' (right now i have it installed, probably not properly and im stuck at updating steam, it wont go any further)

2. Netflix Instant Watch

Is it even possible to do this? And if so how?

3. Game issues

When playing games, even if the game is meant for linux (only fullscreen games, openarena, warzone 2100) the game runs fine for about a couple minutes, than the game freaks out, colors go all crazy and fonts are not visible, any ideas of how to fix this?

4. Uninstall and Download locations

How exactly do i remove apps that are not in my Add/Remove? Also where do my mozilla firefox downloads locate to?

5. theorangesplat.com

Trying to relive my childhood lol, i went to this site to only to find the divx videos will not play. I have mplayer plugin and have streamed other divx videos, but this site will not work, possibly the site?

Here are my specs if needed:
Dell latitude E4300
2.4 dual core processor
4GB of RAM
running 8.10 32bit


Im sorry to burden everyone with all these problems, any help would be great, thank you

1. I dont know much about steam but i know that wine is the software you need to natively run windows software. Check out this wineHQ article on steam: [http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

2.To get instant watch to work: [http://www.hackszine.com/blog/archive/2007/01/netflix_instant_watching_in_fi.html](http://www.hackszine.com/blog/archive/2007/01/netflix_instant_watching_in_fi.html)

3. did you install any support for your graphics hardware from the hardware drivers under system administration? If so and its still not working you might want to disable compiz while you play games. hit alt+f2 and type metacity --replace. When you are done playing and you want to enable your effects again hit alt+f2 and type compiz --replace.

4. Already Answered

5. Add the 3rd part repository for Mediubuntu. for instructions check here [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
After you have that added you can add support for proprietary formats either through synaptic packagemanager or the command line.

In synaptic you can add w32codecs and ubuntu-restricted-extras or at a command line type:
```

sudo apt-get install w32codecs ubuntu-restricted-extras
```

I really hope any of this helps you get started! :)

---

### Post by keithconly on 2009-01-08
Wow, thanks a million, i will get started and let you know how it goes! Love the support around here.

---

### Post by chrisod on 2009-01-08
I don't think the Netflix instant watch will work at all. Linux simply does not support the DRM that cripples that feature.

---

### Post by dark_harmonics on 2009-01-08
> **chrisod said:**
> I don't think the Netflix instant watch will work at all. Linux simply does not support the DRM that cripples that feature.

You could be right i never actually tried it (i dont have netflix to test)

---

### Post by keithconly on 2009-01-08
1.Still no luck with steam :(

2. yeah, that hack is for it to work in firefox, thanks though

3. how do i make sure i have the right drivers?

4. solved:D

5. i am getting this error

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
keith@keith-latitude:~$ 

and now when i try to update my Add/Remove list i get this error

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263


what did i do wrong?

---

### Post by oldos2er on 2009-01-08
You need the key for that repo: [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg)

---

### Post by keithconly on 2009-01-09
what am i supposed to do with that key lol?

---

### Post by oldos2er on 2009-01-09
Go to System, Administration, Software Sources, Authentication, and import the downloaded *gpg file. Then reload your sources.

---

