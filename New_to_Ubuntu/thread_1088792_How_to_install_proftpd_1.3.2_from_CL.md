---
title: "How to install proftpd 1.3.2 from CL"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by cfree220 on 2009-03-06
Hi all,
I have a server running 8.10 set up in my dorm as a personal file server. It's purpose is to provide local and remote access to documents and media files, such as music, pictures, and video. To do this, I installed an FTP server (proftpd). It was my intent to connect to this server using SSL/TLS encryption, however  proftpd 1.3.1 has a problem in this regard which makes it incompatible with my FTP client of choice [Filezilla]. As a workaround, I simply took advantage of the SSH server that also runs on the system. While this is not ideal (providing encryption on only the command channel), it is better than having my pwds sent in plain text.
The current stable release of proftpd is 1.3.2, in which the development team has resolved the issues with the TLS module. I first tried getting and installing updates for the system. That didn't work, so I removed the existing proftpd install and then using 
```
sudo apt-get install proftpd
```
I then checked the version with proftpd -v. Despite 1.3.2 being the current stable release (according to the project website), it had fetched and installed 1.3.1.

What I need to know is: How do I download and install 1.3.2 on a headless server when apt-get install yields 1.3.1?

---

### Post by taurus on 2009-03-06
1.  You can wait for the new version to get into the repos.

2.  You can try to download the .deb and install it on your server.

3.  Or you can download the source and build it for your machine.

---

### Post by cfree220 on 2009-03-06
Thanks for the quick reply!

I have installed it from source in the past, but it wasn't quite the same as a package installation (e.g. location of config files and stuff).

How would I go about downloading and installing the .deb? I understand how to install things from the repositories, but I don't understand how to extract the archive files and where to/how to install them.

---

### Post by OffAxis on 2009-03-06
It doesn't look like the latest release has been crafted into a .deb yet, not even by the proftpd team itself, so you're stuck with compiling it yourself or waiting for the official sites to be updated.



you can use checkinstall to generate (and install) your own .deb file from that source code.

```
sudo apt-get install checkinstall
```


you can also install a .deb file with dpkg 

```
dpkg -i filename.deb
```

---

### Post by cfree220 on 2009-03-06
Thank you, OffAxis.
Just out of curiosity, would there be any differences between a checkinstall .deb and one that would be made by the proftpd team?

---

### Post by taurus on 2009-03-06
I think you misunderstood about checkinstall.  You still need to compile and build it from source first (./configure && make) but instead of running **sudo make install** to install it, you would run **sudo checkinstall**.  Then, if you ever want to remove it later from your machine, you can use dpkg instead of uninstall.  You still have to download the source and compile it first.

And you can specify which directories to install the binary, library, and config files when you run ./configure.

```
./configure --help
```
For info regarding other options.

---

