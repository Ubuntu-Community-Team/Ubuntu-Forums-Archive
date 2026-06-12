---
title: "how to tranfer files in SSH"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by holyct on 2007-11-03
I have school assignment supposed to hand in through SSH to my school server. Obviously lecturer ask us to install SSH file transfer client in Windows, but I am using Ubuntu, so is there any way to do that?

---

### Post by upfwnv03 on 2007-11-03
Try using secure copy (scp).

usage: scp [-1246BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file]
           [-l limit] [-o ssh_option] [-P port] [-S program]
           [[user@]host1:]file1 [...] [[user@]host2:]file2

---

### Post by seachnasaigh on 2007-11-03
You can also try using sftp if your servers support it. 
Generally speaking, you have to kind of keep your head in where you are when you're doing this in a terminal window, but it works something like this:
Open terminal on your Ubuntu machine.
ssh to the server you're trying to access; password etc apply of course.
sftp BACK to your home machine.
Passwords and user apply of course.
do a get <filename> on the file you're trying to move across. Caveat: make sure that you're in the right directory on the target machine (your school server) before you start the transfer.
Second caveat: the GET command may require you to put in the whole file path (for example: get /home/yourname/homeworkdir/myhomework.txt
The file should copy across and an ls should show you the file in your target dir.

If this doesn't work for some reason, you can try to do it the other way round ... open an ftp session on your home machine and do a PUT to the target machine. The GET thing usually works better, however.

I use this all the time for moving files around my own network, and across vpn connections to a variety of client servers. Firewalls can get in the way however so YMMV; given the situation your prof wants, I don't suspect that's to be the case. Good luck!

---

