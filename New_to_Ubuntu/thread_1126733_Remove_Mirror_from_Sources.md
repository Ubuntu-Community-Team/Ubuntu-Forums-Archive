---
title: "Remove Mirror from Sources"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by Luxx on 2009-04-15
I'm not sure where this question belongs. I could not find any info via google searches or on forums, only advice to add other mirrors or repositories. I want to REMOVE a mirror. 

I added [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) intrepid main universe and it didn't work. That is not a problem since I found another source that DID work for my purpose.

The above mirror shows up only below the list of main repositories in Software Sources, Ubuntu Software tab where it says: 
"Download from:" (in the drop-down field). It does not show up in the Third Party Software tab at all.

Upon reloading I get the following error message: 

"An error occurred
The following details are provided:
E: The package cache file is corrupted
E: _cache->open() failed, please report.

W: Duplicate sources.list entry [http://mirrors.xmission.com](http://mirrors.xmission.com) intrepid/universe Packages (/var/lib/apt/lists/mirrors.xmission.com_ubuntu_dists_intrepid_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://mirrors.xmission.com](http://mirrors.xmission.com) intrepid/universe Packages (/var/lib/apt/lists/mirrors.xmission.com_ubuntu_dists_intrepid_universe_binary-i386_Packages)"

As I stated, I found a source that works and that source shows up under Third Party Software.

How can I get rid of the duplicate source which does not? Is there a command I can use?
Thanks for any help.

---

### Post by taurus on 2009-04-15
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
And remove that repo.  Then save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Twitch6000 on 2009-04-15
open up a terminal or press alt f2 and type sudo gedit /etc/apt/sources.list

you can then remove what you added from there.

If you use the alt f2 way check the run from terminal button.

Then when you update again you will not have anymore problems :).

---

### Post by Luxx on 2009-04-15
Thanks Taurus and Twitch. I knew it was something simple, but couldn't remember exactly what to type in. You guys replied so fast --- thank you again.

---

