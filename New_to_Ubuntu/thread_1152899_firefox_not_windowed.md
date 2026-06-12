---
title: "firefox not windowed"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-05-08
Since i rebooted for some reason firefox is not windowed there is no title bar with the minimize,ect buttons at all how do i get it back i am running jaunty if the makes a difference.

Trinidad

---

### Post by suitedaces on 2009-05-08
Is it only firefox or other applications? And do you have compiz enabled?

---

### Post by freak42 on 2009-05-08
try pressing F11 within the firefox window.

or else you can try deleting your settings in the ~/mozilla/firefox folder (warning all your firefox settings, bookmarks, addons, cookies , passwords,... get lost!).

hth

---

### Post by trinidadflores on 2009-05-08
> **suitedaces said:**
> Is it only firefox or other applications? And do you have compiz enabled?

i just noticed that its all and not just firefox.  and not i dont have compiz enabled not even installed.

---

### Post by suitedaces on 2009-05-08
Give it a while to see if someone has a more straightforward fix, but try entering

sudo apt-get install compizconfig-settings-manager

in the terminal, then when it's installed, go System > Preferences > compiz config settings manager, then go to effects and make sure window decoration is selected.

Wait a while before you do that though, there may be a better way I'm unaware of.

---

### Post by trinidadflores on 2009-05-08
> **suitedaces said:**
> Give it a while to see if someone has a more straightforward fix, but try entering

sudo apt-get install compizconfig-settings-manager

in the terminal, then when it's installed, go System > Preferences > compiz config settings manager, then go to effects and make sure window decoration is selected.

Wait a while before you do that though, there may be a better way I'm unaware of.

that didn't work anyone else have an idea of what i can do?

Trinidad

---

### Post by Niniel on 2009-05-08
Looks like you don't have a window manager.
Run "metacity" (alt-F1 or alt-F2, I think, will bring up the Run dialog).
Then add "gnome-wm" to your startup applications. That cured it for me.

---

### Post by trinidadflores on 2009-05-08
> **Niniel said:**
> Looks like you don't have a window manager.
Run "metacity" (alt-F1 or alt-F2, I think, will bring up the Run dialog).
Then add "gnome-wm" to your startup applications. That cured it for me.

I just tried that and nothing happened.

---

### Post by Niniel on 2009-05-08
You didn't get the run dialog, or running metacity didn't fix it for you?

---

### Post by trinidadflores on 2009-05-08
"Looks like you don't have a window manager.
Run "metacity" (alt-F1 or alt-F2, I think, will bring up the Run dialog).
Then add "gnome-wm" to your startup applications. That cured it for me."

I pulled up the run prompt (alt+f2) and tried to run metacity but it would not.

---

### Post by supermooshman on 2009-05-08
sounds like you have the same thing I have, in my thread is a link to the bug (and someone who explains it, because I couldn't figure it out how to fix it)

anyway, I am currently not in the vicinity of my ubuntu, so I cannot confirm if it works or not, if it does, I would appreciate it if you could let me know

Good luck!

[http://ubuntuforums.org/showthread.php?t=1153128](http://ubuntuforums.org/showthread.php?t=1153128)

---

### Post by trinidadflores on 2009-05-08
The above  post reminded me to mention that i am running the 64 bit version of jaunty.

---

### Post by fooman on 2009-05-08
try the alt-f2 again,  this time type or copy/paste the following into it:

```
metacity --replace
```then click run.

hope that helps.

---

### Post by trinidadflores on 2009-05-08
> **fooman said:**
> try the alt-f2 again,  this time type or copy/paste the following into it:

```
metacity --replace
```then click run.

hope that helps.

no go nothing at all

---

### Post by Prince Valiant on 2009-05-08
Hey-

I had the same problem for a while, and I would simply press F11 to bring Firefox to fullscreen, then again and it would be windowed.  The problem disappeared a while ago, and I'm not sure what fixed it.  Maybe a couple of restarts?  I'm running Intrepid Ibex (8.10).

Hope this helps!

---

### Post by Pjotrovitz on 2009-05-08
Well, I would install fusion-icon (sudo aptitude install fusion-icon) and then run it (fusion-icon). This creates an icon in your task bar that lets you select (by right-clicking it) the window manager to use. Try the different settings out. Most likely your window manager is borked in some way.

---

### Post by trinidadflores on 2009-05-08
> **Prince Valiant said:**
> Hey-

I had the same problem for a while, and I would simply press F11 to bring Firefox to fullscreen, then again and it would be windowed.  The problem disappeared a while ago, and I'm not sure what fixed it.  Maybe a couple of restarts?  I'm running Intrepid Ibex (8.10).

Hope this helps!

no the f11 does not get the bar back.  I have tried that.  thanks though.

---

### Post by trinidadflores on 2009-05-08
I am not sure what to do now i have tried all of the sugestions that was posted to no avail.  now i am contemplating reinstalling.  is that whats best to do? If i do reinstall what version would be the best to use i have a processor that is a dual core and have 4 gb of ram?  i have both 9.04 32 and 64 bit versions.


trinidad

---

### Post by durand on 2009-05-08
You could try creating another user (Systenm > Administration > Users and Groups) and log in as that. See if the problem still occurs. If not, then its a configuration problem, otherwise, its a software problem.

---

### Post by Sir Jasper on 2009-05-08
Hi,

As a test, in Firefox, if you go to View then tempoarily disable one or more toolbars - can you then see the Title bar?

If so perhaps you need to adjust you screen height?

My regards

---

### Post by Didius Falco on 2009-05-08
Did you do anything (install a video driver,for example) right before this started happening? Problems often don't show up until after you've logged out and back in or rebooted.

---

### Post by Zoowey on 2009-05-09
Try rebooting again or just logout, sometimes programs fail to load correctly at startup.

---

### Post by DaveySpeedstar on 2009-05-25
It might not be much help to you, but this happened to me a couple of days ago after I'd done a re-install.  

I assumed that the files hadn't copied properly, so I re-installed again and everything was OK

---

### Post by mistypotato on 2009-10-12
Kinda getting this same issue after updating my system yesterday.

Now, Firefox opens in this Full Screen kind of mode and there is no minimize maximize or close buttons, however, F11 DOES work and after pressing F11 FF goes to full screen (with the buttons) and then pressing F11 again returns FF to what I call "normal" meaning WITH the buttons that I expect.

Also, the top bar that says Firefox is missing when I first open Firefox along with the buttons.

---

