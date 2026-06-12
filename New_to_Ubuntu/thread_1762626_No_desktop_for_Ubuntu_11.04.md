---
title: "No desktop for Ubuntu 11.04"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by omnibuntu63 on 2011-05-19
Hello all, please help.

I updated my system to Ubuntu 11.04 using the Update Manager on my Asus EEE pc. I get the Ubuntu logo, followed by the purple desktop screen, and the indication that my wireless is on. But the screen is blank. **No Icons. No Dock**.**No Menu on Top** The only thing I can do is Force quit the netbook with the power button. The BIOS setup seems to be fine. 

Since there is nothing to point to, I can't access the terminal to even tell whats going on. 

Will I need to re-install from a USB at this point ?

---

### Post by 3xp10r3r|X13 on 2011-05-19
[FONT=Courier New]what about booting into safe mode and accessing the terminal that way???

Or doesn't that work ( 0.o ) 
[/FONT]

---

### Post by omnibuntu63 on 2011-05-19
I press F9, and it gives me options to run in recovery mode. Of course, do you think I can remember what my login and password are ??  no...

---

### Post by ajgreeny on 2011-05-19
You can easily recover your password and username from recovery mode, see the link below, so no need to reinstall just for that.  Just make sure you remember the username and password in future or you'll have to repeat the procedure.  Simple, but time wasting and boring.

Having done that you can then login to the classic gnome desktop from the login screen by choosing username, then in the session menu, bottom right choose **classic gnome** or **classic ubuntu**, I don't remember how it's described.  As you do not have any way to logout, as far as I can see, hold **Print-Screen+Alt-Gr+K** to kill the xsession, which should bring you back to the login screen.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by omnibuntu63 on 2011-05-19
Hi there!

I was away at work. I'm back now

I was able to set a new password . Thanks. Now What? I'm in terminal and it's asking for a command. What should I put in ?? :confused:

---

### Post by omnibuntu63 on 2011-05-20
Greetings

I'm here for now. I wanted to add that in the terminal I see that the Ubuntu 11.04 is installed, ready to go. But still no dock or icons . I have terminal in recovery mode and it is asking for a command. What should I put in??

Thanks !

---

### Post by ubume2 on 2011-05-20
...> **ajgreeny said:**
> 
  As you do not have any way to logout, as far as I can see, hold **Print-Screen+Alt-Gr+K** to kill the xsession, which should bring you back to the login screen....

or

reboot?
sudo reboot

or, if all else fails:
```
$/etc/init.d/gdm restart
```

---

### Post by omnibuntu63 on 2011-05-20
Nothing happens, just the Ubuntu rainbow screen. The wireless doesn't even come on anymore.

---

### Post by ubume2 on 2011-05-20
I think you are over my head. It sounds like the reboot is hanging....
Try pressing enter or space key on the keyboard. Sometimes I can get the boot to proceed if I do that. If not reboot again.

If you still get the rainbow screen:
From a terminal try ```
/etc/init.d/gdm restart
```

If that doesn't work, I'm out of tricks.
If all else fails, IMO try a fresh install of 11.04.

Good luck!

---

### Post by omnibuntu63 on 2011-05-20
Thanks so far:

[3xp10r3r|X13]("http://ubuntuforums.org/member.php?u=1301342")

[ajgreeny]("http://ubuntuforums.org/member.php?u=27747")

[ubume2]("http://ubuntuforums.org/member.php?u=181548")

I will be away from the computer till later. Nothing happening on the Asus. If you think of anything else let me know. I think a clean install may be in order.

---

### Post by Tkdboy on 2011-05-20
I had the same problem a few days ago.
My solution is the use of Ubuntu classic.

Have a look here...
[http://www.liberiangeek.net/2011/04/change-classic-ubuntu-desktop-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/04/change-classic-ubuntu-desktop-ubuntu-11-04-natty-narwhal/)

---

### Post by sikander3786 on 2011-05-20
Unity is not that bad. There have been glitches but overall, I am loving it.

Hope this link would help you repair your desktop.

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by ubume2 on 2011-05-21
Edit: I'm learning how to tutor as I proceed. Try this:
Go to tty by Alt+Ctrl+F2
At the command line enter $nano /boot/grub/grub.cfg
Now do not edit grub.cfg. Page down  1 or 2 times using Ctrl+V
Hopefully  you will see the Windows install and the Ubuntu install. Copy grub.cfg to the Desktop
```
$sudo cp /boot/grub/grub.cfg  /home/yourusername/grub.cfg
```

exit the document by Ctrl+x. You may have to exit a second time by entering "exit" in the command line, and login again. You can no longer edit grub.cfg, but can view it.  You can now safely view the grub.cfg file by ```
$ nano grub.cfg
```

If you see both Ubuntu and Windows in the grub.cfg file.
```
Ctrl+x
$exit
```

Try this:
cd
```
$sudo grub-install /dev/sda
$sudo update-grub
```
Reboot
Hopefully you will have a grub to boot into.  You may want to modify grub later. That's a different story.
> **sikander3786 said:**
> Unity is not that bad. There have been glitches but overall, I am loving it.


I agree
----------------------------------------------------------------------------------------------------------------------------
Don't go here if the above works.
You can try these suggestions or try to reinstall.
```
$unity --reset
```      or
Force Unity Compiz to run in [http://ubuntu4beginners.blogspot.com/](http://ubuntu4beginners.blogspot.com/)

You installed Ubuntu using a usb stick?  Is that stick a usb Live stick?

Did you use a Netbook Remix install or a regular install?

IMO, if it is USB Live and it works, it's probably time to reinstall to the same partition where your faulty Ubuntu is now.

---

### Post by omnibuntu63 on 2011-05-21
I reinstalled the 11.04. It seems to work well.

Now I have a problem with the wireless connection. 

The computer indicates that the wireless is disconnected. When I first installed ubuntu, that was not an issue. now it is

I'll try the Asus settings and see if I can re-establish the connections

thanks

---

### Post by ubume2 on 2011-05-21
Good news on the reinstall.

Wireless can be tricky, depending on your wireless card.  Did you try clicking on the upside down triangle on the top panel--towards the right?

---

### Post by omnibuntu63 on 2011-05-21
Thanks I got the wireless working. It was disabled on the Asus , it's back on


Thanks everyone for advice and help . Ubuntu people rule !!:guitar:

---

### Post by Pra_ap on 2011-06-11
HI,
I am having the same problem.I have upgraded it from version 10.10. After logging in it shows notification for the wifi connection and nothing is on the desktop. So I logged in through ubuntu classic, it is working fine and i have created shortcut of the terminal on screen so I can access directly. How can I restore all panels on desktop .

---

### Post by wildmanne39 on 2011-06-11
> **Pra_ap said:**
> HI,
I am having the same problem. After logging in it shows notification for the wifi connection. I logged in through ubuntu classic, it is working fine and i have created shortcut of the terminal on screen so I can access directly. How can I restore all panels oon desktop .
Hi, click on reset unity and compiz in my signature and see if that works,but you really have not given enough information for me to know what your problem is. Did you mess with compiz settings? Did you do a clean install or upgrade?

---

### Post by Pra_ap on 2011-06-11
Thanks for the rply. I have upgraded my ubuntu from version 10.10. Previously I had compiz installed  in it. After the upgrade the special effects were not seemed to be working so I did uninstall compiz. Is it because of this ..?

---

### Post by Pra_ap on 2011-06-13
Is there no solution for this problem ..?I think I have to re-install it.

---

