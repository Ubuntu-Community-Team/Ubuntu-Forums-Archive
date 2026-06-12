---
title: "Keyring &amp; Network problems"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by ant1060 on 2006-10-21
Hi,
Have the following problem : went away to a hotel where I had to connect via a cable to the hotel Broadband service. When I came home, suddenly my wifi wouldn't work anymore. I no longer have the blue clockwise arrow when trying to log on to my home wifi network and the keyring is no longer asked for. Additionally although I CAN connect by fiddling around with the sttings, NM tells me "No network connection", and also in NETWORK TOOLS the network device is always on "loopback" howvever often I set it to ETH1 (my wireless setting).
What should I do?  Have been working for 5 hours on this with absolutely no success :(

---

### Post by ant1060 on 2006-10-22
Hi all : I am replying to myself as, after MANY hours of fiddling around, I finally found the answer to my problem. 
Here it is for anyone else who is experiencing NETWORK MANAGER ISSUES.

1. Go to /etc/network/interfaces (in gedit, for example) and place a # before EVERY SINGLE LINE EXCEPT THESE first two 
auto lo
iface lo inet loopback

(NB : Under no circumstances place the # before the quoted two lines or else your computer will not start and you'll then have to edit the file again from the command prompt which took me a very long time to figure out.)

2. Save
3. Make sure you have the Notification Area enabled in your top panel. (If not, right click on panel --> Add to Panel --> Utilities --> Notification Area)
4. Make sure you have Network Manager installed. (If not, install it through Synaptic or Applications --> Add Programmes)
5. Reboot
Then, with luck, you should see the NM applet now working.
If it's there but NOT working here's what I finally did (because I couldn't find the place to edit my Keyring to verify the access code to my wifi network).
6. I accessed my router, renamed my wifi to a different name, then rebooted my computer once more.  This obliged NM to ask me for a new code for the "new" wireless network and AT LAST all was working.
Good luck to everyone else.
:D

---

