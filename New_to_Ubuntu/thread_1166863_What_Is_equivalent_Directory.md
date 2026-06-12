---
title: "What Is equivalent Directory ??"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by aravindc26 on 2009-05-22
May I Know what is the equivalent directory for c:\programs in ubuntu.
which folder does the programs get installed when I install through synaptic manager ?

---

### Post by Tibuda on 2009-05-22
most executables are in /usr/bin

---

### Post by scorp123 on 2009-05-22
> **aravindc26 said:**
> May I Know what is the equivalent directory for c:\programs in ubuntu. **/usr/bin**  ... mostly.

> **aravindc26 said:**
>  which folder does the programs get installed when I install through synaptic manager ? You can ask the program itself. Let's suppose you wanted to know where Firefox has its files ... so you'd just ask the package manager: ```
dpkg -L firefox-3.0
```

This would spit out this list:
```
 /usr
/usr/lib
/usr/lib/firefox-addons
/usr/lib/firefox-addons/extensions
/usr/lib/firefox-addons/plugins
/usr/lib/firefox-addons/searchplugins
/usr/lib/firefox-addons/searchplugins/amazondotcom.xml
/usr/lib/firefox-addons/searchplugins/answers.xml
/usr/lib/firefox-addons/searchplugins/creativecommons.xml
/usr/lib/firefox-addons/searchplugins/eBay.xml
/usr/lib/firefox-addons/searchplugins/google.xml
/usr/lib/firefox-addons/searchplugins/wikipedia.xml
/usr/lib/firefox-addons/searchplugins/yahoo.xml
/usr/lib/firefox-addons/searchplugins/debsearch.gif
/usr/lib/firefox-addons/searchplugins/debsearch.src
/usr/lib/firefox-3.0.10
/usr/lib/firefox-3.0.10/components
/usr/lib/firefox-3.0.10/components/aboutRights.js
/usr/lib/firefox-3.0.10/components/aboutRobots.js
/usr/lib/firefox-3.0.10/components/FeedConverter.js
/usr/lib/firefox-3.0.10/components/FeedWriter.js
/usr/lib/firefox-3.0.10/components/fuelApplication.js
/usr/lib/firefox-3.0.10/components/nsBrowserContentHandler.js
/usr/lib/firefox-3.0.10/components/nsBrowserGlue.js
/usr/lib/firefox-3.0.10/components/nsMicrosummaryService.js
/usr/lib/firefox-3.0.10/components/nsPlacesTransactionsService.js
/usr/lib/firefox-3.0.10/components/nsSafebrowsingApplication.js
/usr/lib/firefox-3.0.10/components/nsSearchService.js
/usr/lib/firefox-3.0.10/components/nsSearchSuggestions.js
/usr/lib/firefox-3.0.10/components/nsSessionStartup.js
/usr/lib/firefox-3.0.10/components/nsSessionStore.js
/usr/lib/firefox-3.0.10/components/nsSetDefaultBrowser.js
/usr/lib/firefox-3.0.10/components/nsSidebar.js
/usr/lib/firefox-3.0.10/components/WebContentConverter.js
/usr/lib/firefox-3.0.10/components/browser.xpt
/usr/lib/firefox-3.0.10/components/libbrowsercomps.so
/usr/lib/firefox-3.0.10/components/libbrowserdirprovider.so
/usr/lib/firefox-3.0.10/modules
/usr/lib/firefox-3.0.10/modules/distribution.js
/usr/lib/firefox-3.0.10/firefox
/usr/lib/firefox-3.0.10/run-mozilla.sh
/usr/lib/firefox-3.0.10/defaults
/usr/lib/firefox-3.0.10/defaults/preferences
/usr/lib/firefox-3.0.10/defaults/preferences/firefox-l10n.js
/usr/lib/firefox-3.0.10/defaults/preferences/firefox.js
/usr/lib/firefox-3.0.10/defaults/preferences/firefox-branding.js
/usr/lib/firefox-3.0.10/defaults/preferences/channel-prefs.js
/usr/lib/firefox-3.0.10/defaults/preferences/ubuntu-useragent.js
/usr/lib/firefox-3.0.10/browserconfig.properties
/usr/lib/firefox-3.0.10/blocklist.xml
/usr/lib/firefox-3.0.10/application.ini
/usr/lib/firefox-3.0.10/distribution
/usr/lib/firefox-3.0.10/distribution/distribution.ini
/usr/lib/firefox-3.0.10/chrome
/usr/lib/firefox-3.0.10/chrome/classic.jar
/usr/lib/firefox-3.0.10/chrome/classic.manifest
/usr/lib/firefox-3.0.10/chrome/en-US.jar
/usr/lib/firefox-3.0.10/chrome/en-US.manifest
/usr/lib/firefox-3.0.10/chrome/browser.jar
/usr/lib/firefox-3.0.10/chrome/browser.manifest
/usr/lib/firefox-3.0.10/.autoreg
/usr/lib/firefox-3.0.10/firefox.sh
/usr/lib/firefox-3.0.10/firefox-3.0-restart-required.update-notifier
/usr/lib/firefox-3.0.10/ffox-3-beta-profile-migration-dialog
/usr/lib/xulrunner-addons
/usr/lib/xulrunner-addons/extensions
/usr/lib/xulrunner-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}
/usr/lib/xulrunner-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
/usr/lib/xulrunner-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/chrome.manifest
/usr/share
/usr/share/doc
/usr/share/doc/firefox-3.0
/usr/share/doc/firefox-3.0/copyright
/usr/share/doc/firefox-3.0/firefox.cfg
/usr/share/doc/firefox-3.0/MPL.gz
/usr/share/menu
/usr/share/menu/firefox-3.0
/usr/share/bug
/usr/share/bug/firefox-3.0
/usr/share/bug/firefox-3.0/presubj
/usr/share/apport
/usr/share/apport/package-hooks
/usr/share/apport/package-hooks/firefox-3.0.py
/usr/bin
/etc
/etc/firefox-3.0
/etc/firefox-3.0/profile
/etc/firefox-3.0/profile/bookmarks.html
/etc/firefox-3.0/profile/localstore.rdf
/etc/firefox-3.0/profile/prefs.js
/etc/firefox-3.0/profile/mimeTypes.rdf
/etc/firefox-3.0/profile/chrome
/etc/firefox-3.0/profile/chrome/userChrome-example.css
/etc/firefox-3.0/profile/chrome/userContent-example.css
/etc/firefox-3.0/pref
/etc/firefox-3.0/pref/firefox.js
/usr/lib/firefox-3.0.10/defaults/syspref
/usr/lib/firefox-3.0.10/defaults/profile
/usr/lib/firefox-3.0.10/abrowser
/usr/lib/firefox-3.0.10/abrowser-3.0
/usr/lib/firefox-3.0.10/firefox-3.0
/usr/lib/firefox-3.0.10/extensions
/usr/lib/firefox-3.0.10/plugins
/usr/lib/firefox-3.0.10/searchplugins
/usr/lib/firefox-3.0.10/dictionaries
/usr/share/doc/firefox-3.0/changelog.Debian.gz
/usr/bin/abrowser
/usr/bin/abrowser-3.0
/usr/bin/firefox
/usr/bin/firefox-3.0 
```

You can achieve the same by going into Synaptic and then looking at a package name and then at the "Installed Files" tab.

And while we're at it you may want to look at this Wikipedia article. It explains why all program files are in /usr/bin and why config files are in /etc and so on ....
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by lisati on 2009-05-22
There is no one place specifically equivalent to c:\programs

Have a look here: [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

---

### Post by aravindc26 on 2009-05-22
> **scorp123 said:**
> **/usr/bin**  ... mostly.

 You can ask the program itself. Let's suppose you wanted to know where Firefox has its files ... so you'd just ask the package manager: ```
dpkg -L firefox-3.0
```

This would spit out this list:
```
 /usr
/usr/lib
/usr/lib/firefox-addons
/usr/lib/firefox-addons/extensions
/usr/lib/firefox-addons/plugins
/usr/lib/firefox-addons/searchplugins
/usr/lib/firefox-addons/searchplugins/amazondotcom.xml
/usr/lib/firefox-addons/searchplugins/answers.xml
/usr/lib/firefox-addons/searchplugins/creativecommons.xml
/usr/lib/firefox-addons/searchplugins/eBay.xml
/usr/lib/firefox-addons/searchplugins/google.xml
/usr/lib/firefox-addons/searchplugins/wikipedia.xml
/usr/lib/firefox-addons/searchplugins/yahoo.xml
/usr/lib/firefox-addons/searchplugins/debsearch.gif
/usr/lib/firefox-addons/searchplugins/debsearch.src
/usr/lib/firefox-3.0.10
/usr/lib/firefox-3.0.10/components
/usr/lib/firefox-3.0.10/components/aboutRights.js
/usr/lib/firefox-3.0.10/components/aboutRobots.js
/usr/lib/firefox-3.0.10/components/FeedConverter.js
/usr/lib/firefox-3.0.10/components/FeedWriter.js
/usr/lib/firefox-3.0.10/components/fuelApplication.js
/usr/lib/firefox-3.0.10/components/nsBrowserContentHandler.js
/usr/lib/firefox-3.0.10/components/nsBrowserGlue.js
/usr/lib/firefox-3.0.10/components/nsMicrosummaryService.js
/usr/lib/firefox-3.0.10/components/nsPlacesTransactionsService.js
/usr/lib/firefox-3.0.10/components/nsSafebrowsingApplication.js
/usr/lib/firefox-3.0.10/components/nsSearchService.js
/usr/lib/firefox-3.0.10/components/nsSearchSuggestions.js
/usr/lib/firefox-3.0.10/components/nsSessionStartup.js
/usr/lib/firefox-3.0.10/components/nsSessionStore.js
/usr/lib/firefox-3.0.10/components/nsSetDefaultBrowser.js
/usr/lib/firefox-3.0.10/components/nsSidebar.js
/usr/lib/firefox-3.0.10/components/WebContentConverter.js
/usr/lib/firefox-3.0.10/components/browser.xpt
/usr/lib/firefox-3.0.10/components/libbrowsercomps.so
/usr/lib/firefox-3.0.10/components/libbrowserdirprovider.so
/usr/lib/firefox-3.0.10/modules
/usr/lib/firefox-3.0.10/modules/distribution.js
/usr/lib/firefox-3.0.10/firefox
/usr/lib/firefox-3.0.10/run-mozilla.sh
/usr/lib/firefox-3.0.10/defaults
/usr/lib/firefox-3.0.10/defaults/preferences
/usr/lib/firefox-3.0.10/defaults/preferences/firefox-l10n.js
/usr/lib/firefox-3.0.10/defaults/preferences/firefox.js
/usr/lib/firefox-3.0.10/defaults/preferences/firefox-branding.js
/usr/lib/firefox-3.0.10/defaults/preferences/channel-prefs.js
/usr/lib/firefox-3.0.10/defaults/preferences/ubuntu-useragent.js
/usr/lib/firefox-3.0.10/browserconfig.properties
/usr/lib/firefox-3.0.10/blocklist.xml
/usr/lib/firefox-3.0.10/application.ini
/usr/lib/firefox-3.0.10/distribution
/usr/lib/firefox-3.0.10/distribution/distribution.ini
/usr/lib/firefox-3.0.10/chrome
/usr/lib/firefox-3.0.10/chrome/classic.jar
/usr/lib/firefox-3.0.10/chrome/classic.manifest
/usr/lib/firefox-3.0.10/chrome/en-US.jar
/usr/lib/firefox-3.0.10/chrome/en-US.manifest
/usr/lib/firefox-3.0.10/chrome/browser.jar
/usr/lib/firefox-3.0.10/chrome/browser.manifest
/usr/lib/firefox-3.0.10/.autoreg
/usr/lib/firefox-3.0.10/firefox.sh
/usr/lib/firefox-3.0.10/firefox-3.0-restart-required.update-notifier
/usr/lib/firefox-3.0.10/ffox-3-beta-profile-migration-dialog
/usr/lib/xulrunner-addons
/usr/lib/xulrunner-addons/extensions
/usr/lib/xulrunner-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}
/usr/lib/xulrunner-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
/usr/lib/xulrunner-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/chrome.manifest
/usr/share
/usr/share/doc
/usr/share/doc/firefox-3.0
/usr/share/doc/firefox-3.0/copyright
/usr/share/doc/firefox-3.0/firefox.cfg
/usr/share/doc/firefox-3.0/MPL.gz
/usr/share/menu
/usr/share/menu/firefox-3.0
/usr/share/bug
/usr/share/bug/firefox-3.0
/usr/share/bug/firefox-3.0/presubj
/usr/share/apport
/usr/share/apport/package-hooks
/usr/share/apport/package-hooks/firefox-3.0.py
/usr/bin
/etc
/etc/firefox-3.0
/etc/firefox-3.0/profile
/etc/firefox-3.0/profile/bookmarks.html
/etc/firefox-3.0/profile/localstore.rdf
/etc/firefox-3.0/profile/prefs.js
/etc/firefox-3.0/profile/mimeTypes.rdf
/etc/firefox-3.0/profile/chrome
/etc/firefox-3.0/profile/chrome/userChrome-example.css
/etc/firefox-3.0/profile/chrome/userContent-example.css
/etc/firefox-3.0/pref
/etc/firefox-3.0/pref/firefox.js
/usr/lib/firefox-3.0.10/defaults/syspref
/usr/lib/firefox-3.0.10/defaults/profile
/usr/lib/firefox-3.0.10/abrowser
/usr/lib/firefox-3.0.10/abrowser-3.0
/usr/lib/firefox-3.0.10/firefox-3.0
/usr/lib/firefox-3.0.10/extensions
/usr/lib/firefox-3.0.10/plugins
/usr/lib/firefox-3.0.10/searchplugins
/usr/lib/firefox-3.0.10/dictionaries
/usr/share/doc/firefox-3.0/changelog.Debian.gz
/usr/bin/abrowser
/usr/bin/abrowser-3.0
/usr/bin/firefox
/usr/bin/firefox-3.0 
```

You can achieve the same by going into Synaptic and then looking at a package name and then at the "Installed Files" tab.

And while we're at it you may want to look at this Wikipedia article. It explains why all program files are in /usr/bin and why config files are in /etc and so on ....
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
Thanks guys that was usefull

---

### Post by Tibuda on 2009-05-22
I don't really like to tell about terminal commands in the absolute beginner talk, but the "which" commands returns the full path for any application.
```
$ which firefox
/usr/bin/firefox
$ which cat
/bin/cat
```

---

