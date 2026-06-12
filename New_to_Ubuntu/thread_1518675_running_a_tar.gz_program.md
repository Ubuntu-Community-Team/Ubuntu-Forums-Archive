---
title: "running a tar.gz program"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by beelzebufo on 2010-06-26
I am having a hard time running really any downloaded program, anyway, this time specifically I am trying to run yamipod.  I can extract, but then, as always no executable progam... what am I missing?

---

### Post by -humanaut- on 2010-06-26
Try this from the command line

tar -xvf /whereprogramis/program.tar.gz
gunzip /whereprogramis/program.tar.gz
chmod +x /whereprogramis/program
cd /programfile
./program

---

### Post by aysiu on 2010-06-27
Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
wget -c http://download1.schoonzie.com/yam-linux.tar.gz
tar -xvzf yam-linux.tar.gz
cd yam-linux
sudo cp libfmodex.so.4.02.05 /usr/lib/
chmod +x YamiPod
./YamiPod
``` If you get any error messages, post them back here.

---

### Post by beelzebufo on 2010-06-27
ok, so now I got it... where is it? what do I do to rip my ipod? and isnt' there an easier way other than having to know some foreign programming language to use ubuntu?  It seems like every time I am trying to do anything on here, I have to come onto the forum and have you computer gurus show me how, even the simplest things.  I really like ubuntu, but I must be missing something because everything is ridiculously difficult

---

### Post by da burger on 2010-06-27
This is isn't the typical way to install software. Generally you would go into the ubuntu software center, find the program you want to install and click on it. However the program you mentioned isn't in the software center and the people who make it haven't provided and easier way to install it (for example a .deb file allows one click install like in windows). 

Also all the commands given by the people above me could have been done by point and click but since this is a one off operation and it's a lot easier for us to give you the info like this they chose to use terminal commands.

If you have any questions about my post please just ask.

Angus

EDIT Just realised I didn't answer your question. The program appears to be in the YamiPod file. Double clicking that should run it, and if you want an icon on your desktop right-click, select create launcher give  it a name, the command is the path to that YamiPod file.

---

### Post by -humanaut- on 2010-06-27
A quick suggestion have you tried gtkpod its a very capable program and only requires a quick sudo aptitude install gtkpod from the terminal so you don't have to build from source.

---

### Post by aysiu on 2010-06-27
Can't Ubuntu just "rip" iPods without installing additional software?

Are you running Ubuntu 10.04 (the latest version)?

More details here:
[http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

---

### Post by beelzebufo on 2010-06-27
I am running 10.04.  when I open the yamipod folder, I see the icon for the program, but then I double click and nothing happens.  trying the gtkpod now...

---

### Post by aysiu on 2010-06-27
> **beelzebufo said:**
> I am running 10.04. If that's the case, I'm not sure Yamipod or Gtkpod is really necessary. So when you plug in your iPod, it doesn't just show up as a drive on the desktop? And what happens when you open up Rhythmbox?

---

### Post by beelzebufo on 2010-06-28
when I just open it from the places menu, I don't get any music files, just the base folders on the ipod, with gtkpod, it all opens, but I can't play any of the songs, something about xmms play now function?

---

