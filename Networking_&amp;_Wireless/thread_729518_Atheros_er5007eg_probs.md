---
title: "Atheros er5007eg probs"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by BETELGEUSE58 on 2008-03-19
I am trying to get the wireless card working on my acer 5315. It is an atheros ar5007eg. I've tried to follow the instructions in other posts, for both feisty and gutsy, but both have links to places that dont exist so i cannot get it to work.

Anyone know of how to get this working with links to places that work?

Thankyou.

---

### Post by azwar on 2008-03-20
Go to System -> Administration -> Restricted Driver Manager -> Disable Atheros Hardware Acces Layer (HAL)

Install build-essential. Then download the madwifi ticket for AR5007EG here [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

Then open terminal
cd /to madwifi folder you downloaded @ drag the downloaded folder to terminal

then type in terminal 
make

then type again
sudo make install

Then to load the driver on every boot-up, type again
sudo modprobe ath_pci

Then reboot your laptop

If still doesn't work try to switch-on wifi button on your laptop. Or using NDISWRAPPER driver

Good Luck!!!

---

