---
title: "tar.bz2?  What do I do with it?"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by arinlares on 2009-09-09
I know what a tar.bz2 file is, it's an archive used by Unix systems.  But, what do I do with it?  I'm trying to install Schism Tracker from the official page [here](http://eval.sovietrussia.org/wiki/Schism_Tracker).  I can extract the files from the tar.bz2 archive, and run the program, but want to install it properly, so that there's an entry in the Applications menu.  How would I do this?

Note: The version available in Synaptic does not run in Ubuntu Netbook Remix 9.04, which led me to use the tar.bz2.

---

### Post by mlentink on 2009-09-09
[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by Perfect Storm on 2009-09-09
```

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential libx11-dev libxxf86misc-dev libxv-dev x11proto-kb-dev zlib1g-dev libsdl1.2-dev

cd ~/Desktop
tar jxfv schismtracker-20090817.tar.bz2
cd schismtracker-20090817
./configure
make
sudo make install
```

Something like that.

Do also counsult **./configure --help** before running **./configure** to set flags and prefixes.

---

### Post by wojox on 2009-09-09
Open a terminal and go to the directory of the .bz2 file:

```
tar jxvf <filename>.tar.bz2
```

This will show you what it extracts, and in most cases will create a directory named <filename>.

---

### Post by nothingspecial on 2009-09-09
See above.

---

### Post by perce on 2009-09-09
> **nothingspecial said:**
> You put it in your path. ie the file you run (the executable) in /usr/bin/

sudo cp *[COLOR="Red"]executable[/COLOR]* /usr/bin/

That way you just have to type the name to run it. Then create a custom launcher with that command in it.

this is usually NOT the way things are installed. 

After extracting the archive, it will create a directory, and inside the directory there will probably be a file with some instructions - README or something like that - follow those instructions.

tar.b2, tar.gz and tgz are simply directories compressed in a unique file, like a zip in Windows. What you do with them depends on the content of the directories being compressed.

---

### Post by nothingspecial on 2009-09-09
You`re quite right.

Because he said he could run it, I made the wrong assumption.

I didn`t look at the software before I posted and assumed it was a .sh or something similar.

---

### Post by arinlares on 2009-09-09
So, the readme didn't have anything about installation.  I guess I'll move the file to /usr/bin as soon as I can figure out how to put a shortcut in Applications.  If it's called something else in Linux, correct me, as I'm still used to Windows.

---

### Post by nothingspecial on 2009-09-09
No no, read the INSTALL file. That`s where the install instructions are.

Follow Artificial Intelligence`s advice.

I was wrong, I assumed it was just a bash script.

Guess that`s the problem with quoting, bad advice is still there. Although I am well aware that it is my fault entirely.

---

### Post by arinlares on 2009-09-09
It isntalled to /usr/local/bin.  Thanks, guys.

---

### Post by Perfect Storm on 2009-09-09
<deleted as it seems OP edited post at the same time>

---

### Post by arinlares on 2009-09-09
How do I put a shortcut in Applications -> Sound & Video?  That's the last part.

---

### Post by perce on 2009-09-09
> **arinlares said:**
> How do I put a shortcut in Applications -> Sound & Video?  That's the last part.

right click on the menu to edit it, then it's quite self-explanatory.

---

### Post by perce on 2009-09-09
Do you know there is a schism in the repository? 

```
schism - ImpulseTracker clone aiming at providing the same look&feel

```

Is it what you were looking for?

---

### Post by davo11 on 2009-09-09
I had a big problem with this when I started using Ubuntu.
Basically you need to get rid of the .tar.bz2. Well to get rid of the bz2 just r-click>extract. Easy.
Now you need to open a terminal, navigate to the folder containing the file cd /???/???/???. Then type something like "tar -xzvf filename.tar".
And there you have it!

---

### Post by arinlares on 2009-09-09
> **perce said:**
> Do you know there is a schism in the repository? 

```
schism - ImpulseTracker clone aiming at providing the same look&feel

```

Is it what you were looking for?

In that package, everything *but* Schism worked.

How do I add icons to my /usr/share/icons/hicolor/scalable directory?  I would like to have the launcher icon have the schism icon next to it, instead of the GNOME launcher icon.

---

