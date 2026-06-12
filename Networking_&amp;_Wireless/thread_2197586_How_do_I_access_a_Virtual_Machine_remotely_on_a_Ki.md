---
title: "How do I access a Virtual Machine remotely on a Kindle Fire or iPad?"
date: 2014-01-04
forum: Networking &amp; Wireless
---

### Post by EarlsFurniture on 2014-01-04
Yes, I know, this isn't entirely a *buntu issue, but perhaps someone here can point me in the right direction.

I presently am running Ubuntu 12.04 on a business machine, using VMware to serve up an XP VM for a pesky Windows only app. (our Inventory/Point of Sale system)

I'll likely be switching that over to VBox soon, but help with getting either to do what I'm looking for is appreciated.

The boss is headed out of town in a few weeks, and wants to be able to access inventory remotely using either a Kindle Fire HD or an iPad. (he has both)

My best guess was to use a VNC or RDP client to view the VM remotely. I presently have his VM set up on VNC now and I can access it from my own separate machine on the LAN.(for maintenance ease)

I don't want or think I need to install an additional VNC/RDP server either in the VM or on his Ubuntu box, as VMware (or Vbox) already is serving up that connection. (I could also serve the Ubuntu box itself, but he really only needs the XP VM)

I can't seem to find a simple RDP/VNC client for the Kindle (or iPad) where all I have to do is enter the IP address and port and connect. (like I can from other machines on the LAN)

Then there is the added issue of being behind router with a firewall. I'm expecting I'll have to change a setting on the router to be able to access his local machine remotely. (we have a static IP address for the LAN, so that's not an issue) I'm guessing something along the lines of a VPN connection is needed, but not sure what all is involved in setting that up, or if that's a jackhammer, when all I need is something simpler. Perhaps I just need to forward a port, or something.

Any help will be greatly appreciated. If I need to clarify anything or provide more info, just let me know.

note, I've already tried Splashtop on the Kindle, but it wanted to install a local streaming server on the Ubuntu machine (or in the VM) and the Kindle never could see the computer. I tried setting the IP address as I have it on my local VNC connection, but that didn't work either.

---

### Post by tomearp on 2014-01-04
Something like [Teamviewer]("http://www.teamviewer.com") installed on the XP virtual machine will work. Bear in mind that it is free for personal use, commercial users should really buy a licence.

Manual for teamviewer is [here]("http://www.teamviewer.com/en/res/pdf/TeamViewer9-Manual-RemoteControl-en.pdf"). You want to install it on the VM and set it up for unattented access (i.e. configure it with a permanent password, rather than a randomly-generated throwaway one), read page 65 of the PDF onwards, it's not difficult to configure.
Then you can install the [free iPad app]("https://itunes.apple.com/gb/app/teamviewer-remote-control/id692035811?mt=8"). To connect on the iPad you'll need the Teamviewer ID of the machine and the permanent password that you've configured, or you can create a free teamviewer account and add the VM to the account and it will appear in the computer list in the iPad app when you log in.

Connections are initiated through teamviewer's servers so firewalls and multi-NAT configurations are no problem, unless you have a particularly exotic network set up you won't have to do anything to make it work.

---

### Post by EarlsFurniture on 2014-04-04
FYI for anyone interested, I did end up going with Teamviewer because I was crunched for time, though that's not what I wanted to do. I'm still interested in finding a VNC/RDP client for tablets for future use.

---

### Post by tgalati4 on 2014-04-04
A longer term solution is to migrate the WinXP inventory system to a web-based, enterprise server.  Then any device with a browser and login-credentials could access the database.  Otherwise, I would write a cronjob to run once a day to capture the inventory data to a text file and send an email.  Presumably your boss (possibly "Earl") can get his email while out and about.

Check out openERP:  [https://bitnami.com/stacks](https://bitnami.com/stacks)

---

