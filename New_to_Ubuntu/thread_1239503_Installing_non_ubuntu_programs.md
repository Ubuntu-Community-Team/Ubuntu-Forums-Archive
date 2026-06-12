---
title: "Installing non ubuntu programs"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by wheels5894 on 2009-08-13
I thought I knew what i was doing by installing Thunderbird 3 beta 3 but I came into copmflict with the system in trying to instal it to a folder in /lib/usr I am not allowed to do this and I could not see a way of talaking the system into letting me. 

I opened the .tar file in ARK and could unpack it into a folder as long as it is not in /lib/usr. I have it running nicely  in a folder on /home but would rather like to get it working correctly. How do I do it? 

I'd also quite like to persuade Flash Player to do the same but the problem is the access to /lib/usb and the permissions to do it. 

Thanks for any help for a poor windows user!

---

### Post by Tibuda on 2009-08-13
This is because of permissions. Only root can write outside /home. There's nothing wrong in running Thunderbird from your home folder, but if you really want to save it somewhere else, you must run your file manager with kdesu (like **kdesu dolphin**). Why /lib/usb ?

---

