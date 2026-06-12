---
title: "Start Firefox 5 in 32 bit mode"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by buntolith on 2011-07-09
With the new Firefox 5 (on Ubuntu 11.04 in 32 bit mode) I have noticed that I cannot longer log into by bank since my security program is only compatible with Firefox running in 32 bit mode. I suppose that the new versions of Firefox starts in 64 bit mode automatically.

Is it possible to change some setting so that Firefox starts up in 32 bit mode. This is apparently easy to do with a Mac but how can this be done in Ubuntu?

Thanks...

---

### Post by jtarin on 2011-07-09
If you installed Firefox in 32 bit it is in 32 bit. Where did you download from?

You might try [user-agent-switcher]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/")

or [Modify Headers add-on]("https://addons.mozilla.org/en-US/firefox/addon/modify-headers/")

---

### Post by buntolith on 2011-07-09
I once installed Ubuntu 10.10 on my netbook using the 32 bit version because of this problem with my security program from my bank that only runs in 32 bit mode. I have upgraded my Ubuntu version to 11.04 with no problem. I assume it is still running in 32 bit mode so I don't think the problem is Ubuntu. The problem is with Firefox. It was working fine before but since Firefox have been upgraded to version 5 it does not work anymore. And I assume that it has to do with Firefox 5 running in 64 bit mode by default now. I know Mac have had the same problem but they had an easy fix to the problem where it is possible to choose in which mode to start up Firefox during boot. I could install an older version of Firefox again, but I'd rather not.

So is it possible to change this setting in Firefox as it is possible on Mac in the finder?

---

### Post by jtarin on 2011-07-09
Firefox. It's not 64 bit. If you did not download 64 bit it is not 64 bit. Either try the links I gave you or downgrade Firefox.

---

### Post by mikewhatever on 2011-07-09
If you have a 32bit OS - 'Ubuntu 11.04 in 32 bit mode', it's pretty unlikely to have a 64bit Firefox.

---

### Post by lovinglinux on 2011-07-09
> **mikewhatever said:**
> If you have a 32bit OS - 'Ubuntu 11.04 in 32 bit mode', it's pretty unlikely to have a 64bit Firefox.

Indeed. Most likely there is an incompatibility in that extension with FF 5.

Please type **about:support** in the address bar, then copy the User Agent string and paste here.

BTW, there is no such 32bit/64bit switching mode on Ubuntu. Either you have a 32bit Firefox or a 64bit Firefox. However, if you are running a 64bit OS, you can still run a 32bit Firefox, if you install the 32bit version manually.

---

### Post by buntolith on 2011-07-15
Hi again and thanks a lot for the replies. Sorry for the late reply but I have been travelling?

It seems like my assumptions are wrong based upon some mac solutions? Anyway, this is my user agent string:

Mozilla/5.0 (X11; Linux i686; rv:5.0) Gecko/20100101 Firefox/5.0

Maybe I just have to downgrade my firefox to the version that was was working before :)

---

### Post by lovinglinux on 2011-07-15
> **buntolith said:**
> Hi again and thanks a lot for the replies. Sorry for the late reply but I have been travelling?

It seems like my assumptions are wrong based upon some mac solutions? Anyway, this is my user agent string:

Mozilla/5.0 (X11; Linux i686; rv:5.0) Gecko/20100101 Firefox/5.0

Maybe I just have to downgrade my firefox to the version that was was working before :)

You have Firefox 32bit. Most likely that your problem is a compatibility issue between the add-on and the new Firefox version. See the Add-on section of the first post of [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247")

---

### Post by buntolith on 2011-07-17
Thanks lovinglinux for your help. I will have to downgrade to Ff4 to get things to work. Or maybe just use a windows box :(

---

### Post by lovinglinux on 2011-07-17
> **buntolith said:**
> Thanks lovinglinux for your help. I will have to downgrade to Ff4 to get things to work. Or maybe just use a windows box :(

If the only thing that doesn't work is your bank plugin, then you don't need to downgrade or use Windows (doing bank transactions via Linux is much more secure than doing via Windows). Instead, [download the latest Firefox 3.6 from Mozilla]("http://www.mozilla.com/en-US/firefox/all-older.html"), extract it to your home directory, close all instances of Firefox, then launch FF 3.6 by clicking the *firefox* file inside the extracted folder. Better than downgrading, since you only need to start Firefox 3.6 to pay your bills and Firefox 4 won't be updated with security patches anymore, just Firefox 5 and 3.6.

Keep in mind that Firefox installed manually won't update automatically. You need to download each new version manually and replace it. If you think that is too much trouble, then use my [FoxTester]("https://addons.mozilla.org/en-US/firefox/addon/foxtester/") extension. It allows to install/uninstall/launch multiple versions and multiple builds of Firefox with just a click. All you need is to download them to the same directory.

---

### Post by buntolith on 2011-07-18
Thanks again lovinglinux for your great help. Your extension works great to launch different versions but it still doesn't work:(

When I run the 3.6 version it passes the web browser control OK but the browser doesn't find the "persadm" program that I need to have installed to be able to log into my bank. I have installed the "persadm" OK. It seems like the installation of the "persadm" program does not install the PKCS#11 module under preferences/advanced/security devices. When I try to load a new PKCS#11 module manually with the correct path to the file libP11.so that I find in the persadm folder (all according to instructions) firefox freeze up completely. 

I think the "persadm" program doesn't install the PKCS#11 module correctly because the firefox program is not in the normal location. Now with the changes I have made the firefox program is launched from /opt/foxtester/firefox. Is this correct?

Should I just try and uninstall everything and download the 3.6 version from Firefox and do a clean install. Do you have any other solution?

Thanks again!

---

### Post by lovinglinux on 2011-07-18
> **buntolith said:**
> Thanks again lovinglinux for your great help. Your extension works great to launch different versions but it still doesn't work:(

When I run the 3.6 version it passes the web browser control OK but the browser doesn't find the "persadm" program that I need to have installed to be able to log into my bank. I have installed the "persadm" OK. It seems like the installation of the "persadm" program does not install the PKCS#11 module under preferences/advanced/security devices. When I try to load a new PKCS#11 module manually with the correct path to the file libP11.so that I find in the persadm folder (all according to instructions) firefox freeze up completely. 

I think the "persadm" program doesn't install the PKCS#11 module correctly because the firefox program is not in the normal location. Now with the changes I have made the firefox program is launched from /opt/foxtester/firefox. Is this correct?

Should I just try and uninstall everything and download the 3.6 version from Firefox and do a clean install. Do you have any other solution?

Thanks again!

It could be due to the new location. However, when you install via FoxTester and make it default to install in the /opt/foxtester/firefox, it creates a symlink to the plugins folder. Not sure why it is not picking up.

---

