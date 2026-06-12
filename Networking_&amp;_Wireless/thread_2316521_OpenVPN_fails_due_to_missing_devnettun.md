---
title: "OpenVPN fails due to missing /dev/net/tun"
date: 2016-03-08
forum: Networking &amp; Wireless
---

### Post by Richard_Payne on 2016-03-08
I've installed OpenVPN on Ubuntu 14.04 but when I try to run it I get:

> Tue Mar 8 23:24:32 2016 ERROR: Cannot open TUN/TAP dev /dev/net/tun: No such file or directory (errno=2)Tue Mar 8 23:24:32 2016 Exiting due to fatal error

Following a search session, I tried the following:

> # modprobe tun

which results in:

> modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.13.0-52-generic/modules.dep.bin'

/lib/modules does not exist.

However, I've been unable to find a solution for this.
Any thoughts?

---

### Post by Richard_Payne on 2016-03-08
Forgot to add, this is inside a docker container running on a ubuntu 14.04 host, if it makes any difference.

---

### Post by SeijiSensei on 2016-03-08
I found this which sounds like the same problem: [https://groups.google.com/forum/#!topic/docker-user/2jFeDGJj36E](https://groups.google.com/forum/#!topic/docker-user/2jFeDGJj36E)

He had to use the -privileged switch to get root privileges in the container and create /dev/net/tun with the mknod command.  See the post by Pierre Masci for the details.

---

