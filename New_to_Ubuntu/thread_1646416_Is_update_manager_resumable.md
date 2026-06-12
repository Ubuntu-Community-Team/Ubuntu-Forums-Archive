---
title: "Is update manager resumable?"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by degarb on 2010-12-15
I need to shut down the machine.  It took 4 hours to download the 200 plus megs of updates.  Now it is hanging on the half way mark, saying it is installing.  But the progress bar hasn't budged in over an hour. 

If I shut down now will it resume installing, or need to redownload everything?

---

### Post by degarb on 2010-12-15
It is hanging on unpacking the python minimal.  Probably something corrupt.

---

### Post by degarb on 2010-12-15
No it is certain that I cannot get past python minimal.  Ever.   I don't see any way of deleting the install of these updates.  I suppose wipeout installation and reinstall, and hope after 4 or 5 hours it works next time.  A bit severe, but I don't see an alternative.  Yet.

---

### Post by JOHNNYG713 on 2010-12-15
You could boot in to recovery mode, drop to root shell with networking and **sudo apt-get update** .works a lot faster, for me anyway!

---

### Post by spook1980 on 2010-12-15
this has happend to me before there should be a little hidden thing-a-mijig that will show terminal out put maybe u need to do something there like accept a licence agreement or a changed config file

---

### Post by degarb on 2010-12-15
> **spook1980 said:**
> this has happend to me before there should be a little hidden thing-a-mijig that will show terminal out put maybe u need to do something there like accept a licence agreement or a changed config file


well, I killed and forced a reboot  sudo apt-get install -f to repair the structure,  I then unclicked all the python stuff I could see,  then hit install.   it is still hanging on unpacking the replacement python minimal package.

I don't see how dropping to recovery console will help.  Might try that.  but will wait for a better hint or response, if someone has one.

---

### Post by degarb on 2010-12-15
I rebooted into the recovery console.  I then did a repair packages.

IT WIPE OUT the installation!!!  I cannot get into the recovery console or ubuntu.  

cant mount anything like /  cause device not present.
udev not configured is error message.


Who knows this could be the fault of failure for up to second status reporting by the recovery.  Maybe I hit some key too soon.

---

### Post by degarb on 2010-12-15
What now?

---

