---
title: "DLed new update. How do I remove old versions?"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by EddieNYC on 2010-07-04
Hi All,

Been running ubuntu for about 2-3 months now. Just downloaded the latest kernel update. (2.3.23?)

My boot menu now has 3 Ubuntu versions to choose from (aside from Win7 as well). 

How do I remove the 2 "older" versions from the menu ?

I'm a newbie to linux so a nice step by step would be appreciated.

Thanks!

---

### Post by mike555 on 2010-07-04
Write down which one it is ,then open package manager and click on the "status" button ,then click on " installed (local or obsolete), then uncheck the old ones , be careful not to uncheck the ones your using or other stuff....

---

### Post by -humanaut- on 2010-07-04
It's not necessary to delete the other kernel infact it's best to keep a couple around just in case one breaks compatibility with your system I always keep at minimum 3 kernel versions.

---

### Post by Zintha on 2010-07-05
> **-humanaut- said:**
> It's not necessary to delete the other kernel infact it's best to keep a couple around just in case one breaks compatibility with your system I always keep at minimum 3 kernel versions.
Then OP will need to know how to edit the grub menu :P
But I do agree with this. Searching the forums will find several posts and topics and whatnot about editing the grub menu (which is the menu you see when you boot up, the menu you're talking about)

---

### Post by 3rdalbum on 2010-07-05
> **Zintha said:**
> Then OP will need to know how to edit the grub menu :P
But I do agree with this. Searching the forums will find several posts and topics and whatnot about editing the grub menu (which is the menu you see when you boot up, the menu you're talking about)

Not really; I thought the kernel removal triggered a rebuild of the GRUB menu. If it doesn't, then just:

```
sudo update-grub
```

should do the trick.

---

### Post by EddieNYC on 2010-07-06
Sorry guys, I am indeed referring to the GRUB menu, The version i updated to is 2.6.23.

So what is the final verdict on this? remove old versions or keep?

I dont mind keeping at least 1 if needed.

thnx again

---

### Post by EddieNYC on 2010-07-06
> **mike555 said:**
> Write down which one it is ,then open package manager and click on the "status" button ,then click on " installed (local or obsolete), then uncheck the old ones , be careful not to uncheck the ones your using or other stuff....

Just checked via the steps mentioned above (thanks Mike!) and the only 2 things I have listed under Status>Installed (local or obsolete) are: LImewire (I know..crappy but sometimes I get better luck looking for media than using torrents), and Picasa.

---

### Post by EddieNYC on 2010-07-06
This is what I have installed at the moment. Looking to get rid of the older ones:

eddie@eddie-laptop:~$ dpkg -l | grep linux-image
ii  linux-image-2.6.32-21-generic             2.6.32-21.32                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-22-generic             2.6.32-22.36                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-23-generic             2.6.32-23.37                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-generic                       2.6.32.23.24                                    Generic Linux kernel image

---

### Post by mike555 on 2010-07-07
You could install "Ubuntu-tweak" from; [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)   it will let you get rid of them easy , plus it does a lot of other stuff...

---

### Post by oldsoundguy on 2010-07-07
> **mike555 said:**
> you could install "ubuntu-tweak" from; [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)   it will let you get rid of them easy , plus it does a lot of other stuff...

+ 1

---

### Post by Big Nate on 2010-07-07
I need to remember to come back to this when I get home.  Great info guys.


I hate haveing deal with all those extra items on the grub menu.

---

