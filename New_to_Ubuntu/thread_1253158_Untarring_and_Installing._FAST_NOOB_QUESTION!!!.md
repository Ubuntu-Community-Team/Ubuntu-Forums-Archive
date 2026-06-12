---
title: "Untarring and Installing. FAST NOOB QUESTION!!!"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by Nukester on 2009-08-29
I untarred madwifi, and a folder named madwifi-0.9.4 with the files inside appeared, but it isnt a .deb file, so I can't just double click on it and install. So my question is: How do I install through Terminal?

---

### Post by NoaHall on 2009-08-29
First, use
cd #location of files
and then do
ls
and copy and paste the out put on here

---

### Post by nhasian on 2009-08-29
this is a fast noob question?  hehe  

This may be what you'll need:

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

alternatively using a newer version of ubuntu should automatically recognize your wifi adaptor.

---

### Post by Nukester on 2009-08-29
[b]cd ~/Desktop
sudo -s
apt-get install build-essential
tar -xzvf ndiswrapper*
cd ndiswrapper*
make
make install[/b]

I see this, but where do I substitute the madwifi file?
Can anyone do this for me?

---

### Post by NoaHall on 2009-08-29
No where, you use insteed of ndiswrapper* the location of the file
so, it could be
```

 cd /home/noah/Downloads/madwifi
make 
make install

```

---

