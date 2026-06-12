---
title: "rsync Ubuntu and Windows"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by rgotten on 2010-04-09
I use rsync to copy a  windows client (windows xp) folder into the ubuntu server every day using rsync and Cron. So for example Folder “test” on windows is mounted on ubuntu and from there thu rsync it copies into another folder,  at the present moment to do this I have to share on the windows computer the folder “test” with every body for this to happen…. i would like to know if there is a way to avoid sharing my windows folder with everybody and still do the backups thru rsync?

Thanks

---

### Post by The Cog on 2010-04-09
There is a windows rsync port called cwrsync. I guess that might do the trick for you. It can (I think) use either rsync or rsync-over-ssh protocol.

---

