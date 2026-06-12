---
title: "nautilus Question(s)"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by green0eggs on 2009-03-15
Hello.

I am using nautilus to do some serious ultra mega tidy housekeeping and have found it brilliant to use.

I do have a couple of questions:

1)[INDENT]Is there any way to have a folder (in list view) always expand out certain sub-folders whenever I re-enter the folder?

That may not have been all to clear, to clarify:
I have a folder called '\University Work' and inside, it has folders 'Year 1' 'Year 2' etc then inside those there is a subsubfolder for each module taken i.e. 'PH1002 Classical Mechanics' which lives in Year 1 and so on. 

Is it possible to set up '\University Work' so that the default view is List View ***and*** that the subfolders are open so I can effectively have a list of all the modules appear whenever I open it?
[/INDENT]
2)[INDENT][nautilus thinks some of my mounted volumes are Picture CDs]("http://ubuntuforums.org/showthread.php?t=1003547") and asks if I want to open them in F-Spot in a chunky toolbar whotsit underneath the location bar. Unfortunately, they're not and it takes up my valuable screen space (I live in small monitor land). 

I've tried obvious places both in nautilus>Edit>Preferences *and* F-Spot>Edit>Preferences neither of seem to have a satisfying 'Turn off annoying chunky toolbar whotsit' button.[/INDENT]


Any help would be greatly appreciated.

---

### Post by gandaran on 2009-03-15
for the second question, try nautilus » edit » preferences » media tab, in the  photos option set it to do nothing.
sorry don't know about the first question.

---

### Post by green0eggs on 2009-03-15
> **gandaran said:**
> for the second question, try nautilus » edit » preferences » media tab, in the  photos option set it to do nothing.
sorry don't know about the first question.
Just found it: below the common media types is a drop down menu entitled 'Other Media' choose PhotoCD and set to 'Do Nothing' 50% solved.

Thanks

---

### Post by green0eggs on 2009-03-15
Ok. On closer inspection that only works for my External HD. One of my internal partitions is still given the PhotoCD head band. Despite the option being turned off.

---

### Post by roycrom on 2009-03-23
Hi,
Did you manage to get rid of the bar?  Takes up way too much room on a netbook 1024x600!

I'm getting this issue when I mount remote fs using sshfs.

---

### Post by green0eggs on 2009-03-30
Nope still havn't found a way to get rid.

---

### Post by jo4hnc on 2009-03-30
Hi,

I had the same problem when I upgraded to Intrepid in one partition of my second internal drive. A kind soul advised me that it was because I had a file on the drive named "Pictures". I changed the name of the file, rebooted and the bar went away. Don't know if this will solve the problem for you but it's something to try.

John

---

### Post by green0eggs on 2009-03-31
It worked!

Renamed "Pictures" to "Pictures " and got rid of the big ol' bar at the top. My humble 1024x768 resolution thanks you. As do I.

---

### Post by jo4hnc on 2009-03-31
> **green0eggs said:**
> It worked!

Renamed "Pictures" to "Pictures " and got rid of the big ol' bar at the top. My humble 1024x768 resolution thanks you. As do I.

Cool! Glad it worked.

---

### Post by mikechant on 2009-03-31
> Is there any way to have a folder (in list view) always expand out certain sub-folders whenever I re-enter the folder?

That may not have been all to clear, to clarify:
I have a folder called '\University Work' and inside, it has folders 'Year 1' 'Year 2' etc then inside those there is a subsubfolder for each module taken i.e. 'PH1002 Classical Mechanics' which lives in Year 1 and so on. 

Is it possible to set up '\University Work' so that the default view is List View and that the subfolders are open so I can effectively have a list of all the modules appear whenever I open it?

That's an interesting requirement. I don't think that Nautilus can do this (but happy to be proved wrong!). The only things I can think of are:
a) Try an alternative file manager to Nautilus. Eg. Konqueror (even though it's for KDE - it's probably got more config settings than Nautilus, and there is a package called 'konq-plugins' for Ubuntu which provides a 'directory filter' facility which sounds worth investigating)

or the following workarounds:

b) In the example above, move all the modules up into the 'University work' folder after attaching a prefix of 'y1.', 'y2.' etc. to their names. This is a bit crude but might achieve what you want!  (or would you even need the prefixes - in your example, does 'PH1...' mean it's a year 1 course?)

c) Create links to each file and place them in the higher level folder.

---

