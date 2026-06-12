---
title: "pairing handset with bluetooth on Kubuntu 8.10 howto"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by gabor78 on 2008-11-20
Hi!
I have installed Kubuntu 8.10 Intrepid Ibex on my HP Compaq 6720s notebook, and started to experiment with the built in bluetooth. I wanted to connect my Nokia E51 handset with the notebook, but to time I did not manage to. I saw in the release notes of Ubuntu 8.10, that bluetooth does not work with KDE because something with bluez is not compatible with the Intrepid kernel (they will fix it in an upcoming update, if I understood well...). However, the graphical interface may not work, but I believe, that pairing a bluetooth device should not be a problem, since all the necessary packages came with the new distribution. So to cut it short: I tried to connect my phone with the notebook with gnokii (I set the proper MAC address, connection type, port, etc.), but when I give a "gnokii identify" command, the phone asks for a PIN. I could not find out what should be this PIN, the usual (0000, 1234, etc.) don't work. Neither could I find any useful explanation on how I could set my notebook's bluetooth PIN. When I issue a "hcitool scan", or "hcitool browse" command, these work, they find my phone and list the available services, but when I use "hcitool cc MAC" nothing happens (prompt comes back), but when I try to use any other commands afterwards, the answer is "not connected".

So, could anyone please provide a step-by-step "howto" about howti pair a mobile handset with a computer with KUbuntu 8.10 on it using only commands in a terminal? 

FYI: on KUbuntu 8.10 there is NO hcid.conf file, I tried to use a /etc/blietooth/pin file, but It also didn't work.

Thanks in advance!

---

### Post by puppywhacker on 2008-11-20
Hi,

I think you are looking for the hciattach and rfcomm commands, below is a list of my favorite commands. Hope that helps you

(rfcomm for creating virtual com-ports, you might not need that if use obex instead)

```

vi /etc/bluetooth/hcid.conf
vi /etc/bluetooth/rfcomm.conf
hciconfig hci0
hcitool scan
l2ping 00:0F:DE:2F:1F:A1
sdptool browser
sdptool search DUN
hcitool cc 00:0F:DE:2F:1F:A1
hciattach -b 00:0F:DE:2F:1F:A1
rfcomm connect rfcomm0 00:0F:DE:2F:1F:A1 4
rfcomm bind rfcomm0 00:0F:DE:2F:1F:A1 4
rfcomm release rfcomm0 00:0F:DE:2F:1F:A1 4
rfcomm -a

```

---

