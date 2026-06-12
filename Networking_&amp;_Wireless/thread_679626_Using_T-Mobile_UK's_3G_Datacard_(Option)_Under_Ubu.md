---
title: "Using T-Mobile UK's 3G Datacard (Option) Under Ubuntu (2.6.22+)"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by kubuntuuser on 2008-01-27
The following how-to should work with a Globetrottor Fusion+ i.e. the card t-mobile use for web-n-walk 1.8 Meg 3g access.

To install the driver and use the datacard the following packages need to be installed
- build-essential
- kpp
- there may be more, but this is all I had to install.

You can install these using synaptic or apt-get.

Download the latest nozomi driver (provided by option - the manufacturers of the datacard) from :
[http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,118/]("http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,118/")

Extract the files to a working directory and edit nozomi.c. For the driver to compile correctly a couple of amendments to the source are required due to API changes with the kernel shipped with gutsy (2.6.22+)

**Replace the following calls**
```
- INIT_WORK(&dc->tty_flip_wq_struct, tty_flip_queue_function, dc);
- rval = pci_module_init(&nozomi_driver);
```
**with** 
```
- INIT_WORK(&dc->tty_flip_wq_struct, tty_flip_queue_function);
- rval = pci_register_driver(&nozomi_driver); 
```

Save the file.

On a terminal and as sudo run the following:

```

sudo mknod /dev/noz0 c 241 0; 
sudo mknod /dev/noz1 c 241 1; 
sudo mknod /dev/noz2 c 241 2; 
sudo mknod /dev/noz3 c 241 3;
```

All the pre-requistes for compilation should now have been completed.

In a terminal cd to the working directory where the nozomi.c resides and run the following
[B]sudo make
sudo make install[/B]

This should install the driver into the kernel. If you see the words "ERROR" anywhere you have done something wrong. Warnings should not affect operation.

Now follow the instructions at 
  [http://net42.co.uk/os/linux/tmobile_datacard.html](http://net42.co.uk/os/linux/tmobile_datacard.html) 
to set up KPPP and get your connection set up.

NOTE:
/dev/modem should be replaced with /dev/noz0. The reference to /dev/modem did not work for me.


Resources 
- [http://net42.co.uk/os/linux/tmobile_datacard.html](http://net42.co.uk/os/linux/tmobile_datacard.html)
- [http://net42.co.uk/os/linux/tmobile_datacard.html](http://net42.co.uk/os/linux/tmobile_datacard.html)

---

