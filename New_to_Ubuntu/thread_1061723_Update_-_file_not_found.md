---
title: "Update - file not found?"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by longtom on 2009-02-06
Hi,

when I want to download update information with any of the update programs, this is the error message I get:

[b]Failed to fetch file:/tmp/setupsdeb/Packages.gz  File not found
Some index files failed to download, they have been ignored, or old ones used instead.[/b]

I am still fiddling around to fix my [samba](http://ubuntuforums.org/showthread.php?t=1061689) - could that be my problem?

clueless

longtom

---

### Post by hyper_ch on 2009-02-06
```

sudo apt-get update

```
what's the output of that?

---

### Post by longtom on 2009-02-06
> **hyper_ch said:**
> ```

sudo apt-get update

```
what's the output of that?

Here you are:

sudo apt-get update
[sudo] password for cango: 
Ign file:  Release.gpg
Ign file:  Translation-en_ZA
Ign file:  Release
Ign file:  Packages                   
Err file:  Packages                   
  File not found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_ZA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_ZA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
W: Failed to fetch file:/tmp/setupsdeb/Packages.gz  File not found

E: Some index files failed to download, they have been ignored, or old ones used instead.

Hope that helps.

longtom

---

### Post by hyper_ch on 2009-02-06
post the output of:

```

cat /etc/apt/sources.list

```

---

### Post by longtom on 2009-02-06
> **hyper_ch said:**
> post the output of:

```

cat /etc/apt/sources.list

```

here you are:

cat /etc/apt/sources.list
deb file:/tmp/setupsdeb /

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe main

---

### Post by hyper_ch on 2009-02-06
that's all you got in there?

---

### Post by longtom on 2009-02-06
> **hyper_ch said:**
> that's all you got in there?

That's it mate.  Pasted in in, typed it myself....that's all I get.

You sound perplexed...?

---

### Post by hyper_ch on 2009-02-06
well, somehow you got your sources.list beaten up badly, best to recreate it.

You can use the tool in my signature. It will generate the could that you need to put in.

use then
```

gksudo gedit /etc/apt/sources.list

```

to edit it.

---

### Post by longtom on 2009-02-06
My dear friend from Helvetia - you did it!

I can see my Ubuntu machine on the WinXP network!  Danke vielmal!!!:D

Now...

One of these WinXP machines has a shared Canon Pixma 4500 connected to it.  How can I convince my Ubuntu machine, firstly, recognise this printer, and than print to it.

Sorry I press this in this thread, but you seem to be a network man of note, so I take advantage...:p

Thanks again

longtom

---

### Post by hyper_ch on 2009-02-06
better to open a new thread for that question.

---

