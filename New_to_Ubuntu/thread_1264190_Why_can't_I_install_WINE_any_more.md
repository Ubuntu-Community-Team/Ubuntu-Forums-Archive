---
title: "Why can't I install WINE any more?"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-09-11
I was able to install and use WINE on 7.04 on a different hard drive ............ it worked beautifully but that's history.

Ever since I upgraded from 7.04 to 8.04 (and now 8.10) I have never been able to reinstall WINE.

I have cleared everything connected to it out of my present hard drive and still when I try to install ........... nothing works, no menu in the "Applications" menu, no nothing.

I have just recently converted my daughters old Fujitsu laptop over to Ubuntu and have recently bought a terrible piece of equipment called an Everex Gbook .......... WINE works beautifully on them both :confused: (except for a dissappearing mouse pointer that I can live with).

This is what I get when I try to launch the program in a terminal ;

```
dad@dad-desktop:~$ wine program
wine: could not load L"C:\\windows\\system32\\program.exe": Module not found
dad@dad-desktop:~$
``` 

Can someone please help me to figure out what's going on? and how to get things running like they should?

Is something in my home folder corrupted? It seems like WINE is there but just doesn't want to play with me. It's weird.

Thanks a million in advance.


Fresh from the terminal after purge and install of WINE ;

```
dad@dad-desktop:~$ wine program
wine: created the configuration directory '/home/dad/.wine'
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Logitech USB Headset, disabling mixer
Could not load wine-gecko. HTML rendering will be disabled.
wine: configuration in '/home/dad/.wine' has been updated.
wine: could not load L"C:\\windows\\system32\\program.exe": Module not found
dad@dad-desktop:~$ 
```

I just spent a while trying to find this file .......... and it's really not there!! Should it be? Is this a Windows thing? or is it some configuration file lost in the depths of my remote /home folder that is hanging on through the updates that I do to the system?

---

### Post by CatKiller on 2009-09-12
> **tahitiwibble said:**
> 
This is what I get when I try to launch the program in a terminal ;

```
dad@dad-desktop:~$ wine program
```

Why are you trying to run that? You're attempting to run a program called "program." Since that doesn't exist, Wine can't find it, which is exactly what it told you.

Run a program that actually exists and you'll have more luck.

---

### Post by swoody on 2009-09-12
Did you install Wine from the repos, or from WineHQ.com? Do you get any success/output from running:
```
winecfg
```

Also, I haven't used Wine in quite some time, but are you sure 'wine program' is a command? Typically from what I remember, you would run something like:
```
wine ~/Desktop/program.exe
```
Whereas 'program.exe' would be the name of an .exe file on your Desktop. Am I mistaken in this? Is 'wine program' an actual command?

---

### Post by swoody on 2009-09-12
Double-post :(

---

### Post by swoody on 2009-09-12
Triple-post

---

### Post by tahitiwibble on 2009-09-12
> **CatKiller said:**
> Why are you trying to run that? You're attempting to run a program called "program." Since that doesn't exist, Wine can't find it, which is exactly what it told you.

Run a program that actually exists and you'll have more luck.

How do I run WINE from the terminal? 

```
dad@dad-desktop:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
dad@dad-desktop:~$ 

```

In any case, WINE just doesn't work any more. It used to!

---

### Post by swoody on 2009-09-12
Quadruple-post :(

---

### Post by swoody on 2009-09-12
Wow, I think I must be going for a new multi-post world record! :D

Sorry about all of that ^^

---

### Post by tahitiwibble on 2009-09-12
> **CatKiller said:**
> Why are you trying to run that? You're attempting to run a program called "program." Since that doesn't exist, Wine can't find it, which is exactly what it told you.

Run a program that actually exists and you'll have more luck.

How do I run WINE from the terminal? 

```
dad@dad-desktop:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
dad@dad-desktop:~$ 

```

In any case, WINE just doesn't work any more. It used to! When I try to install the same reference library CD that always worked before I get the same answer.

I've never had to get into the workings of WINE or do anything to it before. I installed WINE, stuck my Windows CD in the reader and bingo!! it all worked perfectly just as if it was a Windows machine without any intervention from me.

---

### Post by tahitiwibble on 2009-09-12
> **swoody said:**
> Did you install Wine from the repos, or from WineHQ.com? Do you get any success/output from running:
```
winecfg
```

Also, I haven't used Wine in quite some time, but are you sure 'wine program' is a command? Typically from what I remember, you would run something like:
```
wine ~/Desktop/program.exe
```
Whereas 'program.exe' would be the name of an .exe file on your Desktop. Am I mistaken in this? Is 'wine program' an actual command?

Hi, yes I did winecfg and everything is in place but still no menu entries like on my daughters computer or on my Everex marvel.

Regarding the "wine program" ........... duhhhhhh, how silly of me!

---

### Post by swoody on 2009-09-12
> **tahitiwibble said:**
> still no menu entries like on my daughters computer or on my Everex marvel.

Do you happen to remember if you ever had to edit your menus manually, and remove the Wine menu entries in the past? I have noticed that sometimes when I remove a menu item in this way, it won't auto-create that same item in the future.

---

### Post by mc4man on 2009-09-12
Two things you can ck. with simple solutions.

First just run this in a terminal and see if wine is listed but not enabled in the right side box. If so just click the box to enable

```
alacarte
``` 

If no sign of wine then ck. this file for a deleted entry for wine. Might as well use  cat to ck. While you can't edit if need be, you also can't cause an inadvertent new issue.

```
cat ~/.config/menus/applications.menu
```

If you see this somewhere 
```
	<Menu>
		<Name>wine-wine</Name>
		[COLOR="Red"]<Deleted/>[/COLOR]
	</Menu>
</Menu>

```

Then run this command and in the newly opened file **remove only what's in red** and save
```
gedit ~/.config/menus/applications.menu
```

If there is no such entry in applications.menu, then post back and there are a couple of other things to try
One is to go back to edit menus (alacarte) and click the revert button, though I wouldn't try that till you've checked the above 2 things

---

### Post by swoody on 2009-09-12
> **mc4man said:**
> If no sign of wine then ck. this file for a deleted entry for wine. Might as well use  cat to ck. While you can't edit if need be, you also can't cause an inadvertent new issue.

```
cat ~/.config/menus/applications.menu
```

If you see this somewhere 
```
	<Menu>
		<Name>wine-wine</Name>
		[COLOR="Red"]<Deleted/>[/COLOR]
	</Menu>
</Menu>

```

Then run this command and in the newly opened file **remove only what's in red** and save
```
gedit ~/.config/menus/applications.menu
```

If there is no such entry in applications.menu, then post back and there are a couple of other things to try
One is to go back to edit menus (alacarte) and click the revert button, though I wouldn't try that till you've checked the above 2 things

Ah, thanks for this post mc4man! That's what I was referring to :)

---

### Post by tahitiwibble on 2009-09-13
Oh wow! It's such a pleasure to see guys that know what they're talking about!

Thanks very very much to both of you .......... it worked like a charm. Fantastic!

---

