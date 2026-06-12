---
title: "Just bought a laptop."
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by Roasted on 2007-11-22
My desktop is bloated with thousands of pictures and thousands of songs. I want to put a lot of songs and photos on my laptop. On Windows, I used to do this by applying the file sharing wizard and doing a \\192.168.x.x in the run box and I'd just copy/paste or drag and drop over and they'd be there.

How can I do this? I'm doing this from Desktop (Gutsy - wired) to Laptop (Gutsy - wireless).

---

### Post by Jussi Kukkonen on 2007-11-22
You could put up an NFS share (I imagine that works by just right-clicking on a folder in nautilus and selecting "share"), and connect to it.

Personally I just use ssh because it's so convenient: I have sshd on my server already so it's just a matter of:
```
scp server:/path/to/music/ /target/path/
```
This is not fast though, as everything is encrypted.

---

### Post by megamania on 2007-11-22
> **Roasted said:**
> My desktop is bloated with thousands of pictures and thousands of songs. I want to put a lot of songs and photos on my laptop. On Windows, I used to do this by applying the file sharing wizard and doing a \\192.168.x.x in the run box and I'd just copy/paste or drag and drop over and they'd be there.

How can I do this? I'm doing this from Desktop (Gutsy - wired) to Laptop (Gutsy - wireless).

set up nfs:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

then just mount the directories you want to access.

---

### Post by Roasted on 2007-12-08
Just curious, could I FTP it to the laptop? I haven't tried NFS yet... and I'll consider giving that a shot. I just figured I'd ask about FTP before I do NFS. :)

---

### Post by Roasted on 2007-12-09
Can this work with Windows machines too? My girlfriend's laptop is unusually slow, so she wants to format it and reinstall. She doesn't have a DVD burner or any other major storage media, so I figured I'd just FTP everything to my desktop (which has 700 gig of HDD space) and then wipe her PC.

Can NFS work with windows machines if I know the IP of that windows machine?

---

### Post by Roasted on 2007-12-11
Okay. Now that I'm getting everything set up to run the NFS, I'm a little confused. It's telling me to go into my /etc/exports directory and add a line to control what I want to do.

My desktop is 192.168.1.101
My laptop is 192.168.1.106

What exactly do I need to put in there to enable full read/write permissions from Desktop-To-Laptop? I read it several times and... maybe it's easier than I think and I'm just drawing a blank or maybe I'm just plain stupid. I just want some confirmation on the matter due to the fact I haven't used this before.

---

