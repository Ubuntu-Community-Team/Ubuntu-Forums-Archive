---
title: "Automatic mounting of network drives at startup"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by Pawcatuck on 2008-07-19
I'm sure this has been asked and answered 1,000 times, but I'm not very adept at the search function on this forum.

I'm using Ubuntu 8.04 on a desktop computer that is connected to a Windows 2003 server. There are two shared folders on that server that I would like to have automatically mounted once I log in to Ubuntu. I can go into Nautilus, hit Ctrl-L, and mount them for the session, but I'd like to skip that step.

If anybody can suggest where I can go and find information on this tactic, or write a sample script and tell me where to put it, it would be greatly appreciated.

I have to use Samba. I've had no luck at all establishing a workable SSH route with this server.

Thanks.

---

### Post by cdtech on 2008-07-19
Have you tried Places > Network ? I have mine setup as samba shares from my server and using "Windows Network - Home". I can either connect to server or use the Network Places to go to my shares.

---

### Post by goexplode on 2008-07-20
Samba shares can be automatically mounted at boot.

Step 1. Create a mountpoint, e.g.
[INDENT]```
sudo mkdir /media/share
sudo chmod 777 /media/share
```[/INDENT]

Step 2. Edit /etc/fstab
[INDENT]```
sudo gedit /etc/fstab
```
Add something like the following:
```
//remotecomputer/share /media/share cifs user=USERNAME,password=PASSWORD,workgroup=WORKGROUP,user,noatime 0 0
```
If you do not have an appropriate line in /etc/hosts for your server then just use the IP address instead, e.g. "//SERVERIP/share". Also, replace USERNAME and PASSWORD with the username and password that you use to connect to the share. If you do not use a specific username and password then you can you can just delete "user=USERNAME,password=PASSWORD,".
[/INDENT]

Step 3. Repeat steps 1-2 as needed for all other shares.

Step 4. Reboot and make sure everything works.

---

### Post by bolewin on 2008-07-20
> **goexplode said:**
> Samba shares can be automatically mounted at boot.

Step 1. Create a mountpoint, e.g.
[INDENT]```
sudo mkdir /media/share
sudo chmod 777 /media/share
```[/INDENT]

Step 2. Edit /etc/fstab
[INDENT]```
sudo gedit /etc/fstab
```
Add something like the following:
```
//remotecomputer/share /media/share cifs user=USERNAME,password=PASSWORD,workgroup=WORKGROUP,user,noatime 0 0
```
If you do not have an appropriate line in /etc/hosts for your server then just use the IP address instead, e.g. "//SERVERIP/share". Also, replace USERNAME and PASSWORD with the username and password that you use to connect to the share. If you do not use a specific username and password then you can you can just delete "user=USERNAME,password=PASSWORD,".
[/INDENT]

Step 3. Repeat steps 1-2 as needed for all other shares.

Step 4. Reboot and make sure everything works.

Not having posted the original question, but having the same problem I attempted the solution so thoroughly described in the post quoted. The solution was exactly along the lines of my preconceptions (based on earlier experience with Linux back in the days of 1.x kernels).

In spite of following what seems to be good advice all I get is:
 CIFS VFS: cifs_mount failed w/return code = -22

which is not very helpful to me, and I really need to 'properly' (i.e. traditionally) mount my nework shares since the kind of 'mounting' that Nautilus executes hide the share from many programs (i.e. those that do not understand the syntax smb://192.168.100/SHARE)

Help would be appreciated.

Bo L

---

### Post by goexplode on 2008-07-20
See [this]("http://ubuntuforums.org/showthread.php?t=280473") thread for more information.

**bolewin** and **Pawcatuck** too, be sure that you have smbfs and smbclient installed before you do what I mentioned in my previous post.

```
sudo apt-get install smbfs smbclient
```

**bolewin**, if that doesn't solve your problems then you should probably start a new thread, don't want to hijack the OP's thread! :)

---

### Post by Pawcatuck on 2008-07-20
Before I get going on this, I have one question about the code line:

It ends with 0 0. What does that mean? I'm probably just being obsessive, but that's me. I know I have smbclient, I'll make sure I have smbfs as well. (On edit:

```
/lib/modules/2.6.24-19-generic/kernel/fs/smbfs
```

That looks like the real deal?)

I don't mind if bolewin hijacks this thread...just in case the same thing happens to me!

Thanks!

---

### Post by bolewin on 2008-07-20
Thanks to **goexplode**! I had to install also the smbfs package (which is not included in the standard setup). Ironically the description of the smbclient package ends with: " If you want to mount shares exported from Microsoft Windows machines or a Samba server you must install the smbfs package." Which makes me wonder why I should want the smbclient package if I did not want to mount shares from a Samba server, and why the two packages don't come together.

Anyway, now it all works like a charm.

And as for **Pawcatuck's** question about the two zeros the answer is that:

"The  fifth  field,  (fs_freq),  is  used  for  these filesystems by the dump(8) command to determine which filesystems need to be  dumped.   If the  fifth  field  is not present, a value of zero is returned and dump will assume that the filesystem does not need to be dumped.

The sixth field, (fs_passno), is used by the fsck(8) program to  determine the order in which filesystem checks are done at reboot time.  The root filesystem should be specified with a fs_passno of  1,  and  other
filesystems  should  have a fs_passno of 2.  Filesystems within a drive will be checked sequentially, but filesystems on different drives  will be  checked  at  the  same time to utilize parallelism available in the
hardware.  If the sixth field is not present or zero, a value  of  zero is  returned  and fsck will assume that the filesystem does not need to be checked."
(quoting man fstab)

All the Best!

---

### Post by Pawcatuck on 2008-07-20
> **goexplode said:**
> Samba shares can be automatically mounted at boot.

Step 1. Create a mountpoint, e.g.
[INDENT]```
sudo mkdir /media/share
sudo chmod 777 /media/share
```[/INDENT]

Step 2. Edit /etc/fstab
[INDENT]```
sudo gedit /etc/fstab
```
Add something like the following:
```
//remotecomputer/share /media/share cifs user=USERNAME,password=PASSWORD,workgroup=WORKGROUP,user,noatime 0 0
```

I have it working now!

A couple of notes, for those who might be passing through:

I added four shares, and they all looked something like:

```
//192.168.1.2/Workbooks /home/pawcatuck/share cifs user=Pawcatuck,password=mindyourownbusiness,workgroup=OURHOUSE,user,noatime 0 0
```

In the other cases, the name "Workbooks" was replaced by the names of the Windows shares.

I ended up with four icons and four corresponding Nautilus entries, each named "share," and each with identical contents: the last of the four. It turned out that each line overwrote the previous one, because I was writing each shared folder in turn to /home/pawcatuck/share.

I fixed that, and it still didn't work. The solution was to rewrite fstab yet again, and then create directories with the target name, and *then* reboot. For instance, /home/pawcatuck/share/Workbooks, /home/pawcatuck/share/ToDoLists (not a favorite around here, but necessary), /home/pawcatuck/share/Letters. Once I created those directories, the commands that I'd put in fstab had an actual destination, so to speak, and it's working better than I could even have imagined.

Giddy from my success, I installed about 60 Bitstream fonts from my WordPerfect discs. I'm about 99.8% of the way to Ubuntu Nirvana, and the .2% will be taken care of when I add a couple of lines to my .emacs file.

Thanks to all who chipped in with this.

---

### Post by Pawcatuck on 2008-07-20
Well, it's never over....

I noticed that Ubuntu now hangs during shutdown. The last two lines were

```
CIFS VFS: server not responding
CIFS VFS: No responce for cmd 50 mid 69
```

I had to hold the "off" button on the computer, which I never like to do.

I had the idea that if I unmounted the shared folders before shutting down, I would avoid that. But when I tried, I was told that "only root can unmount this shared volume" (or words to that effect).

So I think I need some help with permissions...or, if there's a known way around this problem, that would be great, too.

Thanks again.

---

### Post by Pawcatuck on 2008-07-20
Gaa. Just noticed that everything on the shared folders is read-only. Don't know why I didn't catch that an hour ago. Guess I really need some permissions help.

---

### Post by Pawcatuck on 2008-07-21
I noticed something this morning. In the line I copied a few posts ago -- the end of it was obscured by this board's "code" formatting, so here it is again --

//192.168.1.2/Workbooks /home/pawcatuck/share cifs user=Pawcatuck,password=mindyourownbusiness,workgroup=OURHOUSE,user,noatime 0 0

Near the end, I've still got "user". If I replace that with my sign-in name, might that take care of some of the permissions problems?

I'm not at that particular computer now, but I'll try that when I get there. In the meantime, any suggestions deeply appreciated.

(Later)
It didn't help. Now even when I try to open a file through the traditional Ctrl-L | smb://blahblah, the files are coming up "read only."

(A day later)
The "read only" went away. There are a lot of variables here, but I'll report what I did:

For some obscure reason, some of my Windows shares had reverted back to various statuses that weren't full rights. I went through and checked every one for sharing status. That didn't seem to remedy my problem immediately; however, I did not completely shut down both boxes right then; I went upstairs and shut down the Linux computer again afterwards, and still had trouble.

I then uninstalled ConSSH, a Windows SSH client with which I was experimenting. That seemed to help. I have no idea whether, or how, ConSSH was keeping shares open even after I had shut down ssh-agent and ssh-add in Ubuntu, but maybe it was doing things on the Windows side.

I also unshared several folders on the server, and put new shares on. That apparently finally broke whatever connections had remained opened, and I can get to everything now. I still have to do the Ctrl-L and type in smb://192.168.blah/blah/blah to get to my network files, so my original question remains lost in the thickets of whatever quirks my home network has. But I'm living with it just fine. 

To anybody who has been following this thread, I apologize for the panicky posts and the blow-by-boring-blow reports. But maybe the information will help someone down the road.

---

