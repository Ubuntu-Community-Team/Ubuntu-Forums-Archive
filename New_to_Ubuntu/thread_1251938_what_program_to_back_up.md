---
title: "what program to back up"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by intense.ego on 2009-08-28
I need to back up my entire home partition. I don't want anything fancy - this is just a one-off thing and I want the entire directory copied. a command would do just fine as well

Thanks

---

### Post by NoaHall on 2009-08-28
cp /home/ #the location of where you want to copy to#

So, for me, it would be

cp /home/ /media/disk

---

### Post by mike555 on 2009-08-28
I use "Back in Time" ,  [http://backintime.le-web.org/](http://backintime.le-web.org/)

---

### Post by LewRockwell on 2009-08-28
learn clonezilla, it is OS independent so if you change or come across different systems you still know the product!

.

---

### Post by b0b138 on 2009-08-28
rsync -vurt --progress /home/username /path/to/destination    or
rsync -vurt --progress /home /path/to/destination  to backup to WHOLE home directory with multiple users

---

### Post by mapes12 on 2009-08-28
/home is owned by root so you would need sudo e.g. ```
sudo cp /home /*path to destination directory*
```in it's simplest format would copy /home to wherever. If you need compression or a syncing routine that would be used more than once e.g. regular backups then please post back.

---

### Post by cguy on 2009-08-28
[http://www.linux.org/lessons/interm/c316.html](http://www.linux.org/lessons/interm/c316.html)

Rewind a few pages and you'll get some details about the commands.

---

### Post by intense.ego on 2009-08-28
but would it matter if I was using teh computer at the same time?

---

### Post by mapes12 on 2009-08-28
> **intense.ego said:**
> but would it matter if I was using teh computer at the same time?As doing what? Wrapping up a tar file or just cp copying? Linux is the Queen of multi tasking so provided your CPU and RAM are up to it = no probs.

---

### Post by intense.ego on 2009-08-28
thanks. i was just wondering whether me accessing application data on my /home would be a problem. apparently not.

---

### Post by BDNiner on 2009-08-28
I use fwbackups. So far it has done everything that I needed it to. The project website is: [http://www.diffingo.com/oss/](http://www.diffingo.com/oss/). You will have to compile it from source though. There currently isn't a deb package and I haven't had time to try and create one.

---

### Post by jrox717 on 2009-08-28
When I was moving my /home directory to a new partition, [the guide I used]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")  said:
>  Since the &#8220;/home&#8221; directory will have hardlinks, softlinks, files and nested directories, a regular copy (cp) may not do the job completely. Therefore, we use something we learn from the Debian archiving guide: 
```

$cd /home/
$find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome/

```

It worked well for me.

---

