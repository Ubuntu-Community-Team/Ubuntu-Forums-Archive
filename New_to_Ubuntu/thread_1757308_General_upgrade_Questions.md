---
title: "General upgrade Questions"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by JasonSCarter on 2011-05-13
I'm running Netbook 9.10. If I upgrade to 10.10 through the update manager. will it reformat the HD? will I need to back up my files prior to installing the upgrade? also can I change the distro to the desktop 10.10 version?

Jason

---

### Post by nickgaydos on 2011-05-13
No, it will not reformat anything. But, that being said, you should always backup your files prior to upgrade in case something goes wrong. and I believe in order to change the distro, you have to reformat.

---

### Post by kn0w-b1nary on 2011-05-13
Back up to be safe, though you don't need to.

Also, make note of programs that you like, in case they get removed in the upgrade. Ubuntu Tweak was removed during the upgrade from 10.10 to 11.04.

---

### Post by seawolf167 on 2011-05-13
I strongly recommend backing up just to be sure, I like using [Clonezilla ]("http://www.clonezilla.org")

Additionally, I recommend a fresh clean install over an upgrade to ensure that there are no package version issues and that everything runs smoothly.

If you have a separate /home partition this is a breeze to cleanly reinstall and keep your settings and files. Simply boot off the LiveCD and specify your mount points (i.e. / and /home) when installing. If you don't have a separate /home partition you can [easily make one ]("https://help.ubuntu.com/community/Partitioning/Home/Moving")and then do a fresh install.

---

### Post by JasonSCarter on 2011-05-13
Thanks guys!

---

### Post by Sef on 2011-05-13
If you have any proprietary software installed or PPAs either disable or remove them.

---

### Post by hansolo4949 on 2011-05-13
No, it will not, though if something goes wrong and the installation aborts, you may have a damaged system. Essentially a upgrade is a gigantic package update, with a few configuration changes.

---

