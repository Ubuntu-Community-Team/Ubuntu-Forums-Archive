---
title: "Just starting and already problems (download)"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by DC80 on 2010-04-22
Hi all,

I'm not really sure were to post this so i'm hoping i'm in the right spot. I'd like to download Ubuntu so i can install it. However, there is a problem. My first attempt had a file size of just 407 Mb. My second attempt had a file size of 641 Mb or so it said.

My question is, what is the right download size of the .iso file? And is my internet connection to fast?

Some more information:

OS: Win 7
Inet speed: between 1.7 Mb and 2.1 Mb (1700 Kbps/2100 Kbps)
Browser: Mozilla Firefox 3.6.x

Thanks in advance and kind regards

DC80

---

### Post by jerome1232 on 2010-04-22
Do you have a bit torrent client? Try torrenting it, torrent clients generally verify the data and such so you know your download was good.

[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

---

### Post by DC80 on 2010-04-22
Hi jerome1232

I'm sorry but i do not have bittorrent. I had some bad experience with it so i use newsgroups instead. Maybe ubuntu can change my mind. However, i still like newsgroups.

Thanks anyway

Kind regards

DC80

---

### Post by lovinglinux on 2010-04-22
> **DC80 said:**
> Hi jerome1232

I'm sorry but i do not have bittorrent. I had some bad experience with it so i use newsgroups instead. Maybe ubuntu can change my mind. However, i still like newsgroups.

Thanks anyway

Kind regards

DC80

I also prefer BitTorrent, which is perfectly safe and legal when downloading Linux distros. See [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

To test if your regular ISO download is fine, you should compare the [hash](https://help.ubuntu.com/community/UbuntuHashes) provided by Ubuntu with the one generated for the downloaded file. You can do that easily with [CheckIt](http://lovinglinux.megabyet.net/?page_id=662) extension for Firefox (I'm the developer btw). For more info on hashes see [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by RedRat on 2010-04-22
Unless the newsgroup is moderated, i would not use them as a source of the important OS, I am distrustful and cynical I guess. Why not download directly via the web pages? this is how I have gotten most all of my distro updates.

---

### Post by Hal1ow3en on 2010-04-22
I downloaded of the site and the iso file size is 690.8mb thats for 9.10 64mb

---

### Post by jerome1232 on 2010-04-22
Do as lovinglinux suggested, check the md5sum, if it matches with what ubuntu.com has on their site the download is fine.

That extension actually sounds very nifty, I'll have to try it myself.

---

### Post by DC80 on 2010-04-22
Hi,

I got it. However still having problems. I had downloaded the wrong version so i had to download again. This time it stops after 14 Mb (first attempt) and then 26 Mb (second attempt), finally i got it. 

Although i have what i need, it still make me wonder why this is happening. Not a good message to a first user (i'm not easely scared).

Anyway, thanks for the help and i have another problem so i'm gonna open a new topic. 

DC80

---

### Post by quadproc on 2010-04-22
> **DC80 said:**
> Hi,

I got it. However still having problems. I had downloaded the wrong version so i had to download again. This time it stops after 14 Mb (first attempt) and then 26 Mb (second attempt), finally i got it. 

Although i have what i need, it still make me wonder why this is happening. Not a good message to a first user (i'm not easely scared).

The Ubuntu distributions are designed to fit on a 700 MB CDROM so the distribution is usually just under 700 MB (e.g. 690.8 MB for the 64 bit version of 9.10 LiveCD).

Your downloading problems sound like your internet connection is noisy and/or unreliable.  I highly suggest, as others have mentioned, checking the md5sum of what you download.  Something might have corrupted some data even if the file size is correct; the md5sum will almost certainly find that problem.

Most internet access has provisions for retrying defective packets.  If damaged packets are occurring then the system will try again.  This can slow down the file transfer so a slow download is highly suspect.

quadproc

---

### Post by DC80 on 2010-04-23
Hi quadproc

My connection is very fast. I had ubuntu downloaded within 5 minutes. My guess is that my internet connection is unstable. But like i said earlier, i have ubuntu so there is no need to discuss this further. Unless someone need more information about this.

Thanks for your answer. 

DC80

---

### Post by coffeecat on 2010-04-23
> **DC80 said:**
> Not a good message to a first user

I'm curious. You had difficulty downloading a file using Windows 7. What message to new Ubuntu users is that? :wink:

Have fun! :)

---

