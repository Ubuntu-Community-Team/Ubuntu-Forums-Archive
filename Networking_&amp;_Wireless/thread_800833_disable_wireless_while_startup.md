---
title: "disable wireless while startup"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by tanyeun on 2008-05-20
hi, all ^_^
I installed gutsy on Lenovo X61
the wireless network will automatically turn on while startup
cause I'm not frequently use wireless
is there any way to turn it off 

thx

David

---

### Post by mhedges48 on 2008-07-13
cd /etc/network
sudo gedit interfaces

You should get something like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# auto eth0
#iface eth0 inet dhcp


I put a "#" in front of the auto eth0 and that disabled the wireless on my thinkpad from starting automatically at startup. To turn it on, just right click on the network icon...

---

### Post by nova47 on 2009-03-23
For some reason this is all I have in my interfaces file

auto lo
iface lo inet loopback

I've got two ethernet ports (both are intergral with the mobo) and one PCI wifi card.

My fix was a bit jerry-rigged but it worked:

1.) right click on the network button
2.) click on edit connections
3.) go to the wireless tab
4.) highlight the wifi network you don't want it to connect to
5.) click edit
6.) Uncheck the box that says connect automatically and now you won't connect to
    that network. It doesn't disable the wireless but it did the trick for me.

---

### Post by nlr on 2009-10-08
Hello,

I too was getting annoyed after a recent update (to jaunty on lenovo X61) by the wireless automatically enabling on startup; my LAN is much faster, and I believe it was causing problems with my connection. I came up with the same "jerry-rigged" fix that Nova47 has enumerated above. This worked for most of the wireless networks that Ubuntu was finding on startup and listing under "networks" in the panel.

However, one of the wireless networks in my building has some degree of protection - most of the selection options for this network were "grayed out" and I could not change them, including the "connect automatically" option. I ignored this network since I couldn't do anything to the settings for it, even on my own PC, and since I was never going to use it. However, now on startup I am asked for "authentication" for a wireless network as the panel is loading the internet stuff. Whether I click cancel, or the "x" button on the window, or do nothing, there's some kind of crash in that part of the startup and the panel does not finish loading. Some icons load before the internet icon. These however I cannot click. Some icons load after the internet one, and these don't appear. Right or left clicking the panel on the top or bottom produces no action. In other words, the panel is broken. However, I may access the applications on the panel (such as the terminal, firefox, etc), via shortcut keys and the terminal, and I may access anything on my regular desktop. The wired internet works fine (I am browsing on it now). If I try to shut down, I get the effective message "panel is still running" do you want to shut down anyway or cancel, etc.

I tried google and the forums to help me out, but no luck after lots of searching, so I finally joined the forum and thought I'd give asking for help directly a try. Any help is appreciated. Thanks.

---

### Post by tanyeun on 2009-12-16
I am not really sure what's your problem is
but I have a way to disable the wireless effectively
```
$ sudo iwconfig eth1 txpower off
```

---

### Post by francoise_peace on 2010-06-06
So how do you do this in Lucid Lynx 10.04 ?

---

### Post by ferriol on 2010-07-03
I found a possible solution on Lucid. This works for me, may be for you

[https://answers.launchpad.net/ubuntu/+source/network-manager/+question/72343](https://answers.launchpad.net/ubuntu/+source/network-manager/+question/72343)

---

### Post by NetJunky on 2010-08-21
> **ferriol said:**
> I found a possible solution on Lucid. This works for me, may be for you

[https://answers.launchpad.net/ubuntu/+source/network-manager/+question/72343](https://answers.launchpad.net/ubuntu/+source/network-manager/+question/72343)
Nope. Done that. Didn't help in my Ubuntu 10.04.

Any other suggestions?

---

