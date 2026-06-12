---
title: "Cannot install Adobe Flash Player Plugin on amd64 architecture"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by webwiller on 2009-09-13
As simple as that.
Mozilla Firefox tells me I'm missing plugin in order to watch a flash video and, while installing it, Firefox prompts me saying it couldnt install it. When I check it manually from adobe site I cant find the 64bit version but only the 32.
Any clue where I can find a .deb 64bit version or how to workaround?
Ty;)

---

### Post by NoaHall on 2009-09-13
Follow this guide -> [http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html](http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html)

---

### Post by webwiller on 2009-09-13
Thanks...I followed the process...everything worked fine, download, decompressing, command line...but when I restarted firefox  still asks me for adobe flash plugin...and still he cannot find it

---

### Post by NoaHall on 2009-09-13
Perhaps try reinstalling firefox. Or use Opera instead.

---

### Post by oldos2er on 2009-09-13
There's a script to install 64-bit flash here: [http://ubuntuforums.org/attachment.php?attachmentid=127602&d=1252205004](http://ubuntuforums.org/attachment.php?attachmentid=127602&d=1252205004)

---

### Post by Arand on 2009-09-13
Better guide: [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

If you are going to use the 64bit manually, make sure you have cleaned out all other flash related packages (see above). 

Also, double-check that the plugin file is in the right place, which is NOT the one mentioned in the blog noted previously, instead: /usr/lib/mozilla/plugins/libflashplayer.so

 - Arand

---

### Post by Dangger on 2009-09-13
I had a similar problem, it was a corrupted profile. Try another browser see if you can play flash with it and if you can then you need to delete your profile and reinstall firefox to create a new one.

---

### Post by running_rabbit07 on 2009-09-13
Go to myspace.com and install the flash offered there. Works on my 64-bit. Results may vary.

---

### Post by bumanie on 2009-09-13
The only way I could get flash working on 9.04 64bit with stability was by following [this]("http://www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit.html"). Never had a problem since.

---

### Post by webwiller on 2009-09-13
I thank you all....
But now I guess I did a bit of a mess installing different versions...
Any easy way to clean up all old flash-plugin versions?

---

### Post by webwiller on 2009-09-13
On this page I folloewd all instruction:
[http://www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit.html]("http://www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit.html")

and when I get to point#4
> sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

I get this error:
> webwiller@webwiller-laptop:~$ sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
nspluginwrapper: **no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so**

???

---

### Post by webwiller on 2009-09-13
I did try a fresh install already, if it was a profile problem, but no changes what so ever.

---

### Post by gn2 on 2009-09-13
Downlaod 64-bit flash [here]("http://labs.adobe.com/downloads/flashplayer10.html")

Then follow [the simplest instructions I know of]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml").

---

### Post by webwiller on 2009-09-14
> **running_rabbit07 said:**
> Go to myspace.com and install the flash offered there. Works on my 64-bit. Results may vary.

This was the one that worked for me! I found out it's version #9 instead of 10 or above. Old stuff might work better;)

Ty all any way...

I'd love to know WHY with Firefox latest version (3.5.3) I cant get latest flash working but old one yes btw... but I guess my curiosity wont be satisfied this time :lolflag:

---

### Post by webwiller on 2009-09-14
Nop! I just dreamed it was solved!!!
I got video playing BUT NO SOUND!!!
Oh gosh...

---

### Post by running_rabbit07 on 2009-09-14
Darn. That's crazy. I am sorry to hear that you are having so many issues trying to get Flash. Are you sure it is flash causing the problem?

---

### Post by gali98 on 2009-09-14
All you have to do is run the command

sudo apt-get install ubuntu-restricted-extras

That's it. It installs flash.

As a note, you can also install the package flashplugin-nonfree. That will install just flash.
Kory

---

### Post by running_rabbit07 on 2009-09-14
> **gali98 said:**
> All you have to do is run the command

```
sudo apt-get install ubuntu-restricted-extras
```

That's it. It installs flash.

As a note, you can also install the package flashplugin-nonfree. That will install just flash.
Kory

That one installs 32 bit flash, but it could still work.

---

### Post by webwiller on 2009-09-14
> **running_rabbit07 said:**
> That one installs 32 bit flash, but it could still work.

Done already, but no effect!

Can anybody explain me why my firefox plugins which are under:

> /opt/firefox/plugins/

is in reality just a symlink pointing to:

> /usr/lib/xulrunner-addons/plugins

I've been trying all versions, in any case best result is video with no sound. Opera works well...and flash does work in it! You know why?

I have a firefox add-on whin I'm not glad at all to leave, it's Xmarks, which allows me to have all my bookmarks and passwords on any pc, just installing the add-on and remembering one pwd, the Xmarks one. Anything similar on Opera?

---

### Post by supererki on 2009-09-14
i think there is 64bit installer available, you have to google for it.

if you dont find it then maybe

dpkg --force-archidecture -i /your/path/blabla.deb 

will help you:)

---

### Post by webwiller on 2009-09-14
Can anybody explain WHY do I get this:
> webwiller@webwiller-laptop:~$ sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

---

### Post by NoaHall on 2009-09-14
Don't use the 32 bit one. Seriously. It sucks.

---

### Post by webwiller on 2009-09-14
> **NoaHall said:**
> Don't use the 32 bit one. Seriously. It sucks.

I'm not! Am I?

---

### Post by NoaHall on 2009-09-14
Well, if you're using the native one, you shouldn't need nspluginwrapper - it should just work once you put it in the right place.

---

### Post by 3rdalbum on 2009-09-14
Gaaah this is frustrating to watch.

Go into Synaptic and **remove** these packages:

flashplugin-nonfree
flashplugin-install
nspluginwrapper

Remove all instances of Flash Player except for your 64-bit alpha version from Adobe Labs. You can find all instances by using this command:

```
locate libflashplayer.so
```

Close Firefox and start it back up.

---

### Post by running_rabbit07 on 2009-09-14
I have another question that may or may not help figure this out. Are you using the Shiretoko FF3.5 or the official download from Mozilla?

---

### Post by webwiller on 2009-09-14
- I'm using the official download

I've tried your command to lacate liblflashplayer.so on terminal, but I didnt get any answer at all.
I checked manually and there's still a file I can see left over. How can I make sure is the only one? 
if I just write:
> locate libflashplayer.so
I get nothing out of it. Should I specify where to look for?

---

### Post by oldos2er on 2009-09-14
If you run the script I pointed you to ([http://ubuntuforums.org/attachment.php?attachmentid=127602&d=1252205004](http://ubuntuforums.org/attachment.php?attachmentid=127602&d=1252205004)), it will first uninstall any versions of flash you may already have, before installing 64-bit flash.

---

### Post by webwiller on 2009-09-14
> **oldos2er said:**
> If you run the script I pointed you to ([http://ubuntuforums.org/attachment.php?attachmentid=127602&d=1252205004](http://ubuntuforums.org/attachment.php?attachmentid=127602&d=1252205004)), it will first uninstall any versions of flash you may already have, before installing 64-bit flash.

Your script wont work on my pc, dont know why. I double click it, I get prompt if I want to whatch content or execute file as a program, I choose to execute, and nothing happens. Just nothing.

Sorry, I'm wrong, is not yours which doesnt work, the script works, I type in yes and it downloads and installs, but I cant find the plugin typing in the URL bar of firefox about:plugins, and cant watch any flash video.

---

### Post by NoaHall on 2009-09-14
Try running it from the terminal instead - then it will output any errors.

---

### Post by oldos2er on 2009-09-14
> **webwiller said:**
> Your script wont work on my pc, dont know why. I double click it, I get prompt if I want to whatch content or execute file as a program, I choose to execute, and nothing happens. Just nothing.

Sorry, I'm wrong, is not yours which doesnt work, the script works, I type in yes and it downloads and installs, but I cant find the plugin typing in the URL bar of firefox about:plugins, and cant watch any flash video.

 Did you restart Firefox after running the script?

---

### Post by webwiller on 2009-09-14
All process proceeds smoothly. No errors. Apart from the fact that flash doesnt work.

---

### Post by webwiller on 2009-09-14
> **oldos2er said:**
> Did you restart Firefox after running the script?

Firefox was off during installation, I'm browsing with Opera.

The problem, I believe, is the file itself, as video without sound worked when I installed version9 of flash in the same way, same position. Process is fine, position (which is the only one that counts really) is fine. Is either something that has to do with graphic card...or the file, or that specific file.
Which is the stable version released b4 this for 64bit arch if any?

---

### Post by Arand on 2009-09-14
Use```
ls /usr/lib/mozilla/plugins/
```to confirm that this directory does not contain any files with **flash** in their name EXCEPT for libflashplayer.so which the script pulled in for you.

Also, if you still have that file in /usr/lib/firefox-addons/plugins/ -- remove it

Btw that script has a typo, although I doubt it affects this case:```
sudo rm -f /usr/lib/mozilla/plguins/npwrapper*flash*so
```-> s/plguins/plugins/

Prior to this version, there was NO 64bit flash available, hence nspluginwrapper was used to consolidate 32bit flash in 64bit OS. From my experience, running the 64bit version, even though it's alpha, is far more stable.

- Arand

---

### Post by oldos2er on 2009-09-14
> **webwiller said:**
> Firefox was off during installation, I'm browsing with Opera.


 Then you probably need to manually copy libflashplayer.so to Opera's plugins directory.

---

### Post by NoaHall on 2009-09-14
> **oldos2er said:**
> Then you probably need to manually copy libflashplayer.so to Opera's plugins directory.

No, it will work if you put them in the Firefox place. Mine works just fine.

---

### Post by oldos2er on 2009-09-14
> **NoaHall said:**
> No, it will work if you put them in the Firefox place. Mine works just fine.

 I had to copy libflashplayer.so to /usr/lib/opera/plugins to make it work.

---

### Post by NoaHall on 2009-09-14
Mine worked fine when it was in mozilla. Clean install, not messing around with anything.

---

### Post by gali98 on 2009-09-15
If locate didn't work, you probably need to run 
updatedb 
first.
Kory

---

### Post by Cypher1101 on 2009-09-15
I used 
```
 
sudo aptitude purge flash-installer
sudo aptitude install flash-installer flash-nonfree

```

Everything worked with sound in flash after that

amd64 jaunty

---

### Post by Arand on 2009-09-16
Cypher1101: There are no packages by that name in the normal repos; also, I think we're past that stage.

---

### Post by webwiller on 2009-09-16
The problem's still there. I downgraded to Firefox 1.0.14, the repo's one, and flash works just fine. I ask myself what Flash-plugin is using, if version9-64bit, or version10-32bit+nswrapper.
???
If anyone has new suggestions...are welcomed!

Noa...I understand your installation run smoothly, but it's not my case and, it's not an absolute rule that what worked on your system must work on mine. I'm not so good with ubuntu to understand what differencies could there be...but obviously there are! As I followed step-by-step your kind instruction but could not watch neigher hear any flash video nor or sound.

---

### Post by tomBorgia on 2009-09-16
> **3rdalbum said:**
> Gaaah this is frustrating to watch.

Go into Synaptic and **remove** these packages:

flashplugin-nonfree
flashplugin-install
nspluginwrapper

Remove all instances of Flash Player except for your 64-bit alpha version from Adobe Labs. You can find all instances by using this command:

```
locate libflashplayer.so
```

Close Firefox and start it back up.

+Mod up... like a million times.

---

### Post by webwiller on 2009-09-17
Finally I sorted it out having flash-plugin working on ubuntu9.04 amd64 following the instruction given here:

[http://meandubuntu.wordpress.com/2008/08/20/flash-10-rc-on-ubuntu-amd64/]("http://meandubuntu.wordpress.com/2008/08/20/flash-10-rc-on-ubuntu-amd64/")

I ask you only one thing...am I using 32bit plugin with nswrapper or native 64bit flashplugin? I enclose the script:

# echo "Stopping any Firefox that might be running"  
# sudo killall -9 firefox    
#   
> # echo "Removing any other flash plugin previously installed:"  
# sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper  
# sudo rm -f /usr/lib/mozilla/plugins/*flash*  
# sudo rm -f ~/.mozilla/plugins/*flash*  
# sudo rm -f /usr/lib/firefox/plugins/*flash*  
# sudo rm -f /usr/lib/firefox-addons/plugins/*flash*  
# sudo rm -rfd /usr/lib/nspluginwrapper    
#   
# echo "Installing ia32-libs and nspluginwrapper"  
# sudo apt-get install ia32-libs nspluginwrapper    
#   
# echo "Getting libs"  
# sudo getlibs -p libcurl3  
# sudo getlibs -p libnss3-1d  
# sudo getlibs -p libnspr4-0d    
#   
# echo "Installing Flash Player 10"  
# cd ~  
# wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)  
# tar zxvf install_flash_player_10_linux.tar.gz  
# sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/  
# sudo chmod +rx /usr/lib/mozilla/plugins/libflashplayer.so  
# rm -rf ~/install_flash_player_10_linux/  
# sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so    
#   
# echo "Linking the libraries so Firefox can find it."  
# sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/  
# sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/ 

I would guess it is 32bit plugin...but at least it works!

Ty all!

---

### Post by NoaHall on 2009-09-17
Yep, it's 32 bit :) Hang around the forums, and maybe we can tell you when the beta is out, and maybe then you can install it and see if anything has changed.

---

### Post by webwiller on 2009-09-18
But flash-plugin 64bit alpha (or beta...same meaning..."sperimental") is ALREADY out!

I guess...but not sure, it didnt work with all previous attempts I made because of the missing libraries as (bolded ones):

> # echo "Stopping any Firefox that might be running"
# sudo killall -9 firefox 
# echo "Removing any other flash plugin previously installed:"
# sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
# sudo rm -f /usr/lib/mozilla/plugins/*flash*
# sudo rm -f ~/.mozilla/plugins/*flash*
# sudo rm -f /usr/lib/firefox/plugins/*flash*
# sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
# sudo rm -rfd /usr/lib/nspluginwrapper
#
# echo "Installing ia32-libs and nspluginwrapper"
# sudo apt-get install ia32-libs nspluginwrapper
#
[B]# echo "Getting libs"
# sudo getlibs -p libcurl3
# sudo getlibs -p libnss3-1d
# sudo getlibs -p libnspr4-0d[/B]
#
# echo "Installing Flash Player 10"
# cd ~
# wget [http://fpdownload.macromedia.com/get...0_linux.tar.gz](http://fpdownload.macromedia.com/get...0_linux.tar.gz)
# tar zxvf install_flash_player_10_linux.tar.gz
# sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/
# sudo chmod +rx /usr/lib/mozilla/plugins/libflashplayer.so
# rm -rf ~/install_flash_player_10_linux/
# sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
#
# echo "Linking the libraries so Firefox can find it."
# sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
# sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/ 

Could I get back uninstalling everything but the lib's? And try it out that way? 

What you think Noa?

I could use just this same script above without the installation process to clean previous (actual) flash-plugin, and then install the 64bit just moving it in the same folders as in the above script, with same symlinks...???

Could it be a good idea?

TX,
W.W. :KS

---

### Post by radioactivet on 2009-09-22
> **NoaHall said:**
> Follow this guide -> [http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html](http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html)


Worked perfectly for me. Thanks a million!
(AMD Athlon X2 64 with Ubuntu 9.04 AMD64)

---

