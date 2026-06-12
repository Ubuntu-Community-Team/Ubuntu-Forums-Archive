---
title: "Wine"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by corncob on 2010-05-02
I just made a fresh install of Lucid, went into Synaptic and installed Wine.  I then tried to install Print Shop Ensemble III, an old windows program that I like to make Mother's Day cards, etc with, but it just doesn't install.  I right-click on setup.exe on the CD, select open with Wine windows program loader, and a window opens briefly and closes, and nothing happens. I've installed this in the past with no problems.  What could be wrong?

---

### Post by cuberts on 2010-05-02
> **corncob said:**
> I just made a fresh install of Lucid, went into Synaptic and installed Wine.  I then tried to install Print Shop Ensemble III, an old windows program that I like to make Mother's Day cards, etc with, but it just doesn't install.  I right-click on setup.exe on the CD, select open with Wine windows program loader, and a window opens briefly and closes, and nothing happens. I've installed this in the past with no problems.  What could be wrong?did you edit the ld configuration script to add the liblber to it?
if  not then it won't find the library when wine asks it for it.

---

### Post by corncob on 2010-05-03
> **cuberts said:**
> did you edit the ld configuration script to add the liblber to it?
if  not then it won't find the library when wine asks it for it.

Oops, I meant to post this in the Absolute Beginner's Forum.  I never heard of these things.  Is this anything you could walk me through?  In any case, thanks for the reply.

---

### Post by roger_1960 on 2010-05-03
Hi

After you installed wine from synaptic, you must go to the GUI menu for Wine (in the main menu) and select "configure wine"  Accept the defaults.  I think the error you have been getting happens if you forget to do this.

---

### Post by madjr on 2010-05-03
> **corncob said:**
> I just made a fresh install of Lucid, went into Synaptic and installed Wine.  I then tried to install Print Shop Ensemble III, an old windows program that I like to make Mother's Day cards, etc with, but it just doesn't install.  I right-click on setup.exe on the CD, select open with Wine windows program loader, and a window opens briefly and closes, and nothing happens. I've installed this in the past with no problems.  What could be wrong?

hmm, this program is like old (1998 :0), why not use something else?

maybe it's a sign you need to substitute it or try something new :)




you could use something like krita (if you prefer something other than gimp)
[http://krita.org/](http://krita.org/)

or pinta (still in dev.)
[http://www.ubuntugeek.com/pinta-paint-net-clone-for-linux.html](http://www.ubuntugeek.com/pinta-paint-net-clone-for-linux.html)


and for slideshows:
[http://ubuntuforums.org/showthread.php?t=668705](http://ubuntuforums.org/showthread.php?t=668705)

[http://www.photofilmstrip.org/3-1-Media.html](http://www.photofilmstrip.org/3-1-Media.html)



or online
[http://www.got-free-ecards.com/Mothers-Day-ecards/](http://www.got-free-ecards.com/Mothers-Day-ecards/)

adobe air app
[http://www.frameshow.com/ecards.htm](http://www.frameshow.com/ecards.htm)


you can let us know which one(s) you decided to go with :)
also since i can't use the windows program you have, which of the above is the most similar or does the same job? others may want to use this

---

### Post by yunone on 2010-05-03
> **madjr said:**
> hmm, this program is like old (1998 :0), why not use something else?

maybe it's a sign you need to substitute it or try something new :)




you could use something like krita (if you prefer something other than gimp)
[http://krita.org/](http://krita.org/)

or pinta (still in dev.)
[http://www.ubuntugeek.com/pinta-paint-net-clone-for-linux.html](http://www.ubuntugeek.com/pinta-paint-net-clone-for-linux.html)


and for slideshows:
[http://ubuntuforums.org/showthread.php?t=668705](http://ubuntuforums.org/showthread.php?t=668705)

[http://www.photofilmstrip.org/3-1-Media.html](http://www.photofilmstrip.org/3-1-Media.html)



or online
[http://www.got-free-ecards.com/Mothers-Day-ecards/](http://www.got-free-ecards.com/Mothers-Day-ecards/)

adobe air app
[http://www.frameshow.com/ecards.htm](http://www.frameshow.com/ecards.htm)


you can let us know which one(s) you decided to go with :)
also since i can't use the windows program you have, which of the above is the most similar or does the same job? others may want to use this




good post, thanks!

---

### Post by corncob on 2010-05-04
> **madjr said:**
> hmm, this program is like old (1998 :0), why not use something else?

maybe it's a sign you need to substitute it or try something new :)




you could use something like krita (if you prefer something other than gimp)
[http://krita.org/](http://krita.org/)

or pinta (still in dev.)
[http://www.ubuntugeek.com/pinta-paint-net-clone-for-linux.html](http://www.ubuntugeek.com/pinta-paint-net-clone-for-linux.html)


and for slideshows:
[http://ubuntuforums.org/showthread.php?t=668705](http://ubuntuforums.org/showthread.php?t=668705)

[http://www.photofilmstrip.org/3-1-Media.html](http://www.photofilmstrip.org/3-1-Media.html)



or online
[http://www.got-free-ecards.com/Mothers-Day-ecards/](http://www.got-free-ecards.com/Mothers-Day-ecards/)

adobe air app
[http://www.frameshow.com/ecards.htm](http://www.frameshow.com/ecards.htm)


you can let us know which one(s) you decided to go with :)
also since i can't use the windows program you have, which of the above is the most similar or does the same job? others may want to use this

Thanks for the info.  I'm going to try these but moving kind of slow with everything else happening right now. (Accepting the Wine defaults didn't help.)  I was looking for my backup disk thinking possible corruption but then its not installing other things either -- tried Faces, German Now, Photoshop Elements by way of testing.
I know I'm back in the last century with Print Shop Ensemble III but at the time there were a lot of 3rd party graphics floating around the bulletin boards which I downloaded so I have huge graphic libraries to go with it.
I'll let you know how it ends up.

---

### Post by Mark Phelps on 2010-05-04
Don't know when Print Shop Ensemble came out, but the little I could find dates it to 1997.  The WineHQ site link below lists the compatibility testing results:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=384]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=384")

If the version is newer than "3", it's not going to work -- no matter what you do.

---

### Post by corncob on 2010-05-05
> **Mark Phelps said:**
> Don't know when Print Shop Ensemble came out, but the little I could find dates it to 1997.  The WineHQ site link below lists the compatibility testing results:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=384]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=384")

If the version is newer than "3", it's not going to work -- no matter what you do.

Yes, it says "1997".  I installed it in VirtualBox (XP).  Seems okay although I haven't gotten my Mother's Day card to print yet lol.

---

