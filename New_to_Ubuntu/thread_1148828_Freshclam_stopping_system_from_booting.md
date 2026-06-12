---
title: "Freshclam stopping system from booting"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by WolfByte on 2009-05-04
Hi all

I have a curious problem with which i can't seem to find a solution to anywhere.

I've installed clamav recently, and upon a restart it gives me this error while trying to update and will go no further.

error: can't get information about db.local.clamav.net: name or service not known

error: can't get information about database.local.clamav.net: name or service not known

Any ideas on how to remove freshclam from my system so i can use my laptop again without having to reload?

I'm still using Intrepid on a Dell D630 if that helps any?

Thanks in advance
WB

---

### Post by Didius Falco on 2009-05-04
To remove it, choose the Recovery Mode boot option, and when you get to the choices screen pick the  **Command Line with Network Access** option - that may not be the exact name for it, it's been awhile since I had to use that, but it should be fairly obvious.

Once you are at the command line, type ```
sudo apt-get purge clamav-freshclam
``` and that will remove it totally from your pc.

Then type ```
sudo reboot
``` and pick the normal boot option. That should get you back to the desktop. 

I hope this helps....

---

### Post by WolfByte on 2009-05-05
Thanks for the swift reply, it did the trick :)

---

### Post by Didius Falco on 2009-05-05
Glad to be of service.Please mark this thread as solved, so if anyone else is having the same problem, it'll be more likely to be found and used in a search.

Regards,

Didius

---

