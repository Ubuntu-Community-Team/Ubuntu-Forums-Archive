---
title: "w32codecs (medibuntu) vs ubuntu-restricted-extras"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by kaixi on 2009-03-29
Which one should I install? Should I install them both?

---

### Post by glennric on 2009-03-29
Just install the one that installs by default.  That should be the one in the medibuntu repository.  There isn't a ubuntu-restricted-extras repository, so I am not sure what you are talking about with that.

---

### Post by Ms_Angel_D on 2009-03-29
On a standard install I install both Ubuntu restricted extras from add/remove programs as well as the w32codecs & libdvdcss2 from medibuntu.

---

### Post by coffeecat on 2009-03-29
> **glennric said:**
> There isn't a ubuntu-restricted-extras repository

You're quite right, but there **is** an ubuntu-restricted-extras metapackage which comes from one of the standard Ubuntu repositories and which provides a number of restricted codecs and a few other things like msttcorefonts. Hence the OP's question. If you don't beiieve me, have a look in Synaptic. :wink:

Ho hum.

**Edit:** forgot to add - **kaixi**, I installed w32codecs from medibuntu without installing ubuntu-restricted-extras first (I'd forgotten - seems to be becoming a habit :(). When I eventually installed ubuntu-restricted-extras, it removed a couple of codecs that had come in with the w32codecs package - presumably to avoid conflicts. I don't know what happens if you do it the other way around.

---

### Post by mkvnmtr on 2009-03-29
I install both and also quite a few gstreamer packages.

---

### Post by glennric on 2009-03-29
I already figured that out.  That was pretty much covered by MetalHellsAngel's post.  So the best answer seems to be install "w32codecs" and "ubuntu-restricted-extras", and if you want to play dvds install "libdvdcss2".  

CoffeeCat: There really was no reason for the attitude in your post.

---

### Post by kaixi on 2009-03-30
Thank you all. That made things clearer.

---

