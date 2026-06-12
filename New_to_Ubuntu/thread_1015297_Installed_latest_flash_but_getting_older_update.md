---
title: "Installed latest flash but getting older update??"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-12-18
I've just installed the latest flash from the Adobe website but I keep getting prompted to download an update which reverts my flash install back to the previous older release...

How can I stop it from doing this?

---

### Post by kansasnoob on 2008-12-18
What version of Ubuntu are you using? 8.10, 8.04, 7.10, older?

---

### Post by kostkon on 2008-12-18
> **kamitsukai said:**
> I've just installed the latest flash from the Adobe website but I keep getting prompted to download an update which reverts my flash install back to the previous older release...

How can I stop it from doing this?
I think it's an update for *Flash 10*, not *Flash 9*. I got the same update today. You are getting an update for the *adobe-flashplugin* package because you have the *Partner* repository enabled in your software sources list.

This is the same package that *Adobe* offer from their site. I assume there was a new version.

Or,
did you remove *flashpluggin-nonfree* package (Flash 9) when you installed the *adobe-flashplugin* package (Flash 10).

---

### Post by kamitsukai on 2008-12-18
I'm on ubuntu 8.10 and i removed the old flash plaugin ans then downloaded and installed the flash plugin from the main website

---

### Post by kamitsukai on 2008-12-19
it's getting kind of annoying now... :P

---

### Post by kostkon on 2008-12-19
> **kamitsukai said:**
> it's getting kind of annoying now... :P
OK. You are using 8.10. The thing is that you didn't need to install the plugin from Adobe to get Flash 10, since in 8.10, the *flashplugin-nonfree* package installs the same version, Flash 10 (and not Flash 9, like in 8.04).

Nevertheless, a vulnerability was found in Flash and there is now a new version of Flash 10.

I assume that you are getting an update notification for the package that you have downloaded from Adobe (it is named *adobe-flashplugin*). This is happening because the same package is now offered by the *Partner* repository and so you obviously are getting an notification to update to the latest version from this repository.

Could you check if that's the case? i.e. does the update manager lists an update for a package named *flashplugin-nonfree* or a package named *adobe-flashplugin*?

---

### Post by kamitsukai on 2008-12-20
it was adobe-flashplugin the only reason that i had to install the one from the website was because of the new bbc iplayer for linux wouldnt install till i did....

---

