---
title: "Accessing Windows shares for uploading photos to Facebook"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by RotsiserMho on 2010-05-12
Hello,

I'm fairly familiar with Linux and Ubuntu, but I find myself unable to perform what I consider to be a typical operation for a Linux newbie.  I have a bunch of photos shared via Windows file-sharing on another machine on my home network.  It was easy enough to mount the share and there's a shortcut to it on my desktop, but I have no idea how to access it via the Facebook photo uploader.  For those unfamiliar with the uploader, it's a Java applet that allows me to browse my home directoy and the root filesystem for photos.  My first attempt seemed obvious enough: I navigated to the Desktop directory in my user directory but the share is not there!  It's on my desktop, but not in my desktop directory.  This confuses me greatly.  How can I browse to this share from the uploader?

Thanks in advance!

---

### Post by blueridgedog on 2010-05-12
You will need to mount the shared folder as part of your local file system.

It is slightly complex, but not impossible.  Sadly, there is no GUI for such an action (we need one).

Take a look here:

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

and

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

A similar post to yours describes the exact problem:

[http://ubuntuforums.org/showthread.php?t=597671](http://ubuntuforums.org/showthread.php?t=597671)

When you mount it as part of your local file system, you can then "browse" to the files using most common dialog boxes.

Read over the documentation I linked to and if you give it a try I and others can step in if you get stuck.

---

