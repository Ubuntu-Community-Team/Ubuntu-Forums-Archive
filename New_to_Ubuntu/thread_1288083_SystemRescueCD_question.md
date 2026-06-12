---
title: "SystemRescueCD question"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by BobJam on 2009-10-10
I have a question on the SystemRescue CD, specifically how to read what's on my internal HDD via the terminal command line.

The terminal command line defaults to the SRCD root, NOT the internal HDD root.  Consequently, typing "cd /" just gets you back to the same place.  So how would you navigate to the internal HDD root?

I think mapes12 may have answered my question in his excellent "How To" on Partimage here:  [http://ubuntuforums.org/showpost.php?p=7800125&postcount=11](http://ubuntuforums.org/showpost.php?p=7800125&postcount=11)

As I understand it, you need to mount the internal HDD root onto the SRCD virtual machine (I may be using the term "virtual machine" incorrectly), so that it's in the memory and SRCD can "see" it.

But I'm not clear on this, and I'm not sure what the SRCD terminal commands would be to do this.

And a related question . . . what would the FSArchiver commands be in the SRCD terminal?  You can get FSArchiver "example" commands, but these are relative to the SRCD root.  I'd like to see if I can get FSArchiver to read my internal HDD.  In fact, to get a viable FSArchiver file, that's absolutely necessary . . . isn't it?

---

