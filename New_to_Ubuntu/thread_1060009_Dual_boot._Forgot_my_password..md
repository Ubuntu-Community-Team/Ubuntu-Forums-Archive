---
title: "Dual boot. Forgot my password."
date: 2009-02-04
forum: New to Ubuntu
---

### Post by Swerve1000 on 2009-02-04
Hello,

I installed 8.10 Desktop after XP and dual boot my machine with GRUB.

Unfortunately I have forgotten my Ubuntu password, so cannot log in.

I am assuming I have no way of recovering it, and so would like to re-install the OS, but would like to not have to wipe the rest of the hard drive and loose my XP installation.

I am concerned about having to perform a manual install as now the 'use the biggest free space' option won't be available during the installation.

I am seeking some advice on how to sort this out.

Thank you!

---

### Post by apjone on 2009-02-04
At the grub boot menu select the "Recovery" option, this will boot you into single user mode as root where you can reset your password

```

passwd username

```

---

### Post by Swerve1000 on 2009-02-04
Oh thats awesome!

Million thanks :)

---

### Post by apjone on 2009-02-04
Not a problem.... done it myself more than once

---

### Post by Schok on 2009-02-04
Does this mean that it is easy for anyone to reset my password and log in to my computer?

---

### Post by apjone on 2009-02-05
They would have to be phyically infront of your machine to boot into single user mode to do that. But if you really are concerned then you can open a terminal and 

```

sudo -i

```
Put your password in. BECAREFUL YOU ARE NOW ROOT!!!!!

```

passwd

```

This allow you to set the root password. From this point on when you boot to single usermode you will reuqire this password. There are ways to reset this password, but it is harder to reset.

---

### Post by Schok on 2009-02-05
oh i think i did that but thru my normal profile. thanks for the information though.

---

### Post by Stressed Newbie on 2009-02-18
I'm having a problem too and followed the instructions, but when I go to recovery it's asking for my root password. I installled Ubuntu 8.10 on a 4gig USB Kingston Drive using PenDriveLinux.I haven' had any time lately to mess with Ubuntu, but I forgot my password.

I tried another way by following the steps:
1. Turn off your computer.
2. Tap it 3 times
3. Say your favorite magic word.
---- If that doesn't fix your problem, do the steps below...  
4. Turn your computer on.
5. Press ESC at the grub prompt.
6. Press e for edit.
7. Highlight the line that begins kernel ........., press e
8. Go to the very end of the line, add rw init=/bin/bash
9. press enter, then press b to boot your system.
10. Your system will boot up to a passwordless root shell.
CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!
11. Type in passwd <username>. Set your password.
12. Type in reboot.
NOTE: steps 1-3 may help at this point.
13. Bow down to me....

It's still doesn't work

the prompt I get is:
root@(none)

I typed at that prompt "passwd Runner72" and nothing happens.

Help?

---

