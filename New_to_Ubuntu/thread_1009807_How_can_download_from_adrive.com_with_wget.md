---
title: "How can download from adrive.com with wget ?"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by xinloiemnham2 on 2008-12-13
I found that wget is a very good downloader. So I use it to download everythings. But I cannot download from adrive.com with it. When I click on a link shared from adrive, flashgot appear and I choose downloader I want, I choose wget but it download a .html file. If I choose downthemall, it can download files from that link.
Help me plz! Thank you all in advanced !

---

### Post by nakama85 on 2008-12-13
> **xinloiemnham2 said:**
> I found that wget is a very good downloader. So I use it to download everythings. But I cannot download from adrive.com with it. When I click on a link shared from adrive, flashgot appear and I choose downloader I want, I choose wget but it download a .html file. If I choose downthemall, it can download files from that link.
Help me plz! Thank you all in advanced !

Have you tried using wget via the terminal?

---

### Post by nakama85 on 2008-12-13
See if it will work by right-clicking the link and clicking copy link location then in terminal enter
```
wget _*paste link here*_ /home/_*username*_
```

Let me know if that works for you.

note: if this works it will download **everything** within that page
if you don't want to download everything then add any filters that correspond with your needs.

---

### Post by xinloiemnham2 on 2008-12-13
I tried to copy the link that flashgot detected and paste it into terminal like:
```
wget <link>
```
For example, I want to download this link :
```
http://www.adrive.com/public/42939776a6037196dd50cade7a82a79e50f36fa15b22aa10ba73805a431c1fec.html
```
I copied and pasted it into firefox, and flashgot detected the url, I choose downthemall, everything went through till the download complete. But if I copy the url appear in this (don't start download with downthemall)
[IMG]http://img75.imageshack.us/img75/9620/screenshotaddurlsdv8.png[/IMG]
I have this url :
```
http://download.adrive.com/public/view/42939776a6037196dd50cade7a82a79e50f36fa15b22aa10ba73805a431c1fec.html
```
If I copy this link and paste it into terminal for command above, wget wil download a html file.

---

### Post by nakama85 on 2008-12-13
sorry not sure. I tried it myself. The best I can figure is that the link is a java popup type that wget does not recognize

---

### Post by SuperBo on 2008-12-28
You can try this
```
 wget --content-disposition -r  -H -Ddownload.adrive.com -Ahtml -nd -np -e robots=off -l0 <adrive link>
```

---

### Post by julemand101 on 2009-01-18
SuperBo: Are you sure that command is right? The parameter "-Ahtml" will delete all files other than *.html. I was trying you command and after 3 hours the files was finish but wget delete them because the filename was *.rar. Wget don't delete all the *.html temp files.

I try download again without the "-Ahtml" parameter and now its works:
wget --content-disposition -r  -H -Ddownload.adrive.com -nd -np -e robots=off -l0 <adrive link>

---

