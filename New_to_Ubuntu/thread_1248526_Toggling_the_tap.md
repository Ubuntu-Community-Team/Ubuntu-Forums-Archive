---
title: "Toggling the tap"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by BobJam on 2009-08-24
When I type anything in . . . a text editor, email, post window and such . . . the tap capability on my touchpad frequently causes the cursor to roam, and if I'm not looking at the screen then whole lines get placed in a jumbled mess.

I've tried TouchFreeze, but that doesn't remedy the issue.

The only way I seem to be able to solve this problem is entirely disabling the touch function through the System>Mouse program.

I have a Dell Inspiron 15n, and I don't know if it's a Synaptic touchpad or not.  I had an HP ze4700 that had a Synaptic touchpad, and qsynaptic and gsynaptic DID NOT remedy the same issue anyway.  I had to use the System>Mouse program there also.

Doing that every time I want to change back and forth is tedious.  So is there a way I can create a launcher or something so I can just toggle that touch function on and off?

I don't want to turn off the entire touchpad, which would disable the clicking buttons . . . just the tapping function.  As I said, the System>Mouse program allows me to do that, but it's tedious calling it up evey time and disabling the tap.

Toggling the tap on and off would be easier.

---

### Post by drs305 on 2009-08-24
On my laptop, I use the following command to turn on the tap function. You could build launchers for on (1) and off (0).
```

synclient TapButton1=1 # on
*or*
synclient TapButton1=0 # off

```

You could also easily set up keyboard shortcuts for the same commands.

---

### Post by BobJam on 2009-08-24
When I type the command in terminal (did the "off" one), I get "Can't access shared memory area.  SHMConfig disabled?"

What does that mean?  Seems like that would be a simple fix if maybe I could enable "SHMConfig" . . . whatever that is.

I tried "sudo" too, but got the same result.

What am I missing?

---

### Post by drs305 on 2009-08-24
In earlier versions of Ubuntu I had to place a section in /etc/X11/xorg.conf for the synaptics touchpad. It included an entry like "SHMConfig true" or something like that.

I'm running Karmic now and I don't have that section in xorg.conf any longer so it has moved elsewhere, if it's necessary at all. 

Do a search for your specific release of ubuntu and include "SHMConfig" and you will find the correct entry and where to place it.

---

### Post by sandyd on 2009-08-24
just booted up a dell inspiration w/ synaptic touchpad to tes it out.

the synaptic section aparently is needed in 8.04 and 8.10, but is not needed in 9.04 and 9.10.

works without problem.

seems more like a hardware issue.

if your doing a dual boot, does this happen in windows?

---

### Post by BobJam on 2009-08-24
Kewl . . . got it working.  Used the solution [here]("https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig").

Created two launchpads on desktop . . . one for "on" and one for "off".

However, would like to do hotkeys instead.  Am sure if I put my mind to it and read a little on it, I could figure out how to do it.  Is probably a real easy "duhhhh . . ." type of thing.

But, being the "low energy life-style" kinda' guy that I am, can I prevail on you to either give me the step-by-step method or point me to an instruction?  But if you don't have the time or inclination, I'll figure it out.

In any case, thanks VERY much, drs305, for getting me this far.

@carlee,

I'm not dual boot . . . was tethered to Windows there for a while, but am now completely Ubuntu.

Is working as it should now.

BTW, in my Google searches for the SHMConfig solution (thanks again, drs305), I did notice that quite a few folks had a similar problem.  Some added a section to the xconfig file, but for some that didn't work.  Then again, for the solution that I used from the help.ubuntu.com page . . . while that worked for me, it didn't for some others.

My conclusion is that the Synaptic touchpad, especially in Dells, is buggy . . . or Ubuntu doesn't deal with it too well.  Or likely both in some cases.

---

### Post by drs305 on 2009-08-24
Open gconf-editor in terminal.
Go to Apps, metacity, keybinding_commands.
Pick a command number, for instance, command_7
In the value, enter the command you want run.
Now go to apps, metacity, global_keybindings, run_command_7
In the value, put the key combination you want, such as <ALT>L
Done.



If you want a quick way via command line:
```

gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_12  'xkill'
gconftool-2 --set --type string /apps/metacity/global_keybindings/run_command_12 '<Control>P'

```

The example is for command 12.
Instead of 'xkill' you can substitute the synclient command and use whatever key combo you wish.

---

