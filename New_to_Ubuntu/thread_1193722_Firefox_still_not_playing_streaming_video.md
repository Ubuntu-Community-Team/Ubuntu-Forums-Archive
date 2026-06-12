---
title: "Firefox still not playing streaming video"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by FormatSeize on 2009-06-21
I've tried many things to get firefox to play video, but as of yet nothing has worked. I've searched, and Googled, and searched some more, but they just won't play.

Firefox will say that it is "Transferring data from <site>, but the player in which the video should be playing is blank. When I right click where the video should be, it says that it is playing, but I see nothing.

In the Terminal I used to open Firefox, it says:
```

Unhandled Error 19
```.

Is there something that I am doing wrong or have missed. I have installed a lot of packages related to video (or what my limited knowledge has led me to install), but none of them are doing the trick.

Any help is appreciated
KLB.

---

### Post by andrew.46 on 2009-06-21
Hi FormatSeize,

> **FormatSeize said:**
> I've tried many things to get firefox to play video, but as of yet nothing has worked. I've searched, and Googled, and searched some more, but they just won't play.

Can you post an address of a video stream that has failed on your system?

Andrew

---

### Post by FormatSeize on 2009-06-21
> **andrew.46 said:**
> Hi FormatSeize,



Can you post an address of a video stream that has failed on your system?

Andrew

Here's an example
```

http://www.youtube.com/watch?v=rHa6h2XYv1U&feature=featured
```.

---

### Post by izizzle on 2009-06-21
Do you have flash installed and are you sure it is working properly?

---

### Post by FormatSeize on 2009-06-21
> **izizzle said:**
> Do you have flash installed and are you sure it is working properly?

I'm pretty sure I do. I installed the non-free version as well. That was sometime this morning, and I have rebooted several times since then. Is there some other flash that I should have installed? Is there something that I should uninstall? 

How do I check to make sure I have the correct flashplayer installed?

---

### Post by wpshooter on 2009-06-21
If you have the flash plugin from Synaptic installed you need to UNINSTALL that first, reboot and then go to the "REAL" Adobe website and download the tar version of Adobe Flashplayer for Linux and then install it.  If you need installation directions, please write back.

---

### Post by FormatSeize on 2009-06-21
> **wpshooter said:**
> If you have the flash plugin from Synaptic installed you need to UNINSTALL that first, reboot and then go to the "REAL" Adobe website and download the tar version of Adobe Flashplayer for Linux and then install it.  If you need installation directions, please write back.

Yes. I need uninstall and install directions.

Thanks a lot.

---

### Post by wpshooter on 2009-06-21
First do a search in Synaptic for something like "flash plugin".  I think it is listed as Flash plugin non-free.  If you have it installed then the box to the left should be green.  Click on the green box and choose mark for removal (not complete removal).  The apply it.

Let us know when you have that done and have rebooted.

---

### Post by wpshooter on 2009-06-21
After they get that done, can someone else help them get the tar version of Adobe Flashplayer for Linux properly installed thru the terminal.  I have been up since 4 o'clock this morning and I have got to get some sleep.

---

### Post by FormatSeize on 2009-06-21
I've uninstalled the flash players from Synaptic. I also uninstalled the Shock wave players as well. And rebooted.

---

### Post by Jcdlvsrbld on 2009-06-21
i had this prob for a while. uninstall the plugins and install only one plugin for each type. you also need to make sure that the latest version of sun java is installed

---

### Post by FormatSeize on 2009-06-21
> **Jcdlvsrbld said:**
> i had this prob for a while. uninstall the plugins and install only one plugin for each type. you also need to make sure that the latest version of sun java is installed

I see that I don't have the Sun Java installed, but there are 5 in my Synaptic. Which one is the latest one?

---

### Post by FormatSeize on 2009-06-22
It's working now. 
Thanks for all of your help.

How do I put one of those [SOLVED] tags on the thread?

---

### Post by Hutto on 2009-06-24
Save this code somewhere for flash player install on firefox AMD64

echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing Flash Player 10"
cd ~
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz)
tar zxvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 

echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

# now doing some cleaning up:
sudo rm -rf libflashplayer.so 
sudo rm -rf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz

---

