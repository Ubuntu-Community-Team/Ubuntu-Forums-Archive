---
title: "USB Wlan0 NetGear wg111v2"
date: 2014-05-11
forum: Networking &amp; Wireless
---

### Post by acidviews on 2014-05-11
Hi guys this is kind of maybe a slight how too or a guide as i had one of the wort experiences over the last few days.
Anyways if this comes in hand for anyone or perhaps any idea for troubleshooting/whatever good luck.

When i first started, i was trying out mint and actualy i liked it a bit but oh well here i am now on ubuntu gnome 14 04
The dongle simply refused to work after following several guides, simptoms : very slow, bitspikes , d/c

After much trial and error, 
 
1st thing to try with the **wireless usb dongle netgear wg111v2 **
is to install some firmware 
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111)

Although this simply didnt solve my issues as i had hoped :( 
and ofcorse it took forever to get anything done

2nd thing was to disable ipv6  network > settings > ipv6 > ignore
didnt realy help at the moment but should help later anyway,

3rd was to excersize patience and install **synaptic and all the dependencies**
 either with this slow or by this link on another machine
[http://packages.ubuntu.com/trusty/synaptic](http://packages.ubuntu.com/trusty/synaptic)

4th using synaptic i marked the following packages for installation;

network-manager (reinstall)
ndiswrapper (all)
wicd (all)

at this stage there should be a few dependecies marked etc, to include these is a must .

In synaptic go to file > Generate package download script
and point it to your home folder and lable it something simple.

Get this list onto a computer that has the net i.e. copy paste to a windows or whatever.

5th on windows i ended up downloading something like **37 files**, this was realy painfull
and if anyone has a quicker way of doing this plz share. opening the script is easy with notepad or gedit.
but yea **painfull**, had to remove -c and wget from each item whatever that is?

Put them all in the same folder

6th
 back to ubuntu and install pkg 1 by 1 to make sure, i diddnt reinstall anything apart from network-manager.

Reboot

i had not touched wicd, or ndiswrapper but perhaps it was just reinstalling netowork-manager ? or it wanted a dependency maybe?
Finaly i got a stable working connection, so
i did my 1st trial with 

sudo apt-get install linux-headers

i seen all was well and so i thought i better share with others as this dongle is an out right neausence!
and if i forget i consider it to be like a memo for later.

---

