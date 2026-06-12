---
title: "trying to change my etc/enviroment script back to default path"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by ickarus on 2011-06-29
from the begining

i was looking at clutter view on google ,and it looked nice so i went about installing the ppas for nautilus from [http://www.webupd8.org/2010/09/install-nautilus-elementary-with.html](http://www.webupd8.org/2010/09/install-nautilus-elementary-with.html). after doing this i restarted my session.once i logged in i followed these further instructions to get clutter view going (because it wasn't going) i typed gksu gedit /etc/environment in terminal  following instructions from [http://gbutola.wordpress.com/2010/10/16/enable-clutter-view-in-nautilus-elementary/](http://gbutola.wordpress.com/2010/10/16/enable-clutter-view-in-nautilus-elementary/)and a enviroment script came up in text editor with PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games" i went to paste export CLUTTER_VBLANK=none at the end but i deleted usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games" and replaced it with export CLUTTER_VBLANK=none after saving it i logged out..(big mistake) no my system wont log in iv restarted my system countless times but im only ever at the login screen and after i logg in the screen blacks out as if tryna log in but then it logs out .is there a way to change it in terminal or have my hdd run on my 2nd computer which has ubuntu 10.10 and change the enviroment script back?

i am running ubuntu 10.10 on both harddrives the one i mainly use is the 1 i cant log into.i have tried changing the file after connecting the hdd to my secondary desktop but it says i do not have permission. i know the root password i just dont know if there is a way to get around it?

---

### Post by nothingspecial on 2011-06-29
You need to log in to the root recovery console.

Then ```
nano /etc/environment
```

then put it right.

Ctrl-O then Enter to save

Ctrl-X to exit

Then type ```
exit
``` and see if you can resume a normal boot.

---

### Post by jtarin on 2011-06-29
Don't ever set your environment variable in /etc/environment. You set your PATH through the terminal in your /home/username directory by the terminal. It is then written to ~/.bash_profile
In the terminal the command would be ```
export PATH=$PATH:<NEW DIRECTORY TO ADD>
```You should see a backup of the file in /etc/environment that you overwrote. Rename the existing (new) one to environment.old and the old one give it the correct name.

---

### Post by ickarus on 2011-06-29
i have tried out your solution i loaded up the grub boot and wen to root recovery console and input what you have provided after restarting my computer it loads up as per normal once im at the login screen i selet the usr profile and enter password ,after that it seems like its logging in the screen goes black as it did before then takes me back to the login screen.im entering the right password as if i insert a wrong password or no password it just says log in failed.

---

### Post by ickarus on 2011-06-29
to Jtarin were do i enter this command? in the login window in terminal or the boot window?

---

### Post by jtarin on 2011-06-29
> **ickarus said:**
> to Jtarin were do i enter this command? in the login window in terminal or the boot window?In a terminal as the **user** you are going to login in as. If you cannot login to issue this command you switch to a virtual terminal by using the key combination of Ctrl+Alt+F1-F6. This will get you a terminal. Then when finished Ctrl+Alt+F7 to get you back to the GUI.

---

### Post by ickarus on 2011-07-16
> **jtarin said:**
> In a terminal as the **user** you are going to login in as. If you cannot login to issue this command you switch to a virtual terminal by using the key combination of Ctrl+Alt+F1-F6. This will get you a terminal. Then when finished Ctrl+Alt+F7 to get you back to the GUI.
@jtarin i tried it out and it worked thanks alot buddy was a bit slow to get back as you can see...im still running yay tyvm ur advice rocks =)

---

### Post by jtarin on 2011-07-16
Your welcome.:P

---

