---
title: "Weird Refresh Problem Ubuntu 9.10"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by kronosss on 2010-03-05
I am having a strange problem with a mounted windows drive. I have a windows drive set to mount automattically with an entry in the fstab file and everything seems to work fine. Basically what I am doing is using mutt to send an email with an image attached located in the windows directory to a few users. The attachment is updated twice a day and the email is set to be sent after the images have been updated.
 
Sometimes it works fine with no issues and sometimes the image that is sent is an older version. If I browse to the directory the image is located on a windows machine, the image is current with the correct creation date and time. If I browse to the mounted drive on Ubuntu I see the an older version of the file. It is as if the mounted drive is not refreshing. The weird thing is sometimes it works fine and I can go a couple of days without an incident then when it happens it can take a couple of days to refresh itself without me doing anything. During that time the image file is updated several times but still shows the old file on the mounted drive in Ubuntu but the updated file shows up fine from a windows box.
 
If I do a restart of Ubuntu it does update. A couple of things I thought about trying is scheduling a restart of Ubuntu after the files are created but before the email is sent or look into automating an unmount and mount of the drive so that it refreshes that way. I would prefer to find out where the issue is and correct to avoid setting up a process that shouldn't have to be that complicated. Does anyone have any ideas?
 
Thanks for the help

---

