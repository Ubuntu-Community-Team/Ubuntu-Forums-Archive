---
title: "Need to reenter WPA Password each time at start"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by ptaramelli on 2008-05-22
Hi!
I have intalled Hardy 8.04 from 7.10 in a Dell Inspiron 6400 laptop, I ve installed my wireless with ndiswrapper 1.52 and I use WPA personal, DHCP for dynamic address. Each time I start my PC I have to reenter the password to have wireless working. What can I do to avoid that?, Maybe edit the file where the password is stored to introduce it ??

I had the same problem in 7.10.

Thanks

Pablo

---

### Post by linuxology on 2008-05-22
Thanks to Valloric for originally helping me with this.  I will just repost the info he gave me.  Do an advanced search on my name and you will find it..... Hopefully your /etc/network/interfaces is correct if not you will want to read up on creating it here.... [http://ubuntuforums.org/showthread.php?t=318539]("http://ubuntuforums.org/showthread.php?t=318539")


Create a folder in your home directory. Let's call it "scripts".

Code:

mkdir scripts

Now, you need to create a shell script with that restart command.

Code:

gedit scripts/net_restart

Now put this in the script:

Code:

#!/bin/bash
echo "net_reset attempt" 
/etc/init.d/networking restart

Close it and save it. Now change permissions so it can be run:

Code:

chmod +x scripts/net_restart

Ok, now edit "/etc/init.d/rc.local"...

Code:

 sudo gedit /etc/init.d/rc.local

...and add the full path to your script at the end of the file:

Code:

# run my script to restart wireless after boot
/home/<YOUR USERNAME>/scripts/net_restart

And that should be it. Granted, you could have just added the restart command to "/etc/init.d/rc.local", but I was trying to make a point. The adage about "teaching a man how to fish" comes to mind... scipts are nicer if you have more that one command to execute (even though this isn't that case ).

EDIT: I think this solution for the net restart causes my computer to pause for like 10 seconds during boot at "Starting MTU...". It could be unrelated, and it could be specific to my computer, but anyway, it continues booting after that pause. Just thought I should give a heads-up just in case.

EDIT2: For the solution to the "Starting MTA..." pause, look here.

---

### Post by dcruwys on 2008-05-22
Thank you!!!

The solution after 2 reinstalls.

THANKS \\:D/

---

### Post by ptaramelli on 2008-05-23
Thanks a lot linuxology, it works really fine.

One more thing, as usual, in the spanish forum I didn t have any answer, i will put a link to your post.

Thanks again.

Pablo

---

### Post by linuxology on 2008-05-26
Your very much welcome.  I want to give thanks to valloric who originally helped me with this issue.  Also, maybe the mods should make it a sticky since more and more people it seems to be an issue.

---

