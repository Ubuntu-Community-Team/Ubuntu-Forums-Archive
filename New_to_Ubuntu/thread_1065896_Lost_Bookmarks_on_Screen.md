---
title: "Lost Bookmarks on Screen"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by jamiehendrich on 2009-02-10
[U]Lost Bookmarks on Screen:

[/U]  Quick question:  I have visually lost my bookmarks that were in a column on the left-hand side of my screen.  (Please see screenshot)  When I go to "places" and click on "bookmarks" they are all still there.  I just cannot see them on the screen.  How do I get them back?

Please advise.   Thank you.

Jamie

PS  I even tried re-adding a bookmark.    It doesn't place it in a column to the left.

PS/PS  Where, oh, where are they?

---

### Post by arjuntank on 2009-02-10
press f9.

---

### Post by jamiehendrich on 2009-02-10
thank you.  All F9 does is make my screen just slightly move from left to right, with no results.

Just so you know, when this happened, I had gone into users and groups to check my user ID number.  You know where you have that white box that has name and login and home directory and underneath it says root, root and /root?  

I think my name used to be in that box.  When I closed out of that "users and groups" yesterday, i didn't see "jamie" any longer and the whole appearance of my screen changed.    I think it was in there but I'm not sure.  Does that help?

thank you so much.

jamie

---

### Post by theozzlives on 2009-02-10
Are they still in your Places menu???

---

### Post by arjuntank on 2009-02-10
> **jamiehendrich said:**
> thank you.  All F9 does is make my screen just slightly move from left to right, with no results.

Just so you know, when this happened, I had gone into users and groups to check my user ID number.  You know where you have that white box that has name and login and home directory and underneath it says root, root and /root?  

I think my name used to be in that box.  When I closed out of that "users and groups" yesterday, i didn't see "jamie" any longer and the whole appearance of my screen changed.    I think it was in there but I'm not sure.  Does that help?

thank you so much.

jamie

do u think ur problem with nautilus is due to this?
there is no connection.
may be ur username must have been deleted somehow
but then ur not sure. :)
okay so try logging in again, giving you username(jamie) and ur password.
if u can log in than u have prob messed up ur window manager or perhaps nautilus itself.
need more details.

---

### Post by jamiehendrich on 2009-02-10
PS  My side panel already had a check next to it.

---

### Post by jamiehendrich on 2009-02-10
To "ozzlives:"  Yes, all of my bookmarks are in "places."  They are just not in the column to the left on my screen.  Any ideas?

To arjutank:  I have just turned my computer completely off and logged back in and I still see the same thing:  No left-hand column bookmarks.  The whole appearance of my screen is different.  Any ideas to correct it?

I think on my home computer I have the word "places" above the bookmarks column.  On this computer that whole column has disappeared.

---

### Post by jamiehendrich on 2009-02-10
PS  I hate to admit this but I must:    I know NOTHING about computers.  How do I remedy it if I have done something to Windows Manager or Nautilus?  I'll tell you anything you want to know............if I can explain it.....which is doubtful. I hate being a novice!!!!  I really do.:):)

---

### Post by ibuclaw on 2009-02-10
> **jamiehendrich said:**
> thank you.  **All F9 does is make my screen just slightly move from left to right, with no results**.

Just so you know, when this happened, I had gone into users and groups to check my user ID number.  You know where you have that white box that has name and login and home directory and underneath it says root, root and /root?  

I think my name used to be in that box.  When I closed out of that "users and groups" yesterday, i didn't see "jamie" any longer and the whole appearance of my screen changed.    I think it was in there but I'm not sure.  Does that help?

thank you so much.

jamie

Your first sentence tells me that it is working just fine.

Press **F9** again until the browser view moves to the **right** again. Then put your Icon to the left side edge of broswer, but not completely on the edge, so the cursor becomes **two arrows attached to each other**. That is when you "click" and drag to the right.

The Places menu should appear :)

Regards
Iain

---

### Post by jamiehendrich on 2009-02-10
RESOLVED:

I got it.  You know what it was?  I clicked on the "Windows Menu" in the upper left-hand corner and clicked on "resize." And dragged the left hand "bar" over to the right and it literally "uncovered my bookmarks."  Please see screenshot.

Thank you everyone. 

Jamie

PS  I need an aspirin.

PS/PS  Lesson Learned:  Don't touch ANYTHING!  :)

---

### Post by arjuntank on 2009-02-10
im not sure bout this.
```

sudo gconf-editor

```
head to /apps/nautilus/preferences or /sidebar_panels
try changing some values there.

glad u got it jamie.
thanks tini!

---

### Post by ibuclaw on 2009-02-10
> **jamiehendrich said:**
> RESOLVED:

I got it.  You know what it was?  I clicked on the "Windows Menu" in the upper left-hand corner and clicked on "resize." And dragged the left hand "bar" over to the right and it literally "uncovered my bookmarks."  Please see screenshot.

Thank you everyone. 

Jamie

PS  I need an aspirin.

PS/PS  Lesson Learned:  Don't touch ANYTHING!  :)

Just as I thought :)

Nice to know it's fine again.

Regards
Iain

---

### Post by jamiehendrich on 2009-02-10
PS  I would mark this entire thread as "resolved," but i don't remember how.    I thought it was under "thread tools" but I don't see it.  Maybe that is no longer required.

---

