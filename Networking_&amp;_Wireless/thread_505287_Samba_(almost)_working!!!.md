---
title: "Samba (almost) working!!!"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by dsewell on 2007-07-20
Hi,

I have set-up Ubuntu to boot from USB, added Webmin and Samba, and, with the exception of the issue below, seems to be working well (not bad for a first attempt at Linux!)

I am primarily using the Ubuntu box as a low-power file server, with a 500gb drive running on a Via EPAI fanless main-board. The Ubuntu box is on a home network, and will be used as a media server (music, movies, backup photos, etc...)

I have managed to access the 500gb drive (sda1), and by using CHMOD I have changed access so that everyone has read / write access. Except, than I can not move files from Explorer in XP. The reason, I think, is that when I move a directory, the directory attributes are changed and I no longer have write access. Therefore, I get a message in Windows saying that I dont have the privalages to edit the directory.

So, I have two questions:

1) How do I fix the issue and set-up Samba / Ubuntu so that I have read/write access to new directories & files added to the shared drive?

2) Is this secure? I have not seen any firewall settings in Ubuntu. Should I be using User accounts and Groups to access the files? If so, any pointers? I have three other PC's on the network so if I need to set-up Users / Groups I guess I will need to do this three times? Yes?

What is the correct / secure way to set-up such a media / home server? If it's using Users & Groups, how do I tie the three XP users to Ubuntu and then to Samba so that they have read/write (and move) access?

Finally, I use SyncToy to back up data on the three XP machines. If I get the XP users set-up, should SyncToy be able to access the Ubuntu box without any problems.

Lots of questions I know, but I am very enthusiastic about the progress so far. This seems to be a sticking point (I have read pages and pages on Samba set-up and still am having problems!)

Thanks in advance.

Dean

---

