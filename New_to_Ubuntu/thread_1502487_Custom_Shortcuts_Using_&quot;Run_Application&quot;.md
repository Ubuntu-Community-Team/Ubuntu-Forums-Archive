---
title: "Custom Shortcuts Using &quot;Run Application&quot;"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by Abby.S.Morgan on 2010-06-05
Hey Guys,

I'm in the process of "fully" convterting from XP to Ubuntu and seem to be stuck on one small thing.  I live by the Windows keyboard shortcuts using the Windows Key, mainly Win+R for the "Run" command for quickly opening 'Notepad' and other things.  I've got that same keyboard shortcut setup on my Ubuntu laptop but now I'm trying to figure out how to get gedit to open by typing in "Notepad" instead of "gedit". I know, 'gedit' is shorter than 'notepad' but just go with me here ;)  So, how can I get gedit to launch by typing in 'notepad' at the 'Run Application' prompt?

Thanks all,

Abbs

---

### Post by pizza-is-good on 2010-06-05
I'm not sure if this works, but you might want to try it. (I'm on 7 right now, so I can't.)

Alt+F2, and type 'notepad'. Does that bring up gedit on the liat below?

I guess you could also create a custom command that is called notepad that brings up gedit. I'm not sure how to, but I don't think it's that hard. I'll look into it, but maybe somebody will beat me to it.... (Please feel free to do so)


~pizza

---

### Post by acrazyplayer on 2010-06-05
For shortcuts or quicker anything then try one of these two, 

Gnome-do 

Kupfer

I have used Gnome-do and pushing "super" (the windows button) + "space" then typing what it is you want to start and hitting enter is very fast.

It has a memory as well so if for you it would be "super+space g enter" and up pops gedit

---

### Post by Abby.S.Morgan on 2010-06-05
So, I'm looking to do this:

super+R -> type 'notepad' -> hit 'enter' and gedit opens.

I've already taken care of getting the keyboard shortcut super+R to open up the "Run Application" window.  Now I just need to figure out how to create a shortcut that is named 'notepad' that opens up gedit.  I'm sure it real simple, just having a mental block...

Abbs

---

### Post by SoFl W on 2010-06-05
System ->Preferences -> Keyboard shortcuts -> Add.

---

### Post by SoFl W on 2010-06-05
If you want to drop to terminal set up aliases in your .bashrc script.

---

### Post by Abby.S.Morgan on 2010-06-06
Thanks SoFl W ;)

I've got an alias for 'notepad' that opens up gedit from a term, which is great when I'm in a term.  


But this is really what I'm looking for - super+R -> type 'notepad' -> hit 'enter' and gedit opens.  This give me a nice smooth transition from what I already do in Windows, over to Ubuntu.  I know, may seem silly but it gives me a nice 'comfortable' transition.

---

### Post by kerry_s on 2010-06-06
gksudo gedit /usr/local/bin/notepad

put:
```

#!/bin/bash
gedit "$@" &
exit 0

```

chmod +x /usr/local/bin/notepad

---

### Post by Barrucadu on 2010-06-06
Or even just make a symlink:

```
sudo ln -s `which gedit` /usr/local/bin/notepad
```

---

### Post by Abby.S.Morgan on 2010-06-06
Thank you kerry_s and Barrucadu!  I chose to use Barrucadu's suggestion because it seems to be the simplest and it worked nicely.

Thanks guys, this was a huge help.
Abbs

---

### Post by kerry_s on 2010-06-06
yeah, the link is better for your situation.
i just over thought it cause i use a script for the editor, so it automatically uses a root editor for root owned files.
when i use gedit, it runs this.
```

#!/bin/bash

test=`stat -c %U "$@"`
if [ "$test" == "root" ]; then
	gksudo /usr/bin/gedit "$@" &
else
	/usr/bin/gedit "$@" &
fi
exit 0


```

i also have 1 for leafpad, cause its faster when i don't need gedit features.

---

