---
title: "Problems with Flash on Lucid"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by demonic_bunny on 2010-08-22
I'm sure this has been mentioned before somewhere, but I haven't been able to find it.

For some reason, when trying to view Flash content in Firefox, most of the time the content loads, but I can't interact with it. Buttons don;t respond, even though the animation for their rollovers and mouse clicks work. This is annoying since pretty much every embedded video wont play (you need to click the play button for them to start), and any websites using Flash for navigation are unusable. Also, YouTube has a tendency to not load the videos at all, instead showing an error message, and the few times they do play, the controls don't work, so theres no way to pause the content.

I'm sure this is a well documented, easy fix, I just haven't been able to find it.

Thanks in advance, srry for being redundant...

---

### Post by lovinglinux on 2010-08-23
[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---

### Post by demonic_bunny on 2010-08-23
> **lovinglinux said:**
> [http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

Thanks. Was able to fix 90% of my issues.

---

### Post by lovinglinux on 2010-08-23
> **demonic_bunny said:**
> Thanks. Was able to fix 90% of my issues.

What about the remaining 10%?

---

### Post by baddnady23 on 2010-08-23
I had the same issues and it was very frustrating.  I fixed it 100% on my 64 bit Ubuntu installation using the following guide.  A link to it was posted over at psychocat's website:

[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/]("http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/")

Hope this helps!

---

### Post by lovinglinux on 2010-08-23
> **baddnady23 said:**
> I had the same issues and it was very frustrating.  I fixed it 100% on my 64 bit Ubuntu installation using the following guide.  A link to it was posted over at psychocat's website:

[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/]("http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/")

Hope this helps!

That version has a critical vulnerability. You should consider using version 10.1.82 from the repositories. It is working fine in 64bit.

---

### Post by Mediosordo on 2010-08-26
I seem to have the same problem. None of the buttons and flash menus (wordpress, etc) seem to work. It's weird because yesterday everything was working fine and I don't remember doing any system update.

I've tried installing the Flash-Aid plugin but problems are still there. And my system is 32bits, so the solution given on the [Firefox-Tutorial]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html") is no good. :(

Btw, using Lucid 10.04 and Firefox 3.6.8.   Worse is, everything works perfectly with Chrome.

---

### Post by lovinglinux on 2010-08-26
> **Mediosordo said:**
> I seem to have the same problem. None of the buttons and flash menus (wordpress, etc) seem to work. It's weird because yesterday everything was working fine and I don't remember doing any system update.

I've tried installing the Flash-Aid plugin but problems are still there. And my system is 32bits, so the solution given on the [Firefox-Tutorial]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html") is no good. :(

Btw, using Lucid 10.04 and Firefox 3.6.8.   Worse is, everything works perfectly with Chrome.

Start Firefox in safe mode and check if it works.

See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by Mediosordo on 2010-08-26
Just did, same result. I can however play/stop youtube videos (also on normal mode) and I've read it's a common issue with a lot of people having problems with that. I have no problem whatsoever with youtube or vimeo.
In fact, I'm beginning to wonder if it might be a problem with wordpress and firefox on linux, as I don't seem to have any problems with other services that use flash (for example, I can play/pause any myspace music player).  My main issue is that many of the wordpress menus on the dashboard are nor working properly, and I'm not able to drag and drop widgets (to select them) on the widget menu (something I could do yesterday!).
Weird.

Thanks, will try the advices in that turorial see if I have any luck.

---

### Post by lovinglinux on 2010-08-26
> **Mediosordo said:**
> Just did, same result. I can however play/stop youtube videos (also on normal mode) and I've read it's a common issue with a lot of people having problems with that. I have no problem whatsoever with youtube or vimeo.
In fact, I'm beginning to wonder if it might be a problem with wordpress and firefox on linux, as I don't seem to have any problems with other services that use flash (for example, I can play/pause any myspace music player).  My main issue is that many of the wordpress menus on the dashboard are nor working properly, and I'm not able to drag and drop widgets (to select them) on the widget menu (something I could do yesterday!).
Weird.

Thanks, will try the advices in that turorial see if I have any luck.

I don't think those Wordpress widgets are flash based. They must be ajax or something like that.

---

### Post by PPPilot on 2010-08-26
Flash issues seem to be rampant. About 10 times a day, I get a message box in the middle of my screen saying I need to download and install a flash player update. If I click OK, nothing happens. Up in the top bar of that box it says it is from website I never heard of. I installed and ran the FLASH-AID plug in and it said I had the current version installed. 

Then there is the crashing issue. The plugin crashes every time you turn around. At least it does not take Firefox down with it any more. I have both Karmic and Lucid installed and both of these issues occur in either OS.

---

### Post by lovinglinux on 2010-08-27
> **PPPilot said:**
> Flash issues seem to be rampant. About 10 times a day, I get a message box in the middle of my screen saying I need to download and install a flash player update. If I click OK, nothing happens. Up in the top bar of that box it says it is from website I never heard of. I installed and ran the FLASH-AID plug in and it said I had the current version installed. 

Then there is the crashing issue. The plugin crashes every time you turn around. At least it does not take Firefox down with it any more. I have both Karmic and Lucid installed and both of these issues occur in either OS.

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

### Post by PPPilot on 2010-08-27
lovinglinux,

I created PNGs of your first two items. See the attached files...

Here us the output for #3:

> john@john-desktop:~$ echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo '' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ uname -a >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo '' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo '' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo '' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo '' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo '' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo '' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ which firefox >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txtjohn@john-desktop:~$ file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo '' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo '' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo '' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo 'Sources' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo '' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo '' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo 'Flash packages' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo '' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo '' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo '' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo '' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo '' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ echo '' >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
john@john-desktop:~$ firefox ~/Desktop/firefox-report.txt
john@john-desktop:~$ 
[IMG]http://ubuntuforums.org/home/john/Desktop/Screenshot.png[/IMG]

[IMG]http://ubuntuforums.org/home/john/Desktop/Screenshot-1.png[/IMG]

---

### Post by milkyspit on 2010-08-27
> **lovinglinux said:**
> Please provide the output of the following commands and instructions...

(snip)

[IMG]http://tinyurl.com/26b85o2[/IMG]




Sorry to go OT, but could you kindly reveal what theme you're using in the message box above? Looks really clean... I wouldn't mind configuring my desktop to look similar. What is it?

---

### Post by lovinglinux on 2010-08-27
> **PPPilot said:**
> Here us the output for #3:

Is not the output of the commands in the terminal, but the content of the generated **firefox-report.txt** file created on your desktop. The commands won't show anything on the terminal, just on the created file.

> **milkyspit said:**
> Sorry to go OT, but could you kindly reveal what theme you're using in the message box above? Looks really clean... I wouldn't mind configuring my desktop to look similar. What is it?

I'm not using Gnome. My current KDE 4.4 style for Gnome applications is QtCurve Klearlooks.

I have changed it recently. Now my Firefox looks like this:

[IMG]http://tinyurl.com/232oe6j[/IMG]

---

### Post by PPPilot on 2010-08-27
lovinglinux,

> Ubuntu Architecture

Linux john-desktop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox                        install
firefox-2-dbg                    install
firefox-3.5-dbg                    install
firefox-branding                install
firefox-dbg                    install
firefox-gnome-support                install
firefox-gnome-support-dbg            install
kubuntu-firefox-installer            install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.9/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

chromium-daily-ppa-lucid.list
chromium-daily-ppa-lucid.list.save
c-korn-vlc.list.save
c-korn-vlc-lucid.list
c-korn-vlc-lucid.list.save
medibuntu.list
medibuntu.list.save
openoffice-pkgs-ppa-lucid.list
openoffice-pkgs-ppa-lucid.list.save
sevenmachines-flash.list
sevenmachines-flash.list.save
ubuntu-mozilla-security-ppa-lucid.list
ubuntu-mozilla-security-ppa-lucid.list.save
ubuntu-tweak-stable.list
ubuntu-tweak-stable.list.save

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
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)Looks like the last two lines have issues????

---

### Post by lovinglinux on 2010-08-27
> **PPPilot said:**
> lovinglinux,

Looks like the last two lines have issues????

Nope. That is expected on a 32bit system.
I don't see anything wrong in your report, but it seems you are using flash from a non-official ppa. That could be the problem.

Go to "System >> Administration >> Software Sources >> Other Software" and remove the sevenmachines-flash ppa.

Then run the following commands:

```
sudo apt-get update
sudo apt-get purge flashplugin-nonfree
sudo apt-get purge flashplugin-installer
sudo apt-get install flashplugin-nonfree
```

You also have some Firefox packages that are no longer needed.

```
sudo apt-get purge firefox-dbg
sudo apt-get purge firefox-gnome-support-dbg
sudo apt-get purge firefox-2-dbg
sudo apt-get purge firefox-3.5-dbg
```

Additionally, looks to me you have been upgrading your system since Firefox 2. If you never created a new Firefox profile, then I would recommend creating one. you can do that from the profile manager:

```
firefox -P
```

If a new profile works without problems, then see [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

---

### Post by Puzzled Guy on 2010-08-27
Have you installed the ubuntu-restricted-extras (or something like that) package? I think that package has flash in it. You might also need to install openjdk (java) from the repositories.

That fixed all of *my *issues with Firefox.

---

### Post by lovinglinux on 2010-08-27
> **Puzzled Guy said:**
> Have you installed the ubuntu-restricted-extras (or something like that) package? I think that package has flash in it. You might also need to install openjdk (java) from the repositories.

That fixed all of *my *issues with Firefox.

He has flash already.

---

### Post by PPPilot on 2010-08-27
lovinglinux,
I ran all the commands and I'll see how things go and let you know how it works after a few days...

---

### Post by PPPilot on 2010-08-28
lovinglinux,
After completing all the changes and clean ups you outlined, this morning right out of the box I got the update flashplayer box. See Attached Image.... I have not had a flash player ceash yet....

---

### Post by lovinglinux on 2010-08-28
> **PPPilot said:**
> lovinglinux,
After completing all the changes and clean ups you outlined, this morning right out of the box I got the update flashplayer box. See Attached Image.... I have not had a flash player ceash yet....

Would you mind posting the link of the video you were trying to watch, if it is suitable for the forum?

---

### Post by PPPilot on 2010-08-28
lovinglinux,

I was not even trying to open a video. I was at the NOAA site that displays my local weather etc. This is my Firefox home page and I had just opened Firefox. I went to the kitchen and upon my return, there it was. The flash plugin crashes that I spoke of do happen during video play but these update boxes never pop up when opening videos. I have seen them come up when I am on a blank tab. They just pop up randomly as near as I can tell. As a matter of fact, I have not seen one since the one this morning....

---

### Post by lovinglinux on 2010-08-28
I'm asking this because I never saw such alert. I usually see this..

[IMG]http://tinyurl.com/2du55gf[/IMG]

or this...

[IMG]http://tinyurl.com/23982ka[/IMG]

On NOAA I get the first one. I'm not using gnome tho, so I don't know if that alert is normal on Gnome.

Do you see something similar on NOAA's home page or just the popup? In case is just the popup, do you see the video?

---

### Post by PPPilot on 2010-08-28
lovinglinux.
As near as I can tell, there is no video that plays on my NOAA home page and as I said I can even get the message box when on a blank tab. I've never seen either of the boxes you show although the first one is similar to what I see when the flash plug in crashes. I have the KDE and Gnome desktops installed and I get the same message box on either. This session has been going for about 8 hours now and no messages since early in the day.... By the way, Thanks for all your Help:D

---

### Post by lovinglinux on 2010-08-28
> **PPPilot said:**
> lovinglinux.
As near as I can tell, there is no video that plays on my NOAA home page and as I said I can even get the message box when on a blank tab. I've never seen either of the boxes you show although the first one is similar to what I see when the flash plug in crashes. I have the KDE and Gnome desktops installed and I get the same message box on either. This session has been going for about 8 hours now and no messages since early in the day.... By the way, Thanks for all your Help:D

Sorry, is not a video but a flash animation with the featured articles. Can you post a screenshot of NOAA's home page?

I suspect that alert is a fake or Gnome is firing it for some reason, even with flash properly working.

---

### Post by PPPilot on 2010-08-28
Sorry, the NOAA page is long and thin and by the time I get all on the screen for a shot, it is to small to read. Here is the link: 
[http://forecast.weather.gov/MapClick.php?CityName=Raymond&state=IL&site=LSX&lat=39.3202&lon=-89.5737](http://forecast.weather.gov/MapClick.php?CityName=Raymond&state=IL&site=LSX&lat=39.3202&lon=-89.5737) 
As you say, it may be a fake or for what ever reason both Gnome and KDE put it out and I get it on both Karmic and Lucid.

---

### Post by lovinglinux on 2010-08-28
> **PPPilot said:**
> Sorry, the NOAA page is long and thin and by the time I get all on the screen for a shot, it is to small to read. Here is the link: 
[http://forecast.weather.gov/MapClick.php?CityName=Raymond&state=IL&site=LSX&lat=39.3202&lon=-89.5737](http://forecast.weather.gov/MapClick.php?CityName=Raymond&state=IL&site=LSX&lat=39.3202&lon=-89.5737) 
As you say, it may be a fake or for what ever reason both Gnome and KDE put it out and I get it on both Karmic and Lucid.

Can you see this:

---

### Post by PPPilot on 2010-08-28
Yes.......

---

### Post by lovinglinux on 2010-08-28
> **PPPilot said:**
> Yes.......

If you can see the flash content on the page you get the alert, then is a fake or an erroneous message.

I would advise to create a new profile, since yours could be compromised.

See [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

---

### Post by mlemily on 2010-09-14
Thanks! 

The solution for 
"Flash doesn't work or I get an error on some web pages asking to install flash, but I have already installed the latest version."

on the page you posted: 
[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

seems to have worked great!

Interestingly I found that when I installed FLASH-AID it failed to launch a terminal.
I couldn't tell that anything was being run at the command line and I saw no change in the behavior of Flash.

But running the commands you list in a terminal I launched myself worked just dandy

Everyone seemed to like #8's solution on this page:
[https://bugs.launchpad.net/ubuntu/lucid/+source/flashplugin-nonfree/+bug/429841](https://bugs.launchpad.net/ubuntu/lucid/+source/flashplugin-nonfree/+bug/429841)

but that was not working for me and seems like it was probably packaged in a Lucid update.

Thanks again!

---

### Post by sevenX on 2010-09-15
> **lovinglinux said:**
> [http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

SOLVED 100% of my problems thanks lovinlinux... i love linux because of u!

---

### Post by lovinglinux on 2010-09-15
> **sevenX said:**
> SOLVED 100% of my problems thanks lovinlinux... i love linux because of u!

You are welcome. ;)

---

