---
title: "terminal lettering"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by dzon65 on 2009-12-06
Posted this before but since tried to avoid terminal commands.The letters are soo bad,from time to time it's impossible to read.Things are overlapping or being split.I'm beginning to think even the terminal can't read it since some simple commands are prompted invalid.Is this possible?Added a screenshot which is pretty ok but most of the times it's far worse.(check the r-- at the end)

---

### Post by The Cog on 2009-12-06
Green on semi-transparent brown isn't really a good colour choice, IMHO. I prefer black-on-light-yellow, and not at all transparent.

---

### Post by asmeetkumar on 2009-12-06
hi

from what i saw in the image you need to change the font of the terminal.
for that open a terminal. go to Edit > Profile Preferences 
In the new window you'll see a check box stating : Use the system fixed width font.

Uncheck it if its checked and then experiment with the various fonts & sizes and choose whichever suits you.

just to add the system default font is monospace 12.

---

### Post by Joeb454 on 2009-12-06
I generally change mine to semi transparent black background, and very light grey (or gray, if you prefer) text

---

### Post by dzon65 on 2009-12-06
[asmeetkumar]("http://ubuntuforums.org/member.php?u=376185"),did that already.Doesn't change a bit.It's weird,un-and reinstalled ubuntu quite a few times now.(I'm still on wubi,planning to go for a total though,but now it's more forgiving to make mistakes).Anyway,whatever font I'm using>>>same thing.I'm telling you,that screenshot is one of the best,usually letters are either on top of eachother,either miles apart.

---

### Post by asmeetkumar on 2009-12-06
> **dzon65 said:**
> [asmeetkumar]("http://ubuntuforums.org/member.php?u=376185"),did that already.Doesn't change a bit.It's weird,un-and reinstalled ubuntu quite a few times now.(I'm still on wubi,planning to go for a total though,but now it's more forgiving to make mistakes).Anyway,whatever font I'm using>>>same thing.I'm telling you,that screenshot is one of the best,usually letters are either on top of eachother,either miles apart.

ok lets give it one more try...
you seem to have installed a custom visual theme... i reckon changing its default font might change the settings. Its in 
System > Preferences > Appearence 
i think....

this seems to becoming a habit of mine ...

i am editing this to add that you can also edit the font settings in that window to best suit your screen

---

### Post by dzon65 on 2009-12-06
Nope.This happens even on the "naked" fresh startup.Doesn't change whether with clearlooks,human,custom,using emerald or not....

---

### Post by asmeetkumar on 2009-12-06
> **dzon65 said:**
> Nope.This happens even on the "naked" fresh startup.Doesn't change whether with clearlooks,human,custom,using emerald or not....

well just to add could you try another terminal thats present on your system and check the fonts in it...

Press Alt + F2 and type : xterm 
hit enter and look at the terminal whether the fonts are garbled or not?

---

### Post by dzon65 on 2009-12-06
Yep,just the same.Annoying thing,ànd persistent.It's not that I can't sleep,it's just that I'm really starting to wonder if the terminal can read it.Some simple commands weren't recognized.Actually,when I typed them,couldn't read them myself.Strange thing,sometimes it's pretty much readable(pretty) and other times it's plain Dali.

---

### Post by asmeetkumar on 2009-12-06
well only thing i can come up with is : use the the virtual consoles

press CTRL + ALT + F1 (or F2 - F6)
and this will give u a tty terminal

it is readable on almost every system, and is as effective for running some quick commands...

---

### Post by dzon65 on 2009-12-06
> **asmeetkumar said:**
> well only thing i can come up with is : use the the virtual consoles

press CTRL + ALT + F1 (or F2 - F6)
and this will give u a tty terminal

it is readable on almost every system, and is as effective for running some quick commands...

That's a bit drastic and long,don't you agree?The only time I visited the tty terminal was to change my GDM and xsplash.Besides,like I said,doesn't keep me from sleeping.I'll be having ubuntu as my only OS and perhaps it'll be allright then.
Mr A.Thanks a lot for the time you spent into this thread.Wish you a nice day and lots of ubuntu-pleasures.
Kind regards,John.

---

### Post by itcotbtoemik on 2009-12-06
The screenshots weren't xterm (offhand, that looks like gnome-terminal).
So it's hard to tell what result you were seeing in the case where you
switched to xterm.

---

