---
title: "Lost compiz and extra visual effects after openGL update on 10.10"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by trikster_x on 2010-10-20
I did a version upgrade and update today on my aspire one AOA150, and now I can no longer enable compiz.  Everything worked great right up to the point I tried to run the updates for openGL.  That is when compiz stopped working.  Now when I try to enable the extra visual effects I get the looking for drivers window, then a message saying that my system could not enable desktop effects.  

I have tried to reinstall everything from compiz to the video drivers for the intel graphics accelerator, but I get the same result.

Any suggestions on how to fix it?

---

### Post by ephestione on 2010-10-20
I am having the same exact problem, using intel 9450 (or what's his name) video system on my toshiba satellite.
Extra effects didn't work right after upgrading to maverick from lucid, and on top of that the "close/minimize/maximize" icons were lost, I manually removed all compiz packages and reinstalled, after which everything worked, but extra setting for visual effects was lost randomly, and went back to "none".
Now, right after the upgrade, the window icons disappeared for a short while and then misteriously reappeared, but I can't enable normal nor extra visual effects again.

EDIT: for some unintelligible reason the repository for "latest compiz packages" in ubuntu tweak, which I had to disable in order to solve the first problem I had after upgrade, had been reenabled (?).
Disabling that from source editor, updating with aptitude, uninstall all packages with *compiz* in synaptic, then issuing a
```
sudo apt-get install compiz compiz-plugins compiz-gnome compiz-core emerald compiz-fusion-plugins-main compiz-fusion-plugins-extra fusion-icon compizconfig-settings-manager

```restored everything, let's see if now compiz keeps losing randomly the extra visual effects

EDIT 2: there, it's not even been 10 minutes, and the extra visual effects were disabled behind my back. It just happens randomly, and I realize it because closing the windows doesn't show the cool burn up effect I setted.
One thing I noticed is that whenever extra effects are disabled to "none", also the advanced effects in compizn settings get disabled. I just re-enable the extra without enabling the advanced effects, lets see if those are the problem.

EDIT 3: nope, went to set effects in compiz manager, with advanced effects disabled, and extra effects were disabled once again as soon as I double ckicked in "open window effects" to change the fade animation to something else. There is definitely something wrong with intel 945 and compiz under maverick... never had such problems with lucid

---

### Post by trikster_x on 2010-10-20
I can verify everything in ephistione's post, it all happens exactly the same on my computer.  I removed the intel video drivers last night to try and force ubuntu to find and install the latest drivers when I attempt to enable extra effects, but it doesn't even search for the drivers unless I already have them installed.  This is a major crutch for me when I came from a fully working system pre-upgrade.  

If there is nobody who has managed to fix this on their comp, or has an idea on what it could be, let us know.  Or if someone knows how to downgrade a distro, that would be good too.

---

### Post by ephestione on 2010-10-20
I just opened a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/663788](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/663788)
But I just checked and theres plenty of similar reports :D

---

### Post by trikster_x on 2010-10-20
I got it working!!!

so here is what I had to do:

Remove EVERYthing compiz related: Go to synaptic, type in "compiz" in the search bar, and ANYTHING that is installed, completely remove.

If you are using the ppa or any other compiz related repos, disable those in your software sources list.

Close synaptic.

run:
```
sudo apt-get autoclean
```
then back to synaptic and reload your package info. (in synaptic, "EDIT>>reload package information")

Edit: As ephistione pointed out, I forgot to mention a couple packages.  Here is the full package list for compiz-emerald install:

```
sudo apt-get install compiz python-compizconfig compiz-plugins compiz-gnome compiz-core compiz-fusion-plugins-main fusion-icon compizconfig-settings-manager compizconfig-backend-gconf libdecoration0 compiz-fusion-plugins-extra emerald libemeraldengine0
```

Just copy/pasta that command into a terminal or you can type compiz into the search of synaptic and check any of the packages listed in the command above.

Log out and back in to restart X.

I hope this helps anyone else having this problem.

---

### Post by Casey R on 2010-10-20
Having the exact same problem, and trikster's post didn't work for me either :(

---

### Post by Casey R on 2010-10-20
Getting read of the Compiz PPA fixed it! Woohoo!

---

### Post by ephestione on 2010-10-21
Yup, I confirm compix's ppa messes everything up.
Anyway your procedure is the same one I used, exdceot one detail: you do not suggest to install compiz plugins extra, nor by installing just compizconfig settings manager you end up installing compiz-gnome, so you miss two packages that, at least in my case, made the desktop look really ugly (weird windo frames and close/minimize buttons). Also, no advanced animation effects in settings, which were the ones I wanted the most (burn up effects on open/close and skewer on minimize/maximize rule :p).
So I installed those two as well and it's working... for now.
I already removed and reinstalled compiz twice before this time, and it started working again, only to "lose" the settings "on the fly" while I used the system... so let's see if now for some sort of hit of luck this works in a stable fashion ;)

---

### Post by trikster_x on 2010-10-21
You are absolutely right ephistione, I forgot those packages.  I amended the instructions with a terminal command for a full compiz/emerald install.  Thanks for the correction.

---

### Post by ephestione on 2010-10-22
pretty much the command I pasted in #2 :) anyway so far so good, compiz effects haven't disabled themselves yet, which is strange because this last time I didn't do anything different from the other times, that is uninstalling *compiz* and reinstalling...

---

### Post by mail.prabal on 2010-10-23
i was having the same problem.

opened synaptic,searched 'compiz' and found that it wasn't installed....installed it and everything working fine..effects enabled...settings staying....

hope this reply is relevant to the problem...

---

### Post by ephestione on 2010-10-25
you can as well remove the solved flag... visual effects keep getting disabled under my nose, I need to manually enable the extra effects, then each time manually go into compiz settings manager>effect and enable again advanced animations.... no improvement whatsoever, DAM!!

---

### Post by trikster_x on 2010-10-25
Is it a specific effect that is causing the problem?  Because I know with my comp I can't use the blur windows feature.  If I try to, it disables everything and I have to reenable the visual settings in the appearance tabs and some of my compiz effects.

---

### Post by ephestione on 2010-10-26
nope, nothing like it.
As I said, I basically have wobbly windows, burn up and skewer. They all work fine.
Then compiz/X/the whole ubuntu decide to go mental all of a sudden, and extra visual effects get reverted to none, while "animations add-on" in compiz effects is disabled. This happens during the regular use of the system, not between reboots.
I tried to keep just wobbly windows, with animations add-on disabled, and it's the same.
The latest opengl update to compiz changed nothing.

---

### Post by trikster_x on 2010-10-26
What version number of compiz are you running?

---

### Post by ephestione on 2010-10-28
```
~$ compiz --version
compiz 0.8.6
```BTW it now seems that after a reboot (before rebooting compiz lost the settings and I didn't bother reenabling them) the effects are on once again, including the animations addon :|
Wonder when they will be disabled next.

---

### Post by trikster_x on 2010-10-29
Well, good luck to you on keeping compiz working.  I am out of ideas about what makes it occasionally have fits, and since it is working for now, I am going to set the solved tag for the time being.  I'll stay subbed, so if you have more problems and want to bump this back up, I can remove the solved tag.

---

### Post by ephestione on 2010-10-30
oh well, it's non-solved for me on a regular basis, short after my last post it stopped working once again, and now that I just booted it's okay, for probably 15 minutes of regular use still :p
Nevermind...

---

### Post by trikster_x on 2010-10-30
> **ephestione said:**
> oh well, it's non-solved for me on a regular basis, short after my last post it stopped working once again, and now that I just booted it's okay, for probably 15 minutes of regular use still :p
Nevermind...

I marked as unsolved again, but I think you may have better luck starting a new thread.  I'm kinda at the end of my ability to be of assistance, sorry.

---

### Post by ephestione on 2010-10-31
> **trikster_x said:**
> I marked as unsolved again, but I think you may have better luck starting a new thread.  I'm kinda at the end of my ability to be of assistance, sorry.

ahah, nevermind, don't put the burden on yourself, my problem is still relevant to this thread (I think), so for now I choose not to open a new thread, just don't go overboard in order to solve my issue, maybe someone else will bump in :D

---

### Post by cpmman on 2010-10-31
I had a compiz problem and followed this advice which corrected it:-

[***_http://ubuntuforums.org/showpost.php?p=9964610&postcount=2_***]("http://ubuntuforums.org/showpost.php?p=9964610&postcount=2 _")

---

### Post by ephestione on 2010-11-01
That's one interesting input, because I didn't know about the ppa-purge utility, which can be useful in various situations... alas, removing the compiz ppa is something I already did from withint ubuntu tweak, in fact with the ppa version of compiz I coudn't enable the effects at all, while with the vanilla version I do enable them, they just get disabled at random during the laptop usage; I'm thinking to remove the xorg ppa as well, you never know... even if I used that up until lucid with no problme whatsoever

---

### Post by gunith on 2010-11-13
This is brilliant! Had the same problem and this worked for me! Thanks a lot!

UPDATE: But eventually on restart, the window borders would disappear randomly. Then I found that ubuntu-tweak got a setting to set my window manager as **gnome**. After changing into the default **gnome-wm** it worked for me..

Let me know if it works for yall like that as well and we can mark this fixed :)

---

### Post by wiggy25 on 2010-12-24
This is exactly the same fault I'm now getting.

I have removed all of the extra packages, so it's now like a fresh install.
When I installed Ubuntu on this machine as a dual boot, also loaded it on to a spare as it's own OS.

I have now tried to get this installation back to the same as on my spare .

I still can't select the **EXTRA** setting in the visual effects window, just get the'searching for available drivers' then I accept the settings then close window.
When I go back it has dropped back to** NONE**.

Very odd as it was all working perfectly.

Tried everything above but still doesn't work.
There are no additional drivers loaded for this system, I believe it's an integrated Intel graphics card. 

Anybody come up with another solution?

Cheers

Ian

---

### Post by wiggy25 on 2010-12-24
Having searched some more found something else to try:-

apt-get remove gnome-panel
Deleted the panel directory from .gconf
apt-get --reinstall install ubuntu-desktop

All I did was enter the following:-

```
~$ sudo apt-get remove gnome-panel
```I didn't know how to just delete the panel directory from .gconf although no doubt with more searching I could possibly find it.

Then finished off with:-

```
~$ sudo apt-get --reinstall install unbuntu-desktop
```I can now select all of the settings in the visual effects window and they stay selected.
I could tell it worked because as soon as I selected **extra** the screen went blank just the purple background then all desktop icons came back, there was non of the searching for available drivers pop-up window.

Also as soon as I moved the window, wobbly window was back.

It may work.

Cheers

Ian

---

