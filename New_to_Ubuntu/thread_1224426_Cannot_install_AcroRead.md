---
title: "Cannot install AcroRead"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by marianlibrarian on 2009-07-27
The reader that comes with Kubuntu does not work very well. I am unable to find a way to install Acroread in Kubuntu Hardy Heron.

Here is the text from my termanal window:
> librarian@PAC02:/home$ sudo apt-get install acroread
[sudo] password for librarian:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate
We need this. Many forms that our patrons have to fill out for jobs and / or taxes are in PDF.

---

### Post by TeoBigusGeekus on 2009-07-27
[http://get.adobe.com/reader/otherversions/]("http://get.adobe.com/reader/otherversions/")

---

### Post by chrisinspace on 2009-07-27
I'm not sure about Hardy, but in Jaunty you have to have the following archive enabled:

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)

You can do this by going to System -> Administration -> Software sources

It's under the Third-Party Software tab.

---

### Post by marianlibrarian on 2009-07-27
Thank you.

I followed instructions. Here is what my termainal window says:

> librarian@PAC02:~/AdobeReader$ sudo rpm -i AdobeReader_enu-8.1.3-1.i486.rpm
sudo: rpm: command not found
librarian@PAC02:~/AdobeReader$ rpm -i AdobeReader_enu-8.1.3-1.i486.rpm
The program 'rpm' is currently not installed.  You can install it by typing:
sudo apt-get install rpm
bash: rpm: command not found
librarian@PAC02:~/AdobeReader$ sudo apt-get install rpm
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-23-generic linux-headers-2.6.24-23
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libbeecrypt6 librpm4.4
Suggested packages:
  alien
The following NEW packages will be installed:
  libbeecrypt6 librpm4.4 rpm
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
Need to get 1687kB of archives.
After this operation, 6304kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libbeecrypt6 4.1.2-6build1 [108kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main librpm4.4 4.4.2.1-1ubuntu6 [953kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main rpm 4.4.2.1-1ubuntu6 [625kB]
Fetched 1687kB in 4s (341kB/s)
Selecting previously deselected package libbeecrypt6.
(Reading database ... 108716 files and directories currently installed.)
Unpacking libbeecrypt6 (from .../libbeecrypt6_4.1.2-6build1_i386.deb) ...
Selecting previously deselected package librpm4.4.
Unpacking librpm4.4 (from .../librpm4.4_4.4.2.1-1ubuntu6_i386.deb) ...
Selecting previously deselected package rpm.
Unpacking rpm (from .../rpm_4.4.2.1-1ubuntu6_i386.deb) ...
Setting up libbeecrypt6 (4.1.2-6build1) ...

Setting up librpm4.4 (4.4.2.1-1ubuntu6) ...

Setting up rpm (4.4.2.1-1ubuntu6) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
librarian@PAC02:~/AdobeReader$ rpm -i AdobeReader_enu-8.1.3-1.i486.rpm
error: open of AdobeReader_enu-8.1.3-1.i486.rpm failed: No such file or directory
librarian@PAC02:~/AdobeReader$    As you can see i was able to install this rpm successfully. I am lost. Still unable to install adobereader

Edit:
rpm was not the correct command to use

this is:
 tar -zxvf AdobeReader_enu-8.1.3-1.i486.tar.gz

> librarian@PAC02:~/AdobeReader$ tar -zxvf AdobeReader_enu-8.1.3-1.i486.tar.gz
tar: AdobeReader_enu-8.1.3-1.i486.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
librarian@PAC02:~/AdobeReader$ ls
COMMON.TAR  ILINXR.TAR  INSTALL  ReadMe.htm
librarian@PAC02:~/AdobeReader$   


Pretty lost now.

---

### Post by sandeepraj on 2009-07-27
i dont know about kubuntu but in ubuntu u can install through synaptic package manager
ubuntu processes:
system-->administration-->synaptic package manager
now search acroread and install

---

### Post by Clorow on 2009-07-27
You installed an rpm? You should uninstall it and use the deb package instead. As chrisinspace said:

Go to System > Administration > Software Sources. Under the "Third Party" tab, make sure the archive.canonical.com repository is enabled. Then click [here.]("apt:acroread")

---

### Post by marianlibrarian on 2009-07-27
> You installed an rpm? You should uninstall it and use the deb package instead. As chrisinspace said:

Go to System > Administration > Software Sources. Under the "Third Party" tab, make sure the archive.canonical.com repository is enabled. Then click [here.]("apt:acroread")Yes. I realized my mistake and used the tar command instead but still have error. Perhaps tar command won't work after mistake with rpm installation?

---

### Post by marianlibrarian on 2009-07-27
Looked in AdobeReader folder to make sure TAR files were there:
Listed:
COMMON.TAR
ILINXR.TAR
INSTALL
ReadMe.htm

Perhaps Acroreader is not compatible with Kubuntu KDE as it is with Ubuntu Gnome.

---

### Post by thunk77 on 2009-07-27
Go to System > Administration > Software Sources. Under the "Third Party" tab, make sure the archive.canonical.com repository is enabled.

Then open up a Terminal and type:

```
sudo apt-get install acroread
```

..let's see..

---

### Post by marianlibrarian on 2009-07-27
> Go to System > Administration > Software Sources. Under the "Third Party" tab, make sure the archive.canonical.com repository is enabled.

There is a System menu, but there is no Administration selection.

---

### Post by marianlibrarian on 2009-07-27
I clicked on the first item in the System Menu: Adept Manager - Manage Packages

Then clicked on the first menu item at the top Adept.

Then clicked on Manage Suppositories

Then the window changed and there was a "Third Party Tab"
I clicked and placed an X in all the little boxes.

Now I am going to try and install acroread again.

Edit:
After checking all the third party boxes:

> librarian@PAC02:~/AdobeReader$ sudo apt-get install acroread
[sudo] password for librarian:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate
librarian@PAC02:~/AdobeReader$                        

I go round in circles.

---

### Post by philinux on 2009-07-27
Click the medibuntu link below.

Follow instructions then you'll be able to get acroread.

---

### Post by marianlibrarian on 2009-07-27
Went to Medibuntu

put this in my terminal window
> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.listgot the following:
> --12:50:12--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org]("http://www.medibuntu.org")... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80]("http://www.medibuntu.org%7C87.98.242.110%7C:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: 276 [text/plain]

100%[===========================================================>] 276           --.--K/s

12:50:13 (14.33 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [276/276]
nice word - saved

Now have this:
> librarian@PAC02:~/AdobeReader$ sudo apt-get install acroread
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
librarian@PAC02:~/AdobeReader$       should i restart this poor machine?

---

### Post by philinux on 2009-07-27
Or just log out then in.

---

### Post by marianlibrarian on 2009-07-27
Closed all windows and restarted. Went to terminal window:
> librarian@PAC02:~$ sudo apt-get install acroread
[sudo] password for librarian:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate
librarian@PAC02:~$
I am really lost.

Edit: Go back to Adept Manager and click on Adept, click on Manage Suppositories and then Click on the tab Third Party. Then by a wonderful miricle there is a NEW Suppository. Put an X in its little box.

---

### Post by marianlibrarian on 2009-07-27
Added the medibuntu to third party software by the terminal

Then went back to the Adept Manager and made sure there was an X in the box beside Medibuntu. 

I have restarted twice now and when I try to install acroread I still get:
> librarian@PAC02:~$ sudo apt-get install acroread
[sudo] password for librarian:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate
librarian@PAC02:~$


I sure wish I could see what I have done wrong. I need to use Kubuntu KDE for the kiosk lock down for public computers.

---

### Post by philinux on 2009-07-27
Open adept and search for acroread to check if it's there.

---

### Post by philinux on 2009-07-27
Open a terminal.

```
sudo apt-get update && sudo apt-get upgrade

```
then try installing acroread

---

### Post by SunnyRabbiera on 2009-07-27
This should have not been this hard.
You made the big mistake of trying to install acroread the windows way by dowenloading from the adobe website.
Medibuntu should have been your first step but now you might have messed up a config file.
I say try a full system restart, that usually fixes most issues with apt.
if not we might have to repair it for you.
You probably messed it up by trying to install the .rpm

---

### Post by marianlibrarian on 2009-07-27
> This should have not been this hard.
You made the big mistake of trying to install acroread the windows way by dowenloading from the adobe website.
Medibuntu should have been your first step but now you might have messed up a config file.
I say try a full system restart, that usually fixes most issues with apt.
if not we might have to repair it for you.
You probably messed it up by trying to install the .rpm     I wondered about that. I did remove rpm and it looked like a successful remove. No errors anyway.

> Open a terminal.

     Code:
     sudo apt-get update && sudo apt-get upgrade 
then try installing acroread     I did the above and the following is in my terminal window: (PS. I installed acroread after I posted the terminal window text because there are some entries at the end that make it look like it won't work. But it does.)
> librarian@PAC02:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for librarian:
Ign cdrom://Kubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090126.1) hardy Release.gpg
Ign cdrom://Kubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090126.1) hardy/main Translation-en_US
Ign cdrom://Kubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090126.1) hardy/restricted Translation-en_US
Ign cdrom://Kubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090126.1) hardy Release
Ign cdrom://Kubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090126.1) hardy/main Packages
Ign cdrom://Kubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090126.1) hardy/restricted Packages
Err cdrom://Kubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090126.1) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Kubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090126.1) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Get:2 [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg [189B]
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [11.7kB]
Get:4 [http://archive.canonical.com](http://archive.canonical.com) hardy Release [9331B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Get:5 [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages [4571B]
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages [6334B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Get:7 [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources [2037B]
Get:8 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages [7345B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Get:9 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources [2625B]
Get:10 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources [4485B]
Fetched 48.8kB in 1s (32.3kB/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch cdrom:[Kubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090126.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Kubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090126.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
librarian@PAC02:~$   Then install Acroread. Following is terminal window text:
l> ibrarian@PAC02:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libbeecrypt6 librpm4.4 linux-headers-2.6.24-23-generic
  linux-headers-2.6.24-23
Use 'apt-get autoremove' to remove them.
Suggested packages:
  libgnome-speech7 libldap2
The following NEW packages will be installed:
  acroread
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 63.4MB of archives.
After this operation, 152MB of additional disk space will be used.
Get:1 [http://archive.canonical.com](http://archive.canonical.com) hardy/partner acroread 9.1.2-0hardy3 [63.4MB]
Fetched 63.4MB in 2min40s (395kB/s)
Preconfiguring packages ...
Selecting previously deselected package acroread.
(Reading database ... 108735 files and directories currently installed.)
Unpacking acroread (from .../acroread_9.1.2-0hardy3_i386.deb) ...
Setting up acroread (9.1.2-0hardy3) ...
Thank you all for your patience and kindness.

---

