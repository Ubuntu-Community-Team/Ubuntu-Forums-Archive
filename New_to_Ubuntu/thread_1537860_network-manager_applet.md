---
title: "network-manager applet"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by wstay on 2010-07-24
I am using ubuntu 9.10 and I cannot find the network-manager applet on the panel on my original administrative user Desktop after I had added a New User. The network-manager applet appears on the New User panel but disappear from the panel of the original user. I try to add the Notification Area to the panel of the original user but it won't appear. Is there a way to add the network-manager applet onto the panel of the original administrative user?

---

### Post by mikewhatever on 2010-07-24
If the notification area is there, try launching the applet from a terminal window with 'nm-applet --sm-disable'.

---

### Post by wstay on 2010-07-27
I posted: 

wstay@wstay-desktop:~$ nm-applet --sm-disable

** (nm-applet:2455): WARNING **: <WARN>  request_name(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

wstay@wstay-desktop:~$ 

Is there any other way to put the network-manager applet on the panel on my original administrative user Desktop?

---

### Post by wstay on 2010-07-28
Posting: 'nm-applet --sm-disable' on the terminal does not get back the network-manager applet on the panel (taskbar) on the Desktop. The network-manager applet would not appear on the panel (taskbar) on the Desktop

It returns the following message:
wstay@wstay-desktop:~$nm-applet --sm-disable
** (nm-applet:6384): WARNING **: <WARN>  request_name(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3
wstay@wstay-desktop:~$

Can someone please explain and how to resolve this problem?

---

### Post by varunendra on 2010-07-29
See if [this]("http://ubuntuforums.org/showthread.php?t=1311790&page=2") helps. (pages 2-3)
Also [this]("http://ubuntuforums.org/showthread.php?t=1328631"), problem is opposit to yours but solution suggested by dineshs (post #4)may work.
Another [link]("http://www.ubuntugeek.com/possible-solutions-to-fix-the-missing-network-manager-icon-in-ubuntu-9-10.html").


If none of these work, then try uninstalling NM applet and install wickd instead.

---

### Post by wstay on 2010-08-17
I reinstall a fresh install of ubuntu 9.10 and then create a new user.
The network manager applet is not available from the panel where it should be available from the new user desktop.
I tried: wstay@wstay-desktop:~$ nm-applet --sm-disable and 
1. Go to /usr/share/app-install/desktop and find Network Manager
2. Right click.. Properties.. copy the command line
3. Go to System.. Preferences.. Startup Applications and look for Network Manager
4. Click Edit and paste the command then save
5. Log out, log in
Both method did not work.

---

### Post by varunendra on 2010-08-17
> **wstay said:**
> I reinstall a fresh install of ubuntu 9.10 and then create a new user.
The network manager applet is not available from the panel where it should be available from the new user desktop.
I tried: wstay@wstay-desktop:~$ nm-applet --sm-disable and 
1. Go to /usr/share/app-install/desktop and find Network Manager
2. Right click.. Properties.. copy the command line
3. Go to System.. Preferences.. Startup Applications and look for Network Manager
4. Click Edit and paste the command then save
5. Log out, log in
Both method did not work.

For "nm-applet --sm-disable" try
```
sudo nm-applet --sm-disable
```Maybe the error was due to no root privilege which sudo will take care of.

[B]
PS:[/B] To add a new user (if required) to sudoers list, see [how to]("http://ubuntuforums.org/showthread.php?t=139243").

---

### Post by wstay on 2010-08-17
> Maybe the error was due to no root privilege which sudo will take care of.


I enable Administrative privilege from System > Administration > Users and Groups for the new user and post the command:
wstay1@wstay-desktop:~$ sudo nm-applet --sm-disable
[sudo] password for wstay1: 
wstay1@wstay-desktop:~$ sudo nm-applet --sm-disable
[sudo] password for wstay1: 
** (nm-applet:2631): WARNING **: <WARN>  request_name(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3
wstay1@wstay-desktop:~$ 

Even though with the above message,I now notice that the NetworkManager applet does appear on the panel for the new user desktop. BUT when I switch user to the original user, the NetworkManager applet has disappear from the original user desktop.
Is it not possible to have the NetworkManager applet appear on both the original user and the new user desktops?

---

### Post by wstay on 2010-08-18
Having lost the Network Manager applet on the panel on the desktop (and there seem to be no way of getting it back) and if our internet connection is disconnected, what else can we use to reconnect to the internet?
Without the Network Manager applet on the panel on the desktop, there is no way we can know if our internet connection is disconnected.

---

### Post by earthpigg on 2010-08-18
> **wstay said:**
> The network-manager applet appears on the New User panel but disappear from the panel of the original user. 

this is kind of a shot in the dark, but try these three commands:

```
mv ~/.gconf/apps/gnome-settings/gnome-panel ~/.gconf/apps/gnome-settings/gnome-panel-backup

mv ~/.gconf/apps/panel ~/.gconf/apps/panel-backup

mv ~/.gconf/apps/nm-applet ~/.gconf/apps/nm-applet-backup

```

then, go to system -> preferences -> startup applications. verify that "network manager" has a checkbox next to it that is checked.

then log out, and back in.


if all of that doesn't work, please think back and try to recall what unusual things you may have been doing prior to this problem presenting itself - and share it with us.

---

### Post by wstay on 2010-08-18
I find that I have to 'log out' and 'log in' to the other user, to get the Network Manager applet to appear on either users' panel on the desktop. If I use 'switch user' to get into the other user, then the Network Manager applet appears on only one of the user's panel on the desktop and not the other.

---

### Post by dineshs on 2010-08-18
Have you tried this
[http://ubuntuforums.org/showthread.php?t=1545744](http://ubuntuforums.org/showthread.php?t=1545744)
or this
[http://ubuntuforums.org/showpost.php?p=9631393&postcount=7](http://ubuntuforums.org/showpost.php?p=9631393&postcount=7)

---

### Post by wstay on 2010-08-19
The above two links do not help.
I just have to log-out and then log-in to the other user in order to get the Network Manager applet appears on the panel on the Desktop of either one of the users I am logged-in. That would means closing any open applications on the Desktop of the User logging-out.
It would be better if we can get the Network Manager applet appears on the panel on the Desktop of either one of the users whenever we use Switch-User.
If I am not mistaken (I am not sure), while I was using Ubuntu 8.10, I could use Swtich-User and get the Network Manager applet appears on the panel on the Desktop of any one of the users whoever user I was switching-to.

---

### Post by wstay on 2010-08-20
> **earthpigg said:**
> this is kind of a shot in the dark, but try these three commands:

```
mv ~/.gconf/apps/gnome-settings/gnome-panel ~/.gconf/apps/gnome-settings/gnome-panel-backup

mv ~/.gconf/apps/panel ~/.gconf/apps/panel-backup

mv ~/.gconf/apps/nm-applet ~/.gconf/apps/nm-applet-backup

```

then, go to system -> preferences -> startup applications. verify that "network manager" has a checkbox next to it that is checked.

then log out, and back in.


if all of that doesn't work, please think back and try to recall what unusual things you may have been doing prior to this problem presenting itself - and share it with us.

Would you say if I format and install a new copy of Ubuntu 9.10, then I won't have this problem?

---

### Post by wstay on 2010-08-20
Under System > Administration > Users and Groups, how can I or can I enable 'root' in the Users Settings for use whenever I restart my computer in the Login screen.This is to see if the Network Manager applet appears on the panel on the Desktop of both the Root Desktop and my Desktop if I use Switch-User after I have logged in.

---

### Post by earthpigg on 2010-08-20
> **wstay said:**
> Would you say if I format and install a new copy of Ubuntu 9.10, then I won't have this problem?

i hope so. that would indicate that you (or another administrative user) may have misclicked at some point but don't recall it.

if you want to try enabling root, take a look [here]("https://help.ubuntu.com/community/RootSudo"). and, note this:

> Enabling the root account is rarely necessary. Almost everything you need to do as administrator of an Ubuntu system can be done via sudo or gksudo. If you really need a persistent root login, the best alternative is to simulate a root login shell using the following command...

---

### Post by varunendra on 2010-08-21
I just created an additional user with administrative rights & experienced this problem (am assuming yours is same):

[LIST]
[*]Whichever user I log into first gets the nm-applet.
[*]If I switch to the other user (without logging off the first one) there will be no nm-applet. The command nm-applet --sm-disable (with or without sudo) would return this- "an instance of nm-applet is already running". Useless!
[*]If I log off the first user & then log onto the other (fresh log on, not to one that is already logged-on), the applet will be there.
[/LIST]
So I searched & found it to be [**a longstanding bug**]("https://bugs.launchpad.net/fedora/+source/network-manager/+bug/284596") (since intrepid- it seems) reported & confirmed over & over again. (pay special att. to post #40, 44, 45, 46).

Accordingly, I'd suggest to just use Wicd instead of NM.

---

### Post by Darkness Des on 2010-08-21
+1 to Wicd. Once I switched, I never looked back.

---

### Post by wstay on 2010-08-24
Quote:> 
Enabling the root account is rarely necessary. Almost everything you need to do as administrator of an Ubuntu system can be done via sudo or gksudo. If you really need a persistent root login, the best alternative is to simulate a root login shell using the following command...
__________________
Semper Fi

What is the difference between using sudo or gksudo command?
When should we use sudo or gksudo command?

---

### Post by earthpigg on 2010-08-24
> **wstay said:**
> Quote:

What is the difference between using sudo or gksudo command?
When should we use sudo or gksudo command?

99.9999% of the time, you can use sudo and be ok.

when you type sudo whatever, you are asked in the terminal for your password.

when you type gksudo or gku, a graphical box pops up asking for your password.


ummm, yeah. there are other differences. i dont remember what they are and have never found them relevant.

---

### Post by varunendra on 2010-08-24
> **wstay said:**
> Quote:

What is the difference between using sudo or gksudo command?
When should we use sudo or gksudo command?

There is a minor but quite significant difference that suggests 'you should **Never** use sudo for GUI apps'. Explained [here]("https://help.ubuntu.com/community/RootSudo").

---

### Post by wstay on 2010-11-13
> **Darkness Des said:**
> +1 to Wicd. Once I switched, I never looked back.

I installed WICD from the Synatic Package Manager.
I can use it for wired connection.
I can see my connection from whichever user I switch to.
It cannot be use for my wireless connection.
Is there something else like WICD or something better to install say from the Synatic Package Manager for my wireless connection?

---

