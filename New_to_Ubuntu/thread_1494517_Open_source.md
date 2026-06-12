---
title: "Open source"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by Makosz on 2010-05-27
Ive been told many times that linux is open source. I think it means that i can read the written software on somthing. If i am wrong please correct me but if thats what it means how can i read it?

---

### Post by v1ad on 2010-05-27
precisely you can edit the code of just about anything to fit your needs.

though you need to be a decent programmer to do so.

---

### Post by Ozymandias_117 on 2010-05-27
> **Makosz said:**
> Ive been told many times that linux is open source. I think it means that i can read the written software on somthing. If i am wrong please correct me but if thats what it means how can i read it?

The only source that is written to your hard drive by default (you have download any other source code you want) is in /usr/src and /usr/local/src

---

### Post by Ozymandias_117 on 2010-05-27
To download the source code for a package just type ```
sudo apt-get source *packagename*
```

---

### Post by Makosz on 2010-05-27
> **Ozymandias_117 said:**
> To download the source code for a package just type ```
sudo apt-get source *packagename*
```


I just downladed openoffice.org source code where do i view it now? Also what type of software can i view the source of?

---

### Post by jerome1232 on 2010-05-27
Not that it matters but you don't need root privilages to download source code (unless your downloading it to somewhere that requires root privileges to write to!)

So that can be just
```
apt-get source package-name
```

It will be downloaded to your present working directory, so if you just open a terminal and ran that, your home directory. You will need to change it's permissions since you used sudo and thus it will be owned by root.

To do that just open a terminal with your filebrowser still open, type the following, make sure to leave a space at the end and drag and drop the folder to the end of the line, then hit enter.

```
sudo chown -R $USER:$USER 
```

---

### Post by jocko on 2010-05-27
> **Makosz said:**
> I just downladed openoffice.org source code where do i view it now?
You just unpack the archive file you downloaded and open the files in a text editor.
If you downloaded it through apt-get it's already unpacked, so just browse to the folder you downloaded it to.
> **Makosz said:**
> Also what type of software can i view the source of?
Any type of software, as long as it is released under an open source license, such as GPL.

---

