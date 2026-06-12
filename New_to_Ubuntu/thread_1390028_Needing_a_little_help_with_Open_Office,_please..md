---
title: "Needing a little help with Open Office, please."
date: 2010-01-25
forum: New to Ubuntu
---

### Post by L Campbell on 2010-01-25
I'm using 8.04 on my PC and I recently 'copy/pasted' an email into OO word processor so I could save it as an ' .odt ' file.

OO crashed and ever since then I get the 2 screenshots before I can get to the 'untitled' page.

Initially I deleted file '12-08-07' but nothing ended up in Trash.

Is there something I can do to stop having this 'recovery' process each time I need to use OO ?

TIA

---

### Post by L Campbell on 2010-01-25
> **L Campbell said:**
> I'm using 8.04 on my PC and I recently 'copy/pasted' an email into OO word processor so I could save it as an ' .odt ' file.

OO crashed and ever since then I get the 2 screenshots before I can get to the 'untitled' page.

Initially I deleted file '12-08-07' but nothing ended up in Trash.

Is there something I can do to stop having this 'recovery' process each time I need to use OO ?

TIA

Adding screenshots.

---

### Post by Sir Jasper on 2010-01-25
Hi,

A long time ago I had a similar problem, but it cleared itself.

As a last resort (failing a better suggested fix), if you save all your data (say, copy and paste it to another location) you could then uninstall OO, then reinstall it and copy back your data.

My regards

---

### Post by L Campbell on 2010-01-25
> **Sir Jasper said:**
> Hi,

A long time ago I had a similar problem, but it cleared itself.

As a last resort (failing a better suggested fix), if you save all your data (say, copy and paste it to another location) you could then uninstall OO, then reinstall it and copy back your data.

My regards

Thanks, that sounds like a good idea.

Now, bearing in mind that I am quite a dunce with Linux, would removing from Synaptic, then re-installing from there be the way to go, or is there a better way?.

Kind regards.

---

### Post by Sir Jasper on 2010-01-25
Hi again,

Using Synaptic would be fine, though you might delay that for a day a more as there may well be an easier fix suggested.

My regards

---

### Post by jsoellner on 2010-01-25
Have you tried clicking 'cancel' instead of 'start recovery'?

If you do that you shouldn't be asked if you want to recover the document the next time you start OOo.

Of course, you may have already done this so forgive me if that is the case.

---

### Post by halitech on 2010-01-25
This is just a guess but maybe check Tools - Options and in the OpenOffice,org category (should be the first section that is opened) there is a sub-category called Paths. Check and see what the path is for backups and then go to that directory and see if the file is there and delete it. I know you say you deleted a file but was that file in your backup folder or just in your home folder?

---

### Post by howefield on 2010-01-25
If none of the above work and before you take the reinstall sledgehammer advice, you might try renaming the hidden openoffice.org folder.

Next time open office opens, it will rebuild the configuration files.

Places menu > Home Folder and press the ctrl + H keys, rename the .openoffice.org folder, then try again.

---

### Post by L Campbell on 2010-01-25
> **jsoellner said:**
> Have you tried clicking 'cancel' instead of 'start recovery'?

If you do that you shouldn't be asked if you want to recover the document the next time you start OOo.

Of course, you may have already done this so forgive me if that is the case.

EXCELLENT, thank you, that seems to have fixed it.

Kind regards.

---

