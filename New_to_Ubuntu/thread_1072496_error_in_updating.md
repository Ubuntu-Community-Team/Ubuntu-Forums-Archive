---
title: "error in updating"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by chirucam on 2009-02-17
hi,when i started ubuntu, there were some 268 updates to be done.. but 74 are still left to be done. Everytime i do update it shows something like this after a few seconds--- W: Failed to fetch [http://ubuntu.indika.net.id/ubuntu/pool/main/c/compiz-fusion-plugins-main/compiz-fusion-plugins-main_0.7.4-0ubuntu6_i386.deb](http://ubuntu.indika.net.id/ubuntu/pool/main/c/compiz-fusion-plugins-main/compiz-fusion-plugins-main_0.7.4-0ubuntu6_i386.deb)
  404 Not Found [IP: 202.87.191.51 80]
please help.. thanks. (i have 8.o4 and a dell inspiron 1525)

---

### Post by drs305 on 2009-02-17
The file doesn't currently exist on the server. You can try another server by going to synaptic or software sources: settings, respositories, download from > click and try another server.

Added:

The file on this server has been updated from:
compiz-fusion-plugins-main_0.7.4-0ubuntu6_i386.deb
to:
compiz-fusion-plugins-main_0.7.4-0ubuntu6**.2**_i386.deb

---

### Post by avtolle on 2009-02-17
That is a repository for 7.04, which reached its end-of-life (as to support) in October, 2008. I don't know which release you are running, but at a minimum, you will need to comment out or delete the references to 7.04 (if you are using a later release) in your /etc/apt/sources.list file, then try again. 

To edit (I use nano)```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old #make a backup
sudo nano /etc/apt/sources.list #open file for editing
```then, after making your changes, do a Ctrl+o to write out the file as changed, press Enter to save to the default file name, then Ctrl+x to exit nano. Then, also in the terminal do ```
sudo apt-get update
sudo apt-get upgrade
```to see if you can receive your updates/upgrades.

If you are still using 7.04, you need to upgrade to a newer release, imo. Good luck.

---

### Post by chirucam on 2009-02-18
Hey drs305, it worked absolutely fine.. ihad to change the server. thanks everyone..

---

### Post by drs305 on 2009-02-18
I checked before posting and saw that the repository you have enabled still has 7.04 packages, but I would agree with avtolle that you should consider upgrading to a newer version of ubuntu. 

If you don't, you will eventually may need to add a repository from here to continue to access 7.04 packages:
[http://old-releases.ubuntu.com/ubuntu/]("http://old-releases.ubuntu.com/ubuntu/")

---

