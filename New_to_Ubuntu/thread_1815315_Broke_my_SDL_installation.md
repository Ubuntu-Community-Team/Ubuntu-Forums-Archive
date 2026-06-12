---
title: "Broke my SDL installation"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by kaapo123 on 2011-07-31
Hello, I was trying to build DosBox from source in order to get all the fancy IPX network emulation features, and it required a custom build of SDL, which I then proceeded to download.

After download & archive extraction I compiled and installed the SDL with
```
./configure
sudo make install
```

The program compiled all fine, but now when I try to run any SDL app I get the following error message:
```
Couldn't initialize SDL: No available video device

```

I tried reinstalling the SDL from the Synaptic package manager, but it didn't work. The programs that now give that error used to work all fine. 

So any help how can I fix this problem?

System specs: Asus Eee PC 1015PEM running Ubuntu 10.10.

---

### Post by kimda on 2011-07-31
Sometimes you can do a "sudo make uninstall" to remove the compiled program. Check the Makefile if it has this option. Then if removed reinstall the SDL from the repos.

---

