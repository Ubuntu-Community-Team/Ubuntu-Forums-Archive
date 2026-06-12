---
title: "Chrome crashes on startup and ATI driver issues"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by fcmessi on 2010-02-23
Hey,

I am running Ubuntu 8.10 right now and I just got it up and running today. I am facing two issues though.

1. Chrome beta just crashes the moment I click on it. The window gets displayed for a few seconds and then closes. I tried reinstalling the package but to no avail.

2. My ATI Radeon HD3200 drivers are not being auto installed through System -> Administration -> Hardware Drivers. When I click on Activate, the downloading window appears and then vanishes. 

Any help would be appreciated :)

---

### Post by themusicalduck on 2010-02-23
Just out of interest, why did you install 8.10? The latest release is 9.10 and LTS is 8.04. 9.10 might perform better than 8.10.

You could find out why chrome is crashing if you run it in a terminal. Go to Applications > Accessories > Terminal and type in ```
google-chrome
``` hit enter and see if there is any error.

Not sure about the ATI problem. You could download the driver from the ATI website and install it from there instead, or find and install the driver through synaptic (System>Administration>Synaptic Package Manager) but I'm not sure which packages you need to install in that case. (Someone on here might know)

---

### Post by fcmessi on 2010-02-23
Yep, I know 9.10 is the latest release but I had a pretty old download of ubuntu just languishing about and felt like putting it to some use.

I tried downloading the drivers too, but when I tried to install them through the terminal, the install just got stuck.

---

