---
title: "[SOLVED] Hiding file extensions?"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by Dirjel on 2008-12-29
About a week ago, I got my first private computer, so I put Ubuntu on it.  I've transferred all of my files onto here, but I'm really irritated by all the .jpg, .doc, .png, etc. on all of my files.  I see that you can delete that bit of text on Ubuntu and the file will still open regularly, but I don't see any way to remove all the extensions from all of my files simultaneously, and I also don't see any way to hide it like you could in Windows.

Do I have to just go through and manually rename every single file, one by one, or is there a simpler way to clean up the interface?  I've looked through the options for Nautilus, which is my file browser, I think, but I didn't see anything.

Anyway, I'm using Intrepid.  Any help would be appreciated, thanks.

---

### Post by kostkon on 2008-12-29
> **Dirjel said:**
> About a week ago, I got my first private computer, so I put Ubuntu on it.  I've transferred all of my files onto here, but I'm really irritated by all the .jpg, .doc, .png, etc. on all of my files.  I see that you can delete that bit of text on Ubuntu and the file will still open regularly, but I don't see any way to remove all the extensions from all of my files simultaneously, and I also don't see any way to hide it like you could in Windows.

Do I have to just go through and manually rename every single file, one by one, or is there a simpler way to clean up the interface?  I've looked through the options for Nautilus, which is my file browser, I think, but I didn't see anything.

Anyway, I'm using Intrepid.  Any help would be appreciated, thanks.
Yes, in most cases Ubuntu recognises the files through their magic number, but not in all cases. Some file types still need their extension in order Ubuntu to use the correct MIME for them.

Nevertheless, you could use a file renamer application (e.g. *Purrr*) to easily remove the extensions from your files.

---

### Post by Dirjel on 2008-12-29
Alright, cool.  I'll try a renaming program.  Thanks, this is exactly the information I needed.

---

### Post by igknighted on 2008-12-29
Whether this is relevant to you or not, it should be noted that deleting the extensions off of these files will cause Windows to not know how to handle them.  I would think carefully about deleting all the extensions before going about that.

---

### Post by Dirjel on 2008-12-29
Thanks, but I already know that Windows won't like it.  That's OK by me, though, because I don't *have* Windows.  If I ever *do* need to transfer a file or two over to a Windows computer, I can just add the extension back on.

Anyway, it's done now.  I just used the Add/Remove to install KRename.  Of all the ones I tried, it was the easiest and quickest to use.  I give it a gold star ^_^

---

### Post by adobrakic on 2008-12-29
Are you talking about just *hiding* the extension, or completely deleting it? Because it seems like you (Dirjel) want to just hide it, but the other posts are leaning on completely deleting the the extensions.

I ask because I'm interested in this also. 
Also, does KRename delete the extension or hide them?

---

### Post by Dirjel on 2008-12-29
> **adobrakic said:**
> Are you talking about just *hiding* the extension, or completely deleting it?
Either way is fine with me.  I just don't want to have to look at it anymore, as it clutters up my interface.  I don't think there is a way to merely hide the extensions.

> Also, does KRename delete the extension or hide them?
It deletes it, if you so choose.  The only file type thus far that has had issues with the renaming was .xcf, or GIMP files.  If you do decide to delete the extensions, make sure to leave the .xcf unchanged.

---

### Post by igknighted on 2008-12-29
> **Dirjel said:**
> Thanks, but I already know that Windows won't like it.  That's OK by me, though, because I don't *have* Windows.  If I ever *do* need to transfer a file or two over to a Windows computer, I can just add the extension back on.

Anyway, it's done now.  I just used the Add/Remove to install KRename.  Of all the ones I tried, it was the easiest and quickest to use.  I give it a gold star ^_^

I wasn't really warning for you... anything posted on here is like a part of the "how to Ubuntu encyclopedia", and I don't want someone dual booting to wander by and do this, and have their windows install not recognize any files.

---

### Post by PierreDeKat on 2008-12-29
You know, I have often wondered why any sane person would want to hide the file extensions from themselves. 

I have always considered the fact that Windows XP comes out of the box that way as its single biggest security flaw.

One can only imagine how many millions of unsuspecting XP users have double-clicked on a file called, say, "MickeyMouse" thinking they were going to see a picture, when in fact they were launching a virus MickeyMouse.exe.

And you're proposing to carry this security flaw over onto your Ubuntu setup?

Please let us know what happens when somebody emails you MickeyMouse.deb, huh? :roll:

---

### Post by nishant.singh28 on 2010-08-14
Won't it ask for the password :P

---

### Post by Vaphell on 2010-08-14
you can destroy user's data with simple unauthorized recursive rm, no password required :)

---

