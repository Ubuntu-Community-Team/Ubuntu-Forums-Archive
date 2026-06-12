---
title: "How can I make my custom repo trusted?"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by falkTX on 2009-06-15
Hi there guys. I'm having a small trouble...

Some days ago I started making my own repository for Ubuntu:
```
deb http://falktx.xtreemhost.com/repo/ubuntu jaunty sixa
```
It downloads and installs fine all packages, and it's working for amd64, i386 and powerpc. 
The problem is that my repo is untrusted. Also, when refresh by 'apt-get update' it gives me
```
Erro GPG: http://falktx.xtreemhost.com jaunty Release: As seguintes assinaturas eram inválidas: NODATA 1 NODATA 2
```
I know that I need some Release.gpg files on the same dir as Jaunty/Release and Jaunty/Release/binary-'ARCH'. I tried to put there the official Ubuntu ones but it didn't work.

What do I need to do?

Thanks in advance
*(Please don't link me to some Debian docs place, I don't need all that; just need to know how to make it trusted)*

---

### Post by falkTX on 2009-06-15
bump

---

### Post by reeseslover531 on 2009-06-15
check [this]("https://help.ubuntu.com/community/SecureApt") wiki page out

---

