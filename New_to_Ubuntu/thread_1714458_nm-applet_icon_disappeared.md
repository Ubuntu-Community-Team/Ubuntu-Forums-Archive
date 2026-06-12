---
title: "nm-applet icon disappeared"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by wrtell on 2011-03-25
Hi,

 I am running 10.10 server with the Ubuntu Gnome desktop installed. All was well with th nm -applet at first it appeared and I thought nothing of it. Then one day the applet disappeared. 

I have tried adding indicator areas to the Panels. 
I have deleted the nm-applets file in .gconf hidden file.
I have tried manually starting nm-applet from a terminal window. 
I have tried adding another nm-applet start command to the programs that start when I log in. 
I have added share the network connection  tick mark to my root userid in the network connections panel.

Nothing works.

Is there anything else I can do?

I believe this issue  started when I enabled root ID. I found I need root to do somethings I wanted to do.
I log in as root most of the time. I have tried my non root id it too has no nm-applet icon at this time.

Any suggestions?

Once again thanks for any assistance.

Regards.

William

---

### Post by Frogs Hair on 2011-03-25
You can try this to reset the panel applets to default.```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by wrtell on 2011-03-25
Hi,

Thank you for the response.

I tried the command . It does not resolve the problem.

Once again thanks

William

---

### Post by Arijit_Kundu on 2011-03-25
if you try to run nm-applet in a terminal with non-root user, what is the output?

---

### Post by Frogs Hair on 2011-03-25
> **wrtell said:**
> Hi,

Thank you for the response.

I tried the command . It does not resolve the problem.

Once again thanks

William

There was another  thread about this recently and I think it was solved . I have not found it yet , but I will keep looking.

---

### Post by Frogs Hair on 2011-03-25
This thread may be worth reading. [http://ubuntuforums.org/showthread.php?t=1471824&highlight=network+manager+applet](http://ubuntuforums.org/showthread.php?t=1471824&highlight=network+manager+applet)

---

### Post by wrtell on 2011-03-25
Thank you for the response.

I  switch to my non root user id. I invoke terminal. I type nm-applet.

I receive a message stating nm-applet is already running.

If I enter the command 'nm-applet -sm-disable' which is how the command is entered in the startup programs list,
I get the same message stating nm-applet is already running.

---

### Post by wrtell on 2011-03-28
Hi,

I cloned the system with this  nm-applet problem( I run the system under Virtual Box and used the VBOX clonehd command).

Much to my surprise, when I started up the cloned system it did  not have the problem.

Examining the daemon logs for the two systems  I noted the system with the missing nm-applet icon issues the following two messages

ubuntu-server-10 gnome-session[1439]: WARNING: Could not parse desktop file /root/.config/autostart/nm-applet.desktop: File is empty
Mar 27 01:37:46 ubuntu-server-10 gnome-session[1439]: WARNING: could not read /root/.config/autostart/nm-applet.desktop
Mar 27 01:37:49 ubuntu-server-10 NetworkManager[671]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs](http://bugs)

The cloned system does not produce these messages

Any thoughts on how to correct the error messages?

I have tried to  rename the nm-applet.desktop file.

Using my root id I cannot perform the  rename function.
I get a pop message with the text 
The item could not be renamed. 

What is  a .desktop file?


Thank you for your assistance.

Regards

William

---

### Post by fourcheeze on 2011-04-05
I think I have the same problem.

I can kill the nm-applet process and restart from the terminal it but nothing appears although there is a nm-applet process running. If I look closely the other items in the notification area move about 1px to the left when nm-applet starts. I've reset the panel settings as described earlier in this thread.

---

### Post by fourcheeze on 2011-04-05
I started digging around in networkmanager and fixed my issue.

It looks like you need

[ifupdown]
managed=true

for network manager to appear at all in your

/etc/NetworkManager/nm-system-settings.conf

(mine was set to false).

Hope that helps someone else.

---

### Post by wrtell on 2011-04-12
Hi,

I followed fourcheeze's suggestion. It did not change the symptoms.No network icon in the notification area.  I do note that every reboot  alters the order in which the icons are displayed. Not sure if this is significant. 

Any rate once again fourcheeze  thanks for the suggestion.

Can anyone point me to documentation on how I might actually gather  some info on what is going on beyond just stating the icon disappeared. I would be happy to work on this or at least try to reproduce in a controlled way. It seems important that Ubuntu not have issues like this. Maybe 'techies' enjoy fiddling with such things but general users do not.

Of course any other ideas are welcome<Grin>

Regards,

William

---

### Post by wrtell on 2011-04-17
All,

Once again thanks for the responses. As I indicated in an earlier post I previously tried to add the notification area or the menu bar based on many items i had read. It did not work
Searching through logs and the NET  trying to understand this whole process was not getting me anywhere so I again  tried adding the notification area.

This time it worked

Initially after adding the notification area the Nm-applet icon appeared  on the bottom bar. A restart put it back on the top bar. Admittedly in different  place than as it  originally appeared after the install  It it remains there to today..

Not sure what happened. I didn't  modify the menu bar in anyway before this occurred 
Thanks for the assistance

William

---

### Post by boukeas on 2012-04-08
> **Frogs Hair said:**
> You can try this to reset the panel applets to default.```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

This is what worked for me and this is the only post presenting this particular solution Thank you very much.

---

