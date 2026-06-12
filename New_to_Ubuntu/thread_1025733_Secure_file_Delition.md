---
title: "Secure file Delition"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Red Rebel on 2008-12-30
I am looking for a well known utility for ubuntu, command line based, or gui, that will allow me to permanently destroy(overwrite) files on my computer. Also, I am looking for an utility that will destroy all the free space on my drive. Is there a built in utility in ubuntu that will allow me to do this? I searched the forums, but I have not been able to find anyone that really knows much on the subject. Any help with this would be greatly appreciated..

---

### Post by wolfen69 on 2008-12-30
secure delete and wipe are 2 i know of. they are in synaptic.

---

### Post by Sarmacid on 2008-12-30
You can destroy files with the shred utility```
shred -zu file
```

But it can't delete folders.

---

### Post by jerome1232 on 2008-12-30
You can always use dd to wipe out the free space.

```
### to write random junk over the free space
sudo dd if=/dev/random of=/media/drive/junk.img bs=10M conv=notrunc
### or to write zeros
sudo dd if=/dev/zero of=/media/drive/junk.img bs=10M conv=notrunc
```

Then just  delete the resulting image file.

---

### Post by pdtpatrick on 2008-12-30
send it to /dev/null -- the linux blackhole :)

---

### Post by benny bronx on 2008-12-30
You can add the shred command to the context menu using this:

[http://gnome-look.org/content/show.php/shred_file?content=66603]("http://gnome-look.org/content/show.php/shred_file?content=66603")

Also, if you search this forum for "bcwipe", another member posted a good how-to on installing it in Ubuntu. Secure-delete, as mentioned above, is in the repo, but I personally found bcwipe to be better. It is of course a matter of opinion, and bcwipe is not open source.

---

