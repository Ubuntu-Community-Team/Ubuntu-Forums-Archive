---
title: "vlc files on remote drive"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by weaver4 on 2007-05-25
I am using vlc as my multimedia player.

If I have the same avi file locally and also on a remote windows machine. In Nautilus  I can right click and select "play on vlc" on the local copy but this option is not shown for the remove copy of the same file.

I saw on LaunchPad that vlc needs to "register" that it can play remote files.  But I don't know how to modify Ubuntu so that is the case.

Is there some workaround for this?  Can I make a directory on Window machine look like a local mounted drive?  Is there some parameter I can change somewhere that will tell Nautilus that it is ok to use vlc to play remote files.

Playing remote files on vlc works fine from the command line, so I am certain it is a network or Nautilus problem.

---

### Post by meng on 2007-05-25
You can mount a samba share, that should fix your problem, although VLC is supposed to be network-aware (more so than other players anyway).
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
As you say, it's a workaround.

---

### Post by weaver4 on 2007-05-25
It is not a problem with vlc, since vlc will play the file on the command line.

It has something to do with the fact that Nautilus will not pass the file name to vlc because it thinks it shouldn't.

---

### Post by weaver4 on 2007-05-26
Ok that worked kind-of.

When I start the movie with:

vlc /media/MyMoviesOnServer/Movie.xagk67.avi

The movies is all broken-up with pauses in it and such.  When I run it with this command line it plays perfectly.

vlc smb://theServer/Movies/Movie.xagk67.avi

Why is that and what can I do to fix it?

---

