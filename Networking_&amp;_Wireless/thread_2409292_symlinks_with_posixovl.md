---
title: "symlinks with posixovl"
date: 2018-12-31
forum: Networking &amp; Wireless
---

### Post by jduns on 2018-12-31
Happy new year! I'm trying to have symlinks on remote drive (mega). 
With megacmd I have a mega webdav on my pc and I would like to have some symlinks on my mega cloud. 
I tried with davfs2, but it seems that it *does not support the links* and I have not succeeded. 

It seems to me that the only solution would be the one, to which [this post refers]("https://unix.stackexchange.com/questions/309619/is-there-a-light-weight-file-system-that-implements-symlinks-and-file-permission"), to directly use posixovl to mount a remote drive. 
But if I try ```
mount.posixovl -F webdav://127.0.0.1:4443/[remote-path]/schede/ /media/[user]/webdav-schede
```
it gives me error ```
Could not open("webdav://127.0.0.1:4443/[remote-path]/schede/"): No such file or directory
```.
same result if I use http instead of webdav.
Note that in Krusader I *can* open "webdav://127.0.0.1:4443/[remote-path]/schede/" and work on it.

In your opinion is there a way to mount a remote drive directly with posixovl? Or some other workaround?

---

### Post by jduns on 2018-12-31
There would be this program, [MegaFuse]("https://github.com/matteoserva/MegaFuse"), which I tried today: if it did what it says it would be the solution (it should create symlinks in mega), but [crashes]("https://github.com/matteoserva/MegaFuse/issues/99") all the time ... (not updated recently: 3 years ago).

EDIT
There is an [update of megafuse]("https://github.com/meganz/sdk/tree/develop/examples/linux") but it require a lot of packages (more than 600 mb), some not in ubuntu repo...

EDIT
Tried with rclone mount (release from rclone site, not with the ubuntu package: this one is without support for mega): **nothing to do**, impossible create symlinks via posixovl o via rclone itself.

---

