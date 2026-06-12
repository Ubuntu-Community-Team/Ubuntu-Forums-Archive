---
title: "Missing Title Bars in 10.04"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by Intyalle on 2011-02-23
Okay, so my Linux lappy has been down for a few months now due to this problem (due to some moving around that took longer than expected, and it was more to unpack that I might not have time to fix), so I can't say what triggered it. I do know that I don't *know* of anything I did to trigger it, but... there may be something I didn't realise at the time and have forgotten since.

Basically, once upon a boot, all my windows no longer had title bars - the bits with the x and minimise that let you move the windows around and the like, as well as the corresponding bar at the bottom. I could not switch between my four desktops, and after a restart could no longer even see four, but one. The settings said it was still set to four, but only one showed in the area that lets you name them. None of the windows show on the bottom task bar, either. I don't think I can switch windows, but since I kept most of my windows maximised and now can't change that... without taskbar icons, it's hard to tell.

Additionally, I couldn't select any pop-up windows like the one that comes up to ask for the root password in some situations. I could still click the buttons on that, but I couldn't select the text box in order to type in the password.

I've tried what few solutions I've found so far with no success. Does anyone know anything I could try to fix this problem SHORT of reinstalling? I am inclined to wipe and clean install again anyway, but as things stand right now I can't back up my important files, so even a temporary fix just to swap some files across would be good.

Thanks in advance for any help.

---

### Post by SnickerSnack on 2011-02-23
There are several things I know of that you can do to make further attempts at fixing the problem a bit easier (though I don't know how to outright fix your problem).

1. You can move windows without click the title bar.  Holding down Alt allows you to move a window anywhere you click on it.

2. You can close a window using Alt+F4.

3. You can run programs such as synaptic through the command line and enter the password there. Ex:

```
$sudo synaptic
```

4. If all four desktops are there, and the panel simply isn't showing them, then you can switch desktops by Holding Alt+Crtl and pressing up/down/left/right.

5. It sounds like your panel is also not working.  You can restart it with the following command

```
killall xcfe4-panel ; xcfe4-panel
```

which may help.  There may be a specific command for this, but I don't know of it.

6. You can change which window has focus using Alt+Tab.

You might try simply reinstalling xcfe; I don't see any reason to reinstall the whole thing just yet.  I'm not sure of the best way to go about this, though.

---

### Post by Intyalle on 2011-02-23
1. I didn't know that :) Thanks, I'll try that - that ought to help with backing up my files.

2. Closing hasn't been an issue, I can still see the program-specific menu bar, which generally includes a Quit/Close option. Fortunately.

4. They were originally shown but I couldn't switch between them, it was only after a reboot that they stopped showing altogether, so it's more likely that feature has pretty much conked it completely right now.

6. I probably already tried alt+tab in the early stages (if so, obviously without success) in an attempt to, if nothing else, at least be able to change between fix info from Google and the window in which to implement the fix. Or even my two FF windows. I'll make a note to try again in case, though.

And for your last point, I already came across and tried reinstalling xcfe (specifically the fix in question said xcfe4 for the package) without any luck. It was, however, for a similar issue in 6.06, so it's possible that's not the package used now or something...? If I should be using a different package name for that please let me know what I *should* use.

Thanks for your points, if nothing else comes up that should (hopefully, assusming they work) be enough to at least back up my important files so I can wipe and reinstall (which I do have reasons for wanting to do besides this issue).

---

### Post by SnickerSnack on 2011-02-24
xfce4 has more than one component, so you'd probably need to try reinstalling all of them.  It's also possible that there's a corrupted config file somewhere.  I looked for a .xfce4 directory in my home directory, but I didn't find it.

Why can't you backup your files?  All you need for that is the command line.  If you're having trouble opening one (maybe the panel menu isn't working?), just close everything and then open a terminal by right clicking on the desktop and clicking "open terminal here".  Instructions for doing that can be found here: [http://www.thinkwiki.org/wiki/How_to_copy_a_Linux_installation](http://www.thinkwiki.org/wiki/How_to_copy_a_Linux_installation)

---

### Post by Intyalle on 2011-02-24
I'm not good enough with terminal to manage backing up that way, so the reason I haven't been able to back up is not being able to move windows so I can drag and drop from one to the other. Not to mention that I don't know the exact file names of all the files I need to back up... indeed, if I didn't search through every folder I'd probably forget something important altogether.

---

### Post by SnickerSnack on 2011-02-24
Then you need to learn how to use the terminal.  I gave you a link for step-by-step instructions.

---

### Post by vicious blue on 2011-02-24
As a newbie, I'm having the same problem. I have accidentally deleted the applet so when I minimize any window it is lost forever. I have to use alt-tap to cycle nevertheless I'd like to return to classic view; where I minimize any window to an applet. How will I restore?

It's 10.10 though

---

### Post by Intyalle on 2011-02-24
> **SnickerSnack said:**
> Then you need to learn how to use the terminal.  I gave you a link for step-by-step instructions.

I *am* learning how to use the terminal. Moving files around, however, is not what I usually need to do with it, so I haven't learned much in that direction.

As to your tutorial, it doesn't have moving *specific* files. I don't need to back up *everything* - now that I have a specific games computer I can remove a lot of the stuff that's there anyway. I just need to back up important stuff, like my timetables for uni that starts on Monday.

---

### Post by drdos2006 on 2011-02-24
If you need to re-install, leave 20-30 gigs for the Operating system and some for swap file, then use the remainder of the drive for data.
Install the OS in the 20-30 g section.
That way you can get at your data even if the OS is corrupted.

regards

---

### Post by SnickerSnack on 2011-04-18
> **Intyalle said:**
> I *am* learning how to use the terminal. Moving files around, however, is not what I usually need to do with it, so I haven't learned much in that direction.

As to your tutorial, it doesn't have moving *specific* files. I don't need to back up *everything* - now that I have a specific games computer I can remove a lot of the stuff that's there anyway. I just need to back up important stuff, like my timetables for uni that starts on Monday.

I hope you've worked this out by now.

In hindsight, I was maybe a  bit rude in my last post.  That was quite unintentional.  I'm just very adamant about new linux users learning to use the terminal with some fluency (I feel it's a bit like insisting that new drivers learn to shift gears properly).

---

### Post by LJF1 on 2011-06-06
> **Intyalle said:**
> Okay, so my Linux lappy has been down for a few months now due to this problem (due to some moving around that took longer than expected, and it was more to unpack that I might not have time to fix), so I can't say what triggered it. I do know that I don't *know* of anything I did to trigger it, but... there may be something I didn't realise at the time and have forgotten since.

Basically, once upon a boot, all my windows no longer had title bars - the bits with the x and minimise that let you move the windows around and the like, as well as the corresponding bar at the bottom. I could not switch between my four desktops, and after a restart could no longer even see four, but one. The settings said it was still set to four, but only one showed in the area that lets you name them. None of the windows show on the bottom task bar, either. I don't think I can switch windows, but since I kept most of my windows maximised and now can't change that... without taskbar icons, it's hard to tell.

Additionally, I couldn't select any pop-up windows like the one that comes up to ask for the root password in some situations. I could still click the buttons on that, but I couldn't select the text box in order to type in the password.

I've tried what few solutions I've found so far with no success. Does anyone know anything I could try to fix this problem SHORT of reinstalling? I am inclined to wipe and clean install again anyway, but as things stand right now I can't back up my important files, so even a temporary fix just to swap some files across would be good.

Thanks in advance for any help.

I have just encountered the same exact problem, and came across the following board:
[http://ubuntuforums.org/showthread.php?t=309832](http://ubuntuforums.org/showthread.php?t=309832)
"for the solution try pressing Alt+F2 and then type xfwm4. it worked for me just now."

Worked for me as well, was literally pulling my hair out trying to work out what I'd done (still not sure what (or if) I did.

---

