---
title: "ndiswrapper for wi-fi"
date: 2005-09-04
forum: Networking &amp; Wireless
---

### Post by Steve Smith on 2005-09-04
I've got ndiswrapper 1.1 for my wif-fi drivers.  [On this page of the wiki](https://wiki.ubuntu.com/SetupNdiswrapperHowto) it says to type:

sed -e "s/misc/kernel\/drivers\/net\/ndiswrapper/g" debian/rules > debian/temp

But I get an error saying:
sed: -e expression #1, char 29: unknown option to 's'

I take it I could just edit the text file by hand if I knew what I'm supposed to be changing!  Can anyone shed any light on this for me please?  Thanks! :)

---

### Post by bin on 2005-09-04
Assuming stock 5.04 install:-

sudo apt-get install ndiswrapper-utils
sudo apt-get install wireless-tools

modprobe ndiswrapper

ndiswrapper -i xxxxx.inf (from your wireless card windows driver)

iwconfig wlan0 (may be ath0 if Atheros chipset).....

the rest depends on your wireless config - search the forum for bits that may relate to your card.

in light

bin

---

### Post by Steve Smith on 2005-09-04
Thanks, I'll give it a go tomorrow and let you know!  Sounds far more straight forward than what I was reading...

---

### Post by Steve Smith on 2005-09-05
Installing both packages was fine (I didn't realise Ubuntu came with a version of ndiswrapper).  But then modprobe ndiswrapper returned the following:

steve@steve1:~$ modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

I tried sudoing it, and tried it from a root propt, but all were the same.

:)

---

### Post by Steve Smith on 2005-09-08
Bumping after 3 days.

Could anyone shed any light on the "FATAL:..." error above, please?

**Edit:** I've found Linux drivers for my card, so I'm not looking for any  more help with ndiswrapper!

---

