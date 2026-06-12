---
title: "What happened to Fspot"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by brawd on 2009-09-20
There used to be a time when I could plug my sony camera, or my wife could plug her kodak camera into the computer and upload the pics due to the actions of Fspot, which would then copy the pics to a folder in my (or her) home folder, using the date to create a folder. These pics could then be used for email, facebook or simple looking at.

On my computer at least (AMD dual core 64 bit) it's stopped doing that.

These days when we plug in a camera Fspot detects it and uploads the pics. We then tell it to copy said pics and that is where it all has changed.

All that is available to us now are two files, no pics. The computer knows about the pics because provided the camera is plugged in and you run Fspot it shows them. Even using the export command doesn't give us a viewable pic.

So how do I handle this situation. There is no way to back up the pics.

brawd

---

### Post by blackened on 2009-09-20
F-spot can act pretty crazy if the catalog gets screwed up. I would suggest this method as a remedy:

1. Find where F-spot creates its backup for catalogging (mine is ~/Photos, I think that's the default). Make a copy of the entire folder and place it on your desktop. In my case (change the directory names to fit your needs) that would be ```
cp -r ~/Photos ~/Desktop/photobackup
```

2. Open F-spot, go into browse mode, ctrl+a to select all photos, Edit -> Remove From Catalog, then Photo -> Import, select the backup you made on your desktop and re-import all your photos.

The bad part about this is that if you had your collection tagged already, then you'll have to re-tag everything. A small price to pay for not loosing all your photos.

---

### Post by MrWES on 2009-09-20
> **brawd said:**
> There used to be a time when I could plug my sony camera, or my wife could plug her kodak camera into the computer and upload the pics due to the actions of Fspot, which would then copy the pics to a folder in my (or her) home folder, using the date to create a folder. These pics could then be used for email, facebook or simple looking at.

On my computer at least (AMD dual core 64 bit) it's stopped doing that.

These days when we plug in a camera Fspot detects it and uploads the pics. We then tell it to copy said pics and that is where it all has changed.

All that is available to us now are two files, no pics. The computer knows about the pics because provided the camera is plugged in and you run Fspot it shows them. Even using the export command doesn't give us a viewable pic.

So how do I handle this situation. There is no way to back up the pics.

brawd

Take a nice step up and install Picasa:

[http://picasa.google.com/linux/]("http://picasa.google.com/linux/")

---

### Post by brawd on 2009-09-21
Thanks for your help, I shall try the copying folder bit first and see how it goes.

I'll take the step up later maybe. I have to be a bit cautious and give my wife chance to get the hang of a new program.

Frankly stepping up to picassa together may be impossible - I'm bound to tread on her toes.

Thanks again,

brawd

---

