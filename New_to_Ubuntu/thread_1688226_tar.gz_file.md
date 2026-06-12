---
title: "tar.gz file"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by euloiix on 2011-02-15
Hi everyone,

Something not so hard is preventing me to install cakePHP :) 

_There it is:_ 
I use the following command to extract my archive: 

[HTML]tar -zxvf NAME_OF_ARCHIVE[/HTML]

Where has the extraction been done ? 
I can tell that it is not in the same folder as the archive.

Let me know, I am sure the question is not so hard to answer though.

Thank you so much for helping.
++):P

---

### Post by DexterLB on 2011-02-15
welcome :)
the extraction must have been done in the same folder you ran the command in

---

### Post by TeoBigusGeekus on 2011-02-15
Try with
```
tar xvf NAME_OF_ARCHIVE
```
ie without the dash.

---

### Post by Paqman on 2011-02-15
Easiest way to extract a tarball is just right click > extract here.

---

### Post by coffeecat on 2011-02-15
@euloiix, do you have a particular reason for trying to install CakePHP from source code, such as wanting the latest version?

It's in the Ubuntu repository, just a couple of mouse clicks away in the Software Centre. No real need to mess with a tar.gz file.

---

### Post by euloiix on 2011-02-16
No particular reason. I just did not think of using it.
Thank you.

My laptop has been taken away from me by Acer's people for some time but I will use the software center for sure.
Still I am wondering: how come it did not (and this I am sure of) extract the archive in the same folder ? 
And would you have any idea where the content has been extracted ?
How could I look for it for example ?

):P

---

### Post by coffeecat on 2011-02-16
As DexterLB has already said, if you did...

```
tar -zxvf filename.tar.gz
```...the tarball will have been extracted in the same folder. However, it might have had its own folder with all the contents, and you'll find its own folder within the extraction folder. Say you had placed an archive called fred.tar.gz in your home folder and extracted it, then you will probably find a folder called 'fred' in your home folder with all the files inside it. Or sometimes the folder might be called something else. You'll just have to have a look around.

If you right-click on the archive and choose 'open with Archive manager', you can see the structure of the archive without extracting it. You can then extract it with Archive manager without having to use the terminal - as someone has already pointed out.

As far as software installation in Ubuntu is concerned, have a look at this:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

