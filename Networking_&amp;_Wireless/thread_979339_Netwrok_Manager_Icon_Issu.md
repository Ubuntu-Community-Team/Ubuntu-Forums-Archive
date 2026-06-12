---
title: "Netwrok Manager Icon Issu"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by wordslinger on 2008-11-11
[FONT="Trebuchet MS"]Hello People,

I've just installed Ubuntu 8.10 on my Dell Vostro 1400 Laptop. Everything works fine. I love the simplicity of the distribution.

The problem begins when the Network Manager Icon on the top right hand corner of the screen goes missing. I am unable to find any clue on how to get it back.

Please note that I am not talking about Network Monitor. I have searched the web for a solution but nothing works.

Any ideas on a solution to this predicament?[/FONT]

---

### Post by iponeverything on 2008-11-11
Go to System->Preferences->sessions

then to to "Add"

the fields are as follows:

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

then choose "save"

---

### Post by wordslinger on 2008-11-11
[FONT="Trebuchet MS"]Thank you for your reply.

I have done that but it is already there and is in the accurate format.

Do I delete it and then add it back again?

Cheers![/FONT]

---

### Post by andyanderso on 2008-11-11
I am having the same problem.  I startup the computer and my nm-applet icon is there but at some point it will dissappear.  The only way I have found to get it back is by restarting the computer.  When I go into terminal to try to restart the nm-applet I get this message:

[INDENT]> ** (nm-applet:7092): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:7092): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
andy@hermes:~$[/INDENT] 


Any ideas?

---

### Post by iponeverything on 2008-11-12
open a terminal and run "nm-applet"

next time you reboot it should still be there.

If it complains when you try to start it do:  "sudo killall nm-applet"
and try to start it again.

---

### Post by j0natz on 2008-11-12
I have the same problems.

I did a update from 8.04 to 8.10.

I did not had this problems in 8.04

Everytime I boot my Laptop in a foreign enviroment where I have never added a WLAN in 8.04 my nm-applet won't show up.

This also happens if i switch off WLAN, 3G, Bluetooth with the hardware switch. If I switch it on the nm-applet also does not show up.

Br

Jonas

---

### Post by ragonz on 2008-11-12
Sorry if i misunderstood ur problem, but if you're talking about network manager icon in top desktop panel then try to "add to panel" - "notifications area"

---

### Post by j0natz on 2008-11-12
> **ragonz said:**
> Sorry if i misunderstood ur problem, but if you're talking about network manager icon in top desktop panel then try to "add to panel" - "notifications area"

This does not work for me :/

I added a aotification area and did then --> xterm --> nm-applet --sm-disable

No nm-applet icon :(

---

