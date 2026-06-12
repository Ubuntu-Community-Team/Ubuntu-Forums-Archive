---
title: "unknown configuration directive 'DisplayFirstChdir' on line 23 of '/etc/proftpd/proft"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by Reglon on 2010-04-25
:confused:Im trying to set up FTP capabilities using this guide "http://www.intac.net/build-your-own-server/"

In the comments many people have had the same problem as me when trying to start or restart proftpd which is:

"Fatal: unknown configuration directive "DisplayFirstChdlr" on line 23

I have searched quite a bit and tried this:

perl -pi -e 's/DisplayFirstChdir/DisplayChdir/' /etc/proftpd.conf

Didnt so anything that I could tell




I posted this in this forum instead of networking simply because I am an absolute beginner and probably would understand the directions given to me in any other forum.


So does anyone have any idea? help is appreciated

---

### Post by cariboo on 2010-04-26
Does ftp work if you use the default config file? Personally I use sftp, which is a part of the openssh-server package. Just open nautilus and type:

```
sftp://user@server
```

You should also use private/public keys with ssh, for a howto have a look [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys").

---

