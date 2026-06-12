---
title: "Xsane problem"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by Greenwick on 2011-03-09
I have a CanoScan N656U, and I use an Asus EEEPC 1001px.  I downloaded Xsane, and have been able to use it with Gimp just fine until yesterday.

Here is the problem:  In gimp I choose to create a new image with the scanner.  When Xsane was working properly, two windows popped up.  One gave me a set of controls for things like resolution and color.  The other window allowed me to select specific areas of the picture to scan, which I use because I want to scan at a high resolution and don't want it to take too long or to overwork the scanner.  The last successful scan I made was of something smaller than the whole picture.  

Now when I try to make a scan, it will show up for just a second before disappearing.  Because of this, I am able to complete the scan, but it will only scan the area I selected last time.  Nothing else is wrong with the pictures or Xsane, and there doesn't appear to be anything wrong with my scanner.

I have tried uninstalling and reinstalling Xsane, but with no success.  I also tried scanning outside of Gimp, and that did not work either.

Thank you for any help you can offer.

---

### Post by Daveth on 2011-03-09
as a wild guess, I wonder if deleting the config file in your home drive might reset that value. Mine contains information of scan width and height, and I wonder if yours has got reset. The fact that re-installation does not reset it makes me wonder if it is looking at /home for its rules. Might be complete rubbish, of course, but worth considering:D

---

### Post by Greenwick on 2011-03-27
Thank you so much!  I wasn't sure how to do what you were talking about, but I showed it to my boyfriend and he had an idea.  :D  Now it works.  I am not trying to use Xsane anymore, I'm just using the simple scanner, which isn't as nifty but I assume probably won't cause the same problem.

---

