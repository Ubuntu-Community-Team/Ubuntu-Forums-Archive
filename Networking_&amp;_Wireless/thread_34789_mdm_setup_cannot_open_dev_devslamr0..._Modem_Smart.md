---
title: "mdm setup: cannot open dev /dev/slamr0... Modem Smartlink on Kernel 2.6.10-5-386"
date: 2005-05-16
forum: Networking &amp; Wireless
---

### Post by Saul.Lima on 2005-05-16
I download the sl-modem-source, module-assistant and execute:
sudo apt-get install module-assistant
sudo module-assistant auto-install sl-modem
The installation proceed perfectly. After I execute
apt-get install sl-modem-daemon
And don't have any problem, but the modem don't run in kernel 2.6.10.-5-386. I execute the same steps on my old kernel (2.6.8-5-386) and the modem works sucefully. I execute, as a root in kernel 2.6.10-5-386, the comand "slmodemd --country=BRAZIL /dev/slamr0 and the modem driver returns this error:
mdm setup: cannot open dev /dev/slamr0: no such device
error: cannot setup device /dev/slamr0

What is the problem betweem the smartlink modem driver and kernel 2.6.10? How I can to solve this?

P.S.-Sorry for my bad english.....

---

