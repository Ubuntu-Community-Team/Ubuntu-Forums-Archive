---
title: "Unable to automount CIFS share in fstab, wifi network not connected"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by elev on 2007-09-15
This is the entry in my fstab
```
//192.168.2.2/shared_media /home/jason/shared_media cifs defaults,rw,uid=1000,username=jason,password=jason     0       0
```

While booting it hangs when trying to mount this (because the wifi network is not connected) for about 20 seconds until it times out and continues booting.

I don't connect to the network until after I've logged in.  I use an applet call "Wireless Connection Manager" to connect to my network once booting is completed.

Is there a way I can create a script I can just double click once I boot to mount the network drive? 
Or, even better, is there a way I can get the mounting process to be continually checking the status of that network drive in the background and mount it once my network is up?

Thanks for the help

---

### Post by bthessel on 2007-10-24
don't use fstab, use autofs. That is what I do and it works great. I followed this

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

and

[http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs](http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs)

---

