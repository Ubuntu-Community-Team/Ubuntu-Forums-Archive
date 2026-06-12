---
title: "Mouse pad problem"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by Gulfvet91 on 2009-09-19
How do change settings on my mouse pad?  It is set for tap=click and I hate that.

---

### Post by tacantara on 2009-09-19
Check out Preferences > Mouse.  Click on the Touchpad tab.  That should resolve your problem.

---

### Post by kerry_s on 2009-09-20
> **tacantara said:**
> Check out Preferences > Mouse.  Click on the Touchpad tab.  That should resolve your problem.

:lolflag: if only he was using gnome.

---

### Post by tacantara on 2009-09-20
> **kerry_s said:**
> :lolflag: if only he was using gnome.

Oops!  Thanks for catching that kerry_s.  I should know better than to post replies after I've taken my pain medication (I had knee surgery recently).

---

### Post by kerry_s on 2009-09-20
> **tacantara said:**
> Oops!  Thanks for catching that kerry_s.  I should know better than to post replies after I've taken my pain medication (I had knee surgery recently).

:lolflag: i use to do that, my old doc use to give me all kinds of meds. my new doc gives me just what i need to treat the problem. get well soon, try to stay off that knee. :)

---

### Post by Gulfvet91 on 2009-09-20
> **tacantara said:**
> Check out Preferences > Mouse.  Click on the Touchpad tab.  That should resolve your problem.
I don't have any applications named Preferences.  I have looked and looked and it's just not there.  Might it be in synaptic, still uninstalled?

---

### Post by Gulfvet91 on 2009-09-20
So much for that!  I installed an application called preferences but it had nothing to do with my mouse pad or anything else I need help with.

---

### Post by Gulfvet91 on 2009-09-20
I can't even use ghelp!  It's asking me which application I want to open the file and I have no idea which one to use.

---

### Post by ex-wirecutter on 2009-09-20
I just tried " system-preferences-mouse-touchpad " and it worked for me , I dont like touch click either .

---

### Post by Gulfvet91 on 2009-09-20
> **ex-wirecutter said:**
> I just tried " system-preferences-mouse-touchpad " and it worked for me , I dont like touch click either .
I don't have Preferences as an item on my System dropdown.

---

### Post by Gulfvet91 on 2009-09-20
> **ex-wirecutter said:**
> I just tried " system-preferences-mouse-touchpad " and it worked for me , I dont like touch click either .
I have an item called Mouse under Settings but it doesn't list my touchpad as something I can modify.

---

### Post by Tony.B on 2009-09-20
Sorry to butt into your conversation, but I just clicked *System > Preferences > Mouse*. 
I got a small screen labelled *Mouse Preferences*.
There are 3 tabs along the top.
The 3rd tab is labelled *Touchpad*.
The 2nd item down says *Enable Mouse Clicks with TouchPad*.
If you un-tick the box, you won't be able to click by knocking the touchpad.
Does this help?

---

### Post by kerry_s on 2009-09-20
people! he is not using gnome! he does not have that option! xfce4 is not the same as gnome.

Gulfvet91, in xfce4 there is no easy way.
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by Gulfvet91 on 2009-09-21
Kerry,
             First of all, thanks for having my back!  I was about to lose my mind from getting instructions for Gnome when I'm in Jackalope.   Second, the link you posted tells about how to do this with SHMconfig in GNome and how to do things in Kubuntu but there is nothing about Xubutnu 9.04.  My Synaptic does not list SHMconfig or synclient or syndaemon.  Which should I use for 9.04?  Do I need to do an apt-get to install it?

---

### Post by kerry_s on 2009-09-21
> **Gulfvet91 said:**
> Kerry,
             First of all, thanks for having my back!  I was about to lose my mind from getting instructions for Gnome when I'm in Jackalope.   Second, the link you posted tells about how to do this with SHMconfig in GNome and how to do things in Kubuntu but there is nothing about Xubutnu 9.04.  My Synaptic does not list SHMconfig or synclient or syndaemon.  Which should I use for 9.04?  Do I need to do an apt-get to install it?

the instructions are the same for everything. so for you, it would be:

press-> **alt+f2**
type-> **gksudo mousepad /etc/hal/fdi/policy/shmconfig.fdi**
copy this & paste it in->
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
    </match>
  </device>
</deviceinfo>
```

then reboot.
after you get back you need to grab a gui to use, install gsynaptics:
in teminal:
**sudo apt-get install gsynaptics**
or
use synaptic package manager to install it.

good luck

---

### Post by Gulfvet91 on 2009-09-21
Kerry,
                I did all that and I still don't see any way to modify my touchpad settings.

---

### Post by Gulfvet91 on 2009-09-23
Has everyone decided my problem is fixed?  It ain't!

---

### Post by kerry_s on 2009-09-23
> **Gulfvet91 said:**
> Has everyone decided my problem is fixed?  It ain't!

did you install "gsynaptics"?
did you try running it? if its not in the menu: alt+f2, type> gsynaptics

---

### Post by Gulfvet91 on 2009-09-24
That worked but it doesn't seem to have saved.  It's back to doing tap clicks.  This seems to be an ongoing problem of not saving settings,  I'm having the same problem with alsamixer and WINE, too.

---

### Post by kerry_s on 2009-09-24
> **Gulfvet91 said:**
> That worked but it doesn't seem to have saved.  It's back to doing tap clicks.  This seems to be an ongoing problem of not saving settings,  I'm having the same problem with alsamixer and WINE, too.

that don't sound good, check your startup see if it is in there.
i'm using it on lenny, i noticed it put a startup so the settings would be applied at startup.

here's the settings just in case you need to add it:

---

### Post by Gulfvet91 on 2009-10-14
Kerry,
             I had to reload my system and I am trying to do what you showed me to fix my mousepad problem again.  I did the alt+F2 and the shmconfig command.  The system didn't show me anywhere to put the mass of code.  What am I doing wrong?

---

### Post by kerry_s on 2009-10-14
> **Gulfvet91 said:**
> Kerry,
             I had to reload my system and I am trying to do what you showed me to fix my mousepad problem again.  I did the alt+F2 and the shmconfig command.  The system didn't show me anywhere to put the mass of code.  What am I doing wrong?

when you do this part:

```
press-> alt+f2
type-> gksudo mousepad /etc/hal/fdi/policy/shmconfig.fdi
```

your creating the file to put:

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
    </match>
  </device>
</deviceinfo>
```

that in, theres nothing there by default.

---

### Post by Gulfvet91 on 2009-10-15
Thanks, Kerry!  I found the problem.  There was a space missing from the first command line.

---

