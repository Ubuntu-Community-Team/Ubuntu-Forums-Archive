---
title: "Zyxel G-202"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by Okami on 2007-05-23
Hello
I have a problem as usual =)
I have installed ubuntu 7.04 in my mothers computer and I cannot get the zyxel g-202 wireless usb to work. The zyxel g-202 is in the list of cards that are supported with ndiswrapper. I have installed the driver with ndsiwrapper and it seems to work:

ndiswrapper -l
wlanuzg : driver installed
        device (0586:3410) present

Wireless network appear in the network-manager after I wrote

sudo modprobe ndiswrapper
sudo ndiswrapper -m

But it does not work, not with roaming-mode either. Also every time I reboot wireless network disappear from the list and appear again if I write sudo modprobe ndiswrapper... I need help with this too because I cannot tell my mother to write it every time she starts the computer.

In my own computer I have a wireless belkin card and I got that one to work without problem using ndiswrapper.

I hope someone can help me.
Thanks in advance.

Edit: It works now! Sorry for bothering. Once the first problem was solved, the second problem disappeared and wireless appear in the list after reboot.

---

### Post by Kurtson on 2007-06-17
did you manage to get it to work?
I'm sitting here with the same problem.
Ubuntu doesn't recognize the g-202 as a networkdevice at all....

---

### Post by KVroom on 2007-06-21
I have the same problem :( Has anyone found a solution??

---

### Post by Ayuthia on 2007-06-21
If your network device is not being recognized, you will need to install something like ndiswrapper.  Here is a link for some instructions:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I will admit that I have never used ndisgtk so I am not for sure what it does.  I took a quick glance at the link above and it did not seem to use it.

You will also need to get the drivers to use for ndiswrapper.  Here is the link to ndiswrapper where they have a recommended set of drivers for various wireless products:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/)

You will need to search that page for the link for your driver.  Create a folder called 'drivers' in your home directory.  Uncompress the file you downloaded and place them in the drivers folder.  Once you complete this, you should be ready to do everything that is listed in the instructions on the first link.

---

### Post by dandydagenius on 2007-07-20
have a look at this [http://yoten.blogspot.com/2007/07/zyxel-zyair-g-202-in-linux-step-by-step.html]("http://yoten.blogspot.com/2007/07/zyxel-zyair-g-202-in-linux-step-by-step.html") !

---

