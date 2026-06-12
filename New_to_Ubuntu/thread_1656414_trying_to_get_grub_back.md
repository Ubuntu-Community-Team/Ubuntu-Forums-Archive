---
title: "trying to get grub back"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by paul88 on 2010-12-30
I have just installed 10.10 beside window 7 and have lost grub even tho i installed ubuntu last.

I have seen you can get grub back using a live cd but it is not working for me.

I am using the live cd as ubuntu@ubuntu
I had to install grub on the live cd using sudo apt-get grub

inside grub i am getting the following:
```

grub> find /boot/grub/stage1

Error 15: File not found

grub> 



```

Can anyone help?

Thanks

---

### Post by lindsay7 on 2010-12-30
the command you ran is for the old grub setup.

Please type this in the terminal and post the results.

sudo fdisk -ls

that is the lower case letter L and the lower case letter S

---

### Post by paul88 on 2010-12-30
Thanks for your reply

I managed to find a video on youtube which showed me what to do.

thanks

---

### Post by decoherence on 2011-01-01
> **paul88 said:**
> Thanks for your reply

I managed to find a video on youtube which showed me what to do.

thanks

Hi Paul,

could you please post a link?

thanks,

sean

---

