---
title: "questions about .old files"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by jfbooth on 2010-05-10
Just upgraded from 9.10 to 10.04 on 5/10/10.

Opened Thunar File Manager, .. I am pretty sure I am looking in the root directory.  Noticed vmlinuz.old - 3.7MB -link to backup file - 3/24/2010

I have a rather small HD and have to be space conscious.  Got to wondering about '.old' files and if I could/should delete them.

Opened TERMINAL and did the following:

[B]jb@jb-desktop:~$ locate *.old
/initrd.img.old
/vmlinuz.old
/etc/motd.tail.old
/etc/sgml/catalog.old
/etc/sgml/docbook-xml.cat.old
/etc/sgml/sgml-data.cat.old
/etc/xml/catalog.old
/etc/xml/docbook-xml.xml.old
/etc/xml/rarian-compat.xml.old
/etc/xml/sgml-data.xml.old
/etc/xml/xml-core.xml.old
/home/jb/.xsession-errors.old
/usr/share/info/dir.old
/var/lib/belocs/hashfile.old
/var/log/Xorg.0.log.old
jb@jb-desktop:~$[/B]

So the questions are: can/should I delete any of these?  If I delete one that has a LINK to it, will the LINK delete automatically when I delete the file?

thank you in advance.

---

### Post by pricetech on 2010-05-10
".old" files are usually created automatically when new versions of those files are introduced by whatever means.  Some people use the .old extension when they make a backup copy of a file as well.

I don't think you'd have any problem if you deleted them all.  You will have to delete the links to them separately if I recall correctly.  I wonder just how much space you'll gain though.  I noticed some log files which probably aren't that big, so I think I'd look at file sizes and see if it's worth the trouble or not first.

---

### Post by jfbooth on 2010-05-10
> **pricetech said:**
> I don't think you'd have any problem if you deleted them all.

thank you VERY much for the reply.  I would like to respectfully get a couple more opinions if possible and will keep the 'links' in mind.  Thank you again for your input and time.

---

### Post by pricetech on 2010-05-10
No problem.  Here's a thought if you think you might need one or more of them later.  Copy them to a CD or an external drive of some kind.  That way you can restore them in the unlikely event they are needed.

---

### Post by jfbooth on 2010-05-10
Thank you both.  I feel OK with moving them to a storage device.  I appreciate both inputs.  thank you again.

---

