---
title: "simple but good FTP Client"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by manuleka on 2008-12-21
i've been using filezilla on Windows for sometime, now i've migrated to Ubuntu, was wondering if anyone would recommend me a nice FTP Client... i do abit of web designing so i pretty much use it for uploading and updating websites

---

### Post by jimmy the saint on 2008-12-21
gftp works well.  It is in add/remove

---

### Post by manuleka on 2008-12-21
when you say its in add/remove... do you mean synaptic package manager?

---

### Post by 2hot6ft2 on 2008-12-21
> **manuleka said:**
> when you say its in add/remove... do you mean synaptic package manager?
LOL. That would be the place to look... I have gFTP on mine

---

### Post by Defrector on 2008-12-21
FileZilla is available for ubuntu too!

In the terminal, type ```
sudo apt-get install filezilla
```

or...

Use the add/remove programs app, or from the terminal type "sudo synaptic' and search for Filezilla, when you've found it select it (usually right-click) to install, click apply, and that should put it somewhere in your program menu. 

If you have trouble finding it after it is installed, typing something like 'filezilla' in your terminal might bring it up.

---

### Post by scorp123 on 2008-12-22
> **manuleka said:**
> i've been using filezilla on Windows for sometime, now i've migrated to Ubuntu, was wondering if anyone would recommend me a nice FTP Client...  How about staying with FileZilla then?
```
sudo apt-get install filezilla
```

A nice alternative would be "gftp". The file manager would work too, just type in **[ftp://username@server](ftp://username@server)** as target location, and voila, you get a FTP session right in your file manager. Or mount it as remote folder:

Places > Connect to Server > FTP (with login) ... fill out the details such as server address, username, etc. and voila: you'd get your remote FTP directory as folder icon right there on your desktop and can directly drag & drop stuff between FTP and your local computer.

---

### Post by SlidingHorn on 2008-12-22
I just started using gftp the other day, and I'm loving it!

If you're using firefox, you could also use the FireFTP addon

---

### Post by manuleka on 2008-12-23
thanks guys i'll try Gftp since it's been mentioned a few times :)

---

### Post by andrew.46 on 2008-12-23
Hi manuleka,

> **manuleka said:**
> thanks guys i'll try Gftp since it's been mentioned a few times :)

I have Gftp as a backup and it is a great program. However it may be worth your while to invest some time and effort into setting yourself up an rsync script. The syntax is not exactly intuitive and must be used with some caution but it is probably the most effective and economical way to upload website changes.

Can anyone suggest a nice gui for rsync?

Andrew

---

### Post by binbash on 2008-12-23
+1 for filezilla.Get the latest deb forum getdeb.net

---

### Post by orlox on 2008-12-23
Or, you could just use the file manager, if your requirements are not very complex...Just try with File->connect to server

---

