---
title: "installing firefox 3.5"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by supre on 2009-10-15
hi there. i am using ubuntu netbook remix on my msi wind.

i want to upgrade from firefox 3 to 3.5 because the address bar in firefox 3 is complete rubbish but in 3.5 there is an option to fix it back to the way address bars have worked for the past 20 years (which was just fine).

well it wasnt as easy as just downloading and executing a file so i googled a bunch and was told to type apt-get install firefox-3.5.

i did this and now i have some garbage called Shiretoko with a stupid blue icon that appears to be firefox 3.5 but it obviously isn't if it isnt called that and doesnt use the same icons it must be some sort of enchanted firefox that i dont want.

---

### Post by aysiu on 2009-10-15
> **supre said:**
> hi there. i am using ubuntu netbook remix on my msi wind.

i want to upgrade from firefox 3 to 3.5 because the address bar in firefox 3 is complete rubbish but in 3.5 there is an option to fix it back to the way address bars have worked for the past 20 years (which was just fine).

well it wasnt as easy as just downloading and executing a file so i googled a bunch and was told to type apt-get install firefox-3.5.

i did this and now i have some garbage called Shiretoko with a stupid blue icon that appears to be firefox 3.5 but it obviously isn't if it isnt called that and doesnt use the same icons it must be some sort of enchanted firefox that i dont want.
This should help you:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by supre on 2009-10-15
```
 if [[ ! -f /usr/bin/firefox ]]; then sudo apt-get update && sudo apt-get install firefox; fi && if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox

```

why thank you kind sir! i am very lucky there was a top linux scientist working on this very matter for without his diligent work in this field of upgrading to firefox 3.5 i would have been left a hopeless mess trying to find the proper combination of key presses to succeed.

---

