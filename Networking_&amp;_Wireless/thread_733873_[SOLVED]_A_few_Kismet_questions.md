---
title: "[SOLVED] A few Kismet questions"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by Sceiron on 2008-03-24
Hi,

I have kismet running on my Lenovo T61, intel wireless card, iwl 4965 driver/chipset or whatever it is
But some questions:
1. when i use kismet  my internetconnection is going down, is this normal because kismet is using my wireless card? so i cant brows etc when kismet is running?

2. I trying to read the packages downloaded by kismet. I belive they are downloaded and logged in
/var/log/kismet/Kismet-March-24-2008.dump   is this correct?

3. How/with what app do i open this kind of file with?   (.dump)

---

### Post by Junglizer on 2008-03-24
1) Kismet will put your card into RFMon mode which will prevent you from connecting to a specific network as you are then passively recieving info from all sources. I have explained it a bit more throughly in the following thread link: [http://ubuntuforums.org/showthread.php?p=4552934#post4552934]("http://ubuntuforums.org/showthread.php?p=4552934#post4552934")

2) The dump file should be in the directory that Kismet was started in, unless otherwise specificed in the configs.

3) You should be able to open the .dump files with WireShark or something similar, and if you are trying to crack something specific, the Aircrack-ng suite.

---

### Post by Sceiron on 2008-03-24
Thanks dude. Just what i needed !

---

