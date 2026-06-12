---
title: "Save state"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by guriinii on 2009-10-28
I was wondering if their is a way to save the state of Ubuntu so if something goes terribly, terribly wrong you can revert back to the state it once was.

A friend told me about this, but I haven't found anything about it. Does anybody know?

---

### Post by Sarmacid on 2009-10-28
Not sure if you're talking about something specialized, but you can make an image of your hard drive or just tar the entire partition where ubuntu is installed and restore it later.

---

### Post by guriinii on 2009-10-28
I'm not sure either, but that might be it. How would I do that?

---

### Post by alphaniner on 2009-10-28
Look into CloneZilla or SystemRescueCD.  They are LiveCD Distros that include tools like **partimage** and **partclone**.

---

### Post by Sarmacid on 2009-10-28
Well, if you want to make an image out of your drive, just use dd(changing to the appropriate partition)```
sudo dd if=/dev/sda1 of=myimage.img
```The downside of dd is that the image will be as big as the drive, but that will not happen if you tar the entire file system. It's been a while since I did it so I don't remember, but you shouldn't have trouble finding it if you google for it.

---

### Post by winotree on 2009-10-28
Something simple, yet effective can be found in Synaptic Package Manager.  Open it and click File | Save Markings.  [This will save the name and version number of every installed application].  Enter the file name, click Save full state, not only changes.  [This is most important].  Click Save.  To restore click Read Markings, select your file, click Open. The information will appear in the status bar of Synaptic [as if you were installing a package -- only this time it's many packages].  Click Apply and if I remember that's all there is to that.  [Please correct me if, when trying this, you notice I've forgotten a step].

---

