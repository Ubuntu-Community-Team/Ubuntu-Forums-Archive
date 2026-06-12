---
title: "Adobe flash player problem"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by LinkmanSK on 2009-10-25
hi i tried to install Adobe flash player in terminal and it tells me something like

tar: install_flash_player_10_linux: Cannot open: No such file or directory
tar: Child returned status 2

---

### Post by Paqman on 2009-10-25
Is there some reason you're not using the version of Flash in the repositories? Just install the package flashplugin-nonfree (or better yet, the meta-package ubuntu-restricted-extras) and it'll install Flash for you.

---

### Post by lovinglinux on 2009-10-25
Also make sure you don't have other flash plugins installed, otherwise they will conflict with flashplugin-nonfree.

See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by LinkmanSK on 2009-10-25
Ok i try this [http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)

it doesnt help i see

---

