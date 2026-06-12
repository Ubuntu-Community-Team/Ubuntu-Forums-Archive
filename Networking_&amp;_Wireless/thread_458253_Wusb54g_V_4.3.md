---
title: "Wusb54g V 4.3"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by pneujet on 2007-05-29
Can someone give me a detailed method for installing a WUSB54G V 4.3 adapter on Ubuntu 7.04? I have spent many hours trying and have failed.

---

### Post by peter_k on 2007-06-29
> **pneujet said:**
> Can someone give me a detailed method for installing a WUSB54G V 4.3 adapter on Ubuntu 7.04? I have spent many hours trying and have failed.

pneujet:

Did you ever get this resolved?  I'm running into the same problem trying to install edubuntu.

---

### Post by kevdog on 2007-06-30
Can you post the results of the following (command line):

lsusb

Off the top of your head, you dont have the chipset of the device do you?

---

### Post by peter_k on 2007-07-02
FYI -

I managed to get this to work; evidently I was making things way too complex, which I do have a habit of doing from time to time. :eek:

I downloaded various distros, and the only ones to recognize the card were Kanotix and SimplyMepis 6.5.  I thought about it, and realized that this meant it wasn't the card, but the distros support for it, so I did what I should have done all along -- went into Windows, and wrote down the particulars of the connection - IP, subnet mask, gateway, dns.  I had realized that at no point had I been asked to enter these, so that should be the problem.  Therefore, by my admittedly potentially flawed logic, any distro could work...enter edubuntu.

After putting the edubuntu liveCD in, I went to Administration>Network.  The Wired connection was enabled, and the Wireless wasn't.  Both were roaming.  I tried entering the info in various places, but eventually settled on putting it under Wireless, with a Manual IP setup - I don't know my WPA password, so I didn't enable that; as it's a kids' PC, I'm not so concerned, but I think it might work if I figured out what the password was.  I selected the ESS id that was in the drop down box (a good sign, but it had been like that before as well) I also turned roaming OFF (you have to to get at the settings - DHCP might work here too, but I have a manual setup.  I then turned the wired connection OFF.  In the top right corner, the words Enable Networking have a check by them.  Wireless does not appear, but the connection does work, even after a reboot.  I now have a box that provides some nice apps, and my kids (11,7, and two 5 year olds) will be learning Linux (granted, mostly poking around in Gnome, but at least they'll be comfortable with it).

I honestly thought I'd be wrestling with ndiswrapper, but I didn't have to.  I guess edubuntu did see my card, and the error was mine for not inputting the info.  After the necessary reboot (that first update) I was anxious to see if I'd have to re-enter the info.  I didn't.  

Interestingly enough, I chose edubuntu for the educational apps, but none of them were installed - in fact they were removed during the install process; but that's another story, and nothing a few minutes in Synaptic didn't cure. :)

I also mention the above because in my view edubuntu is then ubuntu with different wallpaper and a different icon set, so the same process hould (theoretically) work for ubuntu as well.

---

