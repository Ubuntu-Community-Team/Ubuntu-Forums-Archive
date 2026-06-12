---
title: "how to install OO.org 3.0.1 on Ubuntu 9.04"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by al.adab on 2009-05-02
hello 

I've decided to have a fresh installation of Open Office on Ubuntu 9.04. I dowloaded the file on my home folder (called "daniele") through archive manager. 

I also removed the existing Open Office by typing 

"sudo apt-get -y remove openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer" 

in Terminal. 

This is the name of the Open Office file: *OOO300_m15_native_packed-1_en-US.9379* as it appears in my home folder. 

Could you please tell me

1) how to proceed from here to install Open Office (what command shall I give in Terminal?)
2) what to do to check if some residue (icons?) of the old version (the one I deleted) is still sitting somewhere (I seem to recall someone saying that - if this is the case - the new OO.org extension manager can give you a hard time - I also seem to recall it may be necessary to search "Filesystem" for such residue (or icon or whatever it is). 

Many thanks!!!

---

### Post by gjoellee on 2009-05-02
OOo 3.0.1 is the default OOo installation in Jaunty.

---

### Post by stretch427 on 2009-05-02
If its not already installed all you have to do is type
```
sudo apt-get install file_name
```

---

### Post by al.adab on 2009-05-02
yes, I know, but I removed it anyway...now I'd like to re-install it. The file is ready sitting in my home folder (after extracting it through Archive Manager). Now I just need to know what command I should use to install it. Can you help? Thanks!

---

### Post by Didius Falco on 2009-05-02
Open Synaptic, click the **Status** bar on the left, in the windows above, click **Not Installed (residual or config)** and mark all the OOO packages for removal. Actually, if there are any others list there, you may as well clean that out as well - it's just leftovers from packages you removed.

Then follow the directions here to install what you downloaded:

[http://ubuntuforums.org/showthread.php?t=1054126](http://ubuntuforums.org/showthread.php?t=1054126)

---

### Post by stretch427 on 2009-05-02
if its in your home folder use same command only  add  /home/file_name    after ...install
ie sudo apt-get install /home/...
 or use synaptic as stated above.

---

### Post by al.adab on 2009-05-02
got it. it worked. OO.org seems to be working much better now. Thanks!

---

### Post by stretch427 on 2009-05-02
And just so you know you can mark your threads SOLVED. 

Just something I like to do... the Completion factor lol

CHeers!

---

### Post by al.adab on 2009-05-04
I'd too like to mark the thread as "solved" as I used to...but I can no longer find the option "solved" under "Thread tools" or anywhere else...any idea?

---

### Post by Didius Falco on 2009-05-04
> **al.adab said:**
> I'd too like to mark the thread as "solved" as I used to...but I can no longer find the option "solved" under "Thread tools" or anywhere else...any idea?

Edit your very first post, when the edit window appears, click the **Go Advanced** button under the edit window. When the new screen loads, you can edit the thread title - simply go to the front of the title, type solved (it'll give you variations on it to choose from) and save the post.

---

