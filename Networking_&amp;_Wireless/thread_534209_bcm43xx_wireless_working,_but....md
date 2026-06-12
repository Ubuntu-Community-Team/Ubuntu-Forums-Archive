---
title: "bcm43xx wireless working, but..."
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by loevans on 2007-08-24
Hello all.  Semi-new to linux, freshly new to ubuntu.  Love it so far...only thing I see that is a draw back is the lack of ability to cache root or su key in xwin session.  that would be nice (maybe an advanced feature) that way I wouldn't have to worry about the following issue/question I have.  

I have the bcm43xx (gotta love the free dell)...got it working with the manual ndiswrapper setup.  No worries (well, not many), but when I run the wireless assistant to view the available networks, i get the message the I do not have the rights to run the program.  I can then see the networks, but not connect to any of them.  I can go to a term session and run sudo wlassistant and that works and I can connect (with no other changes).  I'm OK with that...and I really don't have a problem going the sudo route, but was wondering, is there a way to change the wireless assistant link on the applications menu to run as sudo?  another option, I guess would be to kill the existing one and put in another program icon referencing sudo wlassistant...any suggestions here?

other than this...i have had NO problems with the feisty fawn.  I'm actually thinking of calling my daughter that when she gets a little overzealous from now on.

Thanks to the community.  Linux rox, windows sox.

le

EDIT: 
found out how to do it...just right click on  applications, edit menu, click through to the wireless assistant and change the program from wlassistant to gksudo -S wlassistant

very very cool

---

### Post by leohart on 2007-08-25
I have bcm43xx wireless too and I run the native driver flawlessly. Did you try the native driver yet?

There is also a deb that you can download from online and it should just works.

---

