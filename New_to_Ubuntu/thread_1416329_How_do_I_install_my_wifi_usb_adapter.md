---
title: "How do I install my wifi usb adapter??"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by LinuxNoob J on 2010-02-25
[COLOR=DarkRed][SIZE=2]Hi, I just installed Ubuntu a couple hours ago and am totally confused already! In XP, when I plug in my usb adapter, the new hardware wizard pops up, etc., etc..When I do so in Ubuntu, I see no notifications, and don't know where to go to install it manually. I've got the Alfa AWUSO36H, which does include linux drivers on CD. Also, when I insert the cd, I noticed there's no autorun like I've been used to...I see the CD show up on the desktop and can open it to explore the files. I see the folder that contains the linux driver, but I just don't know what to do from there?? Any help would be greatly appreciated, thanks in advance. 

-J 
[/SIZE][/COLOR]

---

### Post by Ozymandias_117 on 2010-02-25
First thing I would try is going to System > Administration > Hardware Drivers. Most wireless cards can be enabled through there. (That's the simplest/easiest way)

---

### Post by dadgetboy on 2010-02-25
Copy the folder containing the Linux driver(s) to your home folder.
CD to the folder.
Look for a .deb file double click and install; if not found:

Look for a .run file and right click and set the permissions for executing.

```
sudo ./nameoffilehere.run
```

If a .run file is not found:

Find a tar.gz or tar.bz2 and extract it;
 then following commands and lemme know:
```


sudo ./configure

sudo make

sudo make install
```

if this does not work:

**[http://tinyurl.com/txpku](http://tinyurl.com/txpku)**

download the Linux driver and install it using the above commands.

---

### Post by superfrogman94 on 2010-02-25
Did You Go To Hardware Drivers?

System > Administation > Hardware Drivers

I think you need the rtl8187 driver

if you cant get that working you can try to use ndiswrapper to use the windows driver.

install it with:
```
sudo apt-get install ndiswrapper-common
```you should also install ndisgtk from the software center to make this much easier to use (gives you graphical interface instead of command line)

---

### Post by LinuxNoob J on 2010-02-26
[SIZE=3]Wow, excellent forums...I didn't expect such quick replies. About to crash for the night now, will try the suggestions tomorrow and post back..Thank all of you for the tips![/SIZE]

---

### Post by 3rdalbum on 2010-02-26
The first thing you should check is if the device is recognised and usable from Network Manager (it's the little icon to the left of your clock). Left-click it, twenty seconds after plugging in the USB device, and see if it's picking up any networks.

Most drivers on Linux are built-in. In fact, having Linux drivers on the CD often means that you already have the drivers in the kernel.

If there's no joy from Network Manager, try the Hardware Drivers panel as previously suggested.

---

### Post by LinuxNoob J on 2010-02-26
[SIZE=2]Thanks to the last post, I did check and find that Ubuntu was recognizing my adapter. I see the available networks as usual and can connect..but, I can't go anywhere. When I launch firefox, it comes up as if I have no connection. This happens when I connect to my own wifi, and also a couple other open networks?? Also, it seems that the adapters range and connection quality/strength is pretty poor..i switch back to XP and it works fine. I'm thinking maybe because Ubuntu is assigning a generic driver to the adapter [/SIZE], [SIZE=2]maybe? If so, can I disable that driver and assign the proprietary one (on the CD)?[/SIZE]

---

### Post by Knapweed on 2010-05-30
> **LinuxNoob J said:**
> [SIZE=2]Thanks to the last post, I did check and find that Ubuntu was recognizing my adapter. I see the available networks as usual and can connect..but, I can't go anywhere. When I launch firefox, it comes up as if I have no connection. 

I had these exact same symptoms. The solution turned out to be embarrassingly simple: move the adapter farther from your router. If the Alfa is too close to the access point, the signal seems to overwhelm it.

Cheers.

---

