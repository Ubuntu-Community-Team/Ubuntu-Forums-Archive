---
title: "Deluge won't show up"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by Jouke S on 2011-02-27
Hey, 

I have Deluge installed and it's working fine, adding torrents works as it's supposed to and it downloads fine too. 
Problem is that it will not show up no matter what I do.
I'm not getting a Deluge entry in the bottom bar, nor does it show up if I minimize programs. 
alt+f2 -> deluge doesn't work either. 
It -does- download and upload while I can't access the actual GUI. 

Hope someone can help me with this, it's quite annoying

---

### Post by davidmohammed on 2011-02-27
how did you install deluge?

If you cant see the GUI, how are you downloading torrents?

---

### Post by Jouke S on 2011-02-27
> **davidmohammed said:**
> how did you install deluge?

If you cant see the GUI, how are you downloading torrents?

Oh, guess I should have added that

If I open a .torrent file it shows me the regular process of adding a torrent (selecting which files you want and clicking Add), after that the window disappears again.
I believe Deluge came pre-installed with Ubuntu 10.10

---

### Post by davidmohammed on 2011-02-27
deluge isnt the default in maverick - it is "transmission"

see here how to install from a [ppa]("http://www.techdrivein.com/2010/11/how-to-install-deluge-131-in-ubuntu.html").

If you start deluge from a terminal session - are there any errors displayed after you add the torrent file?

---

### Post by Hedgehog1 on 2011-02-27
If Deluge is running fine, but not showing up in the buttons on the bottom - that is normal.

In the notifications item (installed in the top panel by default, also shows sound and network icons), there is a blue water drop that you can click on to bring up the deluge GUI.

If, however, you don't have the notification item on a panel, well, you need to add it when using either bit torrent client.

So look for the blue water drop next to the sound and network icons...

:KS

---

### Post by Jouke S on 2011-02-27
> **davidmohammed said:**
> deluge isnt the default in maverick - it is "transmission"

see here how to install from a [ppa]("http://www.techdrivein.com/2010/11/how-to-install-deluge-131-in-ubuntu.html").

If you start deluge from a terminal session - are there any errors displayed after you add the torrent file?
I didn't know how to run something from a terminal so I went ahead and uninstalled Deluge via Synaptic and follow the steps on the link (sudo add-apt-repository ppa:deluge-team/ppa
sudo apt-get update 
sudo apt-get install deluge)
When I came to install deluge I encountered the following error:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Jouke S on 2011-02-27
> **Hedgehog1 said:**
> If Deluge is running fine, but not showing up in the buttons on the bottom - that is normal.

In the notifications item (installed in the top panel by default, also shows sound and network icons), there is a blue water drop that you can click on to bring up the deluge GUI.

If, however, you don't have the notification item on a panel, well, you need to add it when using either bit torrent client.

So look for the blue water drop next to the sound and network icons...

:KS
The panel item didn't bring up the window either, though I may have used the wrong panel? I believe I've added the panel via Applications - Internet and then right click.

---

### Post by Jouke S on 2011-02-27
Sorry for the triple post, the 'unable to lock directory' error is no longer an issue.
I got it working by restarting X (ctrl alt backspace). When adding a new torrent Deluge still doesn't show up, however. 
I now understand that this is meant to happen but I would still like to know how I can get to open up properly :D

thanks

---

### Post by Jouke S on 2011-02-27
Still haven't figured it out.
(bump - no longer on first page)

---

### Post by davidmohammed on 2011-02-28
Open a terminal session via Accessories - terminal

then type

deluge-gtk

this should start deluge.  Are there any errors observed in the terminal session?  If so, copy and paste the output here in a reply between [CODE] tags.

---

### Post by Juvencio on 2011-06-02
[B]In 10.10 and below just see System Tray Notification top right.
But nothing will show on 11.04[/B]

**[SIZE="4"]How To Enable System Tray Notification For All Applications In Ubuntu 11.04[/SIZE]**
By Farshad on May 28 2011

[http://www.addictivetips.com/ubuntu-linux-tips/enable-system-tray-notification-for-all-applications-in-ubuntu-11-04/]("http://www.addictivetips.com/ubuntu-linux-tips/enable-system-tray-notification-for-all-applications-in-ubuntu-11-04/")

System tray notifications were just recently enabled in Ubuntu Unity. Unfortunately, the system tray option is not available for many applications and merely works with a few apps such as Mumble, java applications and Wine. In this post we will tell you how to enable system tray for all applications.

Open a Terminal window and enter the below command:

[PHP]gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"[/PHP]

After that, you can whitelist a certain application if you want, by using the command below. In the given command, make sure you replace “YOUR_APPLICATION”, with the applications name which you wish to add to the whitelist.

**USE THIS FOR OTHER APPLICATIONS**
[PHP]gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'YOUR_APPLICATION']"[/PHP]
[B]
USE THIS FOR DELUGE[/B]
[PHP]gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'Deluge']"[/PHP]

Log out and login back for the changes to take effect.

Hope this helps

---

### Post by Cas07 on 2011-06-04
Deluge 1.3.1 in the official Ubuntu repo is supplied with an App Indicator so does not require being whitelisted.

---

### Post by Mamoth on 2011-07-23
Hello.

I am under Lucid 64 bits.

I have the same problem : Deluge works, but not its GUI. The blue drop in the notification area is there and seems to work fine. But any time I try to show up the GUI (by clicking the drop, by right-cliking it and choosing 'show deluge', by typing deluge-gtk in a terminal), it simply does not show up at all and I have no error message.

Now, it used to work fine until recently when I got a problem with X server. I'll skip the details of how it happened, but now my problem with X server is that :

[LIST]
[*]Configuration of X server is locked on "Separate X screen" (I cannot change it in the Nvidia settings GUI).
[*]I have an error message at boot saying ```
Could not apply the stored configuration for monitors. X server does not support the requested size
```.
[/LIST]
So I suspect the GUI does not show up because of this problem, and that when I'll solve it , I'll solve both at the same time.

---

