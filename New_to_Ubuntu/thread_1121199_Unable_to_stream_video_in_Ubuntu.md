---
title: "Unable to stream video in Ubuntu"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by unicornlover442 on 2009-04-09
As a totally new user to Ubuntu, I didn't realize that when I posted a reply in a previous thread (I think #7044047), that it was already a closed thread. I was trying to follow the directions given by one of the members and got an error message I need help with. Here is my post from the closed thread: Please accept my apologies if I'm doing this incorrectly. Have never posted on a thread b4---I tried to do the commands that
RyanVanDiemen suggested on his thread posted 4 wks ago
At 617a.m. When i did the 2nd line of the command (sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update) I get an error message as follows:W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Can someone please help me??? Does this error message mean that I already have some other type of application already using it??? If so, how do I find out which one it is??
Thanks for ANY help you can suggest.
Sorry I muffed up on my very 1st thread!

---

### Post by Shpongle on 2009-04-09
try   sudo apt-get install ubuntu-restricted-extras

and see [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by jmszr on 2009-04-10
unicornlover442,

This will explain installing medibuntu and the Keyring: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) . For the other problem, this will take care of it:[http://www.ubuntugeek.com/how-to-fix-lock-varlibdpkglock-open-11-resource-temporarily-unavailable-error.html](http://www.ubuntugeek.com/how-to-fix-lock-varlibdpkglock-open-11-resource-temporarily-unavailable-error.html) .

Hope this helps and welcome aboard!

---

### Post by unicornlover442 on 2009-04-10
After I did sudo apt-get install ubuntu-restricted-extras
I finally received a message: 0 upgraded, 32 newly installed, 1 to remove and 0 not upgraded.
Need to get 51.5MB of archives.
After this operation, 82.5MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  w32codecs
Install these packages without verification [y/N]? y

I input y for yes (I hope that is ok). I then got this message (after several "get 1-32 https" responses):

Setting up sun-java6-plugin (6-10-0ubuntu2) ...

Setting up ubuntu-restricted-extras (25) ...
Setting up unrar (1:3.8.2-1) ...

Setting up w32codecs (20071007-0medibuntu3) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

Does this mean I am through??? Can I close the terminal window??? Or do I have to wait for some more responses in the terminal window??? Do I need to restart everything after all this??

Sorry I have so many questions, but I'm very insecure with the terminal commands and I don't want to crash my system!

Thank you again for your patience and help!!!

---

### Post by computermacgyver on 2009-04-10
The "ldconfig deferred processing now taking place" can take a little bit of time, but after that you should be returned to the command prompt. At that point everything is complete and you can type "exit" and hit enter or just close the window with the x.

If you need to restart, you will get a notice in the top right corner of your screen (by the clock).

---

