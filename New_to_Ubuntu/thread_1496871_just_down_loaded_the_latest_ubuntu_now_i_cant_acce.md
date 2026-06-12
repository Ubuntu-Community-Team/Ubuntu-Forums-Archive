---
title: "just down loaded the latest ubuntu now i cant access the internet"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by blake7 on 2010-05-29
yea i downloaded the software from uppdate manager and all seemed fine for about 1 day. then it stoped working everthing else is fine
im on the same connection with my laptop and so no problems with connection

is there any thing i can do to get her up and running

i hope you can help cheers

---

### Post by Bölvaður on 2010-05-29
in grub when you boot up your computer, pick the older kernel that you used in the older version of ubuntu you used.

---

### Post by blake7 on 2010-05-29
cheers i give that a go aspa

have a good one

---

### Post by blake7 on 2010-05-29
which kernel  will it load up next time ???
the older one i have just selected or the stand one

cheers

---

### Post by anewguy on 2010-05-29
It will still boot whatever is your default (e.g, which is highlighted on the grub menu).

If you want to change that, we can walk you through changing the default and updating grub so it will boot a different selection by default.

If you wouldn't mind, also do the following and post the outputs back here:

lshw -C network

Maybe we can find a driver or other method to get it working in the new kernel.

Dave ;)

---

### Post by blake7 on 2010-05-29
i tryed a diffent one and it still did not work

help!!!

what can i try now

thank you for your responses

---

### Post by wojox on 2010-05-29
Have you gone into Hardware Drivers and looked for anything to be activated?

What does this command output:

```
lspci | grep -i net
```

---

### Post by blake7 on 2010-05-29
i have just done lshw -c.........

and it says network disabled

that does not sound right

what do you think 

i post the rest now

thank you

---

### Post by bildr on 2010-05-29
are they both laptops? wireless?

might they have gone into sleep or hibernate?

wireless drivers have long had problems resuming from sleep.

disconnect power cable, remove battery, and attempt to turn on
i know it sounds stupid, but it resets the confusion in the wireless chipset

in the future install rfkill and use that to cycle.

if it's wired check that network-manager is running, you could try killing and restarting the service.  disable and re-enable networking through the gnome widget and/or ifconfig

---

### Post by blake7 on 2010-05-29
lspci | grep -i net


00:10,0 ethernet conrtroller: realtek semiconducdutor co., ltd 
rtl-8139/8139c/8139 c+ (rev 10)

does that help

---

### Post by Nick_Jinn on 2010-05-29
Can you connect with a cable or just not wirelessly?

---

### Post by wojox on 2010-05-29
See if this does anything:

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

### Post by blake7 on 2010-05-29
lshw -C network


desc...:ethernet interface
prod...: rtl -8139/8139c/813
vendor...: realtek semicondutore
phys...:10
bus info...:pci@0000:0010.0
version.....:10
serial...:00;1e;2a;3a;fe;3a
width....; 32bits
clock....;33mzh


should i not just go back to the last version of ubuntu???

---

### Post by blake7 on 2010-05-29
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade


dont i need to be on hte internet to do this???

---

### Post by blake7 on 2010-05-29
yes i have done restart
cheers

---

### Post by blake7 on 2010-05-29
is there a command line to start the hardware up

thank you

---

### Post by blake7 on 2010-05-29
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

tryed all those and no luck

cheers

---

### Post by blake7 on 2010-05-29
should i reload the last version ???

this is just seemingly going no where

---

### Post by wojox on 2010-05-29
> **blake7 said:**
> sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

tryed all those and no luck

cheers

My bad I thought you could connect with an Ethernet cable but couldn't enable wireless.

---

### Post by bildr on 2010-05-29
ifconfig eth0 down
ifconfig eth0 up

chkconfig NetworkMonitor on
service NetworkMonitor restart

lsmod | grep net
modprobe -r "drivermodule"
modprobe "drivermodule"

---

### Post by anewguy on 2010-05-29
A lspci should show a module/driver name with the device, so please do:

lspci

copy the output and paste back here.

Also - is it a hard-wired connection you have a problem with or a wireless connection?

Your Realtek 8139 is a regular wired ethernet controller.

Dave ;)

---

