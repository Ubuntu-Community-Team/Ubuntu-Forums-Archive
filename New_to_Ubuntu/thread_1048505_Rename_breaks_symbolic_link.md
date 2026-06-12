---
title: "Rename breaks symbolic link"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by gddeluca on 2009-01-23
OK, real noob here.

I use Moneydance (a java app).

In Nautilus I Shift-Ctl drag the moneydance.jar to the desktop to create a symbolic link.

The link is created and works perfectly.

However the text for the link says "Link to moneydance.jar" -- a bit wordy for the desktop, so I try to rename it. However, it insists that I leave the .jar extension on whatever I choose or it fails.

It's a LINK for crying out loud, why does IT need the extension, when the thing its pointing at has an extension?

Try explaining to your better half why the new, better operating system has to call it Moneydance.jar instead of her good old MoneyDance. Why clutter up her desktop with meaningless (to her) noise.
And I have to agree.

Am I missing something here?

George

---

### Post by kestrel1 on 2009-01-23
You could always create a launcher on the desktop. To do this right click on the desktop & select 'Create Launcher'
You can then name the launcher & browse to the program file.

---

### Post by gddeluca on 2009-01-24
Yes, I know that's SUPPOSED to work, but the link points at a JAR file (Java) and when created  by the 'Create a launcher' method  the link DOESN'T WORK!

Dragging (SHift-CTl) from Nautillus DOES work, but leaves me with the rename problem.

And yes, Using The SUN JAVA runtime IS the default for Java files.

I'm rapidly losing confidence in being able to move from windows to Ubuntu without ton's of annoyances.

[aside] I had to replace my keyboard, spilled a glass of wine into it and it never recovered. The new keyboard had a slightly shorter cablee, so I had to plug it into a hub rather that directly into the USB port on the back of the CPU, moving one of my other USB devices in the process. The 1st Ubunto b oot after this went nuts and never completed. Had to do recovery boot, then a normal boot, etc. and finally it came back.

VERY UNIMPRESSED

George

---

### Post by kestrel1 on 2009-01-25
Don't get disheartened, I will install MoneyDance & see if I can find a way around this problem.

---

### Post by kestrel1 on 2009-01-25
I just downloaded the tar.gz of moneydance & extracted the file. There is a file just called Moneydance in the folder that I used to run the program. I created a launcher & directed it to that file & it runs no problem & the name is just MoneyDance. There is even a PNG file to use for the desktop icon.

---

### Post by The Cog on 2009-01-25
Nice one, Kestrel1.

As for why the .jar extension is needed, this is a question of understanding how symlinks work. As far as applications are concerned, the name of the symlink **is** the name of the file. The fact that it links to another directory entry somewhere else is pretty-much irrelevant, and the name of the target file is irrelevant. *nix can often work out what to do with a file based on the file contents rather than the name, but in the case of jar files, they are in fact just zip archives full of class files. So if the name doesn't say it's a jar file, then it looks like a zip archive and will likeky be opened with whatever program is set up to open zip files.

You should have no problem getting a launcher to work. If the file Kestrel1 pointed out doesn't work for you for some reason, try launching it from a command prompt with something like
java -jar /home/kestrel1/moneydance/moneydance.jar
and once you have that command working, paste it into a launcher config.

And before sounding off so much, try dragging a .exe file to your desktop in windows and renaming it then running it. See how superior windows is then.

---

### Post by gddeluca on 2009-01-25
1st - to The Cog: I'm really not trying to be negative here, I WANT Ubuntu to do it for me, but ... its really pushing back.

As for Windows EXE on the desktop etc. sure, we're talking the REAL file then.  But WE're talking LINKS / Shortcuts / whatever.

Maybe a bit more background. I have Moneydance and all my data files for it stored in a directory on a thumbdrive so I can use it on my Desktop, my laptop, or my wife's laptop.   All of which works fine.

I now have an Ubuntu partition on my desktop which I hope will slowly displace and take over from Vista.

My Moneydance directory has no Moneydance file without an extension.  So I downloaded the Linux install and unzipped it. Its identical except for that one file which when browsed appears to be some ungodly script designed to find a usable JAVA version to run with.

When I double click on that file I get a pop-up asking me whether to Run In Terminal/Display/Cancel/Run.  I try Run - Nothing. I try Run in Terminal - a quick blink of a terminal window, but nothing! Double click the downloaded Moneydance.jar - Success, moneydance runs.

So I ignore the downloaded version and go back to my thumbdrive.  Here's a summary of what goes on.

** Double click on Moneydancejar in Nautilus - All OK

** Right-Click and choose Make Link - Failed - Operation not permitted. ?????

** Shift-Cntl Drag to the Desktop - Works, get Icon titled "Link to Moneydance.jar" and this works just fine, this is the one I've been trying to rename.

** Right-Click Desktop and create Launcher, name it and browse to the Moneydance.jar file.  Another failure - does nothing.

** Edit the above Launcher and add JAVA -JAR in front of the file address. Again - nothing happens visibly

** Open terminal and paste in the Launcher command and now we have something:
george@ubuntu-desktop:~$ java -jar /media/DELUCA1/Moneydance/moneydance.jar
Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at java.awt.Component.<clinit>(Component.java:568)
	at com.moneydance.apps.md.controller.Main.initializeApp(Main.java:278)
	at com.moneydance.apps.md.controller.Main.main(Main.java:189)
	at Moneydance.main(Moneydance.java:7)
george@ubuntu-desktop:~$ 
------------------------------------
So, WTF is going on, is my java install somehow not quite right? Should I re-install it?
=====================================
OK I'm back editing this on Vista 'cus Ubuntu has ^$%(*& me up for the second time today.
I mentioned I'd replaced my keyboard and had to move USB ports a bit. One device which WAS on a hub is now plugged right to the CPU box and the keyboard is now plugged into the extension hub.  As I said Ubuntu had REAL problems adapting to the change and it took a few re-boots before it settled down.

Then this morning, suddenly my USB drives (2 thumbdrives and one external hard drive, which were located and working after boot-up, just disappeared, and I could not mount or resurrect them other than by a full re-boot.   PITA
Then, while typing the 1st half of this note - the same thing, except now the USB keyboard also goes dead as well!

This is rapidly turning from a Ubuntu conversion into a total joke and waste of time if I can't even count on Ubuntu keeping access to all the devices on my system.

Has anyone seen this kind of stupidity?  Any ideas?

And yes, the hated Vista just keeps on going and going like the Energizer bunny.  Mo problems, no hiccups. Makes me wonder now why I wanted off it.

George

---

### Post by The Cog on 2009-01-25
I really don't know what your problem with the USB is I'm afraid. I've never seen problems like you describe.

I don't understand what's wrong with launching the jar file either. You should concentrate on getting it to launch from the command line, since then you get to see any error messages, and onceyou get it right you can either make a script or put the command straignt into a launcher.

Two things to try:

It may be that the directory you launch it from is important for some reason. So try things like 
[B]cd /media/DELUCA1/Moneydance/
java -jar moneydance.jar[/B]

Right-click the jar file and see what nautilus suggests to open it with, since whatever that is seems to work. Actually, on my system it wants to open it with Archive Manager.

---

### Post by kestrel1 on 2009-01-26
Why are you trying to run the jar file?
When I downloaded Moneydance, as I said there was a file called moneydance, that is the file to run.
What was the file that you downloaded located & called?
To your USB problem, could you not use a USB extension cable to attach your keyboard directly to your USB ports & not via the hub.
If it is not a powered hub, this could be some of the problem.
Not keen on hubs myself, had nothing but problems with them unless they are powered.

---

### Post by gddeluca on 2009-01-26
kestrel1: Why run the JAR file, well because nothing else works right now. The moneydance file (with no extension) when browsed appears to be a collection of routines designed to figure out what Java is installed so it can launch the real java code.  When I click on this - nothing appears to happen, no error messages, but no Moneydance execution either.

Re: the USB problems, I think you might be right although I'm not sure why this wouldn't also cause Vista problems (which if where I am right now) I'm sure I've got a USB extension somewhere, I'll try that and if I still have problems I'll try a powered hub, since the one I've got is unpowered and has 4 others plugged into it.

The Cog:  Yes, I'll try that to see what it takes command-wise to get it to run, but I'm pretty sure I've done this in the past and the normal JAVA -JAR xxxxx worked fine. But then maybe I'm remembering wrong, I've tried so many *^^((*& things.

Thanks both of you for your suggestions.

---

### Post by gddeluca on 2009-01-27
OK, the reason the plain Moneydance file doesn't work appears to be a Moneydance problem. I found something in their forums and it all comes down to the script being unable to properly find a Java runtime.  There is a commented out line in there where you can put in an explicit pointer. I did that and now DblClicking the Moneydance file properly works to start Moneydance. Other users over there are asking for a more standard install process, I can see why, it took me a lot of poking around to figure out where Java really was.

NOW

How the heck do I get the thing to just plain start without prompting me at to HOW I want to run it. (Run in Terminal / Display / Cancel/ Run) I gather Ubuntu doesn't care about file extensions.

Its a shell script, it has #! /bin/sh in the first line, what more does the system want?  

Is this yet another one of those > "Just edit the /blah/blah/file, locate line kjhkjkj=iytiuiu and alter it and TaDa, you're fine" type fixes?  If so then Linux is still way too geeky for people like me, and I've been in systems and programming for 30+ years. 

I've spent ages browsing forums for an answer, maybe it's there but I sure can't see it.

Right now this is looking pretty sad. I've spent DAYS now trying to get a simple app set up to run without being spoon-fed. At this rate I won't be converted off Vista before I'm dead.

---

### Post by gddeluca on 2009-01-27
Deleted - Double post

---

### Post by gddeluca on 2009-01-27
Gee, a nice simple solution.

The action of a link on my Desktop is somehow controlled by the Preferences of the File Browser (Nautilus).

Now that's something which should be intuitively obvious to even a noob like me.

Try searching Help with "Default Open Action" and get as frustrated as I was.

It's a very steep learning curve.

---

### Post by amoun on 2009-05-23
Just an idea.

I had a similar problem launching apache. The link was greyed out as I was not the root user when logged in. So I could run via a terminal but not by the launcher until I used gksudo in the command line which brought up a window for root password.

---

