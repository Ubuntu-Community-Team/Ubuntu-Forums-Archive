---
title: "Which image backup routine would be faster?"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by HarrisonNapper on 2009-10-14
I'm trying to figure out which of these two would be faster (I'm going to script the process, so it won't matter too terribly much, but it's always nice to be efficient):

Copy home directory, make it in to an iso, move to internal storage partition, overwriting the previous iso

or

Unpack existing backup iso, rsync with home directory, make new backup into an iso, replace old iso

Any ideas? Also, any suggestions for backing up are appreciated. Previously, I was just keeping a raw backup in the IS partition, but my home folder is bigger than the partition now >.<

---

### Post by mharrison on 2009-10-14
Can I ask why you want it in an ISO?  Wouldn't you get better compression from creating a TAR file of your /home/user on the internal partition and then just overwriting it each time the backup is supposed to run?

---

### Post by HarrisonNapper on 2009-10-14
Well, I have always been under the impression that image files were slightly less susceptible to corruption than other forms of compression. Can I run a checksum on a tar (I assume so)? Also, one of the things I was hoping to do was only have to compress the changes instead of the entire directory every time. I'm not really jonesing to copy/paste/compress 25GB of stuff every day. That's why I loved rsync is it will only make the changes that need to be made without being repetitive.

And I would never be repetitive. Never.

---

### Post by Paqman on 2009-10-14
After the first run rync is always going to be quicker than copying data, but all your iso packing and unpacking introduces complexity, so I wouldn't like to say for sure how much time you'd save. The best way to find out would be time a relatively small backup and see.

I'd just use one of the regular compression types myself. I've not heard anything about iso's being particularly desirable for backups.

---

