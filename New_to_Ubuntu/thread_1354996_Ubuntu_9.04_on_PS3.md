---
title: "Ubuntu 9.04 on PS3"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by By Azura on 2009-12-14
I ran out of games and thought it might give me something to do.

I did some reading on several Websites (a lot of them are sadly outdated) 

Installs were a success and my PS3 is now running Ubuntu 9.04

After setting up Opera and the Flash Plugin it desperately desired I decided to take a look at the Post Install Tweaks listed here:
[http://psubuntu.com/wiki/SetupPSUbuntu](http://psubuntu.com/wiki/SetupPSUbuntu)

Some of them worked fine, with others I seem to have a Problem.

For example the Sixaxis tutorial.
Connecting it through USB is no problem but getting it to replace my mouse is a whole different story.

One way was outlined on another site, that wanted me to modify my bluetooth files which failed horribly.

The PSUbuntu site also offered SixA, which appeared to work for the moment and while my Controller was paired, it was never recognized by my system, let alone the "Use Sixaxis as mouse" option didn't work there.

The last tool, Sixaxis GUI (Which is apparently outdated) is working perfectly fine. My Controller is recognized by the system when paired via bluetooth, however the "Use Sixaxis as mouse" option still doesn't work.
In the thread dedicated to the tool ([http://psubuntu.com/forums/viewtopic.php?f=4&t=764](http://psubuntu.com/forums/viewtopic.php?f=4&t=764)), I was pointed to another tutorial which told me to edit xorg.conf . 

I read through it, downloaded the tools required and got ready to edit xorg.conf. 
Well, xorg.conf was empty. But another user claimed that this is normal in Ubuntu 9.04 and that it's safe to just add the things from the post. Said and done and did a reboot. 
Upon reboot, Ubuntu told me that "Screen was not found" and pointed to my Xorg.conf. I undid all changes and Ubuntu booted normally.
Nowhere in this thread did I find any information to my problem.
Anyone else got any pointers?

The next thing is Setting the video mode.
[http://psubuntu.com/forums/viewtopic.php?f=4&t=225](http://psubuntu.com/forums/viewtopic.php?f=4&t=225)
I went through the steps and it seemed to work.
Then I got ready to make the changes to kboot.conf
That failed because the specified line in kboot.conf, that I was meant to edit, wasn't there.
Again, searching for my problem wasn't very fruitful.

These two things are giving me a complete Headache and no matter how precisely I follow the tutorials, I always fail. Maybe I'm missing something, but I wouldn't know what.

Another thing that bugs me is, there is no list of essential tools and programs that I should download, manually, after installing Ubuntu (like the xorg tools outlined in the Sixaxis tutorial)

Any help and pointers from anyone who had success with these things?

---

