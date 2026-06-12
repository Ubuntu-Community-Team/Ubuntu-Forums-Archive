---
title: "Could not mount the shared folder in ubuntu, it works in suse"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by dtzxdtzx on 2007-02-28
Hi, All,

Since I heard that ubuntu is better than suse since it requires less hardware resource. I installed it in vmware server and want to try it.

However, I have encountered a problem to mount the host shared folder. My host is Window XP and the shared folder is C drive. In suse 10.0, I typed
mount -t cifs -o username="domain/username" -o uid="1000" //192.168.187.1/hostC ~frank/hostC

after typed in password, it works. I can read and write in hostC directory. 
The same command in ubuntu in su user mode, I got
mount: block device //192.168.187.1/hostC is write-protected, mounting read-only
mount: cannot mount block device //192.168.187.1/hostC read-only.

Note that ubuntu even did not ask password.

I have the full control of the shared hostC.

Does anyone know why it does not work in ubuntu?

Thanks

Frank

---

### Post by dtzxdtzx on 2007-03-01
I am really disappointed with the help I can get from ubuntu forum. After waiting, I have not get any help on this topics.

I am better to switch back to fedora. By the way, the command is working in fedora, not suse.

Frank

---

