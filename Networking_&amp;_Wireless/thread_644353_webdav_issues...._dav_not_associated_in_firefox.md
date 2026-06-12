---
title: "webdav issues.... dav not associated in firefox"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by heatpumpcontrol on 2007-12-18
Hi guys,

I've been trying to connect to my hosted sites using webdav as I used to in Windows just by adding my web address to "network places" and then using Explorer to view my hosted files.

I have tried [http://ubuntuforums.org/showthread.php?t=314000&highlight=firefox+webdav](http://ubuntuforums.org/showthread.php?t=314000&highlight=firefox+webdav) this posting to no avail and many other combinations. What I do end up getting is either 2 results:

1- firefox doesn't know how to open this address, because the protocol (dav) isn't associated with any program.
 or
 2- unable to connect to server, please check your setting and try again --- while using Konqueror under Gutsy

If I use Konqueror to log in to ftp, it works fine. If I use 'Connect to Server' and create an ftp account under Gutsy, Firefox attempts to open the site but never loads anything.

Any help... please. 

One of my sites is iluvfatcats.com. If you can get it to ask you for credentials then you are ahead of me and maybe I'm missing something.

---

### Post by heatpumpcontrol on 2007-12-19
bump...

---

### Post by heatpumpcontrol on 2007-12-20
bump again

---

### Post by heatpumpcontrol on 2007-12-21
Hello... anyone?

---

### Post by ccrs8 on 2008-02-07
I have the exact same problem.  I create the connection, I click on the mounted folder, I get to enter my username/password, and then that error message in firefox.  I don't know why firefox is even trying to open - I'd like to get it to open in the file browser, not the web browser.  Has anyone figured this out?

---

### Post by neurosis on 2008-03-05
Same problem here. Although it works fine over unsecured webdav, and davs works fine in Konqueror. Seems to be a Nautilus thing..

If I enter 'davs://user@host.com:1234' I get "The location is not a folder".

Another option is mounting locally with [davfs2]("http://dav.sourceforge.net/") and browsing that with Nautilus.

---

### Post by metator on 2008-03-28
> **neurosis said:**
> 
Another option is mounting locally with [davfs2]("http://dav.sourceforge.net/") and browsing that with Nautilus.

Thanks! It worked!

Here's the complete solution:

1 - Install davfs2: ```
sudo apt-get install davfs2
```
2 - Create a directory where you'll mount your webdav remote directory: ```
sudo mkdir /media/dav
```
3 - Mount remote directory:```
 sudo mount -t davfs https://<your_host _url:port>/ /media/dav
```

An icon will show up on your Desktop. Just double click on it and behold your remote directory.  :)

---

### Post by neurosis on 2008-03-28
Anyone try it with Gnome 2.22/Hardy?

---

### Post by PokerJoker on 2008-04-14
> **metator said:**
> Thanks! It worked!

Here's the complete solution:

1 - Install davfs2: ```
sudo apt-get install davfs2
```
2 - Create a directory where you'll mount your webdav remote directory: ```
sudo mkdir /media/dav
```
3 - Mount remote directory:```
 sudo mount -t davfs https://<your_host _url:port>/ /media/dav
```

An icon will show up on your Desktop. Just double click on it and behold your remote directory.  :)

You might want to add uid and gid so you have rw access as a user:

```
 sudo mount -t davfs -o uid=<yourid>,gid=<yourgroup> https://<your_host _url:port>/ /media/dav
```

---

### Post by davbren on 2008-04-14
I'm seriously not having any luck with this, Its not even working in Konqueror. Do you think its a Linux thing because my friends can do it in windows and mac...?

---

