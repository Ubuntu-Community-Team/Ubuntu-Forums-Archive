---
title: "SSH Write Permissions"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by SabreWolfy on 2008-11-08
I've read through many posts on these forums relating to SSH file sharing and write permissions and I have tried the suggestions included in these posts, but I am still not able to write to an SSH mounted folder.

I have a desktop and a laptop, both with Hardy, connected to a local residential gateway ADSL router. The machines can see each other, etc. I can mount an ssh folder with something like:

```

sshfs -p XX user@machine:~ local-folder/

```

This works fine for *read* access of the entire mount. What I cannot get working is being able to *write* to the remote SSH mount. IIRC, I was able to write my /home folder on the remote machine, but I want to write to other folders as well. What I'm trying to do is use Midnight Commander's folder comparison function to copy package files across from one machine to the other, so I need to write to /var/cache/apt/archives on the remove machine.

I've tried running the above command with "sudo", with "-o uid=1000", with "-o allow_other", with "-o allow_root", etc. No combination gives me write access to /var. Some combinations produce a share which I cannot access at all -- the permissions on the local folder are all question marks. Other combinations create the mount and I can read files, but I cannot get write access. I have sshfs and openssh-server install of course.

Any suggestions?

Thanks.

---

### Post by Stu09 on 2009-01-24
Bump.
I'm having a very similar problem.

---

