---
title: "Bootup Problem with X"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by JugglinPhil on 2009-09-15
Got a little trouble here: Whenever I start Ubuntu, X doesn't load, I only get the well known Linux terminals (tty1-tty6) without the graphical interface. I already tried starting X manually using 'startx', which only gives me some error. Any idea how to fix this? Has it got anything to do with the run-levels, and if so how do I set it back to starting X by default (Run-level 5 I believe it is)? Thanks a bunch in Advance.

---

### Post by JugglinPhil on 2009-09-16
Okay I managed to write down the error output I get using 'sudo startx', it took quite a while until I got it all written down by hand. Anyway, here it is:

sudo startx
mktemp: cannot create temp file /tmp/serverauth.UpXvoivpnu: Read-Only file system
/usr/bin/startx: line 158: cannot create temp file for here document: Read-Only file system
xauth: error in locking authority file /home/username/.Xauthority
/usr/bin/startx: line 170: cannot create temp file for here document: Read-Only file system
xauth:error in locking authority file /home/username/.Xauthority
/usr/bin/startx: line 170: cannot create temp file for here document: Read-Only file system
X: warning; process set to priority -1 instead of requested priority 0
Fatal server error:
could not create lock file in /tmp/.tX0-Lock
Please consult the The X.Org Foundation support
at [http://wiki.x.org](http://wiki.x.org)
for help
ddxSigGiveUp: closing log
giving up.

I sort of understand that the problem is it can't create some kind of file, but I really got no plan on how to go on with this.
Ubuntu is pretty much useless to me without X, as I only use it for multimedia and surfing the web so I would seriously appreciate your help folks. :) Always having to use the live cd gets a bit annoying...
Greetings, JP

---

### Post by JugglinPhil on 2009-09-16
Hi folks, I recently posted a thread about my problem with booting X and the graphical interface, but since no one replied to it yet I thought I'd post it in a more frequented forum. Here's the link, please go and take a look: [http://ubuntuforums.org/showthread.php?t=1266977](http://ubuntuforums.org/showthread.php?t=1266977)
Greetings JP

---

### Post by JugglinPhil on 2009-09-16
Hi folks, I recently posted a thread about my problem with booting X and the graphical interface, but since no one replied to it yet I thought I'd post it in a more frequented forum. Here's the link, please go and take a look:  [http://ubuntuforums.org/showthread.php?t=1266977](http://ubuntuforums.org/showthread.php?t=1266977)
Greetings JP

---

### Post by NightwishFan on 2009-09-16
It keeps complaining that it is a read only file system, is something wrong with your root partition?

---

### Post by CoolHand on 2009-09-16
Just a wild guess at it here.  First I believe you should be able to use the startx command as your regular user without sudo.  Asside from that it looks like permission issues to me.  Try creating a new user with default permissions and see if that user can start X.  Also in general check your permissions on your various directories listed in the error.  Did you change them or try to lock things down prior to this?

---

### Post by LewRockwell on 2009-09-16
> **JugglinPhil said:**
> Hi folks, I recently posted a thread about my problem with booting X and the graphical interface, but since no one replied to it yet I thought I'd post it in a more frequented forum. Here's the link, please go and take a look:  [http://ubuntuforums.org/showthread.php?t=1266977](http://ubuntuforums.org/showthread.php?t=1266977)
Greetings JP

looks like you posted in triplicate

please post each trouble-call once(Absolute Beginner Talk works best)

what equipment?

what version?

updates current?

did it ever work properly?

what specifically has been altered/added/changed that might shed some light on the trouble-call difficulties?

.

---

### Post by JugglinPhil on 2009-09-17
Might be, as I said I don't really have any idea... Assuming something was wrong with my root partition, how do I go on to fix it? Thanks for the reply anyway, may the force be with you. :)

---

### Post by wojox on 2009-09-17
Try and boot into single user mode when your computer is starting, there should be a brief message along the lines of "GRUB Loading... Press Esc to enter the menu". Press Esc at this prompt to select recovery mode.

---

### Post by quixote on 2009-09-17
wojox, what should he do once he's in recovery mode?  If he tries startx again, won't it fail with the same permission problems?  Or does recovery mode make a difference there?

Couple of things to check when you're in recovery mode: how full is your root partition?  At the prompt type:```
df -h
``` If it reports / as 100% used or even anything over 95%, that could be your problem right there. Then your first thing, -- before doing anything else because any disk accesses might get confused by the full disk and overwrite other data, -- is to delete something.  If your /home is on the same partition, a space hog that can be harmlessly deleted is ```
rm /home/your-login-name/.thumbnails
``` (That's nautilus's cache of thumbnails.)

If that's *not* the problem, then you probably have broken packages.  ```
dpkg --configure -a
``` might be worth a try.  (You won't need "sudo" first because you're already root.)

---

### Post by quixote on 2009-09-17
There are replies at your link :)

---

### Post by JugglinPhil on 2009-09-17
Hi I'm back with my results:
Tried booting into recovery mode, I don't really know what's supposed to happen but I only got like a blue box giving me a bunch of options, tried them all with no success.
Next thing I tried the 'df -h' command, however the highest 'Use' value was 40%. 
'dpkg --configure -a' told me I need to be root, with 'sudo' in front of it the output was:
'dpkg: unable to access dpkg status area: Read-only file system'
So after all no real success, but thanks anyway 
Should I maybe just reinstall Ubuntu? Might be easier and quicker...

---

### Post by JugglinPhil on 2009-09-17
Yeah by now there are, so should I delete this one or something?

---

### Post by JugglinPhil on 2009-09-17
@ Coolhand, could you tell me any commands on how to do this, I am rather new regarding the terminal.. Without being root nothing really worked, even startx refused to run from my own account

@LewRockwell, sorry about that, in fact I wanted to move my thread to either General Help or Absolute Beginner Talk but couldn't figure out how, so I thought posting a link might be an idea... Won't happen again, do you want me to delete the two with the links?

---

### Post by LewRockwell on 2009-09-17
> **JugglinPhil said:**
> @ Coolhand, could you tell me any commands on how to do this, I am rather new regarding the terminal.. Without being root nothing really worked, even startx refused to run from my own account

@LewRockwell, sorry about that, in fact I wanted to move my thread to either General Help or Absolute Beginner Talk but couldn't figure out how, so I thought posting a link might be an idea... Won't happen again, do you want me to delete the two with the links?

the mods will tidy things up when they get around to it

.

---

### Post by quixote on 2009-09-17
When you boot into recovery mode, go to the last option: "root with network access."

Given those disk usage stats, that's not it.

If you tried the dpkg command in a recovery command line and you got that message, then it sounds like what may have happened is your "sudoers" file got blown up.  This says who has which permissions on the computer, and if "root" doesn't have permissions, then you're dead in the water.

You can fix that file (involves editing one text file at a command line) or reinstall.  It'll take me a while to pull together the instructions on visudo, which is what you have to use to edit sudoers, so let me know if you want that.

Or, others here may have other diagnoses of the problem ...??

---

### Post by bapoumba on 2009-09-18
> **LewRockwell said:**
> the mods will tidy things up when they get around to it

.

Threads merged.

---

### Post by JugglinPhil on 2009-09-18
Thanks for the help quixote, I tried the command from the recovery mode root shell prompt, however with the same results. Do you think it is worth keeping it up and try to do that edit you mentioned? Assuming I would reinstall, is there any way to save the programs I had on it so I get them all back on the fresh one, or at least create a list of them so I can get them through synaptic?

---

### Post by quixote on 2009-09-18
There is a directory that has the complete list of all the programs installed, but I can't remember or find where it is.  /var/cache/apt? I looked on my system, but it doesn't look right.  I know there is one, though, somewhere.

Fixing sudoers:  Boot into recovery mode.  This is what a normal sudoers file looks like. ("#" precedes comments, bolded lines are important)  ```
# /etc/sudoers
# This file MUST be edited with the 'visudo' command as root.
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification
# User alias specification
# Cmnd alias specification

# User privilege specification
**root	ALL=(ALL) ALL**

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
**%admin ALL=(ALL) ALL**
```
You can look at the file by using ```
cat /etc/sudoers
```.  Check it out and see if it looks like the above.  If the root or admin line is missing or commented out, then you can edit it to fix that.

To edit, you have to use the command ```
visudo
```
Visudo, if I remember right, requires use of the arrow keys to get to where you need in the file.  You can backspace to delete, but I don't think the delete key works.  I seem to remember it tells you what to do to save and quit.  (Been a while since I used it.)

---

### Post by JugglinPhil on 2009-09-19
Hi quixote, did as you told me but the problem is somewhere else: The file is exactly the same as the one you posted... :( I decided to go for a reinstallation, simply can't be bothered anymore. But thanks a lot for your help with this. :) Hope it wasn't too much hastle for you.

---

### Post by quixote on 2009-09-19
I think it's probably best to reinstall, so you made the right choice.  When a system is being that flaky, you can spend days fixing it, and then it winds up still not fixed.  It's a shame about having to reinstall all your programs, but that might actually take less time than trying to figure out what's wrong.

Hope the new install doesn't give you any more grief!

---

### Post by JugglinPhil on 2009-09-20
Yes you're right, there was no point in going on. I am just getting all my programs back right now, and I had all my media on external disks anyway so it wasn't too bad. So, see you around the forums buddy. :)

---

### Post by pickarooney on 2009-09-27
I've ended up in the exact sa,e situation as JugglinPhil here after attempting to uninstall splashy and reinstall usplash: I'm just going to reformat but I think it should be made clear that messing about with splash screens can have fatal consequences even when following supposedly sound instructions

---

### Post by quixote on 2009-09-27
Yikes.  I've changed splash screens a couple of times in the distant past. (I think it was even pre-Ubuntu, on Redhat 7 or something.)  I guess if I try again, now I know to be super-careful.  If the karmic bootup screen keeps that horror-movie color scheme that it has in alpha, I'm going to have to try.  :P

---

### Post by pickarooney on 2009-09-29
Karma has ditched Usplash altogether from what I can tell. Who knows what the replacement will be like.

---

