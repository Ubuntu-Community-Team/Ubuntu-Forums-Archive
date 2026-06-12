---
title: "text boot"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by tnt87 on 2011-02-23
hey

i have installed elegant gnome trying to get a nice theme i saw. downloaded it, installed it and it asked me to reload. now 10.10 will only load in text mode. i dont know how to get it back. i have re-installed ubuntu 3 times now due to this problem but because i didnt know where it was coming from i could report the issue. 

specs nividia graphics card... asus ul30vt.

Can anyone help? thanks.

---

### Post by robsoles on 2011-02-23
If you do something 'clever' with something to do with video or GUI and then on restart you land in a text only situation then use the text-only situation to move or remove /etc/X11/xorg.conf and reboot - about 9 out 10 times your system will restart into the GUI for you.

To move it```
sudo mv /etc/X11/xorg.conf ~/borked-X11-xorg.conf
```(New location becomes your home folder named as 'borked-X11-xorg.conf')

To remove it```
sudo rm /etc/X11/xorg.conf
```


If you are reinstalling Ubuntu and still having the problem that made you reinstall then it sounds like you are reinstalling 'over' the top of the existing system and retaining the bad config file(s) - for a nice healthy reinstall where you want to retain your data you should pretty much delete everything except /home from the target file-system.

---

### Post by tnt87 on 2011-02-26
firstly i need to apologise to elegant gnome. i thought it was the problem when it was actually the nvidia driver up date. so after re-installing ubuntu... yet again. i am now faced with the issue of running my nvidia vga. will need it for running graphically intense software when i get back to uni.

Thanks for the help Robsoles. I will keep for code on file in case i have a similar problem.

I think it is a Geforce210M Nvidia card if this helps at all.

---

### Post by deconstrained on 2011-02-26
> **tnt87 said:**
> firstly i need to apologise to elegant gnome. i thought it was the problem when it was actually the nvidia driver up date. so after re-installing ubuntu... yet again. i am now faced with the issue of running my nvidia vga. will need it for running graphically intense software when i get back to uni.
Been there done that.

Use the latest proprietary NVidia driver provided through Canonical. It may not be the bleeding edge latest-from-Nvidia but it's been thoroughly tested for stability and all nicely packaged for seamless integration.

Also, when I saw the title of the thread I just felt like sharing this, which isn't directly related to your problem but is awesome and worked for me:
[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

