---
title: "Cannot find Firefox 6.0 downloaded package"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by hannah187 on 2011-08-21
Hi All,

I have downloaded firefox 6.0 from here 
[http://www.mozilla.com/en-US/firefox/new/](http://www.mozilla.com/en-US/firefox/new/)

and the bzip archive had opened with Archive Manager which I had closed without taking any action. And now I cannot find this bzip archive. I have looked into the download folder and it is not there.

Is there a terminal command which I can use to find out the location of last downloaded file please.

Many thanks

---

### Post by thatguruguy on 2011-08-21
> **hannah187 said:**
> Hi All,

I have downloaded firefox 6.0 from here 
[http://www.mozilla.com/en-US/firefox/new/](http://www.mozilla.com/en-US/firefox/new/)

and the bzip archive had opened with Archive Manager which I had closed without taking any action. And now I cannot find this bzip archive. I have looked into the download folder and it is not there.

Is there a terminal command which I can use to find out the location of last downloaded file please.

Many thanks

When you download a file, you can choose to save it or open it with an appropriate application.  You chose to open it.  Try to download it again, and this time make sure to save the file.

---

### Post by thatguruguy on 2011-08-21
By the way, you may have better luck if you just install the official mozilla ppa.  To do so, type the following in a terminal:
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```You will be prompted for your password, and the public key for the ppa will be downloaded automatically.
Then, type:
```
sudo apt-get update
```You can then install firefox 6 directly from synaptic or the Ubuntu Software Center.

EDIT: Removed erroneous dash in mozillateam.

---

### Post by ankspo71 on 2011-08-21
Hi,
If you have not restarted your computer yet then it should still be in the system's temp folder located at "/tmp". Firefox put it in a temporary location because you chose to open the file instead of saving the file to your downloads folder. Firefox doesn't have a way to download a file and then open it automatically, but there are probably some download managers that might.

Hope this helps.

---

### Post by hannah187 on 2011-08-21
thanks for all the advice.. looked into the /tmp folder..it's not there..but appreciate all the advice..and next time will download properly..

thanks

---

### Post by tetrisalphabet on 2011-08-21
> **thatguruguy said:**
> By the way, you may have better luck if you just install the official mozilla ppa.  To do so, type the following in a terminal:
```
sudo add-apt-repository ppa:mozilla-team/firefox-stable
```You will be prompted for your password, and the public key for the ppa will be downloaded automatically.
Then, type:
```
sudo apt-get update
```You can then install firefox 6 directly from synaptic or the Ubuntu Software Center.
I tried this but when I put in 
```
sudo add-apt-repository ppa:mozilla-team/firefox-stable
```
I got an error that says 
```
Error reading https://launchpad.net/api/1.0/~mozilla-team/+archive/firefox-stable: HTTP Error 404: Not Found
```
Are you sure that's correct?

---

### Post by Brushstroke on 2011-08-21
It's actually: 

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade
```

thatguruguy added an extra dash in the PPA link.

---

### Post by thatguruguy on 2011-08-21
I sure did.  Good catch.

---

### Post by lovinglinux on 2011-08-24
For future reference see [Firefox 4,5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

---

