---
title: "Reinstalling Ubuntu"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by Wootchismo on 2010-03-04
First, I want to iterate that my understanding of the benefits of partitioning your drive(s) during installation is so that you can keep your system files separate from your personal files so that, should the worst happen, you can safely re-install Ubuntu in the / directory while your /home directory remains untouched.

That was my understanding, but I've since had too many frustrations with the Alpha 2.0 of Ubuntu 10.04 on my laptop, so I used a LiveUSB key to put 9.10 back on my drive.  I cannot figure out how, during the installation process, I can retain my home directory and have it report correctly under the new / directory (especially if I had previously selected that my password both logs me in and decrypts my home folder).  Does anyone have specific instructions for how to reinstall Ubuntu to a / partition without in any way affect previously-created partitions that you still want to be recognized as falling under the new / partition?

Thanks in advance, anyone.

---

### Post by tinkerist on 2010-03-04
i'm still a young'un when it comes to linuxing but this looks pretty sound and helpful.  if that works let me know because i need to reinstall with the 64 bit version (installed 32 bit on an AMD64  ](*,)) and i don't want to lose users or upgrades.

[http://linuxologist.com/linuxhowto/howto-fresh-ubuntu-install-without-losing-your-current-settings/](http://linuxologist.com/linuxhowto/howto-fresh-ubuntu-install-without-losing-your-current-settings/)

---

### Post by undecim on 2010-03-04
To reinstall with /home intact, you will need to set up your partitions manually like you did when you installed the first time with a separate home. The only difference this time is that you have to make sure the option to format your /home/ directory is NOT CHECKED.

As for the encrypted home directory, here is what I did when I reinstalled (I also had irrecoverable problems with 10.04 alpha):

I'm not 100% what would happen if you choose the decryption option with an encryption already in place. Knowing how Ubuntu's encryption system functions, I think it would "just work", but I wasn't going to risk it overwriting my current key. 

When installing, choose the option "require my password to log in", (NOT "and decrypt my home folder"), and make sure that you set your password to the exact same as your current installation otherwise you will be decrypting with the wrong key

When you log back in, it will look like your home directory is new, but install the "ecryptfs-utils" package and reboot. The ecryptfs modules will configure your system look for and unlock encrypted files when you log in, and your home directory should be back like it was.

---

### Post by Wootchismo on 2010-03-04
Thanks, guys.

tinkerist:  I looked at the link and it seems to be more specifically for conserving your packages and application settings moreso than your personal documents residing within your home folder.

undecim: That is what I thought I had to do too.  I previously had three partitions: a 16GB root partition, a 2 GB swap space, and the remainder for my home directory.  During the re-installation I select the 16GB space and told it to format and use / as its mount point.  I left the other partitions untouched.  Now when I boot I have a new home folder and my old /home partition now appears as "102 GB Filesystem" which can be mounted as a separate drive.  How can I reinstall Ubuntu and retain the home folder seamlessly with the new install?

---

### Post by kouter on 2010-03-04
just edit your /etc/fstab to mount it to /home?

---

### Post by Wootchismo on 2010-03-04
I'm not at that level of expertise.  I mean I can bring the file up in gedit and see the necessary columns and the UUIDs, but I wouldn't know where to progress from there.  Are there more explicit directions on how to accomplish that?

---

