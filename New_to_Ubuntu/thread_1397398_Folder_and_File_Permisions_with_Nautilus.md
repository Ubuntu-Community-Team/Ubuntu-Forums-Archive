---
title: "Folder and File Permisions with Nautilus"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by santhony on 2010-02-03
This should be an easy one for many out there...

Using Nautilus.. How come I cannot change a folder and it's entire contents??

I cannot do this from either my home directory or even a directory under root.. Even as the original owner of a folder and it's contents, I cannot even give away my permissions to another "Owner".

I've tried this as root and sudo..

I can change the permissions if I do each folder and file individually, but the "Apply Permissions to Enclosed Files" appears to do NOTHING...

I have a huge 2 TB drive that I need to hand off permissions to mythtv and certainly cannot do this on a file by file basis... 

I know I can do this with chown from command prompt.. But why can't I do this on any of my 5 Karmic stations using Nautilus....  Ever!!

This is like the 8th wonder of the world to me....

Anyone??

---

### Post by Sealbhach on 2010-02-03
Hi,

From the command line, you can use the -R option to make your changes apply to all the contents of a folder. e.g.

```
# chmod -R 755 directory-name/
```

See [here]("http://www.cyberciti.biz/faq/how-linux-file-permissions-work/") for more info.

But you probably already know all this. The Nautilus method works for me, so I don't know why it doesn't work for you. Maybe it's something to do with Group Policy or something.

.

---

