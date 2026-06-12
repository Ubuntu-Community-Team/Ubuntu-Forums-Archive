---
title: "dpkg pakage currupted on ubuntu"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by drathi on 2011-02-16
Hi,

dpkg package is not working on my Ubuntu.Please see attached file .When I try to re-install this package it showing me error message as :

[B]dpkg: parse error, in file '/var/lib/dpkg/updates/0132' near line 0:
 newline in field name `#padding'

[/B]Some problem also occur when i use Synaptic Package Manager.  Kindly suggest me ,how i can re-install or make correct this dpkg package.



Regards

---

### Post by plucky on 2011-02-16
> **drathi said:**
> Hi,

dpkg package is not working on my Ubuntu.Please see attached file .When I try to re-install this package it showing me error message as :

[B]dpkg: parse error, in file '/var/lib/dpkg/updates/0132' near line 0:
 newline in field name `#padding'

[/B]Some problem also occur when i use Synaptic Package Manager.  Kindly suggest me ,how i can re-install or make correct this dpkg package.



Regards

Try from a terminal ```
ls -l /var/lib/dpkg/updates/
```to see what is there,and then remove all the files in that directory.

Use again from the terminal ```
cd /var/lib/dpkg/updates/
sudo rm *
```

Or use ```
gksudo nautilus
``` and navigate to that directory and remove all the files stored there.

**be careful as you are deleting from the system files so make sure you are in the correct directory.**

Then run ```
sudo apt-get update
sudo apt-get upgrade
```


Good Luck

---

### Post by drathi on 2011-02-23
Hi,

I following same process as described above and hang on here:

Reading package lists... Done
W: GPG error: [http://deb.playonlinux.com](http://deb.playonlinux.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E0F72778C4676186
deepak@kalpna-desktop:/var/lib/dpkg/updates$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up playonlinux (3.8.10) ...

Setting up sun-java6-doc (6.20dlj-0ubuntu1.9.10) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u19-docs.zip jdk-6u18-docs.zip jdk-6u19-docs-ja.zip jdk-6u19-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[COLOR=Red][Press RETURN to try again, 'no' + RETURN to abort][/COLOR]

[COLOR=Black]Nothing to work after this.. :([/COLOR]

---

### Post by tajiknomi on 2011-02-23
Try this in terminal:-

```
[COLOR=#000000][FONT=Times New Roman]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E0F72778C4676186[/FONT][/COLOR]
```

then:-

```
sudo apt-get update && apt-get upgrade
```

---

