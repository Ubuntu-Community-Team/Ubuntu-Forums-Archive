---
title: "Flashing Tomato to an Asus router"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by Halsnalle on 2008-08-29
I just bought an Asus WL-500g Premium router, mainly because it is compatible with a range of open source firmware. And so I've decided to try Tomato, which seems to suit my demands. But the most helpful installation instructions I can find seem to presuppose you run Windows, and use either Asus restoration utility (Win-based) or something calle TFTP. 

But it out to be possible to do it from Ubuntu too, right? Since I'm rather new to Ubuntu, and also scared of all the warnings not to brick the router, I'd be glad for advice on how to flash an Asus router from Ubuntu.

---

### Post by Halsnalle on 2008-08-31
Realising that TFTP is available for Linux and Mac OS X too, I've made some progress, following [these]("http://wiki.openwrt.org/OpenWrtDocs/Hardware/Asus/WL500GP?highlight=(asus)") and [these]("http://www.dd-wrt.com/wiki/index.php/Installation#Asus_WL500G_Premium") instructions. Now, after putting the router in diag mode (it responds to pings), I tried TFTPing the firmware to the router, like this:

```
$ tftp 192.168.1.1
> mode binary
> put tomato.trx

```

But all I get is an error message that reads:

```
TFTP: tomato.trx: No such file or directory.
```

I've cd'd the directory where the file is located before starting the TFTP thing. What am I missing?

---

### Post by Jackie999 on 2008-08-31
I updated my tomato a little while back - mine was rotten :)
All I did was logged into the router (192.168.1.1 in browser).Once there I went into firmware update and pointed to the downloaded file from polarcloud and said okay, update.
Admittedly, I already had tomato loaded from a year ago, but doesn't the default firmware on your ASUS have an update feature.
Sorry if this is of no help ..I don't remember what I did originally

---

### Post by Halsnalle on 2008-08-31
Yes, the pre-installed Asus web interface has an firmware update feature, but AFAIK, it only accepts updates, not flashing another firmware like Tomato, OpenWRT or the like.

---

### Post by Jackie999 on 2008-08-31
I was reading up on the tomato/MLPPP firmware that I will be flashing once I've changed my provider and think I came across your answer :
```
[SIZE=+1]**_INSTRUCTIONS_**[/SIZE]

Please note that it is required that you reset your router to factory default settings
 (including NVRAM) when installing Tomato/MLPPP (even if upgrading from a previous 
release of Tomato/MLPPP). Your router will not connect to the Internet after installing
 Tomato/MLPPP unless you do so. It is still possible to manually configure
 Tomato/MLPPP correctly without resetting the NVRAM. To do so, you must do the following:

1) In Advanced->Misc change everything to Automatic, save
2) In Basic->Networking, set the retry delay to 5
3) In Basic->Networking, change the "Multilink PPP" dropdown back to the correct value, save.

```Ignore the part about the MLPPP, it's the modified tomato ..but the resetting of the NVRAM ...I did that first on my factory WRT54GL - then flashed tomato - worked like a charm.
Hope this helps.

---

### Post by Halsnalle on 2008-08-31
Thanks, but I think my problem occurs at an earlier stage. I think I'm doing something wrong in the terminal (I'm rater new to Ubuntu); the error message indicates that TFTP simply can't find the file to upload to the router.

I haven't yet used the router at all, except for trying to flash the firmware, so it ought to still have the factory default settings; thus, no need to reset them until Tomato is installed on the router.

---

### Post by Halsnalle on 2008-09-02
> **Halsnalle said:**
>  the error message indicates that TFTP simply can't find the file to upload to the router.

If I understand [this thread]("http://www.unix.com/unix-dummies-questions-answers/167-tftp-setup-2.html#post493") correctly, my problem might be that I have insufficient rw permissions.

---

