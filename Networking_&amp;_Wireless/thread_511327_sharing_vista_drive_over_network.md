---
title: "sharing vista drive over network"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by braves4life@cox.net on 2007-07-27
I am having a problem connecting to a windows Vista shared folder using Ubuntu 7.04. 

I can connect and stream files using both a macbook and using the media center extender of the Xbox 360.

On the ubuntu machine I can connect to the vista machine using the local IP address and the Places->connect to server... menu. I am able to see the folders in the share for the most part, but when I'm navigating through the folders I usually get the following error(for example):

"Nautilus cannot display "smb://192.168.1.136/media/Podcasts". Please select another viewer and try again"

When I am able to navigate to a file and then double-click to open and stream I get this message from Totem Movie player:

"An error occurred"
"Could not open location; You may not have permission to open the file."

If instead I try to copy the file to the Ubuntu computer sometimes it will start and then quit but I can actually play small part that copied over.

I have followed every guide I could find about setting up Samba and smbfs and do not care about accessing the Ubuntu drive from vista because it will be used for streaming media only. Any ideas about what is wrong?

I have set both user names and passwords on both machines to be identical and have tried it without the windows firewall. I don't know what my next step should be.

Thanks for any help!

---

### Post by DugieHowsa on 2007-07-27
Try using cifs instead of smbfs.

I had been having trouble mounting a Windows Share. I tried to mount using smbfs. I tried to mount using cifs. In the end, some one showed me this link:

[https://bugzilla.samba.org/show_bug.cgi?id=1920](https://bugzilla.samba.org/show_bug.cgi?id=1920)

Summary: "smbfs is unmaintained and known to be severely broken." That was posted back in 2004, so needless to say probably not much has happened with smbfs in the last 3 years.

So here is the man page for mount.cifs that lists all the options:

[http://www.die.net/doc/linux/man/man8/mount.cifs.8.html](http://www.die.net/doc/linux/man/man8/mount.cifs.8.html)

Many people here have also listed many good posts, giving several good examples, on how to properly utilize cifs:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

This post solved the particular problem I was having:

[http://ubuntuforums.org/showthread.php?t=483184](http://ubuntuforums.org/showthread.php?t=483184)

In summary: USE CIFS. DO NOT USE SMBFS.

---

### Post by braves4life@cox.net on 2007-07-28
Awsome, that worked perfectly!  Almost... so I used the mount permantly guide and now when ubuntu boots up it tries to mount the networked drives before the wireless has connected causing it to take a long time.

Also when booting into mythtv the drives aren't mounting and the wireless hasn't connected so I have to log in with my username, enter my keychain password so the wireless connects and then go back to mythtv.

Hibernating takes care of the problem but I'd like to be able to shut down and such.  Is there anyway to have the wireless connect early during startup, it seems like that would solve everything.

But thanks for that info atleast I can use the drive now!

---

