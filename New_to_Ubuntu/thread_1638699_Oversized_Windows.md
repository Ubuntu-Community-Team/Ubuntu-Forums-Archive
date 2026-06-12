---
title: "Oversized Windows"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by John Peschken on 2010-12-06
Does anyone know what I can do about Windows that are way too big for my screen?

I am running on a netbook, and I am plagued by Windows that runway off the screen, usually there is no good reason for this.  I can see that there is a scroll bar on the window, but I can not seem to make the windows any smaller  Evolution seems to be the worst about this.  

Then just to aggravate me, attempting to click on anything close to the edge of the screen causes the windows to jump, making it impossible to click on what I am aiming at.  Very frustrating!  

It is also very difficult to grab the edge of a window to re-size it.  It just seems like the borders are very tiny.  Is there a way to adjust that?

---

### Post by wojox on 2010-12-06
Do you have a small screen? You should try Ubuntu Netbook Edition.

Else, what is your video card?

```
lspci | grep "VGA"
```

---

### Post by mcduck on 2010-12-06
You can move a window from any point inside the window (instead of just titlebar) by holding down the Alt key and dragging with left mouse button. And in the same way, you can resize windows with Alt+middle mouse button.

..of course you can just switch to using a window border theme with thicker borders, there are some installed by default and hundreds more available at gnome-look.org. ;)

---

### Post by karthick87 on 2010-12-06
**CTRL + **Increases your windows size.

**CTRL -  **Decreases your window size.

**CTRL 0 **Resets your window to the default size.

---

### Post by diablo75 on 2010-12-06
I usually ALT-Click.  This will let you grab the window from any part (like the middle of it, instead of the top of it) and move it around, giving you access to things off screen.

---

### Post by John Peschken on 2010-12-06
> **mcduck said:**
> You can move a window from any point inside the window (instead of just titlebar) by holding down the Alt key and dragging with left mouse button. And in the same way, you can resize windows with Alt+middle mouse button.

..of course you can just switch to using a window border theme with thicker borders, there are some installed by default and hundreds more available at gnome-look.org. ;)

I know the Alt key trick, but I am trying to do less of that.  It just seems like so many of the windows where I do that should not be necessary.

---

### Post by John Peschken on 2010-12-06
> **wojox said:**
> Do you have a small screen? You should try Ubuntu Netbook Edition.

Else, what is your video card?"

```
lspci | grep "VGA"
```

Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

It is a 1024 X 600 Netbook, but I dislike the interface on the Netbook Edition more than I dislike this problem.

---

### Post by John Peschken on 2010-12-06
> **karthick87 said:**
> **CTRL + **Increases your windows size.

**CTRL -  **Decreases your window size.

**CTRL 0 **Resets your window to the default size.

Now that sounds like just the hint I was looking for.  I will give that a try when I get home.  

Thank You!

---

### Post by mcduck on 2010-12-06
> **karthick87 said:**
> **CTRL + **Increases your windows size.

**CTRL -  **Decreases your window size.

**CTRL 0 **Resets your window to the default size.

I can't really find a single program where that would work. (well, apart form terminal emulators, where changing font size changes the window size accordingly.)

If the keyboard shortcut does anything at all, it increases and decreases the font (or icon) size.

What desktop environment/window manager you are using, and are you sure that shortcut isn't something you have configured yourself?

---

### Post by theozzlives on 2010-12-06
What resolution you using? If it's less than 1024x768, try raising it.

---

### Post by John Peschken on 2010-12-06
> **mcduck said:**
> I can't really find a single program where that would work. (well, apart form terminal emulators, where changing font size changes the window size accordingly.)

If the keyboard shortcut does anything at all, it increases and decreases the font (or icon) size.

What desktop environment/window manager you are using, and are you sure that shortcut isn't something you have configured yourself?

I'm just using the default 10.10 window manager, whatever that is.  I had the same problem with 10.04.

---

### Post by John Peschken on 2010-12-06
> **theozzlives said:**
> What resolution you using? If it's less than 1024x768, try raising it.

Unfortunately, 1024 X 600 is the best this little netbook screen can do.  I do have an external monitor, and to the best of my recollection, the problem goes away with that hooked up, but it's hard to fit in my backpack. ;)

It seems like I should be able to grab the lower right corner of any window and make it whatever size I want, but some windows in some applications just won't let me do that beyond a certain point.  The problem goes away when I run the XP this thing came with, but who wants to run that?  XP makes me sad.  :cry:

By the way, the external monitor can only do 1024 X 768.  The extra 168 pixels makes a big difference.

---

### Post by John Peschken on 2010-12-06
> **mcduck said:**
> You can move a window from any point inside the window (instead of just titlebar) by holding down the Alt key and dragging with left mouse button. And in the same way, you can resize windows with Alt+middle mouse button.

..of course you can just switch to using a window border theme with thicker borders, there are some installed by default and hundreds more available at gnome-look.org. ;)

I am aware of the Alt key trick.  It works for sure.  I have changed mine to the "Windows" key.  I'm trying get to where I need to do less of that.

I encounter so many windows where there are inches and inches of empty space at the bottom.  The bottom part where the buttons usually are hangs way off my screen and I can't make the window any smaller.  It just seems wrong.  I should be able to make it smaller, it seems to me.

Maybe the 11.04 changes, getting away from Gnome will bring relief.

---

### Post by mcduck on 2010-12-06
> **John Peschken said:**
> I am aware of the Alt key trick.  It works for sure.  I have changed mine to the "Windows" key.  I'm trying get to where I need to do less of that.

I encounter so many windows where there are inches and inches of empty space at the bottom.  The bottom part where the buttons usually are hangs way off my screen and I can't make the window any smaller.  It just seems wrong.  I should be able to make it smaller, it seems to me.

Maybe the 11.04 changes, getting away from Gnome will bring relief.
That kind of stuff is pretty much up to each individual application's developers, there's not much Ubuntu could do the change the user interface design of the programs.

Hopefully application developers start soon realizing that there's a large amount of netbook users with very limited display resolutions, and at least normal desktop applications really should be able to resize to fit the 600px vertical resolution. Of course sending some feedback to each app's developers might help a bit... ;)

I suppose it has come as a bit of a surprise that the programs should suddenly work with such small resolutions again when everybody thought that we were already way past those times...

---

### Post by John Peschken on 2010-12-06
> **mcduck said:**
> That kind of stuff is pretty much up to each individual application's developers, there's not much Ubuntu could do the change the user interface design of the programs.

Hopefully application developers start soon realizing that there's a large amount of netbook users with very limited display resolutions, and at least normal desktop applications really should be able to resize to fit the 600px vertical resolution. Of course sending some feedback to each app's developers might help a bit... ;)

I suppose it has come as a bit of a surprise that the programs should suddenly work with such small resolutions again when everybody thought that we were already way past those times...

Although I consider Ubuntu generally superior to Windows, I can not help but notice that in Windows :frown:, I can make any window any size.  I can make any window so tiny the entire contents of the window disappears and only the top and bottom status bars remains.  At the same time, I can make it so narrow only the top left corner icon and the right side control buttons remain.  Then, the next time I open that Window, it remembers the size and position.  

That is the other aggravating thing about Ubuntu for me. It does not seem to remember the size or position of windows, so I have to re-size them every time I open that same window.  That might be okay if they were not so over sized.  It is a +2 for Windows in my opinion.

I imagined that this sort of thing would be under the control of the Gnome desktop or the window manager, but I am not an expert just a humble and somewhat annoyed user.

Okay, I'm done complaining now.  I am probably not making friends here speaking ill of Ubuntu. It is meant as constructive criticism. :D

---

### Post by QLee on 2010-12-06
> **John Peschken said:**
> Although I consider Ubuntu generally superior to Windows, I can not help but notice that in Windows :frown:, I can make any window any size.  I can make any window so tiny the entire contents of the window disappears and only the top and bottom status bars remains.  At the same time, I can make it so narrow only the top left corner icon and the right side control buttons remain.  Then, the next time I open that Window, it remembers the size and position.  

That is the other aggravating thing about Ubuntu for me. It does not seem to remember the size or position of windows, so I have to re-size them every time I open that same window.  That might be okay if they were not so over sized.  It is a +2 for Windows in my opinion.

I imagined that this sort of thing would be under the control of the Gnome desktop or the window manager, but I am not an expert just a humble and somewhat annoyed user.

Okay, I'm done complaining now.  I am probably not making friends here speaking ill of Ubuntu. It is meant as constructive criticism. :D

Well John, I can change the size of my application windows too, and they are remembered the next time I use the application. I remember there used to be a problem with evolution on the Netbook Edition but I thought it was fixed for 10.10, I haven't tracked the bug because I don't have it.

It doesn't do a whole lot of good to constructive criticise in a user support forum, the best would be to file a bug against any offending program, that way a developer will look at your criticism and advise.

---

### Post by John Peschken on 2010-12-06
> **QLee said:**
> Well John, I can change the size of my application windows too, and they are remembered the next time I use the application. I remember there used to be a problem with evolution on the Netbook Edition but I thought it was fixed for 10.10, I haven't tracked the bug because I don't have it.

It doesn't do a whole lot of good to constructive criticise in a user support forum, the best would be to file a bug against any offending program, that way a developer will look at your criticism and advise.

If it is a bug, I agree.  I came to the forum hoping and thinking it was a setting I needed to tweak.  I'm still not sure whether it is a bug or just the way it's designed.

I am not running the netbook edition. I am not a fan of Unity, but I suppose I will have to adapt when it is adopted for Ubuntu for grown-ups.  I'm also not sure if that would solve my problem.  Are you?

---

### Post by QLee on 2010-12-06
As I mentioned, I don't run Netbook Edition, so no I can't be sure it would solve anything for you.

---

### Post by John Peschken on 2010-12-06
> **QLee said:**
> As I mentioned, I don't run Netbook Edition, so no I can't be sure it would solve anything for you.

Maybe I should give the Netbook Edition another go.  On the other hand, if McDuck (above) is correct and it's in the hands of the application developer (and therefore the application) that would not help since I would be running mostly the same applications.

If it is likely to help. it would be nice to hear someone say so with some certainty before I go to the trouble of a reinstall.

- John

---

### Post by John Peschken on 2010-12-06
> **wojox said:**
> Do you have a small screen? You should try Ubuntu Netbook Edition.

Else, what is your video card?

```
lspci | grep "VGA"
```
Some research into the Netbook Edition has scared me off of that solution a bit.  There sure are a lot of people complaining about stability and performance!

---

### Post by John Peschken on 2010-12-06
The more I think about this, the sillier this all seems.  I can't think of a reason any application should throw up a window bigger than the available screen size.  That's what scroll bars are for!  Surely some part of the system knows how much screen is available.  Why would anyone want "Save" and "Cancel" buttons to appear off the screen?  There must be a way to control this, somehow.

I do have the Compiz configuration manager installed.  I am hoping for a solution there, but the closest thing seems to be the window "rules" settings, and from what I can get by looking at the Compiz forums and Wiki, it does not look promising.

Time to give upon this as unsolvable maybe.

---

### Post by John Peschken on 2010-12-06
> **karthick87 said:**
> **CTRL + **Increases your windows size.

**CTRL -  **Decreases your window size.

**CTRL 0 **Resets your window to the default size.

I don't seem to be having any luck with this suggestion.  For instance, in Evolution, it seems to decrease the Font size in the header of whatever message you are viewing, but nothing else.  Bummer.

Evolution does seem to be the worst offender.  I've been trying to adapt to it because of the calendar features, but so far I still like Thunderbird better and it does not seem to have this problem as much.  Maybe that's the way to go.

---

