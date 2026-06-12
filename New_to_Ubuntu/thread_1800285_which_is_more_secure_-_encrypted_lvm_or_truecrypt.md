---
title: "which is more secure - encrypted lvm or truecrypt?"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by chedderslam on 2011-07-08
Which would be the better choice?  This will be a virtualbox install of 11.04.

---

### Post by nrundy on 2011-07-08
I don't believe either is more secure than the other. Just be aware that you can't do full disk encryption with TrueCrypt on Linux.

---

### Post by chedderslam on 2011-07-08
Thank you very much.  As full disk encryption is my goal, I now know what to do.  Cheers.

---

### Post by chedderslam on 2011-07-08
The two guides I found seem a little different in their implementaion.  Would anyone mind telling me which would be the preferred method?

[http://www.linuxbsdos.com/2011/05/09/home-directory-and-full-disk-encryption-in-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/09/home-directory-and-full-disk-encryption-in-ubuntu-11-04/)

or

[http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/](http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/)

---

### Post by nrundy on 2011-07-08
Please vote here for this brainstorm idea to put LUKS Encryption in the default installer:  [http://brainstorm.ubuntu.com/idea/24712/](http://brainstorm.ubuntu.com/idea/24712/)

Hopefully we'll see this in Oneiric!

---

### Post by nrundy on 2011-07-08
> **chedderslam said:**
> The two guides I found seem a little different in their implementaion.  Would anyone mind telling me which would be the preferred method?

[http://www.linuxbsdos.com/2011/05/09/home-directory-and-full-disk-encryption-in-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/09/home-directory-and-full-disk-encryption-in-ubuntu-11-04/)

or

[http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/](http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/)

If you want FULL DISK, there is only two ways to do it, to my knowledge. The easiest way is to just use the Alternate CD and use the Guided setup to use entire disk with encrypted LVM. The only reason not to use the Guided setup would be if you want to give /home its own partition.

My advice for now? Just do the Guided setup on the Alternate CD and make life easy. And prey that Oneiric gets the encrypted lvm option in the default installer and then life will be glorious for sure :)

---

