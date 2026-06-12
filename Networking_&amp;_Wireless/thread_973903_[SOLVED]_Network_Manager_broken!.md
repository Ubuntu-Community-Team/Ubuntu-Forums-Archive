---
title: "[SOLVED] Network Manager broken!"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by hornetster on 2008-11-07
Have tried to get a response to this before, but apparently nobody knows... :(  I have been trying to configure my network for  a fixed IP, but Network manager won't save my configuration. There is no "unlock" button, which I assume there should be, so I can reconfigure the network with elevated rights. I can reconfigure temporarily if I set a fixed IP and restart (/etc/init.d/NetworkManager restart), but after a reboot, is set back to normal. I would really appreciate some help with this....  or, how do I do it Manually. I assume I edit network/interfaces, but that is only the ip setup, not DNS or anything else necessary. And, how can I get a COMPLETE idea of the current network settings (dare I say it, like ipconfig /all in windows..)
Thanks.

---

### Post by kerpow on 2008-11-07
What version of Ubuntu you on?  The Network Manager has changed recently I think.

On my install of 8.04 if I click on the Network Manager icon in the system tray and click 'manual configuration...' there is an unlock button on the resulting window.  Not for you?

The equivilant of 'ipconfig' is 'ifconfig' and 'ifconfig -a' gives you many details.

To get default gateway type 'route' or 'route -n'.

---

### Post by hornetster on 2008-11-07
Thanks for the reply. I'm on 8.10, and, no I don't get an  unlock button... Think that may be the problem...?? Thanks for the other info!

John.

---

### Post by lesbianpenguin on 2008-11-07
i think using ifconfig ethX should fix your problem and dont forget to check your resolv.conf

---

### Post by rturner on 2008-11-07
> **hornetster said:**
> Thanks for the reply. I'm on 8.10, and, no I don't get an  unlock button... Think that may be the problem...?? Thanks for the other info!

John.

You have to uncheck System Setting in 8.10.  That will save your static ip.  I still have a nuisance where upon rebooting, my same network card has both the static ip and the assigned ip.  So far I'm just deleting the assigned ip in network manager, but it's a small nuisance.

---

### Post by Sergiu Bivol on 2008-11-07
hornetster, DO NOT try to configure your machine to use a static IP. 
There is no way to do this in Intrepid as long as NM 0.7 is present in your system.
And there is NO working solution, no matter what other users would say - they either do not use NM 0.7, either do not reboot their machines to check that their solution works. 

This is what I have done (and tested - it works):
1. # sudo aptitude purge network-manager network-manager-gnome
     This command will remove NM from the system.
2. Reboot the system (this is not an optional step!)
3. Configure the network from the terminal (ifconfig...)

Maybe somebody could point out a valid grafical frontend for configuring the network in Step 3?

---

### Post by hornetster on 2008-11-07
Thanks for the replies - will give them a go! But.... ifconfig etc is great for setting up an IP address, but what is the EASY way to manually config DNS?? I assume it is resolv.conf, but whenever I try to edit this, it either just doesn't work or gets overwritten... frustrating... Luckily(?) I have a windows box running in VMware, so it can still connect to the net.... :confused:
  John

Edit: Just found this post: [http://ubuntuforums.org/showthread.php?t=974382&highlight=workaround](http://ubuntuforums.org/showthread.php?t=974382&highlight=workaround) and this has 'partly' fixed the problem... at least gave me the info to resolve manually.
   John

---

