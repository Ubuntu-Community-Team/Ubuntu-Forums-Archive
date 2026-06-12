---
title: "ndiswrapper 1.9 and Fiesty Fawn"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by ciphermixx on 2007-05-05
Just wanted to make a quick post and say thank you for the great community.  I've got an older HP ze4300 that I've been trying different distros out on, and none of them could manage to get my Linksys WPC54g working with WPA.  The good news is with some great tutorial work on a couple of different threads, I was able to download and install the latest ndiswrapper from sourceforge and get it up and running in 7.04.

All-in-all, it took me about two hours of searching and reading threads, downloading things off my other laptop, burning them to disc and moving them over.  As a casual observer, I think the Ubuntu folks did themselves a real disservice by not making it easier to get ndiswrapper up and running, especially when the currently packaged drivers aren't working with some of the wireless cards.

I do like the Beryl interface though.  Very slick.  NetworkManager is a nice add on.  I can't decide if I like SuSE's YAST and Network control panel or Ubuntu's, though.

Just got Flash installed for the kids (it's their laptop), next stop - installing WINE and seeing if I can get some of their games running.

Thanks again folks!

---

### Post by Floppyjoe on 2007-05-05
I'm pretty sure ndiswrapper is on the Ubuntu install disk. It may not be installed by default because not everybody needs it. You can use the install disk as a repository to install ndiswrapper. This works if you have not installed ndiswrapper from sourceforge.net previously.

I open the package manager by clicking on System/Administration/Synaptic Package Manager.
Then click Edit/Add CDRom and follow the directions for inserting the CD.
Then click reload.
Then search for ndiswrapper.

Cheers,
Floppyjoe

---

### Post by ciphermixx on 2007-05-05
> **Floppyjoe said:**
> I'm pretty sure ndiswrapper is on the Ubuntu install disk.

Well, I did use the synaptics manager to begin with.  It isn't in the "networking" section nor under the "libraries" section.  I did a search, too, and it didn't come up there.  If it is on the disc, that's fantastic.  I just found it was easier to go grab the latest ndiswrapper, install it, and go that route because I couldn't find it on in the disc.

Out of the default install package, when you do a ndiswrapper, you get a "package not installed" error.  With the 7.04 install disc in the drive, doing a sudo apt-get install ndiswrapper-common (which is the package mentioned when you type ndiswrapper on a fresh install) reports back a package not found error.

Anyhow, it's working - I'm happy.  Thanks a ton!

---

