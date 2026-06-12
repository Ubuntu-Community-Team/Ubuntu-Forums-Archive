---
title: "Unable to upadte from Ibex to Jaunty"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by rfbeck on 2009-05-26
I've been trying to update from Ibex to Jaunty. I get an error message during the update that says "Error during update" and the process ends. I get several error messages along with it like: "failed to fetch CDROM" etc and "Some index files failed to download, they have been ignored, or old ones used instead."

I also tried several different servers but to no avail. 
please help. Thanks.

______
Robert

---

### Post by Didius Falco on 2009-05-26
Hi,

Going by the error messages, I'm guessing that you have the CD enabled in your Software Sources.

Go to **System/Administration/Software Sources** and make sure the CD is not enabled on the T**hird Party Sources** tab.

That should do the trick.

If not, post again with the new errors...

Regards,

Didius

---

### Post by Sef on 2009-05-26
**Back up** your **data **before upgrading.  Upgrading is not 100% perfect and does fail at times.

---

### Post by rfbeck on 2009-05-27
Didus Falco,

That worked! Thanks a lot.
_______
Robert

---

### Post by Didius Falco on 2009-05-27
You are welcome.

Sef gives some great advice - the first three rules of successful computing:

1. backup your data!
2. backup your data!!
3. backup your data!!!

Regards,

Didius

---

