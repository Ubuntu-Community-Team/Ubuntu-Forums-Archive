---
title: "Blank screen after logon"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by nanco on 2009-10-30
Hello, 

I have been using Jaunty for a few weeks and it is a lot of fun. I have run into a problem I have not been able to solve. I tried to install a driver for my Radeon 9550 and I must not have followed all the instructions. So I aborted and undid everything. 

However, since then, I get a blank screen with a movable cursor after I logon. I know the video works OK. I can give a command from terminal and get nautilus or gedit visible and working. 

It seems to me that I have either deleted or improperly modified the files responsible for putting the normal screen up. 

I would appreciate it if someone could tell me which is (are) the file(s) Jaunty uses to put up the information that normally appears after the signon. 

Thanks.

---

### Post by jhenager on 2009-10-30
[http://blog.phpkemist.com/2009/04/24/ubuntu-video-driver-repair/](http://blog.phpkemist.com/2009/04/24/ubuntu-video-driver-repair/)

"Hit Ctrl+Alt+F1 when you get stuck at the &#8220;Boot Scripts&#8221; part, or even at the login screen. Give this a try even if the login screen doesn&#8217;t appear, but you think it&#8217;s there. You should then see a standard white text on black screen interface for terminal control.

Now, enter the following with subsequent authentication:

sudo dpkg-reconfigure xserver-xorg

Ubuntu should walk you through some easy to answer questions, using the arrows and tab key to navigate and accept or reject options. Enter the &#8220;sudo reboot&#8221; when it&#8217;s done and you should be good to go&#8230;"

---

### Post by ajgreeny on 2009-10-30
Unless things have changed since either hardy or jaunty, the command ```
sudo dpkg-reconfigure xserver-xorg
```is useless with the newer xorgs, and will not help you at all.  I suggest you uninstall the driver if you can, then try booting into recovery mode from the grub menu and when the small menu appears choose **xfix** then restart when that has finished.  Hopefully that will get you back to the OS driver again.

It may, of course, be that you uninstalled something important when removing the driver but without knowing more it's difficult to say.

---

### Post by nanco on 2009-10-30
Thank you fellows, but I guess I did not make myself clear. I did all that you suggest. The problem is NOT with the xorg since I have no problem getting the full log on screen and thereafter am able to selectively sned programs to the display. The problem is that all that normally loads after the logon, that is the top and bottom menu bars, and the screen background don't. I believe thare is a program that sends all this information to the screen but it does not in this case either because the file is missing or corrupt. What is this file, so that I can correct the problem.

Thank you.

---

### Post by ajgreeny on 2009-10-31
I don't know if you have found your answer to this problem yet, but having now tried 9.10 myself, and with an ati 9200SE card, I have exactly your problem; the desktop appears with panels and applications will open, but there is no desktop wallpaper background.

This is apparently a problem with the open source ati/radeon driver and has been noted and a bug filed at launchpad.

Here are several links about the problem with various solutions, ranging from not using desktop effects, using 16 bit colour, to a driver mod.  have a look at them all and make your choice.
[http://ubuntuforums.org/showthread.php?t=1304961](http://ubuntuforums.org/showthread.php?t=1304961)
[http://ubuntuforums.org/showthread.php?t=1305306](http://ubuntuforums.org/showthread.php?t=1305306)
[http://ubuntuforums.org/showthread.php?p=8199471#post8199471](http://ubuntuforums.org/showthread.php?p=8199471#post8199471)

---

