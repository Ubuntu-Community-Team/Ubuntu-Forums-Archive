---
title: "Getting out of &quot;Full Screen&quot; without rebooting"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by Chris Edgell on 2009-08-28
There are certain downloads that, when I open them up, automatically my computer goes to a full screen (nothing around the edges at all).  Then I can find no possible way to get out--short of rebooting. What's this about?

---

### Post by Chris Edgell on 2009-08-28
Most often, when I open a download, the computer goes to full screen and then I can find no way out except rebooting. Anyone know how to solve this problem?

---

### Post by Chris Edgell on 2009-08-28
[I have submitted this twice now and don't know where it's landing.]

Anyway, my problem is that when I open a download, it always/usually goes to full screen and I can find no way out except to reboot.  What's all this, and how do I avoid this  problem?  Thank you.

---

### Post by Sir Jasper on 2009-08-28
Try tapping F11 while holding down the Alt key else read the book you just downloaded,

My regards

---

### Post by Chris Edgell on 2009-08-28
Hi there,

I actually was trying to get this question answered before I download that book.  So let me go and see if this works.  Thank you.

---

### Post by achianese on 2009-08-28
What kind of download are you trying to open? A PDF file? Document of any sort?  ... racy video perhaps? Is this something you saved and tried to open or something opening straight from Firefox?

Basically, it would be useful to know which program Ubuntu is using to open the file.

---

### Post by Chris Edgell on 2009-08-28
Achianese,

Thank you for your attention to this.  The file was/is a PDF.  It was a study guide for the Book of Romans taken from a site where Bible studies are available for download.  It was sent to me from a friend one time, and I tried to download it myself once.  

I have since removed them because of the problem about reading them but always having to shut off my computer to get rid of it. 

I have just responded at the other place I "asked"--as I said I don't know how it got printed three times, I guess I just didn't wait long enough for it to show up.

Anyway, with that interaction, I have stated that I don't know WHAT to use to open a PDF.

This is all for the purpose of getting that Beginners Guide to Ubuntu; you can see I need some basics.

Thanks again.

---

### Post by ainsworth_t on 2009-08-29
There are ways to get around rebooting the computer completely when there is something wrong with your desktop (that's the beauty of *nix-type systems, you shouldn't have to reboot the entire system every time something goes wrong).

So, to answer your initial question, in order to avoid completely rebooting your computer when something goes wrong with your desktop (in your case, stuck in Fullscreen PDF view), simply enter into a new command line prompt by hitting CTRL+ALT+F1. Log into that prompt with your login credentials and run the command:
```
sudo /etc/init.d/gdm restart
```

However, this is kind of like using a sledgehammer to hang a picture. The simplest way to get out of fullscreen would be to hit F11 (no ALT key). If that doesn't work and you are not happy with the current PDF viewer installed, you can enable the Canonical partner repository and install Acrobat Reader and make it your default PDF viewer if you think you will feel more comfortable with something familiar. Let us know if you need help with this procedure.

---

### Post by Sir Jasper on 2009-08-29
Did F11 work? If not post back.

Download the Ubuntu Pocket Guide and it should appear on your desktop.

If the last three letters are pdf just left click and it should open for you to read.

If the last three letters are zip then left click and tell us what you see.

If you can open one pdf (portable document file) you should be OK with Romans.

My regards

PS The inbuilt Xubuntu help file Xfce 4 manual - Window Manager says under Shortcuts -
Toggle fullscreen : Alt + F11 (this was copied and pasted).
However, the toggle also works by just pressing F11.

My regards

---

### Post by Sir Jasper on 2009-08-29
I have now downloaded the Ubuntu Pocket Guide and set my PDF viewer to facing pages - click on the picture below:

[[img]http://a.imagehost.org/t/0413/Screenshot.jpg[/img]](http://a.imagehost.org/view/0413/Screenshot)

Tip

Have a general read and then use it as a reference book applying some common sense as it is a book on Ubuntu not Xubuntu (though it will still be of great assistance).

Click on Contents and use the index noting there are 18 preliminary pages so if you want to go to page 20 add 18 and under goto enter 38 (for page 57 use 75).

My regards

PS It depends which pdf viewer(s) you have as to the precise look and options available.

---

### Post by warreno on 2009-08-29
Wouldn't hurt to provide the URL so we could download the problem file ourselves and troubleshoot it.

Try ESC, or ctrl-w or ctrl-q. Alt-f4 might also work, or ctrl-x. Depends on the program being used to load the document in question.

---

### Post by Chris Edgell on 2009-08-29
Good Morning!  Always happy to see you on the case...(smile)

WELL....I awoke and found "it" on my desktop...clicked around, couldn't open,and finally hit on your early morning post.  The download is called "Zip Archive".  I left-clicked, got a "window" (?) with what looks like it will be a list of this type of file-though now there's only this one...I left clicked and it opened into a full screen copy of the book.  I tapped F11 and got a workable border; just what I wanted.  I love this feeling of problem solved.  Than you!

Also, thank you for your additional clarifications about xubuntu and xfce!

---

