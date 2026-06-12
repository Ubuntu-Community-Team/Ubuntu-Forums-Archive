---
title: "Restore image of older version on top of fresh install?"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by head2head on 2011-04-28
Not sure where to put this so hope it's in the right place.

I've currently got 10.04 installed (updated from 9.10) and have am image of the drive to use to restore. I'd like to do a clean install to 11.04 as I've got audio problems on my 10.04 install and am trying to work out the best way to do this without losing my applications/config files etc.

I'm assuming restoring the image of 10.04 on top of 11.04 won't work very well? 

I'd like to do this as cleanly as possible - I'm a bit nervous about it if I'm honest!

Any help greatly appreciated!

---

### Post by Paddy Landau on 2011-04-28
I'm a bit confused with your query. Do you want to install 11.04 or 10.04?

If I understand you correctly, this is what I suggest.

[LIST=1]
[*]Back up your entire [FONT=Courier New]/home[/FONT] folder. Ensure you have included all hidden files and folders (i.e. those starting with a ".").
[*]Install your new system (10.04 or 11.04 or whatever you are using). This would wipe out your [FONT=Courier New]/home[/FONT] folder.
[*]Restore (from your backup) your entire [FONT=Courier New]/home[/FONT] folder.
[*]Only as needed: When you need an application, install it (it's so fast & easy with Ubuntu that it's not an issue).
[/LIST]
HTH

---

### Post by mörgæs on 2011-04-28
Agree on most, but I would not as a first step copy the hidden configuration files to the new system. You might risk bringing an error with you.

Begin the fresh 11.04 without adding the old configuration files, but keep them within reach if needed.

---

