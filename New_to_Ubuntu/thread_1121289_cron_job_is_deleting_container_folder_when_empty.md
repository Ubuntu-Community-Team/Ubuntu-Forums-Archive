---
title: "cron job is deleting container folder when empty"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by mishkin on 2009-04-09
find /home/mishkin/torrent/downloads/ -mmin +1500 -exec rm -rf {} \;         

is deleting the folder .../downloads/ when it has no files left in it

how do I avoid this? why is it doing that?

If the folder gets deleted rtorrent can't create the file where it is sopost to and my torrents get stuck not starting :(

---

### Post by lovinglinux on 2009-04-10
The problem is the ***rm -rf***, which deletes the folder recursively if no file is found. Use ***rm -f*** instead.

---

### Post by mishkin on 2009-04-10
I thought the r made it delete everything within the folders??

Because I think before when I ran it without rf it did something weird like delete only the folders but not the files inside them

for a temp fix until your reply i put in a txt file called "no delete" and put -type d in the search cmd so it can't delete that file (only folders), thus it is never empty and shouldn't delete itself...

downside is any packs without folders won't be able to be automatically removed

---

