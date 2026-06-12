---
title: "tar.gz"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-02-01
how to install the applications from .tar.gz files?

---

### Post by bolucpap on 2010-02-01
I think you need to be a little more specific if you want a serious answer to your query.

---

### Post by kellemes on 2010-02-01
[https://help.ubuntu.com/8.04/add-applications/C/install-file.html]("https://help.ubuntu.com/8.04/add-applications/C/install-file.html")

Ask if you need any more assistance..

---

### Post by Cheezespread on 2010-02-01
Installation depends on the files that have been included in the zipped tarball you are having. You can extract the contents using this ( in terminal )

```
tar -zxvf <name of tar.gz file >
```

---

### Post by 1991sudarshan on 2010-02-01
sreenivassudarshan@sreenivassudarshan-desktop:~$ tar -zxvf BitTorrent-5.3-GPL.tar.gz
tar: BitTorrent-5.3-GPL.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
 

i got this message in the terminal

---

### Post by Bradtek on 2010-02-01
Also

Right click on file and select extract here
Then look what you have extracted, another file or folder ?
if a folder look inside it for a file named README or INSTALL
or something similar.

---

### Post by ad_267 on 2010-02-01
A .tar.gz file is the same sort of thing as a .zip file, so it depends on what is inside the .tar.gz file after you've extracted it.

Why are you trying to install Bit Torrent from a .tar.gz file anyways? Many Bit Torrent clients are available from Add/Remove or the Ubuntu Software Centre, including the original Bit Torrent client.

---

### Post by Cheezespread on 2010-02-01
> **1991sudarshan said:**
> sreenivassudarshan@sreenivassudarshan-desktop:~$ tar -zxvf BitTorrent-5.3-GPL.tar.gz
tar: BitTorrent-5.3-GPL.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
 

i got this message in the terminal

Is the file in your Desktop or Downloads folder ?

---

### Post by jsmnuk on 2010-02-02
> **1991sudarshan said:**
> sreenivassudarshan@sreenivassudarshan-desktop:~$ tar -zxvf BitTorrent-5.3-GPL.tar.gz
tar: BitTorrent-5.3-GPL.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
 

i got this message in the terminal


The same thing happens to me. My tarball is a Blu-Ray authoring tool, so it's a forgone conclusion that there's nothing like that downloadable with aptitude or Synaptic. If anyone knows differently, plz respond.

---

### Post by ICEB3AR on 2010-02-02
What exactly do you mean?
first of all you have to extract the files/directories of the tar.gz archive. Use a commmand like mentioned before. **Be sure to put in the right path!**
Then told us which files are there. It could be that you have to use a script of itself or e.g. that you have to use
```

./configure
make
sudo make install

```

---

### Post by ad_267 on 2010-02-03
1. Right click on the file
2. Click on extract here
3. See what you've got inside

---

