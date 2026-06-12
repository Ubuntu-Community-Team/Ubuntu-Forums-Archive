---
title: "Help connecting to a Wireless Network"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by msmb on 2009-03-27
I need help connecting to a wireless network, please. I'm running Xubuntu 8.10 off my thumb-drive  I go through 'Network Connections', and configure my wireless connection(via built in wireless in the laptop). Xubuntu wont recognize the network.  no-where do i see a 'enable wireless network' button, and when I go through Applications->System, there is no button for setting up a network.  It will, however, connect to a wired network just fine, and other computers see the wireless just fine.
Thanks!

---

### Post by ronocdh on 2009-03-27
I myself only have experience with native installs (i.e. not run off of peripheral devices), but what I think is happening here is that you haven't set up drivers for whatever wireless hardware you're using.

Try the Wireless Networking forum we have here. There you can search for threads discussing your specific chipset. Try:```
sudo update-pciids
lspci
```
That should output your wireless hardware (you'll have to look through the output yourself till you find something resembling wireless).

---

