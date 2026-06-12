---
title: "[SOLVED] Can someone write me a simple program?"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by 311005901 on 2008-12-20
I don't know how to write code, but this should only take like 30 seconds and about 10 lines if someone could (please) do it for me. [-o<

I just need a simple program written that can take a ".bin" or ".sh" file and run it so I don't have to open up a terminal and drag it in there.

I'm thinking the steps would go like this:
1. sudo chmod "file" 770
2. "file"
or
2. sh "file"

Thats all it would take. I just want a program that runs applications automatically like the Windows equivalent ".exe" when I double click in Nautilus.

Can someone please do this for me? [-o<
I would be your friend forever. :D

---

### Post by mapes12 on 2008-12-20
> **311005901 said:**
> I don't know how to write code, but this should only take like 30 seconds and about 10 lines if someone could (please) do it for me. [-o<

I just need a simple program written that can take a ".bin" or ".sh" file and run it so I don't have to open up a terminal and drag it in there.

I'm thinking the steps would go like this:
1. sudo chmod "file" 770
2. "file"
or
2. sh "file"

Thats all it would take. I just want a program that runs applications automatically like the Windows equivalent ".exe" when I double click in Nautilus.

Can someone please do this for me? [-o<
I would be your friend forever. :DNautilus is a file browser, not an application launcher. What applications exactly are you trying to start?

---

### Post by jamesrl on 2008-12-20
Windows specifies files that are executable by their extension e.g. (binary executables *.exe or *.com, batch files *.bat).

Linux the file extension is just for part of its name for organization purposes (and for programs to help recognize it).  Execution privelges have to be given to the executable before it can be run.  This can be done in the terminal by the method you described, or in nautilus by right clicking, going to properties and clicking mark as executable.  [This is a good thing, so say files you download from the internet thinking they contain say pornographic images of a local celebrity (or whatever the spam screensavers used to have) do not have permission to execute arbitrary code on your computer, unless you explicitly change it.] 

The commands you listed:
1) chmod 770 file 
gives all read/write/execute permission (4+2+1)
2) ./file (executes the file from the script), though you could equivalently launch it from nautilus by clicking on it (based on default settings -- sometimes you get to look at source code for executable scripts).

The second command explicitly launches a shell script, by executing /bin/sh.

---

### Post by ugm6hr on 2008-12-20
You can already double-click on executables to launch.

Try /usr/bin/firefox or /usr/bin/gimp etc

Why would you want to launch them from Nautilus? That's what the menu is there for.

But if you want, it is easy enough to create links to anywhere else (other than /usr/bin) if you want (e.g. Desktop).  You don't need any programming or script.

---

### Post by jamesrl on 2008-12-20
If you really want to do what you say you do; just type this in to the terminal.
```

ln -s /bin/bash ~/Desktop/bash_link

```
This creates a link on the desktop, to bash (a shell) that you can drag text files into.
Then just drag what ever executable shell script (e.g., typically ends in .sh).  If it is a python script (ends in .py), you can do the same thing but with
```

ln -s /usr/bin/python ~/Desktop/python_link

```
This method (similar to the 'sh file_name' method doesn't change the execution privileges of the script).

---

### Post by 311005901 on 2008-12-20
Ok. I guess I didn't write clear enough. Sorry...

I'll give an example:
Step 1: I download "planeshift.bin" from the internet and save it on my desktop.
Step 2: I look at my desktop.
Step 3: I double click on "planshift.bin" and the program I'm dreaming about automatically opens it after I type my password.

or

Step 1: I wget "planeshift.bin" and save it to my home directory.
Step 2: I look at my home directory in Nautilus.
Step 3: I double click "planeshift.bin" and the program I'm dreaming about automatically opens it after I type my password.

What I have to do now:
Step 1: I download "planeshift.bin" from the internet and save it on my desktop.
Step 2: I look at my desktop.
Step 3: I open up a terminal.
Step 4: I type "gksu chmod" [click and drag "planeshift.bin" into the terminal] 770 [hit enter and type in password]
Step 5: Click and drag "planeshift.bin" into the terminal and hit enter.
Step 6: Minimize the terminal because it looks ugly.

I just want a simple solution to let me run stuff I download regardless of the permissions.

---

### Post by ugm6hr on 2008-12-20
What happens if you double-click the .bin file to begin with?

It should be possible to make it an executable by right-clicking (and also change permissions - although I suspect that shouldn't actually be necessary) - this is only necessary once for each executable.

Once done, a double-click should run it each time (if you set nautilus to run executables as default).

---

### Post by starcannon on 2008-12-20
I am a wee bored and too much snow outside, so what the hell, I'll give this a shot; besides I am interested in learning more about bash scripting.
Let me start by saying, I am no Bash Scripting Guru, and that anything I come up with should be considered highly experimental, and that anyone who decides to use the script takes on full responsibility for any damage the script may cause. To be blunt, if something goes tragically wrong, its your problem, not mine. Okay that said, I will start with basic, and then continually update it as I find more interesting things to put on it, it should be noted that the script itself will require you to right click on it and under the permissions tab set it to "Allow executing file as program" to be checked (you can do this to your bin file as well by the way, and then you could Alt+F2 gksu /path/to/planeshift.bin) but this for me is more about doing it for kicks than anything practical, as in my opinion a script like this is superfulous and un-needed to begin with ;)

So without further ado, my first most basic stab at this is:
```

#!/bin/bash 
# This script will set a file to be exectuble, and then run with super user
# permissions. First attempt will be short and crude; eventually I would like
# it to be capable of being useful in a r-click on item menu option, for now it
# will have to reside in the directory where the file is located.
#
# Install instructions, save this file as binx.sh, then r-click the file, and
# under the permissions tab enable the "Allow executing file as program" option;
# now double click the binx.sh file and choose "Run" from the options in the
# pop-up window.
# These instructions were developed using Ubuntu 8.10 with Gnome, your distro
# and Desktop Manager may require other directions.
#
# Change every bin file in the current directory to be executable
# by all users
chmod a+x ./*.bin
# Run every bin file in the current directory as superuser 
gksu ./*.bin

```
You must put the bin file your working with in it's own directory, this version of binx.sh will change permissions for ALL bin files in its directory, AND run all bin files in its directory as Super User.

---

### Post by 311005901 on 2008-12-20
Hmmm... Didn't work for me.
Terminal spits out:
```
tim@laptop:~$ '/home/tim/Desktop/binx.sh' 
chmod: cannot access `./*.bin': No such file or directory
tim@laptop:~$ 

```

The file I was opening was "GoogleEarthLinux.bin"

---

### Post by anewguy on 2008-12-20
Why not:

(1) in a terminal window:

cd wherever-the-file-is

sudo chmod 755 filename - enter your normal password when asked

(2) in the normal file browser:

locate the file

right-click on it and say create link

drag the link to your desktop

(3) on your desktop, click on the link

Step (1) makes the file executable
Step (2) creates the equivalent of a Windows short cut and places it on your desktop

Step (3) is just to execute the program


Dave :)

---

### Post by starcannon on 2008-12-20
The script is just clicked and run in the directory where the bin file you want is.

This is crude, and as pointed out in my first post, superfluous, though once I get the hang of using **read** in a bash script it may become useful. But for now what one would do with my dinky little script would be to save it in a directory where google_earth.bin is located, then double click the binx.sh script, it will make the google_earth.bin file executable, and then run it with super user permissions.

Anyway, I'm reading up on the **read** man pages; I even found a script [here]("http://cfaj.freeshell.org/shell/scripts/mouse-demo-sh") that demonstrates the use of a mouse in a bash script using **read** so one step at a time. As mentioned before I'm no guru, and am only doing this because I have nothing else to do today, and I have a desire to work on my bash scripting; this should definately accomplish all of my goals, but may not accomplish any of yours hehe. Anyway, keep an eye on the script in [Post Number 8]("http://ubuntuforums.org/showpost.php?p=6407043&postcount=8"), as I will just continue to modify it instead of making new posts for revisions.

I'll likely move my script over to the programming forum shortly as it seems more appropriate to what I'm doing, and update post number 8 as progress is made.

---

### Post by anewguy on 2008-12-21
In reality, if what you want to do is install a program and click on it on your desktop like you would with Windows, just follow my previous post.  You only need to be sure it is accessable to you (if you don't own it, use sudo to change the permissions and also the ownership).  Then just create the shortcut (link in Linux terms) and move it to your desktop.

Dave :)

---

### Post by jediborger on 2008-12-21
Really want you want is a small program/script to do the executing work for you. Then we will tell nautilus to use this script to launch certain file types such as ".bin". So here we will make a script called bin_launcher.sh
```
/bin/bash

gksu chmod +x $@
$@
```
Save this file somewhere, I would put it in /usr/local/bin and make this file executable by
```
sudo chmod +x /usr/local/bin/bin_launcher.sh
```
Now you will only have to do this once but get a bin file and right click and go to properties. Select the "Open With" tab and click "Add." Expand this window so you can select a custom command. Click "Browse" and select "/usr/local/bin/bin_launcher.sh". Now Nautilus should remember this selection for all bin files or whatever file type you do this procedure to. So for any file you want to automatically chmod and launch just point it to this script. Hope this solves your problem.

---

### Post by 311005901 on 2008-12-21
> **jediborger said:**
> Really want you want is a small program/script to do the executing work for you. Then we will tell nautilus to use this script to launch certain file types such as ".bin". So here we will make a script called bin_launcher.sh
```
/bin/bash

gksu chmod +x $@
$@
```
Save this file somewhere, I would put it in /usr/local/bin and make this file executable by
```
sudo chmod +x /usr/local/bin/bin_launcher.sh
```
Now you will only have to do this once but get a bin file and right click and go to properties. Select the "Open With" tab and click "Add." Expand this window so you can select a custom command. Click "Browse" and select "/usr/local/bin/bin_launcher.sh". Now Nautilus should remember this selection for all bin files or whatever file type you do this procedure to. So for any file you want to automatically chmod and launch just point it to this script. Hope this solves your problem.

Wonderful!
That was just what I was dreaming about!
Thanks! :D

---

