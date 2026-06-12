---
title: "accidentaly removed my network manager"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by mustard greens on 2009-06-21
I accidentaly removed my network manager instead of just reinstalling it.  

due to an intermitant ethernet network connectivity issue, I tried uninstaling the network manager, thinking I could just download it off the live CD.  I have not been able to retrieve it from the live CD, and cannot get back on the internet via hard drive install, but have had no problem connecting to the web via said CD.  

I have tried
 
sudo /etc/init.d/networking restart
and 
ifconfig
and
sudo ifup lo (lo is the name of a "local loopback" connection which shows my valid mac address and IP info)

but firefox cannot find the network

tried to copy and paste terminal output from a text doc on hard drive, but live CD wont allow me permission into my documents.  is there a way to access hardrive via live CD?  I can view folders but it wont let me open them.  doesnt offer me a chance to enter password. just says I dont have permission.

thank you

---

### Post by lswb on 2009-06-21
Try starting synaptic, then from the synaptic menu, select Settings/Repositories/third party software. Check the box for the cd, close the diaog, then try reinstalling NM.

---

### Post by mustard greens on 2009-06-21
so the cd select option for me is not under third party, but in the ubuntu software tab, should there be something under third party?  I have had the cd checked, and had to uncheck all other options to get it to stop trying to connect to the web when I reload repository options (mandatory).  finally, synaptic shows that Network-manager is not available from the live CD (even though it obviously installs when I boot from the CD).

---

### Post by faintscrawl on 2009-06-21
I erased my network manager yesterday, semi-accidentally. I had to download the .deb file onto a usb key using my wife's windows laptop, then put the key in my ubuntu machine and reinstall. I'm not entirely sure if it worked, though, because I'm having other issues too.

---

### Post by mustard greens on 2009-06-21
so I ran 

sudo dhclient eth0

and I got my network back!
 it was all just guess work from reviewing other threads.
next I will try to download network manager from the internet.
  I would consider this thread solved, but cant seem to find that option anymore.
thanks everyone.

---

### Post by mustard greens on 2009-06-21
I tried the usb trick, but I am so new that I have trouble understanding archiving, compiling, installing, etc.  I got an openable folder onto my desktop, but could not figure out how to run it.
 you might try the line of code I showed above, as it activated my down connection which allowed me to download the whole package, plus dependencies through synaptic via the internet.  
it could be the dependencies causing your hassle.

---

### Post by Cheesemill on 2009-06-21
Just to let people know, the Live CD doesn't have any installable .deb files on it, You need the Alternate Install CD for that.

---

### Post by faintscrawl on 2009-06-21
> **mustard greens said:**
> I tried the usb trick, but I am so new that I have trouble understanding archiving, compiling, installing, etc.  I got an openable folder onto my desktop, but could not figure out how to run it.
 you might try the line of code I showed above, as it activated my down connection which allowed me to download the whole package, plus dependencies through synaptic via the internet.  
it could be the dependencies causing your hassle.

When I right-click on the deb file, it asked me if I wanted to open it with GDebi Package Installer. Then it installed. But it sounds like you figured out the best method--synaptic.

I ended up getting on by using pppoeconf, but my network manager still doesn't work.

---

