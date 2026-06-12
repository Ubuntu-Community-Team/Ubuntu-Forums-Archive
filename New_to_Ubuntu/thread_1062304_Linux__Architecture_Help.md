---
title: "Linux  Architecture Help"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by icyest on 2009-02-06
According to this:
[http://wiki.services.openoffice.org/wiki/Documentation/FAQ/General/How_can_I_add_fonts_to_OpenOffice%3F](http://wiki.services.openoffice.org/wiki/Documentation/FAQ/General/How_can_I_add_fonts_to_OpenOffice%3F)
Where is my open office directory?
I'm trying to install Microsoft fonts so that my Open office is a replica of ms word.

Secondly,
I really liked having "program files" around. That way, you don't have to know anything. Everything is just installed right there. Does Ubuntu replicate this efficiency? or is everything installed all over the place.

---

### Post by ChildOfMana on 2009-02-06
Create a folder in your /home directory called **.fonts**  (note the full stop preceeding the name of the folder - this will make it hidden) and drop the whateverfont.ttf file in there.

Restart OO if you have it open and the font should now be accessible.

If not you may need to drop the font into the **/usr/share/fonts** directory.

_Edit:_ You may need root privileges to do this;

```
sudo cp whateverfont.ttf /usr/share/fonts
```

Note: hit Ctrl+H in Nautilus to see hidden folders.

---

### Post by Claus7 on 2009-02-06
Hello,

sorry about that, yet 100 or so posts and you "seek" to have program files?...

So, answering your second question first, you can have your programs in order from the applications menu. There, you can check the latest installations by category. So, I do not understand exactly the phrase "all over the place".

The link you provide has hellenic letters on one side, so except of hello I salute you with :&#935;&#945;&#943;&#961;&#949;&#964;&#945;&#953;!

Now, as far as the first question is concerned. 
Look at first there:
[http://ubuntuforums.org/showthread.php?t=446809](http://ubuntuforums.org/showthread.php?t=446809)

Then if you are not so happy, do the following:
open synaptic and type openoffice. There you will be able to see where open office is installed and all its components. 

If you do not like synaptic type:
cd /
and then
find -name openoffice

If you want to find where is this spadmin command type:
cd /
find -name spadmin

and it will give you the full path.

If you want to find out where is the fonts folder of open office, go straight ahead to /usr/lib/openoffice/share/fonts , at least there it was mine.

Hope this helped,
Regards!

---

### Post by Temposs on 2009-02-06
Regarding "Program Files", Linux is set up a little differently, yes. Most of the user-oriented files for any program are located in appropriately named hidden folders in your home directory. That's the closest thing to a "Program Files" directory in Linux. That's where you find most things you need. A program's system files are organized in a different way in the system folders.

Here's an explanation of the Linux directory structure: [http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/)

---

### Post by theozzlives on 2009-02-06
Linux is not Windows. Linux organizes files according to their function. With 7.04 I too was lost, but I've learned a great deal since.

---

### Post by ChildOfMana on 2009-02-06
[quote="Claus7"]If you want to find out where is the fonts folder of open office, go straight ahead to /usr/lib/openoffice/share/fonts , at least there it was mine.[/quote]

This is where OO stores its default fonts (the ones it comes with). Placing your whateverfont.ttf file in here will make it accessible to OO but nothing else.

Placing it in **/usr/share/fonts** or in **.fonts** in your /home directory will make the font available to *all* (or at least most) applications.

All valid ways to achieve your goal - whichever works for you. :)

---

### Post by yeats on 2009-02-06
Also, if you're looking to run a program, almost all of them are in /usr/bin, which is one of the locations in which your shell looks for binary files to run - the others are found when you open a terminal and type

```
echo $PATH
```

and you'll see something that looks like this:

```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

If you're looking for program settings, they are mostly found in text files in the /etc directory, or as has been mentioned, in hidden (dot) files in your home directory.

Hope that helps.

---

### Post by donkyhotay on 2009-02-06
> **icyest said:**
> I really liked having "program files" around. That way, you don't have to know anything. Everything is just installed right there. Does Ubuntu replicate this efficiency? or is everything installed all over the place.

Efficiency? Linux doesn't use 'program files' because it's *highly* inefficient. Sure it may be harder for you the user if you aren't familiar with it but on the other hand all the programs you have installed can share the various libraries (essentially .dll's on windows) together instead of each having their own set installed for each program. Think of it this way, is it easier to place something into 
/usr/share/fonts
once or to place something into
c:\program files\program1\fonts
c:\program files\program2\fonts
c:\program files\program3\fonts
c:\program files\program4\fonts
for each program you have installed? Admittedly fonts isn't a good example because most fonts are installed onto the windows fonts folder on windows but you look at all the code stored within program files and figure how much of it is probably the same as all your other programs... well you get the idea.

---

