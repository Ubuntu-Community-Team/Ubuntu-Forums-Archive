---
title: "Renaming Shiretoko to Firefox??"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by FoxFireX on 2009-07-09
Just installed firefox 3.5, donno if I did it right, but I delete the old firefox, from my usr/lib/
and now theres just firefox-3.5 in there, I also replaced the icons of the new firefox 3.5 with the original ones from firefox 3.0.11, and I made the icon on the top desktop bar, link back to firefox 3.5, Pretty good for a noob I guess? Some googling helped.

Anyway, When I open firefox 3.5, it named Shiretoko, and the useragent is also that.

Not that theres a problem with the useragent being that, its just some sites see me using a browser that they have never heard of and some sites block me from entering them.

So did I do everything right? How do I rename Shiretoko to Firefox, and change the useragent, so that it shows me as using firefox 3.0 or something. 


PS: Thats funny, My thread is the only thread that seems like its to much of a complex question, I always ask complex questions it seems, that takes longer then usual for an answer. Where's all the smart people! help me out ^_^

---

### Post by skymera on 2009-07-09
I don't think you can. 3.5's codename is Shiretoko just like 3.0 is Grand Paradiso.

What if you download the beta from Mozilla's site and not the Firefox PPA

---

### Post by Tibuda on 2009-07-09
You change the user agent with this addon: [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by FoxFireX on 2009-07-09
Nevermind fella's I've figured it out.


Mozilla Firefox addon Nighty Tester Tools, worked for renaming Shiretoko to Firefox, Infact I just left the name of the browser blank. Woot.

Also, found out how to change the user agent.. You don't need an addon to change it.

its just about:config, in the address bar and then you make a new string, general.useragent.override

But I'm go ahead and get the user agent switch anyway sense thats way easier. thanks ^^

---

### Post by lovinglinux on 2009-07-09
> **FoxFireX said:**
> ...but I delete the old firefox, from my usr/lib/

Not a good idea. You shouldn't remove Firefox 3.0.11 and even if you do so, the proper way is trough the package manager.

> **FoxFireX said:**
> So did I do everything right? How do I rename Shiretoko to Firefox, and change the useragent, so that it shows me as using firefox 3.0 or something.

Sorry, but you went through a lot of trouble to make modifications that could create more problems than solutions and that could be achieved in less then 2 minutes with the proper commands. Don't get me wrong, I'm not criticizing you, but I feel compelled to write to avoid other users following your method.

If you want Firefox 3.5 with proper branding (name and logo), that you can open through the default menus without changing the launcher paths, coexisting with Firefox 3.0.11 without removing it and without messing with meta packages, then follow method #1 of the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

I strongly recommend that you undo your changes before proceeding, by removing firefox-3.5, re-installing firefox-3.0 and relinking launchers and other stuff as they should be. Go to "System >> Administration >> Synaptic Package Manager", then select firefox-3.5 for removal and select firefox and firefox-3.0 for re-installation. Then click apply.

After that, apply the method **[COLOR="Red"]1 - Manual installation of fresh final releases from Mozilla[/COLOR]** from the tutorial above and Firefox 3.5 should be installed appropriately, with the correct name, logo and paths.

BTW

> **FoxFireX said:**
> PS: Thats funny, My thread is the only thread that seems like its to much of a complex question, I always ask complex questions it seems, that takes longer then usual for an answer. Where's all the smart people! help me out ^_^

There are [a few threads](http://ubuntuforums.org/showthread.php?t=1200781) with questions about the Shiretoko name

---

### Post by FoxFireX on 2009-07-09
Okay, I revert all changes and did the manual install in the tutorial, rebooted firefox..

And it says I'm using Firefox 3.0 still. -_-

heres terminal log.

```

XXXX@XXXX-Ubuntu:~$ cp -R ~/.mozilla ~/.mozilla.backup
XXXX@XXXX-Ubuntu:~$ sudo tar -jxvf firefox-*.tar.bz2 -C /opt
[sudo] password for XXXX: 
firefox/
firefox/update.locale
firefox/plugins/
firefox/plugins/libnullplugin.so
firefox/Throbber-small.gif
firefox/components/
firefox/components/nsSessionStore.js
firefox/components/nsFilePicker.js
firefox/components/nsBadCertHandler.js
firefox/components/libmozgnome.so
firefox/components/browser.xpt
firefox/components/libbrowserdirprovider.so
firefox/components/nsPrivateBrowsingService.js
firefox/components/nsTryToClose.js
firefox/components/FeedProcessor.js
firefox/components/pluginGlue.js
firefox/components/txEXSLTRegExFunctions.js
firefox/components/nsHelperAppDlg.js
firefox/components/nsPlacesTransactionsService.js
firefox/components/nsMicrosummaryService.js
firefox/components/nsTaggingService.js
firefox/components/nsBrowserContentHandler.js
firefox/components/nsBlocklistService.js
firefox/components/nsSearchService.js
firefox/components/nsSidebar.js
firefox/components/nsDefaultCLH.js
firefox/components/nsWebHandlerApp.js
firefox/components/nsLoginManager.js
firefox/components/nsUpdateService.js
firefox/components/nsUrlClassifierLib.js
firefox/components/nsSetDefaultBrowser.js
firefox/components/nsDownloadManagerUI.js
firefox/components/nsSafebrowsingApplication.js
firefox/components/nsUrlClassifierListManager.js
firefox/components/nsSearchSuggestions.js
firefox/components/NetworkGeolocationProvider.js
firefox/components/storage-mozStorage.js
firefox/components/fuelApplication.js
firefox/components/nsContentDispatchChooser.js
firefox/components/nsLivemarkService.js
firefox/components/jsconsole-clhandler.js
firefox/components/nsExtensionManager.js
firefox/components/nsURLFormatter.js
firefox/components/nsSessionStartup.js
firefox/components/storage-Legacy.js
firefox/components/FeedConverter.js
firefox/components/libdbusservice.so
firefox/components/aboutSessionRestore.js
firefox/components/aboutCertError.js
firefox/components/FeedWriter.js
firefox/components/aboutPrivateBrowsing.js
firefox/components/libbrowsercomps.so
firefox/components/nsPlacesDBFlush.js
firefox/components/nsProxyAutoConfig.js
firefox/components/WebContentConverter.js
firefox/components/nsAddonRepository.js
firefox/components/aboutRights.js
firefox/components/libnkgnomevfs.so
firefox/components/nsHandlerService.js
firefox/components/nsBrowserGlue.js
firefox/components/nsContentPrefService.js
firefox/components/aboutRobots.js
firefox/components/libimgicon.so
firefox/components/nsLoginInfo.js
firefox/components/nsLoginManagerPrompter.js
firefox/platform.ini
firefox/libnssutil3.so
firefox/blocklist.xml
firefox/firefox
firefox/removed-files
firefox/libnssdbm3.so
firefox/browserconfig.properties
firefox/old-homepage-default.properties
firefox/firefox-bin
firefox/crashreporter-override.ini
firefox/libsmime3.so
firefox/libnspr4.so
firefox/crashreporter.ini
firefox/libsqlite3.so
firefox/libsoftokn3.chk
firefox/updater.ini
firefox/run-mozilla.sh
firefox/libnssckbi.so
firefox/libssl3.so
firefox/libfreebl3.chk
firefox/updater
firefox/crashreporter
firefox/.autoreg
firefox/libxpcom.so
firefox/chrome/
firefox/chrome/comm.manifest
firefox/chrome/pippki.jar
firefox/chrome/comm.jar
firefox/chrome/pippki.manifest
firefox/chrome/reporter.jar
firefox/chrome/en-US.manifest
firefox/chrome/toolkit.jar
firefox/chrome/reporter.manifest
firefox/chrome/toolkit.manifest
firefox/chrome/browser.manifest
firefox/chrome/classic.manifest
firefox/chrome/icons/
firefox/chrome/icons/default/
firefox/chrome/icons/default/default32.png
firefox/chrome/icons/default/default16.png
firefox/chrome/icons/default/default48.png
firefox/chrome/classic.jar
firefox/chrome/en-US.jar
firefox/chrome/browser.jar
firefox/libnss3.so
firefox/greprefs/
firefox/greprefs/xpinstall.js
firefox/greprefs/all.js
firefox/greprefs/security-prefs.js
firefox/dictionaries/
firefox/dictionaries/en-US.aff
firefox/dictionaries/en-US.dic
firefox/extensions/
firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/
firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
firefox/res/
firefox/res/table-add-row-after-hover.gif
firefox/res/svg.css
firefox/res/arrow.gif
firefox/res/table-remove-row-hover.gif
firefox/res/grabber.gif
firefox/res/hiddenWindow.html
firefox/res/loading-image.gif
firefox/res/table-remove-row-active.gif
firefox/res/html.css
firefox/res/langGroups.properties
firefox/res/EditorOverride.css
firefox/res/table-add-column-before-active.gif
firefox/res/table-remove-column.gif
firefox/res/fonts/
firefox/res/fonts/mathfont.properties
firefox/res/fonts/mathfontSTIXNonUnicode.properties
firefox/res/fonts/mathfontStandardSymbolsL.properties
firefox/res/fonts/mathfontUnicode.properties
firefox/res/fonts/mathfontSTIXSize1.properties
firefox/res/table-remove-column-active.gif
firefox/res/forms.css
firefox/res/table-add-row-after.gif
firefox/res/entityTables/
firefox/res/entityTables/html40Latin1.properties
firefox/res/entityTables/html40Special.properties
firefox/res/entityTables/htmlEntityVersions.properties
firefox/res/entityTables/transliterate.properties
firefox/res/entityTables/html40Symbols.properties
firefox/res/entityTables/mathml20.properties
firefox/res/table-add-column-before.gif
firefox/res/ua.css
firefox/res/broken-image.gif
firefox/res/table-remove-row.gif
firefox/res/table-add-column-after.gif
firefox/res/table-add-column-after-hover.gif
firefox/res/quirk.css
firefox/res/table-add-column-before-hover.gif
firefox/res/charsetalias.properties
firefox/res/mathml.css
firefox/res/table-add-row-before-active.gif
firefox/res/table-add-row-before.gif
firefox/res/table-remove-column-hover.gif
firefox/res/table-add-row-before-hover.gif
firefox/res/designmode.css
firefox/res/viewsource.css
firefox/res/contenteditable.css
firefox/res/arrowd.gif
firefox/res/charsetData.properties
firefox/res/table-add-row-after-active.gif
firefox/res/html/
firefox/res/html/folder.png
firefox/res/dtd/
firefox/res/dtd/xhtml11.dtd
firefox/res/dtd/mathml.dtd
firefox/res/unixcharset.properties
firefox/res/table-add-column-after-active.gif
firefox/res/language.properties
firefox/libsoftokn3.so
firefox/libfreebl3.so
firefox/modules/
firefox/modules/PluralForm.jsm
firefox/modules/distribution.js
firefox/modules/WindowDraggingUtils.jsm
firefox/modules/Microformats.js
firefox/modules/PlacesDBUtils.jsm
firefox/modules/XPCOMUtils.jsm
firefox/modules/utils.js
firefox/modules/DownloadUtils.jsm
firefox/modules/ISO8601DateUtils.jsm
firefox/modules/debug.js
firefox/modules/DownloadLastDir.jsm
firefox/modules/SpatialNavigation.js
firefox/README.txt
firefox/libplc4.so
firefox/application.ini
firefox/searchplugins/
firefox/searchplugins/answers.xml
firefox/searchplugins/google.xml
firefox/searchplugins/eBay.xml
firefox/searchplugins/creativecommons.xml
firefox/searchplugins/amazondotcom.xml
firefox/searchplugins/wikipedia.xml
firefox/searchplugins/yahoo.xml
firefox/icons/
firefox/icons/updater.png
firefox/icons/document.png
firefox/icons/mozicon16.xpm
firefox/icons/mozicon128.png
firefox/icons/mozicon50.xpm
firefox/libplds4.so
firefox/mozilla-xremote-client
firefox/libxul.so
firefox/defaults/
firefox/defaults/profile/
firefox/defaults/profile/bookmarks.html
firefox/defaults/profile/prefs.js
firefox/defaults/profile/mimeTypes.rdf
firefox/defaults/profile/localstore.rdf
firefox/defaults/profile/chrome/
firefox/defaults/profile/chrome/userChrome-example.css
firefox/defaults/profile/chrome/userContent-example.css
firefox/defaults/pref/
firefox/defaults/pref/channel-prefs.js
firefox/defaults/pref/firefox.js
firefox/defaults/pref/reporter.js
firefox/defaults/pref/firefox-branding.js
firefox/defaults/pref/firefox-l10n.js
firefox/defaults/autoconfig/
firefox/defaults/autoconfig/platform.js
firefox/defaults/autoconfig/prefcalls.js
firefox/libmozjs.so
XXXX@XXXX-Ubuntu:~$ rm firefox-*.tar.bz2
XXXX@XXXX-Ubuntu:~$ sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
XXXX@XXXX-Ubuntu:~$ sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
XXXX@XXXX-Ubuntu:~$ sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
XXXX@XXXX-Ubuntu:~$ sudo ln -s /opt/firefox/firefox /usr/bin/firefox
XXXX@XXXX-Ubuntu:~$
```

---

### Post by Ascenti0n on 2009-07-09
I had the same problem, and I posted on the forums. Here is a quote from my thread, for an easy fix:


>  Re: where is my Firefox 3.5? I now have Shiretoko 3.5
Quote:
Originally Posted by Justin Trouble View Post
If you've used the ubuntu-mozilla-daily PPA ([http://ppa.launchpad.net/ubuntu-mozi...tu/jaunty/main](http://ppa.launchpad.net/ubuntu-mozi...tu/jaunty/main)) to install Firefox then you've most likely got a daily development build, not the final 3.5 version. I wouldn't recommend this.

Either install Firefox 3.5 (branded as Shiretoko) from the Jaunty-proposed repository (it may be in main from today) or the branded Firefox from mozilla.org, or using Ubuntuzilla: [http://ubuntumanual.org/posts/193/in...u-the-easy-way](http://ubuntumanual.org/posts/193/in...u-the-easy-way)
Thanks justin, that worked a treat. I'm back in my comfort zone again 

in other words, the Ubuntuzilla script worked a treat, and is very easy to use.

[http://ubuntumanual.org/posts/193/in...u-the-easy-way](http://ubuntumanual.org/posts/193/in...u-the-easy-way)

---

### Post by Ascenti0n on 2009-07-09
Sorry, that link no longer seems to work. Try this one:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by lovinglinux on 2009-07-09
> **FoxFireX said:**
> Okay, I revert all changes and did the manual install in the tutorial, rebooted firefox..

And it says I'm using Firefox 3.0 still. -_-

heres terminal log.

```

XXXX@XXXX-Ubuntu:~$ cp -R ~/.mozilla ~/.mozilla.backup
XXXX@XXXX-Ubuntu:~$ sudo tar -jxvf firefox-*.tar.bz2 -C /opt
[sudo] password for XXXX: 
...
XXXX@XXXX-Ubuntu:~$ rm firefox-*.tar.bz2
XXXX@XXXX-Ubuntu:~$ sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
XXXX@XXXX-Ubuntu:~$ sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
XXXX@XXXX-Ubuntu:~$ sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
XXXX@XXXX-Ubuntu:~$ sudo ln -s /opt/firefox/firefox /usr/bin/firefox
XXXX@XXXX-Ubuntu:~$
```

It shouldn't be loading Firefox 3.0. You probably forgot to revert some of your previous manual changes.

Paste the output of the command below:

```
whereis firefox
```

---

### Post by lovinglinux on 2009-07-09
Also paste the output of these:

```
whereis firefox-3.0
```

```
whereis firefox-3.5
```

---

### Post by FoxFireX on 2009-07-09
firefox: /usr/bin/firefox.ubuntu /usr/bin/firefox /usr/share/firefox



also just ran that one download the guy above your post told me to try. And I'm still stuck with 3.0 it seems, theres not even a firefox 3.5 in the usr/lib/


```

XXXX@XXXX-Ubuntu:~$ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.6.1

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/ 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.5. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at http://ubuntuzilla.sourceforge.net/ for steps you can take to resolve this problem.]
  0. af           1. ar           2. as           3. be        
  4. bg           5. bn-BD        6. bn-IN        7. ca        
  8. cs           9. cy          10. da          11. de        
 12. el          13. en-GB       14. en-US       15. eo        
 16. es-AR       17. es-CL       18. es-ES       19. es-MX     
 20. et          21. eu          22. fa          23. fi        
 24. fr          25. fy-NL       26. ga-IE       27. gl        
 28. gu-IN       29. he          30. hi-IN       31. hr        
 32. hu          33. id          34. is          35. it        
 36. ja          37. ka          38. kk          39. kn        
 40. ko          41. ku          42. lt          43. lv        
 44. ml          45. mn          46. mr          47. nb-NO     
 48. nl          49. nn-NO       50. oc          51. or        
 52. pa-IN       53. pl          54. pt-BR       55. pt-PT     
 56. rm          57. ro          58. ru          59. si        
 60. sk          61. sl          62. sq          63. sv-SE     
 64. ta-LK       65. ta          66. te          67. th        
 68. tr          69. uk          70. vi          71. zh-CN     
 72. zh-TW     
Enter your choice of localization (integer, from 0 to 72): 14
You have chosen localization en-US. Is that correct [y/n]? 
Please enter 'y' or 'n': y

Updating repositories information with apt-get update. You may be prompted for your password.

[sudo] password for XXXX: 
Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Hit http://us.archive.ubuntu.com jaunty Release.gpg
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty Release
Hit http://us.archive.ubuntu.com jaunty-updates Release             
Hit http://security.ubuntu.com jaunty-security/main Packages        
Hit http://us.archive.ubuntu.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
The following packages were automatically installed and are no longer required:
  xulrunner-1.9.1 xulrunner-1.9.1-gnome-support
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
Success!: firefox-3.5.tar.bz2

Downloading Firefox archive from the Mozilla site

--2009-07-09 09:55:31--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/firefox-3.5.tar.bz2
           => `firefox-3.5.tar.bz2'
Resolving releases.mozilla.org... 216.165.129.141, 204.152.184.196, 202.177.202.154, ...
Connecting to releases.mozilla.org|216.165.129.141|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US ... done.
==> SIZE firefox-3.5.tar.bz2 ... 9908255
==> PASV ... done.    ==> RETR firefox-3.5.tar.bz2 ... done.
Length: 9908255 (9.4M)

100%[======================================>] 9,908,255   1.88M/s   in 5.4s    

2009-07-09 09:55:38 (1.74 MB/s) - `firefox-3.5.tar.bz2' saved [9908255]


Downloading Firefox signature from the Mozilla site

--2009-07-09 09:55:38--  ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/firefox-3.5.tar.bz2.asc
           => `firefox-3.5.tar.bz2.asc'
Resolving releases.mozilla.org... 204.152.184.113, 149.20.20.5, 128.61.111.9, ...
Connecting to releases.mozilla.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US ... done.
==> SIZE firefox-3.5.tar.bz2.asc ... 194
==> PASV ... done.    ==> RETR firefox-3.5.tar.bz2.asc ... done.
Length: 194

100%[======================================>] 194         --.-K/s   in 0.008s  

2009-07-09 09:55:39 (22.4 KB/s) - `firefox-3.5.tar.bz2.asc' saved [194]

tru::1:1247140575:0:3:1:5
gpg: error reading key: public key not found
gpg --list-keys --with-colons 0E3606D9
Mozilla GPG key not present on the system. Will attempt to retrieve from keyserver.
Process returned code 2

Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpg: requesting key 812347DD from hkp server subkeys.pgp.net
gpg: key 0E3606D9: public key "Mozilla Software Releases <releases@mozilla.org>" imported
gpg: key 812347DD: public key "Mozilla Software Releases <releases@mozilla.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 2
gpg:               imported: 2
Successfully retrieved Mozilla Software Releases Public key from subkeys.pgp.net .


Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Wed 24 Jun 2009 03:49:59 PM EDT using DSA key ID 17785FE8
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 8D6F 1BA4 A340 4DDB 3F2F  D080 7447 4499 8123 47DD
     Subkey fingerprint: 3338 E6BA FF10 3B3D A6A9  E424 B57B 5484 1778 5FE8
Trying to determine firefox plugin path...

Linking plugins


Linking dictionaries


Linking launcher to new Firefox

Leaving `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 3.5 has been installed successfully.

Would you like to set up automatic update checking for the official Mozilla build of Firefox (recommended)? This feature will regularly check for updates to Firefox, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
no crontab for XXXX
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, http://ubuntuzilla.sourceforge.net/ , and click the donate button.
```

---

### Post by lovinglinux on 2009-07-09
Please don't install anything else. I will give a series of commands to revert everything. If you keep installing different versions will be hard to find the problem.

First right-click on all Firefox launchers on your desktop (one at a time) , then select properties and copy what you see in the command option. Paste it here and wait for more instructions.

---

### Post by Ascenti0n on 2009-07-09
it sounds simply that you have both Firefox versions installed. Nothing wrong there.

type in a terminal:
> cd /usr/bin

then 

> ls -l fire*

and you should see all the Firefox versions installed.

---

### Post by FoxFireX on 2009-07-09
Give me one sec, I will post a screenshot, theres only one launcher on my desktop.

If somebody would like to connect via remote desktop let me know would be easier[IMG]http://img38.imageshack.us/img38/6647/screenshotyod.png[/IMG]








lrwxrwxrwx 1 root root 20 2009-07-09 09:57 firefox -> /opt/firefox/firefox
lrwxrwxrwx 1 root root 32 2009-07-09 09:25 firefox-3.0 -> ../lib/firefox-3.0.11/firefox.sh
lrwxrwxrwx 1 root root 11 2009-07-09 09:25 firefox.ubuntu -> firefox-3.0

also.

---

### Post by lovinglinux on 2009-07-09
Change that launcher command to **firefox %u**


First, let's remove the installation from Ubuntuzilla and form the method I suggested.

```
ubuntuzilla.py -a remove -p firefox
```

```
sudo rm /usr/bin/firefox && sudo dpkg-divert --rename --remove /usr/bin/firefox && sudo rm -r /opt/firefox
```


Now choose one of the methods from the tutorial (the second one is the same method suggested by Ascenti0n):

1 - Manual installation of fresh final releases from Mozilla

this method is easy to perform, gives you total control of which version you will install and it gives you only official Mozilla releases, with Firefox branding (name and logo). Additionally, it uses the same Firefox profiles as the official Ubuntu version and updates your Firefox launchers automatically. It does not provide new version checking and download. You have to download new versions manually, remove the old version before updating with a new one and perform the installation commands for each new install.

2 - Automatic installation of fresh final releases from Mozilla

essentially the same as the method #1, but provides a way to check for updates from Mozilla releases site and install them automatically. Also provides an automated method of removal. Initial setup is not as easy as the manual installation, but is not complicated at all, since the automated script is provided as a deb install. It requires a single command to perform installation/removal of Firefox and other Mozilla applications.

---

### Post by FoxFireX on 2009-07-09
XXXX@XXXX-Ubuntu:~$ sudo rm /usr/bin/firefox && sudo dpkg-divert --rename --remove /usr/bin/firefox && sudo rm -r /opt/firefox
No diversion `any diversion of /usr/bin/firefox', none removed
rm: cannot remove `/opt/firefox': No such file or directory


I'll play a game of chess while i wait for you to read this, i'll check back every 2 mins or so.


EDIT: FFFUUU--- The computer on EASY to extremely hard to beat. Or maybe I just suck :(

---

### Post by lovinglinux on 2009-07-09
> **FoxFireX said:**
> XXXX@XXXX-Ubuntu:~$ sudo rm /usr/bin/firefox && sudo dpkg-divert --rename --remove /usr/bin/firefox && sudo rm -r /opt/firefox
No diversion `any diversion of /usr/bin/firefox', none removed
rm: cannot remove `/opt/firefox': No such file or directory


I'll play a game of chess while i wait for you to read this, i'll check back every 2 mins or so.

Ok, no problem there. It means it was already removed.

We only need more two steps:

1 - make sure your launcher in the desktop has the command **firefox %u** instead of /usr/lib/firefox-3.0.11/firefox-3.0

2 - repeat the Ubuntuzilla installation

```
ubuntuzilla.py -a install -p firefox
```

Launch firefox and it should be Firefox 3.5 with the correct logo and name.

---

### Post by FoxFireX on 2009-07-09
It worked! SWEEETTTT!!!

Hey dude ya think we can stay in touch somehow lol?

AIM,MSN? or anything else that pidgin supports.

It would be awesome to have a linux guru online, that I can just message if I have a quick question or something ya know? otherwise I just have to use here.


Gonna install some themes now woot, If I can figure out how to rofl.

Would definitely say linux is so much better then windows, excluding the fact that its less user friendly, and takes longer to learn and get used to, and the fact that nothing modern is supported by it without the use of wine, which sometimes fails. But its so much faster.


I wanna customize my ubuntu and make it look really sexy.

Any recommendations?

Things somebody that wants to customize their ubuntu to make it look cool should have?

Tell me what things I should get.

or if you could just give me a bunch of terminal commands, that will download, install all the good stuff for me.

Pretty sure I downloaded compiz already from package manger

---

### Post by lovinglinux on 2009-07-09
> **FoxFireX said:**
> It worked! SWEEETTTT!!!

See? If you knew about these methods, all these procedures could be avoided. You just would have to use the Ubuntuzilla script or the other method to install it. It's pretty easy when you do it for the first time, without modifying other stuff.

My advice, before doing stuff, ask for help in the forums and don't run commands you don't know. Additionally, when you post a question, wait for a few replies. Don't go running everything in a row. Sometimes there are different methods of accomplishing the same thing and they might have different degrees of difficulties. Besides, when someone suggests a different method, it doesn't necessarily mean that you can try one after another. 

> **FoxFireX said:**
> 
Hey dude ya think we can stay in touch somehow lol?

AIM,MSN? or anything else that pidgin supports.

It would be awesome to have a linux guru online, that I can just message if I have a quick question or something ya know? otherwise I just have to use here.

I don't do IM :)  I'm not a guru. I don't even have an year of experience with Linux ;) Besides, the forum is full of people with a lot more experience than me and they all reply to posts regularly. Feel free to send PM's but you will be better supported by posting here in the Absolute Beginner Talk forum.


> **FoxFireX said:**
> I wanna customize my ubuntu and make it look really sexy.

Any recommendations?

Things somebody that wants to customize their ubuntu to make it look cool should have?

Tell me what things I should get.

[http://www.gnome-look.org/](http://www.gnome-look.org/)
[http://customize.org/](http://customize.org/)
[http://ubuntuforums.org/forumdisplay.php?f=329](http://ubuntuforums.org/forumdisplay.php?f=329)
[http://ubuntuforums.org/showthread.php?t=1201267](http://ubuntuforums.org/showthread.php?t=1201267)

I like Compiz, screenlets and awn.

My Desktop: [http://ubuntuforums.org/showpost.php?p=7378756&postcount=10](http://ubuntuforums.org/showpost.php?p=7378756&postcount=10)

---

### Post by FoxFireX on 2009-07-09
Thanks :D! Awesome desktop by the way!

---

### Post by caravel on 2009-07-09
> **lovinglinux said:**
> Not a good idea. You shouldn't remove Firefox 3.0.11 and even if you do so, the proper way is trough the package manager.

That remninds me of the "IE should not be removed from Windows" fiasco.  If a user wants to remove something like a browser then they should be able to without affecting the normal functioning of the OS.

---

### Post by lovinglinux on 2009-07-09
> **caravel said:**
> That remninds me of the "IE should not be removed from Windows" fiasco.  If a user wants to remove something like a browser then they should be able to without affecting the normal functioning of the OS.

Actually I don't really know what side effects could be created by Firefox removal, but I do not recommend removing it, specially manually deleting files. All applications removal should be performed through the package manager, which controls dependencies on other packages. For example, if you remove Firefox 3.0, then when you try to install gecko-mediaplayer plugin, it installs Firefox 3.0 again. 

Obviously that you can do a lot more than what it is suggested, but i don't think is a good idea to recommend such things on a beginner forum.

By the way, Windows is a monolith compared to Ubuntu.

---

