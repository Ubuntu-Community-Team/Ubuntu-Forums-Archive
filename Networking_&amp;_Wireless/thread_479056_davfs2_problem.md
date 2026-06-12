---
title: "davfs2 problem"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by Biochem on 2007-06-19
I mounted my webdav account using this command:

sudo mount -t davfs -o uid=Biochem,rw,dir_mode=775,file_mode=775 [https://www.server.ca/dir/](https://www.server.ca/dir/) media/Maison

When I try to copy some file by entering:

cp -r /media/Microscopy/Sam /media/Maison

I get I the following error message:

cp: cannot create regular file `/media/Maison/Sam/D5_GFP_02.tif': Invalid argument

I also have the same invalid argument when I create files.

Any Idea what I'm doing wrong?

Thanx

---

