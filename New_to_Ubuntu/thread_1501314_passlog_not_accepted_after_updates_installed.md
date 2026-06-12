---
title: "pass/log not accepted after updates installed"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by Primus1 on 2010-06-04
Hi,

I downloaded and installed some updates this morning. The computer needed to be restarted, so I restarted. The machine displayed lots of writing instead of the usual quick boot. Then it said something like "not been checked, forcing check", more writing too fast for me to read. Then asked for login and password, I had changed it in the past for a more secure one as recommended. When the computer asks for a login or pass as far as I know there is only one and I use that for everything. The machine would not accept any combination of either the old password or the new, just kept saying "incorrect", in despair I keyed "ctrl+alt+del"
The computer rebooted and acted as normal with the usual login screen and accepted my password!

Anyone understand why this happened and is it a sign something is wrong?


:confused:

---

### Post by cariboo on 2010-06-04
Try booting from your Live CD, and once at the desktop open a terminal and type:

```
sudo fsck -a /dev/sda1
```

Substitute the partition you have Ubuntu installed on for the one in the example above.

---

### Post by Primus1 on 2010-06-05
Thanks for that, the computer started properly without any problem this morning so don't know what happened.
Is it ok to run the code you gave me now the problem seems resolved? does it give a log of errors for example or should I not run it now?

I have 2 hard drives, Lucid on both. I only use the Lucid on the secondary drive and want to put Windows XP on the first drive which is 'C'. But of course the C drive has all the boot options. How could I put xp on the first drive and still have the option to boot into Lucid on the second drive please?
Hope that makes sense.

Reading up I have used a script that a member provided which shows boot information for all drives installed and have a txt file showing the results which I can upload if that would help you to see what is going on.

the script is called: boot_info_script055.sh

Thanks

---

