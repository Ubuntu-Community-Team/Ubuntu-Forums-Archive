---
title: "Need help with my sftp repository."
date: 2009-06-03
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-06-03
I made a custom repository and put it on a computer in the other room of my house that is a ubuntu server, I shared a folder so I can RW from my desktop comp(this one). When I do apt-get it does not support it, anyone know a fix.

---

### Post by ericeclifford on 2009-06-04
Bumpy

---

### Post by ericeclifford on 2009-06-04
God this is getting under my skin, Apt-get will not work with sftp, but it will work with ftp.

IS There a way to disable the S in SFTP, or to tell apt-get to get stuff from sftp addresses.

---

### Post by wirelessmonkey on 2009-06-04
You could install an FTP server... SFTP is an SSH implementation, completely different from FTP.

---

### Post by cariboo on 2009-06-04
> **ericeclifford said:**
> I made a custom repository and put it on a computer in the other room of my house that is a ubuntu server, I shared a folder so I can RW from my desktop comp(this one). When I do apt-get it does not support it, anyone know a fix.

Apt-get is only useful for handling packages. If that is you intention, that you store packages on your server, then you need apt-cacher. Apt-cacher is in the repositories

---

### Post by ericeclifford on 2009-06-04
> **cariboo907 said:**
> Apt-get is only useful for handling packages. If that is you intention, that you store packages on your server, then you need apt-cacher. Apt-cacher is in the repositories

Well i got apt-cacher, but does that like install from a sftp server, I made my sources.list like sftp://home/repo/the_mirror_of_ubuntu_respository

 I mean I am totally confused :(.

---

### Post by bear912 on 2009-06-04
Are you using a particular tutorial, etc.? What, exactly, are you trying to accomplish? A little more info would be great!

---

### Post by ericeclifford on 2009-06-04
Ok I mirrored the ubuntu 8.04 repositories with apt-mirror, copied the folder repo(the folder which stores the repositories) to a folder in my home/user on my ubuntu 8.04 server edition.

I am running 8.04 desktop edition on this machine. I am trying to find out, how I can do a apt-get install packages from my repositories from my server.

but the sftp(the only way atm i can connect to my server) system is not supported by apt methods. 


So I am either trying to get rid of the sftp and make it a ftp by either disabling the ssh(if I can) from the sftp so it turns into a ftp.
Or any other way i can access it with apt, apt supports ftp http ssh, but not sftp.

---

### Post by decoherence on 2009-06-04
> **ericeclifford said:**
> So I am either trying to get rid of the sftp and make it a ftp by either disabling the ssh(if I can) from the sftp so it turns into a ftp.
Or any other way i can access it with apt, apt supports ftp http ssh, but not sftp.

sftp is not ftp, it is ssh. If you have instructions for getting apt to work over ssh, follow those. I haven't seen that before, though.

Or install an ftp server. It'll run side-by-side with your ssh server. It doesn't really matter which one you use as long as you only log in to it anonymously (otherwise FTP is a security risk.)

There are tutorials on mirroring a repository. [This one]("https://help.ubuntu.com/community/Debmirror") worked for me. This sets up a repository served over http.

---

### Post by ericeclifford on 2009-06-04
> **decoherence said:**
> sftp is not ftp, it is ssh. If you have instructions for getting apt to work over ssh, follow those. I haven't seen that before, though.

Or install an ftp server. It'll run side-by-side with your ssh server. It doesn't really matter which one you use as long as you only log in to it anonymously (otherwise FTP is a security risk.)

There are tutorials on mirroring a repository. [This one]("https://help.ubuntu.com/community/Debmirror") worked for me. This sets up a repository served over http.

got any good ftp server's? :(

---

### Post by decoherence on 2009-06-04
> **ericeclifford said:**
> got any good ftp server's? :(

I avoid ftp as a matter of policy, so I'm not the guy to suggest one. If I had to do this, I'd probably just go with ftpd. Just make sure it's strictly an anonymous ftp server, otherwise you might end up with usernames and passwords being sent over your network in clear text.

I really recommend following that tutorial, though. It is much less work than the length of it would suggest.

Good luck,

---

### Post by ericeclifford on 2009-06-04
> **decoherence said:**
> I avoid ftp as a matter of policy, so I'm not the guy to suggest one. If I had to do this, I'd probably just go with ftpd. Just make sure it's strictly an anonymous ftp server, otherwise you might end up with usernames and passwords being sent over your network in clear text.

I really recommend following that tutorial, though. It is much less work than the length of it would suggest.

Good luck,

I already downloaded 60 gigs from the ubuntu repositories, All I need is a way to put it on my server, so the apt can get it.

---

### Post by decoherence on 2009-06-05
> **ericeclifford said:**
> I already downloaded 60 gigs from the ubuntu repositories, All I need is a way to put it on my server, so the apt can get it.

install apache2 and put your repo in /var/www

If your 60 gigs are in a directory called "Ubuntu" you would have /var/www/Ubuntu

then you would configure apt on the client machine to point to ```
http://*your repository host's name or IP*/Ubuntu
``` obviously replacing the italics with the appropriate value.

---

### Post by ericeclifford on 2009-06-05
> **decoherence said:**
> install apache2 and put your repo in /var/www

If your 60 gigs are in a directory called "Ubuntu" you would have /var/www/Ubuntu

then you would configure apt on the client machine to point to ```
http://*your repository host's name or IP*/Ubuntu
``` obviously replacing the italics with the appropriate value.

Ty man that work perfectly, I am using it right now, will report to you if anything changes, the reason why I am making my own repos, is because the ubuntu one screwed up a cupsys thing update/upgrade and it screws up the live cd environment when you customize a 8.04.2. live cd.

So I am in the chroot environment and going to see how this works, I did a fix for the cupsys(I think) but I wanted my own archive to insure it does not happen again.

Thanks again.

---

