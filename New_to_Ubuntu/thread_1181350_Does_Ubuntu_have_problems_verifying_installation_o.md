---
title: "Does Ubuntu have problems verifying installation on a SATA drive?"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by Carolla on 2009-06-07
Some of you may remember that I installed a dual boot system by opening the installation CD in Windows and used Wubi to set it up. I did this with 8.10 and it seemed to work (though there was an error message) but the whole thing was confusing and I ended up putting my CD back in and running the liveUser CD. I downloaded 9.04 and tried the same installation with it, same problem. 

I get an error message saying it fails to verify and that maybe there is a problem with the CD or the drive. However, if I click "OK" without putting the CD back in the drive, it seems to run alright. 

I'm installing it on my SATA drive, not drive C: that has Windows. Does that cause a problem? 

Thanks for helping me out so far... :)

---

### Post by k3lt01 on 2009-06-07
I fought with my SATA drive setup for over a week and found the problem was my BIOS setting. After I adjusted it to boot to "other" everything was fine and dandy.

---

### Post by QIII on 2009-06-07
Can you try again and give us the exact text of the error?

There should be no problem installing a dual boot on separate physical drives.  I always do that anymore.

I just make sure that Ubuntu is on the first SATA header so my BIOS looks for that drive first, and I can modify my menu.lst to boot to Windows from GRUB.

If you feel comfortable with a phillips screwdriver, I could talk you through that.  If you'd rather not (and I can understand why you wouldn't!), then there are a number of tutorials for setting up a second Linux drive when Windows is on the first one.

But first, could you give us the exact text you are seeing?

---

### Post by Carolla on 2009-06-07
Ok, I tried something - since there was a couple of Windows files on that drive that I didn't need, I reformatted the SATA drive and reinstalled. No error message! Yay! 

Then it booted into the user interface and wanted my name and password. I had made a very simple password, but it didn't accept the name/password combination. Is there some way to retrieve my username/password? I'm sure I remember it right, but it's a no go. 

Thanks!

---

### Post by mrbiggbrain on 2009-06-07
is numlock on, also remember linux is case sensitive

Nick is not the same as nick is not the same as NICK.
sometimes you forget this for your user name (i do it sometimes because i have a cap at the beginning and dont hit shift

---

### Post by Carolla on 2009-06-07
> **mrbiggbrain said:**
> is numlock on, also remember linux is case sensitive

Nick is not the same as nick is not the same as NICK.
sometimes you forget this for your user name (i do it sometimes because i have a cap at the beginning and dont hit shift

I tried the various combinations - I can't imagine I'd type my username any other way than I normally do, but I also didn't realize I needed my password to just boot the OS. I'm not concerned about security, if I can recover my password (or maybe my username! lol ) is there some way to just turn that part off?

I guess I'll go reboot to Ubuntu again and play around with it.

---

### Post by k3lt01 on 2009-06-07
System > Administration > Login Window gets you the program to change the automatic login settings. Go to the Security tab and at the top you will see "Enable Automatic Login" tick the box next to it and underneath it will say "User" use the drop down and find your username. Select your username click "close" at the bottom of the page, you should now be set to login without having to remember your username and password.

Now, having said all that, you WILL need to remember your username and password (in its correct form) to make any changes to your system. Ubuntu is very security conscious and will ask for these details anytime you want to change anything system related.

---

### Post by Carolla on 2009-06-08
Ok, thanks! I managed to figure out the combination of username/password and case that worked, so all is well until the next thing I want to try.

THANKS! :)

---

