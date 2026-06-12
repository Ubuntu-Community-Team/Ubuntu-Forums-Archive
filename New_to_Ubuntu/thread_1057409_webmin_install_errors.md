---
title: "webmin install errors"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by parts-man73 on 2009-02-01
I just installed Ubuntu Server 8.10 on an old computer to act as a home file/print server.

I tried to install Webmin via the following method -

to /etc/apt/sources.list I added 
```
deb http://download.webmin.com/download/repository sarge contrib

```
then
```
cd /root
wget http://www.webmin.com/jcameron-key.asc
apt-key add jcameron-key.asc 
```

then I...
```
apt-get update
apt-get install webmin
```

when I run apt-get update - I get the following errors

W: GPG error: http:download.webmin.com/download/repository sarge release: the following signatures were invalid: NODATA 1 NODATA 2"

W: Failed to fetch [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge/contrib/binary-i386/packages.B22 subprocess Bzip2 returned on error code (2)

Then apt-get install webmin fails

any ideas on what i need to do to get Webmin loaded? 

Thank you
Brian

---

### Post by albinootje on 2009-02-01
> **parts-man73 said:**
>  any ideas on what i need to do to get Webmin loaded? 


[http://webmin.com/](http://webmin.com/) --> click on "Debian Package". That should do.
(And remove that old Debian Sarge repository from your sources.list).

---

### Post by parts-man73 on 2009-02-01
I really can't "click" on anything, I'm trying to do this from a command line. I am using a fresh install of Ubuntu Server 8.10. there is no GUI, Firefox, anything. 

I tried to "Wget" it, but errors trying that also

---

### Post by cariboo on 2009-02-01
I'd just download it to your desktop computer, then sftp it over to the server.

If you really want to do this from the command line, install elinks, it is a text based web browser that is available in the repositories. You will need it to setup cups if you intend to setup a print server.

Jim

---

### Post by parts-man73 on 2009-02-01
ok, I WGOT it...lol 

it's installed now. 

Thank you

---

### Post by nyktovus on 2009-03-13
When i try to install webmin on a BRAND new ubuntu 8.10 server install.. heres what happens


$ sudo dpkg -i webmin_1.460_all.deb

(Reading database ... 37811 files and directories currently installed.)
Preparing to replace webmin 1.460 (using webmin_1.460_all.deb) ...
Unpacking replacement webmin ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
 webmin depends on libauthen-pam-perl; however:
  Package libauthen-pam-perl is not installed.
 webmin depends on libio-pty-perl; however:
  Package libio-pty-perl is not installed.
 webmin depends on libmd5-perl; however:
  Package libmd5-perl is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 webmin



..help?

---

### Post by albinootje on 2009-03-13
> **nyktovus said:**
> 
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
After that simply run :
```

sudo apt-get -f install

```
and all should be fine.

---

### Post by nyktovus on 2009-03-13
your a champ ;) thanx!

---

### Post by nokynoky on 2009-04-25
> **albinootje said:**
> After that simply run :
```

sudo apt-get -f install

```and all should be fine.



help !
when i try

~$ sudo apt-get -f install <== this one i got following error

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-image-2.6.30-020630rc2-generic linux-headers-2.6.30-020630rc2-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libauthen-pam-perl libio-pty-perl libmd5-perl libnet-ssleay-perl
The following packages will be REMOVED:
  linux-headers-2.6.30-020630rc2-generic linux-image-2.6.30-020630rc2-generic
The following NEW packages will be installed:
  libauthen-pam-perl libio-pty-perl libmd5-perl libnet-ssleay-perl
0 upgraded, 4 newly installed, 2 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 41.7kB/266kB of archives.
After unpacking 84.8MB disk space will be freed.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libnet-ssleay-perl libio-pty-perl
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libio-pty-perl 1:1.05-1
  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libi/libio-pty-perl/libio-pty-perl_1.05-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libi/libio-pty-perl/libio-pty-perl_1.05-1_i386.deb)  404 Not Found [IP: 91.189.88.140 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


im using ubuntu 6.XX please help i need it badly

---

### Post by albinootje on 2009-04-25
> **nokynoky said:**
> 
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libi/libio-pty-perl/libio-pty-perl_1.05-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libi/libio-pty-perl/libio-pty-perl_1.05-1_i386.deb)  404 Not Found [IP: 91.189.88.140 80]


You're using Ubuntu Edgy which is officially no longer supported.
Change you repositories in /etc/apt/sources.list to use these : [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)
Or, better, make backups and reinstall Ubuntu Hardy, the LTS.

---

