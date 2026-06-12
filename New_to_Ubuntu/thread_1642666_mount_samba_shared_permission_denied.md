---
title: "mount samba shared permission denied"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by Clive McCarthy on 2010-12-10
I have a shared directory on another Ubuntu machine but I can't get it to mount. The permission denied doesn't say where/which permission is denied. Is it on the remote on on the local machine? The remote has sharing enabled for the shareddocs directory and after I have mkdir'ed the local mount point and I open it's permissions too.

My command from a Bash shell script looks like this:
[INDENT][COLOR="Blue"]sudo mount.cifs //artshow16/shareddocs local_share --verbose -o domain=WORKGROUP,username=clive,password=*****
[/COLOR][/INDENT]
The verbose response from mount.cifs looks like this:

[INDENT][COLOR="Blue"]mount.cifs kernel mount options: unc=//192.168.1.102\shareddocs,domain=WORKGROUP,ver=1,rw ,username=clive,,,,,,,,,,,ip=192.168.1.102,pass=** ******
mount error(13): Permission denied
Refer to the mount.cifs( manual page (e.g. man mount.cifs)
[/COLOR][/INDENT]
The man page does not have a list of error codes.

I'm beginning to suspect that there is something wrong with cifs. There are a number of suggestions on the web that it has problems. One possible issue is the back-slash that cifs converted from a forward-slash in my original command? Any ideas? I'm stuck.   ](*,)

---

