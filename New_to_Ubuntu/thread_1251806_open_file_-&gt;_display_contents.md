---
title: "open file -&gt; display contents"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by anatak on 2009-08-28
Hello,

I am trying to change the behavior of opening .inc files (include files for php)
I want to open the files with jEdit.
but now ubuntu always asks me if I want to run the file or display it contents. I know I can change the behavior for every single file but is there a way to change the settings so that .inc files always open with jEdit without having to confirm that you want to display the content and not run it as a program ?

thank you
anatak

---

### Post by stumbleUpon on 2009-08-28
Ubuntu asks something to run as a program if you have enabled permissions to run the file as an executable program.

Right click on the file >  Properties > Permissions
Uncheck "Allow executing file as program"
Then go to the "Open with" tab. Select jedit if you see it in the list. If not,  click on add, use custom command and enter the path to jedit (usuaully /usr/bin/jedit , but you can find out exactly which one by entering "which jedit" in a terminal )

---

### Post by anatak on 2009-08-28
I did that with two files.
Ubuntu still asks me if I want to run the files as a program or display the content ?
Do I have to do this with every single file ?

---

### Post by CatKiller on 2009-08-28
> **anatak said:**
>  Do I have to do this with every single file ?

Every file that you've set as [executable]("http://en.wikipedia.org/wiki/Executable"), yes. There's no reason to make a file executable unless you actually intend to execute it. But this warning is for people that have random files set as executable, to prevent them from inadvertently running something that may bork their system.

If you don't want to get out of the habit of having files executable when they shouldn't be, and you never want to run an executable file from the file manager, you can change this warning behaviour by changing the preferences.

(Open a file browser window) &#8594; Edit &#8594; Preferences &#8594; Behaviour &#8594; View executable text files when they are opened.

---

### Post by blueridgedog on 2009-08-28
> **CatKiller said:**
> 

(Open a file browser window) &#8594; Edit &#8594; Preferences &#8594; Behaviour &#8594; View executable text files when they are opened.

Agree...

Advice to the original poster: good housekeeping and good longterm habits suggest that you manage the permissions/mode of your files (especially if you are a developer).  Keeping your .inc files in a location that works for you could simply be a matter of cd'ing to that location and doing a chmod 644 *.inc.

Many files come across from other non-aware files systems with execute permissions and the thing to do (in my opinion) is to correct the properties of the file.

---

### Post by anatak on 2009-08-30
Thanks everybody,

The files are indeed copied from a window system. This may be the reason they are flagged as executable.
I also found out that I can select multiple files and change them to text files in the gui.

thank you for helping.
anatak

---

### Post by CatKiller on 2009-08-30
> **anatak said:**
> my first wish for linux would be that CTRL+C and CTRL+V would work across all programs.

And what would you have them do? Ctrl-C has been the shortcut to cancel a running process on UNIX-like platforms for longer than Microsoft has existed. Graphical tools have adopted this shortcut for the convenience of users like yourself, but there's no reason at all for the command line to change the behaviour that it's had for decades. If you want to copy and paste with gnome-terminal, you could use Shift-Ctrl-C & -V. That's what they're there for; something easy for ex-Windows users to remember that doesn't break everything else.

---

