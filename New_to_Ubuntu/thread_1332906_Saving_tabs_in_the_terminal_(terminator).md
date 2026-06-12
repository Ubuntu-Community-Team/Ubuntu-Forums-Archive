---
title: "Saving tabs in the terminal (terminator?)"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by maja_z on 2009-11-20
Hi! Complete newbie here, appreciating the terminal though!
In particular the tabs and am wondering if there is any way of saving them after a session.
In particular I tend to run a lot of R sessions at once - under Wins I would simply have a different shortcut starting in a different folder. Using the terminal I have to open a new tab and navigate tho the desired folder /working directory. Is there any way I could start the terminal with 5 tabs already open, each one pointing to a predetermined folder? I hear the terminator is meant to be good, but not sure if you can save the tabs in this way?
m.

---

### Post by cjohnston on 2009-11-20
I would try using byobu or screen.. you attach and detach from it, and you could have 5 different screens running

---

### Post by pi.boy.travis on 2009-11-20
> **maja_z said:**
> Hi! Complete newbie here, appreciating the terminal though!
In particular the tabs and am wondering if there is any way of saving them after a session.
In particular I tend to run a lot of R sessions at once - under Wins I would simply have a different shortcut starting in a different folder. Using the terminal I have to open a new tab and navigate tho the desired folder /working directory. Is there any way I could start the terminal with 5 tabs already open, each one pointing to a predetermined folder? I hear the terminator is meant to be good, but not sure if you can save the tabs in this way?
m.


I believe you can choose commands to execute as the terminal opens with arguments in the launcher, but I would recommend you do what I do: Use screen!

Screen is a window manager for the command line interface, and it does support multiple open windows, each with their own command and working directory at startup.  Screen used to be difficult to configure, but Ubuntu now includes a script called byobu that makes screen easy to use.  Just run byobu in a terminal (assuming you are using 9.10, the latest release) and screen will start.  You can press F9 to get the setup and help menu, where you can read about the keyboard shortcuts and setup multiple startup windows.  The best part is that byobu works with any terminal emulator, even if the emulator itself doesn't support tabs.  You can even suspend a byobu session to the background, even with processes running, and then reopen it from another emulator.  I find this particularly handy if I have to ssh in from Putty under Windows.

I hope this is what you were looking for!

---

### Post by pi.boy.travis on 2009-11-20
> **FFEMTcJ said:**
> I would try using byobu or screen.. you attach and detach from it, and you could have 5 different screens running

You beat me.  Sometimes there is beauty in brevity. . .

---

### Post by maja_z on 2009-11-21
Ha, from a newbie perspective brevity seems a tad overrated!

Thanks though, I'm figuring out byobu (I think). Still getting confused about the difference between windows and tabs... but I think I'll manage somehow. 

Cheers!

m.

---

### Post by pi.boy.travis on 2009-11-21
> **maja_z said:**
> Ha, from a newbie perspective brevity seems a tad overrated!

Thanks though, I'm figuring out byobu (I think). Still getting confused about the difference between windows and tabs... but I think I'll manage somehow. 

Cheers!

m.

In screen/byobu, windows and tabs are kind of the same thing. . . They look like tabs on the display, but they are really windows. . . I think. . . 

I guess I really don't know either. . .

---

### Post by maja_z on 2009-11-21
OK, sorry for this, but I have searched for a decent tutorial on byobu and am a bit lost..

OK, so I get the window/tab thing. If I open a "new window" (C-a c) it opens in the same window and I can see it as a "tab" at the bottom left. And I can switch between them using C-a C-a or C-a n/C-a p.

I can then physically open a new terminal window, where I will automatically see all the previously open tab/windows. So far so good.

Following some instructions somewhere, I did F9 and chose "Byobu currently launches at login" and in the terminal Edit/Profile Preferences/Title and Command I chose "Run command as login shell". So OK, when I start the terminal, byobu starts automatically.

But I'm completely confused about the detaching and sessions. If e.g. I close the terminal, with all the "tabs" in it. And open it again, they are all still there. (Forgive my descriptive skills of a 5-year-old). But if I reboot they are gone. So how do I save them? I tried playing around with the F9/create new window options, but can't figure out what to put as the "command" or how to activate the "add to default windows option".

Argh, I hope this makes sense!

---

### Post by niteshifter on 2009-11-21
Hi,

Alas, there's no way to save tabs with GNOME's terminal. But that doesn't mean you can't create such an environment. The script given below creates a single terminal window with three tabs, each tab has it's own working directory. This is a demo so we need to make two folders first. Open a terminal (or use the GUI) and create temp and temp2 folders in your home folder:
```
mkdir temp
mkdir temp2

```

```
#!/bin/bash
# 
gnome-terminal --tab-with-profile=Default --working-directory=/home/$USER/ --tab-with-profile=Default --working-directory=/home/$USER/temp/ --tab-with-profile=Default --working-directory=/home/$USER/temp2/

```

To make life easy create a bin folder in your home folder. Open a terminal and type:
```
mkdir bin
```
Logout and back in. The bin folder will be placed in your path.

Copy and paste the above script into Gedit and save it as tab3terminal in the bin folder.  
Next, make it executable. Either mark the file as executable in the GUI or in a terminal:
```
cd bin
chmod +x tab3terminal

```
When working from an already opened terminal just type
```
tab3terminal
```

You can create a launcher on the desktop for it as well.

The three tabs / directories (from left to right in the terminal) are:
```

Home folder     (/home/$USER)
temp            (/home/$USER/temp
temp2           (/home/$USER/temp2

```


How it works:
Command: gnome-terminal
Followed by three pairs of settings for gnome-terminal: --tab-with-profile=Default and --working-directory=<full path to directory>

Possible modifications:
Want different color schemes / fonts for each tab? Or each tab titled differently? Create and save profiles - give your new profile a distinct name - with what you like, and then use --tab-with-profile=<your profile name here>

Want more tabs? Just add more pairs.
Note that gnome-terminal <tab & directory pair> must be one logical line. Yes, it gets long. Doesn't matter. The below doesn't do what we want:
```
#!/bin/bash
# 
gnome-terminal --tab-with-profile=Default --working-directory=/home/$USER/ 
gnome-terminal --tab-with-profile=Default --working-directory=/home/$USER/temp/
gnome-terminal --tab-with-profile=Default --working-directory=/home/$USER/temp2/

```
That creates three separate windows, each window with it's own working directory.

---

### Post by maja_z on 2009-11-21
Wow, thanks, that worked like a charm! (once I disabled and detached all the byobu sessions..)

So except for the attaching and detaching in byobu/screen, which I haven't been able to put to good use any way (or understand for that matter), there is really no need for me to use byobu, I can just set up a terminal launcher with as many tabs as I like, starting wherever I want!

Thanks for taking the time and not resorting to the beauty of brevity!

---

