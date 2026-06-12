---
title: "Saving Audacity Project Files"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Tootler on 2009-04-26
I made some recordings using a portable recorder and I have transferred these to my computer for editing using Audacity. 

The recordings are 16 bit wav files and are saved on a FAT partition mounted at /media/DATA which I use so as I can access the files from either windows or ubuntu. This works fine most of the time, but when I try to save the files as Audacity projects I get the following error message:

```
Impossible to set permissions for /media/DATA/Target Folder/Song_data/xx..xx.au (error 1: Operation not permitted)
```

When you 'OK' the error message you get a second message box which says:

```
Unable to save project. Perhaps /media/DATA/Target Folder/Song Name is not writeable or the disk is full
```

As the drive partition was only about 1/3 full the latter was clearly not the case.

I tried copying the original audio data to my home folder, imported it into Audacity and was able to save it as an Audacity project no problems. 

I then looked at the folder properties of the target folder and in the permissions tab, the owner of the folder was set to root and the group was also root and the permissions were set to create and delete files. Similarly looking at individual files permissions were set as owner root and group root with read and write permissions.

On the other hand, the permissions for folders and files show the owner and group as my  user_id with the permissions set to create and delete files or read and write as appropriate.

Up till now this has caused no problems and I have been able to create, edit and delete files with no problems. Even with Audacity I can open the wav file and export it as an mp3 OK, so it seems that the problem lies with Audacity somehow needing permission to create a critical file. The problem seems to lie with the .au file that holds the information about the data as the folder with all the project data is created OK.

I tried changing file and folder ownership using chown but that did not work and got a message saying "Operation not permitted"

A search suggested that the ownership needs to be set when the partition is mounted at startup, but I have not been able to work out how to do that. FWIW the line in fstab that mounts the partition is:

```
UUID=1C80-61A1  /media/DATA      vfat    user,fmask=0111,dmask=0000   0   0
```

Any help appreciated.

Geoff

---

### Post by Tootler on 2009-04-27
I have just looked on the Audacity Forum and this problem has been reported there for v1.3x

---

### Post by FSHero on 2009-08-10
I am trying to save a project using Audacity 1.3.7. I'm using Kubuntu 9.04 (Jaunty) amd64. I'm saving it to an NTFS partition, presumably using ntfs-3g.

Every other application I use (e.g. Kate) can save files to this drive. However, when I try to save a project in Audacity I get the following error message:
Could not save project. Perhaps /media/data/mypath/myfile 
is not writeable or the disk is full.

Audacity is able to save to my ~ (home) folder.

I tried setting the following line in my fstab:
```

UUID=17C637E46C4ACABC /media/data     ntfs    defaults,nls=utf8,umask=001,gid=users 0       1

```

Important part: umask=001, to give "other" users read and write permissions.

Now, running "ls -l" shows the following (an example file and directory are given):
```

drwxrwxrw- 1 root users 20480 2009-08-10 07:56 download
-rwxrwxrw- 1 root users 691491576 2009-06-08 13:30 nexuiz-251.zip

```

However, I still get the same error message when I try to save in Audacity. Why is Audacity unable to save? How do I get it to save?

---

### Post by Tootler on 2009-08-10
This appears to be an ongoing problem with audacity. See this thread in the audacity forum
[http://forum.audacityteam.org/viewtopic.php?f=18&t=2724](http://forum.audacityteam.org/viewtopic.php?f=18&t=2724)

Currently I save my audacity projects on my /home/me directory and will do so until the issue is resolved.

---

