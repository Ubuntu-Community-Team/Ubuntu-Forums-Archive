---
title: "Ubuntu 64 bit flash is buggy"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by gogogo111 on 2010-06-10
Hey guys, just trying to convert over to Ubuntu. This is the last big issue I'm having. Flash WORKS, but its really buggy...

For example on Youtube, sometimes the player will play the video, but the controls do not work. Pause does nothing, neither does fullscreen. I can't click the X on adds, or scroll through the timeline. Doesn't really make any sense because it's random, sometimes it works one day, sometimes it doesn't. 

And the actual Flash does not lag or anything. I really don't get it. 

So my question is, how do we fix it? Thanks in advance!

Also, I'm running 10.04, I need to update my profile.

---

### Post by tom.swartz07 on 2010-06-10
Thats because the version from the Ubuntu source is a little buggy.

Fortunately the install for the official Adobe version is nice and easy: I wrote a script to install the official version of flash.

Just download it from here: [http://bazaar.launchpad.net/~tom-swartz07/codemonkey/trunk/annotate/head:/x64%20Flash%20Installer](http://bazaar.launchpad.net/~tom-swartz07/codemonkey/trunk/annotate/head:/x64%20Flash%20Installer)

Right click on it, select properties and edit it's attributes to make it executable.
For convenience, put it on your Desktop.

Then run it from the terminal>

Applications>accessories>terminal

then run
```
cd Desktop
```
Then ```
sudo ./NAMEOFFILE
```
this will run it, and install the newest version of Flash for x64 computers.

Then youre done! :D

---

### Post by gogogo111 on 2010-06-10
Sorry for being such a scrub, but when I try that, I get this:

```
matthew@matthew-desktop:~/Desktop$ ./x64 Flash Installer
bash: ./x64: No such file or directory

```

Yet when I ls it's right there. :-/

---

### Post by GrantStoner on 2010-06-10
What version of flash is this?

---

### Post by tom.swartz07 on 2010-06-10
> **gogogo111 said:**
> Sorry for being such a scrub, but when I try that, I get this:

```
matthew@matthew-desktop:~/Desktop$ ./x64 Flash Installer
bash: ./x64: No such file or directory

```

Yet when I ls it's right there. :-/

enclose it all within quotes, and dont forget sudo!

```
sudo ./"x64 Flash Installer"
```

---

### Post by eriktheblu on 2010-06-10
edit: already answered

---

### Post by Irony on 2010-06-10
Really you don't need a script simply download 64 bit from here;

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Right click on it to extract the file. Then put it in your ~/.mozilla/plugins file.

**Note** uninstall your current flash first;

```
sudo apt-get remove flashplugin-nonfree
sudo apt-get remove --purge flashplugin-nonfree
```

Check the following and remove them;
```

/usr/lib/mozilla/plugins/*flash*
~/.mozilla/plugins/*flash*
/usr/lib/firefox/plugins/*flash*
/usr/lib/firefox-addons/plugins/*flash*
```

---

### Post by gogogo111 on 2010-06-10
Sweet it worked! Thanks so much! Everything seems to be working.

---

### Post by tom.swartz07 on 2010-06-10
> **Irony said:**
> Really you don't need a script simply download 64 bit from here;

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Right click on it to extract the file. Then put it in your ~/.mozilla/plugins file.

**Note** uninstall your current flash first;

```
sudo apt-get remove flashplugin-nonfree
sudo apt-get remove --purge flashplugin-nonfree
```

Check the following and remove them;
```

/usr/lib/mozilla/plugins/*flash*
~/.mozilla/plugins/*flash*
/usr/lib/firefox/plugins/*flash*
/usr/lib/firefox-addons/plugins/*flash*
```

Not to be a party pooper, but thats exactly what my script does, in addition to uninstalling gnash and swfdec (which interfere with the newly installed adobe flash)...

Jussayin.


Gogogo- if youre problem is solved, please mark it as such from the 'thread tools' at the top of the page! Thanks!

---

### Post by GrantStoner on 2010-06-10
Downloading scripts can be sketchy and dangerous, and Ubuntu Forums urges members now to run them without caution. But in the case of the script for Flash provided here, I can vouch for it! Just used that method and it was extremely easy, fast, and worked no problem. Just don't forget quotes around "x64 Flash Installer". Script was safe, and it saved me the time and trouble of navigating through directories. Thanks mate!

---

### Post by tom.swartz07 on 2010-06-10
> **GrantStoner said:**
> Downloading scripts can be sketchy and dangerous, and Ubuntu Forums urges members now to run them without caution. But in the case of the script for Flash provided here, I can vouch for it! Just used that method and it was extremely easy, fast, and worked no problem. Just don't forget quotes around "x64 Flash Installer". Script was safe, and it saved me the time and trouble of navigating through directories. Thanks mate!

I agree, and others must understand the dangers.

Knowing this, that is why the link I had posted resolved directly to the source code page on Launchpad. Users could view the code inside of the file, and after verifying this, they could download it themselves or create their own by copying and pasting the code listed on the page.

---

### Post by lovinglinux on 2010-06-10
> **GrantStoner said:**
> Downloading scripts can be sketchy and dangerous, and Ubuntu Forums urges members now to run them without caution. But in the case of the script for Flash provided here, I can vouch for it! Just used that method and it was extremely easy, fast, and worked no problem. Just don't forget quotes around "x64 Flash Installer". Script was safe, and it saved me the time and trouble of navigating through directories. Thanks mate!

Install [FLASH-AID](http://flash-aid-extension.blogspot.com). It is approved by Mozilla. I can vouch for it because I'm the developer.

---

### Post by tom.swartz07 on 2010-06-10
> **lovinglinux said:**
> Install [FLASH-AID](http://flash-aid-extension.blogspot.com). It is approved by Mozilla. I can vouch for it because I'm the developer.

Does that also cover the x64 version? 

As a side note: this extension appears to only install Flash for Mozilla Firefox, as it is an extension for the browser. This will not have the permissions to install the plugin for other browsers, such as Google Chrome and Chromium, and Opera.

Granted, my script doesnt have support for Opera either, but it does take care of Chrome(ium). 
Just something to take note of before using other browsers.

---

### Post by lovinglinux on 2010-06-10
> **tom.swartz07 said:**
> Does that also cover the x64 version?

Yes. It detects the browser architecture automatically and prompt for the appropriate flash version install. Nevertheless, 64bit users can still install the 32bit from the repositories. The 64bit version is selected by default tho.

> **tom.swartz07 said:**
> As a side note: this extension appears to only install Flash for Mozilla Firefox, as it is an extension for the browser. This will not have the permissions to install the plugin for other browsers, such as Google Chrome and Chromium, and Opera.

Although the extension itself can only be installed in Firefox, the installed flash version will be detected by all those browsers.

---

### Post by tom.swartz07 on 2010-06-10
> **lovinglinux said:**
> Yes. It detects the browser architecture automatically and prompt for the appropriate flash version install. Nevertheless, 64bit users can still install the 32bit from the repositories. The 64bit version is selected by default tho.



Although the extension itself can only be installed in Firefox, the installed flash version will be detected by all those browsers.

Excellent! Ill have to add it to my list of 'recommends' when another thread like this pops up! Thanks for the info!

---

### Post by lovinglinux on 2010-06-10
> **tom.swartz07 said:**
> Excellent! Ill have to add it to my list of 'recommends' when another thread like this pops up! Thanks for the info!

You are welcome and thanks for recommending it.

---

### Post by kraus3742 on 2010-06-13
Just an FYI Adobe has pulled the download from Adobe labs for Linux  64-bit flash.  Anybody know of an alternative until Adobe release the  next version to support this again?

I tried Flash-Aid and still do not have the ability to use the flash controls.  Any ideas anyone?

---

### Post by tom.swartz07 on 2010-06-13
> **kraus3742 said:**
> Just an FYI Adobe has pulled the download from Adobe labs for Linux  64-bit flash.  Anybody know of an alternative until Adobe release the  next version to support this again?

I tried Flash-Aid and still do not have the ability to use the flash controls.  Any ideas anyone?

I recently read from their newsletter that they were stopping the development of the x64 version...

BUT! 

As I type this, I just tested my script, and it still correctly downloads the most recent version of the x64 flash player. Apparently the website landing page for the download was removed, but the file itself is still hosted on their servers.


I will continue to support this script through these changes. If anyone has any difficulty running my script, please post here or file a bug report on my Launchpad page: [https://edge.launchpad.net/codemonkey/](https://edge.launchpad.net/codemonkey/)

**_EDIT: I have filed the bug report myself, ([https://bugs.edge.launchpad.net/codemonkey/+bug/593362](https://bugs.edge.launchpad.net/codemonkey/+bug/593362)) if this script stops working, please post there._**


I will possibly make it so that the latest stable (and last available) version of x64 flash is hosted on my Launchpad project. I need to verify copyright and all of that jazz before I could do so.

---

### Post by philinux on 2010-06-13
[http://ubuntuforums.org/showthread.php?t=1503920&highlight=flash](http://ubuntuforums.org/showthread.php?t=1503920&highlight=flash)
[http://ubuntuforums.org/showthread.php?t=1506874](http://ubuntuforums.org/showthread.php?t=1506874)

I've reverted to using the 32 bit flash with the wrapper for now.

---

### Post by tom.swartz07 on 2010-06-13
> **philinux said:**
> [http://ubuntuforums.org/showthread.php?t=1503920&highlight=flash](http://ubuntuforums.org/showthread.php?t=1503920&highlight=flash)
[http://ubuntuforums.org/showthread.php?t=1506874](http://ubuntuforums.org/showthread.php?t=1506874)

I've reverted to using the 32 bit flash with the wrapper for now.

I updated my preferences in synaptic and installed the 10.1 version now.

Thanks for pointing out the possible security holes in x64.

---

### Post by Lucky. on 2010-06-13
Yeah, Flash-Aid pretty much rocks.  I tried it a few days back and it worked like a charm.  Thanks!

Of course the script posted by Tom is great too.  And Carlee has a solution too.  Can't say there aren't enough choices in getting Flash working here!

---

### Post by Sergio PC on 2010-06-13
Thanks, all Scripts posted worked great.
Use the remover and the installer.
Thanks to all!

---

### Post by MissouriNewb on 2010-07-19
> **tom.swartz07 said:**
> Thats because the version from the Ubuntu source is a little buggy.

Fortunately the install for the official Adobe version is nice and easy: I wrote a script to install the official version of flash.

Just download it from here: [http://bazaar.launchpad.net/~tom-swartz07/codemonkey/trunk/annotate/head:/x64%20Flash%20Installer]("http://bazaar.launchpad.net/%7Etom-swartz07/codemonkey/trunk/annotate/head:/x64%20Flash%20Installer")

Right click on it, select properties and edit it's attributes to make it executable.
For convenience, put it on your Desktop.

Then run it from the terminal>

Applications>accessories>terminal

then run
```
cd Desktop
```Then ```
sudo ./NAMEOFFILE
```this will run it, and install the newest version of Flash for x64 computers.

Then youre done! :DWorked like a charm!!

Thanks!!

Respectfully Submitted

MN

Romans 6.23

---

