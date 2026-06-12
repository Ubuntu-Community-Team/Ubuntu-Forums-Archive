---
title: "The path is clogged with repetitions"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by Chris Edgell on 2009-06-09
Hardy Huron 8.04 (I think that's right).

I have worked around many unsolved glitches with this computer...but in the meantime I have never really learned to open a new folder. Now I need to be able to sort through it all. I have paths that read like: home>Chris>desktop>poetry>desktop>poetry.  It loops and loops. Is there an easy explanation to this system as opposed to how easy it was with Microsoft?  I feel like the eternal beginner...

I've tried to study the gnome learning manual but it doesn't seem straightforward about opening a new file folder and dragging and dropping individual documents into the new folder and doing away with all the repetition.  

Any sites will be read and studied, I just can't seem to find what I need.

---

### Post by Sir Jasper on 2009-06-09
Hi,

What happens if you bring up your Home directory and right click?
At the top of the menu do you get a New Folder option.
If you do, just rename it if and as desired.

You can copy, highlighting one of the files and then use the Shift or Ctrl to highlight more files. Then you can paste them as you wish.

In your example you could copy, paste, check and then delete the files and folders you don't need.

My regards

ADDENDUM:

If Chris posts back with a problem, I'm away for a few hours, so would someone else  kindly help?

---

### Post by Chris Edgell on 2009-06-09
[My problem started when I wanted folders on my desktop to sort to.  I had been used to "MY computer" being all business and "Chris's Documents being my personal work.  Misc files I could lay on my desktop.  Everything "dragged" around.]

I have gone and right-clicked "Home"  It opened, I could open a new folder.  The banner across the top read, "Chris-File Manager" Then the path was:  Home>  Chris>  New folder.

I can work from here; I can try to go on and sort things out--now I see at this point that the thing I next would want to do would be to put that folder ON the desktop, (then of course that puts another link in the path..that can't be right).

Any course of action, based on this info?

---

### Post by Chris Edgell on 2009-06-10
Thank you, Sir Jasper, I greatly appreciate your advise.  

Now everything is on the path:  Home> Chris>

My next step will be to find out how to put these folders on the desktop.  Will it just be quick launch.  (What would normally be on the desktop as far as the path goes?)

But thanks again, I feel like I have a new lease on life.

---

### Post by Sir Jasper on 2009-06-10
Hi again,

If you do not already have a "Places" shortcut on one of your panels you could:
right click on a blank area of one of your panels then click on "Add New Item", then scroll down to "Places" and click.

Now you can copy and paste or cut and paste folders to your desktop.

Let us know how you fare.

My regards

There may be other shortcuts you would like on a panel so just see if anything appeals to you when you scroll down the list of those available.

---

### Post by mcduck on 2009-06-10
> **Chris Edgell said:**
> [My problem started when I wanted folders on my desktop to sort to.  I had been used to "MY computer" being all business and "Chris's Documents being my personal work.  Misc files I could lay on my desktop.  Everything "dragged" around.]

I have gone and right-clicked "Home"  It opened, I could open a new folder.  The banner across the top read, "Chris-File Manager" Then the path was:  Home>  Chris>  New folder.

I can work from here; I can try to go on and sort things out--now I see at this point that the thing I next would want to do would be to put that folder ON the desktop, (then of course that puts another link in the path..that can't be right).

Any course of action, based on this info?

IF you want similar desktop shortcuts to your documents and "my computer" as used in Windows, using launchers or links isn't the way to do it.

Instead, press Alt-F2 and run "gconf-editor" (or start it from a terminal), browse to apps/nautilus/desktop and enable the icons you want.

For other directories than those built into Nautilus, you might want to use launchers instead of links if you have problems with the way links work compared to shortcuts used in Windows.

The reason for your strange paths is simple, links in Linux aren't like desktop shortcuts. While a shortcut from desktop into your documents directory would take you to the documents directory, links used in Linux would bring the documents directory to where the link is.

In other words a shortcut takes you to where it's pointing at, while a link creates a true connection between the two locations, making the target appear where the link is.

If you want shortcuts-style desktop icons instead use launchers, not links.

---

### Post by Sir Jasper on 2009-06-10
Hi mcduck,

You may not remember you helped me but it was your helping me that has prompted me to try to help others.

I would just say that since Chris is using Xubuntu it's probably Thunar not Nautilus that is used.

My regards and thanks

---

### Post by mcduck on 2009-06-10
> **Sir Jasper said:**
> Hi mcduck,

You may not remember you helped me but it was your helping me that has prompted me to try to help others.

I would just say that since Chris is using Xubuntu it's probably Thunar not Nautilus that is used.

My regards and thanks

good point.. :)

Anyway, the basic aspect of links not being the same thing as shortcuts is the same.

I can't remember if Thunar had some option for enabling some built-in desktop shortcuts, but if it does it's better to use them instead of trying to create ones of your own. Ad for the rest, use launchers if you don't feel comfortable with the way links behave.

---

### Post by Chris Edgell on 2009-06-10
Thank you both so much for concentrating and communicating on and about my problem.  I begin to see the light.

 (Yes it's Thunar)  I think I see the difference between shortcut and link now.
  
 I'll try to say where I am now: Here's my path:

Title at top of window File system- File Manager
unnamed sq box>Home(One folder only in it.  It says "Chris" That was when I was trying to create a place for only personal, not programs, etc. although it didn't work)
Blank>home>Chris (This folder has 63 items-one of these items is a folder entitled "Chris and it has 49 of the items found in the first "Chris folder--if I just delete it will it disturb the matching "Chris" file existing [that it's "in"]?  (Did I create a matching file when I made a link instead of a shortcut?)

When you used the word directory, it reminded me of something I used to know...

If you can clear me up on this, I'd like to go on a step or two more.  Thanks again, both of you!

---

### Post by Sir Jasper on 2009-06-10
Hi Chris,

I didn't immediately follow what you said and I won't be available for a while.

Can make a folder called say, backup in your home>chris directory and then copy all the other folders that you are trying to organise to it. So that everything, even if duplicted, is saved and safe?

If you can, then you will be able to experiment a step at a time and you shouldn't lose anything you need.

Also consider you already have folders for documents, music etc if they are the type of personal files you want to organise.

My regards

---

### Post by mcduck on 2009-06-10
> **Chris Edgell said:**
> Thank you both so much for concentrating and communicating on and about my problem.  I begin to see the light.

 (Yes it's Thunar)  I think I see the difference between shortcut and link now.
  
 I'll try to say where I am now: Here's my path:

Title at top of window File system- File Manager
unnamed sq box>Home(One folder only in it.  It says "Chris" That was when I was trying to create a place for only personal, not programs, etc. although it didn't work)
Blank>home>Chris (This folder has 63 items-one of these items is a folder entitled "Chris and it has 49 of the items found in the first "Chris folder--if I just delete it will it disturb the matching "Chris" file existing [that it's "in"]?  (Did I create a matching file when I made a link instead of a shortcut?)

When you used the word directory, it reminded me of something I used to know...

If you can clear me up on this, I'd like to go on a step or two more.  Thanks again, both of you!
Linked files/directories don't take any more disk space, although some programs might count them to total count of your files.

Linking doesn't copy the file, simply makes one file appear in two different places in your file system. Also, removing the link is safe and doesn't remove the original files.

---

### Post by Chris Edgell on 2009-06-10
Was that Mcduck and Sir Jasper,

I can't thank you enough.  I have it just the way I like it.  When I would right-click on the file folder of my choice, I would get a drop- down menu.  One choice is "Send to", a sliding drawer came out and offered me two choices-one of which is "Desktop"; I click there and the full file folder pops onto the desktop.  It has a thumbnail size box upon which is a whoosh-type arrow.  (Is that a short-cut sign?)  

Again I thank you and hope I meet you again.

---

