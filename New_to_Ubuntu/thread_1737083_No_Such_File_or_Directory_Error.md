---
title: "No Such File or Directory Error"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by ruff1298 on 2011-04-23
I keep getting a Terminal Error that says my Downloads folder in the Home folder does not exist. I´m trying to install Wine via source tar.gz package (Synaptic has issues), and I´m losing hope after several tries and still no success.

Would somebody please tell me how to get the Terminal to recognize that downloaded files exist? Thanks.

---

### Post by frup on 2011-04-23
Better copy and paste the error here. It will be case sensitive so there is a difference between Downloads and downloads for example.

---

### Post by LowSky on 2011-04-23
dont build from source!!!!!

what is wrong with synaptic?

what happens if you run this code from terminal

```
sudo apt-get update && sudo apt-get update && sudo apt-get upgrade && sudo apt-get install wine
```

yes i know there are two updates.. just do it. sometimes that will fix it.. if not let us know

---

### Post by ruff1298 on 2011-04-23
ramon@Garcia:~$ tar xvzf wine.tar.gz
tar (child): wine.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

Downloads Folder is in Home Folder.

---

### Post by Locke_99GS on 2011-04-23
If the wine tarball is in the Downloads directory, you either need to change to that directory first, or specify that directory in the tar command. I would create a new directory,move the file to it, make it you working directory, then untar it and build it.

```

mkdir ~/wine_build
mv ~/Downloads/wine.tar.gz ~/wine_build/wine.tar.gz
cd ~/wine_build
tar xzvf ./wine.tar.gz

```


I personally only build things when I need a newer version than I can get packaged, or I need to apply patches or specify configure options. It would probably be worth it to get your package manager sorted out.

---

### Post by yetiman64 on 2011-04-23
> **ruff1298 said:**
> ramon@Garcia:~$ tar xvzf wine.tar.gz
tar (child): wine.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

Downloads Folder is in Home Folder.

Have a look at the file in your home directory and check the extension. I suspect it may be a .targz file. Not .tar.gz.

It's up to you if you want to build from source but I would recommend you try the command LowSky gave. Building from source is generally not recommended for beginners.

---

