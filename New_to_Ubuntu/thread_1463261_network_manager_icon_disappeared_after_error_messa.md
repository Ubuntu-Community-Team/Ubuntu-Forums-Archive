---
title: "network manager icon disappeared after error message about resources."
date: 2010-04-26
forum: New to Ubuntu
---

### Post by candiru on 2010-04-26
I'm trying to make a switch to Ubuntu from Windows.  Things were going great, including internet working immediately after installation, until I got a small window saying something about the Network Manager not having enough resources.  I clicked the only button in the pop-up window, and the Network manager icon in the notification area went away.  the internet continued to work though the icon was gone.  however, when I restarted the computer, the network manager icon did not show up, nor did the internet connection work.  I'm trying desperately to get these things working again.  I want to use Ubuntu for everyday things because it's much faster than Windows, but I need the internet.  I'm actually using a Windows OS computer to type this message.  

Thanks for any help.

---

### Post by candiru on 2010-04-27
[COLOR=black][FONT=Verdana]While working on the Internet, an error message popped open and said the Network Manager didn't have enough resources, and I clicked the close button on the error window message, then the Network Manager Icon disappeared.  After rebooting the computer, the Icon was still gone, but so was the internet.  When I run the Live CD, the network manager starts up fine.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]How do I get the Network Manager to start working again?  I really like Ubuntu, but I need the internet to do homework on.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks for any help.  [/FONT][/COLOR]
[FONT=Courier New][SIZE=3] [/SIZE][/FONT]

---

### Post by Hospadar on 2010-04-27
I'm not sure why it might have disappeared and not restarted on re-boot, but you can try starting it manually.
I believe the command is "nm-applet"

First start it up in a terminal and watch for error messages:
Applications->Accesories->Terminal
nm-applet

If that works fine, close the terminal, then Alt-F2 and type nm-applet and hit enter.

If the command doesn't work, or gives you some non obvious error messages, you may need to restart the network manager backend (NetworkManager, which handles network connection in ubuntu, has a backend which does all the dirty work, and a front end, nm-applet, which lets you click to do stuff).

To restart the backend network manager, in a terminal
sudo /etc/init.d/NetworkManager restart

Now start/restart nm-applet

If it still doesn't work, post any error messages you get or new insights gained from error messages and terminal output and we can try to go from there.

fyi:
/etc/init.d is a folder that contains a lot of start-up scripts
/etc/init.d/NetworkManager is a script to start/stop/restart network manager, the restart argument restarts it (start and stop do the obvious things as well).

There are a lot of other scripts in that folder that can do useful things for you if you know what you're doing.

---

### Post by candiru on 2010-04-27
Somehow, after messing around with the ubuntu boot options, I did the recovery mode.  After the reboot, the internet worked, but the icon did not show up.  I updated the Network manager in the Ubuntu Software center, followed your instructions (after a few failed attempts because the terminal did not find the nm-applet file), and the icon showed up on the notification area.  So, the problem is solved for now.

Next time I experience this, I'll make sure to take screen shots and post the error message.  I appreciate the help, and want to make sure that others that experience a similar scenario are able to find resolution.

Thanks so much.  I owe you one.

---

### Post by cariboo on 2010-04-29
Please don't create multiple threads on the same subject, I merged your two threads,

I see your problem is solved, so I'll mark this thread solved.

---

