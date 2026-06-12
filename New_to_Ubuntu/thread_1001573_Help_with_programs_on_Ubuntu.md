---
title: "Help with programs on Ubuntu"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Timslin on 2008-12-04
I was getting confused in the iRC earlier so that I'd come here and ask. I would like to use Media Player Classic, Winrar and uTorrent on Ubuntu. I am well aware that there are Linux equivalents which I will eventually use but would like to have these programs on the OS to start until I get used to the equivalents.

I've got uTorrent to install through Wine and will eventually like to know how I install the uTorrent WebUI but for now can anybody please help me install Winrar and Media Player Classic.

---

### Post by Michael.Godawski on 2008-12-04
Face your fear...

install the linux versions. It will become awfully complicated when you try to run you beloved windows application through wine, which might get you from the Ubuntu path.

Fire up the terminal and run

```
sudo apt-get install ubuntu-restricted-extras
```

this should install the essential codecs and applications like unrar, java and stuff like flash.

There are many torrent applications for linux. If you use the latest version 8.10 why not try out Transmission?

For the Media Player I can recommend vlc. Just search for it in the add/remove application.

For further reading on media formats have a look at:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Michael.Godawski on 2008-12-04
This might also be helpful:

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

---

### Post by Timslin on 2008-12-04
So how would I unrar .rar files? The Archive Manager will not allow it.

---

### Post by nothingspecial on 2008-12-04
If you haven`t already, in your menus go to System > Administration > Software Sources and enable the universe and multiverse repositories. Reload/update when prompted.

Then open synaptic package manager, also in System > Administration and search for rar. Make sure "All" is selected in the left hand window.

---

### Post by AllanPoe on 2008-12-04
You can install Winrar through Wine. This is what I did. Works perfectly.

---

### Post by philinux on 2008-12-04
Deluge-torrent I find is very slick. It's in the synaptic package manager to.

Install the ubuntu-restricted-extras package from synaptic for unrar etc.

---

