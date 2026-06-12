---
title: "Which download for Flash"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by Churchwarden on 2011-05-04
I am using Firefox 4 in Ubuntu v.11.04.  The ohases of the moon tool on my iGoogle page needs flash.  I have click through and find that I need to manually install it.

When I come to the download dialogue it asks me to select which version to download ans gives me the following options:

1.  YUM for Linux
2.  .tar.gx for Linux
3.  .rpm for Linux
4. .deb for Ubuntu 8.04+
5.  APT for Ubuntu 9.04+

Which one should I go for?

Nick

---

### Post by collisionystm on 2011-05-04
> **Churchwarden said:**
> I am using Firefox 4 in Ubuntu v.11.04.  The ohases of the moon tool on my iGoogle page needs flash.  I have click through and find that I need to manually install it.

When I come to the download dialogue it asks me to select which version to download ans gives me the following options:

1.  YUM for Linux
2.  .tar.gx for Linux
3.  .rpm for Linux
4. .deb for Ubuntu 8.04+
5.  APT for Ubuntu 9.04+

Which one should I go for?

Nick


are you using 64 bit ubuntu?

---

### Post by pqwoerituytrueiwoq on 2011-05-04
if you are using 32 bit use apt
if 64bit go here [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)
extract to ~/.mozilla/Plugins
you will need to make the plugins folder

edit 
the command [FONT=Courier New]uname -m[/FONT] will tell you if your are using 64bit or 32 bit

x86_64 is 64bit if it is not that it is 32 bit

---

### Post by collisionystm on 2011-05-04
You need the .tar.gz

If its 64 bit you need it from here

[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

Download the file you need, open it with archive manager.

Open the directory until you find the libflash.so file

extract it to your Desktop.

Now open terminal

```
cd Desktop
```

```
sudo bash
```

```
cp libflash.so /usr/lib/firefox-addons/plugins/
```

```
exit
```

run firefox, you now have flash

---

### Post by 5149.5 on 2011-05-04
The Flashaid plugin will take care of all of this for you.

---

### Post by collisionystm on 2011-05-04
> **5149.5 said:**
> The Flashaid plugin will take care of all of this for you.


Flash aid does not work with 64 bit. At least it didn't for me.

---

### Post by 5149.5 on 2011-05-04
> **collisionystm said:**
> Flash aid does not work with 64 bit. At least it didn't for me.

It has worked fine for me several times. That is part of the beauty of it. It doesn't matter which flavor of FF you have, it figures out what you need and installs it. If you have an issue with it, the author lovinglinux is always hanging around in the sticky FF 4 thread.

---

### Post by Churchwarden on 2011-05-05
> **collisionystm said:**
> are you using 64 bit ubuntu?

No, 32 bit, I am almost certain.  I will check.

Nick

PS I am too far down the learning curve ATM.  I can't even discover how to enter commands with 11.04.  I will look further and learn stuff as I look....

---

### Post by Churchwarden on 2011-05-05
> **pqwoerituytrueiwoq said:**
> if you are using 32 bit use apt
if 64bit go here [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)
extract to ~/.mozilla/Plugins
you will need to make the plugins folder

edit 
the command [FONT=Courier New]uname -m[/FONT] will tell you if your are using 64bit or 32 bit

x86_64 is 64bit if it is not that it is 32 bit

I found my way to Terminal and it told me:

i686

I don't know what that means, though.

Nick

---

### Post by oldos2er on 2011-05-05
> **collisionystm said:**
> Flash aid does not work with 64 bit. At least it didn't for me.

FlashAid should work with all architectures. If you need help, see [http://www.webgapps.org/support/add-ons/flash-aid](http://www.webgapps.org/support/add-ons/flash-aid)

---

### Post by oldos2er on 2011-05-05
> **Churchwarden said:**
> I found my way to Terminal and it told me:

i686

I don't know what that means, though.

It means you're using 32-bit. If you install the package ubuntu-restricted-extras, it will install flash, java, and some commonly used codecs. ```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

---

### Post by SavageWolf on 2011-05-05
Just install "Adobe Flash Plugin" from the software centre...

---

### Post by kaldor on 2011-05-05
> **Churchwarden said:**
> I found my way to Terminal and it told me:

i686

I don't know what that means, though.

Nick

If you downloaded Ubuntu, chances are you have 32-bit unless you chose 64 in the list anyway. i686 is 32-bit to my knowledge. This is easy :)

Method 1 (GUI)

Open the Ubuntu Software Centre. Search for "Flash" and install the Flash player. You may need to enable additional repositories. Click Edit > Software Sources and enable the Universe repository for non-foss software.

Method 2 (Terminal)

Run: *sudo apt-get install flashplugin-nonfree*

Have fun

---

### Post by ikt on 2011-05-05
> **oldos2er said:**
> FlashAid should work with all architectures. If you need help, see [http://www.webgapps.org/support/add-ons/flash-aid](http://www.webgapps.org/support/add-ons/flash-aid)

Yes, flashaid is one of the best things I've seen in a while.

---

### Post by Wolligog on 2011-05-05
You can get flash from the software centre, i had to install it a few days ago before i could watch any vids online,

---

