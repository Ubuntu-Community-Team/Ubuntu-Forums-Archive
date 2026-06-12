---
title: "Open programs quit showing in gnome panel"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by oldsoundguy on 2010-09-23
OK .. had a program I tried to install from a usually reliable site and it really kludged up my desktop.  
After running re-build and fixing packages on boot I still have the issue in gnome where there is no "open  program" indicator on the lower panel where they normally show up.

Any clue as to steps to get that function back?

(mods .. if this needs to be moved .. feel free.)

---

### Post by bradleypariah on 2010-09-23
I feel like there's no way your solution could be this simple...
So, sorry if this is not the problem you are trying to describe:

If I understand you correctly, you simply cannot see the buttons for open windows in your panel?

Have you already tried right-clicking on the panel, choosing "Add to Panel...", and then chosen "Window List"?

If you have, but it didn't work, I have seen something similar before.
I had to right-click every single millimeter across the entire panel until I found an option for "Remove from Panel".
I was like, "Remove ***what ***from panel??" because I couldn't see anything where I was clicking.
After that, I just added "Window List" again and it worked.

---

### Post by 0N3 on 2010-09-23
What was the program and can you post a picture of whats happening?

---

### Post by oldsoundguy on 2010-09-23
> **bradleypariah said:**
> I feel like there's no way your solution could be this simple...
So, sorry if this is not the problem you are trying to describe:

If I understand you correctly, you simply cannot see the buttons for open windows in your panel?

Have you already tried right-clicking on the panel, choosing "Add to Panel...", and then chosen "Window List"?

If you have, but it didn't work, I have seen something similar before.
I had to right-click every single millimeter across the entire panel until I found an option for "Remove from Panel".
I was like, "Remove ***what ***from panel??" because I couldn't see anything where I was clicking.
After that, I just added "Window List" again and it worked.

OK .. doing the second "fix" got the open programs to show but I had to remove them and then re set the "show" .. but that got it .. thanks for the help!

---

### Post by bradleypariah on 2010-09-23
Word!  :-D

---

### Post by oldsoundguy on 2010-09-23
> **0N3 said:**
> What was the program and can you post a picture of whats happening?

Not to leave you hanging (since the problem was solved) but the program was: 
wcamstudio

the link I was given on a forum post sent me to ws4slgl.org
in turn the program was linked to the Source Forge site.
Downloaded the .deb to my desktop
opened the required program and when I did, the program installer kept opening over and over again .. finally had to rt alt/print screen/k to kill all.
Went to re-boot and it was not happening so used rebuild option in grub .. including rebuilding dkpg. A couple of attempts at rebooting hung up but finally it loaded .. then I discovered the gnome glitch .. since fixed.

ALL is back to normal from what I can ascertain.

---

