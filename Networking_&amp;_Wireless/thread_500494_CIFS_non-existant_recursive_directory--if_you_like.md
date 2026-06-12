---
title: "CIFS non-existant recursive directory--if you like filesystem/sharing puzzles..."
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by Maytag on 2007-07-13
Problem in short: **On a CIFS share (problem didn't exist when same share mounted as smbfs) I can access a directory that doesn't exist, which takes me back to the root of the share.** IE: /media/fileserver/Unsorted/mp3/ doesn't actually exist (verified directly on the server, via WinXP share, and an ls -al from the Ubuntu machine that the problem is occurring on) but if I "cd /media/fileserver/Unsorted/mp3/" I end up back at the directory listing for the root of the share, ie: /media/fileserver/ This recursion does not continue (/media/fileserver/Unsorted/mp3/Unsorted/ exists, but /media/fileserver/Unsorted/mp3/Unsorted/mp3/ does not, and attempting to cd etc. doesn't work--ie; expected behavior.)

Problem in long: (is that a turn of phrase?)

I have a file server, also running Ubuntu Feisty, setup with a main Samba (3.0.24) share that I access with a variety of computers, both Ubuntu and WinXP. I have never had any problems accessing this share, and am relatively sure that the problem is not on the server side.

When I had the share mounted using smbfs, (which I had always done since.. kernel 2.2? and all the current howtos still direct you to do so...) I was having frequent problems with smbiod going into a 100% cpu use state when I was trying to do large catalogs of the fileserver over a share. After a bit of searching, I discovered this page: [http://joey.ubuntu-rocks.org/blog/2007/04/25/resolution-to-mounting-samba-shares-dont-use-smbfs/]("http://joey.ubuntu-rocks.org/blog/2007/04/25/resolution-to-mounting-samba-shares-dont-use-smbfs/") which told me, essentially, that smbfs is depreciated and cifs is the way to go. Switching the share to cifs did, in fact, fix the problems I was having.

I am not entirely sure if this is relevant to the problem at hand, but I figure the more information the better. I am going to post this resolution elsewhere on the forums so that it might help someone else, but not before I'm sure it's a reasonable solution. I had a very strange problem when I switched the syntax to cifs--essentially, the uid and gid were no longer being set correctly. The mount was fine, but I couldn't write to it because, despite what I put in the mount line, it was mounting using a different uid and gid. Based off of the information here: [http://lwn.net/Articles/183704/]("http://lwn.net/Articles/183704/") I setup a very shoddy hack to disable LinuxExtensionsEnabled (which is only available after the cifs module loads) and then mount the share much later in my boot. Again, I'm going to share that whole procedure elsewhere, but it might be relevant here, so that's the summary.

The directory in question, /media/fileserver/Unsorted/mp3/ did exist when I noticed the problem. My initial thought was that it was simply too large a directory for cifs to handle (~5000 files+ subdirectories), so I decided to split the directory into 4 separate, smaller directories. This served two purposes: 1. It excluded the large directory size hypothesis. 2. It allowed me to completely delete the original /media/fileserver/Unsorted/mp3/ directory. I made these changes via ssh directly on the fileserver. This being done, (and for any other changes on either side, so it's clear) I unmounted the share locally, restarted samba on the fileserver via ssh, and then remounted the share locally. 

Here's the fun part. After I deleted the directory mp3 from the server (done while logged into the server using ssh, so it was verified not there) I could still navigate into the directory if I did a "cd /media/fileserver/Unsorted/mp3/". This brought me back to the root of the share (/media/fileserver/), as described in the initial problem; this does not recurse.

A few things I've tried:

Server side:
I re-created a directory mp3. Within this directory, I created a directory called test. I restarted everything as mentioned above. The local mount ignores the existence of this directory entirely, unless I recurse through to it (ie: /media/fileserver/Unsorted/mp3/Unsorted/mp3/test/). This makes me think it is a issue with the cifs mount client side. Additionally, all windows and smbfs shares detected this change without issue.

I added "follow symlinks = no" and "dont descend = /pub/Music/Unsorted/mp3" to the share settings in smb.conf on the server, and then restarted as above. These settings made no difference.

I tried ln -s to another empty directory. Ie: I made a symbolic link from an empty mp3test directory to mp3 (of which there was no such file or directory, after my above modifications). This had no effect. I removed this.

Client side:

I have tried mounting using both the command line mount command as well as fstab. Here is the fstab command line I'm using:

//192.168.2.2/mp3 /media/fileserver cifs noauto,uid=maytag,gid=mp3,credentials=/etc/cifspw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

I've tried this with and without the filemode/dirmode, iocharset, and gid/uid entires. The removal/addition of each has the expected result, but does not affect the existence of the non-existent directory.

I looked all over, thinking that cifs or smbfs or something might make a client side cache of the share. I was unable to find anything useful in terms of information about this online. /var/cache/samba/ does exists, but I renamed all existing files to .old and then restarted samba and remounted my shares, and the problem still happened. I don't think much, if any, caching happens on the client side, and doubt that is the problem.

I looked into the possibility that it's a bug with the kernel (running "2.6.20-16-lowlatency"). I have been unable to find any specific bug report related to this with any kernel version. 2.6.22 is available, and the kind Ubuntu kernel team finally decided to make it somewhat possible for users to compile their own kernel (previously this was next to impossible--I've compiled thousands of kernels, and Ubuntu was always a giant pain...) via this website: [https://wiki.ubuntu.com/KernelCustomBuild]("https://wiki.ubuntu.com/KernelCustomBuild") and its sister site: [https://wiki.ubuntu.com/KernelGitGuide]("https://wiki.ubuntu.com/KernelGitGuide"). I have yet to get this possibility to work due to dependency issues after the compile, which is irrelevant for this thread.

I've probably tried other things too, but at this point am running out of ideas, so I posted this monster. If you read the whole damn thing, thanks. If you respond, even more thanks. Any ideas would be welcome--I'm stumped, and would like to straighten this out so I can post and help others...

---

### Post by Mr. C. on 2007-07-13
These types of problems are best described with actual evidence via commands and output.

This is likely a client caching issue (without client caching, performance would be abysmal).  Have you review the sync and dirsync options in the mount man page?

MrC

---

### Post by Maytag on 2007-07-15
Surely, here's some examples:

My fstab line was in the original post, but here it is again: 
```
//192.168.2.2/mp3 /media/fileserver cifs noauto,uid=maytag,gid=mp3,credentials=/etc/cifspw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

As I said before, I've tried this with and without the filemode/dirmode, iocharset, and gid/uid entires. The removal/addition of each has the expected result, but does not affect the existence of the non-existent directory.

As per your suggestion, I have tried this:

```
sudo mount -t cifs //192.168.2.2/mp3 /media/fileserver -o iocharset=utf8,file_mode=0777,dir_mode=0777,credentials=/etc/cifspw,sync,dirsync,uid=maytag,gid=mp3

```

Then these commands, truncated for relevancy:

```

cd /media/fileserver
maytag@BigBlue:/media/fileserver$ ls -al
total 32000
drwxrwxrwx  21 maytag mp3         0 2007-07-15 21:40 .
drwxr-xr-x  13 root   root     4096 2007-07-15 20:32 ..
-rwxrwxrwx   1 maytag mp3       937 2005-07-03 00:41 adblock.txt
drwxrwxrwx 360 maytag mp3         0 2007-07-07 14:29 Albums
(snip)

maytag@BigBlue:/$ cd /media/fileserver/Unsorted/
maytag@BigBlue:/media/fileserver/Unsorted$ ls -al
(snip)
drwxrwxrwx   1 maytag mp3        0 2004-08-11 23:46 Misc. Sounds
drwxrwxrwx   1 maytag mp3        0 2007-07-09 09:34 mp3ae
drwxrwxrwx   1 maytag mp3        0 2007-07-09 09:37 mp3fm
drwxrwxrwx   1 maytag mp3        0 2007-07-09 09:37 mp3ns
drwxrwxrwx   1 maytag mp3        0 2007-07-09 09:43 mp3t9
(snip)

```

As you can see, there is no directory "mp3" in /media/fileserver/Unsorted.

```

maytag@BigBlue:/media/fileserver$ cd /media/fileserver/Unsorted/mp3
maytag@BigBlue:/media/fileserver/Unsorted/mp3$ ls -al
total 31996
drwxrwxrwx 21 maytag mp3        0 2007-07-15 21:40 .
drwxrwxrwx 74 maytag mp3        0 2007-07-09 23:27 ..
-rwxrwxrwx  1 maytag mp3      937 2005-07-03 00:41 adblock.txt
drwxrwxrwx  1 maytag mp3        0 2007-07-07 14:29 Albums
(snip)

```

So this shows the same directory listing in /media/fileserver/Unsorted/mp3 as the mount point, /media/fileserver, despite the fact that mp3 doesn't appear in the directory listing.

```

maytag@BigBlue:/$ cd /media/fileserver/Unsorted
maytag@BigBlue:/media/fileserver/Unsorted$ mkdir mp3
mkdir: cannot create directory `mp3': File exists

```

Something thinks the directory does exist, but ls -al doesn't see it.

```

maytag@BigBlue:/$ cd /media/fileserver
maytag@BigBlue:/media/fileserver$ ls -al
total 32000
drwxrwxrwx  21 maytag mp3         0 2007-07-15 21:40 .
drwxr-xr-x  13 root   root     4096 2007-07-15 20:32 ..
-rwxrwxrwx   1 maytag mp3       937 2005-07-03 00:41 adblock.txt
(snip)

maytag@BigBlue:/media/fileserver$ mkdir 1test
maytag@BigBlue:/media/fileserver$ ls -al
total 32000
drwxrwxrwx  22 maytag mp3         0 2007-07-15 21:56 .
drwxr-xr-x  13 root   root     4096 2007-07-15 20:32 ..
drwxr-xr-x   2 maytag mp3         0 2007-07-15 21:56 1test
-rwxrwxrwx   1 maytag mp3       937 2005-07-03 00:41 adblock.txt
(snip)

maytag@BigBlue:/media/fileserver$ cd /media/fileserver/Unsorted/mp3
maytag@BigBlue:/media/fileserver/Unsorted/mp3$ ls -al
total 31996
drwxrwxrwx 22 maytag mp3        0 2007-07-15 21:56 .
drwxrwxrwx 74 maytag mp3        0 2007-07-09 23:27 ..
drwxrwxrwx  1 maytag mp3        0 2007-07-15 21:56 1test
-rwxrwxrwx  1 maytag mp3      937 2005-07-03 00:41 adblock.txt
(snip)

```

So now I've made a new test directory in the root of the mount, and the directory appears in the non-existant /media/fileserver/Unsorted/mp3 immediately.

My initial thoughts were on caches too, but I have no idea where they are or how to clear them. This immediate appearance of directories inside the offending recursive directory makes me doubt caches.

The same results happen with and without the sync and dirsync options. The mount man page states that those options may not be implemented on all filesystems, and the mount.cifs man page does not mention those options at all.

I appreciate the prompt response. Any other ideas would be greatly appreciated. Please let me know if there is any other information I can provide.

-Maytag

---

### Post by Mr. C. on 2007-07-15
Are you using the automounter autofs ?

MrC

---

### Post by Maytag on 2007-07-15
No, I'm not using autofs. I did not have the package installed, however the package info states >  The kernel automounter implements an almost complete SunOS style automounter under Linux. Automounter version 4 (autofs4) has to be enabled when compiling the kernel. Debian packaged kernels have it enabled. I installed the package "autofs", which creates a dummy set of configuration files, and am looking them over as well as the documentation online, but if I am following your logic correctly after reading the section on two-machine NFS mounts, this package would be a cause and not a solution.

I am going to leave the package unconfigured for the time being and look over the documentation; however, I'm unsure as to whether this will provide a functional solution. Is there some way I should be looking to utilize this specifically?

Or was no the correct answer? :)

---

### Post by Mr. C. on 2007-07-15
I asked about autofs because "mounted" directories under autofs don't appear until their contents are actually referenced.  Under autofs, one can mount, say, /home/me and an ls of /home will not show /home/me.  However, a cd /home/me will succeed, as the file system is mounted upon reference.

Your situation appears on the surface to have the same characteristics, so I suspected autofs.

MrC

---

### Post by Maytag on 2007-07-15
Yes, as I continued to read the documentation on it I gathered that that was likely the cause of your question. I removed the package that I had just installed. I wish that was the solution... 

Additional information: This does not occur if I mount using smbfs. Unfortunately, smbfs fails in many other ways that make it unusable for my needs. Also, I can neither see nor access the recursive directory from any Windows machine, or any other machine I have used to mount with smbfs. 

I have a third Ubuntu machine running at home, tomorrow I will try mounting using the same CIFS lines and see if the problem is reproducible there. 

Is there anything else that I might be able to try that could be useful? I greatly appreciate the time and feedback.

---

### Post by Mr. C. on 2007-07-15
I don't have much experience with cifs.

The man page (man mount.cifs) shows some areas of concern or investigation:
> 
**setuids**
    If the CIFS Unix extensions are negotiated with the server the client will attempt to set the effective uid and gid of the local process on newly created files, directories, and devices (create, mkdir, mknod). If the CIFS Unix Extensions are not negotiated, for newly created files and directories instead of using the default uid and gid specified on the the mount, cache the new file's uid and gid locally which means that the uid for the file can change when the inode is reloaded (or the user remounts the share). 
**nosetuids**
    The client will not attempt to set the uid and gid on on newly created files, directories, and devices (create, mkdir, mknod) which will result in the server setting the uid and gid to the default (usually the server uid of the user who mounted the share). Letting the server (rather than the client) set the uid and gid is the default.If the CIFS Unix Extensions are not negotiated then the uid and gid for new files will appear to be the uid (gid) of the mounter or the uid (gid) parameter specified on the mount. 
**perm**
    Client does permission checks (vfs_permission check of uid and gid of the file against the mode and desired operation), Note that this is in addition to the normal ACL check on the target machine done by the server software. Client permission checking is enabled by default. 
**noperm**
    Client does not do permission checks. This can expose files on this mount to access by other users on the local client system. It is typically only needed when the server supports the CIFS Unix Extensions but the UIDs/GIDs on the client and server system do not match closely enough to allow access by the user doing the mount. Note that this does not affect the normal ACL check on the target machine done by the server software (of the server ACL against the user name provided at mount time). 
**directio**
    Do not do inode data caching on files opened on this mount. This precludes mmaping files on this mount. In some cases with fast networks and little or no caching benefits on the client (e.g. when the application is doing large sequential reads bigger than page size without rereading the same data) this can provide better performance than the default behavior which caches reads (readahead) and writes (writebehind) through the local Linux client pagecache if oplock (caching token) is granted and held. Note that direct allows write operations larger than page size to be sent to the server. On some kernels this requires the cifs.ko module to be built with the CIFS_EXPERIMENTAL configure option.

Perhaps the cifs mailing list will provide more answer?

MrC

---

### Post by Maytag on 2007-07-21
I just posted on the CIFS mailing list. I will promptly post any solution they might help me uncover.

Here's something I put in that email, which all of the sudden came to me. Why it didn't occur to me sooner I'm not sure, because it took me several hours to figure out this hack:

I have one note that wasn't mentioned on that thread, that came to me now. The only way I could get cifs to mount the share with the correct uid/gid was to manually set /proc/fs/cifs/LinuxExtensionsEnabled to 0. I accomplished this by adding the share to fstab but not automounting it, then running an echo and the mount command at the end of my startup scripts. The uid/gid that gets set otherwise is 1001/1001. I believe this is due to misconfigured VFS on the server, but I'm not sure--this workaround solved that problem. Hopefully it is not the cause of the one I'm having now. 

I'm not sure if that could have anything to do with it. The documentation is proving to be unhelpful at best. Hopefully someone with more knowledge than I will be able to help!

---

### Post by Maytag on 2007-08-01
This is an update from information/additional followups on the linux-cifs-client mailing list:

I apologize on taking so long to reply--I had to convince Ubuntu that it wanted to work correctly with a custom kernel (no easy task) so that I could compile in 1.50. If interested, there is some really poorly written documentation on their custom kernel compilation here: [https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild) , which also has a link to using git to pull from their current development tree, which is what I did. Their current development version is 2.6.22-9 according to uname -r, and I replaced their cifs with 1.50 as well as patching with ck's ck1 patch set.

The good news is that 1.50 seems to have fixed the permissions errors I was working around before. I can leave LinuxExtensionsEnabled set to 1 and mount successfully. The share now honors the uid and gid that I specifiy, albeit ignoring my file_mode and dir_mode requests. Using the nounix option worked as you described (essentially LinuxExtensionsEnabled to 0), which then honors the uid, gid, file_mode and dir_mode as specified in the mount.

Here is the command I used to mount:
```
sudo mount -t cifs //192.168.2.2/mp3 /media/fileserver -o iocharset=utf8,file_mode=0777,dir_mode=0777,credentials=/etc/cifspw,sync,dirsync,uid=maytag,gid=mp3

```
Unfortunately, I am still having the same problem with the "ghost" recursive directory, as originally described (or as seen in detail here: [http://ubuntuforums.org/showthread.php?p=3055182#post3055182](http://ubuntuforums.org/showthread.php?p=3055182#post3055182) ).

To update on that thread slightly, I was able to replicate the ghost directory problem on a separate Ubuntu system using the same mount commands, albeit using the LinuxExtensionsEnabled 1 workaround due to the older version of cifs in the non-custom kernel.

Possibly relevant information:
On the client:
package samba is version: 3.0.24-2ubuntu1
package smbfs is version: 3.0.24-2ubuntu1

On the server, samba, smbfs, samba-common are all of the same version.

Could the problem be server side? Possibly something I have wrong in my smb.conf?

Thanks again for your time and responses.

---

