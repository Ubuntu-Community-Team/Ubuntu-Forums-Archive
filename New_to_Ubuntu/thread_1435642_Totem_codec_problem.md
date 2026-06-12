---
title: "Totem codec problem"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by John Wolf416 on 2010-03-21
Having problems with Totem multimedia player. Default install does not include any codec. Help directed me to G Streamer website where I found and downloaded plug-in to my download directory which contains codec's. I can't copy, move,cut, paste to Totem sub directory plug ins. I need super human permission to do computer basics.

---

### Post by collinp on 2010-03-21
The popular GStreamer plugins can be found in the Ubuntu repositories.
Open a terminal and execute the following command:
```
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```

---

### Post by lidex on 2010-03-21
First thing you should do is install restricted extras. See this page for help:
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

