---
title: "Odd Characters in Documents"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by TunaCanTommy on 2009-06-03
I occasionally get the following "odd" characters in text documents . . .

   

Do I need to load, or enable, a font set to get rid of them ? ?

---

### Post by VCoolio on 2009-06-03
Probably, yes. Drop your fonts in ~/.fonts (or in /usr/share/fonts to make them system-wide available). Sometimes it happens with script-generated text or with text from e.g. html-files (usually at the end of a line); don't know what that is.

---

### Post by The Cog on 2009-06-03
Those you pasted in the post are backspace characters, hex value 0008. These are by their nature not printable. And a little box with 0008 init is a reasonable way for an editor to show them. Geany shows a box with BS in it instead. Your problem here is having a rogue document, not that you are missing a font.

---

### Post by TunaCanTommy on 2009-06-03
Thanks to both of you, I appreciate you response.
I don't think a rouge document is at fault; in that I saw them while watching the "output" when GnomeBacker was running . . . burning an ISO.
Odd to me indeed . . . I'll put my fonts in ~./fonts and see if that fixes it.
Will post back to let you know what happens . . .


Edit:  Just checked . . I already have a /usr/share/fonts directory. It contains folders: "truetype" "type1" and "X11"

---

### Post by hovzio on 2009-06-04
> **TunaCanTommy said:**
> Thanks to both of you, I appreciate you response.
I don't think a rouge document is at fault; in that I saw them while watching the "output" when GnomeBacker was running . . . burning an ISO.
Odd to me indeed . . . I'll put my fonts in ~./fonts and see if that fixes it.
Will post back to let you know what happens . . .


Edit:  Just checked . . I already have a /usr/share/fonts directory. It contains folders: "truetype" "type1" and "X11"


I've been using gnomebaker for some time and its always (for me that is) given this output. Like mentioned above, they are a hex representation of a backspace.  What are you doing when you see these characters, just writing a text file, or is it the output of a program? What editor are you using?

---

### Post by TunaCanTommy on 2009-06-04
Thanks for the reply hovzio . . .

Where I'm seeing it is when I go to a gaming web-site and open a "walk-through" of a particular game, which is usually a text file. I copy and paste the text-file of the walk-through into an OpenOffice document to save it. 

What I've seen is that they represent a "single-quuote" character as in  . . isnt,
or cant.

I then just use "find and replace" to get rid of them.

---

### Post by kaibob on 2009-06-04
> **TunaCanTommy said:**
> Thanks for the reply hovzio . . .

Where I'm seeing it is when I go to a gaming web-site and open a "walk-through" of a particular game, which is usually a text file. I copy and paste the text-file of the walk-through into an OpenOffice document to save it. 

What I've seen is that they represent a "single-quuote" character as in  . . isnt,
or cant.

I then just use "find and replace" to get rid of them.
I frequently see those characters in text files and have never found a way to avoid them. Instead, I use the tr utility to get rid of them. For example, to strip out the backspace character:

```
cat file.txt | tr -d '\010' > newfile.txt
```

To strip out most unprintable characters:

```
cat file.txt | tr -d '\001-\010\013-\037\177-\377' > newfile.txt
```

If this is an ongoing issue, I would place the above command line in a nautilus script.

---

### Post by SunnyRabbiera on 2009-06-04
I see this a lot, especially when translating from a older version of microsoft text editor to one of linux's text editors.
Its probably encoding, but this is more fault of Microsofts text editor then anything else.

---

### Post by TunaCanTommy on 2009-06-04
Thank you gentlemen . . . good information.

This isn't a "huge" issue with me, just a minor annoyance.  My main concern was that I didn't have fonts correctly installed or implemented.  From your responses I get the impression this is just a "quirk" in the system and relatively easy to deal with.

I personally haven't come across it very often, and when I do I've found the "find-and-replace" method suitable for my needs.

As an aside; I, like most of you, started my computer experience with DOS. Building batch files, editing config.sys and autoexec.bat files. Never had much UNIX exposure.  Eventually I grew tired of the "spoon-fed" M$ stuff as it evolved, and the extreme cost of their software.  I found LINUX about three years ago.  I have really enjoyed building my expertise and learning, but there is so much to learn.  UBUNTU has been lots of fun and very rewarding.  I'm in this forum quite often, looking for answers and picking up tips.  Guys like you helping guys like me has made it a real pleasure - I appreciate all the help you guys provide.  Thanks ! !:D

---

