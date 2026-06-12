---
title: "Setting up wireless on Xubuntu"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by pmshirey on 2007-01-17
I just installed Xubuntu:) . But i need to know how to configure wireless. How do i do it? I used to have ubuntu but i think there are different instructions for wireless on Xubuntu.

---

### Post by cihtog on 2007-01-24
If you had wireless working on ubuntu, then it should be the same setup for xubuntu. All of the ubuntu distributions are basically the same. The only difference is the installed packages. xubuntu is ubuntu lite and kubuntu is ubuntu heavy. I switched from ubuntu to xubuntu and followed the same steps in setting up my wireless for both distributions on the same machine.

ndiswrapper seems to work for just about anything so far that I have tried

1.) You need to add Universe to your list of sources in the Synaptic Package Manager.

2.) Install g++ 4.1 or higher from the package manager.

3.) Download the most up to date ndiswrapper package to your desktop. ( At this writing it was 1.34)

3.) Do some research on your machine and wireless device. There should be a list at the ndiswrapper website and other websites searchable through Google.

4.) My driver was not on the list but it works anyway. Copy the winXP or win2000 drivers to a folder on your desktop, so that you can try them both. The XP driver is usually the first choice to try, but in my case the 2000 driver was the only one that would work. The folders containing the driver files should have the; inf, sys, and firmware files in them as well.

5.) Now that you have all of the stuff that you need. Follow the ndiswrapper instructions located in the INSTALL file, until you get to the point of installing the windows driver. At this point you need to remove the obviously non-working driver that xubuntu installed. In my machine it was the ACX driver. In my case this driver was for a acx100 chipset, mine is in fact an acx110, totally different chip.

Post some details of your machine so that me or someone else can give you more detailed instructions. PC or laptop?, what brand are your components? Are you trying to setup wireless LAN or or a cellular Internet connection?

Installing wireless while running any ubuntu version is pretty easy as long as you follow the instructions, take notes, and do everything in the right order. I took notes on my install, the first time around took several hours, but I can set it up from scratch in about 5 minutes now, minus the time it takes the machine to install everything. The bonus is, that my card was not even supposed to work at all.! :)

---

### Post by ogomoe on 2007-01-27
Who is the manufacturer of your wireless, what model and version is it?

---

### Post by mshirey8 on 2007-01-31
This thread was started by my 11 year old son who is an avid ubuntu fan. We will be able to get it set up using ndiswrapper without too much trouble. Thanks for the replies!

---

