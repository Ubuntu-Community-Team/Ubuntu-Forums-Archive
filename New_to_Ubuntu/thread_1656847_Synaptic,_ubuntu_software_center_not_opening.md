---
title: "Synaptic, ubuntu software center not opening"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by abybaddi on 2010-12-31
When I tried open ubuntu software center nothing showed up.
Clicking on Synaptic Showed the following error message.

Then I tried the terminal:
> 
abybaddi009@linuxmint ~ $ synaptic

(synaptic:2410): libglade-WARNING **: could not look up stock id '_Read Markings...'

(synaptic:2410): libglade-WARNING **: could not look up stock id '_Save Markings'

(synaptic:2410): libglade-WARNING **: could not look up stock id 'Save Markings _As...'

(synaptic:2410): libglade-WARNING **: could not look up stock id '_Quit'

(synaptic:2410): libglade-WARNING **: could not look up stock id '_Undo'

(synaptic:2410): libglade-WARNING **: could not look up stock id '_Redo'

(synaptic:2410): libglade-WARNING **: could not look up stock id '_Search...'

(synaptic:2410): libglade-WARNING **: could not look up stock id '_Reload Package Information'

(synaptic:2410): libglade-WARNING **: could not look up stock id '_Add CD-ROM...'

(synaptic:2410): libglade-WARNING **: could not look up stock id '_Mark All Upgrades...'

(synaptic:2410): libglade-WARNING **: could not look up stock id 'A_pply Marked Changes'

(synaptic:2410): libglade-WARNING **: could not look up stock id 'U_nmark'

(synaptic:2410): libglade-WARNING **: could not look up stock id 'Mark for _Installation'

(synaptic:2410): libglade-WARNING **: could not look up stock id 'Mark for R_einstallation'

(synaptic:2410): libglade-WARNING **: could not look up stock id 'Mark for _Upgrade'

(synaptic:2410): libglade-WARNING **: could not look up stock id 'Mark for _Removal'

(synaptic:2410): libglade-WARNING **: could not look up stock id 'Mark for Co_mplete Removal'

(synaptic:2410): libglade-WARNING **: could not look up stock id '_Properties'

(synaptic:2410): libglade-WARNING **: could not look up stock id '_Filters'

(synaptic:2410): libglade-WARNING **: could not look up stock id '_Contents'

(synaptic:2410): libglade-WARNING **: could not look up stock id '_About'

(synaptic:2410): Gtk-CRITICAL **: gtk_text_buffer_set_text: assertion `text != NULL' failed



Any ideas what should be done??
Help is appreciated. Thanks in advance.

---

### Post by Scunnered on 2010-12-31
Is your system fully up to date?  I had problems when attempting to use synaptic which were resolved by ensuring that the system was updated.

Suggest you try 

sudo apt-get update

Having done that it may resolve this difficulty

---

### Post by RJ12 on 2010-12-31
To update your system (sudo apt-get update will only update the package information) you need to run

```
sudo apt-get upgrade
```

---

### Post by abybaddi on 2011-01-01
here's what I did

> 
abybaddi009@linuxmint ~ $ sudo apt-get upgrade
[sudo] password for abybaddi009: 
E: Type '&#65533;PNG' is not known on line 1 in source list /etc/apt/sources.list.d/local-repository.list
E: The list of sources could not be read.
abybaddi009@linuxmint ~ $ 



---

### Post by abybaddi on 2011-01-01
Happy New year to you all!!!

---

### Post by PatchesTheCaveman on 2011-01-01
That file is probably unnecessary.  It looks like a PNG graphics file.

Try running:
```
sudo mv /etc/apt/sources.list.d/local-repository.list /root
```

and then running
```
sudo apt-get update
``` again.

And happy new year to you too!

---

### Post by abybaddi on 2011-01-01
> **PatchesTheCaveman said:**
> That file is probably unnecessary.  It looks like a PNG graphics file.

Try running:
```
sudo mv /etc/apt/sources.list.d/local-repository.list /root
```

and then running
```
sudo apt-get update
``` again.

And happy new year to you too!
Works like a miracle!!! Thank you.:D

---

