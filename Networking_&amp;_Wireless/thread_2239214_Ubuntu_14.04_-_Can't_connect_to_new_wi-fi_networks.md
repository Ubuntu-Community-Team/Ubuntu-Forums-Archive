---
title: "Ubuntu 14.04 - Can't connect to new wi-fi networks"
date: 2014-08-12
forum: Networking &amp; Wireless
---

### Post by tatianeps2 on 2014-08-12
After the upgrade to Ubuntu 14.04, my notebook won't connect to new wi-fi networks. The output of the wireless_script is attached as [ATTACH]255422[/ATTACH].

When I try to connect to a new wi-fi network Ubuntu throws this message: "(1) Creating object for path '/org/freedesktop/NetworkManager/ActiveConnection/1' failed in libnm-glib."

[ATTACH=CONFIG]255421[/ATTACH]

I noticed that the files for the new connections at /etc/NetworkManager/system-connections/ don't have the psk field under [802-11-wireless-security]. If I sudo gedit to open one of this files and add manually the psk field with the password, then I can connect. It's an ugly workaround though. I'm still looking for a solution.

---

### Post by varunendra on 2014-08-13
The smarter way to save the security key, along with other settings is to do it via Network Manager settings (nm-applet menu > "Edit Connections" > "Wireless" tab > double-click your connection > "Security" tab). That is the frontend to handle those key files.

Assuming something might have broken in Network Manager installation while upgrading, you may try to completely purge it, then re-install it. To download the packages in advance (since you'll lost internet connection as soon as you purge it) -
```
sudo apt-get install -d --reinstall network-manager network-manager-gnome
```
Then to purge it -
```
sudo apt-get purge network-manager-gnome network-manager
```
To reinstall it (I suggest a reboot in-between) from the downloaded packages, simply -
```
sudo apt-get install network-manager-gnome
```

---

### Post by tatianeps2 on 2014-08-13
Thanks, Varunendra! 
It's working now. =D

---

### Post by varunendra on 2014-08-13
You're welcome! :)

---

### Post by jay64 on 2014-11-01
> **varunendra said:**
> The smarter way to save the security key, along with other settings is to do it via Network Manager settings (nm-applet menu > "Edit Connections" > "Wireless" tab > double-click your connection > "Security" tab). That is the frontend to handle those key files.

Assuming something might have broken in Network Manager installation while upgrading, you may try to completely purge it, then re-install it. To download the packages in advance (since you'll lost internet connection as soon as you purge it) -
```
sudo apt-get install -d --reinstall network-manager network-manager-gnome
```
Then to purge it -
```
sudo apt-get purge network-manager-gnome network-manager
```
To reinstall it (I suggest a reboot in-between) from the downloaded packages, simply -
```
sudo apt-get install network-manager-gnome
```

Terminal says that d in -d isn't known.

---

### Post by Bucky Ball on 2014-11-01
@jay64: Welcome. Try pasting the commands in if you didn't do that the first time and please start a new thread with a descriptive title and outline what your issue is, what you've tried, what release and flavour of Ubuntu you are using, and any other relevant details. It will improve your chances of support as this thread was started by someone else and is solved. Good luck. ;)

@tatianeps2: Good news. Please follow the second link in my thread to help others. Thanks.

---

### Post by polochamps on 2015-03-06
> **varunendra said:**
> The smarter way to save the security key, along with other settings is to do it via Network Manager settings (nm-applet menu > "Edit Connections" > "Wireless" tab > double-click your connection > "Security" tab). That is the frontend to handle those key files.

Assuming something might have broken in Network Manager installation while upgrading, you may try to completely purge it, then re-install it. To download the packages in advance (since you'll lost internet connection as soon as you purge it) -
```
sudo apt-get install -d --reinstall network-manager network-manager-gnome
```
Then to purge it -
```
sudo apt-get purge network-manager-gnome network-manager
```
To reinstall it (I suggest a reboot in-between) from the downloaded packages, simply -
```
sudo apt-get install network-manager-gnome
```

It also worked for me.

Thank you!

---

### Post by gcolbourn on 2015-08-26
Hi, This doesn't work for me. Ubuntu 15.04, Wifi keeps disconnecting and coming up with the same error message when I click on the network name in the menu. Only way I can connect is retyping the network name and password with "Connect to Hidden Wifi Network..." It then disconnects anywhere from a minute to a couple of hours later.

---

### Post by johnnyaug on 2015-09-01
> **gcolbourn said:**
> Hi, This doesn't work for me. Ubuntu 15.04, Wifi keeps disconnecting and coming up with the same error message when I click on the network name in the menu. Only way I can connect is retyping the network name and password with "Connect to Hidden Wifi Network..." It then disconnects anywhere from a minute to a couple of hours later.

Same here.

---

### Post by lordnemo on 2015-12-03
Fix doesn't work for me as well, started after upgrade from 15.04 to 15.10. Gets really annoying having to restart network manager every 5-10 minutes when my connection dies.

---

### Post by Bucky Ball on 2015-12-03
To all of those posting on this old and dead thread: If you want support please post a new thread with a descriptive title. You do your chances of support no good by posting on a thread that was solved and has seen no action apart from 'this didn't work' since last November.

If this didn't work for you, then you probably don't have the same issue. They rarely are the same as there are so many variables. 

Thanks and good luck.

*Thread closed.*

---

