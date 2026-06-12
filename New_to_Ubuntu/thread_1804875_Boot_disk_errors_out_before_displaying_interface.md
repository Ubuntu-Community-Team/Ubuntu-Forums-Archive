---
title: "Boot disk errors out before displaying interface"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by malcolm1 on 2011-07-15
A tech friend of mine suggested I download the current version of Ubuntu to boot a Windows/Vista Dell Inspiron 330 PC that appears to have hard drive problems.
 
I downloaded the current ISO file from the download page and placed it on a CD which I then used to restart the ailing PC.
 
I get past the opening splash screen which has two small icons at the bottom with no instrutions. I click ENTER and get a list of languages and choose English. I then select the option that allows me to try Ubuntu without installing.
 
A splash screen displays with the name Ubuntu and a series of moving dots. After several minutes, a command-line prompt for (apparently) native Ubuntu displays. I don't know Linux, so this is gibberish to me.
 
The following error lines display at the top of the screen, being clipped off on the left-hand side so that some of the letters are missing:
 
**General error mounting filesystems**
**maintenance shell will now be started**
**NTROL-D will terminate this shell and reboot system**
**groups: command not found**
 
Rebooting the system simply leads again to this result.
 
The tech friends--who isn't local--said she had never had the user interface fail to appear.
 
Any ideas?
 
Thanks,
 
Malcolm

---

### Post by Rubi1200 on 2011-07-16
Hi and welcome to the forums :-)

The first steps towards troubleshooting this involve the following:

1. post the full specifications for the computer

2. check the integrity of the image: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

3. burn to CD at the lowest speed: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

4. if the computer allows it, try booting from USB after burning the image to a USB stick with [UNetbootin]("http://unetbootin.sourceforge.net/")

Let us know if this gets you further.

---

### Post by malcolm1 on 2011-07-17
Thank you for your reply, Rubi1200.
 
I think the fix here is beyond my capability. For one thing, I am in a Windows environment and  have no means of typing linux instructions to test the image integrity. If Ubuntu sells tested, working CDs that provide the expected functionality of the ISO file, that may be a better way to go. 
 
I appreciate your ideas. If I had linux and/or were more computer savvy, I would definitely see if I could make them work.
 
Best wishes,
 
Malcolm

---

### Post by Rubi1200 on 2011-07-17
You can check the integrity from within Windows; see further down the page on the first link I gave you.

Also, you can order a CD from Canonical (the company that provides Ubuntu) so that is definitely an option to consider.

---

