---
title: "Log Files disappearing + other questions."
date: 2010-08-11
forum: New to Ubuntu
---

### Post by I_Want_To_Learn on 2010-08-11
Hello

Ubuntu 10.04 LTS installed on my 800mhz Celeron, 256MB RAM computer (...waits for readers to stop laughing...) using the Desktop CD purchased on Canonical's Online Store. I've notice various problems/issues while using Ubuntu so I'm seeking help & clarification from the community here.

Log Files - Logs being deleted?

Using Ubuntu for a week now & I've been frequently looking @ my logs in hope of understanding them using the Log File Viewer. One day after disconnecting from the internet, I noticed my logs from past days somehow got deleted! The logs just started logging again from that time as if nothing happened. Also after using the Update Manager today to download & install the latest updates, I notice my syslog did the same thing. Is this normal behavior? or is something wrong here? What are some things I can do to solve this issue?

Cant Install from Ubuntu Desktop CD

Before connecting online, I wanted to see what other packages I can install offline using the Ubuntu Desktop CD. I used the instructions listed below:

[https://help.ubuntu.com/10.04/add-applications/C/offline.html](https://help.ubuntu.com/10.04/add-applications/C/offline.html)

Inserted the CD --> opened Synaptic & selected Origin --> saw the cd not being automatically detected. So I went to Software Sources --> Other Software --> Add CD-ROM button. I then get the following error message:

Error scanning the CD
E: Failed to mount the CDRom

The CD is being detected because it says "Ubuntu 10.04 LTS i386" on my CD drive & I'm able to browse the CD.

Version of GRUB installed?

Just want to confirm GRUB version 1.98 is the new GRUB 2?

Weird "quirks" while using Ubuntu

-Sometimes when shutting down, I don't get the standard "Ubuntu with loading dots screen". I instead get text messages then it shuts down. Sometimes when shutting down, the computer just freezes @ a black screen. I have to press the power button to complete the shut down process.

-Sometimes when opening programs, the theme changes to another theme (Panels are grey). I have to go back to System --> Pref. --> Appearance to change it back although the file browser is still displaying the other theme.

-Sometimes after logging in, I get my Ubuntu background but no panels! I have to restart via Ctrl+Alt+Del. Sometimes I get a missing button (s) on my panel.

..are some weird stuff I've experienced so far while using Ubuntu. Can I contribute them to using Ubuntu on such an old computer? or are they symptoms of a real problem?

Thank You

---

### Post by linux18 on 2010-08-11
> **I_Want_To_Learn said:**
> Hello

Ubuntu 10.04 LTS installed on my 800mhz Celeron, 256MB RAM computer (...waits for readers to stop laughing...)  What! thats 10 times better than my 83MHz celeron with 64 MB of ram running debian. 

anyway logfiles get rotated (I believe the program is called logrotate)

I'll add more here once I read the rest of your post

EDIT: grub 1.98 = grub 2

EDIT 2:  yeah that shutdown thing happens sometimes

EDIT 3: for the panel thing press ctrl+alt+f2, type sudo /etc/init.d/gdm stop &&  sudo /etc/init.d/gdm start

---

### Post by Ozymandias_117 on 2010-08-11
Linux18 is correct, Log files get rotated. Logs are stored in /var/log you can check there to make sure that they ARE getting archived and new ones are being created, not just getting deleted. (Mine are named like aptitude.log aptitude.log.1 aptitude.log.2 etc)

Yes, that's GRUB 2.


The others sound a bit strange... How much RAM is Ubuntu using? How big is your Swap file?

---

### Post by linux18 on 2010-08-11
> **Ozymandias_117 said:**
> Linux18 is correct, Log files get rotated. Logs are stored in /var/log you can check there to make sure that they ARE getting archived and new ones are being created, not just getting deleted. (Mine are named like aptitude.log aptitude.log.1 aptitude.log.2 etc)

Yes, that's GRUB 2.


The others sound a bit strange... How much RAM is Ubuntu using? How big is your Swap file?
I am almost always right, 86% of the time.

the logout thing is normal, the panel thing is rare but not a cause for concern
I'm not sure about the theme thing or the cd thing

---

### Post by Ozymandias_117 on 2010-08-11
> **linux18 said:**
> I am almost always right, 86% of the time.

the logout thing is normal, the panel thing is rare but not a cause for concern
I'm not sure about the theme thing or the cd thing

I've occasionally not gotten the pretty screen, but I've never had to press the power button. I've never had the theme or the panel thing happen. Never tried to install from CD though.

---

### Post by I_Want_To_Learn on 2010-08-12
Ahh, didn't know that logs gets rotated. Checking /var/log & I indeed have the older logs. So that issue is solved...Thanks! :D

> The others sound a bit strange... How much RAM is Ubuntu using? How big is your Swap file? 

Using System Monitor. I'm using about 154MB Ram out of 243MB Total (Dunno why it says 243MB when I have 256MB) with FF open. After booting I'm using about 134MB. The Swap is 712MB total.

I can live with these "quirks" because "life is not perfect", just want to make sure it's nothing serious. Maybe it's something to do with my graphic card? because I've read a couple of topics on here saying Ubuntu doesn't play too nice with Intel 8XX integrated graphic cards. I know I get the same problem as this thread:

[http://ubuntuforums.org/showthread.php?t=1478103](http://ubuntuforums.org/showthread.php?t=1478103)

..but I brushed it off since unlike other users, I'm still able to get to the login screen and log in to Ubuntu.

If anybody have any insight about the CD problem, feel free to share. I'm thinking since I'm able to browse the CD, the CD drive is mounted properly, right?

---

### Post by Ozymandias_117 on 2010-08-12
> **I_Want_To_Learn said:**
> Ahh, didn't know that logs gets rotated. Checking /var/log & I indeed have the older logs. So that issue is solved...Thanks! :D



Using System Monitor. I'm using about 154MB Ram out of 243MB Total (Dunno why it says 243MB when I have 256MB) with FF open. After booting I'm using about 134MB. The Swap is 712MB total.

I can live with these "quirks" because "life is not perfect", just want to make sure it's nothing serious. Maybe it's something to do with my graphic card? because I've read a couple of topics on here saying Ubuntu doesn't play too nice with Intel 8XX integrated graphic cards. I know I get the same problem as this thread:

[http://ubuntuforums.org/showthread.php?t=1478103](http://ubuntuforums.org/showthread.php?t=1478103)

..but I brushed it off since unlike other users, I'm still able to get to the login screen and log in to Ubuntu.

If anybody have any insight about the CD problem, feel free to share. I'm thinking since I'm able to browse the CD, the CD drive is mounted properly, right?

It probably shows 243MB because it's probably shared RAM for your integrated graphics. Meaning your graphics card is stealing the rest of your RAM :P.

---

