---
title: "How do i get ownership of the windows samba mount"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by Sheytan on 2007-12-13
I use this command to mount

sudo smbmount //hades/Downloads /home/sheytan/test ?????

I forgot the ???? command in like two hours so sheytan could delete and copy files to test.

i tried to search but i can't find any help the command was quite simpel it was ????sheytan something like that

Sorry for my crapy english
------------------------

I solved it just took me two hours to find the answer (lol iäm only installing linux  to use [FONT=Arial][SIZE=4]**Comix**[/SIZE][/FONT])

sudo smbmount //hades/Downloads /home/sheytan/test -o rw,uid=sheytan

---

