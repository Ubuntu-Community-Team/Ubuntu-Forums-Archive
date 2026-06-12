---
title: "nm-applet not working when switching user (intrepid)"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by korami on 2008-11-01
Hi there,

I've searched in the forums and have seen that some users out there are experiencing issues with the network manager applet *nm-applet* after upgrading to Intrepid, but noone seems to be describing the following issue I'm having:

After booting and logging in with the default user, the NetworkManager connects fine to my wireless network, and also the network manager applet appears in the Notification Area. So everything fine here. But when switching into the other user (me and my wife are using the laptop with diffferent users), the nm-applet is missing from the Notification Area, although I'm still having wireless connection.

So the only problem is the missing network applet when switching user. It also doesn't matter which user I'm logging in with first.

Entering nm-applet --sm-disable in the terminal, the same error appears as reported by many others:
```
~$ nm-applet --sm-disable
** (nm-applet:9161): WARNING **: <WARN> applet_dbus_manager_start_service(): 
Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:9161): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```

Needless to say this was working all right in Hardy.

Can anyone help?

Cheers.

---

### Post by vitorgatti on 2008-11-01
Yeah, I'm having the same error.

---

### Post by korami on 2008-11-02
So there are 2 of us experiencing this issue... maybe there is a third one having figured out how to fix this...

---

### Post by kivanov1992 on 2008-11-03
Me too) btw, there is a bug in Launchpad with this issue
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284596]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284596")

---

### Post by korami on 2008-11-03
Good to know it is filed as a bug. Hopefully they will also change the status, open it and fix it asap.

---

### Post by Rod Hull on 2008-11-04
I have this too - and had originally posted it in the [how to install the new 0.7 version of NM on Hardy](http://ubuntuforums.org/showpost.php?p=6024062&postcount=241) thread but no-one replied...

Here's hoping they fix it - it's a massive bug IMO, especially when Intrepid replaces the login button with the fast-user-switch button.

Very surprised that more people haven't noticed this behaviour, to be honest!

---

### Post by !nkubus on 2008-11-04
Having the same bug but i'm the only user :(..

a laptop without the network manager tray icon is pretty useless

---

### Post by korami on 2008-11-05
If you're the only user, then you might find details to your issue here:

[http://ubuntuforums.org/showthread.php?t=956187&highlight=nm-applet+intrepid](http://ubuntuforums.org/showthread.php?t=956187&highlight=nm-applet+intrepid)

Cheers.

---

### Post by mymundo on 2008-11-06
I have the same problem!!! 
and still looking for a solution...

---

### Post by cowanh00 on 2008-11-06
I'm sure not if I have found a solution but you could all try this anyway....

Open up a terminal and type in:
```
gconf-editor
```

In the configuration editor click on the arrow next to the 'system' folder and then click on the arrow next to 'networking'. 

Under networking you might have a 'wireless' folder, this seams to be left over from the old version of network manager. (Or at least it was for me because I keep my home on a different partition and this folder was never recreated.) Click on the arrow on the 'wireless' folder and it shows the names of networks you have previously accessed.

What I did is go through and highlight each folder with a network name and right click and unset all of the items on the right. I then did the same for everything under connections (this is divided into numbered folders under the folder 'connections', don't worry this will be recreated.)

You can now close the configuration editor.

*[This part is possibly optional]* Then I went to Applications> Accessories> Passwords and Encryption Keys and then to the Passwords tab. I removed all the keys relating to wireless connections here.

Then reboot. For me this made the network manager load on startup when I logged back in and I was able to use Wireless internet with no troubles.

Not sure if this will fix the issues in this thread but it certainly helped me...

---

### Post by ajm-b on 2009-01-20
I'm glad I stumbled upon this thread as I have experienced this problem also, and it is the main issue holding me back from switching completely to Ubuntu on my laptop. Me and my partner use the same laptop under different user profiles, if one of us boots the machine and connects to the wifi network, the other cannot control the connection. This becomes more of an issue when you put the laptop to sleep. Upon waking, the wifi connection is only restored if the first user that logged on (and thus has the nm-applet running in their session) logs back in.

A while ago I surfed for a solution and someone had indicated some changes to the power manager (can't remember the exact config now :() to shutdown and restart nm-applet upon sleeping should help, however, this didn't fix the issue.

Unfortunately XP seems to cope with such a scenario, as it appears that each user can control their wifi connection separately. I'd love for someone to find a workaround to this issue so I could finally make the switch.

---

### Post by Rod Hull on 2009-01-20
It used to work perfectly in Hardy. They've obviously broken it in Intrepid...still no sign of a fix...

---

### Post by uc50_ic4more on 2009-06-22
Hello -  I just wanted to chime in and add myself to the list of those experiencing this issue (using Jaunty, from a clean install). I auto login my account, but when fast switching to my wife's account, nm-applet is not present in the tray. It presents no inconvenience for us, as this particular computer is on a wired network with a static IP address, but it'd be nice to get a fix.

---

### Post by Matt M on 2009-08-28
I have the same problem running Ubuntu Jaunty (network manager applet appears in the panel for the first user to log on, but not if you switch to another user). 

There is a workaround: install another network manager like Wicd (instructions [[COLOR="Blue"]here[/COLOR]]("http://wicd.sourceforge.net/moinmoin/Wicd%20on%20Ubuntu")). Reboot, and it should work. (It worked for me!)

---

### Post by silviutp on 2009-09-23
Hi,

How can I remove NetworkManager Applet from panel ? <Ubuntu 8.10>

Thanks.

---

