---
title: "Mediatomb + PS3 + Linux problem"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by Kris2456 on 2009-03-05
Ok so i am running a small home server, which i use as a media server for the PS3. I have the latest version of ubuntu installed on it, along with mediatomb. This system works fairly well, however there are a few annoying problems.

1. When media is copied over to the "public" folder it almost always has messed up permissions (IE. 700) meaning it won't play on the PS3. I can of course chmod it to 755 or 777 however my housemates (who are used to windows) are far from amused.

2. BY FAR the most annoying problem is one that i cannot for the life of me explain, although i think it may have something to do with Mediatomb. Namely, when a video is copied over to the server it will sometimes not play on the PS3 OR it will cut off the last 5 minutes. Renaming the file however, seems to fix this. As you can imagine, it's very annoying.

If anyone knows how i can combat these issues in an automated way, i would be very greatful.

---

### Post by skymera on 2009-03-05
Hello, yes that does seem very annoying.

Does this help?
[http://www.debuntu.org/how-to-copy-files-over-network-and-preserve-file-permissions-and-informations-with-ssh-and-rsync](http://www.debuntu.org/how-to-copy-files-over-network-and-preserve-file-permissions-and-informations-with-ssh-and-rsync)

I can't view the link as it's blocked on my college network. 

Perhaps give this a read:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions) (Great site to start)

---

