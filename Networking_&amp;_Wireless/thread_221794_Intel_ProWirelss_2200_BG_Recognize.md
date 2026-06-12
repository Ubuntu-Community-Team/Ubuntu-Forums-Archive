---
title: "Intel ProWirelss 2200 BG Recognize"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by orgy on 2006-07-24
Hi,

Im having problems with my wireless card. I have a Toshiba Tecra A4 laptop and most of the time ubuntu doesnt recognize my wireless card until i reboot again. Is there a way to make ubuntu recognize it right away without rebooting?

---

### Post by chessforce on 2006-07-24
You can try the instructions at [https://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](https://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/) and put `modprobe ipw2200` in the script.

---

### Post by orgy on 2006-07-24
thx, ill try that

---

### Post by orgy on 2006-07-25
doesnt work :( . When i check the device manager i can see the wireless device, the driver is loaded and everything, the thing is, i cant see the eth1 until i reboot, weird.

---

### Post by chessforce on 2006-07-26
Try adding `ifconfig eth1 up` to the start-up script.

---

### Post by Gtaylor on 2006-07-29
I'm running a Tecra A4 as well, see my Tecra A4 wiki page under "Restoring USB/Network" for instructions on fixing this.

[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaTecraA4](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaTecraA4)

---

