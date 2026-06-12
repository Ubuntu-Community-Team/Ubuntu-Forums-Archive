---
title: "ctrl+alt+del equivalent?"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by DaGeek247 on 2010-08-16
I have Ubuntu 10.04, and i am wondering, what is the ctrl+alt+del equivalant for Ubuntu? I have been plagued with a [screen error]("http://ubuntuforums.org/showthread.php?t=1511167") ever since I installed Ubuntu, and was hoping thast the ctrl+alt+del equivalent might help.


______________________________________________________________________

For the average Ubuntu user, these two things should satisfy your need:
To end a frozen program:
> 
press alt+f2
type in xkill
click on the app you want to close.
(thanks [carlee]("http://ubuntuforums.org/member.php?u=717412")!)

To view the processes and the CPU statistics go to:
System>Administration>System Monitor

or for a more advanced display of the processes:
```

sudo apt-get htop

```
then simply type <htop> in the terminal, and you have it.

for a desktop reset (logs out really quickly, and kill everything) ctrl+alt+backspace is for older machines. or for newerversions of Ubuntu (not sure whet version, no one ever told me):
```

<left arrow key>+alt+<print screen key>+k

```
will reset the desktop completely.

---

### Post by ubudog on 2010-08-16
There is CTRL>ALT>BACKSPACE.  It restarts the X server.  To enable it, go to System>Preferences>Keyboard>Layouts>Options and check the "Restart the X server" option.

---

### Post by DaGeek247 on 2010-08-16
Thanks for the help. I will definitely try it out, and reply with the results.

---

### Post by ubudog on 2010-08-16
It is a very good tool to have enabled.

---

### Post by PSioNiC STRaNGLeR on 2010-08-16
i think i'll take that advice as well-cheers-

---

### Post by DaGeek247 on 2010-08-18
nope, the ctrl-alt-backspace did not work. any other suggestions?

---

### Post by sandyd on 2010-08-18
> **DaGeek247 said:**
> nope, the ctrl-alt-backspace did not work. any other suggestions?
press alt+f2
type in xkill
click on the app you want to close.

---

### Post by DaGeek247 on 2010-08-18
Actually, I learned about that in some other thread. (I don't know) and I have tested it, but it did not work. Thank you for the advice though.

Yes this and >System>Administration>System Monitor should satisfy most Windows to Ubuntu users, because it gives the ability to see what is happening with the computer processor and the ability to kill any frozen application (In my limited experience, a very rare occasion with Ubuntu) so I will put it in the first post.

---

### Post by Zorgoth on 2010-08-18
What sort of a screen error?

---

### Post by sandyd on 2010-08-18
> **DaGeek247 said:**
> Actually, I learned about that in some other thread. (I don't know) and I have tested it, but it did not work. Thank you for the advice though.

Yes this and >System>Administration>System Monitor should satisfy most Windows to Ubuntu users, because it gives the ability to see what is happening with the computer processor and the ability to kill any frozen application (In my limited experience, a very rare occasion with Ubuntu) so I will put it in the first post.
try htop.
sudo htop if needed

---

### Post by dfreer on 2010-08-18
+1 for htop. Also, you can configure gnome to respond to a Ctrl-Alt-Del keypress to launch either gnome-system-monitor or htop. It's fairly easy to do using the configuration editor.

This guide shows another way to do it, haven't tried it myself: [http://www.howtogeek.com/howto/20355/use-ctrlaltdel-for-task-manager-in-linux-to-kill-tasks-easily/](http://www.howtogeek.com/howto/20355/use-ctrlaltdel-for-task-manager-in-linux-to-kill-tasks-easily/)

---

### Post by DaGeek247 on 2010-08-18
> **carlee said:**
> try htop.
sudo htop if needed

Apt-getting!

> **Zorgoth said:**
> What sort of a screen error?

lol, I posted the error in [this]("http://ubuntuforums.org/showthread.php?t=1554380") post, but i will restate it here for you.

Every time I open up something that (i don't know how to state it, so I will put in some programs that cause it)

Platinumarts Sandbox 3D Game maker
Battledawn.com
the screen saver options.
wings 3d polygon mesh modeler
transmission bittorrent client (this was really annoying when it happened.
and probably many others that i have not opened.

when the error starts, it seems like the screen res is changing. then it shows some text (windows boot text style) then it sounds like the screen res is chaning again. It shows some vertical white bars, the screen res changes, then it repeats.

---

### Post by oldsoundguy on 2010-08-18
Gnome users can put an applet in the panel. It is called "force quit".  Works great!

---

### Post by DaGeek247 on 2010-08-18
> **dfreer said:**
> This guide shows another way to do it, haven't tried it myself: [http://www.howtogeek.com/howto/20355/use-ctrlaltdel-for-task-manager-in-linux-to-kill-tasks-easily/](http://www.howtogeek.com/howto/20355/use-ctrlaltdel-for-task-manager-in-linux-to-kill-tasks-easily/)

How would I set up htop to open up when I press ctrl+alt+delete?


So, hear is what I have so far:

alt+F2 and typing xkill in the following box kills a graphical problem. It doesn't work for me because I can't open anything graphical.

control+alt+backspace (when set up) resets the desktop (logs out really quickly)

System>Administration>System Moniter shows running processes, and can end them. (not for me either)

htop: ??? I have not tried that yet because I want to know how to set it up for Control+Alt+Delete

---

### Post by ubudog on 2010-08-18
+1 for htop also, great for servers also.

---

### Post by DaGeek247 on 2010-08-18
Oh, so htop is like a command line type system monitor?

---

### Post by ubudog on 2010-08-18
> **DaGeek247 said:**
> Oh, so htop is like a command line type system monitor?

Yes.

---

### Post by oldsoundguy on 2010-08-19
If you insist on using keys for a kill process, ctrl>alt>backspace has been replaced in the newer builds with:
(Right key)alt/printscreen/k

But. If you are looking for the INFO screens (processes, etc), htop IS the answer.

---

### Post by TNT1 on 2010-08-19
Yeah, yeah, yeah, what happened to the ctrl/alt/delete, or whatever, that turned the cursor into a wee skull, and you could kill any window you liked with it? I want that back.

---

### Post by Captain_Falafel on 2010-08-19
> **carlee said:**
> try htop.
sudo htop if needed

+1 for htop! :)
For those looking for a keyboard shortcut to the System Monitor, you can easily create one by going into System > Preferences > Keyboard Shortcuts and Add a new one. The command is ```
gnome-system-monitor
``` Name it what you will and I usually prefer Ctrl + Shift + Esc for my command :popcorn:

Edit: darn, I didn't notice the 2nd page, you guys beat me to it ;)

---

### Post by DarrenMR415 on 2010-08-19
> **oldsoundguy said:**
> Gnome users can put an applet in the panel. It is called "force quit".  Works great!

I was coming here to say this.  So QFT.

---

### Post by DaGeek247 on 2010-08-19
@TNT1
alt+F2 then typing in xkill in the following box should do it.\

@oldsoundguy
It works, but it completely takes away the point. Suppose the screen error comeup when I am typing something really important, and I had no time to save it? your solution would do the same as pressing the power button ctrl+alt+backspace. It would remove the data.

---

### Post by DaGeek247 on 2010-08-19
> **DarrenMR415 said:**
> I was coming here to say this.  So QFT.

QFT? Whats that supposed to mean? and how would I do it?

---

### Post by TNT1 on 2010-08-19
> **DaGeek247 said:**
> @TNT1
alt+F2 then typing in xkill in the following box should do it.\

.

Ta.

---

### Post by bkratz on 2010-08-19
> **DaGeek247 said:**
> QFT? Whats that supposed to mean? and how would I do it?

From the urban dictionary

QFT	
Quoted For Truth. Generaly used on internet forumafter quoting someone to make sure they cannot go back and change what they've already posted. Sometimes used to express you agree with the opinion. "QFT, brutha.

---

### Post by DaGeek247 on 2010-08-19
> **bkratz said:**
> From the urban dictionary

QFT    
Quoted For Truth. Generaly used on internet forumafter quoting someone to make sure they cannot go back and change what they've already posted. Sometimes used to express you agree with the opinion. "QFT, brutha.

lol, oops.

---

### Post by oldsoundguy on 2010-08-19
The same things occurs in Windows with ctrl/alt/del as that ENDS what you are currently involved in doing, so there is no "saving" there also.

IF you are having issues when typing documents, then you are, most likely, hitting the wrong key combinations or you have HARDWARE issues.

The FORCE QUIT app/applet allows you to select the PROGRAM that is giving you trouble and to leave the others ALONE.

---

### Post by KdotJ on 2010-08-19
> **TNT1 said:**
> Yeah, yeah, yeah, what happened to the ctrl/alt/delete, or whatever, that turned the cursor into a wee skull, and you could kill any window you liked with it? I want that back.

+1 for the skull!
My fedora 12 install still does that lol, with the alt+F2 and typing xkill command

---

### Post by mcduck on 2010-08-19
> **KdotJ said:**
> +1 for the skull!
My fedora 12 install still does that lol, with the alt+F2 and typing xkill command

So does  Ubuntu, and in exactly the same way. If you don't get the cool skull icon then just change your cursor theme to one that has it.

What comes to enabling the Ctrl-Alt-Backspace for zapping the X server, you don't really even need to enable it. SysRq-k does the same, works by default, and also works for TTY's unlike the Ctrl-Alt-Backspace method. ;)

---

### Post by DaGeek247 on 2010-08-19
> **oldsoundguy said:**
> The same things occurs in Windows with ctrl/alt/del as that ENDS what you are currently involved in doing, so there is no "saving" there also.

IF you are having issues when typing documents, then you are, most likely, hitting the wrong key combinations or you have HARDWARE issues.

The FORCE QUIT app/applet allows you to select the PROGRAM that is giving you trouble and to leave the others ALONE.

Except, that in windows it does not end everything, just a program you select and only you select. I am not trying to sound winey (but i probably am, so plaese don't quit on me), but, I guess what I am looking for is a program that can kill processes/programs, and be the first on the job for the processor. You press key combination, and window pops up, with the ability to kill anything instantly, and the program is on the top of the "todo list" for the CPU.

It might be that Windows has had to learn how to do stuff like this, and be really good at it because it has so many problems. :lolflag:

---

### Post by mcduck on 2010-08-19
> **DaGeek247 said:**
> Except, that in windows it does not end everything, just a program you select and only you select. I am not trying to sound winey (but i probably am, so plaese don't quit on me), but, I guess what I am looking for is a program that can kill processes/programs, and be the first on the job for the processor. You press key combination, and window pops up, with the ability to kill anything instantly, and the program is on the top of the "todo list" for the CPU.

It might be that Windows has had to learn how to do stuff like this, and be really good at it because it has so many problems. :lolflag:

Then what's wrong with using the System Monitor? It does exactly what you are asking for, and you can even bind it to any keyboard shortcut you want, as described a few posts ago here: [http://ubuntuforums.org/showpost.php?p=9739465&postcount=20]("http://ubuntuforums.org/showpost.php?p=9739465&postcount=20")

---

### Post by DaGeek247 on 2010-08-19
Yes, but I am trying to find something that fixes my error, not exactly an equivalent.

---

### Post by mcduck on 2010-08-19
> **DaGeek247 said:**
> Yes, but I am trying to find something that fixes my error, not exactly an equivalent.

Well, you aren't going to get exactly the same dialog as you get in Windows, no matter what you do, so using the closest equivalent (which does exactly the same thing) is your only option.

I can't really see what's wrong with that approach. It gives you everything you have asked for in this thread.

What comes to your screensaver problem in the other thread, my only suggestion, apart from installing a working driver for your graphics card if there's one available, is to just disable the screensaver. It's been like 20 years since those things actually saved the screens (unless you have old plasma display), these days they really have no function other than displaying pretty images when nobody is there watching, and basically do the very opposite of saving anything. Just set the screen to blank when idle if you want to save your screen or electricity.

---

### Post by DaGeek247 on 2010-08-19
Yes This post has been answered, and I should mark it as solved, but it does not fix my problem. Could you tell me how to install the driver properly, maybe even find one?

---

### Post by mcduck on 2010-08-19
> **DaGeek247 said:**
> Yes This post has been answered, and I should mark it as solved, but it does not fix my problem. Could you tell me how to install the driver properly, maybe even find one?

ok. 

I checked your hardware info from the other thread, and you seem to have Intel-based graphics card. Sadly I don't know much about the exact supported features on different Intel graphics cards, and it's really possible that there even isn't a driver that could give you full 3D support that would make very program work correctly.

Anyway, you already have a correct driver, since Intel's drivers are open-source and are included by default in Ubuntu. So the only way to improve things would to update it to a later version of the drivers, which you can do by enabling tis PPA repository: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") (there's also xorg-edgers PPA with even more up-to-date drivers, but they might not be very stable: [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa"))

Of course there might be some kernel option or setting for xorg.conf that would fix the problems but you'll really just have to wait for somebody with the same graphics card to tell you about that (or try searching the forums/google with your graphics card model to see if there's any info available).

---

### Post by DaGeek247 on 2010-08-19
alright, I have the ppa stuff set up, where do i go from here?

---

### Post by ubudog on 2010-08-19
Check update manager to install.

---

### Post by DaGeek247 on 2010-08-19
Could not find anything about my card (82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device) in the update manager.

I did however find [this pos]("http://ubuntuforums.org/showthread.php?t=256470")t, and i was wondering would it work for 10.04?

---

### Post by DaGeek247 on 2010-08-19
bump heheh

---

### Post by DaGeek247 on 2010-08-20
I borrowed my brothers nvidia card, and it fixed the problem, but ran the gamemaker extremely slow. i have added the other ctrl+alt+delete equivalents to the list on the first post, and I am going to ask a fellow geek if he has any extra cards. hope it works out, and since this post is about the ctrl+alt+delete equivalent, i will mark it as solved, since i got more that enough replys to that.

---

