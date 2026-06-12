---
title: "How do I install an updated Nvidia driver"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by jbocean on 2010-10-26
Running 10.04 on an older Dell & hope to improve graphics performance.
I checked (System >> Admin >> Nvidia X-Server Settings) I have ...

GeForce4M MX 420 w/ the 96.43.17 driver.

I went to Nvidia website found there is an updated driver [ 96.43.18 ] for my graphics card which I downloaded & saved to my Downloads folder & haven't touched it.

How do I update the graphics driver for my graphics card  ...

Do I need to extract the updated driver anywhere?
Do I need to dis-able compiz first?
Do I need to dis-able/delete the current driver first?
How do I install the new driver?
Will I need to reboot?
What if I screw up - what do I need to do to recover?

Thanks!

---

### Post by fooman on 2010-10-26
the 96.43.18 version should be available if you have the restricted repositories enabled in synaptic.

open synaptic (system > administration > synaptic package manager), in the toolbar, click: settings > repositories

when the software sources box opens, click the *ubuntu software* tab and put a check next to all 4 choices (*main-universe-restricted-multiverse*).  click the *other software* tab,  and put a check next to the 2 *partner* choices.

close the software sources box, and you will see a message telling you that the repositories have changed and that they need to be updated...close that box, and then back in the synaptic toolbar, click* reload*.

that will update the newly added repositories....when it finishes reloading,  search for nvidia,  and you should find the newer version available.  just install it,  no need to uninstall anything or disable compiz.  you will have to logout or possibly restart to enable the driver after it installs. 

hope that helps.

---

