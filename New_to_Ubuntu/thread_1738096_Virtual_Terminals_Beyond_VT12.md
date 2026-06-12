---
title: "Virtual Terminals Beyond VT12"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by aphatak on 2011-04-24
Ubuntu gives me six virtual terminals with a log-in screen, and these can be reached by keying ctl-alt-F1 through ctl-alt-F6 (let's call them VT1 through VT6 for short).  The default GUI is reached by ctl-alt-F7 (i.e., on VT7).  Virtual terminals corresponding to ctl-alt-F8 through ctl-alt-F12 (VT8 through VT12) do not show a log-in screen; however, I can use them for additional GUI sessions, either connected to the local machine or remote machines.  Clear so far.
I want to run more than 5 additional GUI sessions.  Is there a way I can configure Ubuntu (a) to have twelve log-in screens instead of the default 6, (b) to start the first GUI session on VT13 instead of on VT7, and (c) configure a convenient keyboard shortcut, such ctl-rightalt-F1 to reach VT13?

UPDATE:  I discovered a minute ago that I do not necessarily have to start new GUI sessions in VT8 through VT12; I can start them in VT6 and lower as well.  For example, I started a console in VT3, logged in and started a new GUI session in VT3.  The world did not come crashing down about my ears, neither were bolts of lightning set down from the heavens to strike me down.  I could operate the GUI session, exit to the console and terminate the console session without doing any harm to myself or my fellow humans.  So if I can control which VT the default GUI session begins, and how many consoles I can get, the problem would be solved.

Any suggestions?

---

### Post by aphatak on 2011-04-25
One more discovery - I can start a new graphical terminal in VT13 without making any configuration changes whatsoever.  And I can switch to VT13 if I key in Shift-alt-F1.  However, this works only from a console terminal.  If I am in a graphical terminal (such as the first graphical terminal in VT7), the Shift-alt-F1 is simply ignored.
So now the problem I need to solve is, (a) how to move the default graphical terminal away from VT7, and (b) how to show the console in VT7-VT12.
Any ideas, anyone?

---

### Post by JKyleOKC on 2011-04-25
There is code in the bootup sequence that creates the virtual terminals. Up until a couple of years ago Ubuntu used the "SysV" boot procedures and it was then quite straightforward -- the code used a "for x = 1 to 6" loop and you could change the "6" to almost any number you wanted to change the number of ttys, although most folk who tweaked it did so to cut the number down rather than to increase it.

Now, however, Ubuntu uses the "upstart" boot procedures and it's not nearly so simple to change. In addition, going past the number of function keys available might well impact other parts of the system.

If you're looking for details on how to do it now, try the "program development" forum here -- it's definitely not a subject for the "absolute beginner" area since changing the boot code is an almost guaranteed way to get a non-working system. However, why do you need multiple consoles to launch multiple GUIs? You can launch many different applications at the same time, and the window managers provide multiple "workspaces" which are essentially what you seem to be looking for. Tell us more about your needs and we can steer you to the existing features that are most likely to fill them. 

And welcome to the forums. You'll find most answers here!

EDIT: To get a GUI on tty2 (ctrl-alt-F2) just login and then type "startx" at the prompt. This will launch the GUI for you, and it will probably be on tty8 since they are created on the first available slot. However using "workspaces" is considerably simpler, and both Ubuntu and Xubuntu allow you to set the number of them you have.

---

### Post by aphatak on 2011-04-25
The reason I need multiple graphic sessions is twofold.  One, I want to compare Gnome, KDE, XFCE4 and LXDE (and eventually Unity) desktop environments with the same core.  Two, I also want to access a couple of other computers - three file-servers and two HTPC computers - from the same physical console.  The physical console has two monitors attached to it, and it is getting two more, giving a grand total of four monitors.  I thought it would be convenient to have the same physical console hooked into the whole lot, and switch machines as and when needed.
I did suspect the 'absolute beginnier talk' would not be the right place for this question; when it comes to computers, I still think of myself as a beginner, scratching the surface and stumbling around without a clue!
Thanks for your advice - I will try the developers' forum.

---

### Post by JKyleOKC on 2011-04-25
Good reasons, all, and not solvable by using workspaces since they are all part of the same window manager/environment.

It might be simpler to install VirtualBox and then create separate identical virtual machines for each distro. They would all have the same core, even though it would not be the actual hardware of the host but rather the guest VM's emulation of it, which would mean they almost surely would have different drivers from those installed in the host system. This ought not invalidate your comparisons, though, since all would have the same emulation.

---

### Post by aphatak on 2011-04-26
VirtualBox fits my needs - I can install any Linux distribution in a VM instance with bridged networking (indeed, any OS capable of X over ssh will do): this lets the instance have its own IP address in the same subnet as the VirtualBox host.

I discovered that I need not dedicate a virtual console AND a graphical console to each machine that I want to run.  What I can do is -
a) Open a terminal from within my main (Ubuntu) desktop environment.
b) Enter 'sudo xinit -- :<n> vt<mm>' where <n> is the session number starting at 1 (0 has been hijacked by the main Gnome session), and <mm> is the virtual terminal number 8-24.  This starts an X-session, and automatically switches me to the target virtual terminal.  The terminal window in the main Gnome environment is then kind of locked, and will not be released till the target session ends.
c) Enter 'ssh -X <ip-address> -l <log-in name>' where <ip-address> is the address of the target VM, and <log-in name> is the name under which you want to log in to the target VM.  When prompted, key in the password to log in.
d) Start the graphical environment with the command 'gnome-session', 'startkde', 'startxfce4' or 'startlxde', depending on which desktop environment you want the VM to run (assuming the VM has that environment installed).  The desktop appears, and the terminal from which it was started appears as a window.  Don't kill this window, merely minimize it to get it out of your way.
[INDENT]At this point I have the virtual machine in all its resplendent glory on all my monitor/s.  Ctl-Alt-F7 gets me back into the main desktop (where I started).

The down side of using virtual terminal numbers beyond 12 is that the shift-alt-F1 through shift-alt-F12 keystrokes to reach virtual terminals 13-24 do not work in a graphical environment; you must 'sudo chvt <mm>' to reach these virtual terminals.  Ctl-alt-F<1-12> keystrokes work anywhere.  Also, if you are in a virtual terminal that is NOT running a graphical environment, shift-alt-F<k> keystrokes work.[/INDENT]e) To extricate myself from this labyrinth and to see daylight again, I log out from the virtual graphical terminal.  I don't see a log-in screen here; I restore the window you minimized, and hit ctl-C.  That is when I see the command prompt again.  I enter 'exit' at this command prompt.  That closes the X environment and returns me to the terminal window in the main graphical environment where I started.


[CENTER]:D :D :D :D Linux ROCKS! :D :D :D :D[/CENTER]


If anyone is crazy enough to want to try this, put in a post.  I will upload screen-shots depicting the whole sequence.

---

### Post by aphatak on 2011-04-27
One last note:  starting virtual terminals with a log-in prompts turned out to be easier than I thought.  All you need to do is create a short script in /etc/init directory.  An example:  if you want to start a virtual terminal in VT8, create a file '/etc/init/tty8.conf', and put the following into it -
```

# Start a terminal with a login prompt in VT8
start on runlevel [23]
stop on runlevel[!23]
respawn
exec /sbin/getty -8 38400 tty8

```
When you re-start, try ctl-alt-F8, and you shound see the log-in prompt instead of a blank screen with a cursor blinking at you.  You might have to tweak the getty parameters for the encoding and baud-rate, but not much else.

**_A word of caution_**:  Do **_NOT_** try starting a terminal in VT7.  Not only will it not work, it will screw up permissions on the .ICEauthority file in your home directory, causing the gdm to complain that it cannot be updated.  Does it look like a tiny little bit of hard-coding (shudder - NO!) to you?  If and when I figure this out, I will update this post, although I am not going to hold my breath for this.

---

### Post by JKyleOKC on 2011-04-28
> **aphatak said:**
> 
**_A word of caution_**:  Do **_NOT_** try starting a terminal in VT7.  Not only will it not work, it will screw up permissions on the .ICEauthority file in your home directory, causing the gdm to complain that it cannot be updated.  Does it look like a tiny little bit of hard-coding (shudder - NO!) to you?  If and when I figure this out, I will update this post, although I am not going to hold my breath for this.I suspect that it's because the gdm process has already created tty7 for use by the GUI. If you want to try to verify this, boot a machine up without starting gdm, by using the "text" boot option, and see whether that lets it work. However this is an at-your-own-risk experiment since I have no idea how to clean up the .ICEauthority file if it gets messed up!

I doubt that it's explicit hard-coding, but it's quite likely that gdm is using some internally-defined value to decide what tty to create for use by the GUI. This might be defined somewhere in the /etc/default subdirectories. Take a look at /etc/default/console-setup if it exists in your system...

---

### Post by aphatak on 2011-05-05
Another update: I could get Gnome desktop to start in VT13 - after a fashion.
[LIST=1]
[*]I created tty7.conf to tty12.conf in /etc/init.
[*]Logged in normally.  No bombs fell, and neither did lightning bolts strike me down.
[*]Switched to a terminal (ctl-alt-F1).
[*]Stopped gdm - ```
sudo service gdm stop
```[*]Started gdm again - ```
sudo service gdm start
```[/LIST]
Lo and behold - I heard a chorus of cherubim and seraphim singing Halleluja and Hosanna, and the Gnome desktop turned up in VT13.  I could reach it with shift-alt-F1 as expected.

@JKyleOKC - you were right.  The first time around, gdm had already kicked in before my .conf files were processed, and assumed that I, like all God-fearing users, was happy with six consoles, decided the seventh slot was open, and put the Gnome desktop there.  When I re-started gdm, it saw VT13 as the first open slot, and duly started the Gnome desktop in it.

Now I have to figure out how my tty.conf's can beat gdm to the starting line.

And one confession: the thought of Gnome in VT13 was the farthest from my mind when I re-started gdm; I was hunting for something entirely different!

---

### Post by JKyleOKC on 2011-05-05
Read up on "upstart" and somewhere in all the material you may find a way to postpone the launch of gdm until after tty12 has been created. I don't know of any specific reference manual, but over the months that I've been dealing with upstart I've found that there's a line in the header of its init-script for each service that shows prerequisites for that service to start. If you can find the script for gdm, and the event tag for tty12, that ought to solve your problem!

EDIT: Also, have a look at /etc/default/gdm which may have a line in it showing 1-6 ttys. Changing that to 1-12 might be all you need to do!

---

