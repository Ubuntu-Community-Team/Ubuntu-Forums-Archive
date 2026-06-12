---
title: "brother dcp330"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by bjhome on 2009-08-27
i have a brother dcp330c printer that seems to have installed on my computer but is storing the print information on the printer and wont print it.do i need to do something on my computer to fix this?

---

### Post by duanedesign on 2009-08-27
you can find drivers for your model here

[http://www.openprinting.org/show_printer.cgi?recnum=Brother-DCP-330](http://www.openprinting.org/show_printer.cgi?recnum=Brother-DCP-330)

there is some documentation here

[http://solutions.brother.com/linux/en_us/](http://solutions.brother.com/linux/en_us/)


I have never installed a printer in Ubuntu so I am afraid I can not be a ton of help. I hope the links get you going in the right direction.

---

### Post by bjhome on 2009-08-27
i tried to load the brother packages in synaptic and i am getting this message."the following packages have unresovable dependencies. make sure all required repositories are added and enabled.  brother-lpr-drivers-bh7: depends a2ps but is not going to be installed." Help me please. I am a beginner.

---

### Post by bjhome on 2009-08-27
i have found the list of dependencies and conflicts .how can i fix this?

---

### Post by plucky on 2009-08-27
> **bjhome said:**
> i have found the list of dependencies and conflicts .how can i fix this?

Use **Synaptic Package Manager** to install the drivers.Open Synaptic and search for **DCP-330C** and it will show "brother-cups-wrapper-bh7" and "brother-lpr-drivers-bh7", select both and apply.(This assumes you have the Ubuntu repositories ticked in software sources).


Then plug in and power on printer and then open **System > Administration > Printing** and select new printer.It should find your printer and get you to select the correct driver.


Good Luck

---

### Post by bjhome on 2009-08-27
Thanks a million plucky- Printer up and running.
Don't know how to close this thread, maybe you can help me with that.?

---

### Post by bjhome on 2009-08-27
Is it ok to leave the all the repositorys sticked in software sources?

---

### Post by duanedesign on 2009-09-27
In Software Sources under Ubuntu Software it is ok to leave Main, Universe, Restricted, and Multiverse checked (and Software Sources if you need source code)

The third party software tab. Without knowing what you might of added here I cant advise whether you should keep them checked or not. As long as you only add reputable well tested repositories you will be OK.

The Updates tab. I keep the following checked:
Important Security updates (jaunty-security)
Recommended updates (jaunty-updates)
(this one is optional, but i have never had any trouble with it)
Pre-released updates (jaunty-proposed)

Glad you got your printer going :)

---

