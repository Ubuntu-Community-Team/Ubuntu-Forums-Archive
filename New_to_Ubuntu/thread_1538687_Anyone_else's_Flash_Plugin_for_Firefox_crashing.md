---
title: "Anyone else's Flash Plugin for Firefox crashing?"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by zer010 on 2010-07-25
It seems to be happening after the latest FF upgrade. Anyone else having this problem or know a fix?

---

### Post by anantshri on 2010-07-25
just few quick info that everyone might ask... which version x64 or x32 of ubuntu you are using also which FF version and which exact version of Ubuntu i.e. ubuntu 10.04 or 9.10

---

### Post by zer010 on 2010-07-25
I'm running a "clean install" of Ubuntu 10.04 32bit.
Firefox 3.6.7
Regularly updated

---

### Post by nakama85 on 2010-07-25
yup... same issue here... interestingly enough Flash is working fine with Google Chrome though! 
Kinda irritating, not that I don't like chrome but It is simply not as powerful as Firefox as far as customization goes!

---

### Post by SunnyRabbiera on 2010-07-25
Try a flash resinstall

---

### Post by nakama85 on 2010-07-25
> **SunnyRabbiera said:**
> Try a flash resinstall

I have tried that a couple times already but still no luck.

However It is still good advice as it may help the OP and many others!

---

### Post by johnsonfarms on 2010-07-25
I am also experiencing this issue.

Ubuntu 10.04
Firefox 3.6.7

However it is working fine in Epiphany web browser.

Has anyone figured this out yet?

---

### Post by lovinglinux on 2010-07-25
It could be a bad interaction between Firefox 3.6.7 and flash, since Mozilla released Firefox 3.6.8 just two days after 3.6.7 release, in order to fix instability issues. That being said, I have no problems with flash crashing with 3.6 series.

Get [FLASH-AID](http://flash-aid-extension.blogspot.com), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture:

[Mozilla download page](https://addons.mozilla.org/en-US/firefox/addon/161939/) (might be one or more versions behind the site, due to review process).

If that doesn't help, then try to start the browser in safe mode or create a new profile to verify if the problem persists. See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by linux18 on 2010-07-25
> **lovinglinux said:**
> It could be a bad interaction between Firefox 3.6.7 and flash, since Mozilla released Firefox 3.6.8 just two days after 3.6.7 release, in order to fix instability issues. That being said, I have no problems with flash crashing with 3.6 series.

Get [FLASH-AID](http://flash-aid-extension.blogspot.com), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture:

[Mozilla download page](https://addons.mozilla.org/en-US/firefox/addon/161939/) (might be one or more versions behind the site, due to review process).

If that doesn't help, then try to start the browser in safe mode or create a new profile to verify if the problem persists. See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.
+1 for flash aid, got my flash vids up to their actual framerate and got rid of " flash plugin broken " messeges.

---

### Post by NoNameWill on 2010-07-25
Another +1 for flash-aid. Just used it to fix my problem. I couldn't run embedded youtube videos. Now I can. Other than that though flash was working in 3.6.7.

---

### Post by zer010 on 2010-07-26
I usually only get the crash on a flash game i play every now and then. I'll check out Flash-Aid. Thanks! :cool:
Dumb question.... how do I install Flash-Aid 1.09?

---

### Post by ayyork on 2010-07-26
my flash problems started when the new firefox came out 3.6.7. i believe it is .

---

### Post by lovinglinux on 2010-07-26
> **zer010 said:**
> I usually only get the crash on a flash game i play every now and then. I'll check out Flash-Aid. Thanks! :cool:
Dumb question.... how do I install Flash-Aid 1.09?

Go to [http://flash-aid-extension.blogspot.com](http://flash-aid-extension.blogspot.com). If you have a Mozilla account, just click the **Automatic Install** link on the stable channel sidebar, otherwise, click the download link next to it to download the file. The open the downloaded xpi file from Firefox menu (File >> Open File) or drag the file to Firefox. It will install automatically. Restart Firefox. It will prompt for flash cleanup and installation.

---

### Post by zer010 on 2010-07-26
Thanks, I just registered for an account for it. Thanks for the download instructions! Easy as pie!  I'll go and test Flash-Aid out...

---

### Post by peggyarmstrong on 2010-07-26
Mine is, I tried this [http://support.mozilla.com/en-US/kb/Managing+the+Flash+Plugin?style_mode=inproduct#Updating_Flash](http://support.mozilla.com/en-US/kb/Managing+the+Flash+Plugin?style_mode=inproduct#Updating_Flash)   But still not working

---

### Post by zer010 on 2010-07-26
Nope, Adobe Flash plugin just crashed again :(......
Just as a little more info, it's crashing on Robot Unicorn Attack  [http://games.adultswim.com/robot-unicorn-attack-twitchy-online-game.html](http://games.adultswim.com/robot-unicorn-attack-twitchy-online-game.html)

Edit: According to Mozilla, Flash is up to date.

---

### Post by lovinglinux on 2010-07-26
> **zer010 said:**
> I usually only get the crash on a flash game i play every now and then. I'll check out Flash-Aid. Thanks! :cool:
Dumb question.... how do I install Flash-Aid 1.09?

I just uploaded 1.0.10 to fix an issue with the auto launcher.

---

### Post by zer010 on 2010-07-26
ok, let me try that then
It works like a charm!
Great work!
Much appreciated!
Even topped my previous scores by a mile!

Edit: For me this problem is Solved!
Thanks again!

---

### Post by lovinglinux on 2010-07-26
> **zer010 said:**
> ok, let me try that then
It works like a charm!
Great work!
Much appreciated!
Even topped my previous scores by a mile!

Edit: For me this problem is Solved!
Thanks again!

You are welcome.

---

### Post by charles woodward on 2010-07-30
I'd tried everything - reloading the flash plugin, eventually removing and re-installing firefox - but flash-aid solved the problem in seconds.  (still have to work out where the sounds gone - but still)

---

### Post by charles woodward on 2010-07-30
solved the sound as well - somehow I'd switched if off - 
also I ought to update my profile - I'm fully up to date with everything

---

### Post by GoRien on 2010-07-30
Seems not just my Firefox suffering from flash issue. Curious before 3.6 series I have no any problem. Same version of flash plug-in works like charm with Opera 10.60.

I will try that flash-aid because I need working flash for Firefox.

---

### Post by p.s. on 2010-07-30
Glad to hear most people got it sorted out. It was already mentioned near the top, but when Flash isn't working in Firefox (which it frequently isn't for me) I usually just use Chrome, despite my reservations about it as a browser.

---

### Post by GoRien on 2010-07-30
Great! Flash-aid helped. I can use flash with Firefox again. :)

---

### Post by lovinglinux on 2010-07-30
> **GoRien said:**
> Great! Flash-aid helped. I can use flash with Firefox again. :)

;)

---

### Post by halw on 2010-08-07
> **lovinglinux said:**
> I just uploaded 1.0.10 to fix an issue with the auto launcher.

Just tried running Flash-Aid, auto launcher not working.

---

### Post by lovinglinux on 2010-08-07
> **halw said:**
> Just tried running Flash-Aid, auto launcher not working.

What version?

You can launch it manually from the statusbar or toolbar icons.

---

### Post by halw on 2010-08-07
v1.0.10

```
hlw@p4p800:~$ #!/bin/bash
hlw@p4p800:~$ 
hlw@p4p800:~$ echo "Please wait...DON'T CLOSE THIS TERMINAL!"
bash: !": event not found
hlw@p4p800:~$ sudo apt-get --yes purge swfdec-mozilla
[sudo] password for hlw: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
```

Got the above results when trying to run script copied into terminal.

---

### Post by lovinglinux on 2010-08-07
> **halw said:**
> v1.0.10

```
hlw@p4p800:~$ #!/bin/bash
hlw@p4p800:~$ 
hlw@p4p800:~$ echo "Please wait...DON'T CLOSE THIS TERMINAL!"
bash: !": event not found
hlw@p4p800:~$ sudo apt-get --yes purge swfdec-mozilla
[sudo] password for hlw: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
```

Got the above results when trying to run script copied into terminal.

Copy the commands before the terminal, without the #!/bin/bash line.

---

### Post by halw on 2010-08-07
> **lovinglinux said:**
> Copy the commands before the terminal, without the #!/bin/bash line.

That did it. Thanks.

---

### Post by rawlins02 on 2010-08-07
New poster here.....running new fresh install of Lucid Lynx.  Firefox 3.6.8.   Flash works, but clicking fullscreen crashes Flash (but NOT the browser) with message:  "The Adobe Flash plugin has crashed"   Fullscreen was working fine until last day or so.  Assume this is related to new version 3.6.x of Firefox that I think came in recent update.

I downloaded Flash-Aid, opened it in File -> Open file.  I'm not certain it installed, as it quickly came back to a screen that said "Firefox must be restarted"  How to tell?

---

### Post by linux18 on 2010-08-07
> **rawlins02 said:**
> New poster here.....running new fresh install of Lucid Lynx.  Firefox 3.6.8.   Flash works, but clicking fullscreen crashes Flash (but NOT the browser) with message:  "The Adobe Flash plugin has crashed"   Fullscreen was working fine until last day or so.  Assume this is related to new version 3.6.x of Firefox that I think came in recent update.

I downloaded Flash-Aid, opened it in File -> Open file.  I'm not certain it installed, as it quickly came back to a screen that said "Firefox must be restarted"  How to tell?
flash aid launches when you start firefox, not by opening the file. if their is no icon in firefox you have to redownload

---

### Post by rawlins02 on 2010-08-07
I now am able to have flash application run in fullscreen.  I just did rightclick on the video ->  Settings -> and then unselect "enable hardware acceleration".

---

### Post by lovinglinux on 2010-08-07
> **halw said:**
> That did it. Thanks.

You are welcome.

> **rawlins02 said:**
> New poster here.....running new fresh install of Lucid Lynx.  Firefox 3.6.8.   Flash works, but clicking fullscreen crashes Flash (but NOT the browser) with message:  "The Adobe Flash plugin has crashed"   Fullscreen was working fine until last day or so.  Assume this is related to new version 3.6.x of Firefox that I think came in recent update.

I downloaded Flash-Aid, opened it in File -> Open file.  I'm not certain it installed, as it quickly came back to a screen that said "Firefox must be restarted"  How to tell?

After installing the extension, it will prompt for flash installation like this:

[IMG]http://tinyurl.com/26t9nlw[/IMG]


Then it will show the commands that will be executed:

[IMG]http://tinyurl.com/253ypnv[/IMG]

Then a terminal will be started to execute the script:

[IMG]http://tinyurl.com/2ecrkl6[/IMG]

If you haven't seen all of that, then start the installation process from the FLASH-AID statusbar or toolbar icons.

---

### Post by Kellemora on 2010-08-07
Firefox began having problems with Flash when they introduced version 3.6.4!
I posted about this many times, but few seemed to believe me.
Firefox jumped quickly to version 3.6.5 for about 8 to 10 hours, then jumped up to 3.6.6 and held there for a few days, then jumped up to 3.6.7 and almost overnight again to 3.6.8..........
But Firefox HAS NOT been compatible with Flash Player since 3.6.4.....

I solved the problem completely by rolling back to version 3.6.3 and 100% of the problems went away and have not returned since.

You Tube and many others have jumped up to Flash 10.1,
They had a major security leak in version 10.0..... 
Unfortunately, Shockwave never wrote a 64 bit version.
Although their web site makes it APPEAR they did.
They say it runs on AMD64, but what they don't tell you is that's only if you've dumbed down to a 32 bit OS in order to use it.

In any case, if you want Firefox to work with Flash, roll back to version 3.6.3 and you'll be home free again!

TTUL
Gary

---

### Post by rawlins02 on 2010-08-08
Fullscreen mode of video running in Firefox 3.6.4 with Flash 10.1 is jumpy. Like it's overwhelming processor. Videos play fine when not in fullscreen.  Yesterday I had to disabled hardware acceleration just to keep fullscreen from crashing.  Might try going back to 3.6.3.

---

### Post by mattgreen on 2010-08-11
I've just run FLASH-AID on Ubuntu 10.04 Firefox 3.6.8 and it has fixed my problem.

My problem was that after upgrading from Ubuntu 9.10 Flash would not work in Firefox - I just got the "This plugin has crashed" message.

So now all is well. Thanks to all who came up with the solution.

---

### Post by Murume on 2010-08-25
I have been having problems with flash in Firefox for the last couple of months. My issue seems to be a bit different to others that I have seen on the forums. Basically what happens is I try and maximise the flash video and the screen goes black and the sound keeps on going. I doesn't always occur but I noticed that as soon as I open another tab or minimise the Firefox window with a flash video playing when I go back to maximise the flash video again the issue occurs.

I was running 9.10 (32bit) and the Flash-Aid plugin didn't help fix this issue. I have now upgraded to 10.04 (32bit) and I tried re-running Flash-Aid but it still did fix the issue. The strange thing is I have tried Chrome and I get a similar issue. In Chrome the picture on the video freezes (no black screen) when I try to maximise.

Any help with this would be greatly appreciated. Thanks for your help

---

### Post by lovinglinux on 2010-08-26
> **Murume said:**
> I have been having problems with flash in Firefox for the last couple of months. My issue seems to be a bit different to others that I have seen on the forums. Basically what happens is I try and maximise the flash video and the screen goes black and the sound keeps on going. I doesn't always occur but I noticed that as soon as I open another tab or minimise the Firefox window with a flash video playing when I go back to maximise the flash video again the issue occurs.

I was running 9.10 (32bit) and the Flash-Aid plugin didn't help fix this issue. I have now upgraded to 10.04 (32bit) and I tried re-running Flash-Aid but it still did fix the issue. The strange thing is I have tried Chrome and I get a similar issue. In Chrome the picture on the video freezes (no black screen) when I try to maximise.

Any help with this would be greatly appreciated. Thanks for your help

See the third item on [this list]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html").

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

### Post by Murume on 2010-08-26
Thanks for getting back to me. I have noticed that if I minimise Firefox once the video goes black the video will popup in full screen and play fine. Here is the out put as requested. I noticed a couple of errors in there but I am pretty new with Ubuntu so I don't know what they mean.

```
Ubuntu Architecture

Linux john-desktop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

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
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.8/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

google-chrome.list
google-chrome.list.distUpgrade
iplist.list
iplist.list.distUpgrade
karmic-partner.list
karmic-partner.list.distUpgrade
karmic-partner.list.save

Flash packages

flashplugin-installer                install
flashplugin-nonfree                install

Plugin locations

/usr/lib/firefox-addons/plugins/libflashplayer.so
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

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
```

---

### Post by lovinglinux on 2010-08-26
> **Murume said:**
> Thanks for getting back to me. I have noticed that if I minimise Firefox once the video goes black the video will popup in full screen and play fine. Here is the out put as requested. I noticed a couple of errors in there but I am pretty new with Ubuntu so I don't know what they mean.

```
Ubuntu Architecture

Linux john-desktop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

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
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.8/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

google-chrome.list
google-chrome.list.distUpgrade
iplist.list
iplist.list.distUpgrade
karmic-partner.list
karmic-partner.list.distUpgrade
karmic-partner.list.save

Flash packages

flashplugin-installer                install
flashplugin-nonfree                install

Plugin locations

/usr/lib/firefox-addons/plugins/libflashplayer.so
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

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
```

Those errors are expected on a normal machine. They are there to catch different setups. There is nothing wrong with your Firefox and Flash installations, so the problem is somewhere else. 

There is no need to run FLASH-AID again. It already did what it was supposed to do. Nevertheless, I don't see the flash version on your report. Please post it. It should be 10.1.82.

Do you have video effects enabled (Compiz)? If yes, have you tried to disable them?

Also try to create a new Firefox profile just for testing. Check if flash behaves the same way. To do that, close Firefox and start it using the command below:

```
firefox -P
```

If it behaves the same, then create a new Ubuntu user just for testing. Sometimes the user Gnome settings can cause such issues.

---

### Post by Murume on 2010-08-26
The Flash version I have running is Flash 10.1.82.

I think I have fixed the issue. Something strange happened when I launched Compiz the desktop seemed to kind of refresh and I noticed that I now have 4 workspace shortcuts in the bottom left hand corner (was only 2 before). This seems to have now fixed my problem as I no longer get the black screen on flash videos and they maximise faster. I notice that windows have effects when they are minimised now as well.

It must have been something to do with my user settings but I really have no idea what was happening. I think Flash-Aid definitely helped though. I will have to try out your suggestion on creating the new profiles if I run into any more issues. Thanks a lot for your help!

---

### Post by ruehara on 2010-08-26
Disabling video acceleration worked a treat.

Thanks Rawlins02

---

### Post by Visible Spirit on 2010-09-23
Hi LovingLinux (as well as the rest of the folks out there :) ),


I've been frustrated as well since upgrading Ff some time ago. I've read this thread and can't seem to solve the problem of flash locking up my browsers (Ff v3.6.10 and Epiphany v2.22.2 (Gecko v1.9)). A good example would be; I go to YouTube[dot]com, click on a video, the page loads with exception to the video itself. In the process of dwnldg the flash video the browser grays over and locks up. My only recourse is to close the browser via the "close button" in the upper right hand corner which results in a crashed session. When closing the browser I always get the following warning relative to whatever website is not responding.

[ATTACH]170388[/ATTACH]

On problematic websites when doing a session restore, the same page will load and repeat the problem. I must then uncheck/remove that particular page during the session restore process to regain a working browser. The process is identical when I use the Epiphany browser.

Interestingly enough, prior to closing/crashing the browser (as described above), I can middle click the problem causing site tab which will remove said tab from the restore session dialog box only; eliminating the need to uncheck such. (I've set the middle click button to close a tab when the cursor is placed on it and I click the middle mouse button.)

Below is posted info about my machine such as you requested of Murume, in the hope that it may help to resolve my problem.

Any help resolving this issue will be greatly appreciated. Thanks for taking the time to read my posting. ;)


Regards,
Visible Spirit

PS - I noticed several ERRORS in the terminal report below. Don't know what they mean though.

---
**Shockwave Flash**

    File: /usr/lib/adobe-flashplugin/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r85

MIME Type 	| Description 	| Suffixes 	| Enabled
application/x-shockwave-flash 	| Shockwave Flash 	| swf 	| Yes
application/futuresplash 	| FutureSplash Player 	| spl 	| Yes

---
**About Firefox**

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.10) Gecko/20100915 Ubuntu/8.04 (hardy)
Firefox/3.6.10 - Build ID: 20100915193946

---
```
[B]Ubuntu Architecture
[/B]
Linux ubuntu 2.6.24-28-rt #1 SMP PREEMPT RT Thu Sep 16 17:18:03 UTC 2010 i686 GNU/Linux

**Ubuntu Version**

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.4 LTS"

**Firefox Packages**

firefox						install
firefox-3.0					deinstall
firefox-branding				install
firefox-gnome-support				install

**Firefox binaries**

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.10/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

**Firefox divertion**

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

**Sources**

medibuntu.list
medibuntu.list.save
pidgin-ppa.list
pidgin-ppa.list.save

**Flash packages**

adobe-flashplugin				install
libflash-mozplugin				install
libflash0c2					install

**Plugin locations**

/usr/lib/adobe-flashplugin/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

**Flash symlinks**

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
```

eof...

---

### Post by lovinglinux on 2010-09-24
> **Visible Spirit said:**
> Hi LovingLinux (as well as the rest of the folks out there :) ),


I've been frustrated as well since upgrading Ff some time ago. I've read this thread and can't seem to solve the problem of flash locking up my browsers (Ff v3.6.10 and Epiphany v2.22.2 (Gecko v1.9)). A good example would be; I go to YouTube[dot]com, click on a video, the page loads with exception to the video itself. In the process of dwnldg the flash video the browser grays over and locks up. My only recourse is to close the browser via the "close button" in the upper right hand corner which results in a crashed session. When closing the browser I always get the following warning relative to whatever website is not responding.

[ATTACH]170388[/ATTACH]

On problematic websites when doing a session restore, the same page will load and repeat the problem. I must then uncheck/remove that particular page during the session restore process to regain a working browser. The process is identical when I use the Epiphany browser.

Interestingly enough, prior to closing/crashing the browser (as described above), I can middle click the problem causing site tab which will remove said tab from the restore session dialog box only; eliminating the need to uncheck such. (I've set the middle click button to close a tab when the cursor is placed on it and I click the middle mouse button.)

Below is posted info about my machine such as you requested of Murume, in the hope that it may help to resolve my problem.

Any help resolving this issue will be greatly appreciated. Thanks for taking the time to read my posting. ;)


Regards,
Visible Spirit

PS - I noticed several ERRORS in the terminal report below. Don't know what they mean though.

The errors i the report are expected.

The only weird thing I see on it is the presence of **libflash-mozplugin** and **libflash0c2**, which I never saw before. Try to uninstall them and see if the problem persists. When doing that, make sure nothing important is removed due to dependency on those packages.

```
sudo apt-get purge libflash-mozplugin
sudo apt-get purge libflash0c2
```

Don't forget to restart the browser after applying any modifications to flash, so the browser can reload the plugin.

---

### Post by Visible Spirit on 2010-09-24
> **lovinglinux said:**
> The errors i the report are expected.

The only weird thing I see on it is the presence of **libflash-mozplugin** and **libflash0c2**, which I never saw before. Try to uninstall them and see if the problem persists. When doing that, make sure nothing important is removed due to dependency on those packages.

```
sudo apt-get purge libflash-mozplugin
sudo apt-get purge libflash0c2
```

Don't forget to restart the browser after applying any modifications to flash, so the browser can reload the plugin.


Thanks for the quick reply LovingLinux. I did as you suggested and it seems to have resolved the issue. I went to YouTube directly after to test and all played fine without a hitch.

The **libflash-mozplugin** was dependent on the **libflash0c2**. The later didn't have any dependencies. Oddly enough, the former was a plugin for "Flash Movie Player v0.4.12" .  Anyway, I tried both browsers since Epiphany runs on the same engine as Ff and each worked fine.

Thank you very much for reviewing my post and finding the discrepancy. ;)

Amazing what an old file will do to turn ones hair gray prematurely! :-o
I wonder why it wasn't removed/purged after various upgrades, but such as it was.

Kudos... ! You made my day today! ;)


Regards,
Visible Spirit... 8-)


Below is my terminal session for reference if needed by anyone.
```
XXXXXXXXXX@ubuntu:~$ sudo apt-get purge libflash-mozplugin
[sudo] password for XXXXXXXXXX: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libflash0c2 libaccess-bridge-java rhino
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libflash-mozplugin*
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
After this operation, 102kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 286828 files and directories currently installed.)
Removing libflash-mozplugin ...
Purging configuration files for libflash-mozplugin ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
XXXXXXXXXX@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libflash0c2 libaccess-bridge-java rhino
The following packages will be REMOVED:
  libaccess-bridge-java libflash0c2 rhino
0 upgraded, 0 newly installed, 3 to remove and 4 not upgraded.
After this operation, 1581kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 286820 files and directories currently installed.)
Removing libaccess-bridge-java ...
Removing libflash0c2 ...
Removing rhino ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
XXXXXXXXXX@ubuntu:~$ exit
```

---

### Post by Kellemora on 2010-09-26
All I can say is Flash-Aid has caused me tons of grief that is virtually impossible to resolve.

The program developer worked with me to try and get Flash back to normal, and it appears to be for a short time.

The SAD thing is, running 64 bit Flash had never caused me a single problem, the only thing I couldn't do was see the You Tube videos linked on FaceBook, but could see them on You Tube itself.

NOW, Flash CRASHES continually, Flash does NOT unload from any web browser and keeps building up to a crash.
I have to use HTOP to KILL the Flash Plug-in and NS something or other 15 to 20 times a day.

I had NONE of these problems before Flash-Aid DELETED my 64 bit Flash Player!

The program SHOULD have merely disabled it, NOT REMOVED IT, because I have found no place to get it back from.

Although FireFox on Linux works OK, the Windows version of FireFox has been royally messed up since the release of 3.6.4........ Serious memory loss problems with it when using Flash.

It appears my only alternative to correct the problems caused by Flash-Aid is to buy a new hard drive and start over using 32 bit Ubuntu 8.04 so I can make the 32 bit version of Flash work.

I wish I NEVER TRIED Flash-Aid, simple as that!

The developer said it's ONLY an installer!

It's also a FILE DELETER that removed a VERY VALUABLE program, a perfectly working 64 bit version of Flash Player that never gave me a single problem with my daily work.

TTUL
Gary

---

### Post by lovinglinux on 2010-09-26
> **Kellemora said:**
> All I can say is Flash-Aid has caused me tons of grief that is virtually impossible to resolve.

The program developer worked with me to try and get Flash back to normal, and it appears to be for a short time.

The SAD thing is, running 64 bit Flash had never caused me a single problem, the only thing I couldn't do was see the You Tube videos linked on FaceBook, but could see them on You Tube itself.

NOW, Flash CRASHES continually, Flash does NOT unload from any web browser and keeps building up to a crash.
I have to use HTOP to KILL the Flash Plug-in and NS something or other 15 to 20 times a day.

I had NONE of these problems before Flash-Aid DELETED my 64 bit Flash Player!

The program SHOULD have merely disabled it, NOT REMOVED IT, because I have found no place to get it back from.

Although FireFox on Linux works OK, the Windows version of FireFox has been royally messed up since the release of 3.6.4........ Serious memory loss problems with it when using Flash.

It appears my only alternative to correct the problems caused by Flash-Aid is to buy a new hard drive and start over using 32 bit Ubuntu 8.04 so I can make the 32 bit version of Flash work.

I wish I NEVER TRIED Flash-Aid, simple as that!

The developer said it's ONLY an installer!

It's also a FILE DELETER that removed a VERY VALUABLE program, a perfectly working 64 bit version of Flash Player that never gave me a single problem with my daily work.

TTUL
Gary

First of all, get [FLASH-AID 1.0.14 ]("https://addons.mozilla.org/en-US/firefox/addon/161939/versions"). It supports the installation of the new 64bit version of flash.

I'm starting to get really uncomfortable with your multiple threads attacking Firefox and FLASH-AID, specially considering I have spent hours personally supporting you by e-mail, fixing problems that are not FLASH-AID fault. You should consider upgrading your system, because Ubuntu 8.04 doesn't even have Flash 10.

Since our last conversation by e-mail, I was considering your issue as fixed. If you weren't satisfied with the solution provided by me, you could simply ask by e-mail to help you find the 64bit version and to help you install it. I would do that, even considering you haven't been to most easy person to deal with and that version had a critical vulnerability and shouldn't be used. But instead of that you come to the forum to make drama again and bash my application. Seriously?

For the record, FLASH-AID is about to reach 30.000 downloads and currently have about 5.000 daily users and the only complain I received comes from you, in a way that I consider at least impolite. 

FLASH-AID removes conflicting plugins and install the proper version from the repositories or from Adobe. That is clearly stated in the extension page. Besides, the extension also shows you which commands will be executed before taking any actions, which includes the removal of any flash version manually saved to your mozilla folder. 

Have a nice day.

---

### Post by Visible Spirit on 2010-10-05
Hmmmm... sounds like someone is getting gray hair trying to figure out issues that seem to go beyond the norm from the replies.

All I can say about Flash-Aid is that it cleaned up and removed the old and redundant excess flash installs and a couple unneeded plug-ins. Soooo... my consensus is ...*it works just as it says on the box*!

I have it installed and never once considered it a problem. Quite the opposite! My problem (as described above in my original post) was a preexisting one long before I installed the Flash-Aid add-on. I did so in the hope that it *would* resolve my problem. In part it did! After installing Flash-aid, my browser wasn't as sluggish and actually loaded a bit faster than usual.

Nothings perfect. The proof is in my post above and lovinglinuxes kind and quick response in reviewing it and locating the real problem. Many developers wouldn't go the extra or even respond to a thread already marked "solved", so my hat's off to lovinglinux! Just simply reviewing *this* thread tells me there is a concerned and active developer at work here, and is the reason I posted in it even *after* it was marked "solved".

We all have bad days, and I'd be lying to say I haven't unloaded on a developer or two, as well as unsuspecting helpful folks after a prolonged problem has pushed my patience out the window. Most will simply ignore rants and those behind them. But once in a while, along comes a tempered person who has the wherewithal to perceive and understand ones frustration and continue to offer help even after a period of complaints and misfortunes brought about by said frustrations and the inability to resolve a problem with a simple solution.

Sometimes it pays to sit back and review not only the problem, but ones approach to it as well as the help that's been given in the process. It's not easy being humble when we unwittingly unload on the very ones attempting to help us. The hardest thing for me, is to admit I was wrong when I've stepped on my own toes and blamed someone else for my shortcomings or lack of composure. Sometimes a bit of 'humble pie' goes a long way toward finding a solution to ones problem by showing I'm only human and have my breaking points, yet I'm big enough to apologize for my shortsighted outbursts, move beyond them, and continue to work with those that offer help, ...if I haven't worn out my welcome with them that is. ;)

---
The above is nothing more than my opinion and is offered as "Food for thought". Nothing more. Take it for what it's worth in the hopes that all can find a solution to their problem(s) and others are still willing to help that have the knowledge and experience to do so. We all need one another to some degree weather we see it or not at the time. Sometimes a relationship patch is far more valuable than 10 OS patches. As noted, this is only my opinion. I may have inadvertently opened a proverbial can-of-worms here with my opinion, ...however, if that's the case, I won't be putting the lid on it any time soon. I have more important things to do than to debate with someone my opinion, which has been clearly stated here.

I hope my comment here is helpful in regaining whatever has been lost to those in need. If not, weeeell... maybe you should read it again! ;)

Rants only prove we're human and don't have all the answers. Sometimes turning over just one more stone ...reveals what we're looking for.

On that note...

Have a great day today, ...and a better one tomorrow! :)


Regards,
Visible Spirit

---

### Post by lovinglinux on 2010-10-06
> **Visible Spirit said:**
> Hmmmm... sounds like someone is getting gray hair trying to figure out issues that seem to go beyond the norm from the replies.

All I can say about Flash-Aid is that it cleaned up and removed the old and redundant excess flash installs and a couple unneeded plug-ins. Soooo... my consensus is ...*it works just as it says on the box*!

I have it installed and never once considered it a problem. Quite the opposite! My problem (as described above in my original post) was a preexisting one long before I installed the Flash-Aid add-on. I did so in the hope that it *would* resolve my problem. In part it did! After installing Flash-aid, my browser wasn't as sluggish and actually loaded a bit faster than usual.

Nothings perfect. The proof is in my post above and lovinglinuxes kind and quick response in reviewing it and locating the real problem. Many developers wouldn't go the extra or even respond to a thread already marked "solved", so my hat's off to lovinglinux! Just simply reviewing *this* thread tells me there is a concerned and active developer at work here, and is the reason I posted in it even *after* it was marked "solved".

We all have bad days, and I'd be lying to say I haven't unloaded on a developer or two, as well as unsuspecting helpful folks after a prolonged problem has pushed my patience out the window. Most will simply ignore rants and those behind them. But once in a while, along comes a tempered person who has the wherewithal to perceive and understand ones frustration and continue to offer help even after a period of complaints and misfortunes brought about by said frustrations and the inability to resolve a problem with a simple solution.

Sometimes it pays to sit back and review not only the problem, but ones approach to it as well as the help that's been given in the process. It's not easy being humble when we unwittingly unload on the very ones attempting to help us. The hardest thing for me, is to admit I was wrong when I've stepped on my own toes and blamed someone else for my shortcomings or lack of composure. Sometimes a bit of 'humble pie' goes a long way toward finding a solution to ones problem by showing I'm only human and have my breaking points, yet I'm big enough to apologize for my shortsighted outbursts, move beyond them, and continue to work with those that offer help, ...if I haven't worn out my welcome with them that is. ;)

---
The above is nothing more than my opinion and is offered as "Food for thought". Nothing more. Take it for what it's worth in the hopes that all can find a solution to their problem(s) and others are still willing to help that have the knowledge and experience to do so. We all need one another to some degree weather we see it or not at the time. Sometimes a relationship patch is far more valuable than 10 OS patches. As noted, this is only my opinion. I may have inadvertently opened a proverbial can-of-worms here with my opinion, ...however, if that's the case, I won't be putting the lid on it any time soon. I have more important things to do than to debate with someone my opinion, which has been clearly stated here.

I hope my comment here is helpful in regaining whatever has been lost to those in need. If not, weeeell... maybe you should read it again! ;)

Rants only prove we're human and don't have all the answers. Sometimes turning over just one more stone ...reveals what we're looking for.

On that note...

Have a great day today, ...and a better one tomorrow! :)


Regards,
Visible Spirit

Thanks for your comments.

BTW, if Kellemora is still reading this, please get version 1.0.14 of FLASH-AID. Adobe has changed the url for the new preview release of square 64bit, so version 1.0.13 is partially broken. This only affects 64bit users. 

Mozilla hasn't approved it yet, so you need to get from one of the links below:

[https://addons.mozilla.org/en-US/firefox/addon/161939/versions/](https://addons.mozilla.org/en-US/firefox/addon/161939/versions/)
[http://github.com/lovinglinux/flash-aid/downloads](http://github.com/lovinglinux/flash-aid/downloads)

---

### Post by mayooresan on 2010-10-06
no wonder Steve Jobs having big problem with Flash.. Hope HTML 5 would bring up the essense of Flash up soon.

---

### Post by Kellemora on 2010-10-07
To Loving Linux

I'M ELATED NOW!  EVERYTHING WORKS PERFECTLY AND BETTER THAN BEFORE AS WELL!

I hated to sound harsh, but the facts were the facts.
Firefox and Flash both worked perfectly except for one minor thing.
And I appreciated the help you gave to me to try and get it going.
But each thing we did just made things go downhill even further.

However, I'm now posting to say that I am ELATED with your new installer version 1.0.14............
Not only do I have my much faster 64 bit Flash Player back, but I'm having no more Crashes, no more Hanging up requiring HTop to Kill the ns wrapper.
AND, dig this, FaceBook Video's now play too!

As far as Ubuntu 10.04.1 goes, we have yet to get it to work right on any of the 5 computers I've tried it on.
On one computer we get the white vertical bars after about 1/2 hour, even with screensaver turned off.
On another computer, it locks up after install and during reboot.
On another, it boots up, gets almost to the log-in screen, then goes black.
I have downloaded so many different copies, checked them, tried CD's, DVD's, USB Sticks, and even an on-line upgrade from the Package Manager.
The computers are besides the built-ups which are 2 Asus machines and 1 BioStar.  The off the shelves are a Dell, an HP pavilion, E-Machine and a 2 Compaq machines.
ALL of them have Ubuntu 8.04 working perfectly on them, some are triple boot to Debian and the Doze.  The former CentOs partition is what was cleaned off to make room for 10.04 and later 10.04.1.......

I'll stick with my perfectly working 8.04 until it's no longer supported, then I'll move over to Debian if they have not fixed the problems with 10.04.1 or higher, by then.

TTUL
Gary

---

### Post by lovinglinux on 2010-10-07
> **Kellemora said:**
> To Loving Linux

I'M ELATED NOW!  EVERYTHING WORKS PERFECTLY AND BETTER THAN BEFORE AS WELL!

I hated to sound harsh, but the facts were the facts.
Firefox and Flash both worked perfectly except for one minor thing.
And I appreciated the help you gave to me to try and get it going.
But each thing we did just made things go downhill even further.

However, I'm now posting to say that I am ELATED with your new installer version 1.0.14............
Not only do I have my much faster 64 bit Flash Player back, but I'm having no more Crashes, no more Hanging up requiring HTop to Kill the ns wrapper.
AND, dig this, FaceBook Video's now play too!

As far as Ubuntu 10.04.1 goes, we have yet to get it to work right on any of the 5 computers I've tried it on.
On one computer we get the white vertical bars after about 1/2 hour, even with screensaver turned off.
On another computer, it locks up after install and during reboot.
On another, it boots up, gets almost to the log-in screen, then goes black.
I have downloaded so many different copies, checked them, tried CD's, DVD's, USB Sticks, and even an on-line upgrade from the Package Manager.
The computers are besides the built-ups which are 2 Asus machines and 1 BioStar.  The off the shelves are a Dell, an HP pavilion, E-Machine and a 2 Compaq machines.
ALL of them have Ubuntu 8.04 working perfectly on them, some are triple boot to Debian and the Doze.  The former CentOs partition is what was cleaned off to make room for 10.04 and later 10.04.1.......

I'll stick with my perfectly working 8.04 until it's no longer supported, then I'll move over to Debian if they have not fixed the problems with 10.04.1 or higher, by then.

TTUL
Gary

Thanks for the heads up. I'm glad is working now.

---

### Post by zer010 on 2010-10-13
ok, I don't know if this an issue with flash or not, but it seems that any flash based audio stutters. What's up with this? the only "help" i can find includes getting the latest flash and updating IE. what to do?

---

### Post by SubCool on 2010-10-15
> **lovinglinux said:**
> It could be a bad interaction between Firefox 3.6.7 and flash, since Mozilla released Firefox 3.6.8 just two days after 3.6.7 release, in order to fix instability issues. That being said, I have no problems with flash crashing with 3.6 series.

Get [FLASH-AID](http://flash-aid-extension.blogspot.com), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture:

[Mozilla download page](https://addons.mozilla.org/en-US/firefox/addon/161939/) (might be one or more versions behind the site, due to review process).

If that doesn't help, then try to start the browser in safe mode or create a new profile to verify if the problem persists. See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

Thank You

---

### Post by zer010 on 2010-10-15
I hate to say this, but every now and then I still get a Flash plug-in crash. :(
Even after installing Flash-Aid. It's nowhere near as bad as it was, but it's still annoying.

---

### Post by lovinglinux on 2010-10-15
> **zer010 said:**
> I hate to say this, but every now and then I still get a Flash plug-in crash. :(
Even after installing Flash-Aid. It's nowhere near as bad as it was, but it's still annoying.

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

### Post by trukker on 2010-10-16
Used Flash-Aid Addon... worked like a charm...

Well done!

---

### Post by zer010 on 2010-10-16
Shockwave Flash
 File: /usr/lib/flashplugin-installer/libflashplayer.so
 Version: 
 Shockwave Flash 10.1 r85

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.10) Gecko/20100915 Ubuntu/10.04 (lucid) Firefox/3.6.10

Ubuntu Architecture

Linux 0home 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox                        install
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

ubuntu-wine-ppa-lucid.list
ubuntu-wine-ppa-lucid.list.save

Flash packages

flashplugin-installer                install
flashplugin-nonfree                install

Plugin locations

/usr/lib/firefox-addons/plugins/libflashplayer.so
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

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

---

### Post by lovinglinux on 2010-10-16
> **zer010 said:**
> Shockwave Flash
 File: /usr/lib/flashplugin-installer/libflashplayer.so
 Version: 
 Shockwave Flash 10.1 r85...

Nothing wrong with your installation. Where does it crash?

---

### Post by zer010 on 2010-10-16
It's pretty random. Anything from video to streaming radio. There's one stress test I can think of that made it crash consistently before. A flash game...robot unicorn. I'll play it and see if it crashes. I'll report back.

---

### Post by zer010 on 2010-10-16
Ok, after playing for a little bit, it did indeed crash. I sent the crash report, but is there any way I can see what exactly is sent?  I'm guessing it's not unlike the report that you had me create.

---

### Post by Nightstrike2009 on 2010-10-16
Mine works fine try downloading the deb from here:

[http://get.adobe.com/flashplayer/otherversions/]("http://get.adobe.com/flashplayer/otherversions/")

Step 1: Linux
Step 2: Flash Player 10.1 for Linux (Deb)

Then hit "download now" and install the .deb by double clicking after downloading thats what I did it works fine for me on Ubuntu 10.10 :-)

---

### Post by zer010 on 2010-10-16
I'm using 10.04, but I might try that. Thanks for the link! 8)

---

### Post by lovinglinux on 2010-10-17
> **zer010 said:**
> I'm using 10.04, but I might try that. Thanks for the link! 8)

10.1 is the flash version, not the Ubuntu version. It works for Ubuntu 10.04 too, nevertheless, is the same version available from the repositories, that you have already installed.

---

### Post by YoHell on 2010-10-17
Hey there! 

Flash has been misbehaving on my system despite your flash-aid magic. I was planning to post that as soon as a web page is doing something flashy the window becomes nearly unresponsive (=completely unusable), and that clicking the X to close the will actually close window once FF gets around to it (~10s later) and not crashing my session or any other open FF windows, and that the CPU usage stays at a leisurely 1% for the whole duration.

However, as I tried to validate this just before submitting, I see that the problem has changed since yesterday and that I'm now getting a plain white rectangle instead of the youtube player, and no crashing involved.

Nevertheless, I'd still appreciate any help with sorting this out.

Here's me: :confused:



Details, as per instructions:

1 - Flash version:
    File: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r85


2 - Firefox version and architecture
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.10) Gecko/20100915 Ubuntu/10.04 (lucid) Firefox/3.6.10


3 - System info 
Ubuntu Architecture

Linux lekrum 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox						install
firefox-3.0					install
firefox-3.0-gnome-support			install
firefox-3.5					install
firefox-3.5-branding				install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.10/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

medibuntu.list
medibuntu.list.distUpgrade

Flash packages

flashplugin-installer				install
flashplugin-nonfree				install

Plugin locations

/usr/lib/firefox-addons/plugins/libflashplayer.so
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

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

---

### Post by lovinglinux on 2010-10-17
> **YoHell said:**
> Hey there! 

Flash has been misbehaving on my system despite your flash-aid magic. I was planning to post that as soon as a web page is doing something flashy the window becomes nearly unresponsive (=completely unusable), and that clicking the X to close the will actually close window once FF gets around to it (~10s later) and not crashing my session or any other open FF windows, and that the CPU usage stays at a leisurely 1% for the whole duration.

However, as I tried to validate this just before submitting, I see that the problem has changed since yesterday and that I'm now getting a plain white rectangle instead of the youtube player, and no crashing involved.

Nevertheless, I'd still appreciate any help with sorting this out.

Here's me: :confused:

Nothing wrong on your report either.

Close Firefox and delete the folders **.adobe** and **.macromedia** from your home. Also delete Fitrefox cache. This should fix the white box problem. About the CPU usage, install [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/") or [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/") and allow only flash content that you really need.

Also see [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

---

### Post by YoHell on 2010-10-17
> **lovinglinux said:**
> Nothing wrong on your report either.

Close Firefox and delete the folders **.adobe** and **.macromedia** from your home. Also delete Fitrefox cache. This should fix the white box problem. 

Nope. :(

I deleted those two dirs, clicked the clear now button in FF preferences > advanced > network and restarted FF. Was there anything else I should have done?

btw flash works just fine in chrome, but I'd rather not use that.

edit: 
oh would you look at that, when starting FF from the terminal it constantly spams this message when I go to youtube:

###!!! [Parent][RPCChannel] Error: Channel error: cannot send/recv

at about 1 message/s.

---

### Post by YoHell on 2010-10-17
I fed that error message to Google and got this:

[http://bugs.gentoo.org/show_bug.cgi?format=multiple&id=326311](http://bugs.gentoo.org/show_bug.cgi?format=multiple&id=326311)

It said to go to about:config  and change dom.ipc.plugins.enabled.libflashplayer.so;true to false.

I did so and the problem went away. I have no idea what it does though?

---

### Post by lovinglinux on 2010-10-17
> **YoHell said:**
> I fed that error message to Google and got this:

[http://bugs.gentoo.org/show_bug.cgi?format=multiple&id=326311](http://bugs.gentoo.org/show_bug.cgi?format=multiple&id=326311)

It said to go to about:config  and change dom.ipc.plugins.enabled.libflashplayer.so;true to false.

I did so and the problem went away. I have no idea what it does though?

Is to disable crash protection:

[http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins](http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins)

---

### Post by joneez on 2010-10-17
God I love Ubuntu forums!
I did a clean install of Ubuntu 10.10 64-bit two days ago and the only issue I was having (so far) was with YouTube vids. The vids wouldn't play in fullscreen and Firefox would grey out when I right-clicked the vid. After installing Flash-Aid, YouTube seems to work better than ever! Except for one weird problem. I have to hold right-click to keep the menu up. When I let go of the button the right-click menu disappears. To select from the menu, I hold the button, move the pointer to my selection and release the button.

Firefox version is 3.6.10
Flash version 10.2

---

### Post by zer010 on 2010-10-17
> **lovinglinux said:**
> 10.1 is the flash version, not the Ubuntu version. It works for Ubuntu 10.04 too, nevertheless, is the same version available from the repositories, that you have already installed.

Your right, I already have that version.

Shockwave Flash
 File: /usr/lib/flashplugin-installer/libflashplayer.so
 Version: 
 Shockwave Flash 10.1 r85...

---

### Post by YoHell on 2010-10-18
> **lovinglinux said:**
> Is to disable crash protection:

[http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins](http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins)

Hmm... crash protection against flash seems like pretty darn good idea to me. Could one expect the error to be fixed sometime so I can reenable it, and how would I know when to do it?

---

### Post by lovinglinux on 2010-10-18
> **YoHell said:**
> Hmm... crash protection against flash seems like pretty darn good idea to me. Could one expect the error to be fixed sometime so I can reenable it, and how would I know when to do it?

There is something you could try. I have received a greasemonkey script by e-mail, from Luke Morton, but I couldn't try it, because I was unable to reproduce the white box.

Re-enable crash protection, install [Greasemonkey]("https://addons.mozilla.org/en-US/firefox/addon/748/") and load the script below:

```
// ==UserScript==
// @name Flash video fix
// @namespace http://lukemorton.com.au
// @description Set the wmode attribute for Flash videos
// @include http://*
// @copyright Copyright 2010 Luke Morton
// @license Copying and distribution of this file, with or without
// modification, are permitted in any medium without royalty
// provided the copyright notice and this notice are preserved.
// This file is offered as-is, without any warranty.

// ==/UserScript==

var allEmbeds, thisEmbed;
allEmbeds = document.evaluate(
"//embed",
document,
null,
XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE,
null);

for (var i = 0; i < allEmbeds.snapshotLength; i++)
{
thisEmbed = allEmbeds.snapshotItem(i);
thisEmbed.setAttribute('wmode', 'opaque')
thisEmbed.parentNode.replaceChild(thisEmbed.cloneNode(true), thisEmbed);
}
```

Please let me know if it fixes the white box for you too.

---

### Post by soldier1st on 2010-10-19
flash aid has fixed issues that i had(minor issues) and another user(Her flash problems were much worse than mine as she runs an older system) and not just firefox's flash would crash right away but also under chrome but flash-aid fixed it completly.wtg for flash aid.

---

### Post by YoHell on 2010-10-20
I never had the time to try out that greasemonkey script yesterday. I'll see if I can do it some time tonight.

---

### Post by YoHell on 2010-10-20
> **lovinglinux said:**
> 
Re-enable crash protection, install [Greasemonkey]("https://addons.mozilla.org/en-US/firefox/addon/748/") and load the script below:

```
// ==UserScript==
// @name Flash video fix
// @namespace http://lukemorton.com.au
// @description Set the wmode attribute for Flash videos
// @include http://*
// @copyright Copyright 2010 Luke Morton
// @license Copying and distribution of this file, with or without
// modification, are permitted in any medium without royalty
// provided the copyright notice and this notice are preserved.
// This file is offered as-is, without any warranty.

// ==/UserScript==

var allEmbeds, thisEmbed;
allEmbeds = document.evaluate(
"//embed",
document,
null,
XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE,
null);

for (var i = 0; i < allEmbeds.snapshotLength; i++)
{
thisEmbed = allEmbeds.snapshotItem(i);
thisEmbed.setAttribute('wmode', 'opaque')
thisEmbed.parentNode.replaceChild(thisEmbed.cloneNode(true), thisEmbed);
}
```

Please let me know if it fixes the white box for you too.

The script did not fix the white box problem. 

Turning on icp brought back the original problems (confirm again FF hangs with 0 cpu use at certain times, white box at other times. flash gone). I saved the script to ~/Desktop/fix.user.js, installed greasemonkey, dropped the icon on FF, said to install it (yes i trust the source :-)), went to youtube and observed problems. Problems did not go away after FF restart nor reboot. Turning off icp made problems go away. Uninstalled greasemonkey. Problems still gone.

---

### Post by lovinglinux on 2010-10-20
> **YoHell said:**
> The script did not fix the white box problem. 

Turning on icp brought back the original problems (confirm again FF hangs with 0 cpu use at certain times, white box at other times. flash gone). I saved the script to ~/Desktop/fix.user.js, installed greasemonkey, dropped the icon on FF, said to install it (yes i trust the source :-)), went to youtube and observed problems. Problems did not go away after FF restart nor reboot. Turning off icp made problems go away. Uninstalled greasemonkey. Problems still gone.

Thanks for the feedback.

---

### Post by radioboy on 2010-10-27
FlashAid worked for me as well in Maverick. Excellent tip!
Every time I closed a tab with flash content while watching a flash video in another, this would crash (but not the browser).

---

### Post by akish on 2010-10-29
Thanks a lot for the tip.  My flash player is working much better after I downloaded flash aid.  Thanks!

---

### Post by rainbowagent7 on 2011-03-06
Thanks lovinglinux. My Adobe flashplugin would crash nearly every time I watched a Youtube vid. The script worked flawlessly once downloaded and opened from my Firefox browser (File > Open File... > Downloaded FIle > Follow Prompts). The plugin no longer crashes which is ultimately what I was trying to accomplish, however I still have the same problems when switching into fullscreen mode where the buffer will reset when I switch to fullscreen after it has loaded (I usually have several Youtube music video tabs open at once) and it will have to completely reload again. Anyway that's another matter entirely, as for the sudden onset of crashing that happened with my latest update your script was just what the doctor ordered. I am running Lucid (10.04) with Firefox 3.6.14 and Kernel 2.6.32-29-generic, I'm not exactly sure which plugin was the culprit though. Thanks again lovinglinux, great work.

Oh yeah, I almost forgot to mention that for some reason simply restarting Firefox for me wasn't enough, I had to reboot my computer before the effects were noticable.

---

### Post by pandaistinto on 2011-03-08
I had the "The Adobe Flash plugin has crashed" placeholder on youtube for quite few days (even though I hadn't any problems with embedded youtube players or other flash applications). I tried the lovinglinux/Luke Morton script and now it works! Now every time I start a video I get the "The Adobe Flash plugin has crashed" placeholder but after few seconds it is replaced by the working video!
So, thank you for your help!

-on Ubuntu 10.04, Firefox 3.6.15, Flash 10.2 r152

---

### Post by savaan on 2011-03-10
I'm having the same kinds of crashes, but very randomly and across both Firefox and Chromium. I ran a report log and I installed the latest and greatest Flash Aid but I can't seem to get them to stop crashing :( 
I'm on Ubuntu 10.10 running Firefox 3.6.15 and Chromium 9.0.597.107 (75357)

I've uninstalled and reinstalled multiple times. I created a new profile for Firefox and this was a one time workaround. By that I mean it worked great and I thought the problem was fixed because I was able to view a clip, but when I tried to replay that clip, flash crashed again. 

```
Ubuntu Architecture

Linux danyaeldemonic-Dimension-5100 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox						install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.15/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

glasen-intel-driver-maverick.list
maverick-partner.list
maverick-partner.list.save
ubuntu-wine-ppa-maverick.list
ubuntu-wine-ppa-maverick.list.save

Flash packages

flashplugin-installer				deinstall

Plugin locations


/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/libflashplayer.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
```

---

### Post by lovinglinux on 2011-03-10
> **savaan said:**
> I'm having the same kinds of crashes, but very randomly and across both Firefox and Chromium. I ran a report log and I installed the latest and greatest Flash Aid but I can't seem to get them to stop crashing :( 
I'm on Ubuntu 10.10 running Firefox 3.6.15 and Chromium 9.0.597.107 (75357)

I've uninstalled and reinstalled multiple times. I created a new profile for Firefox and this was a one time workaround. By that I mean it worked great and I thought the problem was fixed because I was able to view a clip, but when I tried to replay that clip, flash crashed again. 

```
Ubuntu Architecture

Linux danyaeldemonic-Dimension-5100 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox						install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.15/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

glasen-intel-driver-maverick.list
maverick-partner.list
maverick-partner.list.save
ubuntu-wine-ppa-maverick.list
ubuntu-wine-ppa-maverick.list.save

Flash packages

flashplugin-installer				deinstall

Plugin locations


/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/libflashplayer.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
```

I have been experiencing some flash crashes too recently with the latest beta flash version.

Select the "Expert Mode" in the extension, then go to the "Installation Options" tab and change the version to the one in the repositories, then click "Execute" to install the stable version. Let me know if that helps.

---

### Post by Jompa on 2011-03-11
I experience crashes in youtube but no other flash video sites. I get a purple-pink layer over the videos and when I reload it says that the plugin has crashed. Tried the regular flash-aid script and the one where you use the version in the repositories but still the same problem

---

### Post by lovinglinux on 2011-03-11
> **Jompa said:**
> I experience crashes in youtube but no other flash video sites. I get a purple-pink layer over the videos and when I reload it says that the plugin has crashed. Tried the regular flash-aid script and the one where you use the version in the repositories but still the same problem

Try [http://www.youtube-nocookie.com](http://www.youtube-nocookie.com)

---

### Post by savaan on 2011-03-12
well...that youtube-nocookie thing seems to work fine for me. what is that and why would that work as opposed to just going straight to youtube?

---

### Post by lovinglinux on 2011-03-12
> **savaan said:**
> well...that youtube-nocookie thing seems to work fine for me. what is that and why would that work as opposed to just going straight to youtube?

That site is the YouTube version that do not save or check for cookies. So you have a cookie issue, which is not uncommon on YouTube.

Try to delete the cookies, the cache and make sure you are allowing YouTube cookies.

---

### Post by Jompa on 2011-03-14
> **lovinglinux said:**
> Try [http://www.youtube-nocookie.com](http://www.youtube-nocookie.com)

This works for me as well. After deleting my cookies I could watch 3-4 videos on the regular youtube before it crashing again, how do I make sure I allow youtube cookies?

---

### Post by lovinglinux on 2011-03-14
> **Jompa said:**
> This works for me as well. After deleting my cookies I could watch 3-4 videos on the regular youtube before it crashing again, how do I make sure I allow youtube cookies?

Instead of deleting the cookies, disable hardware acceleration.

See discussion at [http://www.webgapps.org/addons/flash-aid](http://www.webgapps.org/addons/flash-aid)

---

### Post by swapnilps on 2011-04-23
I have a same issue.. but with Firefox and Chromium Both..
Flash plug-in gets crashed with any of these browsers. I click on play video; it starts buffering and crash report appears in few moments..
It is very much annoying!!! :(
Any help will be appreciated.

Thanks in advance!!!

---

