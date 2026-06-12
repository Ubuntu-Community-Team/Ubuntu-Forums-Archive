---
title: "Grub2 chainloading"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by rex4u on 2009-12-12
Hello everyone,

Kindly guide me on this issue...

I have 4 linux distros on 4 different partitions. Their bootloaders are installed on their partitions and Ubuntu's grub2 is in MBR. All these distros have Grub2.
Now when I boot I see all the kernel entries of all the distros listed up giving a very clustered and complicated look in Grub2 menu. Now my question is

How can I make it default for Grub2 to always give chainloading entries in menu if it is there ? Just like it does for Windows.

Thanks to everyone.....:popcorn:

---

### Post by s3MA00RRNY on 2009-12-12
You really didn't need to install grub2 on every distro, just the primary one.

Anyway... in order to fix this "problem", you need to modify the GRUB2 scripts. I'm assuming that you don't want the recovery options, so you would need to comment those lines out. Lines 116-119 in /etc/grub.d/10_linux. If you want chainloading, look at lines 96-120 of /etc/grub.d/30_os-prober. I can't make heads or tails of it, but I see Windows and chain in that section.

---

### Post by rex4u on 2009-12-12
Thanks pcdude...
I already have gone through os_prober completely and have some idea how it works but nothing exactly actually. I know changes have to be made in os_prober only but what and where...

Anyone...

---

### Post by oldfred on 2009-12-13
Take a look at Herman's site. He has info on grub partitions and some on grub2 partitions.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install)

In the grub2 partition you can turn off all the auto and make it like grub legacy with just chainboot entries in 40_custom or directly int grub.cfg (even though you are not supposed to edit it):

# Chainload another bootloader
menuentry "Chainload partition 3" {
set root=(hd0,3)
chainloader +1
}

---

### Post by markyb73 on 2009-12-13
Hello,

I think i have a similar setup to you. I run Karmic on my MBR and chainload to other grub or Windows bootloaders on other partitions.

From info i found from others guides and webpages.

The first thing i did was to make /etc/grub.d/30_os_prober non executable so when i ran update-grub2 it wouldn't find all the other distro's kernels because it couldn't execute that file anymore.

sudo chmod -x /etc/grub.d/30_os_prober
Then ran sudo update-grub2 and rebooted to see that all grub2 could see was my main Ubuntu kernels.

If you want to change back simply run sudo chmod +x /etc/grub.d/30_os_prober to make the file executable again and run sudo update-grub2 to get back to where you were.

Then i edited /etc/grub.d/40_custom to add the chainloaders for my other distro's. Don't modify whats in there just add new sections for your other partitions, i.e.

#! /bin/sh -e
echo "Adding /dev/sdb3" >&2
cat << EOF
menuentry "/dev/sdb3 Fedora" {
set root=(hd1,3)
chainloader +1
}
EOF

Then ran sudo update-grub2 again and it was all setup.

Thats how i like to manage it, i little more work that legacy grub but it works for me :D

Hope this helps.

Mark.

---

