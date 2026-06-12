---
title: "Help Installing Songbird"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by psychx on 2009-02-13
[SIZE="4"]Hello all. I am completely new to Ubuntu[/SIZE] and Linux in general. I have tinkered with it before but I have just recently made the switch. In order to learn quickly, I decided not to dual-boot and to just run Ubuntu solely.

Anyway, on with my problem. I have been getting used to simple commands via Terminal, such as changing directories and unzipping files. Now here is where I am lost: I moved my 'Songbird_1.0.0-860_linux-i686.tar.gz' file into the /opt directory. I then moved myself into that directory via Terminal. Then I run the command :

> tar xzvf Songbird_0_2_1_linux-i686.tar.gz
and get this (last few lines of complete output):
```
tar: ./Songbird/components/sbProperties.xpt: Cannot open: No such file or directory
./Songbird/components/browsersearch.xpt
tar: ./Songbird/components/browsersearch.xpt: Cannot open: No such file or directory
./Songbird/songbird.png
tar: ./Songbird/songbird.png: Cannot open: No such file or directory
./Songbird/README.txt
tar: ./Songbird/README.txt: Cannot open: No such file or directory
tar: Error exit delayed from previous errors
mike@mike-linux:/opt$ 

```


What am I doing wrong? I want to install Songbird as my music player. I might also add, when I first downloaded the tar.gz file I opened it via the GUI by double clicking it and extracting it. I wasn't sure what I was doing and opened on the files, which apparently was an executable. It actually opened Songbird and I was looking right at it. Although, I knew this must not be the proper way so I closed out of it and Deleted it. Then I re-downloaded it, just to be safe, and then proceeded to do the above (putting it in /opt and unzipping).

Any help is greatly appreciated, and I am very happy to have found the UbuntuForums.org community and website.

---

### Post by llamabr on 2009-02-13
If you're trying to untar it in /opt, you probably don't have permission.  Try sticking a sudo in front of that command.

---

### Post by psychx on 2009-02-13
Hah.. Thank you. 

I should have known about the sudo command!



This topic can be closed. Thanks for the help, I am sure I will be making more posts around here!

---

### Post by llamabr on 2009-02-13
I think you're the only one who can close it, which you do by changing the subject to include a [solved] tag.

Glad it worked.

---

### Post by thiebaude on 2009-02-13
Just goto getdeb and get the .deb file for Songbird ,[http://www.getdeb.net/](http://www.getdeb.net/)

---

