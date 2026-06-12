---
title: "Mount all shares in the network on Ubuntu"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by darkice83 on 2008-07-08
Is it possible to have my Ubuntu box automatically mount all the shares in my network? (and share that directory as well?)

Let's say I have three PCs networked together, My Ubuntu box(U) and two widows machines (A and B)
Say:
 A has a share named "Code"
 B has two shares, named "School" and "Photos"

is it possible to have a script check smbtree to see the local network shares and attempt to mount them (as guest), if the mount as guest fails, then just don't mount it.

In the end I'd like to have on my Ubuntu box:
/share/A/Code
/share/B/School
/share/B/Photos

note that i would also like to share this folder to the rest of the network, recursion rules apply so if i were to share my /share folder it would now contain

/share/A/Code
/share/B/School
/share/B/Photos
/share/U/share
(which would cause /share/U/share/U/share/ etc.... I think )

and yes I realize this would probably be a bandwidth hog on my local network, but it would be cool to try!

Thanks

---

