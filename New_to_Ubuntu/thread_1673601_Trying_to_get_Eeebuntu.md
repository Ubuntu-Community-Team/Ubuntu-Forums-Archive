---
title: "Trying to get Eeebuntu"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by Anarchy-_- on 2011-01-22
Hey, I'm running an Asus Eee PC Netbook, and I'm trying to get Eeebuntu instead of Windows 7 starter. I used unetbootin to make a USB bootable install of the eeebuntu 3.0 Standard build. I also burned the iso onto a dvd (using an external usb dvd drive). The problem I have is on the boot up, I think both of my possible booting options are good, but I can't make my netbook boot to anything other than windows. On startup I hit esc or f2 and it brings me to a boot screen, but windows 7 is the only option, or I can press tab to get to "Windows Memory Diagnostic Tool". Help?

---

### Post by Daveth on 2011-01-22
do you not need to set the bios to boot from the usb stick as the first device? Otherwise it will default to windows.

---

### Post by Anarchy-_- on 2011-01-22
Maybe you could help me get to the BIOS screen? I was under the impression you got there by hitting esc or f2 on bootup, but it just takes me to the screen I mentioned earlier, which isn't too helpful.

---

### Post by Paqman on 2011-01-22
On my EeePC 1000 it's F2, then go to the Boot tab and make sure the Boot Device Priority is set to "removable Dev." as the first item (put your SSD/HDD second), then reboot with your USB stick in and hit Esc to get the boot menu. Your USB stick should show up there.

---

### Post by Daveth on 2011-01-23
same with my EEEPC 710, you move along the line to the Boot tab and alter the boot priority, as Paqman notes

---

### Post by snowpine on 2011-01-23
Welcome to the forums, Anarchy!

Are you aware that Eeebuntu 3.0 was based on the now-obsolete Ubuntu 9.04 release? It has reached its "end of life" and is no longer supported in any way. The project is now called "Aurora" and their current release is called "Borealis." I'm not even sure if it's still based on Ubuntu. More info here: [http://www.auroraos.org/](http://www.auroraos.org/)

Is there a reason you don't use Ubuntu? Ubuntu runs great on most of the EEE models (you didn't mention which one you have so I can't be specific). Plus Ubuntu is the #1 Linux distro in the world and has a fantastic community here on ubuntuforums.org. :)

Anyways, that's a long-winded answer to your BIOS question. The specific answer will depend on which model EEE you have, but on my 900HA I had to hit F2 at a really precise moment (the "window of opportunity" was less than a second) until I was able to get into the BIOS and disable something called "boot booster." Once I did that, I was able to reboot and hit Esc at boot to select the boot-from-external-drive option. Do a search on your specific EEE model and you'll likely find some good info.

---

### Post by zhogan85 on 2011-01-23
I agree with snowpine. I was running Eeebuntu 3.0 on my Asus 1005 HA and while it eventually worked well, there were several things that didn't work out of the box, but I recently switched to Ubuntu 10.10 netbook edition and it worked much better out of the box, with only a couple minor fixes required. So far I'm quite happy with the switch.

---

### Post by dalee on 2011-01-23
> **snowpine said:**
> Welcome to the forums, Anarchy!

Anyways, that's a long-winded answer to your BIOS question. The specific answer will depend on which model EEE you have, but on my 900HA I had to hit F2 at a really precise moment (the "window of opportunity" was less than a second) until I was able to get into the BIOS and disable something called "boot booster." Once I did that, I was able to reboot and hit Esc at boot to select the boot-from-external-drive option. Do a search on your specific EEE model and you'll likely find some good info.

Hi,

My 1101HA is F2 also. And that Boot Booster is a pain in the backside. It took me 3 or 4 tries to get in to the bios to turn it off and enable boot device selection.

---

### Post by Anarchy-_- on 2011-01-23
Thanks snowpine! To be honest, you could probably convert me into using Ubuntu, I just heard that Eeebuntu was tailor made for for the eeepc and it sounded like a good match. I appreciate your help! I have a 1015PEB

---

### Post by Paqman on 2011-01-23
> **Anarchy-_- said:**
> Thanks snowpine! To be honest, you could probably convert me into using Ubuntu, I just heard that Eeebuntu was tailor made for for the eeepc and it sounded like a good match. I appreciate your help! I have a 1015PEB

Distros like Eeebuntu and Easy Peasy came about when the EeePC was quite new, and there were a couple of tweaks that were needed to make them work 100%. However, since then those tweaks have been rolled into the mainstream distros, so there's no real need for special distros just for the EeePC any more.

---

### Post by Anarchy-_- on 2011-01-23
So I got the bios up and got the eeebuntu loaded up. I was pretty unimpressed. Visually it was meh and it couldn't detect any wireless networks. So what version of Ubuntu would you guys suggest I download? A link wouldn't hurt ;)

---

### Post by snowpine on 2011-01-24
I am not familiar with your specific EEE model (I have an older 900HA) but if you use the forum Search feature, I'm sure you'll find some good information. :)

As far as "visually it was meh" I highly recommend [http://gnome-look.org](http://gnome-look.org)

> **Anarchy-_- said:**
> So what version of Ubuntu would you guys suggest I download? A link wouldn't hurt ;)

Ubuntu is available from [http://ubuntu.com](http://ubuntu.com) and the current version is 10.10 Maverick Meerkat.

---

### Post by s1wood on 2011-01-24
Ubuntu 10.10 netbook runs OK on my EeePC 900, few minor glitches but everything worked without problems.

Susan

---

### Post by mekon on 2011-02-03
I've got Easy Peasy running on an eee 700. I wouldn't mind a newer version of Ubuntu as this seems to have stopped being worked on.

---

