---
title: "Icons to Close, Minimize, Maximize missing!"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by EddieNYC on 2010-08-22
Hi all.

I'm not sure how I did this but the icons to close, minimize, and maximize in windows no longer load by default. 

The only way I have found how to get these back is to go into System>Appearance>Visual Effects and choosing one of the effects. These changes do not stick as whenever I reboot I am back to where I started.

I have searched high and low but can't seem to find how to correct this behavior.

Any help is appreciated.

Running Ubunto 10.4 LTS.

---

### Post by narendraD on 2010-08-23
Not sure what you have done. But a change of theme should bring back the icons. Right click on the desktop nad select Change Desktop Background. In the resulting Window, select the Theme Tab and select a Different theme. This should bring back all icons, albeit in a different theme. You can then change the theme to something you prefer.

---

### Post by venturax on 2010-08-23
if all is screwed up, you could try to type
```
metacity --replace
```
to see if that will fix the problem.

---

### Post by Paqman on 2010-08-23
> **venturax said:**
> if all is screwed up, you could try to type
```
metacity --replace
```
to see if that will fix the problem.

Yep, if you're using desktop effects you could also try:
```
compiz --replace
```

If the problem persists then you might want to temporarily switch on Apport by entering this in a terminal:
```
sudo service apport start force_start=1
```

The when your window decorations crash again Apport will automatically report a bug for you. If the problem is a known one the existing bug report might have a workaround for you.

---

### Post by venturax on 2010-08-24
After I updated til 10.04, I lost all window borders, which was a strange phenomenon, but the fix I mentioned, did the trick. The problem reappeared after reboot / re-login.

The only workaround was to add the metacity --replace to startup applications to prevent the issue to re-appear. Strange why it happened in the first place :confused:

---

### Post by EddieNYC on 2010-08-24
> **venturax said:**
> After I updated til 10.04, I lost all window borders, which was a strange phenomenon, but the fix I mentioned, did the trick. The problem reappeared after reboot / re-login.

The only workaround was to add the metacity --replace to startup applications to prevent the issue to re-appear. Strange why it happened in the first place :confused:


Strange. Now that you mention it, this happened shortly after upgrading to 10.04 as well which was not too long ago. Thanks for the fix. I also had to had the command to my startup applications as it would also lost the setting upon reboot. Adding it solved this.

Any idea what is causing this?

---

### Post by Guilden_NL on 2010-08-24
No idea from me.

But you may want to install Ubuntu Tweak to change the settings around.  I moved my buttons to the right using Tweak.

[[COLOR="Blue"]http://ubuntu-tweak.com[/COLOR]]("http://ubuntu-tweak.com/")

---

### Post by Zorgoth on 2010-08-25
What about gtk-window-decorator --replace?

You could also try using emerald instead of gtk-window-decorator.  I find the Glassbuntu theme for emerald very nice and well done and it works great with compiz and a dark colored Ubuntu theme.

---

### Post by jazzerit on 2010-08-25
whenever I have window borders dissappear, which has happened, I use compiz-fusion icon (which can be installed with sudo apt-get install fusion-icon) which I have added to the startup menu. To get the borders back, right-click on it's icon and select reload window manager.

---

### Post by venturax on 2010-08-30
One problem persists though, as mentioned. It seems that all changes to themes, effects etc are "forgotten" after reboot of the machine, which leads me to think of a permission problem. I tried delete the .gnome, but it didn't fix the issue :-(

---

### Post by J@n on 2010-08-30
Sorry to barge in to this thread but I have a similar issue:(

Somewhere last week I lost my window borders. Not sure if this was caused by an upgrade.

When my system starts, it starts without borders. I can restore the borders by going to System > Preferences > Appearance and select "Normal" in the visual effects tab. After some time Ubuntu tells me the following: "Desktop effects could not be applied". After that the borders return and I have no more problems during that session:confused: After reboot however I have to go through this procedure again. Slightly annoying!

I am using Ununtu 10.04 LTs 32 bit. I have an ATI HD 4350 graphics card which I have updated to the latest release from AMD after this problem occurred. Mind you, updating did not solve this problem.

I'd hate to have to add compizz or metacity to my start-up applications as it did work for about a week ago.

Any clue to the cause of this would be greatly appreciated:)

Greetz,

J@n

---

### Post by topet2k12001 on 2010-10-31
Hi Friends,

Just wanted to share: I did a fresh install of Ubuntu 10.10 by the way. I have an NVIDIA 9500GT Graphics Driver. In Ubuntu 10.04 I didn't have any problems running Compiz without losing my minimize/maximize/close buttons, but your issue is the same that I have experienced with Ubuntu 10.10.

I tried following the instructions from the previous page (type in gtk-window-decorator --replace from the Terminal). I got a notification that i had one component that was not yet installed (compiz-gnome) so I installed it. After doing so, I was able to see the minimize/maximize/close buttons again, but the color doesn't seem right (looks transparent). So I tried to run the gtk-window-decorator --replace command again, and I was able to get the said buttons to conform to the current theme that I was using. Not sure if this means anything to you but hope this one helps. :)

One thing I noticed is that after doing all of these, I lost the ability to switch active windows (Alt+Tab).

---

