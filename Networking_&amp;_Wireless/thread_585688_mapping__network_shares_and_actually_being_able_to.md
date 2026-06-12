---
title: "mapping  network shares and actually being able to use them..."
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by sdellysse on 2007-10-21
there are few things left in linux that make me want to boot up osx for a little while. one of these things is how ubuntu handles mapped drives. is there any standard way of doing this? I have two shares from my university that I use extensively. in some programs' "Open File..." dialog boxes, they show up in the side bar. other programs, still using the standard gnome dialogs, do not have them. i'm surprised considering how polised the rest of the distro is.

unique examples:
gedit: can open files off shares, but only when opened from in the program, not double clicked.
firefox: open file dialog does not have any shares listed
eclipse: open file dialog does no have any shares listed
same for abiword, gimp, etc

is there anyway I can fix this? i would just like a /networkshares folder with symlinks to the mounted shares in the very least

thanks,
shawn

---

### Post by shad0w_walker on 2007-10-21
It can be done as a mount. Depending on what kind of mounts they are it varies in ease. I assume you are using samba as its a university share. If you know the options required to manually mount samba you can add a line to your fstab file so it will mount as a local folder and appear in all programs.

---

