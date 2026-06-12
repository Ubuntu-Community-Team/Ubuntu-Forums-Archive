---
title: "Gimp plugins"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by Wolligog on 2011-04-04
I've been playing around with the gimp and i would like to install the dynamic text plugin but i'm not sure how to do it.  i was reading online and some suggest just downloading, unzipping and then moving stuff to the plug ins folder, only thing is i'm not sure what i should be moving.

i unzipped the folder and there were 3 more folders inside with various stuff in each, am i looking for a specific file or can i just move the whole folder(containing everything) into the plug ins folder?

the folder i have is called gdyntext-1.5.4, 

also is there an easy code i can use to install this and other gimp plugins, i'm pretty new to linux and i'm a bit daunted by the terminal as my spelling isn't the greatest.  but i will adding more plugins once i find them, it's just the actuall install is baffling me,

Is there a way to install without using the terminal and codes as tbh this is one part  of linux i'n not keen on,

As i'm still fairly new to linux, answers in plain simple english would be appreciated

thanks

---

### Post by Nickjpost on 2011-04-04
I found a guide to installing GIMP plugins in Ubuntu; what's awesome is that though some of it may require command line work, you might be able to just copy/paste the commands into the terminal to avoid typos. Good luck!

[http://en.wikibooks.org/wiki/GIMP/Installing_Plugins#Ubuntu_Linux](http://en.wikibooks.org/wiki/GIMP/Installing_Plugins#Ubuntu_Linux)

---

### Post by Wolligog on 2011-04-04
Thanks mate, i've had a read of that link but i'm still none the wiser.  the link says files will be .scm or .py  none of the files i have downloaded have that on the end, i have (.c)(.h) on the end of my files.  also that article doesn't really make it very clear what i'm supposed to be doing.  ive been looking through the gimp plug in registry but i cant find the dynamic text plugin there, any idea where i can find the correct one?

---

### Post by Wolligog on 2011-04-04
ok, i have a file titled README and it says   You must edit the Makefile and change GIMPBIN in order to reflect the path where the GIMP binary and gimptool are installed then you could run 'make install'.  so i need to know please, where are the gimptools and gimp binary files installed? and how do i run a 'make install' command?  this seems to be the only download available with all other sites i have just checked having exactly the same collection of files to download

---

### Post by Wolligog on 2011-04-04
i have found the script and installed it in the gimp scripts folder but i am now getting the following error message

Execution error for 'Dynamic Text':
Error: set!: unbound variable: image

what does this mean please? how do i deal with it?

thanks.

---

### Post by rosencrantz on 2011-04-04
It looks like your plugin is written in C and you downloaded the source code (thus the .c and .h files). Install the build-essential package, it includes the gcc compiler and the make utility. The usual compiling protocol for any C program would be
cd into unpacked tar folder.
Run './configure' if there's a 'configure' script.
Run 'make' to compile (this runs a script called Makefile which sets environemntal variables like GIMPBIN and invokes the gcc compiler).
Run 'make install' to install.
You can find the location of a binary with which, as in 
which gimp (usually /usr/bin/gimp)
You are right about the gimp scripts/plugins in your ~/.gimp folder, this only applies to Python and Scheme scripts. Compiled C plugins are usually copied automatically to their destination folders (which are usually not in ~/.gimp) when you run make install.
The problem with the dynamic text plugin is that the latest release  (1.5.4) seems to be from 2001. I doubt it works with gimp 2.6.

Cheers
rosencrantz

---

### Post by Wolligog on 2011-04-04
[LEFT]ok, ive installed the build essential package but i'm going to need some more help with this, i need to get it all straight in my head before i do this, i have no exp of programming etc so building stuff in C is totally new to me.

am i right in thinking i do the following, (i'm going to need this in steps)

i'm assuming i can only access the build essential through the terminal

run /usr/lib/gimp/2.6/plug-ins/gdyntext-1.5.4/configure.h

then i enter

make (do i need the filepath here?)

then i enter

makeinstall(do i need the filepath?)


and i have to open the makefile file and change the text where it says gimpbin to the location of gimptools or the gimp 2.6 in the usr/bin folder? 

is this right? i'd like to check before i do something and screw up my pc


thanks
[/LEFT]

---

### Post by Wolligog on 2011-04-05
sorry to bump this but i need to know if what i have written is correct, i dont want to try something without being sure and mess up my pc

thanks

---

### Post by Daniel0108 on 2011-04-05
> **Wolligog said:**
> sorry to bump this but i need to know if what i have written is correct, i dont want to try something without being sure and mess up my pc

thanks

I don't know if this works for gimp plugins but normally you have to type:
```
./configure
make
sudo make install
```
To compile and install a program,

Daniel

---

### Post by rosencrantz on 2011-04-05
Bumping is OK, as soon as something drops to the second page in the absolute beginners' forum, it's basically lost ;-)
First, how did you get the gdyntext-1.5.4 folder into /usr/lib/gimp/2.6/plug-ins/?
Did you copy it there? 
In general, you should not copy anything into /usr/lib, /usr/bin etc., as those folders are usually handled by automated installers.
In your case, the folder contains only the source code and not the compiled executable, and gimp needs the latter. In this respect, C plugins are different from the 'normal' .py and .scm plugins. Python and Scheme are scripted languages and can be executed without compilation.
To compile any C program:
extract (e.g. with [FONT="Courier New"]tar -zxf <theprogram>.tgz[/FONT]) the surces anywhere in your home/data directories. It doesn't matter where and you can delete tehm when you are finished.
cd into the extracted folder. Make sure there is a file called 'Makefile' (no extension). It's a script (text file) containing compilig instructions: without it, [FONT="Courier New"]make[/FONT] will not know what to do. The README file advises you to change the GIMPBIN variable. It's set to [FONT="Courier New"]/usr/bin[/FONT] by default, which should be fine (you can check this with [FONT="Courier New"]which gimp[/FONT]).
If there is another file called 'configure' (no extension), run [FONT="Courier New"]./configure[/FONT] This is a script checking dependencies. It makes compiling considerably easier, but is not mandatory.
Now you can run [FONT="Courier New"]make[/FONT]
It compiles the source files (.c and .h) according to the instructions in the Makefile, creating an executable.
If this runs through without errors, you can run [FONT="Courier New"]sudo make install[/FONT]
This takes care of copying the executable to where it's supposed to be and making sure Gimp finds it.

Having said all this, I'm not very hopeful this will work, it's just too old. No configure file, so no idea what the dependencies are. The 10-year-old README file mentions gimp 1.1, which is miles away from the recent gimp 2.6. Also, it requires a gimptools executable, which I could find  neither on my system, nor via apt-get or google. 
I installed the only gimp development package I could find ([FONT="Courier New"]aptitude search gimp[/FONT]), libgimp2.0-dev, but make complained about not finding gimptools and gtkx.h
gtkx.h is included in libgtk2.0-dev (another hidden dependency), so apparently there is something else wrong with the makefile.
I don't want to underestimate your faculties, but this is probably a bit much for a C beginner :-), and my C expertise stops at editing makefiles. Anyway, I need to attend a talk now. Maybe I'll find time later to look into this or somebody else has a brilliant idea.

---

### Post by Wolligog on 2011-04-05
thanks for the reply

i just moved the gdyntext folder into the gimp 2.6 folder, it wasn't actually copied, i take it i should remove it from there? i put the script file in the gimp scripts folder, should i put this back in the gdyntext folder?

assuming i move it back to the downloads folder where it originally was do i then 

open terminal
run/dowloads/gdyntext-1.5.4/configure

run/make(do i need a filepath here?)

if it's ok

sudo make install


also, might sound simple but where you have written 'cd into extracted folder'  does cd mean, copy data?

---

### Post by Daniel0108 on 2011-04-05
> **Wolligog said:**
> thanks for the reply

i just moved the gdyntext folder into the gimp 2.6 folder, it wasn't actually copied, i take it i should remove it from there? i put the script file in the gimp scripts folder, should i put this back in the gdyntext folder?

assuming i move it back to the downloads folder where it originally was do i then 

open terminal
run/dowloads/gdyntext-1.5.4/configure

run/make(do i need a filepath here?)

if it's ok

sudo make install


also, might sound simple but where you have written 'cd into extracted folder'  does cd mean, copy data?

cd means Change Directory.
For example, type:
```
cd run/Downloads/gdyntext-1.5.4/
```
after typing this, you don't have to specify a filepath, because you are IN this directory ;)

Yours,
Daniel

---

### Post by Wolligog on 2011-04-05
ok i just tried run/dowloads/gdyntext-1.5.4/configure  and got the following 

No command 'run' found, did you mean:
 Command 'crun' from package 'ceph' (universe)
 Command 'zrun' from package 'moreutils' (universe)
 Command 'runq' from package 'exim4-daemon-heavy' (main)
 Command 'runq' from package 'sendmail-bin' (universe)
 Command 'runq' from package 'exim4-daemon-light' (main)
 Command 'grun' from package 'grun' (universe)
 Command 'qrun' from package 'torque-client' (multiverse)
 Command 'qrun' from package 'torque-client-x11' (universe)
 Command 'lrun' from package 'lustre-utils' (universe)
 Command 'rn' from package 'trn' (multiverse)
 Command 'rn' from package 'trn4' (multiverse)
 Command 'rup' from package 'rstat-client' (universe)
 Command 'srun' from package 'slurm-llnl' (universe)
run: command not found

any ideas what this means please?

---

### Post by Daniel0108 on 2011-04-05
> **Wolligog said:**
> ok i just tried run/dowloads/gdyntext-1.5.4/configure  and got the following 

No command 'run' found, did you mean:
 Command 'crun' from package 'ceph' (universe)
 Command 'zrun' from package 'moreutils' (universe)
 Command 'runq' from package 'exim4-daemon-heavy' (main)
 Command 'runq' from package 'sendmail-bin' (universe)
 Command 'runq' from package 'exim4-daemon-light' (main)
 Command 'grun' from package 'grun' (universe)
 Command 'qrun' from package 'torque-client' (multiverse)
 Command 'qrun' from package 'torque-client-x11' (universe)
 Command 'lrun' from package 'lustre-utils' (universe)
 Command 'rn' from package 'trn' (multiverse)
 Command 'rn' from package 'trn4' (multiverse)
 Command 'rup' from package 'rstat-client' (universe)
 Command 'srun' from package 'slurm-llnl' (universe)
run: command not found

any ideas what this means please?

yes, you have to type ./run/...

Or you cd to the directory and then type ./configure

EDIT: Here's a tutorial about basic Linux/Unix commands: [http://newsourcemedia.com/blog/basic-terminal-commands/](http://newsourcemedia.com/blog/basic-terminal-commands/)

Yours,
Daniel

---

### Post by Wolligog on 2011-04-05
Doh!  cool thanks,

ok i have changed directory to Downloads/gdyntext-1.5.4   i typed in ./config.h  but it's says permission denied, any ideas how i sort this out?

thanks

---

### Post by Daniel0108 on 2011-04-05
> **Wolligog said:**
> Doh!  cool thanks,

ok i have changed directory to Downloads/gdyntext-1.5.4   i typed in ./config.h  but it's says permission denied, any ideas how i sort this out?

thanks

yes, type:
```
./configure
```

Yours,
Daniel

---

### Post by rosencrantz on 2011-04-05
Erm, don't type [FONT="Courier New"]./configure[/FONT]. The script is missing (see my last post). config.h is something different (a c header file).
Also, run is not meant as a command (I changed all commands to [FONT="Courier New"]Courier[/FONT]). Read that as type into terminal and press enter.
Also, you had better delete the files you moved to /usr/lib/.
Try
[FONT="Courier New"]sudo apt-get install libgimp2.0-dev libgtk2.0-dev 
make
sudo make install[/FONT]
The first line takes care of some missing dependencies. Run that only once.
I guess you will get errors at the second line (compilation), in which case the third line (installation) will not work either.
Try the first two anyway, it can't hurt.

---

### Post by Wolligog on 2011-04-05
[LEFT]ok i tried sudo apt-get install libgimp2.0-dev libgtk2.0-dev  and it started doing stuff but then when i typed in 'make it said

 No targets specified and no makefile found.    Stop. 

do i have to cd tothe gdyntext folder with that file in? thats where there's a file named ' makefile'  it has no.c or .h after it though, should i rename it or leave it.

there is a script file(.scm) in this folder but when i put it in the gimp script folder i couldn't use the dynamic text  function in gimp so at the moment it is back in the gdyntext folder
[/LEFT]

---

### Post by rosencrantz on 2011-04-05
Yes. cd into the gdyntext folder. Makefile shouldn't have an extension, so don't change it. Just run [FONT="Courier New"]make[/FONT].
Don't worry about the .scm file. I suppose it's going to be copied automatically to where it belongs when you run [FONT="Courier New"]make install[/FONT]
(The plugin is a hybrid: it has both a scripted and a compiled component)

---

### Post by Wolligog on 2011-04-06
ok i am in the gdyntext i entered  sudo apt-get install libgimp2.0-dev libgtk2.0-dev  which gave me

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-dev is already the newest version.
libgimp2.0-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 106 not upgraded.
 
(I wasn't in the gdyntext folder when i originally entered the command yesterday)

then i entered 'make' and got

make: /usr/bin/gimptool: Command not found
gcc -o .obj/charmap.o -Wall -Wstrict-prototypes -Wmissing-declarations -I. -DGTK_DISABLE_COMPAT_H  -g   -c charmap.c
In file included from charmap.c:23:
config.h:2: fatal error: gdk/gdkx.h: No such file or directory
compilation terminated.
make: *** [.obj/charmap.o] Error 1


am i doing something wrong?  do i have to type more than just 'make'?

someone else has suggested i could log in as root and change the file permissions using 

chmod 0777 filename 

would that make any difference?

---

### Post by rosencrantz on 2011-04-06
No, you got as far as I got. The compiler can't find gtkx.h, which is in /usr/include/gtk-2.0/gdk/. Changing permissions is not going to help there. We can probably modify the Makefile to help gcc find the file, but I'd have to do some research for that (as I said, not a Makefile expert).
Also, there is still the problem that newer versions of gimp don't include gimptool (remember, the plugin is for gimp 1.1 and you are running 2.6). I'm not sure whether there is a way around it without rewriting the plugin (agh!).

The 'newest version already installed' messages are OK. With apt-get it doesn't matter in which directory you are and as you already ran it yesterday, it just means that the packages are installed and you don't need to do it again.

---

### Post by Wolligog on 2011-04-06
[LEFT]i've been googling to see if i can find a gimp plugin developers forum or similar but i haven't had much luck so far, shame cos i really wanted to use this plug in, guess we'll have to hope someone re writes it or comes up with a way to get to it work, i shall keep trying though!
[/LEFT]

---

### Post by rosencrantz on 2011-04-06
I agree it looks a bit hopeless. Still, you almost compiled your first tarball ;-)
If you can't find an alternative plugin - there are a number of text-related gimp plugins - try contacting the developer, Marco Lamberto (user marcolamberto):
[http://sourceforge.net/project/memberlist.php?group_id=6295](http://sourceforge.net/project/memberlist.php?group_id=6295)
and ask wether he'd be interested in an upgrade.

---

### Post by Wolligog on 2011-04-06
ok someone just suggested trying

sudo apt-get build-dep gimp

and then running make again but i got the same error message as before

make: /usr/bin/gimptool: Command not found
gcc -o .obj/charmap.o -Wall -Wstrict-prototypes -Wmissing-declarations -I. -DGTK_DISABLE_COMPAT_H  -g   -c charmap.c
In file included from charmap.c:23:
config.h:2: fatal error: gdk/gdkx.h: No such file or directory
compilation terminated.
make: *** [.obj/charmap.o] Error 1


would it make any difference if alter the text in the makefile like it suggests in the readme file? it says

You must edit the Makefile and change GIMPBIN in order to reflect the path
where the GIMP binary and gimptool are installed then you could run
'make install'.

i think i might have to email the developer and see if he wants to update it

---

### Post by I2k4 on 2011-04-06
I've been following this discussion, as a fairly new user, hoping I would learn something to help me install one or two of these to GIMP:

[http://garmahis.com/reviews/gimp-plugins/](http://garmahis.com/reviews/gimp-plugins/)

How ridiculously crazy is all this?  I don't know whether trying to install a simple plug in is going to muck up my Lubuntu installations so badly I have to start from square one with a fresh install (which happened earlier in my short experience.)

I've had Photoshop Elements running in Windows XP for a couple of years now, and have never seen such utter confusion and nonsense attending installation of open source plug ins.  What are all the  developer-geniuses thinking when an ordinary human being at the ordinary user end of the software can't figure out how to do something so simple?

---

### Post by rosencrantz on 2011-04-06
@Wolligog: I don't think it would make a difference. On my system the gimp executable is already where the makefile assumes it to be. The problem is the missing [FONT="Courier New"]gimptools[/FONT], and that one doesn't exist at all. I suppose it was part of older Gimp versions. 
Yes, ask the develper whether he has any experience of the plugin working with recent Gimp versions.

@I2k4 a) Don't get frustrated!
b) You'd better start a new thread if you have a specific question. You'll get more attention if others don't have to read through 3 pages of failed C compilation.
c) Unfavourable comparisons to proprietary software are not conducive to getting help here, either ;-) The developers are all volunteers and doing the best they can.

Wolligog wants to run a *very* old plugin requiring additional compilation. The reason it doesn't work is that gimp has changed a lot in the last 10 years and the plugin hasn't been updated. If you tried to use some Photoshop 6 plugin with CS4 you might run into problems, too.
The plugins on the page you linked to are mostly recent Scheme scripts (hint: .scm extension) and should just work if you copy them to 
~/.gimp-2.6/scripts after extracting from tar.gz
Python scripts (.py) go into ~/.gimp-2.6/plug-ins
Copying something into a home subdirectory is easily reversible and can't screw up your system. Just try it. 
Come back if it doesn't work, we're here to help.

---

### Post by Wolligog on 2011-04-06
[LEFT]@rosencrantz,  just a thought but do you think i would have any success if i obtained a older version of gimp and copied the gimptools folder into gimp2.6?,   not really sure if i could actually get an old version but i shall have a hunt for one

@12k4,  the plugins are easy to install, like rosencrantz says, just move the .scm file into the script folder or the .py file into the plugins folder.  it's only the one plugin i'm having trouble with, ive added about 20 in the last 2 or 3 days with no problems.  
[/LEFT]

---

### Post by rosencrantz on 2011-04-06
@Wolligog: OK, you're into evil hack territory here. Try to get a .deb package for the Gimp 1.x series (like 1.2) - I couldn't find one with a quick google, though. Save it somewhere in your home/data dirs.
cd to the directory where the gimp-1.x-somethingorother.deb is
[FONT="Courier New"]mkdir oldgimp
dpkg-deb --extract oldgimp
cd oldgimp/usr/bin
sudo cp gimptools /usr/bin[/FONT]
I hope gimptools is in oldgimp/usr/bin, else you have to look through the oldgimp folder for it. We also need to figure out the missing gdkx.h file and I'm still not sure it's going to work after that. I'm old enough to have used Gimp/Linux in the early 2000's and a lot has changed.

---

### Post by Wolligog on 2011-04-06
[LEFT]well i've had a look but i cant find any old deb packages, the earliest i could see was about 2.2, not sure if that would be any help. if i was to actually do this though what are the chances of my gimp install getting screwed up?

I've sent a message to marco as well so shall have to see if he can offer any help, fingers crossed.
[/LEFT]

---

### Post by PhilGil on 2011-04-06
Old GIMP packages are available here (scroll to the bottom for the oldest ones): [http://snapshot.debian.org/package/gimp/](http://snapshot.debian.org/package/gimp/)

---

### Post by rosencrantz on 2011-04-06
Cool, thanks PhilGil!
Those must be older than Ubuntu itself ...
@Wolligog: 
I think copying gimptool to /usr/bin is harmless, as long as there is no newer version of it already there.
(check with [FONT="Courier New"]ls /usr/bin/gimp*[/FONT] ) Make sure you copy only gimptool and nothing else.
If this breaks anything, you can just delete it again with
[FONT="Courier New"]sudo rm /usr/bin/gimptool[/FONT]
Agh. I'm stupid. Don't copy gimptool! There's a gimp 2 version called gimptool-2.0
We'll fake gimptool by creating a symbolic link to gimptool-2.0 in /usr/bin. (also easily removable)
Run [FONT="Courier New"] sudo ln -s /usr/bin/gimptool-2.0 /usr/bin/gimptool[/FONT]
I used absolute paths (starting with /), so it doesn't matter which directory you are in.
Running make in the gdyntext directory now results in a lot of GTK errors, but the missing file references are gone. See the attachment.

---

### Post by rosencrantz on 2011-04-06
...and that's where the compatibility issues kick in.
The first error is 
charmap.c:58: error: &#8216;GtkArgSetFunc&#8217; undeclared
which results from the fact that in newer versions (>2.0) of the gtk libraries for C the 'GtkArg' family of functions has been replaced by GObject (quoting google here). 
I don't think you can revert to old gtklibs (or part of them) here,  it would mean downgrading your whole desktop.
Edit:
I got the GtkArgSetFunc error resolved for now, working on 
charmap.c:77: error: &#8216;GtkObjectClass&#8217; has no member named &#8216;type&#8217;

---

### Post by Wolligog on 2011-04-07
[LEFT]ok i have just downloaded gimp_1.0.2-3 and shall have a try with the commands you suggested, fingers crossed, i will post my results shortly.
[/LEFT]

---

### Post by rosencrantz on 2011-04-07
erm, you don't actually need the old version. The symlink to gimptools-2.0 should do it.
Sorry, I created a bit of confusion there.
I think you will get a lot of libGTK errors due to compatibility issues. 
You can compare your compiler output to the text file I attached to post # 31. 
GTK is the library that handles how windows and their content look and feel. Gimp1 was built on GTK 1.x, Gimp 2 and recent Ubuntu on GTK 2.x. I sorted out a few of the changes in the source code, but it's slow going and my preliminary patches will not get you much further.

---

### Post by Wolligog on 2011-04-07
ok, i hadn't had a chance to try but i just tried the symlink

 sudo ln -s /usr/bin/gimptool-2.0 /usr/bin/gimptool   

 gave me

ln: creating symbolic link `/usr/bin/gimptool': File exists

then i entered make and got

make: /usr/lib/gimp/2.6/plug-ins//gimptool: Command not found
gcc -o .obj/charmap.o -Wall -Wstrict-prototypes -Wmissing-declarations -I. -DGTK_DISABLE_COMPAT_H  -g   -c charmap.c
In file included from charmap.c:23:
config.h:2: fatal error: gdk/gdkx.h: No such file or directory
compilation terminated.
make: *** [.obj/charmap.o] Error 1

i must be doing something wrong because this totally different to your attachment, when i enter the make command, it is just 'make' isn't it?

---

### Post by rosencrantz on 2011-04-08
Somehow creating the symlink failed. Did you by any chance mix up target and link name?
It should be 
[FONT="Courier New"]sudo ln -s /usr/bin/gimptool-2.0 /usr/bin/gimptool[/FONT]
and not
[FONT="Courier New"]sudo ln -s /usr/bin/gimptool /usr/bin/gimptool-2.0[/FONT]
The other possibility would be that you already have a gimptool in /usr/bin, but you didn't copy the one from the old gimp package yet, right?
Post the output of
[FONT="Courier New"]ls -l /usr/bin/gim*[/FONT]
and we can figure out what's wrong.
Running [FONT="Courier New"]make[/FONT] was the right thing to do, but it still fails because of the missing gimptool.
Think of the compile as an obstacle course -  you'll only see the next problem (the GTK errors) after getting rid of the first one ;-)

---

### Post by Wolligog on 2011-04-08
sorry , was my fault, i never copied the one from the old package, i got confused where you said we didn't need the old gimp package so i never copied it. i shall try it shortly if i get a chance,  i'll post my results soon as

---

### Post by rosencrantz on 2011-04-08
> **Wolligog said:**
> sorry , was my fault, i never copied the one from the old package, i got confused where you said we didn't need the old gimp package so i never copied it. i shall try it shortly if i get a chance,  i'll post my results soon as

No, don't copy it the old one, you don't need it. If you had already done it, it would have explained why the symlink creation failed. 
Try to get the symlink to work.

---

### Post by Wolligog on 2011-04-09
[LEFT]ok, old gimp is still in my downloads folder and i haven't moved anything from it yet.

this is what i entered and the result

phil@JAHWEH:~$ sudo ln -s /usr/bin/gimptool-2.0 /usr/bin/gimptool
[sudo] password for phil: 
ln: creating symbolic link `/usr/bin/gimptool': File exists
phil@JAHWEH:~$ ls -l /usr/bin/gim*
lrwxrwxrwx 1 root root       8 2011-03-29 13:42 /usr/bin/gimp -> gimp-2.6
-rwxr-xr-x 1 root root 4243228 2010-11-12 15:12 /usr/bin/gimp-2.6
lrwxrwxrwx 1 root root      16 2011-03-29 13:42 /usr/bin/gimp-console -> gimp-console-2.6
-rwxr-xr-x 1 root root 2107332 2010-11-12 15:12 /usr/bin/gimp-console-2.6
lrwxrwxrwx 1 root root      21 2011-04-07 19:31 /usr/bin/gimptool -> /usr/bin/gimptool-2.0
-rwxr-xr-x 1 root root   13704 2010-11-12 15:12 /usr/bin/gimptool-2.0

some of these were coloured green in my terminal screen, does that have any significance?
[/LEFT]

---

### Post by rosencrantz on 2011-04-09
Some entries are executables, others are links, so they are coloured differently - see the arrows pointing to the link targets. 
You can't create the link, because it's already there and it's linking to gimptool-2.0, which is as it should be.
Does running make still get you no further than the missing gimptool message?

---

### Post by Wolligog on 2011-04-09
[LEFT]no, running make still gives me the missing gimptool message


make: /usr/lib/gimp/2.6/plug-ins//gimptool: Command not found
gcc -o .obj/charmap.o -Wall -Wstrict-prototypes -Wmissing-declarations -I. -DGTK_DISABLE_COMPAT_H  -g   -c charmap.c
In file included from charmap.c:23:
config.h:2: fatal error: gdk/gdkx.h: No such file or directory
compilation terminated.
make: *** [.obj/charmap.o] Error 1


[/LEFT]

---

### Post by rosencrantz on 2011-04-09
oh, wait...
should have read your error message more closely. 
is GIMPBIN in the Makefile set to /usr/bin? If not, change it that way.
The compiler didn't find gimptools, because it was looking for it in /usr/lib/gimp etc.

---

### Post by Wolligog on 2011-04-10
yeah, you were right it needed changing, i have set GIMPBIN in the makefile to /usr/bin, then i ran 'make and got

phil@JAHWEH:~/Downloads/gdyntext-1.5.4$ make
gcc -o .obj/charmap.o -Wall -Wstrict-prototypes -Wmissing-declarations -I. -DGTK_DISABLE_COMPAT_H  -g  -pthread -I/usr/include/gimp-2.0 -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -c charmap.c
In file included from /usr/include/gtk-2.0/gtk/gtk.h:235,
                 from charmap.c:26:
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:47: warning: function declaration isn&#8217;t a prototype
charmap.c: In function &#8216;charmap_get_type&#8217;:
charmap.c:58: error: &#8216;GtkArgSetFunc&#8217; undeclared (first use in this function)
charmap.c:58: error: (Each undeclared identifier is reported only once
charmap.c:58: error: for each function it appears in.)
charmap.c:59: error: &#8216;GtkArgGetFunc&#8217; undeclared (first use in this function)
charmap.c: In function &#8216;charmap_class_init&#8217;:
charmap.c:77: error: &#8216;GtkObjectClass&#8217; has no member named &#8216;type&#8217;
charmap.c:81: warning: implicit declaration of function &#8216;gtk_object_class_add_signals&#8217;
charmap.c: In function &#8216;on_charmap_char_toggled&#8217;:
charmap.c:149: error: &#8216;GtkButton&#8217; has no member named &#8216;child&#8217;
charmap.c: In function &#8216;charmap_set_font&#8217;:
charmap.c:165: error: &#8216;GtkStyle&#8217; has no member named &#8216;font&#8217;
charmap.c:166: error: &#8216;GtkStyle&#8217; has no member named &#8216;font&#8217;
charmap.c:167: error: &#8216;GtkStyle&#8217; has no member named &#8216;font&#8217;
charmap.c:170: error: &#8216;GtkButton&#8217; has no member named &#8216;child&#8217;
make: *** [.obj/charmap.o] Error 1


i have compared that to your compilation output and i as far as i can tell they are exactly the same

---

### Post by Wolligog on 2011-04-12
Bump!!,  sorry to bump this thread

---

### Post by rosencrantz on 2011-04-12
Yeah, sorry, I got stuck somewhere in the middle of C debugging.
The GTK1/2 transition is rather non-trivial, I'm afraid, and I haven't had a lot of time. 
Did you get any feedback from the developer?

---

### Post by Wolligog on 2011-04-12
ahh, ok sorry, didn't mean to rush you.   I haven't heard anything back from the developer yet

---

