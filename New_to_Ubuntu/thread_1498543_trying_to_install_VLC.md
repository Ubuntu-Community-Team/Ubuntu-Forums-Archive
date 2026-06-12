---
title: "trying to install VLC"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by Kirkland14 on 2010-05-31
I was trying to install VLC as I liked using it in win7.  I tried to install it through the Software center and was denied.  I then went throught the command line checking for the mirrors as instructed by the VLC website. I also tried to follow the code that came from the forum and i received this message(in order from the VLC and then the forum).  Why am I being denied?  Help Please?

kevin@ubuntu:~$ % sudo apt-get update
bash: fg: %: no such job
kevin@ubuntu:~$ % sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc
bash: fg: %: no such job
kevin@ubuntu:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
kevin@ubuntu:~$ 


Thanks,

Kevin

---

### Post by nhasian on 2010-05-31
try removing the % sign from infront of the command:

```
sudo apt-get update
```

then it will work.  now you can do:

```
sudo apt-get install vlc
```

also /etc/apt/sources.list is not a command, its a file.

---

### Post by Kirkland14 on 2010-06-01
Great! thanks.  I'm new to using the command line.  I totally looked right over it.  VLC works fine now.  thanks again for the help

---

