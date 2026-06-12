---
title: "SMB &amp; GUI Failure (Edgy)"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by Nightheir on 2006-12-04
Hello,
Quick Important Info:
I'm still pretty new to Linux or Unix environments but not computers as a whole.  I've only had Ubuntu up for about 2 weeks now.  I'm running 6.10 (Edgy), Nautilus 2.16.1, Gnome.  Yea thats about all I can think of right now.

What I'm doing and The Problem:
I navigate my Nautilus to “smb://{servername}/” then I'm prompted for Username, Domain, and Password.  I enter in all my information and it shows me the first level of shares.  I then choose the share I want to connect to.  So now I'm navigated to “smb://{servername}/Share”.  At this point everything looks just fine.  I see all my subfolders.

Then I try to navigate to the next folder and I get an error saying “Couldn't find “smb://{servername}/Share/myfolder”.  Please check the spelling and try again.”

I had some guys in the office come and take a look.  They hammered around in the CLI for a while and established a connection using the CLI and navigated several levels deep without any problems.  Moved back to Nautilus and had the same problem.  Then they scratched their heads and walked away.

Not sure where else to turn, I've done a lot of searching but no luck.

---

### Post by ingo on 2006-12-06
a quick google came up with this

[http://gnomesupport.org/forums/viewtopic.php?t=10690](http://gnomesupport.org/forums/viewtopic.php?t=10690)

in the old days when i still had to use samba konqueror worked a treat (kde)

---

### Post by Nightheir on 2006-12-08
I think that's a little advanced for me and my current knowledge of Linux but thank you just the same.

---

### Post by ingo on 2006-12-08
well, in that case how about installing kde? As I said, I just to have samba running and Konqueror had no probs doing what Nautilus is apparently stumbling over...

---

### Post by Nightheir on 2006-12-08
That's an idea, but I'm not very fond of KDE.  However I tried to browse the network using Firefox and it had the same exact problem.  I didn't know Firefox could even use smb but I guess you learn something new everyday.  But maybe this proves that its not just Nautilus.

There's a guy just down the hall that is using Ubuntu Edgy and doesn't have any problems, Maybe I can look at his packages and see if he has something special installed.

If that doesn't work I'll try KDE just to see if it will actually work.

---

