---
title: "[SOLVED] simple scripting"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by jonaskn on 2009-01-02
I'm quite new to Linux, and have absolutely no experience in programming, but in windows I was able to make simple .bat files. Now I would like to do something similar in linux, the command I want run is:
 ```
vlc rtsp://streamer-01.dr.nordija.dk/dr2high
```

I can make a text file containing the command, and in terminal type: 
```
bash *mytextfile*
```
and vlc opens the link just fine.

My problem is that I would like, not to do any typing, so how do I make a file on which I can just double click

---

### Post by OutOfReach on 2009-01-02
You can save this script:
```

#!/bin/bash
vlc rtsp://streamer-01.dr.nordija.dk/dr2high

```

On, say, your desktop. Then right click on the file, Select properties then goto the Permissions tab. Select 'Execute as program' (or something along the lines of that). And that should do it.

---

### Post by bump_ on 2009-01-02
First thing is put

```
#!/bin/bash
```

as the first line of your script. This tells the shell to use the bash shell to run your script.

Second, after you are done typing the script, run

```
chmod +x scriptname
```

while you are in the same directory as the script and that will make it executable. Double clicking should work now.

---

### Post by Barriehie on 2009-01-02
I have some scripts that I run and I have them in **/home/barrie/myscripts/bash/** folder.  On the desktop you can right click and select create launcher.  You can give the item a name and then the file to run when the item is selected.  You'll have to add the path to your scripts to your environment.   You can do this by opening ***~/.bashrc*** and find where it says **PATH=** and at the end of that line add **the path to your scripts**, preceeded by a colon.   Save the file and in the terminal type ***source ~/.bashrc*** Now the OS should be able to find your scripts when you double click the launcher.

Can also use a custom icon if you like after you get the icon on the desktop.

Barrie

Edit: the **~/** means your home folder.

My addition to my .bashrc looks like this:

```

#
#    Edit $PATH environment variable
#
PATH=$PATH:/home/barrie/myscripts/bash:/home/barrie/myscripts/python
export PATH

```

---

### Post by jonaskn on 2009-01-02
Thanks a lot for the quick and good answers.

---

### Post by scorp123 on 2009-01-02
> **Barriehie said:**
> I have some scripts that I run and I have them in **/home/barrie/myscripts/bash/** folder. Out of curiosity: Why not have them in **~/bin**? (that's /home/your_user_name/bin for those who don't understand the meaning of "~/" ... )

---

### Post by Barriehie on 2009-01-02
> **scorp123 said:**
> Out of curiosity: Why not have them in **~/bin**? (that's /home/your_user_name/bin for those who don't understand the meaning of "~/" ... )

myscripts seemed more appropriate, first folder name to mind.  No particular reason.

Barrie

---

### Post by scorp123 on 2009-01-03
> **Barriehie said:**
> myscripts seemed more appropriate The reason I ask: **~/bin** is already included per default in the search path if I am not mistaken. So it would make more sense to place your own scripts there. Placing them somewhere else and then having to manipulate the search path .... seems a bit complicated, IMHO.

---

### Post by Barriehie on 2009-01-03
> **scorp123 said:**
> The reason I ask: **~/bin** is already included per default in the search path if I am not mistaken. So it would make more sense to place your own scripts there. Placing them somewhere else and then having to manipulate the search path .... seems a bit complicated, IMHO.

Good to know, thank you!
Barrie

---

