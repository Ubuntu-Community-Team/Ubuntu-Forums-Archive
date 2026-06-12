---
title: "Help w/ Flash on 8.04 x64"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by xXNI4NI on 2009-03-09
It shows up in about:plugins
it sometimes work and sometimes doesn't normally if i refresh often enough i can sometimes get it to load
sudo apt-get flashplugin-nonfree does not work
i've combed threads and threads and i cannot find one that is either up to date or one that works
like i said i have it so i may need to remove it but i am still new so i am not sure how to go about it if someone could please help or link an up-to-date link thats known to work thank you much appreciated.

---

### Post by Kareeser on 2009-03-10
[http://www.kareeser.com/ubuntu/flash64.php](http://www.kareeser.com/ubuntu/flash64.php)

Give it a shot. Tell me if it works :)

You'll have to delete the library (or the link to the library) of the old plugin, before trying the above method.
Do you know how to do that?

---

### Post by xXNI4NI on 2009-03-10
i do not unfortunately thank you for your response and will give it a shot as soon as i remove it

---

### Post by gandaran on 2009-03-10
the old plugin (flashplugin-nontree), go to synaptic find it and mark for complete removal and hit apply.
now get the 64-bits flash [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz"), to install extract the package and move the libflashplayer.so file to /home/'user'/.mozilla/plugins (make the plugins folder) or if you have more than one user account place it in /usr/lib/mozilla/plugins, easy!

---

### Post by xXNI4NI on 2009-03-10
would it be better to use ln to /plugins rather than mv to /pugins?

---

### Post by xXNI4NI on 2009-03-10
gandaran i few problems arose when i did what you asked.
i did remove nonfree via synaptic
i installed and did the following
tar -xzvf libflashplayer10.0...
the .so came out and did
sudo mv. libflash... /usr/lib/mozilla/plugins
and confirmed it is in there
HOWEVER
it seems when i go to flash extensive sites (ie: myspace iee: myspace music)
it slows down my computer terribly and firefox teeders on freezing up, but on non-flash sites like the ubuntu forums everything is fine AND when i go to a myspace artist it says i need the latest version of flash..though it is shown in about : plugins
do i need to ln w/ firefox plugins as well? it seems mozilla is having a hard time executing/performing flash commands and the fact that its asking me to get flash is confusing...ill check other mozilla/plugins and firefox/plugins to see if there is not another .so confliction

---

### Post by stchman on 2009-03-10
> **xXNI4NI said:**
> It shows up in about:plugins
it sometimes work and sometimes doesn't normally if i refresh often enough i can sometimes get it to load
sudo apt-get flashplugin-nonfree does not work
i've combed threads and threads and i cannot find one that is either up to date or one that works
like i said i have it so i may need to remove it but i am still new so i am not sure how to go about it if someone could please help or link an up-to-date link thats known to work thank you much appreciated.

I have a tutorial on how to get Flash 10 up and going in Ubuntu 64 bit.

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

Works great on my 64 bit Hardy boxes.

---

### Post by wolfen69 on 2009-03-10
another way that worked for me is, to extract the tar.gz file, and copy the **libflashplayer.so** file to /usr/lib/mozilla/plugins

do ```
gksudo nautilus
``` before copying the file.

---

### Post by gandaran on 2009-03-10
> **xXNI4NI said:**
> gandaran i few problems arose when i did what you asked.
i did remove nonfree via synaptic
i installed and did the following
tar -xzvf libflashplayer10.0...
the .so came out and did
sudo mv. libflash... /usr/lib/mozilla/plugins
and confirmed it is in there
HOWEVER
it seems when i go to flash extensive sites (ie: myspace iee: myspace music)
it slows down my computer terribly and firefox teeders on freezing up, but on non-flash sites like the ubuntu forums everything is fine AND when i go to a myspace artist it says i need the latest version of flash..though it is shown in about : plugins
do i need to ln w/ firefox plugins as well? it seems mozilla is having a hard time executing/performing flash commands and the fact that its asking me to get flash is confusing...ill check other mozilla/plugins and firefox/plugins to see if there is not another .so confliction
well if the so.file is in /usr/lib/mozilla/plugins then it is correctly installed, you can try installing it on any browser plugins directory like /usr/lib/firefox/plugins but it won't make any deference, you have a problem with flash and it's not due to where it's installed.
check that you don't have any other flash conflicting installed be it adobe, gnash or swfdec.
try also disabling flash hardware acceleration (right click the flash video window » configurations) see if it makes any deference.
did you remove the flashplugin-nonfree dependency as well? I'm not sure but I think it's nspluginwrapper or something similar.
in /usr/lib/mozilla/plugins, is there any other file besides the libflashplayer.so file?

---

### Post by xXNI4NI on 2009-03-10
> **stchman said:**
> I have a tutorial on how to get Flash 10 up and going in Ubuntu 64 bit.

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

Works great on my 64 bit Hardy boxes.

i did this and it worked great when i now go to the adobe test page it now plays the .swf instead of the gray box and youtube videos load along w/ myspace artists' pages thank you! BUT... (dramatic suspense music plays) every so often i will navigate to a page (seems to only happen w/ some myspace artists' pages more specifically ones w/ loads of flash ie: banners ads vidoes...all the bells and whistles) and my firefox will just close. No error message no save tabs and quit...just closes. I'm thinking that due to my failed attempts of installing flash in the past MAYBE there might be some confusion? i am not sure...i don't even know how to trouble shoot this error because it is not giving me much to work with. any help thanks!

---

### Post by xXNI4NI on 2009-03-10
bump maybe? am i allowed to?

---

### Post by xXNI4NI on 2009-03-11
An Update: The miraculous abrupt closing of firefox not only happens on myspace's artists' pages as aforementioned but also on facebook profiles. I know it may seem a bit juvenile and what but hey if a college kid wants some facebook and maybe a little myspace tunes is that so bad? HA anyways any help would be appreciated, I still have no idea to the cause of these terminations but I do know that it happened after I successfully* installed flash.

---

### Post by gandaran on 2009-03-11
> **Kareeser said:**
> [http://www.kareeser.com/ubuntu/flash64.php](http://www.kareeser.com/ubuntu/flash64.php)

Give it a shot. Tell me if it works :)

You'll have to delete the library (or the link to the library) of the old plugin, before trying the above method.
Do you know how to do that?
Kareeser 
may I point out an error on you link instructions, any one coping/paste this code
```
ln -s /usr/local/lib/flash64/libflashplayer.so /usr/lib/.mozilla/plugins/libflashplayer.so 
```
won't get flash installed, the target mozilla folder has a dot which does not exist on the system file, it should be like this
**ln -s /usr/local/lib/flash64/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so **

---

### Post by gandaran on 2009-03-11
> **xXNI4NI said:**
> An Update: The miraculous abrupt closing of firefox not only happens on myspace's artists' pages as aforementioned but also on facebook profiles. I know it may seem a bit juvenile and what but hey if a college kid wants some facebook and maybe a little myspace tunes is that so bad? HA anyways any help would be appreciated, I still have no idea to the cause of these terminations but I do know that it happened after I successfully* installed flash.
what version of firefox are you running? is it fully updated to the latest release? try out another browser, maybe opera!

---

### Post by 3rdalbum on 2009-03-11
The 64-bit plugin is still an alpha version AFAIK. That might be causing some problems. If you run Firefox from the terminal, you can look at the output after Firefox crashes. There might be an error message that gives you a clue of what to do; maybe a missing dependency for audio output?

---

### Post by gn2 on 2009-03-11
[Here's a simple gui-guide]("http://tinyurl.com/68kzmy") that works in 8.04 as well as 8.10.

Two very important points to note, you *must* close all Firefox windows and remove nspluginwrapper before doing it.

Wouldn't hurt to remove Gnash as well.

EDIT: Get the latest 64-bit flash [here]("http://labs.adobe.com/downloads/flashplayer10.html").

---

### Post by xXNI4NI on 2009-03-11
> **gandaran said:**
> Kareeser 
may I point out an error on you link instructions, any one coping/paste this code
```
ln -s /usr/local/lib/flash64/libflashplayer.so /usr/lib/.mozilla/plugins/libflashplayer.so 
```
won't get flash installed, the target mozilla folder has a dot which does not exist on the system file, it should be like this
**ln -s /usr/local/lib/flash64/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so **

Yes I noticed this but was able to re-route the command to work. I am running Firefox 3.0.7

---

### Post by xXNI4NI on 2009-03-11
> **3rdalbum said:**
> The 64-bit plugin is still an alpha version AFAIK. That might be causing some problems. If you run Firefox from the terminal, you can look at the output after Firefox crashes. There might be an error message that gives you a clue of what to do; maybe a missing dependency for audio output? THIS IS FRUSTRATING! it works! when i run sudo firefox everything loads beautifuly! what does this mean? jeez i am assuming it means my flash is fine but firefox (ran under normal) doesn't get privelages needed and therefor closes? I don't know im just a noob stuck in a bold new world

---

### Post by gandaran on 2009-03-11
> **xXNI4NI said:**
> THIS IS FRUSTRATING! it works! when i run sudo firefox everything loads beautifuly! what does this mean? jeez i am assuming it means my flash is fine but firefox (ran under normal) doesn't get privelages needed and therefor closes? I don't know im just a noob stuck in a bold new world
maybe something is wrong with your user firefox profile, you can try backup your hidden home user .mozilla folder first (just change the folder name) now restart firefox with default settings, if it works fine then just find out the deference.

---

### Post by aktiwers on 2009-03-11
Completely remove the flash-plugin and run this command:

```

cd  $HOME/.mozilla/plugins/
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)
tar xvzf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz

```And restart Firefox.

---

### Post by xXNI4NI on 2009-03-11
> **aktiwers said:**
> Completely remove the flash-plugin and run this command:

```

cd  $HOME/.mozilla/plugins/
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)
tar xvzf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz

```And restart Firefox.

done, i removed the flash.so* plugin from /usr/lib/mozilla/plugins as well as /usr/lib/firefox/plugins and ran your code and restarted firefox, flash is still under about : plugins and firefox still closes

To the other suggestion...How would I load user profiles? Sorry I know I should know

---

### Post by gn2 on 2009-03-12
Did you read my previous post?
You need to make sure all Firefox windows are closed before installing  flash.

To change your "user profile" you need to change the contents of the hidden .mozilla folder in your /home directory.

You can close Firefox then Places > Home and click Ctrl+h to toggle between showing and hiding the .hidden files.
You can rename the .mozilla folder to .mozilla_backup and when you next start Firefox a new fresh .mozilla folder with the default settings will be created.
You will need to re-install any add-ons and customise it to the way you had it before.

The job you are trying to do can be achieved using the GUI, there's no need to be messing around in the CLI for this task.

---

### Post by Kareeser on 2009-03-12
> **gandaran said:**
> Kareeser 
may I point out an error on you link instructions, any one coping/paste this code
```
ln -s /usr/local/lib/flash64/libflashplayer.so /usr/lib/.mozilla/plugins/libflashplayer.so 
```
won't get flash installed, the target mozilla folder has a dot which does not exist on the system file, it should be like this
**ln -s /usr/local/lib/flash64/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so **

Thanks for the mistake! I originally had the user installing the plugin in ~/.mozilla/plugins/, but later realized that this would limit functionality of the plugin to the current user only.

Modified accordingly.

---

