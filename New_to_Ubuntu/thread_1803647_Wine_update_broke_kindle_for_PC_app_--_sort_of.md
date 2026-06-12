---
title: "Wine update broke kindle for PC app -- sort of"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by crazybasenji on 2011-07-13
Even though I've had Ubuntu on my laptop for a while (I have Lucid), I don't always understand the lingo, so am putting this thread here. 

I recently managed to get the correct version of Wine installed so that I could use the Kindle for PC on my laptop specifically so that I could read "Packing for Mars" on a larger screen than the one on my Android. I was soooooo happy.:)

Then this morning I had one of those little orange "update" flags on the toolbar, and it was an update for Wine. I was a little hesitant, but thought, "oh, what could it hurt?" I should have hesitated. I should have just said NO! Now I can open every book in my (small) Kindle library EXCEPT "Packing for Mars." 

Here's what I've tried:

[LIST=1]
[*]"Remove from device and re-download." Only moves the book to Archive. Can't be removed from Archive -- only moved back to Home.
[*]Went to folder "My Kindle Content" and deleted the files for the book. Opened Kindle, the book was still there. Still wouldn't open.
[*]Un-installed and re-installed both Wine and Kindle app. Of course, re-installing Wine also re-installed the update. Don't know why I thought that would help.
[*]Sent email to Amazon support for Kindle. They emailed back that they deleted the book, issued me a refund, that I should re-purchase and re-download the book. Did that. Still won't open. Sent email back to Amazon and came here.
[/LIST]
:confused:  Now what? Back to reading my book on my phone, I guess. Has anyone else had issues with the Wine update?

---

### Post by LowSky on 2011-07-15
Sounds like your .wine folder within your /home folder has been corrupted for that book. Even though you delete wine or the kindle app the .wine folder still exists and can give you some issues.

Easiest fix is to delete the .wine folder.  then reinstall the kindle app and see if that fixes your problem. If it doens't work I dont know what else could be the problem.

By the way the .wine folder is hidden, use CTRL + H to un-hide the folder.

---

### Post by crazybasenji on 2011-07-15
> **LowSky said:**
> 

By the way the .wine folder is hidden, use CTRL + H to un-hide the folder.

Thank you for the hint! I tried it. Didn't work. Some days technology is just awesome, other days, it's just awful. Bleah. Maybe I'll just buy the book.

Thanks for trying. Maybe the next update will undo the voodoo. :)

---

### Post by crazybasenji on 2011-07-21
My book is back! I had a Linux update yesterday, and this morning I thought I'd just check to see if anything had changed, and it opened to the last place I had bookmarked. Just like magic. On my birthday. Happy Birthday me! Technology is *awesome!*

---

