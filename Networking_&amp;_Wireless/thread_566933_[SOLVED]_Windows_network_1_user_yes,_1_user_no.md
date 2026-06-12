---
title: "[SOLVED] Windows network: 1 user yes, 1 user no"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by maphew on 2007-10-04
Can someone please explain to me what is happening here? (and how to solve it too I hope!)

1 ubuntu computer (hostname ubuntu-desktop), 7.04 AMD64bit 
1 windows computer (hostname win2k), Windows 2000
domain/workgroup (ourplace)

On the ubuntu computer,
UserA can open up nautilus, type "network:///" in the location bar and get a list of network resources like this:
[i]
   UBUNTU-DESKTOP
   WIN2K
   Windows Network
[/i]
UserB does the same, and only sees:
[i]
   Windows Network
[/i]
UserA results for typing "smb:///":
[i]
   ourplace
[/i]
"smb://ourplace":
[i]
   UBUNTU-DESKTOP
   WIN2K
[/i]
UserB gets an empty screen for "smb:///" and an error for "smb://ourplace":
[i]
   The folder contents could not be displayed

   Sorry couldn't display all the contents of
   "Windows Network: ourplace".
[/i]

Both users are administrators on both computers. Usernames & passwords are the same on both computers for each user. Both users can connect to and use shares on the ubuntu computer from the windows computer.

Any ideas?
thanks

---

### Post by conjur3r on 2007-10-04
Can you see what groups both of the users are in on the ubuntu box?

# groups USERNAME

---

### Post by maphew on 2007-10-04
[i]
userA : userA adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin parents
userB : userB adm dialout fax cdrom floppy tape audio dip video plugdev scanner admin fuse parents
[/i]

userB was able to see the win2k computer a month or so ago and there has been no group management since then (to the best of my recollection). Nonetheless adding userB to 'netdev' cured the problem, so thank you!

---

