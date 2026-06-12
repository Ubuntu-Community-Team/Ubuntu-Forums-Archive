---
title: "Flash player not found in new install of 10.10"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by bob brazie on 2010-10-10
When trying to view a video on MSNBC the Flash player will not open and I am told I need to install a new version.

When I type I type "sudo apt-get install flashplugin-nonfree" in a terminal I am told I have the latest version installed.

Fresh install of Ubuntu 10.10 and Firefox 3.6.10.

Please help me view flash content.

Thanks in advance. Bob.

---

### Post by jonathan22 on 2010-10-10
> **bob brazie said:**
> When trying to view a video on MSNBC the Flash player will not open and I am told I need to install a new version.

When I type I type "sudo apt-get install flashplugin-nonfree" in a terminal I am told I have the latest version installed.

Fresh install of Ubuntu 10.10 and Firefox 3.6.10.

Please help me view flash content.

Thanks in advance. Bob.

Try this thread.
[http://ubuntuforums.org/showthread.php?t=1358591&highlight=flash+64](http://ubuntuforums.org/showthread.php?t=1358591&highlight=flash+64)

---

### Post by crichard on 2010-10-11
uninstall flashplugin-nonfree & install flashplugin-installer or install the restricted extras which includes mp3, flash & java, etc., 

**sudo apt-get install ubuntu-restricted-extras**

---

### Post by 23dornot23d on 2010-10-11
Restart Firefox afterwards  ..... it sometimes helps .... to get it to be recognized once added .....

---

### Post by bob brazie on 2010-10-11
Thanks, but that seems to be for the 64 bit and not the 32. It also says it may not work with 10.10?

---

### Post by bob brazie on 2010-10-11
Re: Flash player not found in new install of 10.10
uninstall flashplugin-nonfree & install flashplugin-installer or install the restricted extras which includes mp3, flash & java, etc.,

sudo apt-get install ubuntu-restricted-extras
__________________

Thanks, what is the command to uninstall the flashplugin-nonfree and what is the command to install the installer?

Thanks in advance. Bob.

---

### Post by crichard on 2010-10-11
__________________
> **bob brazie said:**
> 
Thanks, what is the command to uninstall the flashplugin-nonfree and what is the command to install the installer?

Thanks in advance. Bob.

To uninstall flashplugin-nonfree ```
sudo apt-get remove flashplugin-nonfree
```

To install flash,  ```
sudo apt-get install flashplugin-installer
``` 

To install restricted extras, (flash,java,mp3 & etc.,)

```
sudo apt-get install ubuntu-restricted-extras
```

I highly recommend you to install the restricted extras,  it includes everything.   FYI, I'm also using the 64 bit ubuntu 10.10

---

### Post by bob brazie on 2010-10-11
That did the trick! Thanks!!!!!!!!!

Bob.

---

### Post by cam3roon on 2010-10-15
worked for me also :D thanks

---

