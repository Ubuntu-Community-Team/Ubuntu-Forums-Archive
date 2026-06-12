---
title: "DropTeam install problems"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by acrosome99 on 2009-02-11
Wow.  I'm in over my head here...  New Linux convert.

Anyway, I love wargames and I'm trying to install DropTeam, from Battlefront.com.  I just got the disk in the mail today.  I have managed to copy the InstallData files into a directory on my desktop, and puzzled out the (utterly inadequate) installation instructions.  I figured out that I have to copy a few lib files to the ./InstallData/lib directory... done.  Then I get this:

dean@dean-desktop:~/Desktop/DropTeamSetup$ ./runLinuxInstall
./InstallData/bin/LinuxInstall: error while loading shared libraries: libaa.so.1: wrong ELF class: ELFCLASS64
dean@dean-desktop:~/Desktop/DropTeamSetup$ 

So, what the %@%$# is an ELF class?  Does that mean I can't run this on my 64bit machine, or what?  libaa.so.1 exists in both my /usr/lib directory and in the ./InstallData/lib directory.  Putting copies of libaa.so.1 in the ./InstallData/bin file doesn't change anything- I still get the error.  Is there a way to fix this?

---

### Post by acrosome99 on 2009-02-13
Bump? :confused:

---

