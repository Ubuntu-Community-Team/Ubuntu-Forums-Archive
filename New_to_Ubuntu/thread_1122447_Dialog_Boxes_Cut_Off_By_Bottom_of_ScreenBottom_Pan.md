---
title: "Dialog Boxes Cut Off By Bottom of Screen/Bottom Panel"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by TAllen013 on 2009-04-11
When I try to edit settings in programs, the dialog box that pops up will often-times get cut off by the bottom of the screen (so that you can't see the items at the very bottom and also so that you can't press the "OK" button).

Is there any way to set it so that the windows such as these automatically fit to the screen vertically?

Thanks in advance for any replies.

---

### Post by Elfy on 2009-04-11
You could maximise them - but I have in the past had to use Alt+left mouse button to move windows about.

---

### Post by TAllen013 on 2009-04-11
Thanks for the reply, but there are a couple of problems.

Some of the dialog boxes don't maximize.  (For example, the Preferences in VLC Player.)

Also, I can't simply move the dialog boxes. It will only allow me to raise the boxes to the top of the screen (at which point I can't move them any higher), and a lot of the bottom area of the boxes is still being cut-off by the bottom of the screen.

---

### Post by cwsnyder on 2009-04-11
Are you at the maximum resolution for your monitor?  Programmers don't like to fit dialog boxes into anything smaller than 1024x768 (or even higher resolutions).  It makes it hard to read some of the smaller print, but since many (if not most) users have screen resolutions of 2048x1152 or higher, why should they worry about screen real estate?

Long term, you might want to invest in a 22 inch or larger monitor if you need larger fonts.

---

### Post by CatKiller on 2009-04-12
> **TAllen013 said:**
> When I try to edit settings in programs, the dialog box that pops up will often-times get cut off by the bottom of the screen (so that you can't see the items at the very bottom and also so that you can't press the "OK" button).

That sounds like your resolution is very low. It's worth checking the maximum resolution your monitor can do, from your monitor documentation, and what resolution you're currently using. It's possible that you've got a configuration problem so that you are using a much lower resolution than you could be.

> 
Is there any way to set it so that the windows such as these automatically fit to the screen vertically?

Middle-click on the maximise button does it in Compiz. I can't remember if it works in Metacity. But if you need to fit more information in than you have room for, then some of it has to fall off the bottom.

I believe it is possible to set a virtual resolution that is higher than the physical resolution so that you can pan around to see the information that doesn't physically fit on the screen.

---

### Post by cjv8888 on 2009-04-12
> **TAllen013 said:**
> When I try to edit settings in programs, the dialog box that pops up will often-times get cut off by the bottom of the screen (so that you can't see the items at the very bottom and also so that you can't press the "OK" button).

Is there any way to set it so that the windows such as these automatically fit to the screen vertically?

Thanks in advance for any replies.

Open a terminal
type
gconf-editor
then go to
/ apps / compiz /
plugins / move / allscreens / options / constrain_y. Untick or set this to false.
Now you can grab a window by alt-left click and raise the window above the top of the screen,

---

### Post by keithpeter on 2009-05-10
> **cwsnyder said:**
> Are you at the maximum resolution for your monitor?  Programmers don't like to fit dialog boxes into anything smaller than 1024x768 (or even higher resolutions).  It makes it hard to read some of the smaller print, but since many (if not most) users have screen resolutions of 2048x1152 or higher, why should they worry about screen real estate?

Hello All

Programmers might want their creations used on Web books and mobile phones!

I'm typing this on an ASUS 701 with an 800 by 400 screen. The application windows are ok, its the dialog boxes that dont fit, and some can't be maximised. I'm having to learn the 'tab order'!

---

### Post by hanson53 on 2012-05-31
This is particularly a problem with the Print dialog displayed via the File menu of LibreOffice Writer or Adobe reader, it is not possible to see any of the buttons which have fallen off the bottom of the screen. I am using an Acer Aspire One Netbook with a screen resolution of 1024x600.
Automatic sizing to fit the screen size would be very useful.

---

### Post by AnotherMuggle on 2012-05-31
> **keithpeter said:**
> Hello All
I'm typing this on an ASUS 701 with an 800 by 400 screen. The application windows are ok, its the dialog boxes that dont fit, and some can't be maximised. I'm having to learn the 'tab order'!

I occasionally have this issue on a HP Mini 210 which has a pretty decent screen resolution for a netbook (1024 x 600).  As you mention main windows are fine but dialog boxes are sometimes an issue.

---

### Post by oldflyer on 2012-05-31
I asked about this same issue in this [thread]("http://ubuntuforums.org/showthread.php?t=1990871") . Right clicking in the title bar of the dialog box brings up a menu with a move option. Select the move option to get a hand in the middle of the box, and carefully click and move up only (not left or right), and the lower part will be visible when you unclick. This is working for me on my eeePC.

---

