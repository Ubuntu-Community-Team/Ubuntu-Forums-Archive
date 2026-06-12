---
title: "Side Panel launchers not working."
date: 2010-11-25
forum: New to Ubuntu
---

### Post by s1wood on 2010-11-25
Ubuntu 10.10
I have a side panel with shortcuts to all my common folders and they have suddenly stopped working. I tried removing the panel, starting a new one and replacing them but they still don't work. The top panel is fine.
ALSO, which is probably related, when I go into 'Places' the only connection which works is 'Computer'. Once I open this then all the other folders and drives appear in the left section and can be opened. I can make new shortcuts in the side panel but they don't work. The only panel shortcut which works is 'Computer'.

This happened when I wasn't tinkering with the system at all - working fine one day and not working at all the next.

Please help - now I have a 2nd hard drive I really need those shortcuts.

Susan

---

### Post by s1wood on 2010-11-27
Hallo? 
Nobody got any advice? 
I have set up links on the desktop for now but they do spoil the look - I would like my panel shortcuts back.

Susan

---

### Post by QLee on 2010-11-27
> **s1wood said:**
> Hallo? 
Nobody got any advice? 
I have set up links on the desktop for now but they do spoil the look - I would like my panel shortcuts back.

Susan
Susan, it's possible that more detail could get you more responses.

By "Side Panel" do you mean a panel you've added or something else?

Give an example of a launcher that doesn't work, exact code line you used. Wouldn't hurt to also give the code line from a launcher which does work from your desktop.

Since we aren't looking over your shoulder, it's hard to speculate, even hard to determine what further info might be needed.

---

### Post by s1wood on 2010-11-27
By 'side panel' I mean one of those strips down the side that one can create, remove, shift by right-clicking. By 'shortcut' I mean simply dragging a folder icon onto the panel so that I can open the folder directly from the panel.
The shortcuts will still show the folder name when I pass the pointer over them but nothing happens when I click.
That is all I know about it - I know nothing about any codes. 

Susan

---

### Post by QLee on 2010-11-28
[QUOTE=s1wood]By 'side panel' I mean one of those strips down the side that one can create, remove, shift by right-clicking. By 'shortcut' I mean simply dragging a folder icon onto the panel so that I can open the folder directly from the panel.
The shortcuts will still show the folder name when I pass the pointer over them but nothing happens when I click.
That is all I know about it - I know nothing about any codes. 

Susan[/QUOTE]
Ok, I understand.

Just wanted to make sure we were on the same page with "side panel", we are, it's one you created yourself.

In this by "code line" what I was referring to will be found by right click on the launcher icon (shortcut) and then selecting "Properties", when the properties dialogue box comes up, the "Command:" (that's the "code line") is what you should find. Sometimes people create launchers by entering the commands manually but you did it by drag and drop, which should work too, as long as the system knows which application to use for the location in the launcher.

My suggestion was that we could compare a "Command:" from a launcher (shortcut) that doesn't work to one from a launcher that does work and perhaps we could see a difference that would be relevant to the issue. Anything else would just be blind guesswork.

Edit: Since we appear to be operating in different time zones, I suppose I should go on with another step too.
When you have accessed "Computer" from the top panel, right click on one of the drive icons, or on the filesystem icon and open the "Properties" sheet for it. Then select the "Open With" tab to see what the system thinks it should do. If the system isn't trying to handle the launcher correctly the symptoms you describe could happen.

You won't have to wait for me to get back on the forum, if you describe things clearly, or include a screenshot (picture) if you know how to do that, someone who is operating in your time zone will provide an answer.

---

### Post by s1wood on 2010-11-28
[IMG]file:///tmp/moz-screenshot.png[/IMG]The codes for the launchers are

Documents (not working:  >file:///home/susan/Documents<
         comment:  Open '/home/susan/Documents'

Computer (working):       >nautilus --no-desktop computer:<
 comment  : Browse all local and remote disks and folders accessible from this computer

I can get a screen shot but can't work out how to copy it here!

Documents, Properties: >location /home/susan<

I can't get an 'open with' option for it.

Any use?

Susan

---

### Post by QLee on 2010-11-29
> Documents (not working: >file:///home/susan/Documents<
comment: Open '/home/susan/Documents'

Computer (working): >nautilus --no-desktop computer:<
comment : Browse all local and remote disks and folders accessible from this computer

In order to be able to compare it would be better to have chosen to post the command from the launcher on your desktop (where you stated they do work) for the same launcher, in other words, the working launcher (shortcut) to "Documents". That way we would be comparing two that are supposed to go to the same location, one not working and one working.


You stated that from the top panel, "...when I go into 'Places' the only connection which works is 'Computer'..."

When you have accessed(clicked on) "Computer" from the top panel, you are looking at a file browser window which shows whatever partitions are on your hard disk (shown as drive icons), a cdrom if you have one and "Filesystem" (also shown as a drive icon), is that correct?

If so. right click on the "Filesystem", and select "Properties" from the context menu (should be down at the bottom). After the properties sheet opens, select the "Open With" tab to see what the system thinks it should do. (Note: That Open With tab on the properties sheet has a reset button)

---

### Post by s1wood on 2010-11-29
Got it!
File system was set to open with Wine for some reason. 
Once I altered that to the ordinary open folder option everything worked.

As simple as that - next time I shall know.

Thank you very much for your help.

Susan

---

