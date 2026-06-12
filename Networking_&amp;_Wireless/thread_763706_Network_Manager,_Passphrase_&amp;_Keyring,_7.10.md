---
title: "Network Manager, Passphrase &amp; Keyring, 7.10"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by jtrindle on 2008-04-23
I know this has been asked before, but I'm wondering if there is a solution other than "install wicd".  I'd like to stick with the distribution configuration where possible.

My wireless card works fine *except* that I am prompted for the WPA passphrase periodically.  The WPA key has been saved in the login keyring.  I am not prompted for my keyring password, but for the WPA passphrase.

Is there a way to make things work without roaming (I only need to connect to one network, this is a desktop machine)?  Does 8.04 fix this problem?

I am new to Ubuntu and to Linux desktop in general, but I have been running Debian servers for years, so I'm familiar with the command line.

Thanks!

---

### Post by jtrindle on 2008-04-24
I've switched to WiCD, and had some challenges setting the passphrase.  I got it working, and am still having some sort of problem  I had before, in that the dang thing has to reconnect too often.  I have "78%" to "80%" signal as reported by Network Manager.

The issue hits me hardest when I'm trying to use Remote Desktop from work.  Things work OK until I do something (not sure what) computer intensive, and then the machine goes off the network.  When I get home I'm usually being prompted for a passphrase.

Is there an issue specific to USB wireless (Linksys USB) involving dropped connections?  There are no other noise sources in the room, and my WinXP Thinkpad T60 works flawlessly with wireless.

---

### Post by ElaneFreuyh on 2008-04-25
I did notice this problem while running 7.10, when the network connection would sometimes drop out. Once it had dropped out, it would never successfully reconnect - every time I entered the password, the dialog would reappear about 5 seconds later.

Now I'v installed 8.04, The problem has become persistent. As soon as I log on, it asks for the passphrase. 5 seconds after I enter the password, the dialog pops up again.


xubuntu (64bit version)
athlon 3000+

ADSL router/modem
WPA / TKIP

---

### Post by jtrindle on 2008-04-28
The root cause of the problem seems to be the rt73/rt2x000 driver stack... I'm getting frequent errors in dmesg and syslog.  They seem to be worse when I load the system.  If I reduce my video resolution and turn off the second monitor support my connection lasts a lot longer.

Now I've installed the 2008042717 version of the seamonkey Seamonkey repository and compiled the driver.  The new install gets the same kind of errors (Vendor Request 0x07 failed with error -110) but the driver recovers instead of dying.  I've been off and on for 4 hours with a remote VNC connection and an ssh terminal login and am seeing adequate performance despite the errors.

---

### Post by ElaneFreuyh on 2008-04-29
mm. meethinks i am way over my head here.

on the plus side, "Hardy killed my network connection" threads have sprung up all over the forum - so we're not alone.

I plan on giving it a week or so (during which time i shall be using the enemy's OS) - see if anyone figures it out.

---

