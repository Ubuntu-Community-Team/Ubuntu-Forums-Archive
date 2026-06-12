---
title: "ubuntu-restricted-extras firefox plugins?"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by fremantle on 2011-04-15
i have a fresh installation of 10.10. i installed u-res-extras, and then installed ff4 from ppa. and now i have no plugin (divx, totem, etc.)

---

### Post by idoitprone on 2011-04-15
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

do you have all the codecs?

[http://ubuntuforums.org/showthread.php?t=687738](http://ubuntuforums.org/showthread.php?t=687738)

---

### Post by fremantle on 2011-04-15
yeas, i do. i can play all files in my hdd. but i dont have the plugins for ff. i checked in tools>plugins

---

### Post by idoitprone on 2011-04-15
really? 
enter in the address url "about:plugins"

its about -semicolon-plugins

post screen shot. Now i have to manually find the proper files that you may have to soft link to you firefox plugin page.

---

### Post by fremantle on 2011-04-15
here thats all the plugins i have. even after installing res extras

---

### Post by idoitprone on 2011-04-15
wait you only install ubuntu-restrictive extras, i believe there are more stuff to install. Go to the mediubuntu link i gave you, since you have to add other repositories

Dont worry it will be easy since it basically a copy paste from the wiki to the terminal.

---

### Post by fremantle on 2011-04-15
but in the past whenever i installed res extras i had ALL the plugins for firefox. for example in lucid and in natty devs. why isnt it working now?

---

### Post by fremantle on 2011-04-15
> **idoitprone said:**
> wait you only install ubuntu-restrictive extras, i believe there are more stuff to install. Go to the mediubuntu link i gave you, since you have to add other repositories

Dont worry it will be easy since it basically a copy paste from the wiki to the terminal.
wheres the medibuntu link?

---

### Post by lovinglinux on 2011-04-15
The ubuntu-restricted-extras only install flash and java plugins. You need to install the other plugins as well. You don't need Medibuntu for that.

Depending on the ppa you used to install Firefox 4, it will clone your user profile from *~/.mozilla/firefox* to *~/.mozilla/firefox-4.0*. That happens with *mozillateam-firefox-next*, but not with *mozillateam-firefox-stable*.

Anyways, that shouldn't be a reason for not displaying your installed plugins, since the browser fetches them from the lib directory. However, it is possible that something went wrong and you you got a corrupted profile. Try to delete the file *pluginreg.dat* from your profile and restart Firefox. But first make sure you have the plugins installed.

I recommend [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by idoitprone on 2011-04-15
here the link
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)



next time get linux mint, they prepackage the codecs

[http://distrowatch.com/table.php?distribution=mint](http://distrowatch.com/table.php?distribution=mint)

i was reading the post above to see what is he saying. dododo bye. always listen to the guy smarter than me

---

### Post by fremantle on 2011-04-15
> **lovinglinux said:**
> The ubuntu-restricted-extras only install flash and java plugins. You need to install the other plugins as well. You don't need Medibuntu for that.

Depending on the ppa you used to install Firefox 4, it will clone your user profile from *~/.mozilla/firefox* to *~/.mozilla/firefox-4.0*. That happens with *mozillateam-firefox-next*, but not with *mozillateam-firefox-stable*.

Anyways, that shouldn't be a reason for not displaying your installed plugins, since the browser fetches them from the lib directory. However, it is possible that something went wrong and you you got a corrupted profile. Try to delete the file *pluginreg.dat* from your profile and restart Firefox. But first make sure you have the plugins installed.

i found plugins.ini not .dat

---

### Post by lovinglinux on 2011-04-15
> **fremantle said:**
> i found plugins.ini not .dat

I think you meant profiles.ini. Don't delete that, since it contains your profiles list. The pluginreg.dat is further inside the profiles folders. Nevertheless, I don't think you need to do that anyway. Is clear now that you didn't install the plugins. That's why they are not showing.

Just tell which plugins you need and I will write the installation commands for you.

---

