---
title: "reply to thread Re: Alsa 1.0.15"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by diehardlinux on 2009-02-21
Distribution used with: Ubuntu-7.10
Scripts actually work. I modified the scripts slightly and add the following lines:
#alsa_1.sh
#
#changed lines
echo "installing necessary stuff"
apt-get install build-essential ncurses-dev gettext xmlto xmltoman linux-headers-2.6.22-14-generic

mkdir -p /usr/src/alsa/
cd /usr/src/alsa

#write changes and close

#
#alsa_2.sh
#reboot needed after second shell is ran.
#add note for user to reboot on second script at end of shell:
#change lines
#end of alsa_2
echo "now reboot your machine."

#
#
notes: must select new sound device on login after reboot (system, preferences, sound). Alsa playback can now be selected.

Much thanks to syxbit for his script work "http://ubuntuforums.org/showthread.php?t=577699&page=2"

---

