---
title: "A problem when i try to download ubuntu restricted extras."
date: 2011-04-14
forum: New to Ubuntu
---

### Post by abnordude on 2011-04-14
THis is what i get.

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse_0.10.16-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse_0.10.16-1_amd64.deb) Connection failed [IP: 91.189.88.45 80]

---

### Post by ubudog on 2011-04-14
Could you please post the output of:
```
sudo apt-get update
```

---

### Post by abnordude on 2011-04-14
> **ubudog said:**
> Could you please post the output of:
```
sudo apt-get update
```


Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                   
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en   
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release.gpg          
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                   
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_IN
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages            
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse amd64 Packages
Reading package lists... Done

---

### Post by TeoBigusGeekus on 2011-04-14
Perhaps your server was down when you tried.
Select another server from Administration>System>Software sources.

---

### Post by kn0w-b1nary on 2011-04-14
Why don't you try downloading it manually, then installing the .deb?

---

### Post by abnordude on 2011-04-14
> **kn0w-b1nary said:**
> Why don't you try downloading it manually, then installing the .deb?


Could you explain how to do that?

---

### Post by Enigmapond on 2011-04-14
I just clicked on that error you received and the deb downloaded just fine. Perhaps you need a source archive closer to you. Navigate to Administration/Software sources and right on the main tab you see "Download From". Hit the pull-down menu and select "Other" and have it search for the best download point for you.

Hope this helps!

Cheers!

---

### Post by abnordude on 2011-04-29
> **Enigmapond said:**
> I just clicked on that error you received and the deb downloaded just fine. Perhaps you need a source archive closer to you. Navigate to Administration/Software sources and right on the main tab you see "Download From". Hit the pull-down menu and select "Other" and have it search for the best download point for you.

Hope this helps!

Cheers!

Thakns, it worked.
I got it.
Thanks to all of you too.

---

