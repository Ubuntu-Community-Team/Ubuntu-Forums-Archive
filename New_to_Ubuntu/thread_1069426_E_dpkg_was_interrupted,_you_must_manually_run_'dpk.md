---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the p"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by hifly1231 on 2009-02-14
I've been trying to install Windows Me inside Virtualbox, and got the bright idea to try to upgrade to Virtualbox 2.1.2.  Now I'm getting the message "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.".  I can't get into Synaptic Package Manager to try to undo what I've done, and Terminal is telling me the same thing.  What do I do???  I don't want to have to reinstall my Ubuntu!!!

---

### Post by wolfen69 on 2009-02-14
> **hifly1231 said:**
> Terminal is telling me the same thing.
what is the terminal telling you? did you do ```
sudo dpkg --configure -a
```

---

### Post by lazyart on 2009-02-14
If the OS tells you to do something, it probably a good idea to follow.  Note that you will have to close Synaptic to run the command.

---

### Post by hifly1231 on 2009-02-14
> **lazyart said:**
> If the OS tells you to do something, it probably a good idea to follow.  Note that you will have to close Synaptic to run the command.

When I run the command, it brings up this blue package configuration box that says: 


     &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring virtualbox-2.1 &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
     &#9474;                                                                   &#9474; 
     &#9474; Creating group 'vboxusers'                                        &#9474; 
     &#9474;                                                                   &#9474; 
     &#9474; Users of VirtualBox must be members of that group. Host network   &#9474; 
     &#9474; interfaces will be assigned to that group.                        &#9474; 
     &#9474;                                                                   &#9474; 
     &#9474;                              <Ok>                                 &#9474; 
     &#9474;                                                                   &#9474; 
     &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 

I have no clue what to do now.

---

### Post by egalvan on 2009-02-14
> **lazyart said:**
> If the OS tells you to do something, it probably a good idea to follow.  Note that you will have to close Synaptic to run the command.

I totally agree with this, BUT from a beginner's view-point,
it is not always clear HOW one must follow the instructions given. :confused:

Sure, most of us "know" that we have to
 shut down Synaptic,
 open a terminal,
 type that command,
 type our password (and not get any "feedback" on the screen :-?)
 in order to "fix" this problem.

But for every one of us, there was a time when we DIDN'T know this...:)

let's remember the title of this sub-forum

ABSOLUTE Beginner Talk. :-k

(Yes, i still remember the first time I received this error.
Took me a few moments to parse it through my experiences...
"let's see,
 "manually run" usually means "terminal"
*nix commands are usually 'funny letters' followed by stuff called 'options'
typing the 'funny letters' followed by "-help" often gives us "help" (what a concept; Microsoft should be this friendly)
let's type "dpkg -help" to see if there is some info on this..
sure enough, there it is....
so let's try the exact string that was shown...
I wrote it down somewhere...
hey, it worked!
wow.
I'm learning *nix command line!"

---

### Post by hifly1231 on 2009-02-14
> **egalvan said:**
> I totally agree with this, BUT from a beginner's view-point,
it is not always clear HOW one must follow the instructions given. :confused:

Sure, most of us "know" that we have to
 shut down Synaptic,
 open a terminal,
 type that command,
 type our password (and not get any "feedback" on the screen :-?)
 in order to "fix" this problem.

But for every one of us, there was a time when we DIDN'T know this...:)

let's remember the title of this sub-forum

ABSOLUTE Beginner Talk. :-k

(Yes, i still remember the first time I received this error.
Took me a few moments to parse it through my experiences...
"let's see,
 "manually run" usually means "terminal"
*nix commands are usually 'funny letters' followed by stuff called 'options'
typing the 'funny letters' followed by "-help" often gives us "help" (what a concept; Microsoft should be this friendly)
let's type "dpkg -help" to see if there is some info on this..
sure enough, there it is....
so let's try the exact string that was shown...
I wrote it down somewhere...
hey, it worked!
wow.
I'm learning *nix command line!"

I guess I'll just have to reinstall.

---

### Post by bryanl on 2009-02-14
a re-install is a brute force method, kinda' painful but often works.

The question is why synaptic won't run. It should. Maybe a log-off and log-on to clear any conflicting package managers? There should be some error message indicating why it won't run and that could be a clue.

If you give up on synaptic, try aptitude. Terminal command 'sudo aptitude'

What you need to do is to completely remove the packages that are causing the complaints. Once you get them removed, you can do a system update with no errors. Then you can try to re-install the packages you need.

This particular dpkg configure thing seems to have surface recently in a number of contexts. I wonder what happened, what changed.

---

### Post by oldos2er on 2009-02-14
"When I run the command, it brings up this blue package configuration box that says: 


     &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring virtualbox-2.1 &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
     &#9474;                                                                   &#9474; 
     &#9474; Creating group 'vboxusers'                                        &#9474; 
     &#9474;                                                                   &#9474; 
     &#9474; Users of VirtualBox must be members of that group. Host network   &#9474; 
     &#9474; interfaces will be assigned to that group.                        &#9474; 
     &#9474;                                                                   &#9474; 
     &#9474;                              <Ok>                                 &#9474; 
     &#9474;                                                                   &#9474; 
     &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;  &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 

I have no clue what to do now."

 Use the Tab key to highlight 'ok', then press Enter.

---

