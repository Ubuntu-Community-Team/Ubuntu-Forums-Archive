---
title: "WN311T Driver installation"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by Celebnen on 2007-12-06
Hi there.

I have never used Linux before, and am trying to install my Wireless adapter so i can use the net.

I read in the help file that i need to make some package, with the .ini file, which i have.

But where the readme says to make the package, it is not there.

Can someone help me to install the RANGEMAX NEXT WIRELESS-N PCI ADAPTER - WN311T
From Netgear?

As i am a n00b, please could you explain this step by step, where to go and what to click.

Thanks,
Savell

---

### Post by Celebnen on 2007-12-06
Does anyone know anything that can help?

---

### Post by malegria on 2007-12-11
Use ndiswrapper.

Install with Synaptic Package Manager ndisgtk.

I think the interface will be self-explanatory.  I think you use the driver from the CD.:lolflag:

---

### Post by Greenducky on 2008-03-03
Sorry I cant help you,

My problem is that i have ndiswrapper and i also have wine.

so i loaded wine up and then ran the exec file on my netgear cd. which allowed me to steal the .inf and .sys files and place them in a new directory. i then you used the ndis wrapper util configuration tool and loaded the .inf driver and it said loaded and present.

then i opened a terminal and typed

sudo ndiswrapper -l

output shows:

netmw14x : driver installed
device ( 11AB:2A08 ) present

yet when i type   (iwconfig) 
the out put says

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

I am confused the terminal says its there and ndiswrapper says it loaded 
the file correctly. so whats the deal ????


Netgear WN311T. OS Ubuntu 7.10

---

### Post by midnightracer on 2008-04-15
I am having this exact same problem. Terminal says the driver is there for the wn311t and that it is present, but then when you go to windows wireless drivers, it says that the device is not present. Doesn't make any sense. Did you ever figure this out? Can anyone help. I am using Hardy Heron beta now.

---

