---
title: "Mapping domain network drive issue"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by rojmab on 2008-04-23
I'm trying to map my home drive on my work Active Directory domain.
I am able to mount the drive just fine as a cifs share, but for some reason my files aren't behaving as expected... I'm using Putty to SSH to my box, and the file names on my network drive (when I do ls on the directory) show as Black text on a Yellow background. This is not somthing I set in Putty.

In particular I try to run perl scripts that I have saved on my home drive. When I run the script, i get: "ryan@ryan-desktop:~/PERL/Connections$ perl ~/h/PERL/Connections/ConnectionsTest.pl
Setuid/gid script is writable by world."

If I copy the script to my local machine, and run it:
ryan@ryan-desktop:~/PERL/Connections$ perl ConnectionsTest.pl
No #! line at ConnectionsTest.pl line 1."
The File retains the weird Yellow background in the name. If I open up the file in nano or vi, i get a "Converted" message. If i try to open an ordinary .txt file in nano, it comes back as jibberish.

I mount the drive this way (Taken from my /etc/fstab):
//osi/orbitusers$/rtjensen      /home/ryan/h    cifs credentials=/home/ryan/.smbpasswd,uid=ryan 0 0

Is there somthing wrong with how i'm mounting it? should I be doing somthing differently? Thanks in advance. I'm a Huge newb with Linux, but I'm trying to learn. Thanks.

---

