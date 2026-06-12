---
title: "Text Data from cut disappeared: is it recoverable?"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by greenewbie on 2011-05-04
A day's work of mine has just gone missing from an Open Office Text document, after doing a CTRL + X to paste it to a new document.  I stupidly closed (saying yes to save the change) the original, before I did CTRL + V in the new document but my PC refuses to paste the info.  I also tried Paste in the menu and Paste Special, in desperation but to no avail.
I now believe I inadvertently digged an even bigger hole for myself by desynchronizing the folder of this document from my Ubuntu one account, as I wanted to access it before the mess up change I'd made to my document got through to it.  On accessing my Ubuntu1 account, I see that none of the files in my PC's desynchronized folder appear on it.  So it looks like that potential method of recovery has now been lost.
I'm sure I saw in the past an application on my PC to view (and hopefully recover) data in the clipboard, but it doesn't seem to be on it now. So I downloaded "Parcellite" clipboard manager application and that didn't help either.
I had a brief look at opening my original text document with "Archive Manager" (something I know NOTHING about) in the hopes that I'd be able to access the latest change I made to it (ie the cut text which has vanished).  If anybody knows of a way a novice can access that lost info, I'd be VERY grateful to hear from you.
Or would I perhaps be able to recover my lost info through a type of "System Restore" (as I know is found on Windows), I know roughly the time when I made the disastrous cut described above?
I have searched the documentation website and forums but the notes only seem to refer to recovering deleted files, rather than information from a file which hasn't been deleted. The accident happened just a few hours ago and I daren't turn off my PC, as I'm still hanging on to the hope that I can get the info from my wretched clipboard!
Thanks in advance!

---

### Post by matthewbpt on 2011-05-04
I'm afraid that after closing an application, anything from that application disappears from the clipboard, so unless yo have a backup of the document then there's nothing you can do in that respect. Dropbox allows you to roll back to a previous version of a file from their Web Interface, I don't know if Ubuntu One supports this. I would recommend you contact the Ubuntu One customer service by email and ask about recovering a previous version of a file on their servers, they *may* be able to do it. In the meantime don't make any changes to that file to cause Ubuntu One to update it again.

Good Luck!

Matt

---

### Post by greenewbie on 2011-05-04
> **matthewbpt said:**
> I'm afraid that after closing an application, anything from that application disappears from the clipboard, so unless yo have a backup of the document then there's nothing you can do in that respect. Dropbox allows you to roll back to a previous version of a file from their Web Interface, I don't know if Ubuntu One supports this. I would recommend you contact the Ubuntu One customer service by email and ask about recovering a previous version of a file on their servers, they *may* be able to do it. In the meantime don't make any changes to that file to cause Ubuntu One to update it again.

Good Luck!

Matt

Ok Matt, thanks very much, but it looks like it'll be easier for me just to redo my work.  I do CTRL + V every day....I could have sworn my PC will memorise the last thing I've pasted into the clipboard until I switch if off! As an aside, thanks for the insight into Dropbox which I'd vaguely heard about, it has a promising report on Wikipedia.

---

### Post by rg4w on 2011-05-04
> **matthewbpt said:**
> I'm afraid that after closing an application, anything from that application disappears from the clipboard...
Interesting.  It seems very different from how Clipboards work on other OSes.  Is this by design?  If so, what's the user benefit?  Forgive me if I'm overlooking something obvious, but anything that can potentially cause data loss would seem a serious issue that would be looked into with great care.

---

### Post by searchfgold6789 on 2011-05-04
Actually, all the data is probably still on your clipboard. When I close OpenOffice, all the copied data is still there, at least for me.
There is a clipboard organiser tool built in to the panel, but you may have to enable it by adding it to the panel. My bet is that it will still be there.
Good luck,
 - search
P.S. +1 rg4w

---

### Post by jmore9 on 2011-05-04
Does your open office give you a chance to recover the document.  Sometimes i find that the document i was just using is in the recovery area.

---

### Post by greenewbie on 2011-05-04
> **searchfgold6789 said:**
> Actually, all the data is probably still on your clipboard. When I close OpenOffice, all the copied data is still there, at least for me.
There is a clipboard organiser tool built in to the panel, but you may have to enable it by adding it to the panel. My bet is that it will still be there.
Good luck,
 - search
P.S. +1 rg4w

Thanks very much for your reply. I've looked time and time again for anything to do with a clipboard in my Open Office menus and toolbar, including hunting in the customize button and I can't find anything.  I have O.O. 3.2, and I fear that if I click update I'll reduce my chances even further of recovering the info from the clipboard. I've looked at length in the O.O help menu but nothing has helped! I've looked under Tools - Options - Graphics Memory and alas according to the current setting it's a measly 10 minutes.  What's the +1 rg4w reference? (I searched rg4w's previous postings but didn't find anything to help me here: hoping not to appear too dim here!)

---

### Post by greenewbie on 2011-05-04
> **jmore9 said:**
> Does your open office give you a chance to recover the document.  Sometimes i find that the document i was just using is in the recovery area.

Apparently not, no! :( Nothing ventured, nothing gained I clicked on File - Reload; I also found in the help menu, restoring the "Graphics output" (it looked potentially promising to me) with the command shift + CTRL + R but that didn't work either (is this what you meant by the "recovery area"?)
I believe I'm at the end of the line on this one......

---

### Post by matthewbpt on 2011-05-05
> **searchfgold6789 said:**
> Actually, all the data is probably still on your clipboard. When I close OpenOffice, all the copied data is still there, at least for me.
There is a clipboard organiser tool built in to the panel, but you may have to enable it by adding it to the panel. My bet is that it will still be there.
Good luck,
 - search
P.S. +1 rg4w

If you use a clipboard manager then the clipboard persists when closing programs, but if you haven't enabled one then it doesn't and the data is deleted. Look in the Software Centre for clipboard and you'll find many programs to manage your clipboard. KDE comes with a clipboard manager built in, Klipper, which is quite useful.

---

### Post by alphacrucis2 on 2011-05-05
There is also a clipboard manager built for gnome

[URL="https://help.ubuntu.com/community/glipper"]
https://help.ubuntu.com/community/glipper[/URL]

---

