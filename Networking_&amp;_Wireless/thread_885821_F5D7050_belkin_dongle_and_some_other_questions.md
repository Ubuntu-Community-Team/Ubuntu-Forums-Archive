---
title: "F5D7050 belkin dongle and some other questions"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by Napster69 on 2008-08-10
well me any my mate are doing cisco ccna when we go back to collage next month and to keep us from bordem we have both put a text file on our desktops and gave each other our ips and said each other can do anything as long as it dosent cause any damage to get a the file. hes a gentoo and windows user and we have both agreed to keep the windows box on constantly with firewalls and whatever other protection we want to use. and ive thaught of a good way into the windows machine witch is cracking his wireless sniffing for pws and trying to get into remote registry service as the local admin with the passwords i find. this sounds like a good idea to me since he will be looking for direct attempts from the internet. this is where you come in ive never used wireless on ubuntu and from what i understand you have to get your dongle into monitor mode and then you can use crackers/sniffers etc. i have the F5D7050 belkin wireless usb dongle how do i set about getting this to work under ubuntu ? i heared a while back there were some hacked drivers to let it go into monitor mode. but i cant find them. also id like to know if i set it to wlan0 when i get it working can i still have a wired internet connection on this pc to internet and the wireless just for going onto his network.

kind regards 

Andy

also sorry for the block of text :(

---

### Post by james_vanb on 2008-08-10
I've read that the Belkin USB works out of the box for some people using Ubuntu Hardy.  I've always had to use ndiswrapper both in Gutsy and Hardy.  Process is as follows:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands:

```
sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb

```

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

```
sudo gedit /etc/modprobe.d/blacklist
```

add "blacklist rt2500usb" and "blacklist rt73usb" (Without the quotes) to end of list, save and close.

REBOOT

Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin". Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following (If the .inf file you copied is not the rt73, replace as appropriate below) :

```
sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf
```

Insert the wireless adapter.

Now issue the following commands:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows (If you are using Xubuntu, replace gedit with mousepad):

```
sudo gedit /etc/modules
```

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

```
sudo ndiswrapper -m
```

Reboot

Shouldn't effect your wired connection.

---

### Post by Napster69 on 2008-08-10
ty for help only problem is i cant find drivers from the cd since the cd is lost  :(

---

### Post by Napster69 on 2008-08-10
i have driver installed on windows mount on this pc ill copy over from tehre i thin kthere the same :) im off to bed now ill let you know how i go on tmoorw.

---

### Post by james_vanb on 2008-08-10
You need to copy the .sys and .cat as well, if there is one.

---

