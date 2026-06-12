---
title: "xdmcp setup tool"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by jonmartin on 2007-09-14
Is there a config tool in kubuntu 7.04 to enable and configure xdmcp?

---

### Post by drinkpepsi on 2007-10-18
Just do the following:

If you have access to do a graphical login on the local display of the Ubuntu box, this is extremely easy:

1. Click System, Administration, Login Window. (You'll be prompted for YOUR password at this point.)
2. Select the 'Remote' tab.
3. Change the 'Style' from 'Remote login disabled' to any of the other selections. (I went with 'Same as Local')
4. Once you have changed the Style, you will now have a 'Configure XDMCP' button in the lower right. (You don't have to change anything there, but good to take a look to see what you can change.)
5. Close 'Login Window Preferences'

Everything is set up at this point, but we still have to restart GDM (The graphical login handler) so that it picks up on the configuration changes.

Now we need to restart the KDM process so it will re-read the configuration file.

- The easiest way to do this is to just reboot the machine.

- The quickest way is to do the following:

ps -ef | grep gdm

This will print out a list of processes with the letters 'gdm' in the name. Find the one that looks like the following (Specifically the one that ends in /usr/sbin/gdm):

root    4530      1     0 0:09:20 ?          00:00:00 /usr/sbin/gdm

See the number right after root? 4530 in my example, you will almost certainly have a different number. That's the process ID or PID. Type the following command to restart gdm (Substituting the PID number you have for the 4530 in my example):

sudo kill -HUP 4530

This restarts the Gnome Display Manager. Doing this instantaneously kills all graphic sessions on the box (including the one you are using) with no warning. Don't panic when this happens, the login screen will pop up in a few seconds and you can log back in. (But no reason to, as in the next step you are going to log in from the remote location...)

---

