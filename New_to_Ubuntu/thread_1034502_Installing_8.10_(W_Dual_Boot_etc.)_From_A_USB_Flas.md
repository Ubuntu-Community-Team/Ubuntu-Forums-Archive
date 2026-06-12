---
title: "Installing 8.10 (W/ Dual Boot etc.) From A USB Flashdrive Startup Disk"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by n4lbl on 2009-01-08
Updating my USB startup drive I had some maintenance difficulty but have been running satisfactorily in spite of that.  There were many ticket numbers for what is most likely the same problem, including  but not limited to 279820, 292159, 299894, 301347, 304120, 305817, 306109, 308971, 310855, 314399.  I express this merely to convey the idea that many people seem effected by this problem.  The actual error message was _ErrorMessage: subprocess post-installation script returned error exit status 17_ which I don't know how to look up.  The critical item for me is that I do not understand exactly what maintenance took place.  I don't know how to tell if some fixes were applied and not others.  Therefore I don't know if it is OK to use my startup disk to do an actual install.  Assuming that my maintenance applied to my flash drive is partial I don't know if subsequent maintenance will pick up the pieces and do everything right or not.  Perhaps everything is OK now and maintenance on a real disk will not have the problem.  Please help me to think clearly about this problem.

thanx,,,

---

### Post by Vantrax on 2009-01-08
I would probably suggest recreating the usb startup pendrive if your are worried that it has a problem. Assuming it wasn't being used as a live environment and heavily customized already.

I can say that the usb install does work as I have used it three times in the last week (its faster than a CD). I have an unmodified and non updated version that I update after installing instead of live.

---

### Post by n4lbl on 2009-01-08
If necessary I will start over.  I assumed (wrongly??) that re-customization would be necessary anyway.  What I really wish to hear is that the maintenance system will figure out whatever the current system status is and then select the correct maintenance combination.  If that is the case then I will plow ahead with the system as-is and install on the HD.  Otherwise I will jump thru the flaming hoops and start over.

---

### Post by n4lbl on 2009-01-11
Well, I tried and failed.  Installing from the flashdrive I received an inarticulate message indicating that the partitioning failed.  Then I tried to install 8.10 from the CD that I used to create the flashdrive.  Same inarticulate message.  The CD was validated by the checksum (md5) and the check CD option available upon startup.

I am really thankful that the process did not screw up the windoze installation.

At this point I don't know what to do.  Is there something to do to analyze the problem??  The CD was cut the day that 8.10 came out.  Have there been changes since then that may help??  If so I will cut a new CD but I don't care to as a mere exercise.

The first partitioning option providing a 'suggested' path is idiotic.  Granted, the software doesn't know your plans or mine, but the zero growth for windoze and give the maximum possible to Ubuntu is probably the choice with the very lowest likelihood of acceptance.  Presuming that I try again (I really want Ubuntu to work) my plan is to create _lots_ of filler and then chose that first option.  BTW, that was the option that failed.  I didn't chose custom partitioning because I didn't see anything explicit about swapspace and I believe that that is (or was) an issue.

---

### Post by n4lbl on 2009-01-11
I've decided to move this to the Installation & Upgrades forum at:  [http://ubuntuforums.org/showthread.php?t=1037124](http://ubuntuforums.org/showthread.php?t=1037124)

Thanks for trying.

---

### Post by n4lbl on 2009-01-13
Well, installing from the live CD and live USB drive failed (both at 8.10), but I had the DVD for 8.04 and that worked.  Sure wish that I knew why.  Thanks,,, 

BTW, my complaint about the partitioning options was flat out wrong. I didn't see the slider.

---

