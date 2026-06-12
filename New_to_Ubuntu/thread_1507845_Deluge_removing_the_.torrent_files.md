---
title: "Deluge removing the .torrent files"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by donescamillo on 2010-06-12
Hi,

I would be grateful if someone with more knowledge and insight in Deluge tells me why when I set Deluge to automatically add .torrent files from a certain folder it also removes them from said folder to one of its folders?

thank you 
donescamillo

---

### Post by wilee-nilee on 2010-06-12
> **donescamillo said:**
> Hi,

I would be grateful if someone with more knowledge and insight in Deluge tells me why when I set Deluge to automatically add .torrent files from a certain folder it also removes them from said folder to one of its folders?

thank you 
donescamillo

Change the load deluge from setting to another folder and copy and paste to it after downloading the link. You can also go to preferences I think and set it to save that link where you want, but I use the first method if I want to save the link.

---

### Post by lovinglinux on 2010-06-12
> **wilee-nilee said:**
> Change the load deluge from setting to another folder and copy and paste to it after downloading the link. You can also go to preferences I think and set it to save that link where you want, but I use the first method if I want to save the link.

If it doesn't do that, it would try to add all torrents again every time a new file is added to the folder. I imagine if you had hundreds of torrents, this could impact performance and Deluge would ask if you want to merge the trackers for each repeated torrent. Anyway, if you want to keep the .torrent files, you can set Deluge to make a copy of the .torrents to another folder. I don't remember where is this option, since I haven't used it for a while, but it is there.

---

