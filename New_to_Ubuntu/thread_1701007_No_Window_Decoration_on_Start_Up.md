---
title: "No Window Decoration on Start Up"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by Roger Allott on 2011-03-05
I've had this problem ever since I upgraded to 10.04, and it has persisted now that I've eventually upgraded to 10.10. It's a right pain in the butt.

When I boot ubuntu, all applications are without any window decoration at all, meaning that I cannot move windows and in some cases, cannot quit applications.

To work around this problem, what I've found gets the window decoration back is if I run System>Preferences>Appearance.

In the 4th tab (Visual Effects) I find that the first option (None) is selected, for some bizarre reason. So, I click on Custom, and it goes off to hunt for drivers, which it invariably finds, and then after a few seconds my window decoration reappears with a dialog asking me whether I'd like to keep these new settings. I always answer 'yes'.

But that seems like a really round-the-houses way of doing stuff that ought to be automatic, and certainly **was** automatic up to 9.10.

So, how do I make my window decoration (and custom effects) automatic again?

---

### Post by CaptainMark on 2011-03-06
hmmm, sounds like a compiz issue, im not too sure, perhaps someone with more knowledge can help you fix the root of the issue but as a workaround you could add 

metacity --replace

to the startup applications list and this should give the window manager a kick start on login

---

### Post by Dutch70 on 2011-03-06
Please post the output of...

```
lspci | grep VGA
```

---

### Post by Roger Allott on 2011-03-06
> **Dutch70 said:**
> Please post the output of...

```
lspci | grep VGA
```

```
me@me-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
```

---

### Post by Dutch70 on 2011-03-06
Try this...Please let us know if it works. 

 1) After install, work in a tty (Control + Alt + F1). and remove the following

Code:

```
sudo aptitude remove compiz compiz-core
```

2) After that, reinstall/install the followings

Code:

```
sudo apt-get install compiz compiz-core fusion-icon emerald simple-ccsm
```

3) Back to the graphic environment (Ctrl + Alt + F7) and run Compiz Fusion Icon (Apps -> System tools -> Compiz Fusion Icon.

4) The compiz fusion icon should appear in your notification bar, there, right click -> Compiz options -> Indirect Rendering

5) Select Window Manager -> Compiz<

6) Run compiz icon at the start-up:

System -> Preferences -> Start up apps -> Add
Name: Compiz Fusion Icon
Command: fusion-icon -f
Comment:

7) Reboot

Once again in the desktop compiz should work properly. Configure it with

Code:

```
simple-ccsm
```

source: [http://ubuntuforums.org/showthread.php?t=1307001&page=3]("http://ubuntuforums.org/showthread.php?t=1307001&page=3")

---

### Post by Roger Allott on 2011-03-06
I haven't done the full uninstall-reinstall of compiz (yet), but I did what was suggested below and it seems to have done the trick.

> **CaptainMark said:**
> 
metacity --replace

to the startup applications list and this should give the window manager a kick start on login

However, if the issue re-emerges, I shall do the full blitz as suggested by Dutch70.

Thanks for your help!

---

### Post by Dutch70 on 2011-03-06
> **Roger Allott said:**
> I haven't done the full uninstall-reinstall of compiz (yet), but I did what was suggested below and it seems to have done the trick.

However, if the issue re-emerges, I shall do the full blitz as suggested by Dutch70.

Thanks for your help!

 Glad you found something that worked for you.

---

### Post by JamesNeko on 2011-03-07
I've had the same trouble, and have found this advice on [https://help.ubuntu.com/community/CompositeManager/CompizFusion#Troubleshooting](https://help.ubuntu.com/community/CompositeManager/CompizFusion#Troubleshooting)

> If you ran nvidia-settings, then your xorg.conf lost some info. To fix your compiz window decorations (titlebars) with an nVidia graphics card, run

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

then restart X by logging out and back in again and selecting "Restart X Server" from the login menu. 

I'm about to try this right now. It's an intermittent problem, so I can't guarantee this'll have fixed it until at least half a dozen restarts later, which could be a while...

**EDIT:** Well, seems to work for me right now. There wasn't a "Restart X Server" option on the login screen but luckily ctrl-alt-backspace still works... for me anyway. YMMV.

---

