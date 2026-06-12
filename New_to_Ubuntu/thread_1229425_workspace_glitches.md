---
title: "workspace glitches?"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by The Populist on 2009-08-02
Recently my webpages began to jiggle and jump up and down erratically. At first I had no idea what was happening. Then I minimized my pages and noticed a box with two arrows. The box would pop in, switch arrows, then dissappear.

Any solution?

---

### Post by The Populist on 2009-08-02
I have already tried creating only one workspace with one column and one row. All my webpages still jiggle. I am having trouble posting it is so bad.

...

---

### Post by Riaku on 2009-08-02
Do you have extras turned off in system> prefernces> apperance?

---

### Post by The Populist on 2009-08-02
Yes, visual effects are set to normal.

---

### Post by Riaku on 2009-08-02
Try turning them completely off

---

### Post by The Populist on 2009-08-02
Well, it seems to be working for now. Thanks Raiku. However, I still don't understand what the hell caused it.

...

---

### Post by Riaku on 2009-08-02
Theres an effect that is on linux called "wobbly windows" you may have have been accidently hittin the mouse pad and/or keys to make them move

---

### Post by The Populist on 2009-08-02
Nope, it's still jiggling.

---

### Post by The Populist on 2009-08-02
This started after the last update. I am making short posts because my computer is stuttering and then it reloads the page before I can post. Argghh!

---

### Post by Riaku on 2009-08-02
go to add/remove and download compiz, it;s the first one then go to system>perfernces> compizconfig and go to effects and turn off " wobbly windows"
if it's not that then we'll see what else we can come up with

---

### Post by The Populist on 2009-08-02
I did that. Compiz did not help. There is an effect that creates, wobbly windows. This is not what is happening. 

...

---

### Post by Riaku on 2009-08-02
I don't know then, I'm relatively new to ubuntu and nix in general heh

---

### Post by The Populist on 2009-08-02
I appreciate your help Raiku. I'm a noob myself. But I am sure this has something to do with the workspace box that keeps flashing.

---

### Post by The Populist on 2009-08-02
Help! I can barely use my computer.

---

### Post by The Populist on 2009-08-02
I'm going to keep bumping this until my windows stop bumping.

---

### Post by braete on 2009-08-02
only the pages "jiggle"?
or does the browser window acts the same way  ?

---

### Post by The Populist on 2009-08-02
All my windows stutter. Webpages, file windows, even add/remove. There is something seriously wrong. Again, there is a box that appears in the center of my screen when everything is minimized. Arrows appear and flicker between the two boxes, and everything stutters.

...

---

### Post by braete on 2009-08-02
try to get to compiz and disable desktop wall and viewport switcher

---

### Post by The Populist on 2009-08-02
I did what you suggested Braete, and it didn't work.

---

### Post by dagrump on 2009-08-02
First try setting effects to none, & see if it still acts crazy. You may need to log out & back in or reboot.
Then some hardware info would be helpful. Need to know what you're working with.
Some stuff just doesn't play nice.

---

### Post by The Populist on 2009-08-03
Ok, I've tried setting effects to "none", it didn't help.

Here are a few things:
My system is a compaq presario AMD 3300 prcoessor, NVIDIA graphics and 512 mb of ram. 

This problem came up after the last update.

---

### Post by The Populist on 2009-08-03
Update manager has not had anything new since I updated a few days ago, which is strange. And, when I open update manager, the screen goes crazy. Switching between workstations and stuttering.

I don't know if that means anything.

...

---

### Post by The Populist on 2009-08-03
Ok, I  just did a complete re-install, updated, and the problem is still there. There is something wrong with workspace switcher 2.26.0 on my computer. Apparently it is an applet, but I can't find it in synaptic.

Can someone tell me how to find and remove this program, it is wonking out my PC. 

Let me be clear, a box appears in the center of my screen. The box has two rectangles, and arrows appear erratically in the boxes. When this happens, my computer switches workspaces. This occurs even when I have only one workspace available.

...

---

### Post by braete on 2009-08-03
did you do a clean install or did you reinstalled over ?
and ,b4 applying updates, the jumping from one workspace to an other occurred ?

---

### Post by The Populist on 2009-08-03
Ok, first I did a clean install with no updates. The damn screen kept flickering. Then I broke out my older machine that had jaunty installed, but the first distribution. Are you ready, after a few minutes, the same thing happened.

What did the two machines have in common? I restore my firefox sessions, and both machines had the **Cyberpower** web page saved. I remember when I had ubuntu 8.04, I could not view the page. It just got wonky and wouldn't load.

In jaunty, it loads but parts of the page stutter. I think there is some part of that page that just disagrees with my system.

---

### Post by braete on 2009-08-03
ok, this is strange!

so you have 2 pc that act strange with almost the same software env.
i dont think that it is posibile for a page to afect in any way the os without sudo permission

i just had a very strange idea.
i dont know how ubuntu/the kernel communicates with the hardware part but i know that xorg asks, from the monitor, info about it's physical size(that causes the bug with large letters in the login screen). what if there is ur problem? the monitor reports wrong info to the OS due to excessive heating ?
you said that on the other machine it started **after** a few minutes.
this a long, LONG, **LONG** shot and i dont even know if that is the deal, but ...

or excessive heating of other computer parts (the southbridge, the chip that runs i/o, the video card)

anyway i still thick that it's compiz's fault.
run a file system check (sudo shutdown -rf 0, i think)
completely remove compiz (sudo apt-get remove --purge compiz)
i dont know what does "--purge" remove, so to be sure go to home folder and open .gconf/apps and delete compiz folder

---

### Post by The Populist on 2009-08-03
Well, I am completely stumped. I've been troubleshooting all night and I can't figure out what the hell is going on. This is a brand new install of jaunty, and I only updated security programs, not recommended updates. 

My windows still stutter up and down, but the problem seems to be going away since closing the Cyberpower page. I'm not sure that was, or is, the problem. But I can't make sense of it any other way.

If it gets worse or goes away I'll post again.

Thanks for all the replies.

---

