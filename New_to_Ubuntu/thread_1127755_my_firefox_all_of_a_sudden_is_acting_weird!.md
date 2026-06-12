---
title: "my firefox all of a sudden is acting weird!"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by anico on 2009-04-16
For some reason my ubuntu froze and i had to manually take the battery out to turn it off.. everything seems ok except now when i use firefox... all my bookmarks are gone.. i can't press backwards nor forwards nor refresh.. i can't ADD a bookmark.. it's like everything has been completely removed and i'm stuck with a malfunctioning firefox.. i would appreciate any help!!
Thanks!

---

### Post by lovinglinux on 2009-04-16
It's a corrupted profile. Create a new profile and it should work, then you can restore old bookmark backups from the old profile to the new one.

Check this [http://ubuntuforums.org/showthread.php?t=1124708](http://ubuntuforums.org/showthread.php?t=1124708)

---

### Post by anico on 2009-04-16
thanks alot for replying so soon!
I'm pretty new to all this..how exactly do i create a new profile?

---

### Post by ddrichardson on 2009-04-16
> **anico said:**
> i had to manually take the battery out to turn it off
Most notebooks (in fact I've never seen one that doesn't) can be forced off by holding down the power button until it shuts off.

---

### Post by lovinglinux on 2009-04-16
> **anico said:**
> thanks alot for replying so soon!
I'm pretty new to all this..how exactly do i create a new profile?

If you are familiar with using the terminal, close Firefox then open the console and run the following command:
```

firefox -P
```

The profile manager will show up, so you can create and delete profiles. 

Another option would be deleting your profile folder, so Firefox will ask for a profile next time you open it. Profiles are stored in your home directory under the .mozilla/firefox/ folder. The dot before mozilla means it is hidden, so you have to hit CRTL+H when browsing your home directory with the file browser too see it. Please be aware that if you delete your profile you will loose all bookmarks and Firefox settings.

---

### Post by heatpumpcontrol on 2009-04-16
I suggest 'xmarks' add-on and backing up your bookmarks on their servers so when you recreate a new Firefox profile, all you have to do is install the 'xmarks' add-on again and bingo, done.... all bookmarks are back. 

Now of course, you'll have to personalize your preferred settings as far as the rest of Firefox settings are concerned. Unless, you install 'Tab Mix Plus' add-on and back up your preferences. Then you just restore them again after installing the add-on onto your newly recreated Firefox profile.


Good luck

---

### Post by lovinglinux on 2009-04-16
> **heatpumpcontrol said:**
> I suggest 'xmarks' add-on and backing up your bookmarks on their servers so when you recreate a new Firefox profile, all you have to do is install the 'xmarks' add-on again and bingo, done.... all bookmarks are back. 

Now of course, you'll have to personalize your preferred settings as far as the rest of Firefox settings are concerned. Unless, you install 'Tab Mix Plus' add-on and back up your preferences. Then you just restore them again after installing the add-on onto your newly recreated Firefox profile.


Good luck

You can also use [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) to backup all important stuff from your profile or the entire profile.

---

### Post by anico on 2009-04-16
Thanks guys this really helped!
I would post this as [SOLVED] if it wasn't disabled!

---

