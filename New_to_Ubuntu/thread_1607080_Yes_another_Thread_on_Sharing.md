---
title: "Yes another Thread on Sharing"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by dashpilot79 on 2010-10-27
I know there has been a bunch of Threads about Sharing, but I can't seem to find the answer, maybe because you can't do it?

Anyway I know I can do this in Windows (which I'm trying to get rid of) So I would hope that there would be a way to do it on Linux.  I'm running Ubuntu 10.10.

I have my Windows Share (a USR NAS Device) connected to the network and I have a bookmark to it, so I can easily see all the Shares on it.  On my windows machine I can just click on it and tell it to map it to a drive  it will ask me for my password and its there.  And actually most of the time I don't even have to map it since most programs will allow me to Browse the network during a saving or opening dialogue.

To my understanding the only way I can this in Ubuntu is

1. Do a Command Line Mount - Not too bad for myself but trying to get my wife to switch from Windows with to having to type something in the command ain't going to happen.

2.  Do a Permanent Mount using FTAB not sure I won't to go that route mainly because there are so many shares and its on a laptop which isn't always connected to the network with the shares.

3.  I can go to the bookmark and it will automount the item, but then I gotta go to my home folder and un hide the files and find the .gvf or what ever the directory is and browse that way.


I did manage to write a little script that ask for user name and password and mounts them to a pre assigned folder, but still not nearly as easy as Windows does it.

I would think for any Flavor of Linux to really take off it must be able to do items like this as home networks are starting to really show up but the skills necessary to use them by all family members aren't there yet.  Besides I don't want to have to go through the trouble of doing it all the time if there was a super easy way.

Thank You if you have any thoughts.
Casey

---

### Post by HermanAB on 2010-10-27
It is even easier in Linux.

Run your file browser (Nautilus).  Click the File menu and look for Connect to Server.  Enter the address and select the protocol (SMB).

If you use Dolphin or Konqueror, simply type smb://ip.add.re.ss in the address bar.
(that also works with scp://, [ftp://,](ftp://,) ldap:// and many others.)

---

