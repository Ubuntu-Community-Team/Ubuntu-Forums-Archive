---
title: "Lock Keyboard for Baby"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by Brendantb on 2009-12-05
I have downloaded lk4b, (lock-keyboard-for-baby,) from: 

[http://sourceforge.net/projects/lk4b/files/](http://sourceforge.net/projects/lk4b/files/)

It is a .pl file: how to I go about installing it when it's downloaded? 

Thanks,

---

### Post by LuisGMarine on 2009-12-05
Hello,

Well from some googling I found out that the .pl extentsion belongs to the perl language.  So what we are going to do is try two different methods on how to go about executing and installing this lock baby keyboard thing. :popcorn:  these methods are outline here [http://http://ubuntuforums.org/showthread.php?t=473820]("http://http://ubuntuforums.org/showthread.php?t=473820")

This was posted by the user mannheim, so give this a shot:

> 
If you are in gnome, and don't want to use the command-line, do this. (I assume the script is saved in a file, and that the text in the file begins with something like "#!/bin/perl" or similar:

   1. Right-click on the file, and select "Properties"
   2. Select the "Permissions" tab.
   3. Check the box that says "Allow executing file as a program"
   4. Close the Properties dialog box
   5. To run the perl script, double-click on the file
   6. If a dialog asks for confirmation, click the button that says "Run"


Alternatively, open gnome-terminal, go to the directory in which the file is located, and then enter "perl myfile", replacing "myfile" with the name of the file.

hope this helps! :p

---

### Post by Brendantb on 2009-12-05
Thanks for that, 

I will try it out and let you know how I fare...

---

### Post by LuisGMarine on 2009-12-05
sounds good, let me know if it works and if it does just make sure you tag this as [SOLVED]

---

### Post by dasunst3r on 2009-12-05
You can also lock your screen when you step away.

---

### Post by LuisGMarine on 2009-12-06
That too, but locking your screen might cause your screen to go black.  This is good for when you want to watch a movie on the screen and you have to watch you baby at the same time.  Just put the baby on your lap turn on this program and he wont be a problem for the duration of the movie :D

Still waiting on to see if it works!!! :KS

---

### Post by Brendantb on 2009-12-10
Sorry to taking so long to get back to you, I couldn't log in to the site for some reason... 

I wasn't able to run the program using the first method, but using the terminal did work. The file is currently in the download folder, but I can't seem to make it work using a custom launcher, even browsing to the file. Hopefully I will work it out soon.

---

### Post by Brendantb on 2009-12-10
I can only launch the program by navigating to the program in the terminal and using the perl command. How do I construct a shortcut for this that will work from a panel?

---

### Post by LuisGMarine on 2009-12-10
> **Brendantb said:**
> I can only launch the program by navigating to the program in the terminal and using the perl command. How do I construct a shortcut for this that will work from a panel?

You can edit your menu by right clicking on the Menu Bar, and selecting Edit Menus.

[IMG]http://i244.photobucket.com/albums/gg6/luisgmarine/menu.png[/IMG]

Then from there on the left side you will click where you want this to show up, so I would probably keep this under "other" or "Accessories".  After that just click on "New Item"

---

