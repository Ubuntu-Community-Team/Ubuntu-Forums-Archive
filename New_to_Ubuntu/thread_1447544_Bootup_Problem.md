---
title: "Bootup Problem"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by LunixTucson on 2010-04-05
I've been running happy for 3 months - dual boot configuration.
Yesterday received the following when booting up:

1) "Could not update ICEauthority file /home/jim/.ICEauthority" [I]after clicking "ok"
[/I]2) "There is a problem with the configuration server. (usr/lib/libgconf2-4/gconfig-sanity-check-2 exited with status 256)  [I]after clicking "ok"
3) Background changes to default orange with no icons, toolbars etc. Gives box with the 
following:  "[/I]Nautilus could not create the follow*ing: *folders: /home/jim/Desktop; /home/jim/.nautilus
--------------------------------------------=/=---------------------------------------------
The only (that i remember) thing i had done prior to the problem was try to change the login splash screen.

Using recover mode i did a touch to create the /home/jim/.nautilus and chmoded it to 777.
No change in the above;   Don't want to go furher - afraid to REALLY screw up.

Any advice, help or comments appreciated
jim weber - LunixTucson

---

### Post by stderr on 2010-04-05
I remember having this ICEauthority issue once myself. If I'm remembering the right incident, it was a bizarre case of the ownership of the home folder changing. Try running something like this:

```
sudo chown YOUR_USERNAME -R /home/YOUR_USERNAME
so, e.g., sudo chown ace -R /home/ace
```

chown changes ownership to the specified user. The -R flag tells it to do so recursively - for all files/folders in your home directory.

It might be wise to corroborate this online somewhere, as there's a chance I'm thinking about something else - although it looks right.

---

### Post by Gone fishing on 2010-04-05
Mmm it looks like permissions - 

I'd first see if the home directory exists Alt Control F1 login and use ls to check that /home/Desktop is still there etc. Assuming it is I'd try to 

sudo chown -R jim /home/jim (make sure Jim owns Jim's home) and  I don't think it will like 777 I'd try only letting the user have full privileges in the home directory.

---

### Post by LunixTucson on 2010-04-05
Thank you for the replies - saddly the suggestions did not work. I get the same series of messages are noted above.  After starting up in recovery mode i checked the permissions and owership and all showed correct - with myself as owner 
Any other suggestions or a way to reinstall without overwriting rather important data.
Thank you in advance
jim weber LunixTucson

---

### Post by GO%)$@*1 on 2010-04-05
> **LunixTucson said:**
> Thank you for the replies - saddly the suggestions did not work. I get the same series of messages are noted above.  After starting up in recovery mode i checked the permissions and owership and all showed correct - with myself as owner 
Any other suggestions or a way to reinstall without overwriting rather important data.
Thank you in advance
jim weber LunixTucson

This may have been caused by running a graphical application with sudo and not gksudo. That occurrence has been known to cause problems. Have you done that?

---

### Post by LunixTucson on 2010-04-05
No regarding the use of sudo directly - prior to the problem i was using MoneyEx and also tried to change the login splash screen using the Ubuntu System tool.  Running 9.04 if that is any help.

Thank you.
jim weber LunixTucson

---

### Post by Gone fishing on 2010-04-05
Had a search and all I came up with was:

sudo chown jim:jim /home/test/.ICEauthority 
sudo chmod 600 /home/jim/.ICEauthority

I suppose if that doesn't work you could rename or delete  .ICEauthority and it will probably be remade or create a new user then copy the files to the new user account.

---

### Post by GO%)$@*1 on 2010-04-05
> **Gone fishing said:**
> Had a search and all I came up with was:

sudo chown jim:jim /home/test/.ICEauthority 
sudo chmod 600 /home/jim/.ICEauthority

I suppose if that doesn't work you could rename or delete  .ICEauthority and it will probably be remade or create a new user then copy the files to the new user account.

That's all I found, too.

---

### Post by GO%)$@*1 on 2010-04-05
> **Gone fishing said:**
> Had a search and all I came up with was:

sudo chown jim:jim /home/test/.ICEauthority 
sudo chmod 600 /home/jim/.ICEauthority

I suppose if that doesn't work you could rename or delete  .ICEauthority and it will probably be remade or create a new user then copy the files to the new user account.

Make sure to back up your .ICEauthority file before you delete it.

```
cp /home/jim/.ICEauthority /home/jim/iceauthority-old
```

Copying files to a new user account would cause you to lose config files that aren't stored in the home folder. I don't think that would be a good idea, assuming one wants to preserve their settings.

---

### Post by LunixTucson on 2010-04-05
Once more into the breach dear friends,
removed the .ICEauthority, rebooted - same error msgs as before. and the ice file was not recreated.  Anything else ?
thank you
jim weber - LunixTucson

---

### Post by Gone fishing on 2010-04-06
Very strange but I found two links that suggest a bug with autologin

[http://ubuntuforums.org/showthread.php?t=1431381&highlight=ICEauthority](http://ubuntuforums.org/showthread.php?t=1431381&highlight=ICEauthority)

> Solution Found a fix. I've seen a lot of people with the same or a similar problem so I'm not sure if this is a bug or what but I'll post my solution anyways. After my computer had told me about the errors I entered a terminal with Ctrl+Alt+F2. 

I then typed in:
sudo service gdm restart

This opened up my desktop with everything appearing to be completely normal. I then turned off auto-login and restarted my compute

and 

[http://ubuntuforums.org/showthread.php?t=1437213&highlight=ICEauthority](http://ubuntuforums.org/showthread.php?t=1437213&highlight=ICEauthority)

> When I installed Ubuntu (9.10) I selected the option to encrypt my home directory. Everything worked fine until I enabled the auto-login. Disabling auto-login (by removing /etc/gdm/custom.conf) got my desktop back.

are you using encryption?

If this doesn't I think you might have to create a new user and copy the files over

---

### Post by LunixTucson on 2010-04-07
Removal of the custom.conf did the trick!   Super! Thank you for all the help.  Very much appreciated.

---

### Post by Flos Headford on 2010-04-08
This worked for me:
Use a Ubuntu Live CD to boot up, and choose a command-line (shell) option.
With this, set your $HOME directory (/home/username) permissions to something appropriate (I used 755) and make sure all directories can be listed with the "ls" command. Then remove nautilus with ```
sudo apt-get remove nautilus
``` and delete the .ICEauthority entry in $HOME, and possibly in /var/lib/gdm. Then reboot with ```
sudo shutdown -r now
``` When you choose the same option on boot-up, from the command line you can use ```
sudo apt-get install nautilus
sudo shutdown -r now
``` and retrieve the CD a bit smartish. I do hope you get a clean straight boot and login, as I did!
With thanks to all who helped me,
Phil

---

