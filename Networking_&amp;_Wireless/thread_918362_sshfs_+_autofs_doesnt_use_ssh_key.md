---
title: "sshfs + autofs doesnt use ssh key"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by kazzmir on 2008-09-12
I've set up sshfs and autofs to automatically mount an sshfs directory by following this article: [http://www.tjansson.dk/?p=84](http://www.tjansson.dk/?p=84)

Everything works fine but autofs doesn't use the keys I have created in .ssh so that I don't have to type in my password. Instead when I cd to the automounted directory, an openssh dialog window pops open asking for my password to login. Once I provide it everything is fine, but I'd like it to use the keys I have already made. I can ssh to the remote machine without using a password just fine, so I know its not an issue like that.

As a workaround I have copied my ~/.ssh directory to /root/.ssh and this fixes the issue, but I'd like to not have to do this. Does anyone know a solution?

---

### Post by ManweX on 2012-01-11
I know this is old. But this answer might be relevant to someone else.

I solved the identity file problem with adding ,IdentityFile=PATH to options.
Here's my options.

```
USER='yourUserName'

-fstype=fuse,idmap=user,rw,nodev,nonempty,transform_symlinks,noatime,allow_other,IdentityFile=/home/${USER}/.ssh/id_dsa,max_read=65536
```

---

