---
title: "how to install Vulture's Eye for a complete beginner"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by Amanda HazLaPaz on 2009-03-10
I already know that this thread exists.[http://www.ubuntugeek.com/how-to-install-vultures-isometric-graphics-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-vultures-isometric-graphics-in-ubuntu.html)
I am having trouble with the instructions.

I'm stumped by various messages at different times. Fakeroot? su- ? Run message in /usr/local/? I'm asking for hand-holding guidance if you can tolerate assuming that I know *nothing*. I have done things successfully with the terminal before (sudo apt-get install), but I don't know how to switch directories. I don't know the difference between a tr.gz and a .bz and a zip. I vaguely understand how to unpack an archive (package?) but I don't know where to put stuff.

I'd really like to play specifically Vulture's Eye (or Claw), not the text version.

-----------------------------------------------
Ubuntu Geek says:
==Preparing your system
==First you need to install the following dependencies

==sudo apt-get install byacc flex libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev

[IMG]http://farm4.static.flickr.com/3560/3344649354_062497aa16.jpg?v=0[/IMG]

==Now you need to download the latest version of Vulture’s from here using the following command in /usr/local/
==wget [http://www.darkarts.co.za/projects/vultures/attachment/wiki/downloads/2.1.0/vultures-2.1.0-full_unix-1.bin.sh](http://www.darkarts.co.za/projects/vultures/attachment/wiki/downloads/2.1.0/vultures-2.1.0-full_unix-1.bin.sh)

*Confusing to me. I don't understand. See output in attached image, according to what I vaguely understood of instruction.*

[IMG]http://farm4.static.flickr.com/3615/3344649358_55764a2819.jpg?v=0[/IMG]
==Now you need to make the script executable using the following command

==chmod +x vultures-2.1.0-full_unix-1.bin.sh

==Now you need to execute the script using the following command

==./vultures-2.1.0-full_unix-1.bin.sh

==A few compilation warnings later, the game is installed in the vulture directory in your home’s. You can play either Vulture’s Eye or Claw.
----------------------------------------------


So I'm stuck. I think I have all the correct dependencies.... or do I? What would I need to do to switch to /us/local/ to input the command in the right format?

My signature has relevant information about type of system and release version.

---

### Post by bwang on 2009-03-10
Post the output of:
```
ls
```
from the terminal.

I think the game is installed in the vulture folder in your home directory:

```

cd vulture
ls

```

---

### Post by Amanda HazLaPaz on 2009-03-10
The results of both are included.

*Thank you* for your help.

---

### Post by yeats on 2009-03-10
Looks like your wget command pulled the html web page, not the program you were going for ....

Looks like what you've downloaded are the files called "dashboard."  I see from your wget output that it resolved through several URLs before downloading this.  I would try to get an actual URL for the file you know you're looking for and wget it directly...

---

### Post by Amanda HazLaPaz on 2009-03-10
I found some sites in my travels. I also included a shot of my own desktop with a couple of packages (and extracted files?).

Completely at a loss as to which package will work, and what to do to get the correct one to work.

Again, *thanks* for helping.

I keep trying to remind myself that this is a project that will ultimately lead me to understand my computer better, but the frustration I feel is enormous.

---

### Post by yeats on 2009-03-11
> I found some sites in my travels. I also included a shot of my own desktop with a couple of packages (and extracted files?).

Completely at a loss as to which package will work, and what to do to get the correct one to work.

Installing from source requires basic knowledge of the command line/shell/terminal/bash (whatever you want to call it).  If you don't know the basic commands to move around, you might want to halt this project temporarily until you get some skills under your belt (IMHO :-) ).  But I'll help you as I can...

Okay - to return to your original post, the instructions from the Ubuntu-Geek site are pointing to a file that is no longer at that site, which is why the wget command is not working the way you (and the instructions) intend.  [wget is a utility that downloads a file from the Internet (you can think "web-get" if that helps you remember).]

If I were you, I would start over.  Delete all the files you've downloaded for this and start with a clean slate.  Now, return to the Ubuntu Geek site and instead of the wget command that failed, substitute this:

```
wget http://downloads.usrsrc.org/vultures/2.1.2/vultures-2.1.2-full_unix-1.bin.sh
```

Then follow the rest of the instructions on the site.  If *that* doesn't work, post back and perhaps someone can walk you through.



> 
Again, *thanks* for helping.

I keep trying to remind myself that this is a project that will ultimately lead me to understand my computer better, but the frustration I feel is enormous.

Happy to help.  There's a lot to learn.  My advice is to start using the command line for basic functions - moving around, etc.  This is a good start:
[URL="http://www.tuxfiles.org/linuxhelp/linuxfiles.html"]
http://www.tuxfiles.org/linuxhelp/linuxfiles.html[/URL]

---

### Post by Amanda HazLaPaz on 2009-03-11
MANY thanks, Chris. As soon as I'm done with work for the day and I get home, I will indeed try as you suggested.

I very much appreciate your help.

---

### Post by Amanda HazLaPaz on 2009-03-11
Okay, there is movement forward. The wget command seemed to do something, and the download took much longer.

I made some errors in the chmod command, I forgot that instead of vultures-2.1.0 it should have been vultures-2.1.2. That tripped me up twice, but I realized it and fixed the error.

The directory was indeed there, but it was empty.

---

### Post by Phatbman on 2010-01-18
Hello this is relevant to my interest as when I input this [code]
wget http://downloads.usrsrc.org/vultures/2.1.2/vultures-2.1.2-full_unix-1.bin.sh
The only output I get is

andy@ubuntu:/usr/local$ wget http://www.darkarts.co.za/projects/vultures/attachment/wiki/downloads/2.1.0/vultures-2.1.0-full_unix-1.bin.sh
--2010-01-18 12:30:24--  http://www.darkarts.co.za/projects/vultures/attachment/wiki/downloads/2.1.0/vultures-2.1.0-full_unix-1.bin.sh
Resolving www.darkarts.co.za... 209.20.76.105
Connecting to www.darkarts.co.za|209.20.76.105|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-01-18 12:30:24 ERROR 404: Not Found.


is there a working link out there? I dont mean to necrothread but...

---

### Post by Tarmatt on 2010-02-02
I'm looking for it too. 
It looks like vulture's eye completly disepeared from the net... Nothing in the karmic repositories, nothing on the official website, no sources nowhere...
If someone got a clue...

---

### Post by takeiteasy on 2010-02-02
You can still get Vulture's Eye and Claw from [http://github.com/clivecrous/vultures]("http://github.com/clivecrous/vultures")

Cheers,

---

### Post by Kidaf on 2010-02-08
I am also on this crusade to install Vultures on my Ubuntu, for more than 2 weeks.

All I can find are instructions considering the existence of a .sh file. And the only place I can find where there would be such file is the - now 404 - [www.darkarts.co.za](www.darkarts.co.za).

On the link given above, there is no linux or unix installer. Only win, macOS or the source to compile!

Is there any other way to avoid compiling? Or does anyone has a mirror for that .sh?

Thanks!

---

### Post by Amanda HazLaPaz on 2010-02-17
I started using WINE to run an MS Windows download of Vulture's Claw as I was having no luck figuring out how to run it natively. It has been working fine for me. That might be the best option for the sake of expediency.

1. GO TO:
[http://github.com/clivecrous/vultures/downloads](http://github.com/clivecrous/vultures/downloads)

2. Pick one of these two options. Extract to desired folder.
vultures-2.1.2-eye_win32-1.exe (this is the basic package, if I understand correctly))

vultures-2.1.2-claw_win32-1.exe (as I understand it, this one has the value-added magic stuff)

3. Install WINE.

4. Right-click-->open with WINE

5. Enjoy!

---

### Post by Tharquil on 2010-04-06
This procedure has been tested on Ubuntu 9.10 Karmic Koala.

Download the latest source code from:
[http://github.com/clivecrous/vultures/downloads](http://github.com/clivecrous/vultures/downloads)

Get the current version of the source with this line:
```
wget http://github.com/downloads/clivecrous/vultures/vultures-2.2.100-full.7z
```

You will need these two apps installed:
```
sudo apt-get install p7zip dpkg-buildpackage
```

On my system I had to install these apps to respect the dependecies:
```
sudo apt-get install debhelper libsdl1.2-dev libncurses5-dev bison flex libpng12-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev
```

Decompress the source code:
```
p7zip -d vultures-2.2.100-full.7z
```

Go to the source code directory:
```
cd vultures-2.2.100/
```

Apply the debian patch:
```
patch -Np1 -i dist/linux/debian/debian.patch
```

Build the deb packages:
```
sudo dpkg-buildpackage
```

Three deb packages have been built and the source compressed in the parent directory of the source:
vulturesclaw_2.1.90-1_amd64.deb
vultures-data_2.1.90-1_all.deb
vultureseye_2.1.90-1_amd64.deb
vultures_2.1.90-1.tar.gz

Go to the parent directory of the source:
```
cd ../
```

Install Vulture's Eye:
```
sudo gdebi vultures-data_2.1.90-1_all.deb
sudo gdebi vultureseye_2.1.90-1_amd64.deb
```

You should be able to access Vulture's Eye from the Applications menu:
Applications > Games > Vulture's Eye

Happy Ascending!

Note: The package for Vulture's Claw can also be installed in the same manner but it will not run on my system. I have not looked into it since I am a Vulture's Eye player ;)

---

### Post by buntubunny on 2010-04-17
Thank you Tharquil for the comprehensive help. I managed to get Vulture's Claw working by following Tharquil's instructions, up until the last step.

I am using Ubuntu 9.10 on a Dell Inspiron 600m. This uses an Intel chip instead of an AMD chip, so I installed the file vulturesclaw_2.1.90-1_i386.deb using
```
sudo gdebi vultures-data_2.1.90-1_all.deb
sudo gdebi vulturesclaw_2.1.90-1_i386.deb
```

After installing, you will find a folder in your home directory called ~/.vultures/

To run Vulture's Claw, type (note the dot after -d):
```
vulturesclaw -d .
```

This works for me, but I'm not sure why. Maybe someone can tell me?

---

### Post by LloydM999 on 2010-05-06
apt-get didn't recognize dpkg-buildpackage, I has to install **dpkg-dev** to get the command.

update:
Everything built OK in Lucid Lynx. The execs were in /usr/games, I didn't get a .vultures directory. They were also in Applications > Games so I didn't need to run them from the command line.

---

### Post by mbaucco on 2010-06-08
Is there any way to install this on a netbook running an Atom processor?

Thanks,
Matt

edit: never mind, the i386 instructions appear to work just fine. Thanks! :)

---

### Post by Grek336 on 2010-06-27
I have use the instructions from Tharquil but it not works for me (Ubuntu 8.04.4 LTS)

```
sudo dpkg-buildpackage
``` make an error like

```

test@test-desktop:~/Desktop/vultures-2.2.100$ LANGUAGE=C sudo dpkg-buildpackage
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package vultures
dpkg-buildpackage: source version 2.1.90-1
dpkg-buildpackage: source changed by Daniel Thaler <daniel@dthaler.de>
dpkg-buildpackage: host architecture i386
 debian/rules clean
Can't exec "debian/rules": Permission denied at /usr/bin/dpkg-buildpackage line 477.
dpkg-buildpackage: failure: debian/rules clean failed with unknown exit code -1
test@test-desktop:~/Desktop/vultures-2.2.100$ 

```

I don't now why. Have anyone an idea?

Sorry! I have found the failure. dabian/rules have no executable attribute.

---

### Post by Amanda HazLaPaz on 2010-06-28
I followed Tharquil's amazing instructions and buntubunny's helpful i386 variation after my fresh install of Lucid and, got a Vultures folder in Home directory and a listing in Applications-->Games!

---

