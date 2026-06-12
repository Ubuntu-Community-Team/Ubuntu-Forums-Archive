---
title: "Testing server automatic ftp to Virtualmin sites"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by greentrees on 2011-06-14
Hi All,
 
I'd like to have something akin to automatic ftp from my Windows box to my local Ubuntu webserver which hosts several testing sites via Virtualmin.
 
What I'd like it do is to automatically upload a file to my server when said file is saved on the Windows box then I can surf to the test site and see the result.
 
Am starting to think that some kind of file sync system, perhaps using FreeFileSync on the Windows box via a Samba share would be the way to go then it might preserve file timestamps which would be fab. 
 
I have Samba running and currently use it as a NAS but have struggled to make any headway with my goal. 
 
Sites on the testing server live in home/sitename/public_html so ideally I'd like to synchronise d:mywebs\mysite\ (windoze) with home/mysite/public_html (ubuntu) and d:mywebs\testsite\ with home/testsite/public_html etc.
 
I wonder if someone could help me with some pointers please ? Many thanks -Gt

---

### Post by crispy_420 on 2011-06-14
Are the server and workstation on the same LAN? Why not use samba instead of ftp?

I was thinking the server has a samba share as the root directory of the web server. Then mount said share as a local drive/folder in Windows box. It would look like you are saving locally but the files would be where you need them automatically. 

Does that make sense? It was also eliminate the need for ftp altogether for this purpose.

---

### Post by greentrees on 2011-06-15
What a great idea -thank you !!!

Sorry it's taken a while to reply -been engrossed in my super new development environment :D

Just one small difficulty..  each site on my testing server has a user name so I have to start my Windoze box goto \\myserver then login using a site's username which means I can't access the others, is there any way round this I wonder ?

---

### Post by crispy_420 on 2011-06-15
So multiple directories are used then for several sites?

Why not share/map each? Won't be using any space anyway in the Windows box. Sounds like you need the right set of permissions on each of course. But once you get them mapped and save passwords during the process it should be straight forward after that as long as there are no changes.

---

