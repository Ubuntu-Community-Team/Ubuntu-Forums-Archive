---
title: "iPod Nano 4g libgpod Problem"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by andrewt522 on 2010-01-15
I have a black, 4th Gen, 8gb, iPod Nano.  I mention the color because according to [this bug report]("https://bugs.launchpad.net/ubuntu/%2Bsource/libgpod/%2Bbug/461639"), the black 4g Nano is causing a major problem.

I have all the same problems described at the top of the bug report.  I plug in the device, it mounts, I open Rhythmbox, it is listed in the library, and that's about it.  No sync, although I can see the playlist.  When I eject, the iPod says that there are no songs, although it's still filled.  I should also mention, I can see the files in Nautilus. 

If I am understanding the bug report correctly, because of a bug in libgpod, Rhythmbox is accidentally corrupting the iPod's database.  Apparently, this [has been fixed]("https://bugzilla.gnome.org/show_bug.cgi?id=599772").  This is where I need help.

I see that there is a tar.gz attachment with two Jaunty and Three Karmic iTunes databases.  Is this the necessary fix, and if so, how do I apply it?  Is it possible that the fix has already been applied and am I missing something else?  Am I barking up the wrong tree and need to look elsewhere?

Any help or information you could provide would be most helpful.  Thanks!

---

### Post by warfacegod on 2010-01-16
Try getting gtkpod from Synaptic.

---

### Post by andrewt522 on 2010-01-16
Thanks so very much for your response.

While gtkpod doesn't answer my question, per your suggestion, I have installed it.  This opens up a new problem as gtkpod does not acknowledge my iPod.  Remember, the database has been corrupted and shows no songs, even though, per nautilus, they are there.

I'm not opposed to using gtkpod to manage my iPod.  However, per my previous post, there is a bug fix available for libgpod and I would like to know how to apply it.

In the end, I guess I'd like to have all my available options working and then decide which works best for me.

---

### Post by andrewt522 on 2010-01-16
Update to last post...

The iPod is plugged in, but it's not mounted.  This keeps getting worse.

Yes, ditch the iPod for something friendly.  However, that's not an option right now. Any help would be most appreciated.

---

### Post by warfacegod on 2010-01-16
Didn't want to leave you hanging in the dark. I've been reading your bug fix link. I'm currently trying to translate Dorkese into English. I'll get back to you.

---

### Post by andrewt522 on 2010-01-16
Awesome!  You're the best!  Thanks so very much!!!

---

### Post by nothingspecial on 2010-01-16
The bug report mentions that issue should be fixed in the latest release of libgpod so you could try compiling the latest libgpod and gtkpod. This has fixed this issue with my sons 5th gen with video camera.

```
sudo apt-get remove --purge libgpod4 gtkpod
```

```
sudo apt-get build-essential autoconf flex gettext libglib2.0-dev libgtk2.0-dev libglade2-dev libid3tag0-dev libxml-parser-perl pkg-config automake gcc git-core gtk-doc-tools libcurl4-dev libflac-dev libgnomevfs2-dev libhal-dev libvorbis-dev libmp4v2-dev

```

```

git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/libgpod
```
```
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod
```

```
cd libgpod/
./autogen.sh
make
sudo make install
```
```

cd ../gtkpod/
./autogen.sh
make
sudo make install
```



I don`t know if it will help you. If it works it should fix rhythmbox as well as they both use libgpod.

---

### Post by warfacegod on 2010-01-16
nothingspecial's code looks sound to me. I'm no expert but it looks like it will do what your fix link suggests. If you need help with the code, send me a PM and I'll pop back to the thread and assist.

---

### Post by andrewt522 on 2010-01-16
When I run the first command I get:

```
andrewt522@andrewt522-laptop:~$ sudo apt-get remove --purge libgpod gtkpod
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgpod
andrewt522@andrewt522-laptop:~$ Reading package lists... Done
Reading: command not found
andrewt522@andrewt522-laptop:~$ Building dependency tree       
Building: command not found
andrewt522@andrewt522-laptop:~$ Reading state information... Done
Reading: command not found
andrewt522@andrewt522-laptop:~$ E: Couldn't find package libgpod

```

A quick search in Synaptic reveals that I have libgpod4 0.7.2-1ubuntu1 installed, which I assume is the latest version?

---

### Post by nothingspecial on 2010-01-16
Sorry make that libgpod4

edited original post

---

### Post by warfacegod on 2010-01-16
That means libgpod isn't on your machine. You may have inadvertently solved your problem. Look in Synaptic and search libgpod to see if anything is installed.

---

### Post by Simian Man on 2010-01-16
I don't use Ubuntu, so I can't help with installing the right bits, but I have the EXACT same ipod, down to the color and capacity.  It works great with any program that uses libgpod 0.7.2 including Rhythmbox, so this is definitley something that should work.

---

### Post by andrewt522 on 2010-01-16
Ok, with Nothingspecial's correction, the first step worked fine. When I attempt the second step, I get:

```
andrewt522@andrewt522-laptop:~$ sudo apt-get build essential autoconf flex gettext libglib2.0-dev libgtk2.0-dev libglade2-dev libid3tag0-dev libxml-parser-perl pkg-config automake gcc git-core gtk-doc-tools libcurl4-dev libflac-dev libgnomevfs2-dev libhal-dev libvorbis-dev libmp4v2-dev
E: Invalid operation build

```

Please advise.

---

### Post by warfacegod on 2010-01-16
That may need to be:

```
sudo apt-get install essential autoconf.......
```

Not:

```
sudo apt-get build essential autoconf........
```

But I'm not certain.

---

### Post by Simian Man on 2010-01-16
> **andrewt522 said:**
> Ok, with Nothingspecial's correction, the first step worked fine. When I attempt the second step, I get:

```
andrewt522@andrewt522-laptop:~$ sudo apt-get build essential autoconf flex gettext libglib2.0-dev libgtk2.0-dev libglade2-dev libid3tag0-dev libxml-parser-perl pkg-config automake gcc git-core gtk-doc-tools libcurl4-dev libflac-dev libgnomevfs2-dev libhal-dev libvorbis-dev libmp4v2-dev
E: Invalid operation build

```

Please advise.

It should be:
```
sudo apt-get install **build-essential**
```
instead of:
```
sudo apt-get build essential
```

Even I know that much :).

But if you can install libgpod 0.7.2 from the package manager, that should work as is.  You shouldn't have to install it from source unless the version in the repos is broken or out of date.

---

### Post by andrewt522 on 2010-01-16
Thanks guys.  This is starting to make (a little) sense.  From what I could tell, the first command:```
sudo apt-get remove --purge libgpod4 gtkpod
```uninstalled not only gtkpod, but Rhythmbox and Amarok as well.  I checked Synaptic to see if libgpod had been uninstalled as well (as it should because of the command) and, indeed, it was.

I reinstalled Rhythmbox, plugged in my iPod, and it showed up in the libraries.  Went back to Synaptic and saw that libgpod4 & libgpod-common had been reinstalled as well.  Now, I'm trying to restore the database on the iPod as it still shows 0 songs, all of which show up in Rhythmbox and in Nautilus.  I vaguely remember seeing a thread and I will keep you posted.

On a related note, thanks for the help correcting the commands.  The corrections help make the commands make more sense! :D

---

### Post by warfacegod on 2010-01-16
> **Simian Man said:**
> It should be:
```
sudo apt-get install **build-essential**
```
instead of:
```
sudo apt-get build essential
```

Even I know that much :).

But if you can install libgpod 0.7.2 from the package manager, that should work as is.  You shouldn't have to install it from source unless the version in the repos is broken or out of date.

Yes, that would be it. You guys ever catch Charlton Heston?

---

### Post by nothingspecial on 2010-01-16
@ Andrewt522

I`m sorry about the typos.

I guess that`s why it`s a risky business blindly copying and pasting commands from the command line.

Did you manage to build the latest libgpod and gtkpod?

If so, can you check ```
[COLOR="Red"]/media/ipod[/COLOR]/iPod_Control/Device/SysInfo
```

(substitute the red code for the location of ***your*** iPod)

You should have a line in there that reads something like

```
FirewireGuid: 0xfoo345bar4526bar
```

if so this is good - note the 0x at the start.

If not, run ```
lsusb -v | grep -i Serial
```

and add the line.

---

### Post by andrewt522 on 2010-01-16
No sweat, I appreciate you taking the time and helping me work through this!

Steps 1, 2, and 3 worked fine.  Unless I'm reading it wrong, steps 4 & 5 failed: ```
andrewt522@andrewt522-laptop:~/libgpod$ make
make: *** No targets specified and no makefile found.  Stop.
andrewt522@andrewt522-laptop:~/libgpod$ sudo make install
make: *** No rule to make target `install'.  Stop.
```They did run through their processes, so it's possible they worked.

As such, I can't seem to get ```
/media/ipod/iPod_Control/Device/SysInfo
```to work.```
andrewt522@andrewt522-laptop:~$ /media/ANDREW T/iPod_Control/Device/SysInfo
bash: /media/ANDREW: No such file or directory
```Unless, of course, I'm entering it wrong.

---

### Post by nothingspecial on 2010-01-16
Did ./autogen.sh work?

autogen should automatically generate (see how it works ;)) a make file yet make says there isn`t one. Did autogen exit with errors?

To find out where your iPod is mounted either plug it in and type ```
mount
```

or find it in your file browser and go backwards untill you have the complete path.

---

### Post by nothingspecial on 2010-01-16
> **andrewt522 said:**
>  ```
/media/ipod/iPod_Control/Device/SysInfo
```to work.```
andrewt522@andrewt522-laptop:~$ /media/ANDREW T/iPod_Control/Device/SysInfo
bash: /media/ANDREW: No such file or directory
```Unless, of course, I'm entering it wrong.

Looking specifically at this, if the path to your iPod is /media/ANDREW T/
then in order for the terminal to recognise it you need to type

```
/media/ANDREW\ T
```

This is because a "space" has a special meaning to the terminal and you have to ***escape*** it.

Escape it means to tell the terminal to ignore it`s special meaning and treat it literally.

The escape character in the bash shell is \ 

so putting a \ before a space tells the terminal to ignore it`s special meaning and treat it as an actual space

I hope that makes sense and doesn`t sound like geek speak.......


.....ok it does sound like geek speak, but I hope it makes sense none the less. :P

---

### Post by warfacegod on 2010-01-16
> **nothingspecial said:**
> Looking specifically at this, if the path to your iPod is /media/ANDREW T/
then in order for the terminal to recognise it you need to type

```
/media/ANDREW\ T
```

This is because a "space" has a special meaning to the terminal and you have to ***escape*** it.

Escape it means to tell the terminal to ignore it`s special meaning and treat it literally.

The escape character in the bash shell is \ 

so putting a \ before a space tells the terminal to ignore it`s special meaning and treat it as an actual space

I hope that makes sense and doesn`t sound like geek speak.......


.....ok it does sound like geek speak, but I hope it makes sense none the less. :P

I shall confirm. It does indeed sound like geek speak. Probably because it is.

---

### Post by nothingspecial on 2010-01-16
> **warfacegod said:**
> I shall confirm. It does indeed sound like geek speak. Probably because it is.

Yeah, your right, I thought so.

Just put a \ between the ANDREW and the T and don`t worry about why.

EDIT ----- But keep the space ------EDIT

EDIT2 ---- After the \        ------EDIT2

EDIT3 ---- But don`t forget to say weather libgpod compiled ok or not ----EDIT3

---

### Post by andrewt522 on 2010-01-16
Yes, it appears that libgpod compiled correctly.  At least, I didn't notice any errors and seemed to finish.

Now, I run the code making the ***escape*** correction and I get:```
andrewt522@andrewt522-laptop:~$ /media/ANDREW\ T/iPod_Control/Device/SysInfo
andrewt522@andrewt522-laptop:~$
```
I'm sorry guys.  I feel like I'm missing something obvious here, yet nothing seems to be working right.

---

### Post by andrewt522 on 2010-01-16
I don't know what the difference was, but I was finally able to get something out of SysInfo...```
andrewt522@andrewt522-laptop:~$ /media/ANDREW\ T/iPod_Control/Device/SysInfo
/media/ANDREW T/iPod_Control/Device/SysInfo: line 1: ModelNumStr:: command not found
/media/ANDREW T/iPod_Control/Device/SysInfo: line 2: FirewireGuid:: command not found
andrewt522@andrewt522-laptop:~$ 
``` Doesn't look too promising.

---

### Post by warfacegod on 2010-01-16
Just thought I'd let you know that someone is still reading this. Although I can no longer help, way too geek speak for me.

---

### Post by andrewt522 on 2010-01-16
Thanks for hanging in there, Warfacegod.  I really appreciate all of your help today.  

I'm beginning to think that I should reformat the iPod in iTunes and give gtkpod a go, as you initially suggested.  Even then, there's no guarantee I receive a satisfactory result.  

Honestly, I want to throw in the towel, take all my music to work and manage my iPod from there.  I know that if I just hang in there and work this out, i'll benefit the next guy with the same problem.

Anyway, thanks again.

---

### Post by warfacegod on 2010-01-16
> **andrewt522 said:**
> Thanks for hanging in there, Warfacegod.  I really appreciate all of your help today.  

I'm beginning to think that I should reformat the iPod in iTunes and give gtkpod a go, as you initially suggested.  Even then, there's no guarantee I receive a satisfactory result.  

Honestly, I want to throw in the towel, take all my music to work and manage my iPod from there.  I know that if I just hang in there and work this out, i'll benefit the next guy with the same problem.

Anyway, thanks again.

Usually when I want to give up, I set the issue aside and go back to it later. I did that with Amarok 1.4 (2.2 is horrible), dealt with 1.4 not being fully functional because I couldn't get it to compile. Tried every few months. Got it to work perfectly yesterday.

If doing things this way gets too frustrating, you might consider installing VMware and running Windows in it so that you can use iTunes.

---

### Post by nothingspecial on 2010-01-17
> **andrewt522 said:**
> I don't know what the difference was, but I was finally able to get something out of SysInfo...```
andrewt522@andrewt522-laptop:~$ /media/ANDREW\ T/iPod_Control/Device/SysInfo
/media/ANDREW T/iPod_Control/Device/SysInfo: line 1: ModelNumStr:: command not found
/media/ANDREW T/iPod_Control/Device/SysInfo: line 2: FirewireGuid:: command not found
andrewt522@andrewt522-laptop:~$ 
``` Doesn't look too promising.

Sorry I`m not making myself clear

sysinfo is a text file in your ipod. To check weather your ipod serial number is in there you can use the cat command

```
cat /media/ANDREW\ T/iPod_Control/Device/SysInfo
```

---

### Post by andrewt522 on 2010-01-17
Hooray!!!```
ModelNumStr: xB754
FirewireGuid: 000A27001D3CF207
```

---

### Post by nothingspecial on 2010-01-17
That looks ok.

Can you try running the autogen.sh then make please

---

### Post by nothingspecial on 2010-01-17
> **andrewt522 said:**
> 

I reinstalled Rhythmbox, 

That could be a problem because it will reinstall the old libgpod4 along with it and you are trying to install the new one

```
sudo apt-get remove libgpod4
```

Don`t worry that it will remove rhythmbox, you can reinstall it once you have the latest libgpod

---

### Post by nothingspecial on 2010-01-17
I think I`ve found the problem. You need 2 extra packages, autogen.sh should have given you errors about them.

```
sudo apt-get install libplist-dev libsqlite3-dev

```

Then

```
cd libgpod/
./autogen.sh
make
sudo make install
```

---

### Post by andrewt522 on 2010-01-17
Ok, guys.  I don't fully understand what happened, but things are working.

I gave in and restored my iPod using iTunes on my Wife's laptop.  I went directly to gtkpod, identified my iPod, and transfered an album.  I ejected the iPod and the album was there.  Transfer successful.  

Second, I connected my iPod, opened Rhythmbox, transfered another album, ejected the iPod and both albums were there successfully.

I theorize that gtkpod was able to render the database correctly for use with linux, while Rhythmbox corrupted it.  Therefore, connect the iPod to gtkpod before connecting to any other media player.  I don't know if that's true, but I cannot explain what happened any other way.

Thanks to all, especially warfacegod and nothingspecial for their help and patience.

---

### Post by nothingspecial on 2010-01-17
Ok no problem. Leave it be.

Happy ipodding

---

### Post by warfacegod on 2010-01-17
Glad it worked out, somehow.

---

### Post by fj401971 on 2010-09-01
This is from bug #461639 in launchpad.  A problem with libgpod with it looking for an "oscar" character as opposed to a "zero".

An easier fix is described in the bug report.

[https://bugs.launchpad.net/ubuntu/+source/libgpod/+bug/461639]("https://bugs.launchpad.net/ubuntu/+source/libgpod/+bug/461639")

Quoted from Rock on reply #8

First ensure Rhythmbox is NOT running (killall rhythmbox will do the trick) and then:

# Get root privileges
```
sudo su
```
cd /usr/lib
# Convert libgpod.so.4.1.0 to hex and swap out "3RO" for "3R0", then convert back to binary. eg 33524f is "3RO" in hex
```
xxd -g8 libgpod.so.4.1.0 | sed s/33524f/335230/ | xxd -r > libgpod.so.4.1.0-fix
```
# Changeover the link to use the new binary
```
rm libgpod.so.4
ln -s libgpod.so.4.1.0-fix libgpod.so.4
```

I was able to stop here and reload the database on the ipod by letting it sync itself again.  Connecting to iTunes was unnecessary for me.

If you have problems:

Afterwards, run rhythmbox. If it worked, all should be fine. If something went wrong, it'll tell you that it can't activate the ipod plugin. You'll need to shut it down, run gconf-editor and search for /apps/rhythmbox/plugins/ipod and set active to true to get it to try next time. And, of course, restore the link to the old (broken) libgpod.so.4.1.0.

Note: This was on Ubuntu 9.10 with ipod 4g 8 GB black

---

