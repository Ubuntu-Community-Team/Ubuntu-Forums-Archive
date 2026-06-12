---
title: "extract libflashplayer.so"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by Throbbing Gristle on 2010-01-21
I just don't Know how to extract this I need to apparently get a folder out of this? extract libflashplayer.so? Archive not supported?

---

### Post by marshmallow1304 on 2010-01-21
I'm guessing you followed instructions that told you to extract the archive which contained libflashplayer.so, not extract libflashplayer.so itself.  Once you've got libflashplayer.so, just move it to ~/.mozilla/plugins

---

### Post by CJ Master on 2010-01-21
You should really give us more context on what you're actually trying to do... I'm assuming that you want to install flash player? You should click on Programs -> Ubuntu software center and search for it/install it. It's much easier.

---

### Post by cariboo on 2010-01-21
If you are using a default installation of Ubuntu, all you have to do is double click the file you downloaded and pick a place to store the extracted file, just like in Windows.

---

### Post by Throbbing Gristle on 2010-01-21
> **cariboo907 said:**
> If you are using a default installation of Ubuntu, all you have to do is double click the file you downloaded and pick a place to store the extracted file, just like in Windows.


I have been a sworn Ubuntu guy and I still don't know what I am doing! I am using a SR1750NX COPAQ PRESARIO AMD pc3200 updated from 9.04 Hulu was always choppy. The motherboard thinks acts like a intel? Had to do grub updates put nomodeset etc to the letter to get it to boot up. Everything is peachy but flash. I am trying to get it directly from Adobe. 

Where how if you will is this place to store? Thanks

---

### Post by Throbbing Gristle on 2010-01-21
Using this command does not work    	 	 	 	 	 	  gksu nautilus /usr/lib/flashplugin-installer

---

### Post by Throbbing Gristle on 2010-01-21
All I get is 
** (nautilus:2276): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2276): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> inode/directory
--> root
--> l2049
Shutting down nautilus-gdu extension

(nautilus:2276): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

(nautilus:2276): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 3 elements at quit time

---

