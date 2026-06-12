---
title: "Ubuntu 11.04 Printer problems"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by alexandrutamasan on 2011-04-29
Hi
Just upgraded to Ubuntu 11.04 and already a big problem.
My network printers stop responding. I printed a document over to a windows shared printer and all was fine. But after trying to print a second document to the same printer it froze up on me. My printer job status says that the job is been processing but with no result. Trying a different printer on the network all seems to work fine. I've tried reinstalling the problematic printer (Samsung SCX-4521F) but with no effect.
Please help.

---

### Post by nvjopsddhapnv on 2011-05-04
I am also having kind of similar problem. Recently I have upgraded OS to Ubuntu 11.04, after that I am not able to print using network printer (samsung-CLP620ND); although it is printing well through windows-7 platform running as a virtual machine on Ubuntu 11.04.
Any solution?

---

### Post by sadaruwan12 on 2011-05-04
Same issue with my gestetner printer I tried every thing before coming to the forum but no response.

What happens is that the print job gets submitted to the spooler service in the windows but gets deleted with out giving a print out I tried to install the PPD as well but same results every time.

Can some one help with this matter.

---

### Post by Markie_one on 2011-05-09
Hi I've had the same issue with printing since upgrading to 11.04, the printer (HP laserjet 1020 connected to my desktop via USB) is found ok the job will be sent to the printer but after a couple of min's the job dissappears from the print queue and no printing has occured!

 I have now managed to sort the problem today hope this works with a similar solution for your printers. I opened up the HPLIP imaging and printing toolbox and selected 'download firmware' from the 'actions' tab.

When I retried to print test page the printer now works fine. 

Not sure why this has happened printer worked just fine on ub'u10.10

yours 

Newbie

---

### Post by reswob on 2011-05-10
WOW!  That worked!!!

Thank You!

@Markie_one I would grant you another bean of ubuntu if I could!

---

### Post by alexandrutamasan on 2011-05-17
> **Markie_one said:**
> Hi I've had the same issue with printing since upgrading to 11.04, the printer (HP laserjet 1020 connected to my desktop via USB) is found ok the job will be sent to the printer but after a couple of min's the job dissappears from the print queue and no printing has occured!

 I have now managed to sort the problem today hope this works with a similar solution for your printers. I opened up the HPLIP imaging and printing toolbox and selected 'download firmware' from the 'actions' tab.

When I retried to print test page the printer now works fine. 

Not sure why this has happened printer worked just fine on ub'u10.10

yours 

Newbie

Hi there

Sorry for my late reply but I was away. I've solved my problem by making a fresh install of Ubuntu 11.04 and everything works fine. Why there was a problem in printing after an upgrade to 11.04 and on a fresh install there isn't any is beyond me.

---

### Post by zac evans on 2011-05-21
> **Markie_one said:**
> Hi I've had the same issue with printing since upgrading to 11.04, the printer (HP laserjet 1020 connected to my desktop via USB) is found ok the job will be sent to the printer but after a couple of min's the job dissappears from the print queue and no printing has occured!

 I have now managed to sort the problem today hope this works with a similar solution for your printers. I opened up the HPLIP imaging and printing toolbox and selected 'download firmware' from the 'actions' tab.

When I retried to print test page the printer now works fine. 

Not sure why this has happened printer worked just fine on ub'u10.10

yours 

Newbie

Ya thanks, that worked perfect. It's strange because my printer was already working fine! Then it simply ran out of paper in the middle of a job, and it was just completely unresponsive after that! It seems like it decided suddenly right then out of the blue that it was not going to print again until I updated the firmware. Haha beats me, I'm new to this. At least it worked, cheers.

---

### Post by fixtrot on 2011-06-27
Hi markie_one, sounds like you know what you're doing, unfortunately I don't. WHERE do I find this "HPLIP imaging and printing toolbox" so that I can select "actions" then "download firmware" ? Please help I am lost!

---

### Post by dargaud on 2011-06-27
I have the [same problem since 11.04]("http://ubuntuforums.org/showthread.php?t=1768181"), and then again after the [latest CUPS upgrade]("http://ubuntuforums.org/showthread.php?t=1790220"), but since my printer is an Epson your solution won't do any good.

---

### Post by daveosociologist on 2011-07-12
You will need to make sure hplip is installed (it probably is):

sudo apt-get -s install hplip

You will need to then install hplip-gui:

sudo apt-get install hplip-gui

You will then simply enter the command "hp-toolbox" and follow Markie_one's instructions.

---

