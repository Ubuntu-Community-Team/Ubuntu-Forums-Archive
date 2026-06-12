---
title: "Utube Ripper and a WTF moment"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2011-05-26
I downloaded Utube Ripper from Sourceforge.

I highlighted the package and right clicked to have the Ubuntu Software Center install the package.

A warning returned with the following:

[COLOR="Red"]Lintian check results for /home/mark/Downloads/utube_1.7-1_i386.gtk (1).deb:
E: utube: wrong-file-owner-uid-or-gid usr/ 1000/1000
E: utube: wrong-file-owner-uid-or-gid usr/bin/ 1000/1000
E: utube: wrong-file-owner-uid-or-gid usr/bin/utube.gambas 1000/1000
E: utube: wrong-file-owner-uid-or-gid usr/share/ 1000/1000
E: utube: wrong-file-owner-uid-or-gid usr/share/applications/ 1000/1000
E: utube: wrong-file-owner-uid-or-gid usr/share/applications/utube.desktop 1000/1000
E: utube: wrong-file-owner-uid-or-gid usr/share/doc/ 1000/1000
E: utube: wrong-file-owner-uid-or-gid usr/share/doc/utube/ 1000/1000
E: utube: wrong-file-owner-uid-or-gid usr/share/doc/utube/changelog.Debian.gz 1000/1000
E: utube: wrong-file-owner-uid-or-gid usr/share/doc/utube/copyright 1000/1000
E: utube: wrong-file-owner-uid-or-gid usr/share/menu/ 1000/1000
E: utube: wrong-file-owner-uid-or-gid usr/share/menu/utube 1000/1000
E: utube: wrong-file-owner-uid-or-gid usr/share/pixmaps/ 1000/1000
E: utube: wrong-file-owner-uid-or-gid usr/share/pixmaps/utube.png 1000/1000[/COLOR]

Is this package SAFE or NOT SAFE to install? -- 

Does the end-user have to make some modifications? And if "yes" is that chmod and chown? Or something in the guts of the code?

And before the copyright police show up, let me say that this is for time shifting so that I do not have to watch the video during streaming. The US Supreme Court ruled with the people and Sony (remember 'beta'? and against the TV-Motion Picture industry years and years ago about this). So, please don't start responding to this post about copyright, unless you are a copyright attorney and want to speak to my agent for service of process. And if you are an attorney, bring the suit on, dude!

---

### Post by crispy_420 on 2011-05-27
What is your ultimate goal?

Download and convert video files?

---

### Post by Mark_in_Hollywood on 2011-05-27
Ultimate goal? I don't have one, really, I want a better understanding of the error messages in case I seem them in some other package.

---

### Post by lightstream on 2011-05-27
You have no ultimate goal? Not even the slightest desire for world domination? Shame on you :P

Well you'll just have to work on that. In the meantime, the error messages seem to indicate that the installer was expecting particular files and folders to have a particular owner (or group) and they don't.

The uid and gid it mentions are 1000, which are the IDs of the first user and group created on a clean install. The root user and group on the other hand have IDs of zero.

Do you think you might have chowned certain system files and folders to your username at some point?

For instance, the /usr folder should be owned by root. If you do a
```
ls -nd /usr
```
what do you see?
You should see something like this indicating the folder is indeed owned by root:
```
drwxr-xr-x 10 0 0 4096 2010-10-07 16:56 /usr
```
If on the other hand you see this:
```
drwxr-xr-x 10 1000 1000 4096 2010-10-07 16:56 /usr
```
it would suggest the ownership of that folder has been changed.

This is not a good idea and is potentially dangerous, as it would mean any process you run can alter files in that location without needing root access.

---

### Post by crispy_420 on 2011-05-29
The error message just means the package is built out of spec with debian guidelines.

[http://lintian.debian.org/manual/ch1.html](http://lintian.debian.org/manual/ch1.html)
[http://wiki.debian.org/Teams/Lintian](http://wiki.debian.org/Teams/Lintian)

I have never had this warning come up for me and I even installed this application in a VM. The thing did not complain of dependencies or the like but it does not run. 

I asked your goals because if you want an application that can download and encode the FLV to MP4 I was going to suggest [xVideoServiceThief]("http://xviservicethief.sourceforge.net/"). The pre-built .deb can be had here: [http://www.getdeb.net/software/xVideoServiceThief](http://www.getdeb.net/software/xVideoServiceThief)

---

