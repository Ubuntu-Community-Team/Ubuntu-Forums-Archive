---
title: "Firefox then GUI lockup"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by franklin_m on 2010-08-21
Hello,

I'm running Ubuntu Netbook Remix 10.04 lucid, kernel 2.6.32-24-generic. My system information also tells me that I'm running Gnome (2.30.2 [Ubuntu 2010-06-25]). The firefox version I'm running is 3.6.8 for ubuntu.

Occasionally when I'm surfing the net, Firefox appears to lock up. Doesn't respond, allows clicking on items, but nothing happens. Sometimes the entire Ubuntu GUI locks up as well. Can't minimize, switch to another application, etc.

I've tried going into terminal and using gprep firefox to get the processes running. Usually there are two. I then use PKILL and the process number to kill them. Occasionally it takes more than one PKILL to do it, but eventually GPREP FIREFOX shows nothing running.

However, when I return to the GUI, it is still locked.

Any ideas?
Thanks,
Frank
[email]frank.mellott@earthlink.net[/email]

---

### Post by lovinglinux on 2010-08-21
Does it happen on particular web pages or particular content like flash?

Not  enough information, but here are some things that might help:

[LIST]
[*]Install [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/") and [Adblock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865/") to block things you don't need. 
[*]Use [SQLite Optimizer]("https://addons.mozilla.org/en-US/firefox/addon/11198/") to optimize Firefox databases
[*]Make sure you have the latest proprietary video driver installed
[*]Disable the option to block web forgeries and attack sites on Firefox preferences
[/LIST]

Also see my tutorials on Firefox Optimization and Troubleshooting at [http://firefox-tutorials.blogspot.com](http://firefox-tutorials.blogspot.com)

---

### Post by mapes12 on 2010-08-21
I had a FF problem earlier today and fixed it be resetting the defaults in safe mode. Close FF then in Terminal ```
firefox -safe-mode
``` a pop up then allows you to reset certain FF functions. Make the changes you think are causing the problem. "OK" it into Safe Mode. Then close down and restart FF normally. That fixed my problem.

> Sometimes the entire Ubuntu GUI locks up as well.If this happens when FF is not running the problem could be elsewhere.

Mark

---

### Post by franklin_m on 2010-08-22
> **lovinglinux said:**
> Does it happen on particular web pages or particular content like flash?

Not  enough information, but here are some things that might help:

[LIST]
[*]Install [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/") and [Adblock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865/") to block things you don't need. 
[*]Use [SQLite Optimizer]("https://addons.mozilla.org/en-US/firefox/addon/11198/") to optimize Firefox databases
[*]Make sure you have the latest proprietary video driver installed
[*]Disable the option to block web forgeries and attack sites on Firefox preferences
[/LIST]

Also see my tutorials on Firefox Optimization and Troubleshooting at [http://firefox-tutorials.blogspot.com](http://firefox-tutorials.blogspot.com)

It's usually when there's flash content. One more thing, if I am successful in killing the processes as I described above, when I come out of it particular icons act as if they're being dragged by the mouse. For example, if I position the cursor over an icon, when I move the cursor using the mouse, the icon moves with it. I can deselect the icon by hitting escape, but nothing works. "Reboot it only thing that solves it.

hope this helps.

---

### Post by lovinglinux on 2010-08-22
Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog:

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

### Post by richs-lxh on 2010-08-22
As an alternative, just as a suggestion, my wife and I use Google Chrome on our netbooks, and as we are Youtube fans, we use Html5 instead of flash to view videos. No slowdown and no lockups.

[http://www.google.com/chrome?platform=linux](http://www.google.com/chrome?platform=linux)
[http://youtube.com/html5](http://youtube.com/html5)

Obviously if you are a Firefox fan this won't solve your problem, but at least offers an alternative.

---

### Post by richs-lxh on 2010-08-22
*edit* double post

---

### Post by franklin_m on 2010-08-22
I did everything you said...Can't thank you enough. Starting with the shockwave flash:



    File: /usr/lib/adobe-flashplugin/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r82

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
--------------------------------------------------------


then the Mozilla firefox "about" information. I did a screenshot...there's none of those detailed version info on the screen:

(should be uploaded as attachement)

----------------------------------------------------------

then the results of the commands list in terminal:

Ubuntu Architecture

Linux frank-laptop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox						install
firefox-3.0					install
firefox-3.5					install
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

getdeb.list.distUpgrade
getdeb.list.save
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
lucid-partner.list
playdeb.list
playdeb.list.distUpgrade
playdeb.list.save
ubuntu-wine-ppa-karmic.list
ubuntu-wine-ppa-karmic.list.distUpgrade
ubuntu-wine-ppa-karmic.list.save

Flash packages

adobe-flashplugin				install

Plugin locations

/usr/lib/adobe-flashplugin/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

---

### Post by lovinglinux on 2010-08-22
There is nothing wrong with your flash/firefox setup, so I think is just flash taking too much CPU and causing Firefox to become unresponsive. See [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html).

---

### Post by franklin_m on 2010-08-23
> **lovinglinux said:**
> There is nothing wrong with your flash/firefox setup, so I think is just flash taking too much CPU and causing Firefox to become unresponsive. See [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html).

Hey, can't thank you enough, I really appreciate the help. I'll mess around with the tweaks, the GPU validation seems to be the best place to start.

Frank

---

### Post by lovinglinux on 2010-08-23
> **franklin_m said:**
> Hey, can't thank you enough, I really appreciate the help.

You are welcome.

> **franklin_m said:**
> I'll mess around with the tweaks, the GPU validation seems to be the best place to start.

Frank

Indeed. If you are using Compiz, then you should try to disable it, to see if there is any improvement, since hardware acceleration doesn't work with Compiz.

---

### Post by artium on 2010-08-26
I have the same problem. (And there is another guy [here]("http://superuser.com/questions/171357/what-do-do-when-linux-gui-freezes") apparently suffering from it too).

1. I have the same Ubuntu, gnome, Firefox versions as the original poster.

2. At [first]("http://ubuntuforums.org/showthread.php?t=1556420") I thought that this was caused by the mouse, but the problem repeated itself after changing to a different model.

3. I do not think that it is caused by flash because it happens every time I startup Firefox. 
4. The only workaround that I know (which is a voodoo to me) is to right-click on the top-right corner of the screen. After this Firefox's GUI is unlocked, but the rest of the GUI is still locked. After I close Firefox (ALT-F4) the rest of the GUI is unlocked as well.

5. My CPU levels seems to be normal while running Firefox. 
6. What is Compiz and how can check if I use it or not?

7. Here is the results of the script lovinglinux gave:
[QUOTE="Ubuntu"]
Ubuntu Architecture

Linux artium-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox						install
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

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

[/QUOTE]

---

### Post by lovinglinux on 2010-08-26
> **artium said:**
> 7. Here is the results of the script lovinglinux gave:

All normal there.

Have you tried to start Firefox in safe mode, create a new profile or even a new Ubuntu user for testing?

---

### Post by artium on 2010-08-28
I tried with a new Ubuntu user, still the same.

Currently I think that it is not completely Firefox's fault. Sometimes other GUI applications cause this problem as well.

---

### Post by lovinglinux on 2010-08-28
> **artium said:**
> I tried with a new Ubuntu user, still the same.

Currently I think that it is not completely Firefox's fault. Sometimes other GUI applications cause this problem as well.

Indeed. If the problem occurs with other applications and a clean Ubuntu user, then is most likely that the problem is located somewhere else.

---

