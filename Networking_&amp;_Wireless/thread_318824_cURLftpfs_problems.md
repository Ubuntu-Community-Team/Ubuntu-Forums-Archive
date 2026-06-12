---
title: "cURLftpfs problems"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by shinda on 2006-12-14
I'm trying to setup a virtual ftp folder using curlftpfs. I've downloaded and installed all the libraries and packages, but keep running into a permissions problem when I try to access the folder outside of root.

Basically what I'm doing / have done is the following: 


```
sudo chmod o+rw /dev/fuse
mkdir ftpfolder
sudo curlftpfs -o user="username:password",uid=1000,gid=1000,nonempty ftp://ftp.url.com ftpfolder/

``` 
Now when I try to do a ls of the ftpfolder which I would expect would give me a listing of the main folder on the ftp site I instead get:

```
ls: ftpfolder: Permission denied
```

I've tried as root to chmod the folder but that also generates an error:

```
chmod: changing permissions of `ftpfolder/': Operation not permitted
```

None the less when doing ls as root, everything seems to work the way it should. 

Being new to the linux and the unix world (just installed ubuntu last week) I'm not all that familiar with what I'm doing but trying to go through the paces as best I can, so if anyone could help shed some light on how to fix this, it would be most appreciated. 

Thanks

---

### Post by shinda on 2006-12-14
Nevermind guys was able to figure it all out thanks to: [http://kumar.travisbsd.org/blog/?p=18](http://kumar.travisbsd.org/blog/?p=18)

Basically adding ```
sudo adduser <yourusername> fuse
``` made all the difference.

---

### Post by N00BIE12345 on 2006-12-28
Hi. Or:
```
sudo curlftpfs -o user="username:password",allow_other ftp://ftp.url.com ftpfolder/
```

---

### Post by Mateo on 2007-05-08
hi, I'm trying to get this to work.  I added my user to the "fuse" group but this doesn't help me any.  I looked in nautilus and the FS is under the root group.  I tried to change it to fuse but it wouldn't let me.  any ideas?

edit:  by the way, I didn't mount to my home directory like that link uses, I mounted to the /mnt/ directory.  not sure if that makes a difference or not.

---

### Post by Mateo on 2007-05-08
ok, I figured it out.  for those having similar problems, after creating the directory to mount into, you want to make it part of the fuse group and give the group permission to read and write.  i did this from nautilus but you can do it from command line to (don't ask me how).  then, when you run the curlftpfs command, don't do it from sudo, otherwise your user can't access the filesystem.  Also, I recommend putting in the fstab line, that way it shows up in Computer as any other filesystem.  awesome stuff!

---

