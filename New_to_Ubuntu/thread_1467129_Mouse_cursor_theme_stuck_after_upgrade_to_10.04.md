---
title: "Mouse cursor theme stuck after upgrade to 10.04"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Andy06 on 2010-04-30
Upgrading to 10.04 has got mu cursor stuck as a particular themed cursor in the extra extra large size (comixcursors black in the largest size). I cannot change it. I can uninstall the theme in which case it goes back to the standard white but I cannot select comixcursors blue standard or anything.

Whats going wrong?
Thanks

---

### Post by madjr on 2010-04-30
thats weird
anyone else has reported the bug on launchpad?

---

### Post by privateabstract on 2010-05-01
I have exactly the same problem. The cursor theme is selected in System -> Preferences -> Appearance, however it isn't working on ***most*** windows and the desktop. What is weird is that I have noticed the cursor theme is working in other windows, such as Firefox and Thunderbird ones, but the second I move back onto the desktop it reverts back to the default, white cursor.

---

### Post by AndyP79 on 2010-05-01
I got this issue also after switching to 10.04
Figured it will be a while before this is fixed with an update

---

### Post by miles916 on 2010-05-01
Hi guys!

i remember encountering this on karmic, but i couldnt for the life of me remember how i had solved it (i only remember after logging out, it suddenly worked). 

now, after upgrading, it suddenly happened again. 
so after trying all manner of solutions, here is the one that worked for me: 

edit the file "index.theme" in "/usr/share/icons/default":

```
[Icon Theme]
Inherits=**Your-Cursor-Theme**
```I had "DMZ-White" in there, which is why (i assume) whenever my cursor hit the desktop, it defaulted back to it, and didnt stay with the one i had wanted (comix green). 

a few other things you can try: 

_gconf-editor:_
desktop-->gnome-->peripherals-->mouse-->**cursor_theme **&** cursor_size**
apps-->compiz-->general-->allscreens-->options-->**cursor_theme **&** cursor_size**


good luck!

---

### Post by CEB2nd on 2010-05-01
Having the same problem here, along with disappearing
windows title bars and a scroll problem with the Preferences
menu under System.  It looks like [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/459647") knows
about the pointer bug.

---

### Post by bgreenaway on 2010-05-15
Thanks miles916. That worked for me.

---

### Post by lint4690 on 2010-06-08
> **bgreenaway said:**
> Thanks miles916. That worked for me.


me too!

---

### Post by Liii on 2010-07-28
But what about the size? Has anyone been able to set the size of the cursor to anything other than the default under compiz?

These two suggested settings had no effect for me:

desktop-->gnome-->peripherals-->mouse-->**cursor_theme **&** cursor_size**
apps-->compiz-->general-->allscreens-->options-->**cursor_theme **&** cursor_size**

---

### Post by Liii on 2010-07-28
Also, is it wise to do this:
> **miles916 said:**
> edit the file "index.theme" in "/usr/share/icons/default"
/usr/share/icons/default/index.theme is a link to /etc/alternatives/x-cursor-theme that is also a link to for example /usr/share/icons/DMZ-White/cursor.theme.

Wouldnt it be a better solution to change /etc/alternatives/x-cursor-theme to link to the right cursor theme? That is /usr/share/icons/DMZ-Black/cursor.theme in my case. That seems to work too.

---

### Post by jperelli on 2010-07-28
> **miles916 said:**
> Hi guys!

i remember encountering this on karmic, but i couldnt for the life of me remember how i had solved it (i only remember after logging out, it suddenly worked). 

now, after upgrading, it suddenly happened again. 
so after trying all manner of solutions, here is the one that worked for me: 

edit the file "index.theme" in "/usr/share/icons/default":

```
[Icon Theme]
Inherits=**Your-Cursor-Theme**
```I had "DMZ-White" in there, which is why (i assume) whenever my cursor hit the desktop, it defaulted back to it, and didnt stay with the one i had wanted (comix green). 

a few other things you can try: 

_gconf-editor:_
desktop-->gnome-->peripherals-->mouse-->**cursor_theme **&** cursor_size**
apps-->compiz-->general-->allscreens-->options-->**cursor_theme **&** cursor_size**


good luck!
THANKS!! it works perfectly!!

---

### Post by Gaygerbil on 2010-08-15
After further reexamination I realized this only changed my theme to a dark mouse theme (I don't even think this was DMZ-Black like I wanted). I noticed this when trying to change my theme to redglass cuz I was testing it. It wasn't working.

You have to put the theme you want manually in, it still however doesn't change the mouse pointer size glitch.

All the other cursors change sizes (i.e I-beam pointer, Link pointer, Loading pointer) except the actual mouse cursor. Still though this is a pretty good fix considering I couldn't get the default pointer to change which now it does it just won't change size. Anyone know where we can find the config file that has the mouse cursor's size in it?

---

### Post by roobie on 2010-08-16
> **miles916 said:**
> 

edit the file "index.theme" in "/usr/share/icons/default":

```
[Icon Theme]
Inherits=**Your-Cursor-Theme**
```


good luck!

Thank you miles916, that was a quick and seemingly working fix! :)
Albeit, I'm a bit dissappointed that it does get changed automagically when picking cursor theme in appearence-settings.

---

