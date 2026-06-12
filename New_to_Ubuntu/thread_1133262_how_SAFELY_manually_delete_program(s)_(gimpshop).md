---
title: "how? SAFELY manually delete program(s) (gimpshop)"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by agnes on 2009-04-22
Hello everyone,

well, I' m not an absolute beginner :)... But I'm just not exactly sure of this.

I have installed GimpShop from the Debian package (from the GimpShop website -- NOT from Synaptic), 
now I want to uninstall it.

But Synaptic, does not show the files of course. 
And Applications-->Add/Remove, also not.
Synaptic shows only some library files that have to do with graphics.
I deleted the "does-not-seem-important"-ones of these, but then, GimpShop still worked, i.e. it ran.
(By the way I already deleted Gimp before installing GimpShop, with Applications-->Add/Remove.)

I know there has been some post about this earlier, it said you had to "do" just ```
sudo dpkg -r gimp*
``` but, this didn't work for me either (i.e. gimpshop still ran).

Ok, so my question is: can I just delete everything the finder finds when it searches for gimp?
These directories are:

[B]/etc/gimp/
/home/MyName/Downloads/gimp-2.2.8/
/usr/local/include/gimp-2.0/
/usr/local/share/gimp/
/usr/local/lib/gimp/
[/B]
And some gimp files in **/usr/local/bin**

Or... will that cause me into trouble, or not giving me a complete uninstall?
Or is there another way?

---

### Post by taurus on 2009-04-22
Have you tried something like

```
sudo dpkg -r gimpshop
```

---

### Post by agnes on 2009-04-22
Yes, but that's kind of the same as
```
sudo dpkg -r gimp*
```, right?

It gives me the following message:

**dpkg - warning: ignoring request to remove gimpshop which isn't installed.**
(when I run your code)

---

### Post by llamabr on 2009-04-22
What happens if you try to install it from apt, or synaptic?  Then see if you can uninstall it.

But before that, are you sure it's installed?  Do:

```
which gimpshop
```

---

### Post by agnes on 2009-04-22
If I want to install it from Synaptic, I'd first have to add a line to my software-sources-list (for Debian packages or such), but when I tried to add that line with the software-sources dialog (System-->Administration-->Software sources), the software-sources dialog gave me some error (about confirming signatures) so to avoid that, I just downloaded it from the webpage.

Anyway...

When I type ```
which gimpshop
``` it displays... nothing.

But when I type ```
which gimp
``` it yields:
**/usr/local/bin/gimp**

:confused:

(By the way, I'm pretty sure it's installed. When I run it it is first "initializing" stuff, and then, well, GimpShop is there, and I can paint etc.)

Maybe I should also add that I've downloaded the source, and then built it. (With ./configure && make && make install.)

---

### Post by rhcm123 on 2009-04-22
i think, from my old debian etch days, there is a dpkg-remove command that should take .deb packages and do the run around on them - i think. grab dlocate with apt and try that.

---

### Post by llamabr on 2009-04-22
If you built it from source, then you can't remove it with dpkg.  You need to go back and issue the command make remove or make uninstall, whichever came with the original.  If it didn't you have to go and manually delete all the files.  

The upside of ubuntu is that it's got a really nice package manager.  The downside is that when you try to install things otherwise, you've created a whole lot of extra work for yourself.

Why do you want to remove it?

---

### Post by agnes on 2009-04-23
First, thanks everyone.

And yes, 'make uninstall' worked :)
However a lot of folders are still there (e.g. /usr/local/share/gimp, /usr/local/gimp), but they're empty now, so can be safely deleted.

I wanted to delete it because I have installed Photoshop (and InDesign, and Illustrator) CS3 on a virtualization of Windows XP with VirtualBox and this works fine for me, not slow at all.
I prefer Photoshop above GimpShop for several reasons: 
1. GimpShop opens 3 separate windows at the "taskbar" (the menu, the drawing,  and the layers etc. windows) which I find very annoying; 
2. There are *way* more tutorials for CS3 than for Gimp ánd GimpShop; 
3. I'm not a professional in graphic stuff, I just don't want to spend too much time on it and I'm used to Photoshop. If I use that I'm at least sure I can do everything I may need to relatively easy.

---

### Post by rhcm123 on 2009-04-23
> **agnes said:**
> 
I prefer Photoshop above GimpShop for several reasons: 


I find that photoshop is consistantly better than gimp, despite photoshop costing an arm and a leg (or perhaps "due to costing an arm and a leg). I missed most of the features that i had in photoshop when i tried out gimp, and it's one of the few reasons i keep xtra-poopy around.

---

