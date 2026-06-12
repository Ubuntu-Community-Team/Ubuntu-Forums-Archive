---
title: "help?!"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by cor135 on 2009-05-13
Hello there,

I'm fairly new with Linux so my apologies on vague descriptions.  About a week ago I was just messing around with it to learn it, and came across 'janitor or computer janitor' or something of the sort located in the System/Administrators drop down list.  It gave a few options of things i could delete that possibly were not needed.  I didn't pay attentnion to the warning and went ahead and removed a few of them.  After that i noticed that youtube worked but the music player on myspace didn't.  I went ahead and d/l adobe flash off the web site, and the problem with the music player wasn't fixed, so i decided i would remove what showed up under adobe flash in synaptic (i think thats the name) then only have adobe flash.  Well it deleted that too, and now almost nothing is working.  in the applications/places/system drop down lists at least 1/2 are missing and administration isn't available in system.  I've been in the terminal using help and the manual to try to find a cmd to reverse what i did.  Is there a cmd that can reverse the damage?  Or is there another way to go about it?  

Thank you, and again sorry for not being able to give more details or use correct terms.

---

### Post by skymera on 2009-05-13
Do you remember _any_ of the packages it was going to remove? :)

---

### Post by TheLions on 2009-05-13
Ok you removed flash, so in firefox missing half of the content?

to install flash again type:
```
gksudo apt-get install flashplugin-nonfree
```

to install all restricted plugins and codecs (flash, java, divx, mp3...) type:
```
gksudo apt-get install ubuntu-restricted-extras
```

---

### Post by AgentZ86 on 2009-05-13
> **cor135 said:**
> Hello there,

I'm fairly new with Linux so my apologies on vague descriptions.  About a week ago I was just messing around with it to learn it, and came across 'janitor or computer janitor' or something of the sort located in the System/Administrators drop down list.  It gave a few options of things i could delete that possibly were not needed.  I didn't pay attentnion to the warning and went ahead and removed a few of them.  After that i noticed that youtube worked but the music player on myspace didn't.  I went ahead and d/l adobe flash off the web site, and the problem with the music player wasn't fixed, so i decided i would remove what showed up under adobe flash in synaptic (i think thats the name) then only have adobe flash.  Well it deleted that too, and now almost nothing is working.  in the applications/places/system drop down lists at least 1/2 are missing and administration isn't available in system.  I've been in the terminal using help and the manual to try to find a cmd to reverse what i did.  Is there a cmd that can reverse the damage?  Or is there another way to go about it?  

Thank you, and again sorry for not being able to give more details or use correct terms.

The adobe flash player can be installed via Applications/Add/Remove and select (Macromedia Flash Plugin)-installer for the macro media flash plugin for Mozilla

That should fixup the myspace stuff
And you could install (Mplayer plugin for Mozilla)

That should help your playback trouble

The installer may ask you to un-install some flash stuff in order to re-install, so you may have to open Synaptic Package Manager to uninstall the reminents of flash in order to use the regular Applications/Add/Remove type installed just FYI on that

You can also see your package history in synaptic

System/Administration/Synaptic Package Manager
Then once the Synaptic is opened select File/History
Then select the date so you can see what was removed on that date

I hope this helps.

I'm using 8.10, however this should help you fix up your 9.04 as well, however the location of these menus may have changed, but thats the general idea.

Happy Hacking

---

### Post by billgoldberg on 2009-05-13
> **cor135 said:**
> Hello there,

I'm fairly new with Linux so my apologies on vague descriptions.  About a week ago I was just messing around with it to learn it, and came across 'janitor or computer janitor' or something of the sort located in the System/Administrators drop down list.  It gave a few options of things i could delete that possibly were not needed.  I didn't pay attentnion to the warning and went ahead and removed a few of them.  After that i noticed that youtube worked but the music player on myspace didn't.  I went ahead and d/l adobe flash off the web site, and the problem with the music player wasn't fixed, so i decided i would remove what showed up under adobe flash in synaptic (i think thats the name) then only have adobe flash.  Well it deleted that too, and now almost nothing is working.  in the applications/places/system drop down lists at least 1/2 are missing and administration isn't available in system.  I've been in the terminal using help and the manual to try to find a cmd to reverse what i did.  Is there a cmd that can reverse the damage?  Or is there another way to go about it?  

Thank you, and again sorry for not being able to give more details or use correct terms.

Many people have raised awareness about the Janitor program. It isn't safe to use if you don't know what you are doing.

Sadly you found this out the hard way.

But Ubuntu is to blame here, you couldn't know it wasn't safe.

The best thing to do in your case is a reinstall of Ubuntu.

It could have delete a whole range of apps, dependencies, ...

edit: the file->history option in synaptic (of which I was unaware) is most likely a better option than a reinstall.

---

### Post by cor135 on 2009-05-13
> **skymera said:**
> Do you remember _any_ of the packages it was going to remove? :)
everything in synaptic that was already installed when i typed in 'adobe flash' 

as for the janitor - no. =[

---

### Post by cor135 on 2009-05-13
> **TheLions said:**
> Ok you removed flash, so in firefox missing half of the content?

to install flash again type:
```
gksudo apt-get install flashplugin-nonfree
```

to install all restricted plugins and codecs (flash, java, divx, mp3...) type:
```
gksudo apt-get install ubuntu-restricted-extras
```
1/2 of what was in the drop down lists in Ubunut itself are not there, and administration doesn't show up at all. i can't access the interent (using diff pc at the moment)  i just restarted my laptop and it didn't even go to the GUI.  i typed in sudo get-app flashplayer-nonfree and its the same error message i have been getting

 failed http:us.archive.ubuntu.com jaunty/main libcario2 1.8l6-1ubuntu2
   could not reslove 'us.archive.ubuntu.com'

a bunch of those pop up with different addresses every time i try to sudo get-app anything

---

### Post by cor135 on 2009-05-13
> **AgentZ86 said:**
> The adobe flash player can be installed via Applications/Add/Remove and select (Macromedia Flash Plugin)-installer for the macro media flash plugin for Mozilla

That should fixup the myspace stuff
And you could install (Mplayer plugin for Mozilla)

That should help your playback trouble

The installer may ask you to un-install some flash stuff in order to re-install, so you may have to open Synaptic Package Manager to uninstall the reminents of flash in order to use the regular Applications/Add/Remove type installed just FYI on that

You can also see your package history in synaptic

System/Administration/Synaptic Package Manager
Then once the Synaptic is opened select File/History
Then select the date so you can see what was removed on that date

I hope this helps.

I'm using 8.10, however this should help you fix up your 9.04 as well, however the location of these menus may have changed, but thats the general idea.

Happy Hacking
well i guess messing around with ubuntu and making mistakes is the best way to learn.

im hoping there is some other way cuz i had virtual box running xp that had network simulator software for one of my classes ... BUT if not then thats just life.

do you mean format it?
i don't have the os on disk, i borrowed it from a classmate, but i guess i can d/l it.

---

### Post by AgentZ86 on 2009-05-14
> well i guess messing around with ubuntu and making mistakes is the best way to learn.

im hoping there is some other way cuz i had virtual box running xp that had network simulator software for one of my classes ... BUT if not then thats just life.

do you mean format it?
i don't have the os on disk, i borrowed it from a classmate, but i guess i can d/l it.

No don't format, but you can see the history in synaptic which will tell you which packages you un-installed on that date with janitor.

Then you can manually install those packages that were un-installed on that date that that were un-installed with janitor etc.

Doesn't 9.04 have synaptic installed ? Anymore.

I hope this helps it should re-install all your packages that you uninstalled or at least you can find them with the history menu and then make note of those packages and re-install them.

---

### Post by skymera on 2009-05-14
I agree with the fact that the "Janitor" is a total waste of time.

Last time it was going to remove all my FGLRX packages. Which i sort of need for my ATi to function.

@ Try the solution above.
If it doesn't work, perhaps reinstall. I always do if things go really bad.

Thankfully 9.04 has been relatively stable for me.

---

### Post by NHArticleTen on 2009-05-14
reinstall

also, check out my other posts and have some fun with DSL and Puppy.

---

### Post by Bölvaður on 2009-05-14
if you reinstall you can take backup of the virtual harddisk you got xp installed on. It is a file somewhere.. you can see the name and just look about for it. 


if you have virtualbox then backup this directory

~/.VirtualBox

---

