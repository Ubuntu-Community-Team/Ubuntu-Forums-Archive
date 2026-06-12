---
title: "Best way to sync music/photo/video collection to local file server?"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by XtremeGamer99 on 2008-09-24
I have an old Compaq box running as a file server in my local network. The network, wired, runs at 100Mbps, and yet only gets about 2MBps typically (note the difference between Mb and MB). This is inefficient (for me, anyway) for transferring over large about of data such as music and videos. At the moment, I have an sshfs mount, and I just copy and paste my files to the server. Very slow. So I have three questions:

1) Is there a better way to do this? Like, somehow compress (but not lose) the data so that more data can be passed per second? I read somewhere that rsync can do this, but is the a guide anywhere to mount a remote filesystem automatically with rsync? I'm currently using this guide for the sshfs automount: [http://ubuntuforums.org/showthread.php?t=430312](http://ubuntuforums.org/showthread.php?t=430312). UI'm hoping that the copy & paste functionality will still be available, but faster, if mounted with rsync. Any ideas?

1.2) I sometimes mount my file server on my laptop from a remote location away from home -- such as college. My internet at home isn't that great, I think I get 128Kbps max upstream. So trying to get files from home can be tedious. Using a compression program like above, I think it'll be a lot easier to get files (though I know it'll never be very fast, but a little faster at least). Anyone have any input on this and if it'll work like I think?

2) I need a program that automatically syncs my music player (always located at /media/IAUDIO) with the music directory of the file server (always mounted/linked through somewhere in my home directory). Is there any kind of GUI program to do that? Maybe Unison? I dunno...

Thanks!

---

### Post by XtremeGamer99 on 2008-09-25
Any advise?

---

### Post by XtremeGamer99 on 2008-10-04
Bump?

---

