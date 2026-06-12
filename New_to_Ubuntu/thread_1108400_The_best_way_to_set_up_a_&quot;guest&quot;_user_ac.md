---
title: "The best way to set up a &quot;guest&quot; user account"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by humphreybc on 2009-03-27
... for a Bed and Breakfast guest computer. I bought an old computer for $50 and I am going to put Ubuntu 8.10 on it for our guests to use at our Bed and Breakfast.

What is the best way to allow guests to browse the internet and perform simple functions (such as word processing, printing, calculator etc) but lock them out of modifying any system files or settings?

The computer would be on most of the time, and the user (because it will be different every time) would not know a password - so I would need to turn off the password for the "guest" account, or have them automatically login.

Also, is there a plugin for Firefox or a program that runs in the background that limits the SIZE of a file to be downloaded? I would like to put a size limiter of say, 40mb as the largest single file that could be downloaded. I was thinking of speed-capping the computer, but that would make it slower than necessary, and a bandwidth limiter wouldn't work (eg. 100mb bandwidth: 1st user in the morning uses up 80mb, 2nd user is only left with 20mb). It would be unfair.

Your suggestions please!

---

### Post by LowSky on 2009-03-27
Go to the Top panel, click on System > Admin > Users and Groups (at the bottom)

you can add a "guest user"  there if you like, even set what type of access they have.

I have no idea how you could Cap their internet download use. Technically using the net to stream videos like youtube would effect that. Best options I think might be port blocking, or restricting website use, progrmas like Dan's guardian can do that I believe.

---

### Post by humphreybc on 2009-03-27
In theory they should just be checking their emails so it wouldn't really matter if youtube videos were blocked.

---

### Post by CRIMPS on 2009-03-27
Firefox has a great filter addon... called FoxFilters.  This way, nothing embarrassing happens ;)

---

### Post by skintythe1andonly on 2009-03-27
I have done on our home pc that may work for you. You could setup a guest account, set it up exactly the way you want it.... desktop wallpaper, theme, delete the firefox history .... whatever way you want. Then follow the following thread

[http://ubuntuforums.org/showthread.php?t=1032757]("http://ubuntuforums.org/showthread.php?t=1032757")

Essentially make a backup of this account to your root direcotry, and then run a bash script whenever you log out to reset this directory. This will also give your guests the ability to download large files if they wish as essentially it will get deleted afterwards when you log out.

As far as I can remember I followed the above thread with some modifications... but I cant remember exactly how now.

---

### Post by humphreybc on 2009-03-27
Sweet I will look into that.

Can Ubuntu create a user that has no password? Or can you at least turn off the password requirement to login?

---

### Post by skintythe1andonly on 2009-03-27
Ah that was the other thing I did.... cant remember exactly how I did it but I could change it to be what was on the live CD by changing some file so that the password is <Enter>. Cant remember now. Its in a thread around here somewhere, look around a little more.

---

### Post by humphreybc on 2009-03-27
> **skintythe1andonly said:**
> I have done on our home pc that may work for you. You could setup a guest account, set it up exactly the way you want it.... desktop wallpaper, theme, delete the firefox history .... whatever way you want. Then follow the following thread

[http://ubuntuforums.org/showthread.php?t=1032757]("http://ubuntuforums.org/showthread.php?t=1032757")

Essentially make a backup of this account to your root direcotry, and then run a bash script whenever you log out to reset this directory. This will also give your guests the ability to download large files if they wish as essentially it will get deleted afterwards when you log out.

As far as I can remember I followed the above thread with some modifications... but I cant remember exactly how now.

Looks like Interpid does this anyway and I am intending on using Intrepid so that should be all good.

---

### Post by skintythe1andonly on 2009-03-27
Thats what I thought when I was setting it up but it was not what I was expecting. The guest account in Intrepid is not quite the same as in windows or something like that. You have to be logged in to activate the guest session. You log in and then click to activate the guest session. It is for say ..... using a laptop and then giving it to a friends who wanted to use it for a bit and you didnt want them poking around your stuff. You cannot log into it from the login screen. This was a deliberate decision be the ubuntu team (may have been the gnome team). This may not be so convenient for a computer in the corner in a B&B.

Have a look here for more details
[URL="http://ubuntuforums.org/showthread.php?t=934972&page=2"]
http://ubuntuforums.org/showthread.php?t=934972&page=2[/URL]

---

