---
title: "Run program as root"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by Neoncamouflage on 2011-07-02
So I downloaded the latest VMware Player, as I always enjoyed using it on Windows and have recently come in need of a good virtual machine program. It downloaded fine and I ended up with "VMware-Player-3.1.4-385536.i386.bundle" in my downloads directory. Now here's where it gets annoying. I set it as executable, try to run it, and it says I need root access. So I reset all the permissions to allow everyone access to it, still says I need root. I go to the terminal and type:
```
sudo VMware-Player-3.1.4-385536.i386.bundle
```
and it says that VMware-Player-3.1.4-385536.i386.bundle is not a command.

So, here's something that I've always been trying to figure out, and now it seems I really actually need to know. How do you straight up tell something to run from the terminal, and in this case, do so with root access.

---

### Post by e79 on 2011-07-02
```
chmod +x VMware-Player-3.1.4-385536.i386.bundle
```

```
sudo ./VMware-Player-3.1.4-385536.i386.bundle
```

or

```
sudo sh VMware-Player-3.1.4-385536.i386.bundle
```

Hope this helps

---

### Post by Neoncamouflage on 2011-07-02
./


You're kidding me. All of my trouble, all of my difficulty....was over ./

I love computers. XD Thanks a ton man.

---

### Post by e79 on 2011-07-02
My pleasure :P I'm glad you could get that fixed !

Regards

---

