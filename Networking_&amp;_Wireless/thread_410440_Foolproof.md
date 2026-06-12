---
title: "Foolproof"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by itzpapalotl on 2007-04-15
Well, This is just a post to say that for those of you out there who are just plain fed-up with the configurigamarole of getting your wireless interfaces to work, but just plain have to have wireless. There is a solution, and it's absolutely bullet-proof.

This is CHEATING. It solves nothing except getting you on to a wireless network every time with no fuss no muss. It fails to address any problem, simply provides a solution. This solution is NOT likely to endorsed by the Ubuntu or Debian people, but if you are like me, and you just need a wireless connection NOW, with no fuss, here's the deal:

You will need:
A windows machine (Yeah.. I know... just Boot Beg or Borrow, you'll only need it for a few minutes, and only once)
A Wireless Ethernet Bridge. If you ask for one of these things by name, you'll probably get the same look you might expect to get if you ordered a plate of Squid at McDonald's, so ask for a "Wireless Gaming Adapter". I'm not going to endorse any particular product here, but I will say that I am using a D-LINK GamerLounge DGL-3420. 

What this is, is a device that you plug in to your normal 10/100/1000 Ethernet port, and in turn connects to a wireless network. Basically it's an external wireless client that has all of its own drivers and configuration built in. 
Get one, plug it in to the Windows box (you are going to need to use I.E. to configure. For whatever reason, Firefox won't play nice with most of these things) 
Set up your basic connection, which ususally involves putting the windows machine on a static IP in the same subnet as is the bridge. In the case of the D-LINK it was 192.168.0.XXX. connect to the default IP of the device. In my case 192.168.0.30, and then run whatever wizard is available, enter your SSID, and WEP or WPA information. Switch the Windows box back to DHCP,  Confirm that it is working. (visit your favorite non-cached website) and shut down the Windows box. You won't be needing it anymore.
Now, Fire up you Ubuntu Box, set your Ethernet to receive DHCP, plug in your bridge, and VIOLA! instant fool-proof wireless.

Pros: It works. Every time. No trouble

Cons: You are tethered to the nearest outlet: You are using proprietary devices and software, and you spent a few bucks getting it.

In the case of the D-LINK I used, If you are feeling frisky, and have a soldering iron and a bit of Know-how, you can relieve the first of these problems by soldering the hot and return legs of a standard USB cable to the power connector legs on the bridge. Both types of device operate at 5 volts DC, so now you can plug in the usb cable, and power the device from the 5vdc output that USB provides. Don't do this unless you have the right equipment, and a fair degree of knowledge about electronics. If you blow the soldering job, you have voided both your device, and it's warranty, but it does work of you get it right. 


Okay, so now you have reliable wireless under any OS that can handle Ethernet. 
Hope this helps the frustrated out there! ;)

---

### Post by chili555 on 2007-04-16
I used a Linksys WET11 wireless ethernet bridge for many years when wireless support in Linux was a great deal less than it is now. I was very happy with it on the corner of my desk as a quick and easy, and cheaper, actually, alternative to stringing CAT5 cable through the attic.

It now provides connectivity to our server which resides on a shelf in the garage.

I would hate to use a bridge in a mobile situation, even with 'power over ethernet', but in a fixed location, it can be a easy solution.

This Ubuntian approves of wireless ethernet bridges!

---

