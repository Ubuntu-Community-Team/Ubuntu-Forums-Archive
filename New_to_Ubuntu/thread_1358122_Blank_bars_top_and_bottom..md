---
title: "Blank bars top and bottom."
date: 2009-12-18
forum: New to Ubuntu
---

### Post by benleedy on 2009-12-18
I installed the latest updates with the update manager, then restarted and when it booted up I find that the bars on top and bottom are blank. Right clicking does nothing. When I plug in a thumb drive the icon appears, but if I try to open it I get a blank window. When I try to close the window, it tells me it isn't responding so I have to force quit it. When I try to restart or shut down, it tells me the Panel and Update Notifier are not responding and asks me if I want to logout anyway. Anyone have an idea what's going on?

---

### Post by unmole on 2009-12-18
Try this...
Open a terminal and type
 ```
sudo debconf gnome-panel
 sudo killall gnome-panel
```

---

### Post by jamieleshaw on 2009-12-18
press alt+f2 then in  the run box type gnome-terminal.
In the terminal type 'rm -f ~/.gconf/apps/panel'
then 'sudo reboot'

---

### Post by benleedy on 2009-12-18
Alt+F2  does nothing. Ctrl+Alt+F2 takes me to a command prompt. I used those commands there and nothing happened.

---

### Post by jamieleshaw on 2009-12-18
Well, go into recovery mode then select drop to root shell.
and type 'rm -f /home/your_username_here/.gconf/apps/panel'
then restart and load up like normal

---

### Post by benleedy on 2009-12-19
> **jamieleshaw said:**
> Well, go into recovery mode then select drop to root shell.
and type 'rm -f /home/your_username_here/.gconf/apps/panel'
then restart and load up like normal

It said it couldn't delete it because it is a folder. I'm about ready to call it a loss and start over, reformat the HDD.

---

### Post by Gazneth on 2009-12-19
Just a few commands should repair your panels. If you have the time sometimes it is worth learning to fix the problem rather than the nuclear option. Try these commands and see if they help, you do not need to be in recovery mode, probably better if you aren't.
```
gconftool --recursive-unset /apps/panel
```
```
rm -rf ~/.gconf/apps/panel
```
```
pkill gnome-panel
```
This should reset your panels to their default configuration.The last post command also should have worked. Maybe you left the ' after panel it doesn't need to be there.

---

### Post by jamieleshaw on 2009-12-19
Just type what is below
rm -f ~/.gconf/apps/panel
then restart

---

### Post by jamieleshaw on 2009-12-19
It's to my understanding that they can't use the panels to get to the terminal, that's why I recommended recovery mode. There's always Alt+F2 to open run then type 'gnome-terminal'

---

### Post by benleedy on 2009-12-19
> **jamieleshaw said:**
> Just type what is below
rm -f ~/.gconf/apps/panel
then restart

It still says it can't remove it because it is a folder. How do I open a terminal if Alt+F2 does nothing? I have been pressing Ctrl+Alt+F2 and entering my commands there.

---

### Post by jamieleshaw on 2009-12-19
rm -rf ~/.gconf/apps/panel
Try that.

---

### Post by benleedy on 2009-12-19
> **jamieleshaw said:**
> rm -rf ~/.gconf/apps/panel
Try that.

Exactly where do I type this? Do I pres Ctrl+Alt+F2, enter my username and password, then type it?

---

### Post by jamieleshaw on 2009-12-19
> **benleedy said:**
> Exactly where do I type this? Do I pres Ctrl+Alt+F2, enter my username and password, then type it?
Yes, Do that.

---

### Post by benleedy on 2009-12-20
> **jamieleshaw said:**
> rm -rf ~/.gconf/apps/panel
Try that.

Okay, I tried that and my immediate result was just another prompt, no messages of any type. I then pressed Ctrl+Alt+Delete to restart. When Ubuntu booted up again nothing appeared to have changed.

---

### Post by benleedy on 2009-12-20
BTW, I do appreciate your taint the time to help. I would love to learn everything about programming and Linux and Ubuntu, but I just don't have the time. I thought replacing XP with Ubuntu on my laptop would make it run better and be more stable, but apparently not.

---

### Post by ForgivenByJC on 2009-12-22
benleedy, you are running into several different problems here.  For now, let's try to just get you back up and running, then we can cover the different aspects of things.

The "Ctrl+Alt+F2" terminal you have been using before will work just fine.  Can you post the output of these commands which will help us understand what is going on better.  Login to the "Ctrl+Alt+F2" terminal (or the SSH terminal, explained below), then type these commands and post there outputs.

```
whoami
sudo whoami
uname -a
lsb_release -a
gnome-about --gnome-version
sudo apt-get -f install
```

***Using SSH to make things easier***
This will be easier if you can use SSH from another computer.  If you are not familiar with SSH, you must be on the same network--so access from a computer not in the same building is not likely to work.  Your problem computer with Ubuntu, may not have this installed.  To install it, use this command in terminal.```
sudo apt-get install openssh-server
```

If you are running Windows on another computer, use a free program called PuTTY. ([http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe))  In the "Host _N_ame (or IP address)" field type the computer name (or IP address, if you know it) of the computer with problems.  Then click "_O_pen".  If you get "PuTTY Security Alert" dialog which starts out saying "The server's host key is not cached...," then click "_Y_es".  Then login as usual.  This way you can use copy and paste features.  

PuTTY's copy and paste is weird, highlighting text in PuTTY will automatically copy it to clipboard and right clicking your mouse in PuTTY will paste from clipboard.  Copy and paste in other programs will not be affected by this, that is highlight text in PuTTY to copy and press Ctrl+V in Internet Explorer (IE) to paste.  And, press Ctrl+C in IE to copy and right click in PuTTY to paste.  [http://the.earth.li/~sgtatham/putty/0.52/htmldoc/Chapter3.html](http://the.earth.li/~sgtatham/putty/0.52/htmldoc/Chapter3.html)
***End of SSH section***

---

### Post by benleedy on 2009-12-22
Oh, my bad. I got fed up and went with the "nuclear option". Problem solved.

---

### Post by ForgivenByJC on 2009-12-22
I understand.  Learning Ubuntu has been quite a time-sink for me, so if I can help someone else out, I will.

Look into the SSH option so you can have access to your computer if something else goes wrong.

For the record, [this is what was happening when you enter Ctrl+Alt+F2]("http://ubuntuforums.org/showthread.php?t=833765#3").

---

### Post by benleedy on 2009-12-22
I really wish I had the time to learn Linux, but it just isn't gonna happen anytime soon. Too many other priorities. I really appreciate the help. Maybe next time I'll have the patience to work through the problem, but I didn't have any info on that computer (it has proved unreliable) so I didn't lose anything.

---

