---
title: "Flash not working."
date: 2010-08-28
forum: New to Ubuntu
---

### Post by todayisgood on 2010-08-28
So I'm trying to watch a YouTube video and I come along this little notice...

[IMG]http://i.imgur.com/tUWgw.png[/IMG]

I tried installing it through the Firefox plug-in, but it was already installed.

I then tried to install Flash Player 10 through the software center and it didn't really work. What do I do?

---

### Post by Zzl1xndd on 2010-08-28
When you attempted to install Flash Player 10 through the software centre did the install complete? or did you get an error of some kind?

---

### Post by todayisgood on 2010-08-28
There was a loading bar that stayed at 0% and said "waiting for other software managers to close"  or something like that, but I closed every other program.

---

### Post by Zzl1xndd on 2010-08-28
If the update manager, synaptic, etc. Had been going it might have caused this. If this is still happening you might want to just log out and log back in or reboot and try to install again (I know it sounds a little like Windowsy solution, but it might work).

Also are you using 32 or 64 bit Ubuntu?

---

### Post by lovinglinux on 2010-08-28
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

### Post by todayisgood on 2010-08-28
> **tweakedenigma said:**
> 
Also are you using 32 or 64 bit Ubuntu?

I do not know.

For **lovinglinux**:

**1.** I did everything up to the **about:plugins** thing, and I found that there was no Shockwave Flash. There was VLC Multimedia Plugin (compatible Totem 2.28.2), Windows Media Player Plug-in 10 (compatible; Totem), DivX® Web Player and QuickTime Plug-in 7.2.0 but *no sign* of Shockwave Flash.

**2.** [IMG]http://imgur.com/iTTdW.png[/IMG]

**3.** > Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

Firefox Packages

firefox						install
firefox-3.5					install
firefox-3.5-branding				install
firefox-3.5-gnome-support			install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.8/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

medibuntu.list
medibuntu.list.save
stebbins-handbrake-snapshots-karmic.list
stebbins-handbrake-snapshots-karmic.list.save

Flash packages

flashplugin-installer				install

Plugin locations

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/libflashplayer.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)


---

### Post by lovinglinux on 2010-08-28
Flash is installed, but there are symlinks missing. Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

BTW, you have 32bit.

---

