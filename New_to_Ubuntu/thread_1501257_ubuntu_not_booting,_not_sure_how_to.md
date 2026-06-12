---
title: "ubuntu not booting, not sure how to"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by scotcella on 2010-06-04
Hi all,

I am having a few issues with my laptop. I'll provide a background first before I get to the problem.

Background: I have a Sony Vaio Laptop, which is dual booted with Windows Vista and Ubuntu which I believe is 9.04. I have had no problems with the dual boot up until I came back from my holiday.
 
Problem: Ubuntu just won't boot (argh!), however I am able to boot into the Windows partition without any issues. Currently I am on using the Ubuntu Live CD as I don't have the patience to use Windows. 

Anyway, when I came back from my holiday I discovered that was an extra kernal (there were 3, now there are 4), I believe that my housemate may have accidentally clicked on the update button while I was gone.
I am not sure how to fix the ubuntu partition, and would like some advice where to start and how. Is it a simple matter of removing the kernal? I tried entering the older kernals but was still not able to log into any of them.

ANy help will be greatly appreciated. :(

---

### Post by anewguy on 2010-06-04
> **scotcella said:**
> Hi all,

I am having a few issues with my laptop. I'll provide a background first before I get to the problem.

Background: I have a Sony Vaio Laptop, which is dual booted with Windows Vista and Ubuntu which I believe is 9.04. I have had no problems with the dual boot up until I came back from my holiday.
 
Problem: Ubuntu just won't boot (argh!), however I am able to boot into the Windows partition without any issues. Currently I am on using the Ubuntu Live CD as I don't have the patience to use Windows. 

Anyway, when I came back from my holiday I discovered that was an extra kernal (there were 3, now there are 4), I believe that my housemate may have accidentally clicked on the update button while I was gone.
I am not sure how to fix the ubuntu partition, and would like some advice where to start and how. Is it a simple matter of removing the kernal? I tried entering the older kernals but was still not able to log into any of them.

ANy help will be greatly appreciated. :(

From reading your post about multiple kernels, I assume that means you do at least get the grub menu.  When you say Ubuntu doesn't boot, does it do anything when selected from the menu?  Does it go to a blank screen or perhaps a blinking cursor?  Have you tried one of the recovery console options from the grub menu to see if it will boot to the command line?  When you try to boot Ubuntu, *if* you get a blank screen or blinking cursor, try holding down ctrl-alt and pressing F1 -> does a terminal window appear?

When booted from the LiveCD, open a terminal window and post back the output from the following:

lshw | grep VGA


Thanks
Dave ;)

---

