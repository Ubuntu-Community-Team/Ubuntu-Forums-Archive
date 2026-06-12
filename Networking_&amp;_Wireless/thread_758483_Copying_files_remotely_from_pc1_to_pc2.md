---
title: "Copying files remotely from pc1 to pc2"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by ben22 on 2008-04-18
Hi,

I am trying to copy files from remote pc to local pc.

The target folder is called target1 and on the local pc. The remote pc has the IP 190.160.0.33.

Neither of the following is working, can u help me with the syntax?

```
scp ben3@192.168.0.33:/home/originfolder/ /home/targetfolder

scp ben3@192.168.0.33:/home/originfolder/\/home/targetfolder
```

thx,
ben

---

### Post by SpaceTeddy on 2008-04-18
mhm - how about you try loggin in with sftp command and then just browse the files until you get to the right place. Use get to get the file... 

i.e. it should look like this
> cd /home/targetfolder
sftp ben3@192.168.0.33
cd /home/originfolder/
get %file%

if that is NOT desired (because you need it automated or something) i would like to point out that you can ONLY copy files, and not directories via scp and sftp. If you want full directory structures, i would suggest you have a look at sshfs, which could be used to attach a remote directory to your local filesystem via ssh. Once that is done, you can use the normal cp commands to copy stuff over... 

hope it helps :)

---

### Post by ibutho on 2008-04-18
This works for me
```
$scp -r user@host:/path/to/remote/dir /path/to/new/dir
```

---

