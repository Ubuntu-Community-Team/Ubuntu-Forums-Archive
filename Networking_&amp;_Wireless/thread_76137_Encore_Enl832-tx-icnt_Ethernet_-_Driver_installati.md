---
title: "Encore Enl832-tx-icnt Ethernet - Driver installation problem"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by tHub on 2005-10-14
Hi, I'm kinda new to linux and this is giving me a hard time
Running breezy and it didnt detect the card.
I'm getting this error [http://img406.imageshack.us/img406/8301/sc...eenshot17fc.png](http://img406.imageshack.us/img406/8301/screenshot17fc.png)
driver: [http://www.encore-usa.com/Drivers/ENL832-T...CNT_Drivers.zip](http://www.encore-usa.com/Drivers/ENL832-TX-ICNT_Drivers.zip)
sundance(one of the driver files thats giving me the error): [http://www.eazyshare.com/user_uploads/sund...ance_main.c.TXT](http://www.eazyshare.com/user_uploads/sundance_main.c.TXT)
*had to rename it to .TXT so i could upload*

---

### Post by tHub on 2005-10-15
Problem solved by a Fedora user.

---

### Post by LedStyle on 2005-10-21
HOw?

Im having the same problem! :(

---

### Post by tHub on 2005-11-13
nvm.

---

### Post by LedStyle on 2005-11-13
Thanks!!!

Here the driver: [www.tuxresources.org/files/sundance.tar.gz](www.tuxresources.org/files/sundance.tar.gz)

---

### Post by nothingworks on 2006-09-06
I have the same NIC and I cannot even run make (not installed I guess)

I tried
1) sudo apt-get install build-essential
   Returned: package build-essential is not available
2) sudo apt-get install make
   Returned: package make is not available

why isnt make included by default ? 
can someone attach the .o file so that I can use that directly?

---

### Post by abshnasko on 2006-10-04
I have the same card and a similar problem.... can someone help?

---

### Post by filloy on 2006-10-04
Ok, here the solution that worked for me.

The source is here: [http://www.ubuntu-es.org/index.php?q=node/15332](http://www.ubuntu-es.org/index.php?q=node/15332)
But its in spanish, so ill do my best...

1) Install kernel-source, kernel-headers, make and gcc (so you can compile)

2) Download the drivers from the web page ([www.encore-usa.com](www.encore-usa.com) i think)

3) Edit sundance_main.c:
  
  Line 1400:
  Change this:
```
pci_dma_sync_single
```
  To This"
```
pci_dma_sync_single_for_cpu
```

4) Comment line 1653 (just add // at the begening of the line)

5) Just follow the instructions in the included readme, and then your good to go :D


My problem comes when i reboot. The network is down, and i cant find a way to get it working again, the card is installed and...im just hating this network card.

If i find out how to make the network card work for ever, ill post it here...

Good luck !


// EDIT //

Ok, back to crappy network issues; i have a partial solution
Everytime I log in, i have to remove the module from the kernel and the load it again, so it would be something like this
```
sudo rmmod sundance
```
and then i add it again (please, cd to the directory in which the files are located)
```
sudo insmod ./sundance.ko
```

When i have a script that does this automatically, ill tell you, or if i have another solution...

NOTE: a little bird told me that i could just compile the kernel again, and it would include the module...ill try that and ill tell you whats up...

---

