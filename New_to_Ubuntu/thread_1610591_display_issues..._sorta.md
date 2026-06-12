---
title: "display issues... sorta?"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by taith on 2010-10-31
running ubunto 10.04, i get the following errors constantly when running many programs that require graphics of many sorts, but not all :) some programs are run through wine, some ran naitively... programs like desmume and dozens of others...

```
Xlib:  extension "RANDR" missing on display ":0.0".
Error trying to initialize SDL: No available video device
```

im running a nvidia gForce 9800, with dual monitors(xserver)...

any ideas on how i can fix this?




i have no idea if its related, but when i try to turn preformances on in the appearance preferences box(even to normal) it says "The composite extension is not available" and freezes :S

---

### Post by Crusty Old Fart on 2010-11-06
Are you extending your desktop across both monitors from within xorg.conf using the Xinerama option?

---

### Post by taith on 2010-11-09
yes, and i have tried reinstalling the SDL libs and its still having the same issue :(

---

### Post by Crusty Old Fart on 2010-11-09
Howdy taith:

**Here's what's happening:**[INDENT]When Xinerama is invoked, it disables both RandR and compositiing. Everybody who uses Xinerama with the newer versions of Ubuntu gets the same error:
```

Xlib:  extension "RANDR" missing on display ":0.0".

```[/INDENT][B]Can the error be suppressed?
[/B][INDENT]There may be a way to suppress this error, but if there is, I haven't found it, and I've spent all the time I've been willing to waste looking for it, which was way too much.
[/INDENT][B]Does it indicate that harm is being done to the system?
[/B][INDENT]Not from what I've experienced, or read from other geeks. Those of us who have made the decision to keep running Xinerama, do so with the willingness to tolerate this annoyance.
[/INDENT][B]What can be done about it?
[/B][INDENT]The choices are pretty limited:

[LIST]
[*]The Xinerama option could be disabled in /etc/X11/xorg.conf. Doing so will allow RandR to recognize your displays without complaining, and it will allow compositing. But, unless you can use something other than Xinerama to extend your desktop across both of your monitors, you'll lose the ability to drag windows from one screen to another as well as other features that are unique to extended desktops. _For some systems running Nvidia graphics adapters, the TwinView extension(?) has worked as a replacement for Xinerama. In some cases, TwinView will extend the desktop without disabling RandR or compositing._
[/LIST]

[LIST]
[*]For the folks who cannot use anything other than Xinerama to extend their desktop (me, for one): they can just tolerate the error that results from RandR being missing and live without the eye candy that compositing serves up.
[/LIST]
[/INDENT][B]Does having RandR disabled cause any anomalies in addition to the error message?
[/B][INDENT]Yes, one that I know of. Often, when I run a shell script in a terminal window, the script will hang when it finishes without exiting. In order to get a command prompt after a hang, I have to press the key combination [COLOR=Red]**Ctrl+c**[/COLOR]. In the past, I used to end almost all of my scripts with the last line being:
```

exit 0

```However, this does nothing to prevent a disabled RandR extension from leaving some scripts hanging when they finish. Forcing these scripts to commit suicide by killing their own process allows them to close without hanging. In these cases, instead of using "exit 0" as the last line, I use the following command on the last line:
```

kill $$

```[/INDENT]**With regard to:**
> 
```

Error trying to initialize SDL: No available video device

```

[INDENT]I'm clueless. I never see that on my system, but my suspicion is that it's just another symptom of RandR being disabled by Xinerama, and can be ignored without any serious consequence...but that's just a guess based on a suspicion.
[/INDENT]Hope this helps.

Good luck,

Crusty

---

