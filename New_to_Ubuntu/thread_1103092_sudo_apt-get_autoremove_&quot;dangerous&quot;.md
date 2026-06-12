---
title: "sudo apt-get autoremove &quot;dangerous&quot; ?"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by Vulgor Schnecke on 2009-03-22
hello everyone,

ive searched the forum and i havent quite found an answer to my question, maybe its just because im totally new to ubuntu, been using it for maybe 2 weeks now.

have been trying a lot of new programs in ubuntu, installing and removing them. now i wanted to kinda of clean my computer and after reading some posts my understanding is that "sudo apt-get autoremove" basically gets rid of packages/libraries/etc. that arent being used anymore. so i typed in that command and now my comp tells me that "after this operation, 412 MB will be freed", showing me a long list of libraries and what else there is. so this kinda scares me, cuz this is like a big chunk of the whole OS, and i dont recall even getting close to 50 MB of programs i installed and removed alltogether.

i think i used the autoremove command once, removing a couple MB maybe, and afterwards when using apt-get update my comp told me some dependencies were brokenSo my question is, can autoremove actually kill my system or damage it beyond a point where i can still repair it?. 

thx for ur help!

---

### Post by HermanAB on 2009-03-22
Unscrambling an egg is always more difficult.

If you want to experiment, install Virtualbox or VMware, make an Ubuntu VM (save a copy to a DVD) and experiment with that.  That is how developers build packages and test things without destroying their host systems.

However, since you have only started, you likely don't have anything important on your machine and re-installing Ubuntu only takes about 30 minutes, so you can go nuts with it and re-install when it screws up.

Cheers,

Herman

---

### Post by Rocket2DMn on 2009-03-22
Can you please copy and paste here the list of packages that it is telling you about?  That does seem like a lot, so we should check and see what they are.

---

### Post by leonardo_neo on 2009-03-22
I usually run that command periodically on my comp to clean my system, and I never had any trouble.

I also run the following command

 > sudo apt-get autoclean 

I think you should be good after you run the command.

---

### Post by Vulgor Schnecke on 2009-03-22
wow, thankls for the quick replies

yeah, heres the list (supposedly to be 101 to be removed......)
"
 ca-certificates-java default-jre-headless exfalso gdesklets-data hddtemp
  kde-icons-oxygen kdebase-runtime kdebase-runtime-bin-kde4
  kdebase-runtime-data kdebase-runtime-data-common kdelibs-bin kdelibs5
  kdelibs5-data khelpcenter khelpcenter4 ladcca2 libaccess-bridge-java
  libaudclient1 libaudid3tag1 libavahi1.0-cil libbinio1ldbl libboo2.0-cil
  libcddb2 libclucene0ldbl libconvert-binhex-perl libcrypt-ssleay-perl
  libdumb1 libemail-date-format-perl libestools1.2 libfcgi-perl libfluidsynth1
  libgda3-3 libgda3-bin libgda3-common libgdl-1-0 libgdl-1-common
  libio-socket-ssl-perl libio-stringy-perl libjcode-pm-perl libmcs1
  libmime-lite-perl libmime-tools-perl libmime-types-perl
  libmono-zeroconf1.0-cil libmowgli1 libnet-google-perl libnet-ssleay-perl
  libnotify0.4-cil libossp-uuid-perl libossp-uuid15 libphonon4
  libresid-builder0c2a libsdl-console libsdl-gfx1.2-4 libsdl-ttf2.0-0
  libsidplay2 libsoap-lite-perl libsoprano4 libstdc++5 libstreamanalyzer0
  libstreams0 libstrigiqtdbusclient0 libtaglib2.0-cil libtidy-0.99-0 libtre4
  libuser-perl libwww-search-perl libxul-common libxul0d nullmailer
  openjdk-6-jre-headless openjdk-6-jre-lib phonon phonon-backend-gstreamer
  podsleuth poster python-cddb python-chardet python-feedparser python-fpconst
  python-gamin python-gnome2-extras python-gpod python-mutagen python-ogg
  python-pyogg python-pyvorbis python-soappy python-utidylib rhino
  soprano-daemon streamripper texlive-bibtex-extra texlive-font-utils
  texlive-fonts-extra texlive-fonts-extra-doc ttf-bengali-fonts
  ttf-kannada-fonts ttf-oriya-fonts ttf-telugu-fonts tzdata-java
"

---

### Post by OrangeCrate on 2009-03-22
For future reference, here's a tutorial on cleaning up junk files...

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by Rocket2DMn on 2009-03-22
I think you should be OK to remove that stuff, all that python, java, and kde4 stuff is probably taking up most of that space.  I would only be concerned if you are using KDE4 as your desktop environment - did you install it at one point then decide against using it?  Or perhaps install some KDE programs in Gnome that you later uninstalled?

---

### Post by Vulgor Schnecke on 2009-03-22
cool, nice link there thx @ orangecrate.
hmm kde, well im using ubuntu, the only kde based programs im using atm are amarok and osmo personal organizer, other than that ive installed and removed amarok quite a few times, wasnt satisfied at first but now ive settled with it. ok, think im gonna run that command.. :-), if my system gets killed, oh well, its still gonna take me much less time to reinstall ubuntu than to newly set up windows...
thx for the help

---

### Post by OrangeCrate on 2009-03-22
> **Vulgor Schnecke said:**
> cool, nice link there thx @ orangecrate.
hmm kde, well im using ubuntu, the only kde based programs im using atm are amarok and osmo personal organizer, other than that ive installed and removed amarok quite a few times, wasnt satisfied at first but now ive settled with it. ok, think im gonna run that command.. :-), if my system gets killed, oh well, its still gonna take me much less time to reinstall ubuntu than to newly set up windows...
**thx for the help**

:)

---

