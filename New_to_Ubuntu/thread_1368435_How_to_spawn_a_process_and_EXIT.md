---
title: "How to spawn a process and EXIT"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by Kilarin on 2009-12-30
stupid question, sorry.  This should be easy, but I can't seem to find the answer.

I've got a batch job that does several things, such as mounting a truecrypt volume.  THEN, it runs a program on that truecrypt volume, like this:

wine "j:\\NoteTab-Pro\\NotePro.exe"

Works just fine.  The problem is, the TERMINAL is hung up waiting for NoteTab to exit.  The terminal sticks around until you close NoteTab.  I don't want the terminal anymore.  I want it to spawn the NoteTab process, and then exit.  

I tried

spawn wine "j:\\NoteTab-Pro\\NotePro.exe"

The terminal exited, but it didn't start the wine/notetab process.  

How do I get linux to start a new process and EXIT?

thanks!

---

### Post by thatguruguy on 2009-12-30
The process is running within the terminal. If you close the terminal, you close the process.  Is there a reason, other than purely aesthetic ones, that you want the terminal to close before the process is over?

---

### Post by J V on 2009-12-30
You can't... but when you run the script (bash I presume?) if you chose "run" as opposed to "run in terminal" it wouldn't spawn the terminal anyway...

---

### Post by benfindlay on 2009-12-30
Try using this:

```
wine "j:\\NoteTab-Pro\\NotePro.exe" 2>&1 & exit

```

That should leave it running and close the terminal window. If not let me know what it does and we can tweak more.

I should point out that a potential downside to this is that you will have a process that will keep running until you reboot or kill it off.

EDIT: as an afterthought, a simple & added to the end of the last line of your command list might be enough; I'd try that first! You will only need the 2>&1 if there is funky stuff going on with stderr and stdout

---

### Post by Kilarin on 2009-12-30
> Is there a reason, other than purely aesthetic ones, that you want the terminal to close before the process is over? 
Purely aesthetic.  This terminal window is just sitting around and I'm DONE with it.  It did its thing, it should be gone now.

In DOS, the [START](http://www.computerhope.com/starthlp.htm) command could do this.  It would spawn a new process in a separate window and the batch job could chug merrily along without waiting on that process to "complete".  There has GOT to be a way to do the same thing from the linux command line.

---

### Post by Kilarin on 2009-12-30
> If not let me know what it does and we can tweak more.
I tried both the & and the 2>&1 & exit.

In both cases the terminal closes, but the notetab application does NOT start.  Doesn't even show up on the system monitor.

The & on the end of line looks EXACTLY like what I need.  (now that I know what to look for)  But I can't figure out why it isn't working.


> I should point out that a potential downside to this is that you will have a process that will keep running until you reboot or kill it off.
I'm trying to spawn an actual application.  A text editor to be precise.  So closing it shouldn't involve any more than clicking the X on the gui.

---

### Post by Kilarin on 2009-12-30
Clarification: Using Ubuntu Koala with Gnome

---

### Post by benfindlay on 2009-12-30
When you run it normally, does the terminal window go back to a command prompt (saying something like user@computer$), or just flash a blinking cursor at you?

---

### Post by Kilarin on 2009-12-30
> When you run it normally, does the terminal window go back to a command prompt (saying something like user@computer$), or just flash a blinking cursor at you?
Terminal window just flashes a blinking cursor.

to simplify, forget the wine/notetab program.  What I'm trying to do is the following

script runs, mounts a truecrypt volume, perhaps does some other things, and the last line of the script is:

gedit testfile.txt

which opens a gedit window to edit testfile.txt

BUT, now my terminal window is just hanging around, flashing its cursor.  It's not really DOING anything, Its just waiting for me to close the gedit window.  But I might have the gedit window open for hours.  So why should I have this extra terminal hanging around confusing things?  Sure, I can send it off to a different desktop and not see it anymore, but aesthetically, it just bugs me that its there and it doesn't NEED to be there.

In DOS, I could have simply had the command be:
START notepad testfile.txt

and it would have spawned notepad, and the batch file would run on to the next command without paying any more attention to the notepad window.

So far I've found that almost EVERYTHING I did in DOS/Windows I can do far better in linux.  But this time I'm stymied.

using 
gedit testfile.txt &

doesn't ever spawn the gedit window.

Do I need to route it through gnome-terminal somehow?

gnome-terminal -e gedit testfile.txt

leaves the terminal still locked an waiting for gedit to end

gnome-terminal -e gedit testfile.txt &

never spawns the terminal

---

### Post by benfindlay on 2009-12-30
Okay, lets try another approach. Firstly, I'm assuming that when you just type the command into terminal manually it works?

Am I right in assuming you are invoking a preset bash script that looks something like this to run your series of commands:```
#!/bin/bash
command 1
command 2
command 3
etc
```
If this is so, we can try creating an icon that you can simply click to run it all. I'm a bit rusty on gnome (I use 8.04 server myself so no GUI), but I believe that if you right click on the desktop you have the option to create a "Launcher". In the command section of the dialog box you need to enter the following: ```
sh -c /path/to/your/script
```
The rest of the details are upto you. Make sure your script is marked executable and you should be good to go!

Save it on the desktop, or your home directory, drag it to the menu bar at the top; it's your choice. But you can just click on it and it should run without terminal that way.

---

### Post by Kilarin on 2009-12-30
> If this is so, we can try creating an icon that you can simply click to run it all.
Well, THAT is an approach I had not considered, and it works.  thanks!

---

### Post by benfindlay on 2009-12-30
No problem! I only recently discovered it myself quite recently as a way to get around a hanging terminal problem I was having! Glad I could help!

---

### Post by MartijnNL on 2010-02-25
I was looking for something similar, only my script requires user input (hit any key to continue) so a normal run launcher doesn't do it. Instead I found some post about the dtach command (requires you to install the dtach package).

By using dtach with the -n option I managed to solve this.

```

other stuff
dtach -n /tmp/quod quodlibet
exit
```

This does something similar to "quodlibet &" but this works in a shell script as well.

Maybe this will help other people searching for something similar.

By the way dtach is a slim version of the "screen" package, which I haven't tried.

---

