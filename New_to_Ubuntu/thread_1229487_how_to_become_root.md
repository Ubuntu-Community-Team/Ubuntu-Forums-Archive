---
title: "how to become root"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by Sphynx718 on 2009-08-02
I need to be able to add files to certain usr folders and am unable to because i get the "you don't have the right permissions...etc". So i'm guessing i need to be root. But when i go to terminal and type su and then my password i get a failed autho message. 

I know during fedora setup you get the option of setting up the roots password but i never came across that in ubuntu. However I thought i read somewhere that ubuntu uses the password used by the first user account created for root. Clearly this isn't the case.

Any ideas?

The only reason why I need to get into usr is to copy some conf and ppd files to get my canon mp630 working because the repos only go up to the old 610 model *sigh*.

EDIT: Also, does anyone know of a tool (like fedora) that you can access via the main menu and enter the root password to get privileges that way?

---

### Post by credobyte on 2009-08-02
```
sudo command

```

If you need to do something from Nautilus:
```
gksudo nautilus
```

---

### Post by hellmet on 2009-08-02
use 
```
sudo su
```
to become root. Use at your own risk.

---

### Post by overdrank on 2009-08-02
[RootSudo]("https://help.ubuntu.com/community/RootSudo")

 [Forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=716201")

---

### Post by Sphynx718 on 2009-08-02
Thanks for that. The printer is my last hurdle in making linux a viable alternative to Windows. Also, once I have become root, how does one 'logoff' as root via terminal?

...good old windows, their best version was 3.11 IMO XD

EDIT: titled changed to be more...'descriptive'

---

### Post by W4l0ck on 2009-08-02
sudo <command> <flags>

---

### Post by CatKiller on 2009-08-02
> **Sphynx718 said:**
> Also, once I have become root, how does one 'logoff' as root via terminal?

If you used *sudo*/*gksudo*/*kdesu* to run an application, only that application will be run as root. Anything else won't be. You don't need to do anything special to stop being root, you just close that application when you're done.

If you use *sudo su* to have a root session, you would use *exit* to stop your root session. Not that *sudo su* is recommended. *sudo -i* is a better plan.

---

### Post by sandman55 on 2009-08-02
Another way but it is frowned on by some because you are permanently in root while you have the nautilus window open is to Alt+F2 and in the prompt that opens type gksudo nautilus and in the window that opens you can do anything like you can in windows.

---

### Post by SunnyRabbiera on 2009-08-02
You can also bypass sudo by installing the nautilus-gksu package:
[http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=names&keywords=+nautilus-gksu](http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=names&keywords=+nautilus-gksu)

---

