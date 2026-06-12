---
title: "Retrieving lost files"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by Japster on 2011-02-09
I have a huge problem and need assistance.

I copied files from a ntfs partition onto my ubuntu desktop. It is about 100Gb files. I was not able to make a folder on the system file part of ubunthu, why I don't know. Anyway, i discovered that I could make a file inside the /tmp folder. As I wanted to keep the files only until today, to copy it onto my external, I decided to make a folder there and move it from the desktop to the folder I created inside the tmp.

Today when I start the pc and go to the tmp folder, I discover with shock that the folder I created with the files in are gone. I can't find it, when I look at my free space, I can see that those files are somehow deleted, as I got the free space back.

No can someone pls help me, how do I retrieve those files. Normal undeleteres don't work for the ext3 format, so how am I going to retrieve my data. 

I have not copied anything on the partition to make sure I can retrieve the stuff. Im using ubuntu 9.10

---

### Post by nothingspecial on 2011-02-09
/tmp is cleaned every time you boot or when a program exits.

It's supposed to be for programs to store stuff in that they only need temporarily.

Why didn`t you save them in your home directory?

Don`t know if you can get them back.

Try testdisk/photorec

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Luinar on 2011-02-09
Yes, it is important to remember in future that you shouldn't be creating files and folders yourself inside of the file system. You said that it wouldn't let you, and things like this are the reason why. Any folders you create to store your files should be made within your home directory (/home/USERNAME) - it's what it is there for.

I'm guessing you have deleted the files from the original NTFS partition? If testdisk/photorec doesn't work, I guess you could always try using a file recovery tool on the NTFS partition and trying to get them back that way?

Also, you may want to familiarise yourself with the structure of the Linux file system: [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

---

### Post by Primefalcon on 2011-02-09
[http://www.addictivetips.com/ubuntu-linux-tips/how-to-recover-deleted-filesdata-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-recover-deleted-filesdata-in-ubuntu-linux/)

---

### Post by Japster on 2011-02-09
Thanks guys for the help it seems that I came right

---

