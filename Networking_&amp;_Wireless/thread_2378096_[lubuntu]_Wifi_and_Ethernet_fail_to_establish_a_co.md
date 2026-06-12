---
title: "[lubuntu] Wifi and Ethernet fail to establish a connection on fresh install"
date: 2017-11-20
forum: Networking &amp; Wireless
---

### Post by ainsleo on 2017-11-20
I zeroed out a disk that previously had linux mint 18.2 working with wifi and ethernet.

I then did a fresh install of lubuntu 17.10. The live disk can connect to wifi just fine, but for some reason ethernet no longer works. 
When I restart and boot into the fresh install, wifi works fine (ethernet still broken).
However once I restart (sudo service network-manager restart or just restart the computer or just go to screensaver (and lock screen) ), wifi breaks too. It attempts to connect but continuously fails (for both ethernet and wifi).
This happens irregardless of me doing an update (sudo apt update; sudo apt upgrade, and also dist-upgrade)

I have even less success on lubuntu 16.04.03 and linux mint 18.3, linux mint 18.2, and linux mint 18.1, which all fail to connect to ethernet and simply lack a wireless option (options to create a new bridge, etc are present though).

The computer is an Optiplex 780 with a N300 Wireless N Nano USB adapter. It supports 64 bit (all attempts used 64 bit isos). Ethernet had worked out of the box previously, and wifi as soon as I bought the adapter (and I think install a driver)
Possibly relevant, computer doesn't recognise the iso when I use unetbootin, but works fine with dd.
In hindsight the zeroing was 100% unnecessary since my home drive was encrypted.

Oh, also output of pastebinit: [http://paste.ubuntu.com/26003734/](http://paste.ubuntu.com/26003734/)

---

### Post by praseodym on 2017-11-20
There is a bug in the network-manager applet:
```

echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

### Post by ainsleo on 2017-11-20
Thanks for the help.
Unfortunately this doesn't seem to work.
On my fresh install which loss connection after I locked out of lubuntu, when I turned it back on and followed your command, Wifi was back but not ethernet. I then updated the computer (apt update; apt upgrade). On restart, neither wifi nor ethernet were working. 
I am unsure if Wifi was back before I followed the command but repeating it after reboot then rebooting did not help.

Edit: I just reinstalled Lubuntu 17.10 and copying and pasting the commands also failed to work.
Edit: Okay, I just turned on the computer on again, and wifi is working again. I restart it, wifi fails to connect.
Edit: I believe wifi works when I shut down the computer and turn it back on, but breaks when I restart it or do sudo service network-manager restart

Edit: Alright, since no one knows a solution and this is on the second page, I'm just editing this, hopefully it doesn't pull the thread to the front page. I couldn't find a solution to ethernet or wifi, the computer is now binned (in the proper way) so I can't do any more testing.

---

