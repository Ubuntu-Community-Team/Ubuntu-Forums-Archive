---
title: "Am I 32 or 64?  Can someone tell me? (bits that is )"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by Jedcurtis on 2011-02-20
:confused: Hi everyone!  Thanks ahead of time for helping.  I just went from a dual-boot situation with Windows 7 Ultimate 64bit, and Ultimate Edition 2.8 Gamers Edition.
I got rid of and started from scratch with Ubuntu 'Maverick Meerkat' a week or so ago.  Seems as if it is a little slower than before, and it hit me that I never chose an architecture while installing this time.
I did use the Ubuntu CD I received in the mail to do the install.  When I run the dpkg --print-architecture command in terminal it says i386.  Even with a quadcore intel processor, should it not say AMD64?
Just curious, and also a little puzzled as to how I could have inadvertently done this.  Is there a quick little fix to address this shortsightedness on my part or am I in for a total re-install to get the 64bit architecture?
I'm definitely no pro, but I thought I was at least capable of choosing the right install from the get go.  Oh well...  Again, thanks
Jed :)

---

### Post by deconstrained on 2011-02-20
```
$ uname -m
```

---

### Post by PaulReaver on 2011-02-20
sorry to be the bearer of bad news but if it says i386 you're running 32bit..

but you already knew that???



we've all done something similar at least once.... I even made the mistake of installing openSuse once :lolflag:

---

### Post by Jedcurtis on 2011-02-20
Yeah, I already knew...
Oh well nice part about Ubuntu, it installs easily enough!  Back later when prob is resolved...
Jed

---

### Post by cariboo on 2011-02-20
Just for the record, [shipit]("https://shipit.ubuntu.com/") only ships 32-bit versions.

---

### Post by Jedcurtis on 2011-02-20
Burning a cd now to get the re-install going.  Double checked and sure enough the CD I received is 32bit.  Guess I'll have to pay better attention in the future.  Hey you gotta love accidental learning, right?
Jed

---

### Post by Jedcurtis on 2011-02-20
Ok, an hour later, I'm back and blazing with the 64bit version going this time.  Re-installed and all is golden.  Gotta love Ubuntu.  With Windows I'd be tomorrow sometime getting it all back...
I love this OS!

---

### Post by PaulReaver on 2011-02-20
nice one.... only an hour???  did that include all the updates too???

---

### Post by Jedcurtis on 2011-02-20
Updates running right now in the background!  Aint Ubuntu the greatest?  It is truly an impressive OS.
Jed :P

Update Manager after a little settings change is updating 311 mb.  Just under 200 to go.  Still blows Windows out of the water for install time.  The updates dl and install faster too.  And from the looks and feel of things, there is a noticeable difference between 32 and 64 bit versions when speed is considered.  I should have benchmark tested a couple of things first but oh well.  It's my personal laptop, and as far as I'm concerned it's the fastest one I've ever had.  Laptop or desktop or server for that matter.  Amazing how far they've come...

---

### Post by PaulReaver on 2011-02-20
yup :)

---

