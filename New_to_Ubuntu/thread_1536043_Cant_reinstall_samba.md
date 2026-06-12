---
title: "Cant reinstall samba"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by boxdream on 2010-07-21
Hi, im a new to ubuntu and linux.
 
I've installed Ubuntu server 10.04. 
 
I have managed to break my samba installation. I'm not able to remove or install samba. I just want it to work. But i see that the [FONT=Courier New]***/etc/samba/smb.conf*** is gone and deleted.[/FONT]
 
[FONT=Courier New]If i try to run [/FONT]
```

[FONT=Verdana]***apt-get remove samba***[/FONT]
dpkg: error processing samba (--remove):
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
Errors were encountered while processing:
samba
E: Sub-process returned an error code
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
 
 
[FONT=Courier New]If i try to run [/FONT]
```

[FONT=Verdana]***apt-get install samba***[/FONT]
E: Could not open file /tmp/samba.template.37550 - open (2: No such file or directory)
E: Unable to write to /tmp/samba.template.37550 - ofstream::ofstream (2: No such file or directory)
E: Could not open file /tmp/samba.config.37551 - open (2: No such file or directory)
E: Unable to write to /tmp/samba.config.37551 - ofstream::ofstream (2: No such file or directory)
debconf: apt-extracttemplates failed: Bad file descriptor
(Reading database ... 28268 files and directories currently installed.)
......
......
......and so on......pretty long error-messages !!!

```
 
 
if i run 
```

***dpkg --configure samba***
dpkg: error processing samba (--configure):
package samba is not ready for configuration
cannot configure (current status `half-installed')
Errors were encountered while processing:
samba

```
 
 
What can i do ? all help appreciated?

---

### Post by lisati on 2010-07-21
You might want to try this before reinstalling:
```
sudo apt-get purge samba
```
This will clear out any relevant configuration files it finds.

---

### Post by boxdream on 2010-07-21
Thanx for the quick reply.
 
I ran 
```

***sudo apt-get purge samba***
dpkg: error processing samba (--remove):
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
Errors were encountered while processing:
samba
E: Sub-process returned an error code
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
 
Tried to install and remove, but i got the same error messages as earlier

---

### Post by phillw on 2010-07-21
Hi, it sounds to me like it got all confused. 

You can manually remove it from the apt list by following [http://forum.phillw.net/viewtopic.php?f=4&t=87](http://forum.phillw.net/viewtopic.php?f=4&t=87)

In your case, the offending package is **samba**.

Regards,

Phill.

---

### Post by boxdream on 2010-07-22
Phillw, now ive done what was explained in your link.
 
It seems that i managed to remove the samba installation. 
 
Later i installed samba again. with apt-get install samba.
 
I've got the /etc/samba/smb.conf back. But i cant see my ubuntu computer and its share in windows 7.
 
i ran this command in ubuntu, and it says that samba installation is half-configured ? any clue, what i can do now ?
```

[B][I]dpkg-query -W -f='${Package} ${Version} ${Source} ${Status}\n' | grep samba
[/I][/B]libsmbclient 2:3.4.7~dfsg-1ubuntu3 samba install ok installed
libwbclient0 2:3.4.7~dfsg-1ubuntu3 samba install ok installed
samba 2:3.4.7~dfsg-1ubuntu3  install ok half-configured
samba-common 2:3.4.7~dfsg-1ubuntu3 samba install ok installed
samba-common-bin 2:3.4.7~dfsg-1ubuntu3 samba install ok installed

```

 
I've used many days and hours on this stuff. :) Trying to share a drive on ubuntu to windows. Is there a alternative way to share drives, besides ftp/ssh/samba ?

---

### Post by phillw on 2010-07-22
Hi,

I'm not a user of samba; I only gave you the instructions to kill a confused package.

If you want to automatically mount a Win (samba shared) area to a ubuntu installation then you can follow the draft notes at [http://forum.phillw.net/viewtopic.php?f=18&t=96](http://forum.phillw.net/viewtopic.php?f=18&t=96) I've not had chance to get these notes completed yet so they are fairly technical but they do work.

Regards,

Phill.

---

### Post by phillw on 2010-07-22
Hi,

I'm not a user of samba; I only gave you the instructions to kill a confused package.

If you want to automatically mount a Win (samba shared) area to a ubuntu installation then you can follow the draft notes at [http://forum.phillw.net/viewtopic.php?f=18&t=96](http://forum.phillw.net/viewtopic.php?f=18&t=96) I've not had chance to get these notes completed yet so they are fairly technical but they do work.

Regards,

Phill.

---

### Post by boxdream on 2010-07-23
Anyone other here who can help me to get my half-configured samba up and working ? is there any way to check if my samba is working properly ?
 
thanx for your help phillw...appreciate it.

---

