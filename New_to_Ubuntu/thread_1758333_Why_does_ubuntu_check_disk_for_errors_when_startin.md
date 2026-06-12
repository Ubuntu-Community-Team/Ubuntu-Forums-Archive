---
title: "Why does ubuntu check disk for errors when starting up?"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by amanchesterman on 2011-05-14
I am running Ubuntu 10.10 on a Toshiba laptop: I have been using it for a couple of months now and I am very satisfied with it. It was a clean install (not dual boot) with separate partitions for the OS and the /home folder.

Occasionally, when I start the machine and after entering my password, I get a message saying that Ubuntu needs to check 'disk 1 of 1'. The percentage checked then climbs rapidly to 100% and the machine starts after a short while. Thereafter it operates normally.

This isn't a problem for me but I am curious as to what triggers this behaviour. Is it a standard part of Ubuntu to check the disk from time to time? It doesn't seem to happen at regular intervals. Is it a symptom that something might be wrong, and should I be concerned?

Thanks
John

---

### Post by el_koraco on 2011-05-14
It's a feature of the ext4 filesystem. The disk gets checked for errors on every 30th boot.

---

### Post by shashanksingh on 2011-05-14
I generally happens due to some file system maintainence because of some disrepancies.
Like if you add or delete certain files but some files remained unclosed,or if you do not shut down the system properly.



Don't know the exact technical details though....

---

### Post by amanchesterman on 2011-05-14
Thanks for your quick replies. The partitions are in ext4 format, so I guess that's the explanation.

Thanks
John

---

### Post by matt_symes on 2011-05-14
Hi

> **el_koraco said:**
> The disk gets checked for errors on every 30th boot.

This explains the reasons quite well. You can tune the frequency or disable it using tune2fs command from the command line. 

You can also disable it completely by editing /etc/fstab. It is a good idea to allow it to run though.

Kind regards

---

### Post by Rubi1200 on 2011-05-14
Although you can disable this feature, I would advise against it. The file-system checks help ensure the stability of your system.

If you would like to know the current and maximum mount count and the next check date, you can use this command in the terminal:

```
sudo tune2fs -l /dev/sdXY | grep -i -e "mount count" -e "check"
```

Replace XY with the actual Ubuntu partition e.g. sda1

---

### Post by synapsys on 2011-05-14
Here's a site with some info on how to configure this:

[http://ubuntu4beginners.blogspot.com/2011/02/tune-filesystem-check-fsck-on-ext.html](http://ubuntu4beginners.blogspot.com/2011/02/tune-filesystem-check-fsck-on-ext.html)

---

### Post by matt_symes on 2011-05-14
Hi

@OP

> Although you can disable this feature, I would advise against it.In addendum to the above comment by Rubi, i have actually increased the frequency of fsck checking on my drive on my laptop because there are times when i just cannot find the power lead quickly enough. etc.

Kind regards

---

### Post by wildmanne39 on 2011-05-14
> **amanchesterman said:**
> I am running Ubuntu 10.10 on a Toshiba laptop: I have been using it for a couple of months now and I am very satisfied with it. It was a clean install (not dual boot) with separate partitions for the OS and the /home folder.

Occasionally, when I start the machine and after entering my password, I get a message saying that Ubuntu needs to check 'disk 1 of 1'. The percentage checked then climbs rapidly to 100% and the machine starts after a short while. Thereafter it operates normally.

This isn't a problem for me but I am curious as to what triggers this behaviour. Is it a standard part of Ubuntu to check the disk from time to time? It doesn't seem to happen at regular intervals. Is it a symptom that something might be wrong, and should I be concerned?

Thanks
John
Hi, would you go to the top of the page and click on forum tools and mark this thread solved, if it is to your satisfaction.Thanks :D

---

### Post by amanchesterman on 2011-05-15
Thanks to you all for your helpful and informative replies. As always on this forum, I have learned a lot. The automatic check seems a good idea to me and I have left the settings as they are.

Good wishes

John

(Thread now solved)

---

### Post by Rubi1200 on 2011-05-15
> **amanchesterman said:**
> Thanks to you all for your helpful and informative replies. As always on this forum, I have learned a lot. The automatic check seems a good idea to me and I have left the settings as they are.

Good wishes

John

(Thread now solved)

I think that is the most sensible thing to do. Unless there is some pressing need to do so, most default settings should be left as they are.

Enjoy :-)

---

