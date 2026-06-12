---
title: "nm-applet Keeps Popping Up"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by e.honda on 2008-05-12
I have a problem, whenever I boot up my computer and login to my desktop, I immediately get a popup message that says:

"Enter Password for default keyring to unlock
 - The application 'nm-applet' (/usr/bin/nm-applet) wants to access the default keyring, but it is locked"

Then it has an option for me to enter the password or deny it.

I think it has something to do with network manager application. If I deny it, I don't get internet. If I enter my password, I get internet. I am using WPA Personal, I entered my key and setup AES-CCMP as the type. 

I don't want the nm-applet message to pop up, I just want to boot up normally and connect to the internet. How can I fix this?

Gateway Laptop 3018GZ
Xubuntu 8.04
xfce-desktop

--
UPDATE:
I tried installing libpam-gnome-keyring and adding the following 2 lines at the end of the gdm file(/etc/pam.d), but the problem still persists.
```
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so
```
I've been searching all day trying to find a fix but so far most of them is for Ubuntu and NOT Xubuntu.

I've read a blog [here]("http://mexpolk.blogspot.com/2008/02/ubuntu-change-default-keyring-password.html") where a user has to install 'seahorse' and configure it.....but unfortunately I've also tried that method but no luck because there was no tab for 'GNOME Keyring'....I'm using xfce so I assume it won't provide me with that.

--
UPDATE 2:
I also tried what [this]("http://ubuntuforums.org/showthread.php?t=792779") person suggested by manually configuring and disabling roaming mode, but again it didn't work. That will only disable my wireless network which is not what I want.

I've also tried deleting the default.keyring located at (.gnome2/keyrings) and start from scratch but didn't work. I hope I can draw some of your attention. This is very annoying.

---

### Post by e.honda on 2008-05-13
Anyone care to help?

---

### Post by matthewboh on 2008-05-13
I am also having the same problems and have tried the same solutions as you - just thought I'd chime in on this and get myself subscribed

---

### Post by e.honda on 2008-05-13
Note: Before doing this, make sure you copy and save all of this to your text editor because you will lose your internet connection, unless you have a wired connection you don't have to worry. All the info that is stated and quoted is located here:
```
http://wicd.sourceforge.net/wiki/doku.php?id=faq
```
> Installing Wicd in Ubuntu

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras 

where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy). Then, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd. Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily.

In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). For the command, enter "/opt/wicd/tray.py".

In KDE, you'll need to make a desktop file, so see this post for the directions on how to fix it up. 

- How can I get the tray icon to appear?

* In XFCE (Xubuntu etc), run the Autostarted Applications tool (under Settings) and then Add entry for “WICD WiFi control” and then put “/opt/wicd/tray.py” as the command (1.3.x or later). (Tested with XFCE 4, reconnects on login). 

- How do I get Wicd to recognize my wireless card?

In the main window, click the “Preferences” window. Make sure your card is listed beside “Wireless Interface”. Some common values are wlan0 and eth1. You can adjust your WPA settings here as well.

**sources:** [http://wicd.sourceforge.net/wiki/doku.php?id=faq](http://wicd.sourceforge.net/wiki/doku.php?id=faq)
That fixed my problem. During the installation, synaptic package manager warned me that wicd is not signed/authenticated and it gave me info about the risks of installing it. Anyway, I assume it's safe to install because a lot of people have used and approved it.

Good luck to all.....

---

### Post by jimmurdock on 2008-05-13
e.honda,
I have the same problem with the nm-applet popping up.  My problem started when I installed PCLinuxOS on another partition.  I disabled the password in the bootup process and for both Ubuntu and pclos and then the nm-applet popup started occuring in Ubuntu - doesn't happen in pclos.  Since I just bought a Dell Inspiron 1525 with Ubuntu and they "have" a special tech support number for Ubuntu, I called and they told me to go to the Ubuntu forums for help.  Very satisfying.

My Ubuntu is version 7.1 - I don't know anything about the gutsy, hardy etc and I am using 128 bit WEP encryption which has worked fine in WinXP Pro and in WinXP Home for my wife.  I want to change as little as possible in the as delivered OS.  I read your solution but your setup sounds different than mine so I'm still looking for help.

---

### Post by darco on 2008-05-13
try this worked for me!

[http://ubuntuforums.org/showthread.php?t=776176](http://ubuntuforums.org/showthread.php?t=776176)

good luck
darco

---

### Post by Bubba64 on 2008-05-13
This only happens to me when I have my computer set to roam, which is what I did to get easy access to my own network. With manual configuration I am on the net with no key permissions.

---

### Post by e.honda on 2008-05-13
> **jimmurdock said:**
> e.honda,
I have the same problem with the nm-applet popping up.  My problem started when I installed PCLinuxOS on another partition.  I disabled the password in the bootup process and for both Ubuntu and pclos and then the nm-applet popup started occuring in Ubuntu - doesn't happen in pclos.  Since I just bought a Dell Inspiron 1525 with Ubuntu and they "have" a special tech support number for Ubuntu, I called and they told me to go to the Ubuntu forums for help.  Very satisfying.

My Ubuntu is version 7.1 - I don't know anything about the gutsy, hardy etc and I am using 128 bit WEP encryption which has worked fine in WinXP Pro and in WinXP Home for my wife.  I want to change as little as possible in the as delivered OS.  I read your solution but your setup sounds different than mine so I'm still looking for help.

You have version 7.1? It's best if you update it so you will get the latest new changes and security patches. The new version is 8.04 Hardy and I believe that Gutsy is version 7.1 which is what you have. Your old version configuration files may be different than mine since I have the new release. Although I could be wrong but it shouldn't be that different than mine.

If you read my first post, I forgot to mention that I reverted my changes to the configuration files and I set all of them back to default to avoid confusion. I uninstalled seahorse and libpam-gnome-keyring.

Anyway once you install the program Wicd. You need to add the icon to your tray. Open it and there should be an "advance tab".....from there you can type in your 128 bit WEP key, also make sure you check 'automatically connect to the network' then restart the computer.

If you have trouble installing just post here or make another new thread.

---

### Post by Agent86 on 2008-06-05
On my fresh install of Xubuntu 8.04 Hardy, I was able to stop nm-applet from asking for my password just by installing libpam-gnome-keyring
```
sudo apt-get install libpam-gnome-keyring
```I did NOT edit /etc/pam.d/gdm

The next boot after I installed it, I was asked for the keyring password again, but this time I was given an option to save the password. I entered the password, checked the box to save the password, and that was it. I haven't had to enter the password since then. My login and keyring passwords were identical, though that may not matter.

---

### Post by kalasoka on 2010-03-16
I had recently installed XUbuntu 9.10. Initially I was able to connect to Internet through my USB modem using the NetworkManager Applet. However, *something* happened after that. (I had downloaded and installed a few other packages.) And now, it's not connecting! More strangely, it is not even showing that dialog box related to 'default keyring locked'. 

As a consequence, I have once again returned to good old wvdial, which I used with XUbuntu 8.04. Wvdial is a really small and great program, and you don't get all these headaches there.

---

