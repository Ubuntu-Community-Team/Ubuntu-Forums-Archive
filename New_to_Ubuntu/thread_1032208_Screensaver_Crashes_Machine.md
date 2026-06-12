---
title: "Screensaver Crashes Machine"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Pete666 on 2009-01-06
Hi,

I am a complete newbie to using Linux seriously. I have had a play with some "run from CD only" freebies but have always resisted putting it on my hard drive.

Last week I decided to install a copy of Ubuntu 8.1 onto my hard drive and was very pleased with it, as it installed cleanly and picked-up all my hardware perfectly.

However, last night I was having as look around and went to the screensaver area. I selected Ant to kick-in after 10 minutes.

This it does, but locks the machine totally and the only cure seems to be to re-boot.
I then went back to try to disble the SS but as soon as I  select "Screensaver" from the dropdown menu the machine locks again.

I don't really care about having a screensaver - I was just curious about what was available !

I am thinking of re-installing the OS again, as apart from adding updates and a few Firefox links I have not changed anything.

Is there some way to disable the SS without re-installing the whole OS ?

Thanks.

---

### Post by SteveDee on 2009-01-06
Don't re-install at this stage.

I think the screen saver problem in Intrepid is that it soaks up 100% cpu time. So if your pc is not that powerful it may appear to have completely crashed, but it probably has not.

I suggest you initially install System Monitor and get it to display your cpu usage in a panel. Then when you go into the screen saver config screen you can see if this is the case.

---

### Post by SteveDee on 2009-01-06
This is how you can clear your screen saver selection without going into System > Preferences > Screen Saver and locking up your system:-
 - In a terminal window run: gconf-editor
 - Navigate to apps > gnome-screensaver
 - Go down to: themes
 - Right click then select: Unset Key

Your screen saver will now be the "blank" default.

Note: you maybe able to find gconf-editor under Applications > System Tools > Configuration Editor. This just saves you opening a Terminal window.

---

### Post by Pete666 on 2009-01-06
I ran the CPU check first which rocketed up to 100% on selecting Screensaver from Preferences and then dropped down to 10% just prior to freezing.
My PC is a a 2 Ghz Athlon with 512 meg ram.

Then re-booted & cleared the screensaver as per your instructions. 

Fantasic - screensaver cleared & all OK now.

Thanks a million for your clear instructions.

---

### Post by laceration on 2009-01-06
how about system -> control center -> screensaver
then uncheck activate screensaver when computer is idle
The other answer you got did not disable it it just set it to running a blank screen.

I very much dislike the gnome-screensaver, I will take this opportunity to vent.  
[LIST]
[*]It very well may have crashed your system
It has happened to me before, one of the screensavers it plays does it. 
[*]It is obsolete
Screensavers were invented in the olden days because display phospors would burn in.  Displays have not been built like this for eons.
[*]It uses a lot system resources
[*]It cannot detect if a video is playing and will start while one is playing.  gnome-screensaver expects video players to implement the solution on their end in a burdensome and difficult way.  That is so bassackwards!

I'm going to put this on Brainstorm:idea:  Remove gnome-screensaver from the default installation!
[/LIST]

---

### Post by SteveDee on 2009-01-07
> **laceration said:**
> how about system -> control center -> screensaver
then uncheck activate screensaver when computer is idle
The other answer you got did not disable it it just set it to running a blank screen.

I very much dislike the gnome-screensaver, I will take this opportunity to vent.  
[LIST]
[*]It very well may have crashed your system
It has happened to me before, one of the screensavers it plays does it. 
[*]It is obsolete
Screensavers were invented in the olden days because display phospors would burn in.  Displays have not been built like this for eons.
[*]It uses a lot system resources
[*]It cannot detect if a video is playing and will start while one is playing.  gnome-screensaver expects video players to implement the solution on their end in a burdensome and difficult way.  That is so bassackwards!

I'm going to put this on Brainstorm:idea:  Remove gnome-screensaver from the default installation!
[/LIST]

Hey buddy, I agree with you!:)

Some time in the early 1990's screen savers took on a life of their own. People started spending more time searching, downloading and watching the damn things than they did doing anything useful. On 'buntu I use the ant with the spot light from time to time just to check that my cpu fan is running OK.

The reason I took Pete on the System > Preferences > Screen Saver route was because going to the normal Screensaver screen is also locking up his system, as this runs the selected SS in preview mode upon entry, which still uses 100%cpu. The Blank screen option does not appear to load the cpu.

To completely disable the screen saver via Applications > System Tools > Configuration Editor (gconf-editor) untick the idle_activation_enabled check box.

---

### Post by Pete666 on 2009-01-07
Just to confirm all is now OK.

The black screensaver does indeed kick in after 10 mins but, as Steve says, this does not seem to cause a locking problem.

---

### Post by quicknick_26 on 2009-01-14
I think I might be having the same problem. My screensaver froze up. I was able to <ctrl><alt><backspace> to restart the session, but it just spit out a bunch of errors (attached image) and locked up completely from there.

I have system monitor, but I don't see how to display the cpu usage on the desktop panel.

Is there a way to fix this without disabling the graphical screensaver?

---

### Post by SteveDee on 2009-01-15
> **quicknick_26 said:**
> I think I might be having the same problem. My screensaver froze up. I was able to <ctrl><alt><backspace> to restart the session, but it just spit out a bunch of errors (attached image) and locked up completely from there.

I have system monitor, but I don't see how to display the cpu usage on the desktop panel.

Is there a way to fix this without disabling the graphical screensaver?

System Monitor:-
 -Right click on a clear space in your panel.
 -Select "Add to Panel"
 -Go down the list of Applets and select System Monitor.

This gives you a small graph of cpu % in use.

You can change the monitor function by right clicking on the little graph and selecting Properties.

If you need to monitor more than one parameter, just repeat the process and set the individual graph properties as required (I'm currently running with 3; cpu, memory & network).

As for your screen shot, I've no idea what that is trying to tell you.

---

