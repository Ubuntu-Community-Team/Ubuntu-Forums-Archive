---
title: "BCM4318 does not work on lubuntu 17.10"
date: 2017-12-15
forum: Networking &amp; Wireless
---

### Post by luir on 2017-12-15
Hello comunity,

I feel a bit bad for writing here, because there might be the solution to my problem somewhere...
But i tried a lot and it doesnt work.
So: mit WiFi doesn't work on my old Dell Latitude D410.

Among other things i did [this]("https://ubuntuforums.org/showthread.php?t=370108").

And it came out [that]("http://paste.ubuntu.com/26187651/") with pastebin.

Because there there was the [0280] next to Broadcom, I followed [that]("https://ubuntuforums.org/showthread.php?t=2214110") instructions.

Now I am out of ideas and my wifi doesn't work. 

Somebody has any advice for me?

Greetings
Lui

---

### Post by Hadaka on 2017-12-15
Hi Please open a terminal  ctrl/alt/t then 
from a WORKING wired connection please COPY and PASTE
one line at a time...
```
sudo iw reg set DE
sudo sed -i 's/=.*/=DE/' /etc/default/crda
```
```
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
Remove wired connection,boot and test wireless
Thanks.

---

### Post by luir on 2017-12-15
Hi Hadaka,

thanks for helping!

Unfortunately it didn't work.

The first two lines gave nothing back.
then:
```
 echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist ssb
```

```
 sudo apt-get remove --purge bcmwl-kernel-sourcePaketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Paket »bcmwl-kernel-source« ist nicht installiert, wird also auch nicht entfernt.
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
  dkms fakeroot gcc gcc-7 libasan4 libatomic1 libc-dev-bin libc6-dev libcc1-0
  libcilkrts5 libfakeroot libgcc-7-dev libitm1 libmpx2 libubsan0
  linux-libc-dev manpages-dev
Verwenden Sie »sudo apt autoremove«, um sie zu entfernen.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert. 
```

..which is german and saying that nothing changed.

```
 sudo apt-get remove --purge bcmwl-kernel-sourcePaketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Paket »bcmwl-kernel-source« ist nicht installiert, wird also auch nicht entfernt.
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
  dkms fakeroot gcc gcc-7 libasan4 libatomic1 libc-dev-bin libc6-dev libcc1-0
  libcilkrts5 libfakeroot libgcc-7-dev libitm1 libmpx2 libubsan0
  linux-libc-dev manpages-dev
Verwenden Sie »sudo apt autoremove«, um sie zu entfernen.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
rubennase@rubennase:~$ sudo apt-get install firmware-b43-installerPaketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
firmware-b43-installer ist schon die neueste Version (1:019-3).
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
  dkms fakeroot gcc gcc-7 libasan4 libatomic1 libc-dev-bin libc6-dev libcc1-0
  libcilkrts5 libfakeroot libgcc-7-dev libitm1 libmpx2 libubsan0
  linux-libc-dev manpages-dev
Verwenden Sie »sudo apt autoremove«, um sie zu entfernen.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.


```

same thing - nothing changed.

And after the last code nothing came back.

Is there still hope ?

Lui

---

### Post by Hadaka on 2017-12-15
from a working wired connection please do..
```
sudo apt-get autoremove
```
then do..
```
sudo sed -i '/modprobe/ d' /etc/rc.local
```
Next..Go into bios and remove secure boot, this is preventing your
driver from loading.
then do..
```
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```

---

### Post by luir on 2017-12-16
YESS !

It worked! 
In my old BIOS there was no secure boot - i did some things back and forth though and it seems to be right :)

Thanks a lot, Hadaka!

:guitar:

lui

---

### Post by Hadaka on 2017-12-16
Glad you were able to resolve the fault.
Thank you for marking your thread Solved.

---

