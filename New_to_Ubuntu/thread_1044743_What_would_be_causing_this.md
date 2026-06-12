---
title: "What would be causing this:"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by 3dz on 2009-01-19
I have gotten the repository DVDs, so far I have installed a driver for my display card.  So that I could get desktop effects to work.  I had no problem installing the driver, and it works.
Then I tried to install a package for video codecs, so I could watch movies.
I went to synaptic, and mark the appropriate packages.  When I click the apply a dialogue popped up asking for disk 3 of the DVD repositories:
[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/screenshot-synaptic.png[/IMG] 

I inserted the disk, and clicked OK.  It disappeared for about a 10th of a second, and then reappeared.  I did that over and over again, and got the same thing.
Frustrated, I clicked cancel.  The downloading status, completed three quarters of the way through.  Then I went to this error:
[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/synaptic.png[/IMG]

Judging from this error, I thought I might have a loose IDE cable to my DVD-RW.
But then I noticed this:
[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/screenshot-file-browser.png[/IMG]

According to the file browser, disk 3 is in the drive.  I don't understand, what is going on here?
I would greatly appreciate enlightenment.
Thank you in advance. :confused:

---

### Post by spiderbatdad on 2009-01-19
I believe what you want to do is go to System>>Administration>>Software Sources>> Uncheck the cd-rom source. Check the universe and multiverse repositories.

---

### Post by pdtpatrick on 2009-01-19
you can install all the codecs you need by doing this:

sudo apt-cache search Gstreamer

now install the Gstreamers listed or just the ones that fulfill your needs by entering:

sudo apt-get install Gstream-x-x

Just incase you havent done so already, you can install flash java and all that good stuff for firefox by installing:

sudo apt-get install ubuntu-restricted-extras

---

### Post by Terl on 2009-01-19
It sounds like the OP is using disks as his repository so I believe the internet repositories are not what he needs.

What exactly do you have.  You mention having a dvd yet later you say cd's.  May not be important but I am curious.

Have you used the cd's to set up anything else?  Has it been a problem.

---

### Post by 3dz on 2009-01-20
Correct Terl, I'm not yet on the Internet with that computer.  That's a whole another problem. I have the DVD set, of the repositories.
I see now that I have to sometime soon, get on the Internet. It was something that pdtpatrick said, about installing ubuntu-restricted-extras. Sometime later, I want to install the restricted extras.
I don't believe that these repository DVDs have any restricted extras.  But if I could get some of the codec's installed and working,that would be great.

I did manage to get the display driver installed from the DVD set.
After that, the desktop affects worked. I also noticed, a faster response in the applications.  But after that, I couldn't get anything to install.  I've been trying to install wine also.

any ideas?

---

### Post by sleepyjon on 2009-01-20
This probably wont be that helpful, but after browsing the cd did you try again with the cd already in and mounted?

---

### Post by 3dz on 2009-01-20
Yes, I did.  But thanks for being helpful.

---

