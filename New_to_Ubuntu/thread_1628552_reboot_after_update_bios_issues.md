---
title: "reboot after update: bios issues"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by terashred on 2010-11-22
I've just installed linux for the first time, and it was going great until i restarted after updating the OS and downloaded the driver for my video card.  Now, it boots into what i think is called the command line interface...?   i type in my my login and password which gets me this:

'your cpu appears to be lacking expected security protections.
please check your BIOS settings, or for more information, run:
   /usr/bin/check-bios-nx --verbose

to run a command as administrator (user "root"), use "sudo <command>".
see "man sudo_root" for details.'

after searching for solutions, i guess i need to enable the 'NX capabilities' in my bios but that option doesn't exist..  is there any other options or do i need an older ubuntu version?
any help would be great.  i dont speak all these languages!

---

### Post by Vi3GameHkr on 2010-11-22
NX stands for No Execute, and on Intel processors, it might be XD which stands for Execute Disable.  I'm not an expert on the issue, but it seems like someone else came across this issue in [this thread](http://ubuntuforums.org/showthread.php?t=1413336).

---

### Post by terashred on 2010-11-23
I dont think my BIOS supports this option and I've heard upgrading these is a pain in the ***. but i dont know.
otherwise, how old  of a version would i need to not require nx compatability?  where could I get it, & once I got it would it simply update to require it?  

i only almost know windows well, so i simply dont know all this jive.

---

### Post by Vi3GameHkr on 2010-11-23
Well I believe somewhere in the thread I linked to, someone said this was a new thing in 10.04.  So 9.10 would be old enough really.  I think the best thing you should do is do some research, find out what your BIOS is called or something, and what version it is, find out what processor you have, and see if there is a way to enable NX support.  The best way to do that is perform searches on Google, and perform some searches on the forums here.  According to the thread I linked to, this is something that quite a few people are experiencing problems with.

---

### Post by narcisgarcia on 2010-12-26
I see the "check-bios-nx" message in a lot of computers, and because of lacking BIOS option to enable NX feature, now I remove the warning message:

```
sudo rm /etc/update-motd.d/20-cpu-checker
```

---

