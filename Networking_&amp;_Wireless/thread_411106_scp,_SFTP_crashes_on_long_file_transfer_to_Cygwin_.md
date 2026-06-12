---
title: "scp, SFTP crashes on long file transfer to Cygwin SSH server"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by poscogrubb on 2007-04-16
I am using SSH to transfer files between my Thinkpad T22 running Xubuntu 6.10 and a Windows XP PC running Windows XP (obviously) with Cygwin.

Specifically, I'm using sshfs to mount the Windows XP partition to /mnt/somewhere in Xubuntu, but the same problem occurs when I just use the scp command.

I can successfully scp files in either direction from the Linux command line. However, when I try to do a large copy (one particular file was about 9 MB) from Linux to Cygwin, Linux will crash part-way through the transfer. Sometimes it crashes within one second, one time it crashed after copying about 7 MB of data. The crash is so bad that the only thing I can do is turn off the laptop with the power button (mouse cursor is frozen, and no key combinations work, including Ctrl-Alt-Fx to get the other TTYs). There are no relevant messages in /var/log/messages.

I tried the following, and they all work:
a) from Liunx laptop: scp small-text-file user@windowsxpbox:.
b) scp user@windowsxpbox:small-text-file .
c) scp large-FLAC-file [email]user@outside-of-my-home-network.university.edu[/email]:.
d) from outside my home network: scp large-FLAC-file user@windowsxpbox:.

Connecting via SSH from Linux to Windows also works.

At first I suspected Cygwin's OpenSSH (hey, Cygwin ain't perfect), but I SFTP to my Windows machine regularly from school (Linux), and transfer files without any problem. This also indicates that file/directory permissions are not the problem. Just in case, my Cygwin openssh version is 4.6p1-1.

The connection between the computers is through a wireless router, and there is no problem with signal strength (otherwise, ssh should have reported a connection problem). SSH authentication is also working; I've shared the public key, so there's no chance of mistyping password,etc.

Please help me figure this out. Thanks...

---

### Post by poscogrubb on 2007-04-16
Adding one more note: the Windows PC does not crash when this happens. I can see nothing wrong on the Windows PC except that the files I try to copy aren't copied fully. :(

---

