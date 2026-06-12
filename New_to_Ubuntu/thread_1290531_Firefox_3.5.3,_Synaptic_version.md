---
title: "Firefox 3.5.3, Synaptic version"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by donsy on 2009-10-13
I'm totally confused. I've read other posts on the Ubuntu forums about installing (and problems with) Firefox 3.5. Some claim that it's name is Shiretoko. I would like to install the latest version (without the problems). In Synaptic Package Manager is don't see a package for Shiretoko, however I do see one for firefox-3.5. Is this the package I need to install? After installation will I have to manually do something to make the launcher on the top panel point to the latest version?

---

### Post by HarrisonNapper on 2009-10-13
That is the correct package, you will not have to do anything. It will appear as Shiretoko Web Browser.

---

### Post by lovinglinux on 2009-10-13
> **donsy said:**
> I've read other posts on the Ubuntu forums about installing (and problems with) Firefox 3.5. 

Problems depend on several factors, particularly what extensions and profile conditions and settings the user has. 

> **donsy said:**
> Some claim that it's name is Shiretoko.

Yes. If you install from the repositories, then it's named Shiretoko to avoid confusion with the default install, since it is installed side-by-side with it.

> **donsy said:**
> I would like to install the latest version (without the problems).

If you find a way to install any application "without the problems" you would become a Linux god/goddess :)

Nevertheless, most potential issues can be avoided by following the tutorial [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Anyway, Firefox 3.5 is really good and much better than 3.0.x.

> **donsy said:**
> In Synaptic Package Manager is don't see a package for Shiretoko, however I do see one for firefox-3.5. Is this the package I need to install?

Yes.

> **donsy said:**
> After installation will I have to manually do something to make the launcher on the top panel point to the latest version?

Just drag the launcher from "Applications >> Internet >> Shiretoko Web Browser" to the panel. Ido not recommend messing with the original launcher at this point, since a new Ubuntu will be released soon and Firefox 3.5.3 will be the default browser. Keep in mind that if you do install FF 3.5 from the repositories, it will make a copy of your profile from ~/.mozilla/firefox to ~/.mozilla/firefox-3.5 to avoid messing with the profile used by FF 3.0. When the new Ubuntu comes out, Firefox 3.5 will use the original profile directory again, so you might need to manually synchronize them, so your bookmarks and settings changes while using Shiretoko are transfered to the official Firefox 3.5 profile.

There are also other methods of installation. The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm. I personally recommend Ubuntuzilla if you want to keep Firefox always updated according to Mozilla's releases.

---

