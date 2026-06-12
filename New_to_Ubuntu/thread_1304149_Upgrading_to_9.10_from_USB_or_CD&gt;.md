---
title: "Upgrading to 9.10 from USB or CD&gt;"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by mXe on 2009-10-29
As I said in another one of my posts, one of my computers is currently in disrepair. I was considering just scrapping everything I have, saving a package list, then reinstalling karmic, but I am now curious if it would be possible to just download an image or such and just upgrade from that, to spare me the time of having to reinstall, well, everything. 
Any such luck?

---

### Post by dominiquec on 2009-10-29
You can upgrade using the Alternate Install CD.  The procedure is in the Ubuntu help site somewhere, but you can also look through my own steps: [http://ubuntuliving.blogspot.com/2009/04/upgrading-from-810-to-904.html](http://ubuntuliving.blogspot.com/2009/04/upgrading-from-810-to-904.html)

---

### Post by wilee-nilee on 2009-10-29
If your going to upgrade then I assume you will back up your stuff. So a clean install is the general opinion of installing Karmic, basically due to the ext 3 to ext 4 and grub2. You may be able to do this with the alternative disc but I doubt it. Now you can update the extension and grub if you want, but for me it is a ease of travel issue, I didn't really want to try and update the extension I was already using grub2 in Jaunty. Save yourself time and possible loss of your important and back it up and do a fresh install. I have all my stuff off my computers anyway so it was a easy install.

---

### Post by mXe on 2009-10-29
> **wilee-nilee said:**
> If your going to upgrade then I assume you will back up your stuff. So a clean install is the general opinion of installing Karmic, basically due to the ext 3 to ext 4 and grub2. You may be able to do this with the alternative disc but I doubt it. Now you can update the extension and grub if you want, but for me it is a ease of travel issue, I didn't really want to try and update the extension I was already using grub2 in Jaunty. Save yourself time and possible loss of your important and back it up and do a fresh install. I have all my stuff off my computers anyway so it was a easy install.
 
I would love to, but I have almost my entire hard drive filled with data, and it would be hard to back that all up.

---

### Post by wilee-nilee on 2009-10-29
> **mXe said:**
> I would love to, but I have almost my entire hard drive filled with data, and it would be hard to back that all up.

 Sounds like you might want to wait to upgrade unless you have that stuff on a separate partition, if your upgrade goes south which is unlikely, but it does happen you could lose everything. You can buy a external terabyte size HD for less than 100$, it may be the best investment you would make. I don't know if you have a desktop that has a port for a internal HD, that is another option.

---

### Post by mapes12 on 2009-10-29
You could create and move all your data to a separate /home partition: [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

then do a fresh install using the manual partitioner option so that only /root is formatted but telling the installer where /home is located but DON'T format it. I've done this many times without a hitch.

---

