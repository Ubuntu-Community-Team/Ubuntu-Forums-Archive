---
title: "Questions about Scala, Timidity, etc...First time Ubuntu user"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by boulezfan317 on 2011-04-20
I am not sure if anyone can help me with this, but I am completely ignorant about linux, and I happen to have a laptop with Ubuntu on it that I've been borrowing from someone 'cause my windows computer fried. I haven't used it for much more than email and stuff, mostly cause I'm too ignorant to get much out of it. I have run a program called Scala (which can create and play non-traditional microtonal scales and re-tune MIDI files among other things) on my windows computer with modest success, but I was reading about it and realized that it might work much better on Linux. I have had a hell of a time trying to figure out how to install this thing! There are all of these packages that are recommended for one to install before trying to run scala, and when I look in the Software Center it looks like I have all of them. 

The program can be downloaded from their website (below) as a tar.gz file. I read the INSTALL file in the subdirectory that's created when I download and extract the tar.gz. but it is fundamentally incomprehensible to me. So my first question is: Can anyone help me install or extract, or whatever, a tar.gz file? I can find an icon in the subdirectory that says scala, but nothing happens when I click on it! 
and my second question is: How come when I download software in the Software Center, sometimes an icon just magically shows up in the applications menu, and other times this does not happen? (I guess a corollary question is how do I know what subdirectory these files are being saved in when I download them through the software center?? ) 
I'm also trying to install timidity, which is a software synth/midi player and not having much luck with that either! 
I know this post belies a profound ignorance, but I am a musician by training, not a software developer. any help is greatly appreciated. 

oh yeah, and how can I find out whether I'm running a 32 or 64 bit version? 

By the way, the scala page is at [http://www.huygens-fokker.org/scala/](http://www.huygens-fokker.org/scala/)

Thanks!!

---

### Post by rosencrantz on 2011-04-20
It's cool to see a musician among all the computer scientists!
If you're into sheet music typesetting or audio editing, I can recommend lilypond/frescobaldi and audacity, btw...

I'll give you terminal instructions, because I'm on KDE
(Accessories->Terminal). For a quick introduction on how to navigate the Ubuntu terminal, try this thread.
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)
64 or 32 bit: typing [FONT="Courier New"]uname -a[/FONT]  should give you a clue. If there's anything like i386, i686 and no 64 near the end of the output, it's 32 bit.
To install timidity and scala:
First, you have to install scala's dependencies:
[FONT="Courier New"]sudo apt-get install libgnat-4.4 timidity gnuplot libgtkada2.14.2[/FONT]
(You said it's not your laptop. I hope you have sudo (administrative) permissions, else it's not going to work).
You did already unpack the tar.bz2 file, didn't you? (it's just a file compression format like zip) If not, try 
[FONT="Courier New"]tar -jxf scala-22-pc-linux.tar.bz2 [/FONT]
(The tar.bz2 file is the one I downloaded. You mentioned tar.gz, in that case the syntax is [FONT="Courier New"]tar -**z**xf somefile.tar.gz[/FONT]) You mentioned the INSTALL file, so I assume it's unpacked.
The INSTALL file doesn't help a lot, by the way, as the instructions are dated or wrong, so don't copy the gtkada.so file and don't worry about library paths.
I got scala to run by navigating into the scala directory and typing [FONT="Courier New"]./scala[/FONT]

On your question regarding program icons not showing up:
Usually, applications only get a menu entry when they have a graphical user interface (GUI). If they are text-based and only run in the terminal (e.g. timidity), they will not show up.
You can find out where it's installed with the which command
(e.g. [FONT="Courier New"]which timidity[/FONT]). However, you'll not need the actual location to execute it, because it's in a special folder (most likely /usr/bin) that Ubuntu searches every time you run a terminal command.
So, [FONT="Courier New"]timidity op18nr4.midi[/FONT] will work, no matter in which directory you and the midi file are.
This doesn't apply to scala, as it isn't installed properly into /usr/bin, so we have to be in the same folder as the scala executable and run it with [FONT="Courier New"]./scala[/FONT].

Another thing: If you insist on having a GUI for timidity, try [FONT="Courier New"]timidity -ia[/FONT]. It's not very pretty, though.

Cheers,
rosencrantz

---

### Post by boulezfan317 on 2011-04-20
Wow thanks for the detailed reply! I got the dependencies and I unpacked it, yes.  I will try running the programs from the terminal window. I read on the website that scala versions 2.0 and higher had a graphic interface. I guess I will have to figure out all the text commands for the stuff I was doing intuitively in windows... linux is really a different animal!

---

### Post by rosencrantz on 2011-04-20
Well, for the popular stuff like office applications, web browser etc. Linux works a lot like Windows.
It's only the 'special' software that usually doesn't show up in the startup menu. You can add entries by hand, of course, but in my opinion the easiest way to find your way around a Linux install is a quickstarter like Krunner or, in your case, gnome-do.
[http://linux.digitalsp.com/2009/07/kde4-alt-f2-equivalent-for-gnome.html](http://linux.digitalsp.com/2009/07/kde4-alt-f2-equivalent-for-gnome.html)
In case of scala, you have to put a link to scala in /usr/bin (the common applications folder) first to make linux find it.
[FONT="Courier New"]cd /usr/bin
sudo ln -s /<pathtoscaladirectory>/scala[/FONT]
(Replace the term in brackets with something appropriate)

---

