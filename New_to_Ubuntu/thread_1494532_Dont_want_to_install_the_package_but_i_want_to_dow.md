---
title: "Dont want to install the package but i want to download it.."
date: 2010-05-27
forum: New to Ubuntu
---

### Post by karthick87 on 2010-05-27
I dont want to install the package but i would like to download the package via terminal and install it later.How it can be done..?

---

### Post by lisati on 2010-05-27
Which package?

---

### Post by karthick87 on 2010-05-27
> **lisati said:**
> Which package?

ie.[COLOR=Red]VLC[/COLOR]

---

### Post by inameiname on 2010-05-27
If you want to search for and find a package, or packages, try this:


[http://packages.ubuntu.com/](http://packages.ubuntu.com/)


UPDATE:

Here is 'VLC'

[http://packages.ubuntu.com/search?keywords=vlc&searchon=sourcenames&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=vlc&searchon=sourcenames&suite=lucid&section=all)

---

### Post by lisati on 2010-05-27
Less than a minute with Google: [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by Elfy on 2010-05-27
```
sudo apt-get install -d vlc
```

Will download the package and dependencies and not install it - wasn;t sure so I tried 

```
Fetched 12.8MB in 54s (236kB/s)                                                          
Download complete and in download only mode
```

---

### Post by karthick87 on 2010-05-27
> **forestpiskie said:**
> ```
sudo apt-get install -d vlc
```Will download the package and dependencies and not install it - wasn;t sure so I tried 

```
Fetched 12.8MB in 54s (236kB/s)                                                          
Download complete and in download only mode
```


Thanks a lot,this what i need :)

---

### Post by egalvan on 2010-05-27
> **lisati said:**
> Less than a minute with Google: [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

Except that the commands listed there will download AND install..

the OP wants to download AND NOT install.

---

