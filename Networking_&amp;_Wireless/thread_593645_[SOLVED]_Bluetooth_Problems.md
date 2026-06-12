---
title: "[SOLVED] Bluetooth Problems"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by Inxsible on 2007-10-27
I mistakenly posted in the absolute beginners thread when I meant to post here. 

In Feisty, I had installed the Bluetooth File Sharing app from the Add/Remove and everything worked great. I could send and receive files.

In Gutsy, however, the default install came with an app called 'Bluetooth Analyzer'. So I think I don't need any other apps to get my bluetooth phone working with my computer.

I have successfully got my phone paired with my machine, but when I search from my phone to send a file to my computer, it never finds my computer.

On the flip side, when I right click the Bluetooth Analyzer icon in the tray and select 'Browse Device' and then select my phone, I get this error message
      	```

 	     "obex://[00:16:b3:46:d4:71]" is not a valid location.
Please check the spelling and try again.
``` 
Can someone please tell me what may be missing?

Or do I have to install additional packages ?

---

### Post by Inxsible on 2007-10-27
bump.

---

### Post by varkey on 2007-10-28
I have the same issue. Some one please help.!

EDIT : 

Fixed it! Install this package - gnome-vfs-obexftp. :) :)

Thanks to [http://ubuntuforums.org/showthread.php?p=3629543](http://ubuntuforums.org/showthread.php?p=3629543)

---

### Post by Inxsible on 2007-10-28
I already have that package installed. Still no love :(

EDIT : Strange ! I re-installed the package from Synaptic and now i can browse my phone !!  Whew !

Still though, I cannot see my computer from my phone :( nor the phone from my computer. How would I go achieving that ?

Browsing is all nice and fine, but what's the point if i can't send or receive files ?

---

### Post by Gordone on 2007-10-30
Hi,

Thanks, installing the library helped me, although I still get the error message I can now browse my phone.

Cheers,
Gordon

---

### Post by Inxsible on 2007-11-02
I installed Blueman and now everything works :)

---

### Post by satbunny on 2007-12-07
Thanks, this helped me a lot.

---

