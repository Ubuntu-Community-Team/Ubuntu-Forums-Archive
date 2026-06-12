---
title: "Undeleting a file in  Ubuntu that I already have deleted?"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by TAspr on 2011-06-07
I accidently deleted a bunch of files from Ubuntu, and would like to know how to get them back?  Are there any good undelete programs?

---

### Post by lordadi on 2011-06-07
Are these files in your trash?

---

### Post by Rex Bouwense on 2011-06-07
If you haven't emptied your trash, you could check there.

---

### Post by nothingspecial on 2011-06-07
If you used rm or shift-delete then they are gone.

If they are really really important look at testdisk/photorec

---

### Post by dFlyer on 2011-06-07
> **TAspr said:**
> I accidently deleted a bunch of files from Ubuntu, and would like to know how to get them back?  Are there any good undelete programs?

As far as I know, files deleted from the command line are gone. Also files that are deleted and not moved are trash are also gone and can not be undeleted.

---

### Post by TAspr on 2011-06-07
Well, I should have mentioned that these files were deleted from an exteral drive hooked up by a USB cable.  Where they went to, I do not know.

---

### Post by dFlyer on 2011-06-07
> **TAspr said:**
> Well, I should have mentioned that these files were deleted from an exteral drive hooked up by a USB cable.  Where they went to, I do not know.

External drive with win format try photorec, you might be able to recover them.

---

### Post by TAspr on 2011-06-07
Cool, thanks a bunch for your help and I will let you know if that works or not

---

### Post by nothingspecial on 2011-06-07
> **TAspr said:**
> Well, I should have mentioned that these files were deleted from an exteral drive hooked up by a USB cable.  Where they went to, I do not know.

In your file browser, go to the external drive.

Press Ctrl-H (at the same time)

Hopefully a .trash folder will show up. And hopefully they should be in there.

---

### Post by hakermania on 2011-06-07
> **nothingspecial said:**
> In your file browser, go to the external drive.

Press Ctrl-H (at the same time)

Hopefully a .trash folder will show up. And hopefully they should be in there.
Yes, that's what I'd told, it may by called .TRASH too....

---

### Post by TAspr on 2011-06-08
I did that, and in fact the trash bin did show up, but no dice.  I guess I learned the hard way.

---

### Post by TAspr on 2011-06-08
> **dFlyer said:**
> External drive with win format try photorec, you might be able to recover them.

How do you run **photorec**?

---

### Post by alphacrucis2 on 2011-06-08
> **TAspr said:**
> How do you run **photorec**?

See [http://www.cgsecurity.org/wiki/PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")  especially the section that says Step by Step.

Edit: You don't need to download the program from their site - it's in the Ubuntu repos. Just install testdisk via synaptic or apt or whatever you like to use.

---

