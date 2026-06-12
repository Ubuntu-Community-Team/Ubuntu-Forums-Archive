---
title: "shotwell not showing in default system language"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by yakinikku on 2010-11-21
running 10.04.1, downloaded and installed shotwell via the software center, however it is not showing in the default system language, rather it is defaulting to english.  any ideas?

---

### Post by Daveth on 2010-11-21
I think this bug post may provide a clue as to why it does not change language.

[HTML]https://bugs.launchpad.net/ubuntu-translations/+bug/616856[/HTML]

It might need someone else's opinion to confirm this though!

---

### Post by fly-by-night on 2010-11-21
> **yakinikku said:**
> running 10.04.1, downloaded and installed shotwell via the software center, however it is not showing in the default system language, rather it is defaulting to english.  any ideas?

Did you try and change the language within Shotwell.  Edit/Preferences(or Options) OR Tools/Preferences perhaps.

Also from the above (by Daveth) bug report :  Did you install the latest version?  If Shotwell is regularly updated, the one in the Software Centre might be outdated.

---

### Post by yakinikku on 2010-11-22
> **fly-by-night said:**
> Did you try and change the language within Shotwell.  Edit/Preferences(or Options) OR Tools/Preferences perhaps.

Also from the above (by Daveth) bug report :  Did you install the latest version?  If Shotwell is regularly updated, the one in the Software Centre might be outdated.

that was the first thing i looked for but there is no preferences menu under edit, or any other menu for that matter

---

### Post by yakinikku on 2010-11-22
> **Daveth said:**
> I think this bug post may provide a clue as to why it does not change language.

[HTML]https://bugs.launchpad.net/ubuntu-translations/+bug/616856[/HTML]

It might need someone else's opinion to confirm this though!

interesting...that may be the issue, however on 10.04.1 version 0.7.1 is not available via synaptic or the software center, the newest version available is 0.5.

---

### Post by adamdingle on 2010-11-22
yakinikku,

I work at Yorba, the open source group that develops Shotwell.  I strongly recommend that you upgrade to Shotwell 0.7, which has a more complete set of translations and many more features as well.  You're right that the Ubuntu repository for 10.04.1 contains only Shotwell 0.5.  You can upgrade to 0.7 using the Yorba PPA.  To do that, follow the instructions on the page [http://yorba.org/shotwell/install](http://yorba.org/shotwell/install) .  In the BINARIES section, click the Ubuntu button and follow the directions below.  Good luck!

adam

---

### Post by yakinikku on 2010-11-22
> **adamdingle said:**
> yakinikku,

I work at Yorba, the open source group that develops Shotwell.  I strongly recommend that you upgrade to Shotwell 0.7, which has a more complete set of translations and many more features as well.  You're right that the Ubuntu repository for 10.04.1 contains only Shotwell 0.5.  You can upgrade to 0.7 using the Yorba PPA.  To do that, follow the instructions on the page [http://yorba.org/shotwell/install](http://yorba.org/shotwell/install) .  In the BINARIES section, click the Ubuntu button and follow the directions below.  Good luck!

adam

thanks adam, actually i had solved this before i looked at this page by following the instructions i found here

[http://www.ubuntugeek.com/shotwell-0-7-2-released-and-installation-instructions-included.html#more-8551](http://www.ubuntugeek.com/shotwell-0-7-2-released-and-installation-instructions-included.html#more-8551)

which are the same as yours :).

---

