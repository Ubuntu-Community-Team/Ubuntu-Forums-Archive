---
title: "Ubuntu 10.10 - 2 (hopefully) simple questions"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by risk_reversal on 2011-03-31
Hi guys, first time poster on these forums.

I recently installed Ubuntu 10.10 (as dual boot) with XP and have a couple of questions to ask please.

**1**. I am currently using the (default) *Ambiance* theme. This theme has the *close, minimise & maximise* tabs (in that order from left) on the top left of the windows bar (at top).

I just wanted to move these three buttons to the right and to have the following order *minimise, maximize & close*. Tried to make changes but the only theme that seems to do this is *Clearlooks* but then all the colours change.

Any easy way for me to do this?

**2**. My 2nd question relates to *icon text*. Sorry long winded explanation below

If I copy a music file to the Ubuntu desktop, the text underneath the music file icon is limited to 3 lines unless I roll the mouse pointer over the icon and then the text expands fully. If I roll the mouse pointer off the icon, the text under the icon reverts to just 3 lines (which I am guessing is the default). So far so good.

Just for clarity, if I click on the music file icon on the desktop, the icon turns orange and all the text is displayed.

Now for the problem which I am facing.

If I copy the same music file from the desktop to the say the *Music* folder, the text under the icon does not seem to behave in the same way, in that all the text under the music file icon is always fully displayed. If I roll the mouse pointer over the icon, the icon goes active ie lighter in colour.

I originally copied this music file from an Extended / Logical partition which existed on my HD prior to installing Ubuntu. When accessing this partition and selecting the relevant music file, the text under it behaves correctly similarly to when on desktop.

I did try searching for this in case it was a setting in Nautilus that needed to be altered (eg music preview) but could not find anything.

Can anyone tell me what needs to be done?

Many thanks for any info provided

Cheers

---

### Post by ~Plue on 2011-03-31
1. press alt+F2 and run gconf-editor, then navigate to apps/metacity/general and change the value of 'button_layout' from [I][B]
close,maximize,minimize:[/B][/I] to [B][I]:minimize,maximize,close

[/I][/B]or, you could install and use [ubuntu-tweak]("http://ubuntu-tweak.com/") to change the button layout to the right

2. have you tried closing and reopening the window?

---

### Post by risk_reversal on 2011-03-31
Many thanks for your reply ~Plue 

1. Bless you :). I will also give *Ubuntu Tweak* a go, looks very interesting. Seems to be a little like TweakUI in Windows.

2. I tried closing and reopening the window with no luck. I tried copying the same music file from the extended partition directly to the Music folder and it did the same ie all text lines exposed. 

The only place where I can copy with no issues is the Desktop (or Desktop folder).

In the event that the following info maybe useful, I was trying Ubuntu 10.10 via the Live CD afew days ago and it did the very same thing. When  I was trying the Live CD version, after a while the text did autohide itself after quite some time. However, after it had done so and I copied that music file to another folder (eg from Music to Downloads), it would do the same thing again.

This is also not a single file with this same text issue.

Oh well if you can think of anything (eg setting or other) let me know.

Cheers

[COLOR=Red]_EDIT_: I think I may be closer to a solution. If I right click in the Music folder (not the file), then go to *Arrange Items*, I can get the text to auto hide correctly if I select *Manually*. Selecting *By Name,* or other, leaves the full text visible.

Is this the way that it is supposed to work?[/COLOR]

---

### Post by Blasphemist on 2011-03-31
This is a pretty detailed explanation on moving the buttons to the right side. [http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/](http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/)

I will also add that when using the Natty Unity desktop the buttons on the left in the top panel seems good and right.

---

### Post by risk_reversal on 2011-03-31
Cheers many thanks.

---

