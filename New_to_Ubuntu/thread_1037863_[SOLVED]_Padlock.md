---
title: "[SOLVED] Padlock"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Georgia boy on 2009-01-12
Hi. Quick question. I put the songs from the music library in Windows media to a CD as data so I could get on one CD instead of a group of them. I then put them in a new folder I created as Music2. When I copied them over I noticed that they had padlocks in the upper right corner of each song. I went into properties and noticed that they were read only and also had the execute block checked. I deselected that box and also set the user(me) to read and write. Did I do this right or is there something else I should have done? I know, dumb question but I don't recall seeing that before. 
Hope that everyone had a great weekend. Mine was peaceful and quiet. Just the way I like it. Slowly moving thing over from the Windows so I can eventually go complete Ubuntu.

Thanks for the help.
Tom

---

### Post by ChildOfMana on 2009-01-12
Yeah the padlock icon is Ubuntu's way of telling you that the read/write permissions are restricted for your user account.

Changing the ownership of the file should do the trick. Also change the read/write permissions if you need to - although leaving them as read-only should be okay unless you need to delete or re-name them (or need to change the metadata).

---

### Post by Captain_tux on 2009-01-12
Are they perhaps DRM?

---

### Post by Georgia boy on 2009-01-12
Thanks guys. Don't know anything abut DRM. I did the read and write under the permissions and removed the checkmark in that block. Locks went away. Figure that I would do that then if I want to move them or whatever I could. I'm constantly learning here. I want to eventually move completley over from Windows. I know that if I have a question I can ask if I don't find it already in the forum. 

This is a great bunch of people here that is always willing to help a person out of a bind. I really appreciate it. So, when I ask a dumb question just remember who's asking. :lolflag:

It is nice to know that I can turn to here for all kinds of help. 
Thanks guys
Tom

---

### Post by ChildOfMana on 2009-01-12
You're welcome :)

---

