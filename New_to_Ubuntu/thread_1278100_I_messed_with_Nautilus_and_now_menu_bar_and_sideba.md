---
title: "I messed with Nautilus and now menu bar and sidebars are gone..."
date: 2009-09-29
forum: New to Ubuntu
---

### Post by legolas_w on 2009-09-29
Hi
I do not know what I done with Nautilus and now its menu bar is gone and also the sidebars.

I was unable to find any shortcut  to make the menus and the side bar be shown again. Please let me know if you know how to restore it to normal GUI.

PS: It might be because of the new Nautilus update that I installed trough the update manager.

Here is an image showing hot it look now:
[IMG]http://img12.imageshack.us/img12/4253/screenshot001gq.png[/IMG]
Thanks.

---

### Post by ankspo71 on 2009-09-29
Hi,
That looks really nice, but I can see it being a problem. You might find the settings you need in the Gnome Configuration Editor. In the terminal type this:
```
gconf-editor
```
When it opens, go to apps > nautilus > preferences.
I think the entries you are looking for are "start with...."
Hope this helps,
James

---

### Post by BugBuster on 2009-09-29
Hi..
To restore nautilus preferences to the default..i.e the ones that ship with ubuntu delete the /home/*yourusername*/.gconf/apps/nautilus folder and then log out and login again.

Everything will be restored to defaults...

---

### Post by kerry_s on 2009-09-29
are you using karmic? i read some where they were going for that look.
this is the only page i could find in my history, i must have cleared the rest: [http://webupd8.blogspot.com/2009/07/install-simplified-nautilus-for-ubuntu.html](http://webupd8.blogspot.com/2009/07/install-simplified-nautilus-for-ubuntu.html)

---

### Post by legolas_w on 2009-09-29
> **ankspo71 said:**
> Hi,
That looks really nice, but I can see it being a problem. You might find the settings you need in the Gnome Configuration Editor. In the terminal type this:
```
gconf-editor
```
When it opens, go to apps > nautilus > preferences.
I think the entries you are looking for are "start with...."
Hope this helps,
James

Thanks everyone and thank you James.
I was able to restore the side bar but the menues are still gone.
I was unable to find any entry for menu bar in the address you gave  me.

Thanks

---

### Post by jolsz on 2009-09-29
Do you have third party repository enabled in your sources (e.g. using ubuntu-tweak?) 
Seems like simplified version of Nautilus from Gloobus PPA.
Maybe this thread is something interesting for you:
[http://ubuntuforums.org/showthread.php?t=828774&page=51](http://ubuntuforums.org/showthread.php?t=828774&page=51)

Perhaps alt+m will help to unhide menu bar ;-)

---

### Post by poxix on 2009-12-05
Hi.:KS:KS:KS

I too was the same misfortune. And coincidentally after some days I solved.

In the lower panel of the desktop I added a tool called "Global Menu Panel Applet" and it added the menu of nautilus panel below ... curious. With the right mouse button on the tool I called the property window and I unchecked the option "Enable menu for GTK applications".
I closed the property and it gave me a baloon error. I removed the tool from the bottom panel and ... healed.:D

I hope it works to each other.;)

Bye:popcorn:

---

### Post by asmeetkumar on 2009-12-06
> **poxix said:**
> Hi.:KS:KS:KS

I too was the same misfortune. And coincidentally after some days I solved.

In the lower panel of the desktop I added a tool called "Global Menu Panel Applet" and it added the menu of nautilus panel below ... curious. With the right mouse button on the tool I called the property window and I unchecked the option "Enable menu for GTK applications".
I closed the property and it gave me a baloon error. I removed the tool from the bottom panel and ... healed.:D

I hope it works to each other.;)

Bye:popcorn:

That worked like a charm......
Thank you, it saved me a lot of trouble....

---

### Post by Tiddens on 2009-12-11
This is nuts!  You guys really want people to use Ubuntu?  I am fairly PC-savvy, trying to convert from Windows, trying to use Ubuntu for all of my customers, and just had it where I wanted it, but I just ugraded from 9.04 to 9.10 and there is no menu bar!  So, I can get to the terminal with Alt-F2 and I can get to the file browser with Ctrl-F, and I've reviewed all of the comments above, and don't see how to 'add a tool called "Global Menu Panel Applet", and still don't have a menu bar!  Please help!

---

### Post by milos.forman on 2010-07-18
Thanks bro. You know the things. Thanks again

---

