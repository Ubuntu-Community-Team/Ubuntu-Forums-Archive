---
title: "Jaunty errors have unknown consequences"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by nnjond on 2009-04-23
Hi,

I suffered a sequence of failures installing J:

"Could not install ca-certificates

And

"Could not install the upgrades
- This Upgrade is now aborted"

Followed by:

"The upgraded was completed but with errors"


However I have restarted and the new kernal shows up in place at Grub and after running an automatic routine check I got new splash screen and landed at my desktop. Is their anything wrong with my Health?

Thanks

---

### Post by Peter09 on 2009-04-23
Try System->Admin->Update Manager

this will attempt to get your system upto date and download any packages that failed initially.

---

### Post by nnjond on 2009-04-23
Thanks for your interest. It didn't seem to download anything?

---

### Post by Peter09 on 2009-04-23
If you are seeing no problems, then it most probably did a valid update. It may be that you now have some invalid third party repositories in your sources list.

---

### Post by nnjond on 2009-04-23
Thanks. I'll leave for now

---

### Post by SilentSno on 2009-04-24
My Boss's computer did the same thing, it appears to be working just fine.

Grub still shows the older version and kernel.

Running update-manager says it wants to do a partial update, but silently fails. Rerunning does the same thing over and over.

---

### Post by Peter09 on 2009-04-24
Try doing in a terminal
```
sudo apt-get update
```

```
sudo apt-get upgrade
```

see if you get any error messages.

---

