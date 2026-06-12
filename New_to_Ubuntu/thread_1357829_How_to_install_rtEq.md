---
title: "How to install rtEq"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by mikee55 on 2009-12-17
Hi, I've download an archive containing bin.tar.gz, how do I install this?

Mike:confused:

---

### Post by leprkhn on 2009-12-17
I will assume that it is something like filename-bin.tar.gz.
This is an archive file (like a zip or rar on windows). This is often how source-code is downloaded.
You cannot "install" this file.
Instead you must extract it's contents. The contents are what you install (well... compile THEN install).

To extract the file's contents:
```
gunzip filename-bin.tar.gz
```

This should make a new directory (folder) in the same location as the original file. Inside that directory are the files that were contained in the archive.

---

### Post by mikee55 on 2009-12-17
Hi, the file is called

rtEq-0.6.0-bin

is gunzip your extraction tool?

Mike:)

---

### Post by aysiu on 2009-12-17
It looks like a precompiled binary and not source code.

**Instructions**
Assuming it's on your desktop, pasting these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) should do it: ```
cd ~/Desktop
tar -xvzf rtEq-0.6.0-bin.tar.gz
cd rtEq-0.6.0-bin
./rteq
``` **Explanation**
Roughly translated, that's ```
cd ~/Desktop
``` Change directory to be the desktop folder of the currently logged in user.
```
tar -xvzf rtEq-0.6.0-bin.tar.gz
``` Extract the compressed file.
```
cd rtEq-0.6.0-bin
``` Change directory to be the newly extracted one.
```
./rteq
``` Execute the precompiled binary in that folder.

---

### Post by leprkhn on 2009-12-17
> **mikee55 said:**
> Hi, the file is called rtEq-0.6.0-bin

The full filename, then, is rtEq-0.6.0-bin.tar.gz, yes?

> **mikee55 said:**
> is gunzip your extraction tool?

Yes.
```
gunzip rtEq-0.6.0-bin.tar.gz
```

This should leave you with a directory containing the following files: COPYING, CONTACT, and rteq.
To run the application do the following from the command line:
```
cd /path/to/rteq
``` - if you extracted in your /home/user directory it will be something like:
```
cd /home/user/rtEq-0.6.0-bin
```
Then, once inside the rtEq directory, you should enter:
```
./rteq
```

---

### Post by mikee55 on 2009-12-17
Did that

lounge-pc@lounge-pc-desktop:~$ cd ~/Desktop
lounge-pc@lounge-pc-desktop:~/Desktop$ tar -xvzf rtEq-0.6.0-bin.tar.gz
tar: rtEq-0.6.0-bin.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
lounge-pc@lounge-pc-desktop:~/Desktop$ cd ~/Desktop
lounge-pc@lounge-pc-desktop:~/Desktop$ tar -xvzf rtEq-0.6.0-bin.tar.gz
rtEq-0.6.0-bin/
rtEq-0.6.0-bin/rteq
rtEq-0.6.0-bin/CONTACT
rtEq-0.6.0-bin/COPYING
lounge-pc@lounge-pc-desktop:~/Desktop$ cd rtEq-0.6.0-bin
lounge-pc@lounge-pc-desktop:~/Desktop/rtEq-0.6.0-bin$ ./rteq
./rteq: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
lounge-pc@lounge-pc-desktop:~/Desktop/rtEq-0.6.0-bin$ 




What did I miss?
Mike:)

---

### Post by aysiu on 2009-12-17
> **mikee55 said:**
> 
What did I miss? I think you missed this: [quote=SourceForget rtEq page]As of 2007-06-06 0:00:00 GMT, this project is no longer under active development.[/quote] The last project feed was actually from five and a half years ago.

It depends on libgtk1.2, which doesn't appear to be available any more.

---

### Post by mikee55 on 2009-12-17
Hi, okay thanks. I'm just looking for Graphic Equaliser for Alsa player.

Thanks again 

Mike:(

---

### Post by aysiu on 2009-12-17
> **mikee55 said:**
> Hi, okay thanks. I'm just looking for Graphic Equaliser for Alsa player.

Thanks again 

Mike:(
How about *alsamixer*?
[https://help.ubuntu.com/community/SoundTroubleshooting#Using alsamixer](https://help.ubuntu.com/community/SoundTroubleshooting#Using alsamixer)

---

### Post by mikee55 on 2009-12-18
Hi, Alsa mixer is just that, a mixer. must be one somewhere?

Mike:)

---

