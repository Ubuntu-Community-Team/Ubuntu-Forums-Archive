---
title: "Firefox 3.6 now Namoroka?"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by Tholley on 2010-02-20
I just ran synaptic and Mark All Upgrades, and Firefox updated to Namoroka 3.6.
No traditional Firefox logo, hardly even any mention of Firefox, even the top header only says Namoroka. I thought I had been hijacked.... 

Is this normal?

---

### Post by Greenwidth on 2010-02-20
It is Firefox, but I thought it only had that name whilst in development, the dev one before that was called Shiretoko if I remeber right.

---

### Post by JackRock on 2010-02-20
See [this thread](http://ubuntuforums.org/showthread.php?t=1393533) for a current discussion on it.  The question comes up regularly.

---

### Post by stmiller on 2010-02-20
It's normal. That is the mozilla code name for that version of the browser.

---

### Post by lovinglinux on 2010-02-20
As already mentioned on other posts and several threads, it is perfectly normal. You probably have added the *ubuntu-mozilla-daily* ppa to your Software Sources and now it has upgraded Firefox to 3.6, with the codename Namoroka.

If you want to install the branded version, with proper logo and name, then remove the *ubuntu-mozilla-daily* ppa, add the *mozillateam/firefox-stable* ppa and reinstall firefox. See the [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) for additional info.

---

### Post by Tholley on 2010-04-17
> **lovinglinux said:**
> As already mentioned on other posts and several threads, it is perfectly normal. You probably have added the *ubuntu-mozilla-daily* ppa to your Software Sources and now it has upgraded Firefox to 3.6, with the codename Namoroka.
 
If you want to install the branded version, with proper logo and name, then remove the *ubuntu-mozilla-daily* ppa, add the *mozillateam/firefox-stable* ppa and reinstall firefox. See the [COLOR=sienna]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567") for additional info.
 
I hadn't switched over because everything seemed to be working fine, but just yesterday I noticed my NoScript was not showing, and then saw that it is not compatible with Namoroka, so I will be switching back to the branded version.
 
I can't believe it took me 2 months to realize my NoScript wasn't working! What a dork I am...

---

### Post by lovinglinux on 2010-04-17
> **Tholley said:**
> I hadn't switched over because everything seemed to be working fine, but just yesterday I noticed my NoScript was not showing, and then saw that it is not compatible with Namoroka, so I will be switching back to the branded version.
 
I can't believe it took me 2 months to realize my NoScript wasn't working! What a dork I am...

You can install [Add-on Compatibility](https://addons.mozilla.org/en-US/firefox/addon/15003) Reporter to make NoScript work. Nevertheless, I would stick with the stable version of Firefox. Namoroka 3.6.4pre has a serious issue with flash and is causing a lot of trouble to several users.

---

### Post by Tholley on 2010-04-19
>  
If you want to install the branded version, with proper logo and name, then remove the *ubuntu-mozilla-daily* ppa, add the *mozillateam/firefox-stable* ppa and reinstall firefox. See the [COLOR=sienna]**Installing Other Versions**[/COLOR] section of [[COLOR=#444444]Firefox optimization and troubleshooting thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1193567") for additional info.

 
I looked for ubuntu-mozilla-daily in my Software Manager and I think also in Synaptic, but did not see anything labeled that. Where do I go to find it and remove it?
 
I went to NoScript site, and was able to click on "add to Firefox" and it is working now, but would still like to look at reverting back away from Namoroka.
 
Also about the same time, when my Thunderbird updated, it changed to Shredder, and things did not work the same either.

---

### Post by lovinglinux on 2010-04-19
> **Tholley said:**
> I looked for ubuntu-mozilla-daily in my Software Manager and I think also in Synaptic, but did not see anything labeled that. Where do I go to find it and remove it?
 
I went to NoScript site, and was able to click on "add to Firefox" and it is working now, but would still like to look at reverting back away from Namoroka.
 
Also about the same time, when my Thunderbird updated, it changed to Shredder, and things did not work the same either.

You need to go to "System >> Administration >> Software Sources >> Other Sofware" and disable or remove the ubuntu-mozilla-ppa then run the command below on a terminal:

```
sudo apt-get install --reinstall firefox thunderbird
```

---

### Post by Tholley on 2010-04-20
I followed the instructions, unchecked the ppa.launchpad.net/ubuntu-daily/ppa/ubuntu karmic main.

this is what I got after running the command..

```
terrell@terrell-bedroom:~$ sudo apt-get install --reinstall firefox thunderbird
[sudo] password for terrell: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of firefox is not possible, it cannot be downloaded.
Reinstallation of thunderbird is not possible, it cannot be downloaded.
The following packages were automatically installed and are no longer required:
  dvdrip-doc linux-headers-2.6.31-19 librpmbuild0 debhelper intltool-debian
  libevent-execflow-perl postfix libnet-ssleay-perl libwxgtk2.6-0 libintl-perl
  lsb-graphics lsb-desktop libsox-fmt-ao m4 librpmio0 librpm0 po-debconf
  ncurses-term transcode-utils transcode-doc transfig libnss3-dev
  libmail-sendmail-perl gettext python-urwid blt python-tk libqt4-gui
  libevent-rpc-perl ogmtools gtk2-ex-formfactory-perl libwxbase2.6-0 lsdvd
  libsox-fmt-pulse vamps lsb libnspr4-dev pax fping netpbm libsox-fmt-mp3
  anyevent-perl rpm libsox-fmt-base sox tcl8.5 python-wxversion libsox-fmt-oss
  linux-headers-2.6.31-19-generic gocr libsox-fmt-alsa libevent-perl tk8.5
  libnetpbm10 xine-ui bsd-mailx html2text libconfig-tiny-perl python-wxgtk2.6
  libio-socket-ssl-perl mailx mkvtoolnix libsox1a lsb-core libjpeg-progs alien
  libsys-hostname-long-perl lsb-cxx libnet-libidn-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```

---

### Post by lovinglinux on 2010-04-20
> **Tholley said:**
> I followed the instructions, unchecked the ppa.launchpad.net/ubuntu-daily/ppa/ubuntu karmic main.

this is what I got after running the command..


Uninstall, then install again.

---

### Post by Tholley on 2010-04-20
Well I was able to un-install Shredder using Ubuntu Software Center, and reinstall Thunderbird.

But, wasn't able to remove Firefox from Software Center, even tho I checked remove, Namoroka is still there, I went to Synaptic and realised it would un-install Songbird too, so as of now opted not to yet, since I don't want to have to re-add all my play-lists and stuff.

---

### Post by lovinglinux on 2010-04-20
> **Tholley said:**
> Well I was able to un-install Shredder using Ubuntu Software Center, and reinstall Thunderbird.

But, wasn't able to remove Firefox from Software Center, even tho I checked remove, Namoroka is still there, I went to Synaptic and realised it would un-install Songbird too, so as of now opted not to yet, since I don't want to have to re-add all my play-lists and stuff.

I never used Songbird, but you shouldn't lose any settings or playlist by just removing applications. Such data is stored on your home directory. For instance you did removed Thunderbird and didn't lose your e-mails.

So, open a terminal and run this:

```
sudo apt-get remove firefox && sudo apt-get install firefox songbird
```

---

### Post by Tholley on 2010-04-21
>  
I never used Songbird, but you shouldn't lose any settings or playlist by just removing applications. Such data is stored on your home directory. For instance you did removed Thunderbird and didn't lose your e-mails.



 
Um... yeah, I did lose all my emails, and had to re-configure all the mail settings as well yesterday. It did that when it changed to shredder also.
 
And when it changed from Firefox to Namoroka, same thing. I lost all my bookmarks, add-ons, and settings from firefox, and had to re-install Songbird and re-do everything on it too.
 
I may still go ahead and do it, just may have to wait until I have the time to spend on setting everything back up.

---

### Post by lovinglinux on 2010-04-21
> **Tholley said:**
> Um... yeah, I did lose all my emails, and had to re-configure all the mail settings as well yesterday. It did that when it changed to shredder also.
 
And when it changed from Firefox to Namoroka, same thing. I lost all my bookmarks, add-ons, and settings from firefox, and had to re-install Songbird and re-do everything on it too.
 
I may still go ahead and do it, just may have to wait until I have the time to spend on setting everything back up.

The problem is that when you install a development version of Firefox or Thunderbird, sometimes the developers set things up to clone your profiles, in order to avoid messing with your current settings. I don't like this approach, exactly because of situations like this, when the user downgrade. To make things worse, I have seen versions that do that and versions that don't.

Bottom line, your settings are probably located on a different folder. Your default Firefox profile should be located under ~/.mozilla/firefox. This is the one you are using right now. The cloned profile should be located at ~/.mozilla/firefox-3.6 or ~/.mozilla/firefox-3.5 depending on which version you upgraded. Thunderbird cloned profile should be under ~/.thunderbird-3 or something similar.

---

