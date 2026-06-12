---
title: "Download - The most basic issue!"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Grant Sixtus on 2009-06-15
Hi, 

I have a problem in that I have now tried to download the 700MB Ubuntu desktop solution and both times have had the download interrupted due to my 3G connectivity falling over.

The question is, does the entire download need to start all over again or will it resume from the point where the connection dropped? I have been using Google Chrome as my browser and the download window 'tells' me that the download won't resume. Any advice for an absolute Ubuntu beginner please?

Thanks
Grant

---

### Post by Cheesemill on 2009-06-15
I'm not sure if Chrome can resume downloads, your best bet is to download the torrent as this can resume as well as perform hash-checking on the download.

---

### Post by Dexter_Greycells on 2009-06-15
I am a relative newbie myself and I believe you would need to start all over again with the download. (If I am wrong, please feel free to correct me.)

A suggestion would be to use another mirror from where you can download your copy of Ubuntu. Torrent links are even better for connectivity issues like yours.

Best Of Luck!

---

### Post by Grant Sixtus on 2009-06-15
Sorry, going to be a moron here.... where do I find the torrent locations with the hash checking capability?

---

### Post by Celauran on 2009-06-15
[Here](http://www.ubuntu.com/getubuntu/downloadmirrors#bt).

---

### Post by ricardofilipemoreira on 2009-06-15
you can always use wget to download it.
in console type
wget -c [http://(url](http://(url) of the cd image)

if the download fails, re-run the command and it will resume from where it stopped.

---

### Post by 3rdalbum on 2009-06-15
All torrents will check the integrity of the file; it's part of the underlying system. And all torrents can resume downloads of the file - all torrents are actually just a collection of ~256 kilobyte sections that are independently hashed. If your connection gives out while downloading Section #501, that's okay; the torrent will resume from the start of Section #501. And if you get a faulty bit of data while downloading Section #440, the torrent client will just download #440 again immediately.

---

### Post by Grant Sixtus on 2009-06-15
Thanks team, sorted! Appreciate your help.

---

