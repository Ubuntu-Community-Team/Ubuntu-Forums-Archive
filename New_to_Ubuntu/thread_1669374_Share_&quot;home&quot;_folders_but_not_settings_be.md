---
title: "Share &quot;home&quot; folders but not settings between users?"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by mechanizedmedic on 2011-01-17
my wife doesn't like the way i set up my desktop so i made a user for her. the issue now is making it brainless for her to access our files that are in MY home folder.

currently i have a 1TB HDD mounted as my /home/*myuser*, her home is on an SSD with the rest of the file system. i've already changed the permissions so that she can access my files. is there a way of merging our home folders while keeping separate settings?

---

### Post by Vaphell on 2011-01-17
use symbolic links for folders/files of choice
eg
```
cd /home/wife/
ln -s /home/me/Videos
ln -s /home/me/Music
```
you need to create 1 for each item to be shared, you can't share whole home and not include your configuration

you can try to do this for all non-hidden stuff at once
```
ln -s /home/me/* /home/wife
``` but be warned, any new item created located in /home/me or home/wife will not be shared by default - by default it will work only in the shared subdirectories of /home/me

---

### Post by mick222 on 2011-01-17
Another possible way to do this would be to use a data partition and move all the files to be shared to that then you could both read and write while you can still use your own home for data that your wife doesn't need or want.

   I know my wife hates some of my music and doesn't want work related documents on her computer.

---

### Post by JKyleOKC on 2011-01-17
You may also need to add your wife to YOUR group, which probably has the same name as your login name, and use chmod to give all the files in the shared directories rw permissions for group members. They probably already do have read-only permission for the group members, so if that's okay you won't need to chmod them.

---

### Post by mechanizedmedic on 2011-01-17
thanks for the great suggestions! ...i replaced some of her folders with links to mine. since she already had permissions it works like a charm.

for other Kubuntu noobs like me: to make a folder/file link in dolphin Right Click -> New -> Basic link to file or directory  ...it's kind of like mounting a file or folder into another directory. really useful for config or log files that you use a lot.

does anyone have a link to where i could learn more about user/group/login configuration? i've never learned their functions and uses.

---

### Post by endotherm on 2011-01-17
I have one other suggestion that may help you manage the permissions on new files a little easier. it involves setting the GID on the shared folder, so that all files/folders created within the shared folder will be owned by the same group that owns the share.

if you and your wife are added to the group "Users", you can chown -r your shared folders to <youruser>:Users (don;t do this to your whole home however). that way, you and your wife, both being of group users, will have access to the dir. Since GID is set on the folder, all new items will be owned by <creator>:Users. 

that way, you and your wife may change the rights you provide to eachothers files on a case by case basis, by configuring the group permission. you could make a file private, readonly, or readwrite. only the owner user may change permissions, the owner group may not.

you can also use the "Sticky bit", to prevent any user other than the owner from deleting a file. that would allow both of you to create files within the folder (have write priv on the files by default) but not be able to delete or rename each others files. the flaw here is that if you can write to a file, you can write over it with a 0KB file. 

here is some info about SetGid and Sticky. The documents I used to use for this were hosted at sun.com and have disappered after the oracle buyout, but you should be able to find lots of info on line.

[http://linuxmall.blogspot.com/2009/08/how-to-setuid-setgid-and-sticky-bit.html](http://linuxmall.blogspot.com/2009/08/how-to-setuid-setgid-and-sticky-bit.html)

---

### Post by mechanizedmedic on 2011-02-18
@endotherm i went back in just now and set the GID like you suggested. great tip, THANKS!

---

