---
title: "restricted extras for your codecs"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by macheted01 on 2009-10-18
Does anyone know about how much space on the hard drive is needed to install the restricted extras package?

---

### Post by OpenGuard on 2009-10-18
```
sudo apt-get install ubuntu-restricted-extras

```

Before you hit Y ( Yes ), read what it says ( download / space required ).

---

### Post by macheted01 on 2009-10-18
OK, cool, thanks.

---

### Post by MelDJ on 2009-10-18
go to synaptic and search for ubuntu-restricted-extras. then right click the package and press properties and you will be able to see its size

---

### Post by mcduck on 2009-10-18
If you are short on disk space, you might not want to get the whole ubntu-restricted-extras -package, as it contains other stuff than just the codecs (like Adobe Acrobat, which is usually not necessary since Gnome already has it's own PDF reader, evince, and Java, which you might not need at all.)

So, instead of installing the ubuntu-restricted-extras -package you could just open Synaptic Package Manager, do a search for "gstreamer" and install all the gstreamer codec packages you need.

(Actually I always do it this way, no matter how much disk space I have available, since I have absolutely no use for Acrobat or Java.. :))

---

### Post by Paqman on 2009-10-18
> **mcduck said:**
> it contains other stuff than just the codecs (like Adobe Acrobat)

Actually Acrobat's not included. You might be thinking of Flash?

---

### Post by OpenGuard on 2009-10-18
> **mcduck said:**
> If you are short on disk space, you might not want to get the whole ubntu-restricted-extras -package, as it contains other stuff than just the codecs (like [COLOR=Red]**Adobe Acrobat**[/COLOR], which is usually not necessary since Gnome already has it's own PDF reader, evince, and **Java**, which you might not need at all.)


Red - doesn't exist
Black - only in Hardy and 64bit Jaunty ( if I remember right )

---

### Post by mcduck on 2009-10-18
> **Paqman said:**
> Actually Acrobat's not included. You might be thinking of Flash?

At least it was in some previous Ubuntu version. I haven't followed the contents of that package more closely after that. But the main point was that it includes other stuff than just the codecs, so if you only want the codecs you might want to install them individually.

---

### Post by Paqman on 2009-10-18
> **mcduck said:**
> I haven't followed the contents of that package more closely after that.

The repos are actually [pretty searchable]("http://packages.ubuntu.com/search?keywords=restricted+extras&searchon=names&suite=all&section=all") for that kind of thing.

But yes, you can of course install the contents separately if you like.

---

### Post by macheted01 on 2009-10-18
Yeah, I am very short on disc space. I intalled restricted codecs earlier and pretty much used up everything I had for space. I than went to add/remove and found them in the Others column and removed them. I was trying to get Totem to play avi files. I can live with just playing mpegs. I will keep that tip in mind though for later. Thanks.

---

