---
title: "Problem with plugins"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2010-10-05
Hello everybody.
I'm running Ubuntu 10.04 and Win XP pro sp3 in my laptop. If it makes a difference, it's an Acer 5000.

A moment ago, I was trying to open a page in Firefox, and got the message that I was missing plugins. So I clicked on "install plugins". Once it searched, I was missing Adobe Flash Player, SWFDEC SWF Player, and Gnash SWF Player. So I clicked "next" to install them, and got a message saying the plugins are already installed...:confused:
I looked in the "add ons" list (under "plugins"), and Flash Player is not there.
Also, I restarted the computer, being that I had just updated to 10.04, but no luck.

How can I fix this?

Thanks in advance. :)

---

### Post by oldos2er on 2010-10-05
To install Adobe flash, run ```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
``` in a terminal. Restart Firefox, and it should work.

---

### Post by Inodoro Pereyra on 2010-10-05
Thank you Oldos2er for the reply. 

Tried what you suggested, but it didn't work. :(
Is there a way I can uninstall it, so I can install it back later?

---

### Post by oldos2er on 2010-10-05
Need more info; what exactly didn't work? If there were errors in the terminal, please copy and paste them here.

---

### Post by Inodoro Pereyra on 2010-10-05
No errors in the terminal. Everything went smoothly. But after restarting Firefox, I still get the same error as before. Even after restarting the PC, the error remains. It's telling me I'm missing the plugins, and when I try to install them, it says they're already installed.

---

### Post by Inodoro Pereyra on 2010-10-05
I tried it again. This is what I got:

bernardo@bernardo-laptop:~$ sudo apt-get update && sudo apt-get install flashplugin-nonfree
[sudo] password for bernardo: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  sdparm
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bernardo@bernardo-laptop:~$

---

### Post by sandyd on 2010-10-05
> **Inodoro Pereyra said:**
> I tried it again. This is what I got:

bernardo@bernardo-laptop:~$ sudo apt-get update && sudo apt-get install flashplugin-nonfree
[sudo] password for bernardo: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  sdparm
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bernardo@bernardo-laptop:~$


post output of 
```

ls /usr/lib/mozilla/plugins
```

---

### Post by lovinglinux on 2010-10-05
Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by Inodoro Pereyra on 2010-10-05
Sorry, I was away from the computer.

> **sandyd said:**
> post output of 
```

ls /usr/lib/mozilla/plugins
```

bernardo@bernardo-laptop:~$ ls /usr/lib/mozilla/plugins
libjavaplugin.so                       libtotem-gmp-plugin.so
librhythmbox-itms-detection-plugin.so  libtotem-mully-plugin.so
libtotem-cone-plugin.so                libtotem-narrowspace-plugin.so
bernardo@bernardo-laptop:~$ 

Lovinglinux: I will get to it right away, and post my results in a moment. :)

---

### Post by sandyd on 2010-10-05
> **Inodoro Pereyra said:**
> Sorry, I was away from the computer.



bernardo@bernardo-laptop:~$ ls /usr/lib/mozilla/plugins
libjavaplugin.so                       libtotem-gmp-plugin.so
librhythmbox-itms-detection-plugin.so  libtotem-mully-plugin.so
libtotem-cone-plugin.so                libtotem-narrowspace-plugin.so
bernardo@bernardo-laptop:~$ 

Lovinglinux: I will get to it right away, and post my results in a moment. :)

64bit or 32bit linux?

32bit
```

wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
tar xvfz install_flash_player_10_linux.tar.gz
mkdir ~/.mozilla/plugins
mv libflashplayer.so ~/.mozilla/plugins

```

64bit
```

wget -c http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz
tar xvfz flashplayer_square_p2_64bit_linux_092710.tar.gz
mkdir ~/.mozilla/plugins
mv libflashplayer.so ~/.mozilla/plugins
```

---

### Post by Inodoro Pereyra on 2010-10-05
Ok, let's go by the numbers.

1. when I typed **about:config**, I've got a HUGE list. I'm guessing that's normal.
Then, when I put **plugin.expose_full_path**in the filter, I've got...nothing.:confused:
Nothing to double click...
Then typed  **about:plugins**, and looked for Shockwave. I'm feeling really stupid right now, but I couldn't find it. This is what I've got:

**Installed plugins**

 Find more information about browser plugins at  [mozilla.org]("https://pfs.mozilla.org/plugins/"). 
 Help for installing plugins is available from  [plugindoc.mozdev.org]("http://plugindoc.mozdev.org/"). 
 **VLC Multimedia Plugin (compatible Totem 2.30.2)**

 File:  libtotem-cone-plugin.soVersion:   The [Totem]("http://www.gnome.org/projects/totem/") 2.30.2 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-vlc-plugin VLC Multimedia Plugin 
Yes   application/vlc VLC Multimedia Plugin 
Yes   video/x-google-vlc-plugin VLC Multimedia Plugin 
Yes   application/x-ogg Ogg multimedia file ogg Yes   application/ogg Ogg multimedia file ogg Yes   audio/ogg Ogg Audio oga Yes   audio/x-ogg Ogg Audio ogg Yes   video/ogg Ogg Video ogv Yes   video/x-ogg Ogg Video ogg Yes   application/annodex Annodex exchange format anx Yes   audio/annodex Annodex Audio axa Yes   video/annodex Annodex Video axv Yes   video/mpeg MPEG video mpg, mpeg, mpe Yes   audio/wav WAV audio wav Yes   audio/x-wav WAV audio wav Yes   audio/mpeg MP3 audio mp3 Yes   application/x-nsv-vp3-mp3 NullSoft video nsv Yes   video/flv Flash video flv Yes   application/x-totem-plugin Totem Multimedia plugin 
Yes  **Windows Media Player Plug-in 10 (compatible; Totem)**

 File:  libtotem-gmp-plugin.soVersion:   The [Totem]("http://www.gnome.org/projects/totem/") 2.30.2 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-mplayer2 AVI video avi, wma, wmv Yes   video/x-ms-asf-plugin ASF video asf, wmv Yes   video/x-msvideo AVI video asf, wmv Yes   video/x-ms-asf ASF video asf Yes   video/x-ms-wmv Windows Media video wmv Yes   video/x-wmv Windows Media video wmv Yes   video/x-ms-wvx Windows Media video wmv Yes   video/x-ms-wm Windows Media video wmv Yes   video/x-ms-wmp Windows Media video wmv Yes   application/x-ms-wms Windows Media video wms Yes   application/x-ms-wmp Windows Media video wmp Yes   application/asx Microsoft ASX playlist asx Yes   audio/x-ms-wma Windows Media audio wma Yes  **DivX® Web Player**

 File:  libtotem-mully-plugin.soVersion:   DivX Web Player version 1.4.0.233   MIME Type Description Suffixes Enabled    video/divx AVI video divx Yes  **QuickTime Plug-in 7.6.6**

 File:  libtotem-narrowspace-plugin.soVersion:   The [Totem]("http://www.gnome.org/projects/totem/") 2.30.2 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    video/quicktime QuickTime video mov Yes   video/mp4 MPEG-4 video mp4 Yes   image/x-macpaint MacPaint Bitmap image pntg Yes   image/x-quicktime Macintosh Quickdraw/PICT drawing pict, pict1, pict2 Yes   video/x-m4v MPEG-4 video m4v Yes  **iTunes Application Detector**

 File:  librhythmbox-itms-detection-plugin.soVersion:   This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.   MIME Type Description Suffixes Enabled    application/itunes-plugin 

Yes  **IcedTea NPR Web Browser Plugin (using IcedTea6 1.8.1 (6b18-1.8.1-0ubuntu1))**

 File:  IcedTeaPlugin.soVersion:   The IcedTea NPR Web Browser Plugin (using IcedTea6 1.8.1 (6b18-1.8.1-0ubuntu1)) executes Java applets.   MIME Type Description Suffixes Enabled    application/x-java-vm IcedTea class,jar Yes   application/x-java-applet IcedTea class,jar Yes   application/x-java-applet;version=1.1 IcedTea class,jar Yes   application/x-java-applet;version=1.1.1 IcedTea class,jar Yes   application/x-java-applet;version=1.1.2 IcedTea class,jar Yes   application/x-java-applet;version=1.1.3 IcedTea class,jar Yes   application/x-java-applet;version=1.2 IcedTea class,jar Yes   application/x-java-applet;version=1.2.1 IcedTea class,jar Yes   application/x-java-applet;version=1.2.2 IcedTea class,jar Yes   application/x-java-applet;version=1.3 IcedTea class,jar Yes   application/x-java-applet;version=1.3.1 IcedTea class,jar Yes   application/x-java-applet;version=1.4 IcedTea class,jar Yes   application/x-java-applet;version=1.4.1 IcedTea class,jar Yes   application/x-java-applet;version=1.4.2 IcedTea class,jar Yes   application/x-java-applet;version=1.5 IcedTea class,jar Yes   application/x-java-applet;version=1.6 IcedTea class,jar Yes   application/x-java-applet;jpi-version=1.6.0_18 IcedTea class,jar Yes   application/x-java-bean IcedTea class,jar Yes   application/x-java-bean;version=1.1 IcedTea class,jar Yes   application/x-java-bean;version=1.1.1 IcedTea class,jar Yes   application/x-java-bean;version=1.1.2 IcedTea class,jar Yes   application/x-java-bean;version=1.1.3 IcedTea class,jar Yes   application/x-java-bean;version=1.2 IcedTea class,jar Yes   application/x-java-bean;version=1.2.1 IcedTea class,jar Yes   application/x-java-bean;version=1.2.2 IcedTea class,jar Yes   application/x-java-bean;version=1.3 IcedTea class,jar Yes   application/x-java-bean;version=1.3.1 IcedTea class,jar Yes   application/x-java-bean;version=1.4 IcedTea class,jar Yes   application/x-java-bean;version=1.4.1 IcedTea class,jar Yes   application/x-java-bean;version=1.4.2 IcedTea class,jar Yes   application/x-java-bean;version=1.5 IcedTea class,jar Yes   application/x-java-bean;version=1.6 IcedTea class,jar Yes   application/x-java-bean;jpi-version=1.6.0_18 IcedTea class,jar Yes

2. I don't know how you did the whole screen, but this is all I could copy:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.10) Gecko/20100915 Ubuntu/10.04 (lucid) Firefox/3.6.10

3. Here it is:

Ubuntu Architecture

Linux bernardo-laptop 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox                        install
firefox-3.5                    install
firefox-3.5-branding                install
firefox-3.5-gnome-support            install
firefox-branding                install
firefox-gnome-support                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.10/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources


Flash packages

flashplugin-installer                install
flashplugin-nonfree                install

Plugin locations



Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

Sorry for the huge post. I just didn't want to leave anything out. And thank you all for the help. :)

---

### Post by Inodoro Pereyra on 2010-10-05
Oops, the plugin list got messed up...Sorry.
How do I go about posting the whole list, so it can be understood?

---

### Post by utnubuuser on 2010-10-05
Safe to assume Firefox has been restarted after installing flashplugin-nonfree, and I'd also suggest to try the "install --reinstall" argument instead of just "install"

and what about > sudo apt-get install ubuntu-restricted-extras

---

### Post by Inodoro Pereyra on 2010-10-05
> **sandyd said:**
> 64bit or 32bit linux?

32bit
```

wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
tar xvfz install_flash_player_10_linux.tar.gz
c
mv libflashplayer.so ~/.mozilla/plugins

```64bit
```

wget -c http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz
tar xvfz flashplayer_square_p2_64bit_linux_092710.tar.gz
mkdir ~/.mozilla/plugins
mv libflashplayer.so ~/.mozilla/plugins
```


I'm guessing 32 bit. How do I find out?
Anyways, tried the 32 bit one. Didn't work.:(

---

### Post by Inodoro Pereyra on 2010-10-05
> **utnubuuser said:**
> Safe to assume Firefox has been restarted after installing flashplugin-nonfree, and I'd also suggest to try the "install --reinstall" argument instead of just "install"

and what about


I'm restarting the computer every time I do anything.

Also just tried your suggestion. Nothing.:(

---

### Post by sandyd on 2010-10-05
> **Inodoro Pereyra said:**
> I'm guessing 32 bit. How do I find out?
Anyways, tried the 32 bit one. Didn't work.:(

```


uname -m

```


x86_64
 means 64bit

---

### Post by Inodoro Pereyra on 2010-10-05
> **sandyd said:**
> ```


uname -m

```
x86_64
 means 64bit

Ok, I got "i686". That's 32 bit, right?

---

### Post by lovinglinux on 2010-10-06
Yes, you have 32bit.

The problem is that although you have flash installed, your plugins folder do not have the expected shared object.

Try this:

```
sudo apt-get purge flashplugin-installer
sudo apt-get purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

```

Restart Firefox and test again.

---

### Post by Inodoro Pereyra on 2010-10-06
FINALLY!!!
Lovinglinux YOU-ARE-A-[SIZE=5]MASTER!!!

[SIZE=1]Thank you so much, and thanks everybody for all the help. You guys rock! =D>[/SIZE]
[/SIZE]

---

### Post by lovinglinux on 2010-10-06
> **Inodoro Pereyra said:**
> FINALLY!!!
Lovinglinux YOU-ARE-A-[SIZE=5]MASTER!!!

[SIZE=1]Thank you so much, and thanks everybody for all the help. You guys rock! =D>[/SIZE]
[/SIZE]

:)

You are welcome. Have fun.

---

