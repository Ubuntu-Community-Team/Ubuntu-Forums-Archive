---
title: "Root failed to mount.  Yikes!"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by greep on 2010-12-04
One of my linux assignments involved editing fstab, the book we're reading was pretty vague about what actually goes on in there, and I screwed up. Upon restarting my computer I get sent to a read only maintenance shell. Ls shows nothing from the start, although going to /etc and lsing shows everything there. I can even look at the fstab file, but there's nothing I can do to change it and chmod will not change the permissions to allow me to change it.
 
I e-mailed my teacher, and this is what he said:
 
"Uh-oh! Definitely sounds like fstab got changed in a way it shouldn't have.
Do you mean a "root#" prompt (with a #)? It may be possible to read or edit /etc/fstab in that situation. 
 
What happens if you do "df"? What about just "ls"?
Depending on what actually *did* mount, you might be able to create a temporary directory, manually mount your main drive, and then find fstab within it.
If not - hmm... Are you running a physical box or VM? 
 
If its a physical box, you could boot from the CD and look at /etc/fstab on the hard drive to try to change it back the way it was originally. If its vm, then its trickier: You could install a *second* distribution (on another virtual drive) and use that to look back at the first drive, but if you're doing that you might as well re-install the original appliance."
 
I am running a physical box, but I'm not really sure what to mount where, and if that helps. Anyways, if I have to reinstall, I'm fine with that, as there is nothing I particularly need stored on ubuntu. But any help would be very appreciated :)

---

### Post by ikt on 2010-12-04
> **greep said:**
> I am running a physical box, but I'm not really sure what to mount where, and if that helps. Anyways, if I have to reinstall, I'm fine with that, as there is nothing I particularly need stored on ubuntu. But any help would be very appreciated :)

Heya,

The fstab is a little tricky at first but once you *get it*, it all makes sense and is completely easy to use.

I would definitely give this a read: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Then you're going to want to boot onto a live usb drive, or live cd, so you can get access to your linux partition and edit the fstab file.

If you know how to boot into a live usb drive I won't explain, but basically head back into terminal on the ubuntu live,

```
sudo nautilus
```

And that should allow you to get onto the installed linux partition and edit the fstab, if you want you can paste your fstab here and we may be able to figure out what's wrong, but I would recommend reading the above link and knowing yourself.

gl :)

---

### Post by greep on 2010-12-04
I actually don't even know how to use the live cd, sorry :(. I start the computer with the Ubuntu Cd, I get a few options like try without installing/install/ etc. I choose boot from first hard disk, and get a list of places I can go, like ubuntu generic pae, windows 7. I try the one that normally gets to ubuntu, the first one listed, and it has the same error "mount of root filesystem failed."  And nautilus doesn't work from there.

---

### Post by ikt on 2010-12-04
> **greep said:**
> I actually don't even know how to use the live cd, sorry :(.

All good :D

> **greep said:**
> 
 I start the computer with the Ubuntu Cd, I get a few options like try without installing/install/ etc.

That's the one you want, try without installing, that will give you an environment similar to an installed version of ubuntu, but it will actually all be running off the cd.

---

### Post by greep on 2010-12-04
Alright, I'm on the live CD now.  Unfortunately, I don't know how to access my actually installed files.  I tried go and then computer, but it says"nautilus cannot handle 'computer' locations"

Edit: Anyways, I'm getting tired, so I'm going to bed.  Won't be able to respond for about 9 hours.

---

