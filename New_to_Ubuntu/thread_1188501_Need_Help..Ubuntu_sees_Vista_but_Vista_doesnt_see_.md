---
title: "Need Help..Ubuntu sees Vista but Vista doesnt see Ubuntu"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by blsbball on 2009-06-15
Been searching all day for an answer. So I am somewhat new with ubuntu but have played around with it before. Just installed 9.04 on an old dell and hooked it up to a router in my apartment. I want to keep all my movies and music on this computer so myself and my roommates can access it with our lappys. I installed Samba which resulted in full access to the vista shares from ubuntu (once i figured out my firewall). But when I go into the Networks on the vista laptop it does not show any sign of the ubuntu desktop. Any ideas? Let me know what information you need.
thanks

---

### Post by jamesrfla on 2009-06-15
Have you tried sharing any files on Ubuntu yet? Installing samba will not automatically start sharing files.

---

### Post by briguy47 on 2009-06-15
Have you already Right-Clicked on the folder you want to share and set the "Sharing Options"?  

If not, you need to do that and enter a "Share Name".  That is what your Vista machines will be able to see on the network.  :)

Let me know if that works or if you have any questions.  :D

---

### Post by SoftwareExplorer on 2009-06-15
Also, by default, your Ubuntu computer will be in the 'workgroup' workgroup. That means that you may have to look for it in a different workgroup than Vista's.

---

### Post by blsbball on 2009-06-15
Thanks for the replies....I have created a folder on the desktop to share and right clicked it and set up sharing. And my vista workgroup is WORKGROUP as well so Im pretty sure that is not the issue.

---

### Post by SoftwareExplorer on 2009-06-15
This might be obvious, but are ports 137,138, and 139 open?

And, of course, welcome to UbuntuForums.org

---

### Post by GenePayne on 2009-06-15
I had the same problem, this page helped me to get it working:

[HTML]https://help.ubuntu.com/9.04/internet/C/networking-shares.html[/HTML]

---

### Post by Hoodline on 2009-06-15
its actually vista its self i had the same issue when i burned a cd on vista and put it in a pc with xp it showed up as the cd was blank you could upload the files to rapidshare or something like that and download them via your pc to solve the issue

---

### Post by blsbball on 2009-06-15
well after trying to make changes to the shared folders i found out that my root folder is completely out of space. somehow my old dell messed up the partition and everything has been put into dev/sda5

---

### Post by blsbball on 2009-06-16
So I finally worked it out and now the network is up and running just fine. However I am having a new problem Im sure you experts could work out. The space in my /dev/sda3 folder where ubuntu is installed is depleting rapidly. 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              17G  3.7G   13G  24% /
tmpfs                 123M     0  123M   0% /lib/init/rw
varrun                123M  524K  122M   1% /var/run
varlock               123M     0  123M   0% /var/lock
udev                  123M  148K  123M   1% /dev
tmpfs                 123M  256K  122M   1% /dev/shm
lrm                   123M  2.4M  120M   2% /lib/modules/2.6.28-11-generic/volatile

I have only installed Samba. Any ideas?

---

