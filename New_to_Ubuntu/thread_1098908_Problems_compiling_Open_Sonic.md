---
title: "Problems compiling Open Sonic"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by shiv379 on 2009-03-17
Hi all,

I'm having a problem compiling something, and I really don't know where to go to fix this. I've searched online but I can't find anything that seems to help. It's OpenSonic I'm trying to compile, and I do have allegro downloaded and compiled, however the compiler doesn't seem to be able to find it when linking.

```
# 85%# Building C object CMakeFiles/opensonic.dir/src/iconlin.o
Linking C executable opensonic
gcc: `allegro-config: No such file or directory
make[2]: *** #opensonic# Error 1
make[1]: *** #CMakeFiles/opensonic.dir/all# Error 2
make: *** #all# Error 2
```
NB: I've replaced the square brackets in the output above with # symbols so it'll display.

```
sudo find / -name allegro-config
/opt/allegro-4.2.2/allegro-config
/usr/local/bin/allegro-config

```
NB: The /opt/ dir is where I've got the source for allegro and am compiling it from. Yeah I know it's not the right place!

I've tried editing my ld.so.conf file but to be honest I haven't the faintest clue what I'm doing! This is what my file looks like now:
```
include /etc/ld.so.conf.d/*.conf /usr/local/lib
```

Can anyone point me in the right direction? I'm keen to learn how to do these things right!

~Shiv

---

