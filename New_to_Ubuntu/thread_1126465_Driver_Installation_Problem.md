---
title: "Driver Installation Problem"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by Azhtabak on 2009-04-15
Hi. As part of my attempts to fix my irritatingly slow internet, I had the idea of downloading the latest windows driver for it, and installing it via ndiswrapper. 

Happily, when I got to their website, (Reaktek 8010E) I found that there was a linux driver, which I apparently don't have installed. I downloaded that, and now have a problem:

The readme file in it told me to check if I had the previous driver - which I did - and then to remove it - which I did. However, I am unable to install the new one - I get 'error 1' or 'error 2' when I try, depending on whether I sudo it or not.

My internet is still working at the moment (that's what I'm posting this from) - however, I am slightly nervous about rebooting, as I think that will update the kernel and hence delete the driver, from what little I know about how it works?

Does anyone know why it might not be installing? I'm guessing I might have to reboot first, but I'll probably destroy my internet connection if I'm wrong :P

---

### Post by mbzn on 2009-04-15
try to reboot, chances are that it wont need the windows drivers after the kernel update.
give some detail on your hardware, what type of card your using etc.

---

### Post by Hospadar on 2009-04-15
Could you be more specific about what exactly you did to delete the driver, and what command gave you the error, and could you post the full content of the error?

Also have you checked the restricted driver manager for your wifi card?

System->Administration->Hardware Drivers

---

### Post by Azhtabak on 2009-04-15
I'm using a 'RTL8101E' I believe:
```
  *-network UNCLAIMED                           
       description: Ethernet controller         
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.                        
       physical id: 0                                                 
       bus info: pci@0000:02:00.0                                     
       version: 02                                                    
       width: 64 bits                                                 
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd cap_list
       configuration: latency=0

```

The previous driver I had - the one I uninstalled - was a linux one I believe that came with kubuntu jaunty. As far as I know, rebooting my laptop - and hence the kernel - will uninstall it, hence stopping me connecting, but I'm also guessing it might be the cause of the new one not installing (due to the old one not being fully removed)

The command I used to delete it were:

```

sudo lsmod | grep r8169

```

To check whether it was there - it gave me a response, where as it now does not.

I then used:
```

sudo rmmod r8169
[/code

to remove it. The wireless was working before - just slowly, slower than it had been on the windows that this laptop came with. It was also much more sporadic in its connection.

The readme then told me to use:
[code]
sudo make clean modules

```

Which gives me the error message:
```

azhtabak@azhtabak-laptop:~/Desktop/r8101-1.011.00$ sudo make clean modules
make -C src/ clean                                                        
make[1]: Entering directory `/home/azhtabak/Desktop/r8101-1.011.00/src'   
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order                                                                                      
make[1]: Leaving directory `/home/azhtabak/Desktop/r8101-1.011.00/src'                                 
make -C src/ modules                                                                                   
make[1]: Entering directory `/home/azhtabak/Desktop/r8101-1.011.00/src'                                
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/src modules                                      
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'                                 
scripts/Makefile.build:41: /src/Makefile: No such file or directory                                    
make[3]: *** No rule to make target `/src/Makefile'. Stop.                                             
make[2]: *** [_module_/src] Error 2                                                                    
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'                                  
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/azhtabak/Desktop/r8101-1.011.00/src'
make: *** [modules] Error 2

```

---

