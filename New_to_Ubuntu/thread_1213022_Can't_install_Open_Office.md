---
title: "Can't install Open Office"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by roobee on 2009-07-14
Trying to upgrade to Open office 3.1 I somehow managed to delete the whole bang-shoot. So I thought I'd head for the package manager and start from scratch again. It seems I've deleted dependencies all over the place - I can't install via Synaptic or using an open office CD...

Any help with sorting this out please? 

This is the error message I get when I try to mark open office.org-core:

openoffice.org-core:
 Depends: libdb4.7  but it is not installable
  Depends: libgtk2.0-0 (>=2.14.1) but 2.12.9-3ubuntu5 is to be installed
 Depends: libhunspell-1.2-0 (>=1.2.4) but it is not installable
 Depends: libhyphen0 but it is not going to be installed
  Depends: libneon27 (>=0.28.2) but 0.27.2-1 is to be installed
 Depends: libstlport4.6ldbl  but it is not installable
 Depends: ure but it is not going to be installed

I've also noticed that some of the options have the box filled in green, I can't select them...

Any suggestions for how I can fix this most appreciated.

Thanks, ruby

---

### Post by philinux on 2009-07-14
Not sure if this will work but. Go through your list of dependencies,find and install them via synaptic one by one.

Green filled box means already installed.

---

### Post by roobee on 2009-07-14
Thanks Phil, will give it a go - my biggest problem seems to be that many of the other options I choose kick up a similar problem about dependencies...
So I guess it's a pain thing. 
Oh well.

Thanks again, ruby

---

### Post by philinux on 2009-07-14
> **roobee said:**
> Thanks Phil, will give it a go - my biggest problem seems to be that many of the other options I choose kick up a similar problem about dependencies...
So I guess it's a pain thing. 
Oh well.

Thanks again, ruby

One thing to try is this. Before the above.

Use synaptic and mark for complete removal of any openoffice* packages.

Then in terminal use

sudo apt-get autoremove.

Then try to install openoffice from synaptic again.

---

