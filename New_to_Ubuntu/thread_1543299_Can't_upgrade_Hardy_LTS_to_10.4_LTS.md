---
title: "Can't upgrade Hardy LTS to 10.4 LTS"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by bitmechanic on 2010-07-31
I'm jealous of all the posts showing problems updating individual Ubuntu programs. My Dell M1330 shipped with Hardy Heron pre-installed  --  I can't upgrade to 10.4 LTS at all!

I used the update manager to install all 8.04 LTS updates. That worked fine. Then tried to upgrade to 10.4 LTS. I get the message: "W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY (XXXXXXXXXXXXXXXXXX).

My understanding is that I should be able to go directly from 8.04 LTS to 10.04 LTS. Perhaps I need to install each and every incremental upgrade instead of jumping so far all at once? I'd be willing to wipe the hard disk, if necessary, and start from scratch, since the current situation is a no-go. Any thoughts or guidance much appreciated from this Linux N00b.

Best,
Bitmechanic

---

### Post by Terl on 2010-07-31
I would really recommend doing a clean install of 10.04 rather than doing the upgrade.  It is much cleaner in my opinion.  I know it seems like you are going from one LTS to the next, but there were many changes between the two versions.  In my opinion there is less "breakage" and hassle just doing a fresh install of the newer version.

---

### Post by louieb on 2010-07-31
Depends - if you have 3rd party software or in your case ppa repositories. the upgrade path is pretty much hit or miss. It is recommended to disable ppa and none official software sources.   

Before trying the upgrade again: 
Try going to System>Administration>software sources  and turn off the ppa repository and any other 3rd party repositories you may have set up. 

When I when from Hardy to Lucid - did a fresh install - had several ppa's and programs installed that were newer versions  - it just made sense for to got that route.

---

### Post by dwbsr on 2010-08-01
> **bitmechanic said:**
> I'm jealous of all the posts showing problems updating individual Ubuntu programs. My Dell M1330 shipped with Hardy Heron pre-installed  --  I can't upgrade to 10.4 LTS at all!

I used the update manager to install all 8.04 LTS updates. That worked fine. Then tried to upgrade to 10.4 LTS. I get the message: "W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY (XXXXXXXXXXXXXXXXXX).

My understanding is that I should be able to go directly from 8.04 LTS to 10.04 LTS. Perhaps I need to install each and every incremental upgrade instead of jumping so far all at once? I'd be willing to wipe the hard disk, if necessary, and start from scratch, since the current situation is a no-go. Any thoughts or guidance much appreciated from this Linux N00b.

Best,
Bitmechanic
I might be missing something but if you can't get Ubuntu 10.04 from  the update manager, go to  [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) and download the iso or for USB stick, run it, and it should give your the option to upgrade to 10.04.

---

