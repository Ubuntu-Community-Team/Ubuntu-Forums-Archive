---
title: "Flash problems"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by sorbeth on 2010-02-10
Hi, I'm new to Ubuntu but I really like it.  Unfortunately I'm having some troubles.

I have the 8.04 (dell) netbook version with 3.0.5 firefox.  I tried to install flash 10 but got the libnspr4-dev error.  I tried looking up solutions and did the uninstall for the non-free flash and tried installing the download again, and now I have no flash at all.  I do not have the libnspr4-dev in synaptic to add it there and when I try to use the synaptic to add the non-free flash back in I just get an error.

I'm really at a loss here.  How can I get Flash 10 on my netbook?  

Thank you!

---

### Post by HappyFeet on 2010-02-10
Get rid of any flash you have, and go here [http://get.adobe.com/flashplayer/?promoid=DXLUJ](http://get.adobe.com/flashplayer/?promoid=DXLUJ) and download the .tar.gz flash file. Right click it and **extract here**. You will be left with **libflashplayer.so** file.

Do
```
gksudo nautilus
```
then just copy and paste libflashplayer.so into /usr/lib/mozilla/plugins

---

### Post by sorbeth on 2010-02-10
Thank you Happy Feet.  I have that file in the mozilla/plugins folder.  I restarted my computer but still no flash.

I'm guessing there is something obvious that I should do... but I really don't know what.  What would I need to do to finish this?

---

### Post by tom.swartz07 on 2010-02-10
> **sorbeth said:**
> Thank you Happy Feet.  I have that file in the mozilla/plugins folder.  I restarted my computer but still no flash.

I'm guessing there is something obvious that I should do... but I really don't know what.  What would I need to do to finish this?

Heyo.

Open your browser and see if it recognizes the plugin.

type 

```
about:plugins
```
into the address bar, and see if it lists adobe flash player.


You can, alternatively, simply install ubuntu-restricted-extras package from the software center and it should take care of all of the heavy duty work.

---

### Post by no2498 on 2010-02-10
do as tom said

You can, alternatively, simply install ubuntu-restricted-extras package from the software center and it should take care of all of the heavy duty work.

---

### Post by sorbeth on 2010-02-10
Firefox doesn't recognize flash as being there when I use about: plugin in the address bar.  When I tried the update I get a bunch of error messages, I think relating to IP addresses.

Not sure what to do here. :(

---

### Post by Crossbow on 2010-02-10
Hey, I am having the exact same problem. I have tried uninstalling and reinstalling everything with the words flash, player, or adobe, multiple times! 

I WAS working just fine. I don't know what changed, but the other day I was suddenly unable to use flash. The applications said I had the Adobe Flash Plugin, but it wasn't showing in the browser's plugins, and only shockwave is showing when I do about:flash. And shockwave is not working with what I'm trying to watch. 

When I try to install from the Adobe site, I get the message that a newer version is already installed.

I already had the ubuntu-restricted-extras installed. I uninstalled and reinstalled that too.

PS. This isn't just in Firefox. I'm having the same problem with Google Chrome, Epiphany, and Konqueror.

---

### Post by sorbeth on 2010-02-10
I don't think I have a 'Software Center' (or a 'Ubuntu Software Center'), I do have an 'Add/Remove software' but when I used that I got error messages that looked like it was not connecting with the right IP address.

---

### Post by sandyd on 2010-02-10
> **sorbeth said:**
> I don't think I have a 'Software Center' (or a 'Ubuntu Software Center'), I do have an 'Add/Remove software' but when I used that I got error messages that looked like it was not connecting with the right IP address.

only 9.10 has the ubuntu software center.

have you tried running
```

sudo apt-get update
```?

p.s. theirs a lot of people running around with repo IP problems lately...
wonder whats up with that?

---

### Post by Crossbow on 2010-02-10
> **carlee said:**
> only 9.10 has the ubuntu software center.

have you tried running
```

sudo apt-get update
```?

p.s. theirs a lot of people running around with repo IP problems lately...
wonder whats up with that?

I just did that. What was it supposed to do? It didn't change anything.

I wish someone would just tell me what applications I should have and not have.

---

### Post by sandyd on 2010-02-10
if that doesnt work,
run this
```

gksudo gedit /etc/apt/sources.list

```
Do this for all lines that are in this format: (the xx is the country code, just ignore it)
[http://xx.archive.ubuntu.com](http://xx.archive.ubuntu.com)

replace
```

http;//xx.archive.ubuntu.com

```
with
```

http://archive.ubuntu.com
```

---

### Post by sandyd on 2010-02-10
> **Crossbow said:**
> I just did that. What was it supposed to do? It didn't change anything.

I wish someone would just tell me what applications I should have and not have.

that was for the other guy w/ IP problems.
or whoever just posted about IP problems in the thread.

---

### Post by Crossbow on 2010-02-10
(never mind)

---

### Post by sandyd on 2010-02-10
install flash properly....
```

sudo rm /var/lib/dpkg/info/adobe-flashplugin*
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
tar xvfz install_flash_player_10_linux.tar.gz
sudo mv *.so /usr/lib/firefox/plugins/ 
rm install_flash_player_10_linux.tar.gz
```
[s]and I hope your not using a 64-bit OS, cause the instructions are different.[/s]
-Added x64 instructions
[s]I have the full instructions documented in one of the threads around here.... but unfortunately I cant find it.[/s]
if your running x64 bit, run this instead.
```

sudo rm /var/lib/dpkg/info/adobe-flashplugin*
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
wget -c http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz
tar xvfz libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/firefox/plugins/libflashplayer.so
rm libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz

```

---

### Post by Crossbow on 2010-02-10
> **carlee said:**
> flash issues, to purge adobe flash and reinstall it....
```

sudo rm /var/lib/dpkg/info/adobe-flashplugin*
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
tar xvfz install_flash_player_10_linux.tar.gz
sudo mv *.so /usr/lib/firefox/plugins/ 
rm install_flash_player_10_linux.tar.gz
```
[s]and I hope your not using a 64-bit OS, cause the instructions are different.[/s]
-Added x64 instructions
[s]I have the full instructions documented in one of the threads around here.... but unfortunately I cant find it.[/s]
if your running x64 bit, run this instead.
```

sudo rm /var/lib/dpkg/info/adobe-flashplugin*
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
wget -c http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz
tar xvfz libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/firefox/plugins/libflashplayer.so
rm libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz

```

I honestly don't know if it's 64 or not. That's how illiterate I am. But I tried both of those codes, and neither one made a difference in getting Flash to work.

---

### Post by sandyd on 2010-02-10
> **Crossbow said:**
> I honestly don't know if it's 64 or not. That's how illiterate I am. But I tried both of those codes, and neither one made a difference in getting Flash to work.

yours is a different issue.
those commands were for sorbeth, who is having installation problems, not problems getting it to run.

---

### Post by sandyd on 2010-02-10
> **Crossbow said:**
> I honestly don't know if it's 64 or not. That's how illiterate I am. But I tried both of those codes, and neither one made a difference in getting Flash to work.

```

sudo apt-get remove --purge flashplugin-installer
sudo apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash 
sudo apt-get remove --purge iceweasel-flashplugin mozilla-flashplugin firefox-flashplugin 
sudo apt-get remove --purge swfdec-mozilla libflashsupport nspluginwrapper iceape-flashplugin 
sudo apt-get remove --purge xulrunner-flashplugin midbrowser-flashplugin xulrunner-addons-flashplugin
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/iceape/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/iceweasel/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/midbrowser/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/xulrunner/plugins/flashplugin-alternative.so
sudo rm -f /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
```
run that and reinstall flash.

---

### Post by tekkidd on 2010-02-10
hey you could try 

sudo apt-get install flashplugin-nonfree 

or since you are using a netbook (Im assuming its a 32 bit system) you could always download the flash installer from adobe

---

### Post by sandyd on 2010-02-10
> **sorbeth said:**
> Hi, I'm new to Ubuntu but I really like it.  Unfortunately I'm having some troubles.

I have the 8.04 (dell) netbook version with 3.0.5 firefox.  I tried to install flash 10 but got the libnspr4-dev error.  I tried looking up solutions and did the uninstall for the non-free flash and tried installing the download again, and now I have no flash at all.  I do not have the libnspr4-dev in synaptic to add it there and when I try to use the synaptic to add the non-free flash back in I just get an error.

I'm really at a loss here.  How can I get Flash 10 on my netbook?  

Thank you!

use post 17 (in this thread)
then use post 14.
your using a 32 bit system since its a netbook.

---

### Post by Crossbow on 2010-02-10
> **carlee said:**
> ```

apt-get remove --purge flashplugin-installer
apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash 
apt-get remove --purge iceweasel-flashplugin mozilla-flashplugin firefox-flashplugin 
apt-get remove --purge swfdec-mozilla libflashsupport nspluginwrapper iceape-flashplugin 
apt-get remove --purge xulrunner-flashplugin midbrowser-flashplugin xulrunner-addons-flashplugin
rm -f ~/.mozilla/plugins/*flash*
rm -f /usr/lib/firefox-addons/plugins/*flash*
rm -f /usr/lib/firefox/plugins/*flash*
rm -f /usr/lib/iceape/plugins/flashplugin-alternative.so
rm -f /usr/lib/iceweasel/plugins/flashplugin-alternative.so
rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
rm -f /usr/lib/midbrowser/plugins/flashplugin-alternative.so
rm -f /usr/lib/mozilla/plugins/*flash*
rm -f /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
rm -f /usr/lib/xulrunner/plugins/flashplugin-alternative.so
rm -f /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
```
run that and reinstall flash.

Oh, I thought Sorbeth and I were having the same issue - I thought he (?) said it was there but not running. 

Anyway, I tried that and just got a lot of "unable to remove" messages. I'm giving up for the night.

---

### Post by sandyd on 2010-02-10
> **Crossbow said:**
> Oh, I thought Sorbeth and I were having the same issue - I thought he (?) said it was there but not running. 

Anyway, I tried that and just got a lot of "unable to remove" messages. I'm giving up for the night.

whaaaaaaaaaa!!!!!!!!!!
forgot sudos infront of all of them. as usual. :(

---

### Post by Crossbow on 2010-02-10
> **carlee said:**
> whaaaaaaaaaa!!!!!!!!!!
forgot sudos infront of all of them. as usual. :(

Oh, I did it with sudo. When I tried it without sudo it simply said I didn't have permission, so I did it with sudo and then got a screen full of messages that it couldn't be done.

---

