---
title: "WN311T cant get to work, but im close"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by Greenducky on 2008-03-03
y problem is that i have ndiswrapper and i also have wine.

so i loaded wine up and then ran the exec file on my netgear cd. which allowed me to steal the .inf and .sys files and place them in a new directory. i then you used the ndis wrapper util configuration tool and loaded the .inf driver and it said loaded and present.

then i opened a terminal and typed

sudo ndiswrapper -l

output shows:

netmw14x : driver installed
device ( 11AB:2A08 ) present

yet when i type (iwconfig)
the out put says

iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

I am confused the terminal says its there and ndiswrapper says it loaded
the file correctly. so whats the deal ????


Netgear WN311T. OS Ubuntu 7.10

---

### Post by {BzF}~JOKesTER on 2008-03-05
First Off Unplug Your USB Card.

Next Type: ndiswrapper -r (Whatever The Driver Name Is)

Now DON'T USE THE NETGEAR INSTALLER!!!

Instead Browse The CD To: 

>>Driver

And Copy The "XP Or WINXP" Folder To The Desktop - {You Must Copy The Entire Folder!!!}

Now:

In The Terminal:

Cd To The Folder You Just Copied.

Type:

ndiswrapper -i Drivername.inf

{Replace "Drivername" With The Name Of The .inf File In The Folder}

Now Type:

ndiswrapper -m

ndiswrapper -mi

ndiswrapper -ma

Now Plugin The Adapter.

And Now Type:

lsusb

Find Your Device In The List And Copy The 8 Symbol Code With The Colon {Example 0201:0a60}

Now Type:

ndiswrapper -a XXXX:XXXX DrivernameGoesHere

{Note: Replace The XXXX:XXXX With Your 8 Symbol Code From Before -INCLUDE THE COLON!!}
{Note: Replace "DrivernameGoesHere" With The Name Of The Driver You Installed - Don't Put .inf After This DriverName}

Type:

modprobe ndiswrapper

And See If The Light On The USb Card Blinks -{If There Is One}

Restart Your Computer.

Hope This Helps!!

:guitar:

---

### Post by at4germany on 2008-03-08
Hello,
i've the same problem as greenducky has. 
You describe the installation for the netgear WN121T card. That's an USB-Card, but the WN311T Card is an pci card, you can't unplug this card.
If you've another idea, please tell me.

---

### Post by {BzF}~JOKesTER on 2008-03-08
Sure - 

Just Don't Unplug The PCI Card...

And Replace The lsusb Command with

lspci

And Instead Of Just XXXX:XXXX

It's

XX:XX.X

That You Put In The Device Number:)

---

### Post by at4germany on 2008-03-08
okay, i've tried, but if i want do add the device nb: "00:0d.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a02 (" ., i get the message " '00:0D.0' is not a valid device ID".
Where's the problem?

---

### Post by {BzF}~JOKesTER on 2008-03-10
Try It Again...

Note: Just Copy And Paste The Entire Device Number From lsusb - It MUST Include The Colons And The Dot!!!!


Hope This Helps!!:)

---

### Post by at4germany on 2008-03-10
No not really. I tried to copy and paste this part with the dots!
Yesterday I tried this system with the WN121T card (USB!), but it didn't worked either. I looked with dmesg | grep ndiswrapper:   

[http://ubuntuusers.de/paste/73322/]("http://ubuntuusers.de/paste/73322/")

so, what's the problem?

---

