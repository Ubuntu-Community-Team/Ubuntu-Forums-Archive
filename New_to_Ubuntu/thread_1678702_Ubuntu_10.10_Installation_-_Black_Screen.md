---
title: "Ubuntu 10.10 Installation - Black Screen?"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by kestal on 2011-01-30
Hello everyone.

I don't imagine I've ever had this problem before with installing Ubuntu.. I have an Nvidia 8500gt and when I go to install Ubuntu 10.10, after the purple screen with the keyboard and person at the bottom, It goes to a black screen then my monitor shuts off.

I also tested with a built in ATI-based card and it worked just fine, and an ATI 5770.

I do not recall ever having seen my monitor turn off and stay off when installing any version of Ubuntu prior to 10.10.

Any ideas? I downloaded multiple times (32-bit and 64-bit).

---

### Post by diablo75 on 2011-01-30
You might try to install with the Alternate CD instead of the Live CD.  It's text-based and will help you bypass hardware incompatabilities that sometimes come up during install.

There is also a "Safe Video Mode" (or something like that) option available with the Live CD you have.  When that purple screen comes up, press Enter, select English, then look at the F4 option at the bottom for Modes to see if you can start it up through that.  Use the Alternate CD if that doesn't work and then apply all available updates and install hardware drivers after installation.

---

### Post by kestal on 2011-01-30
well, I managed to try a nomodeset and I was able to go through the installation but at a horrible display size (I've used Ubuntu with this card many times and I never had problems with it).

However, when I booted up, the same thing happened. Black screen then monitor shuts off. Remains off.

I guess I will play with a few other options..

But yes, keeping in mind that this is a fresh install + nvidia 8500gt...

---

### Post by myth1914 on 2011-01-30
> **diablo75 said:**
> You might try to install with the Alternate CD instead of the Live CD.  It's text-based and will help you bypass hardware incompatabilities that sometimes come up during install.

There is also a "Safe Video Mode" (or something like that) option available with the Live CD you have.  When that purple screen comes up, press Enter, select English, then look at the F4 option at the bottom for Modes to see if you can start it up through that.  Use the Alternate CD if that doesn't work and then apply all available updates and install hardware drivers after installation.

Agreed.  I have a Dell 755, same experience.  I installed with the alternate CD without issue.  However, I still had to boot from the onboard video to install the Nvidia/ATI drivers before it would boot to the login screen on the external card.  The catch 22 is, in my situation, the newest bios halts, stating you need to use the external video rather than the onboard.  In this case, I had to install the Nvidia or FGLRX drivers then install the card and boot.

Another note:  If you are attempting audio using the fglrx driver, the only way I was able to get it working is to do the above to boot on the ATI card, then remove it in synaptic and run the hardware driver tool to configure the card.  There may be a better solution, but if so, I couldn't come up with it.

---

