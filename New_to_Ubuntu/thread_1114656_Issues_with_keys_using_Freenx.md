---
title: "Issues with keys using Freenx"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by azmyth on 2009-04-03
I've installed Freenx on my Ubuntu 8.10 computer and I'm accessing from WindowsXP using the download from nomachines. I can get freenx to work without using keys but when I try to do this with keys I have authentication issues.

I followed these two guides.

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)
[http://ubuntuforums.org/showthread.php?t=467219](http://ubuntuforums.org/showthread.php?t=467219)

On the second link, I was able to pass the connection test on 6. I think my problem occurs when I try to add a user.

I do a nxserver --aduser username

and I get an error that says

/etc/nxserver/users.id_dsa.pub No such file or directory

If I just create the file and then adduser the file is blank after I add user and the same goes for the /home/username/.ssh/authorized_keys2 as this is blank as well.

I figured I just create keys and add to the file but this doesn't work either. Anyone have a hint?

---

### Post by azmyth on 2009-04-04
I believe there's a bug with Freenx with respect to using keys. I ended up going to nomachine.com and downloaded their packages and everything is now working.

---

