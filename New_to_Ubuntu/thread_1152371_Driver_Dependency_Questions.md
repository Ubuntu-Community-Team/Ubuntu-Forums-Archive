---
title: "Driver Dependency Questions"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by Doctor Colossus on 2009-05-07
Hello, all!  I've just installed Ubuntu 9.04 on my [WiBrain]("http://www.wibrain.com"), a handheld 'UMPC'* computer.  I received it with Ubuntu 7 installed, which worked OK.  I installed Windows XP on a separate partition.  Immediately afterward I tried to upgrade to Hardy Heron, and that seemed to destroy my Linux installation.  I wasn't in the mood to try fixing it for a long time, since I'm very comfortable with Windows.  Well the other day my friend recommended Jaunty Jackalope to me, so I decided to give it another try and overwrote my old, corrupted installation without notable incident.

Now my problem is that of finding drivers.  As you can see, it's a relatively rare device I'm operating on.  There is some community of Ubuntu users for it, but I haven't found news yet from anyone else attempting upgrade to Jackalope on it.  The latest supplied drivers are [here]("http://code.google.com/p/wibrain-b1l/downloads/list"), for version 2.6.24 of the kernel -- the 7th and 9th downloads listed are the ones I seek in particular, for the touch-screen and wireless LAN card.

Attempting to install either of these on my current installation yields errors because they want the package "Ubuntu supplied Linux modules for version 2.6.24"/"linux-ubuntu-modules.2.6.24.16-generic".  Now I see that Jaunty Jackalope ships with 2.6.28 of the kernel...  Is it really so fundamental a difference that this package can't use libraries from the newer version to install correctly?  Is there a way to redirect its dependencies to the latter kernel's counterpart meta-package?  Or can I simply install the slightly antiquated modules for kernel ".24 to make these drivers work? (I notice that upon setting out to do such a thing, I am warned that "[I] likely do not want to install this package directly.")  Is it possibly to downgrade the kernel?  Should I simply uninstall Jaunty Jackalope, and try to revert to Hardy Heron?

Please understand that I'm a rank newb with Linux.  I've accumulated a basic knowledge about *nix command-line, principally via FTP and telnet, so I'm not afraid of that.  But I've tried reading a bit about packages and such, and I haven't been able to find answers to my questions yet -- which may be too simple or obvious for other people to discuss!  I am a bit overwhelmed.  That's why I'm posting here, in hopes that someone else can enlighten me somewhat without too much trouble on their part.

Thank-you!
Doctor Colossus

* UMPC = ultra-miniature PC (handheld).

---

### Post by tyroeternal on 2009-05-13
Unfortunately, from what it looks like, your best bet is going to be running only Hardy.  I do not know much on this front, but in general I do not think that drivers built for old kernel versions build against the new ones usually.  (I've had these problems too)

I also do not know about reverting jaunty to an old kernel (or if that is even possible), but I can tell you up front that just installing hardy will be easier and the best route.  That source for drivers also included a document for installing hardy with pictures!  (thankfully it has pictures with English writing, because the document is in Japanese?!).

---

### Post by Doctor Colossus on 2009-05-15
Thank-you, **tyroeternal**, for your sound advice!  [-:

I saw that document (it's in Korean) and, yes, the screenshots do look profuse enough to guide me very well!  I'll try installing Heron tomorrow or the next day, and let you know how it goes...

(Ooh...  Actually, I just found an interesting thread about this [here]("http://ubuntuforums.org/showthread.php?t=992906") -- it describes the exact video problem I experienced, and which utterly befuddled me, when I upgraded from Gibbon to Heron.  Very helpful...)

Too bad it doesn't look like I will be able to try Jackalope any time soon though... :sad:

---

### Post by tyroeternal on 2009-05-16
Well I know that running an older OS is not usually that exciting, but I hope that Hardy will work well for you!

---

### Post by Doctor Colossus on 2009-05-27
Just to follow up, I did get Hardy installed without much ado.  For any Wibrain owners looking for advice about this, I found [this thread]("http://www.umpcportal.com/modules/newbb/viewtopic.php?topic_id=3161&viewmode=flat&order=ASC&start=0") at UMPCportal.com useful, and made a short post about my experience there.

Thanks again for your advice, tyro.

I do hope Wibrain will eventually provide support for later kernels...

---

### Post by tyroeternal on 2009-05-28
I'm glad to hear things are at least working under hardy.  There do seem to be people making some effort on the project, over on the google code page, so there is always hope!

Don't shy away from asking questions if you ever have any more :D

---

