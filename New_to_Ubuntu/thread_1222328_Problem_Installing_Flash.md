---
title: "Problem Installing Flash"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by Commisar Jimp on 2009-07-24
I've got Ubuntu 64, and I am trying to get flash to work so I can visit youtube, but I can't work it out. Flash.tar.gz isn't in Synaptic, and I'm not sure how to get it in apt, so I downloaded it straight from the Flash website, but when I click on the installer it says it is an executable test file and gives me the option to run in terminal, display, cancel or run. Running in terminal just make the terminal flash up then disappear. Display shows the source code, and run does nothing, how do I install it? Btw, I don't mind going through apt, I just don't know how.

---

### Post by starcraft.man on 2009-07-24
Two means. You can install the meta-package *ubuntu-restricted-extras* which will net you a lot of extras like codecs for video, MS fonts, java, etc (almost all useful). The other option, simply install the flash package in the repos. It's called *flashplugin-installer*.

See my install guide in sig for more instructions.

---

### Post by Commisar Jimp on 2009-07-24
Thanks, I downloaded the meta-package, but the terminal displayed a EULA from Sun. I scrolled to the bottom and hit enter, but I can't advance past it, this feels like a really n00bish question, but how do I agree to the terms? (it's labeled "configuring sun-java6-jre" at the top)

---

### Post by starcraft.man on 2009-07-24
> **Commisar Jimp said:**
> Thanks, I downloaded the meta-package, but the terminal displayed a EULA from Sun. I scrolled to the bottom and hit enter, but I can't advance past it, this feels like a really n00bish question, but how do I agree to the terms? (it's labeled "configuring sun-java6-jre" at the top)

Make sure the terminal is highlighted, then push tab and ya should be at an ok option in the text gui. Then it will ask if you agree, use tab and select yes and push enter.

A lesson, this is fairly universal. All pseudological gui's (cross between text and gui) use tab to move from menus/selections, enter as confirm and arrows to move around.

There are no stupid questions btw, don't feel down about asking.

---

### Post by Commisar Jimp on 2009-07-24
> **starcraft.man said:**
> Make sure the terminal is highlighted, then push tab and ya should be at an ok option in the text gui. Then it will ask if you agree, use tab and select yes and push enter.

A lesson, this is fairly universal. All pseudological gui's (cross between text and gui) use tab to move from menus/selections, enter as confirm and arrows to move around.

There are no stupid questions btw, don't feel down about asking.

thanks so much... but more problems. I installed both packages, but I still can't play flash videos. the terminal says flashplugin is ready to be manually installed, how does that work?

---

