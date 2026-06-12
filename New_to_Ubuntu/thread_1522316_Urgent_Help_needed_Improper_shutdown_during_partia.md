---
title: "Urgent Help needed: Improper shutdown during partial upgrade: Help to recover files"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by astrobob.tk on 2010-07-02
Hello guys,

You help is urgently needed.

I have until recently been working on Ubuntu 9.04. When I inserted the 10.04 disc, 9.04 promoted to upgrade. I canceled, but the update manger kept asking for partial upgrade which I finally permitted. I nthe process, my system crashed (i was also using firefox & openoffice.org word processor).

The system seems unable to load. I am currently working from the 10.04 live disc. I request your help to retrieve many files on my system. Those include files & folders on the desktop & My Documents. I also need the latest firefox bookmarks & the "saved sessions" from Opera.

I'd like to move/copy these files to my external HDD. I tried to copy the desktop files but many of them I can't retrieve due to denied permission. I also tried doing so using: "gksudo nautilus" but it does no better job. ](*,)

Hope you could help asap.

I use: Dell Inspiron 8600. Win XP SP 3, KUbuntu 9.04 (my main use is gnome) & Fedora (maybe 10, I don't use this distro anymore).

you help is appreciated. thx in advance :P

---

### Post by akureikorineko on 2010-07-02
You could use su from the livecd and copy the files you need.

```
su
cp /path/to/file /path/to/save
```

---

### Post by astrobob.tk on 2010-07-02
authentication failed. what directory should i be in to issue su ?

---

### Post by akureikorineko on 2010-07-02
you should just be able to become su. su = sudo = root. If you are booting from a livecd, the su should work, unless it has been disabled. (I am a linux mint user mostly, but use ubuntu for other things.)

When you type "su" in the command line from the livecd, does it let you become root? minus the quotations.

---

### Post by prshah on 2010-07-02
> **astrobob.tk said:**
> update manger kept asking for partial upgrade which I finally permitted. I nthe process, my system crashed (i was also using firefox & openoffice.org word processor).

The system seems unable to load. 

I request your help to retrieve many files on my system. 

I use: Dell Inspiron 8600. Win XP SP 3, KUbuntu 9.04 (my main use is gnome)

Without going the "proper" way, here's a quick tip: In your Windows installation, install Ext2 IFS drivers from [www.fs-driver.org](www.fs-driver.org). This will allow you access to your linux partitions from Windows XP. Enable read-only access, (you may need to reboot) and then copy your files via Windows.

Then, let's try to recover your system: Boot back into Ubuntu recovery, more and give the command```
sudo dpkg --configure -a
``` to complete the interrupted upgrade. More details about this is here: [Hardy is wonderful..]("http://ubuntuforums.org/showpost.php?p=4872499&postcount=1")

Please post back with results and details if you need more help.

---

### Post by astrobob.tk on 2010-07-02
actually "su" asks for a password. its failing.
 
 i managed to change to root using "sudo -i". I then was able to use "cp -  r Desktop Destination" to copy them. Its seems it worked coz i got no  error or msg. I checked my files & they're in the destination, but  checking the number of items (through properties after selecting them  all) & there are more items in the destination. Originally there are  97 items totaling 225 MB (some contents unreadable) compared to 827  items totaling 330MB. Would it be the unreadable contents that combine  to 827 items ?

@prshah: I prefer to learn to do it on linux. I do know some commands & as i mentioned above it seems to work. I am now retrieving the other files.

Now i need your help in finding the firefox bookmarks & the opera saved sessions plz. I am sure they should be saved somewhere within the Filesystem right ?

As for trying this from windows, I will do try it though i prefer not to after all I am on my last step to get rid of Windows. All that hooks me to Win for the time being is Photoshop which i will surely replace with gimp once I get accustomed with it & a couple of pro software i use.
I will also get back for you help in regard of trying to fix the system, though i will be installing a fresh one after I do so :)
Speaking of the recovery mode: should I run the command after selecting to use the shell ?

---

### Post by prshah on 2010-07-02
> **astrobob.tk said:**
> finding the firefox bookmarks & the opera saved sessions plz. 

Speaking of the recovery mode: should I run the command after selecting to use the shell ?

No idea about opera, but firefox profile will be saved in a random name under ~/.mozilla/firefox/ ("~" indicates your home directory).

Presumably, opera stuff will be under "~/.opera".

When you are copying using sudo, please use "-p" to preserve permissions and ownerships, otherwise you will have to manually change permissions and ownerships when you copy then back. (If you are copying to a FAT32 partition, "-p" has no effect, and for an NTFS partition only minimal).

Yes, the command is to be run in a recovery mode (root) shell session.

If your HDD is giving the "click-of-death", it may not help at all to try to recover it. In any case, you need to also run a check for bad sectors (bad blocks): use fsck with the "-c" (-cc for more thorough and longer) option.

---

### Post by astrobob.tk on 2010-07-02
> **prshah said:**
> No idea about opera, but firefox profile will be saved in a random name under ~/.mozilla/firefox/ ("~" indicates your home directory).

Presumably, opera stuff will be under "~/.opera".

I tried searching for such directories using the "locate" command but can't seem to find it any.
Here's what i get when searching for opera:
```
$ locate opera
/lib/modules/2.6.32-21-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-opera.ko
/usr/lib/evolution/2.28/plugins/liborg-gnome-exchange-operations.so
/usr/lib/evolution/2.28/plugins/org-gnome-exchange-operations.eplug
/usr/lib/pitivi/python/pitivi/factories/operation.py
/usr/lib/pitivi/python/pitivi/factories/operation.pyc
/usr/lib/pymodules/python2.6/lazr/restfulclient/docs/operations.txt
/usr/lib/python2.6/dist-packages/twisted/test/test_cooperator.py
/usr/lib/python2.6/dist-packages/twisted/test/test_cooperator.pyc
/usr/lib/python2.6/lib2to3/fixes/fix_operator.py
/usr/lib/python2.6/lib2to3/fixes/fix_operator.pyc
/usr/share/evolution/2.28/errors/org-gnome-exchange-operations.error
/usr/share/man/man7/operator.7.gz
/usr/share/pyshared/lazr/restfulclient/docs/operations.txt
/usr/share/pyshared/twisted/test/test_cooperator.py
/usr/src/linux-headers-2.6.32-21-generic/include/config/dvb/usb/opera1.h
```& here's what I get for firefox:

```
/usr/lib/firefox-3.6.3/libnspr4.so
/usr/lib/firefox-3.6.3/libnss3.so
/usr/lib/firefox-3.6.3/libnssckbi.so
/usr/lib/firefox-3.6.3/libnssdbm3.chk
/usr/lib/firefox-3.6.3/libnssdbm3.so
/usr/lib/firefox-3.6.3/libnssutil3.so
/usr/lib/firefox-3.6.3/libplc4.so
/usr/lib/firefox-3.6.3/libplds4.so
/usr/lib/firefox-3.6.3/libsmime3.so
/usr/lib/firefox-3.6.3/libsoftokn3.chk
/usr/lib/firefox-3.6.3/libsoftokn3.so
/usr/lib/firefox-3.6.3/libsqlite3.so
/usr/lib/firefox-3.6.3/libssl3.so
/usr/lib/firefox-3.6.3/libxpcom.so
/usr/lib/firefox-3.6.3/libxul.so
/usr/lib/firefox-3.6.3/modules
/usr/lib/firefox-3.6.3/platform.ini
/usr/lib/firefox-3.6.3/plugins
/usr/lib/firefox-3.6.3/res
/usr/lib/firefox-3.6.3/run-mozilla.sh
/usr/lib/firefox-3.6.3/searchplugins
/usr/lib/firefox-3.6.3/chrome/browser-branding-en-US.jar
/usr/lib/firefox-3.6.3/chrome/browser-branding-en-US.manifest
/usr/lib/firefox-3.6.3/chrome/browser-branding.jar
/usr/lib/firefox-3.6.3/chrome/browser-branding.manifest
/usr/lib/firefox-3.6.3/chrome/browser.jar
/usr/lib/firefox-3.6.3/chrome/browser.manifest
/usr/lib/firefox-3.6.3/chrome/classic.jar
/usr/lib/firefox-3.6.3/chrome/classic.manifest
/usr/lib/firefox-3.6.3/chrome/comm.jar
/usr/lib/firefox-3.6.3/chrome/comm.manifest
/usr/lib/firefox-3.6.3/chrome/en-US.jar
/usr/lib/firefox-3.6.3/chrome/en-US.manifest
/usr/lib/firefox-3.6.3/chrome/icons
/usr/lib/firefox-3.6.3/chrome/pippki.jar
/usr/lib/firefox-3.6.3/chrome/pippki.manifest
/usr/lib/firefox-3.6.3/chrome/toolkit.jar
/usr/lib/firefox-3.6.3/chrome/toolkit.manifest
/usr/lib/firefox-3.6.3/chrome/icons/default
/usr/lib/firefox-3.6.3/chrome/icons/default/default16.png
/usr/lib/firefox-3.6.3/chrome/icons/default/default32.png
/usr/lib/firefox-3.6.3/chrome/icons/default/default48.png
/usr/lib/firefox-3.6.3/components/FeedConverter.js
/usr/lib/firefox-3.6.3/components/FeedProcessor.js
/usr/lib/firefox-3.6.3/components/FeedWriter.js
/usr/lib/firefox-3.6.3/components/GPSDGeolocationProvider.js
/usr/lib/firefox-3.6.3/components/NetworkGeolocationProvider.js
/usr/lib/firefox-3.6.3/components/WebContentConverter.js
/usr/lib/firefox-3.6.3/components/browser.xpt
/usr/lib/firefox-3.6.3/components/fuelApplication.js
/usr/lib/firefox-3.6.3/components/jsconsole-clhandler.js
/usr/lib/firefox-3.6.3/components/libbrowsercomps.so
/usr/lib/firefox-3.6.3/components/libbrowserdirprovider.so
/usr/lib/firefox-3.6.3/components/libdbusservice.so
/usr/lib/firefox-3.6.3/components/libimgicon.so
/usr/lib/firefox-3.6.3/components/libmozgnome.so
/usr/lib/firefox-3.6.3/components/libnkgnomevfs.so
/usr/lib/firefox-3.6.3/components/nsAddonRepository.js
/usr/lib/firefox-3.6.3/components/nsBadCertHandler.js
/usr/lib/firefox-3.6.3/components/nsBlocklistService.js
/usr/lib/firefox-3.6.3/components/nsBrowserContentHandler.js
/usr/lib/firefox-3.6.3/components/nsBrowserGlue.js
/usr/lib/firefox-3.6.3/components/nsContentDispatchChooser.js
/usr/lib/firefox-3.6.3/components/nsContentPrefService.js
/usr/lib/firefox-3.6.3/components/nsDefaultCLH.js
/usr/lib/firefox-3.6.3/components/nsDownloadManagerUI.js
/usr/lib/firefox-3.6.3/components/nsExtensionManager.js
/usr/lib/firefox-3.6.3/components/nsFilePicker.js
/usr/lib/firefox-3.6.3/components/nsFormAutoComplete.js
/usr/lib/firefox-3.6.3/components/nsHandlerService.js
/usr/lib/firefox-3.6.3/components/nsHelperAppDlg.js
/usr/lib/firefox-3.6.3/components/nsLivemarkService.js
/usr/lib/firefox-3.6.3/components/nsLoginInfo.js
/usr/lib/firefox-3.6.3/components/nsLoginManager.js
/usr/lib/firefox-3.6.3/components/nsLoginManagerPrompter.js
/usr/lib/firefox-3.6.3/components/nsMicrosummaryService.js
/usr/lib/firefox-3.6.3/components/nsPlacesAutoComplete.js
/usr/lib/firefox-3.6.3/components/nsPlacesDBFlush.js
/usr/lib/firefox-3.6.3/components/nsPlacesTransactionsService.js
/usr/lib/firefox-3.6.3/components/nsPrivateBrowsingService.js
/usr/lib/firefox-3.6.3/components/nsProxyAutoConfig.js
/usr/lib/firefox-3.6.3/components/nsSafebrowsingApplication.js
/usr/lib/firefox-3.6.3/components/nsSearchService.js
/usr/lib/firefox-3.6.3/components/nsSearchSuggestions.js
/usr/lib/firefox-3.6.3/components/nsSessionStartup.js
/usr/lib/firefox-3.6.3/components/nsSessionStore.js
/usr/lib/firefox-3.6.3/components/nsSetDefaultBrowser.js
/usr/lib/firefox-3.6.3/components/nsSidebar.js
/usr/lib/firefox-3.6.3/components/nsTaggingService.js
/usr/lib/firefox-3.6.3/components/nsTryToClose.js
/usr/lib/firefox-3.6.3/components/nsURLFormatter.js
/usr/lib/firefox-3.6.3/components/nsUpdateTimerManager.js
/usr/lib/firefox-3.6.3/components/nsUrlClassifierLib.js
/usr/lib/firefox-3.6.3/components/nsUrlClassifierListManager.js
/usr/lib/firefox-3.6.3/components/nsWebHandlerApp.js
/usr/lib/firefox-3.6.3/components/pluginGlue.js
/usr/lib/firefox-3.6.3/components/storage-Legacy.js
/usr/lib/firefox-3.6.3/components/storage-mozStorage.js
/usr/lib/firefox-3.6.3/components/txEXSLTRegExFunctions.js
/usr/lib/firefox-3.6.3/defaults/autoconfig
/usr/lib/firefox-3.6.3/defaults/pref
/usr/lib/firefox-3.6.3/defaults/profile
/usr/lib/firefox-3.6.3/defaults/syspref
/usr/lib/firefox-3.6.3/defaults/autoconfig/platform.js
/usr/lib/firefox-3.6.3/defaults/autoconfig/prefcalls.js
/usr/lib/firefox-3.6.3/defaults/pref/channel-prefs.js
/usr/lib/firefox-3.6.3/defaults/pref/firefox-branding.js
/usr/lib/firefox-3.6.3/defaults/pref/firefox-l10n.js
/usr/lib/firefox-3.6.3/defaults/pref/firefox.js
/usr/lib/firefox-3.6.3/defaults/pref/kde.js
/usr/lib/firefox-3.6.3/defaults/pref/ubuntu-useragent.js
/usr/lib/firefox-3.6.3/distribution/distribution.ini
/usr/lib/firefox-3.6.3/distribution/searchplugins
/usr/lib/firefox-3.6.3/greprefs/all.js
/usr/lib/firefox-3.6.3/greprefs/security-prefs.js
/usr/lib/firefox-3.6.3/greprefs/xpinstall.js
/usr/lib/firefox-3.6.3/icons/document.png
/usr/lib/firefox-3.6.3/icons/mozicon128.png
/usr/lib/firefox-3.6.3/modules/CertUtils.jsm
/usr/lib/firefox-3.6.3/modules/DownloadLastDir.jsm
/usr/lib/firefox-3.6.3/modules/DownloadUtils.jsm
/usr/lib/firefox-3.6.3/modules/FileUtils.jsm
/usr/lib/firefox-3.6.3/modules/ISO8601DateUtils.jsm
/usr/lib/firefox-3.6.3/modules/LightweightThemeConsumer.jsm
/usr/lib/firefox-3.6.3/modules/LightweightThemeManager.jsm
/usr/lib/firefox-3.6.3/modules/Microformats.js
/usr/lib/firefox-3.6.3/modules/NetUtil.jsm
/usr/lib/firefox-3.6.3/modules/NetworkPrioritizer.jsm
/usr/lib/firefox-3.6.3/modules/PlacesDBUtils.jsm
/usr/lib/firefox-3.6.3/modules/PluralForm.jsm
/usr/lib/firefox-3.6.3/modules/SpatialNavigation.js
/usr/lib/firefox-3.6.3/modules/WindowDraggingUtils.jsm
/usr/lib/firefox-3.6.3/modules/XPCOMUtils.jsm
/usr/lib/firefox-3.6.3/modules/ctypes.jsm
/usr/lib/firefox-3.6.3/modules/debug.js
/usr/lib/firefox-3.6.3/modules/distribution.js
/usr/lib/firefox-3.6.3/modules/openLocationLastURL.jsm
/usr/lib/firefox-3.6.3/modules/utils.js
/usr/lib/firefox-3.6.3/res/EditorOverride.css
/usr/lib/firefox-3.6.3/res/arrow.gif
/usr/lib/firefox-3.6.3/res/arrowd.gif
/usr/lib/firefox-3.6.3/res/broken-image.png
/usr/lib/firefox-3.6.3/res/charsetData.properties
/usr/lib/firefox-3.6.3/res/charsetalias.properties
/usr/lib/firefox-3.6.3/res/contenteditable.css
/usr/lib/firefox-3.6.3/res/designmode.css
/usr/lib/firefox-3.6.3/res/dtd
/usr/lib/firefox-3.6.3/res/entityTables
/usr/lib/firefox-3.6.3/res/fonts
/usr/lib/firefox-3.6.3/res/forms.css
/usr/lib/firefox-3.6.3/res/grabber.gif
/usr/lib/firefox-3.6.3/res/hiddenWindow.html
/usr/lib/firefox-3.6.3/res/html
/usr/lib/firefox-3.6.3/res/html.css
/usr/lib/firefox-3.6.3/res/langGroups.properties
/usr/lib/firefox-3.6.3/res/language.properties
/usr/lib/firefox-3.6.3/res/loading-image.png
/usr/lib/firefox-3.6.3/res/mathml.css
/usr/lib/firefox-3.6.3/res/quirk.css
/usr/lib/firefox-3.6.3/res/svg.css
/usr/lib/firefox-3.6.3/res/table-add-column-after-active.gif
/usr/lib/firefox-3.6.3/res/table-add-column-after-hover.gif
/usr/lib/firefox-3.6.3/res/table-add-column-after.gif
/usr/lib/firefox-3.6.3/res/table-add-column-before-active.gif
/usr/lib/firefox-3.6.3/res/table-add-column-before-hover.gif
/usr/lib/firefox-3.6.3/res/table-add-column-before.gif
/usr/lib/firefox-3.6.3/res/table-add-row-after-active.gif
/usr/lib/firefox-3.6.3/res/table-add-row-after-hover.gif
/usr/lib/firefox-3.6.3/res/table-add-row-after.gif
/usr/lib/firefox-3.6.3/res/table-add-row-before-active.gif
/usr/lib/firefox-3.6.3/res/table-add-row-before-hover.gif
/usr/lib/firefox-3.6.3/res/table-add-row-before.gif
/usr/lib/firefox-3.6.3/res/table-remove-column-active.gif
/usr/lib/firefox-3.6.3/res/table-remove-column-hover.gif
/usr/lib/firefox-3.6.3/res/table-remove-column.gif
/usr/lib/firefox-3.6.3/res/table-remove-row-active.gif
/usr/lib/firefox-3.6.3/res/table-remove-row-hover.gif
/usr/lib/firefox-3.6.3/res/table-remove-row.gif
/usr/lib/firefox-3.6.3/res/ua.css
/usr/lib/firefox-3.6.3/res/unixcharset.properties
/usr/lib/firefox-3.6.3/res/viewsource.css
/usr/lib/firefox-3.6.3/res/dtd/mathml.dtd
/usr/lib/firefox-3.6.3/res/dtd/xhtml11.dtd
/usr/lib/firefox-3.6.3/res/entityTables/html40Latin1.properties
/usr/lib/firefox-3.6.3/res/entityTables/html40Special.properties
/usr/lib/firefox-3.6.3/res/entityTables/html40Symbols.properties
/usr/lib/firefox-3.6.3/res/entityTables/htmlEntityVersions.properties
/usr/lib/firefox-3.6.3/res/entityTables/mathml20.properties
/usr/lib/firefox-3.6.3/res/entityTables/transliterate.properties
/usr/lib/firefox-3.6.3/res/fonts/mathfont.properties
/usr/lib/firefox-3.6.3/res/fonts/mathfontSTIXNonUnicode.properties
/usr/lib/firefox-3.6.3/res/fonts/mathfontSTIXSize1.properties
/usr/lib/firefox-3.6.3/res/fonts/mathfontStandardSymbolsL.properties
/usr/lib/firefox-3.6.3/res/fonts/mathfontUnicode.properties
/usr/lib/firefox-3.6.3/res/html/folder.png
/usr/lib/firefox-addons/extensions
/usr/lib/firefox-addons/plugins
/usr/lib/firefox-addons/searchplugins
/usr/lib/firefox-addons/extensions/langpack-aa@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-af@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-am@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ar@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-as@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ast@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-az@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-be@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ber@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-bg@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-bn-BD@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-bn-IN@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-bo@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-br@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-bs@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ca@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-crh@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-cs@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-csb@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-cy@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-da@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-de@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-dv@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-el@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-en-AU@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-en-CA@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-en-GB@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-en@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-eo@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-es-AR@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-es-CL@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-es-ES@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-es-MX@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-et@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-eu@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-fa-AF@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-fa@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-fi@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-fil@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-fo@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-fr@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-fur@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-fy-NL@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ga-IE@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-gd@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-gl@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-gu-IN@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-he@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-hi-IN@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-hr@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-hsb@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ht@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-hu@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-hy@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ia@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-id@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-is@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-it@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-iu@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ja@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ka@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-kk@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-km@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-kn@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ko@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ks@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ku@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-kw@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ky@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-la@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-li@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-lo@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-lt@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-lv@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-mg@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-mk@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ml@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-mn@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-mr@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ms@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-mt@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-nan@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-nb-NO@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-nds@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ne@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-nl@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-nn-NO@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-oc@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-om@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-or@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-pa-IN@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-pap@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-pl@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-pt-BR@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-pt-PT@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ro@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ru@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-rw@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-sa@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-sc@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-sd@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-shs@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-si@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-sk@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-sl@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-so@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-sq@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-sr@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-st@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-sv-SE@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ta-LK@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ta@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-te@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-tg@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-th@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ti@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-tl@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-tlh@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-tn@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-tr@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ts@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-tt@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ug@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-uk@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-ur@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-uz@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-vi@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-wo@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-xh@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-yi@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-yo@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-zh-CN@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-zh-HK@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-zh-TW@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-zu@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}
/usr/lib/firefox-addons/extensions/langpack-de@firefox-3.6.ubuntu.com/chrome
/usr/lib/firefox-addons/extensions/langpack-de@firefox-3.6.ubuntu.com/chrome.manifest
/usr/lib/firefox-addons/extensions/langpack-de@firefox-3.6.ubuntu.com/install.rdf
/usr/lib/firefox-addons/extensions/langpack-de@firefox-3.6.ubuntu.com/chrome/de.jar
/usr/lib/firefox-addons/extensions/langpack-en-GB@firefox-3.6.ubuntu.com/chrome
/usr/lib/firefox-addons/extensions/langpack-en-GB@firefox-3.6.ubuntu.com/chrome.manifest
/usr/lib/firefox-addons/extensions/langpack-en-GB@firefox-3.6.ubuntu.com/install.rdf
/usr/lib/firefox-addons/extensions/langpack-en-GB@firefox-3.6.ubuntu.com/chrome/en-GB.jar
/usr/lib/firefox-addons/extensions/langpack-uk@firefox-3.6.ubuntu.com/chrome
/usr/lib/firefox-addons/extensions/langpack-uk@firefox-3.6.ubuntu.com/chrome.manifest
/usr/lib/firefox-addons/extensions/langpack-uk@firefox-3.6.ubuntu.com/install.rdf
/usr/lib/firefox-addons/extensions/langpack-uk@firefox-3.6.ubuntu.com/chrome/uk.jar
/usr/lib/firefox-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/icon.png
/usr/lib/firefox-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
/usr/lib/firefox-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/preview.png
/usr/lib/firefox-addons/searchplugins/bn-BD
/usr/lib/firefox-addons/searchplugins/bn-IN
/usr/lib/firefox-addons/searchplugins/common
/usr/lib/firefox-addons/searchplugins/de
/usr/lib/firefox-addons/searchplugins/en-GB
/usr/lib/firefox-addons/searchplugins/en-US
/usr/lib/firefox-addons/searchplugins/es-AR
/usr/lib/firefox-addons/searchplugins/es-CL
/usr/lib/firefox-addons/searchplugins/es-ES
/usr/lib/firefox-addons/searchplugins/es-MX
/usr/lib/firefox-addons/searchplugins/fr
/usr/lib/firefox-addons/searchplugins/it
/usr/lib/firefox-addons/searchplugins/pt-BR
/usr/lib/firefox-addons/searchplugins/pt-PT
/usr/lib/firefox-addons/searchplugins/ru
/usr/lib/firefox-addons/searchplugins/zh-CN
/usr/lib/firefox-addons/searchplugins/zh-HK
/usr/lib/firefox-addons/searchplugins/zh-TW
/usr/lib/firefox-addons/searchplugins/de/amazondotcom.xml
/usr/lib/firefox-addons/searchplugins/de/answers.xml
/usr/lib/firefox-addons/searchplugins/de/creativecommons.xml
/usr/lib/firefox-addons/searchplugins/de/eBay.xml
/usr/lib/firefox-addons/searchplugins/de/google.xml
/usr/lib/firefox-addons/searchplugins/de/wikipedia.xml
/usr/lib/firefox-addons/searchplugins/de/yahoo.xml
/usr/lib/firefox-addons/searchplugins/en-GB/amazondotcom.xml
/usr/lib/firefox-addons/searchplugins/en-GB/answers.xml
/usr/lib/firefox-addons/searchplugins/en-GB/creativecommons.xml
/usr/lib/firefox-addons/searchplugins/en-GB/eBay.xml
/usr/lib/firefox-addons/searchplugins/en-GB/google.xml
/usr/lib/firefox-addons/searchplugins/en-GB/wikipedia.xml
/usr/lib/firefox-addons/searchplugins/en-GB/yahoo.xml
/usr/lib/firefox-addons/searchplugins/en-US/amazondotcom.xml
/usr/lib/firefox-addons/searchplugins/en-US/answers.xml
/usr/lib/firefox-addons/searchplugins/en-US/creativecommons.xml
/usr/lib/firefox-addons/searchplugins/en-US/eBay.xml
/usr/lib/firefox-addons/searchplugins/en-US/google.xml
/usr/lib/firefox-addons/searchplugins/en-US/wikipedia.xml
/usr/lib/firefox-addons/searchplugins/en-US/yahoo.xml
/usr/share/firefox
/usr/share/app-install/desktop/firefox-greasemonkey.desktop
/usr/share/app-install/desktop/firefox-launchpad-plugin.desktop
/usr/share/app-install/desktop/firefox-ubuntu-it-menu.desktop
/usr/share/app-install/desktop/firefox-webdeveloper.desktop
/usr/share/app-install/desktop/firefox.desktop
/usr/share/app-install/icons/firefox-greasemonkey.xpm
/usr/share/app-install/icons/firefox-installer.png
/usr/share/app-install/icons/firefox-launchpad-plugin.xpm
/usr/share/app-install/icons/firefox-themes-ubuntu.xpm
/usr/share/app-install/icons/firefox-ubuntu-it-menu.png
/usr/share/app-install/icons/firefox-webdeveloper.xpm
/usr/share/applications/firefox.desktop
/usr/share/apport/package-hooks/firefox.py
/usr/share/bug/firefox
/usr/share/bug/firefox/presubj
/usr/share/doc/firefox
/usr/share/doc/firefox-branding
/usr/share/doc/firefox-gnome-support
/usr/share/doc/firefox/MPL.gz
/usr/share/doc/firefox/README.Debian
/usr/share/doc/firefox/changelog.Debian.gz
/usr/share/doc/firefox/copyright
/usr/share/doc/firefox/firefox.cfg
/usr/share/doc/firefox-branding/changelog.Debian.gz
/usr/share/doc/firefox-branding/copyright
/usr/share/doc/firefox-gnome-support/changelog.Debian.gz
/usr/share/doc/firefox-gnome-support/copyright
/usr/share/firefox/defaults
/usr/share/firefox/defaults/pref
/usr/share/firefox/defaults/pref/apturl.js
/usr/share/menu/firefox
/usr/share/pixmaps/firefox.png
/usr/share/ubiquity-slideshow/slides/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.am/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.ar/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.ast/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.be/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.bg/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.bn/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.bs/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.ca/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.cs/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.da/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.de/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.el/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.en_AU/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.en_CA/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.en_GB/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.eo/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.es/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.et/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.eu/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.fi/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.fr/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.gl/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.he/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.hi/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.hr/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.hu/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.id/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.is/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.it/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.ja/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.kk/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.kn/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.ko/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.lt/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.lv/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.mn/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.nb/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.nl/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.nn/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.oc/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.pl/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.pt/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.pt_BR/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.ro/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.ru/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.si/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.sk/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.sl/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.sq/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.sr/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.sv/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.th/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.tr/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.uk/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.vi/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.zh_CN/firefox.html
/usr/share/ubiquity-slideshow/slides/loc.zh_TW/firefox.html
/usr/share/ubuntu-artwork/home/firefox-index.html
/usr/share/ubuntu-docs/common/prepare-firefox-startpage-translations
/usr/share/ubuntu-docs/libs/img/firefox-3.5.png
/var/cache/apt/archives/firefox-branding_3.6.3+nobinonly-0ubuntu4_i386.deb
/var/cache/apt/archives/firefox-gnome-support_3.6.3+nobinonly-0ubuntu4_i386.deb
/var/cache/apt/archives/firefox_3.6.3+nobinonly-0ubuntu4_i386.deb
/var/lib/dpkg/alternatives/firefox-homepage
/var/lib/dpkg/info/firefox-branding.list
/var/lib/dpkg/info/firefox-branding.md5sums
/var/lib/dpkg/info/firefox-gnome-support.list
/var/lib/dpkg/info/firefox-gnome-support.md5sums
/var/lib/dpkg/info/firefox-gnome-support.postinst
/var/lib/dpkg/info/firefox-gnome-support.prerm
/var/lib/dpkg/info/firefox.conffiles
/var/lib/dpkg/info/firefox.list
/var/lib/dpkg/info/firefox.md5sums
/var/lib/dpkg/info/firefox.postinst
/var/lib/dpkg/info/firefox.postrm
/var/lib/dpkg/info/firefox.preinst
/var/lib/dpkg/info/firefox.prerm
```> When you are copying using sudo, please use "-p" to preserve permissions and ownerships, otherwise you will have to manually change permissions and ownerships when you copy then back. (If you are copying to a FAT32 partition, "-p" has no effect, and for an NTFS partition only minimal).How would that affect the copied/moved files if i don't use "-p" when i work with them after a fresh installation ?

> If your HDD is giving the "click-of-death"What exactly is that ? could you please explain it a bit

---

### Post by corcomp84 on 2010-07-02
My system did the same thing, but I used the system update not the cd... after it had crashed it rebooted then asked for a partial update which I did.  after that it worked fine.. I hate the way Ubuntu updates from one version to another. I do know that it took a long time to reload after installing a partial update. how long did you give it.. and how far did it load before it stoped

---

### Post by astrobob.tk on 2010-07-02
> Then, let's try to recover your system: Boot back into Ubuntu recovery, more and give the command```
sudo dpkg --configure -a
``` to complete the interrupted upgrade. More details about this is here: [Hardy is wonderful..]("http://ubuntuforums.org/showpost.php?p=4872499&postcount=1")result:

> Configure rpm
Package information database for rpm cleaned up.
The database which rpm keeps about installed packages is not usable with the new version.
The old database has been moved to /var/backups. Please read /usr/share/doc/rpm/README.Debian for details
OK button After pressing OK another process was triggered for a minute or so & finally going back to root level shell.
After that I rebooted normally & was promoted with a login window which seemed to freeze. Actually it's not the login which freezes after all but  it seems that the keyboard & touch pad are simply not working. The only thing that works is the power button which turns the system off when pressed.

I should note that when in normal booting & just seconds before th login window appears I get this statement:

IO APIC could not be located
mount: mounting none on /dev failed: No such device


Anyways, I went back to shell in recovery mode & ran: ```
sudo apt-get upgrade
```result: > Reading package lists...Done
Building dependency lists...Done
Building dependency tree...Done

You might want to run 'apt-get -f install' to correct these.
the following packages have unmet dependencies:
cupsddk: Depends: cupsddk-drivers
phpmyadmin: Depends: php5-mcrypt but it is not installed.

E: unmet dependencies. Try using -f.I then ran ```
apt-get -f install cupsddk-drivers php5-mcrypt
``` which required the Jaunty disc. result:
> Failed to fetch [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com)It was suggested to use the same command without any options, i.e; ```
apt-get -f install
```This promoted to install the unmet dependencies but I got the same result:
> Unable to fetch some archives. maybe run ```
apt-get update
``` or ```
--fix -missing
```I issued ```
apt-get --fix -missing
``` to get > --fix is not understoodI then tried aptitude. I chose "g" for the "Upgradable package (346)" which leaded to the same result.

Finally when I was going to boot from the live disc & post the results I recalled that the update command I issued was NOT in the "shell mode with networking". I rebooted to recovery mode & used the "shell with networking" running the "update" command once more. Things went smoothly until i got:
> W: GPG error: [http://www.fbreader.org](http://www.fbreader.org) stable release: The following signatures couldn't be verified because the public key is not available.I retried > apt-get -f install & with the Jaunty disc things went smooth this time with not errors.
I then ran > autoremove & approved to remove 107 packages which are to free 250MB.

Then ran > autoclean & > check & rebooted. The keyboard & touch pad problem persists which doesn't allow me to log in.

I am now back on live disc.](*,)

---

### Post by astrobob.tk on 2010-07-03
Anyone out there ?

---

