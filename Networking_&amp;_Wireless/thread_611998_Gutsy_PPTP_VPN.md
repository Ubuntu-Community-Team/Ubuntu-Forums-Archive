---
title: "Gutsy PPTP VPN"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by BagOBones on 2007-11-13
I have looked at no less than 6 guides for setting up VPNs and none of them seem to work or apply to Gutsy, Edgy and previous versions all seem to have differing methods for doing the same thing.

The main theme seems to be that a VPN option should magically show up if you have the right packages installed.

If I click on my network manager icon right now I only have one option"Manual Configuration..."
When I open that I get a window.

In that window I have two items:
Wired connection
Modem connection

On a CLEAN install of Gutsy what are the steps needed to setup a VPN client connection from a Gutsy Desktop to a windows PPTP VPN server?

---

### Post by CHFFriday on 2007-11-13
Do This:

Go to Applications -> Add& Remove Programs

After it loads Chick on INTERNET. Then at the top do a search for VPN. 

Install Connection Manager (PP Generic)

Reboot. 

Then when you click on the NM icon at the top of your screen you will see VPN Connection.

You can take it from there.

CHFFriday

---

### Post by BagOBones on 2007-11-13
I assume you meant VPN Connection Manager (PPP generic)

Steps:
1. Located VPN Connection Manager (PPP generic)
2. Installed VPN Connection Manager (PPP generic) No errors reported
3. Rebooted


Opened Connection manager.. No new options have appeared.

Left click still only displays "manual configuration"
Right click displays "enable networking" , "connection information" and "about"

I am not sure what is wrong or missing.. The steps you provided are the same I originally tried but with the same result.

I have also tried removing and reinstalling network manager with no change..

---

### Post by CHFFriday on 2007-11-13
Do This:

Go to System -> Administration -> Synaptic Package Manager

After it starts (you will have to enter your password) click on search. Type in PPTP.

Then check to see if Network-Manager-PPTP AND PPTP-Linux are installed. If not install them.

CHFFriday

---

### Post by BagOBones on 2007-11-13
I have it all installed, double, and triple checked.

The problem appears to be network manager it self as per bug #5364 I am using a static IP for my eht0 interface.
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/5364](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/5364)

So as a WHOLE it is a GUI limitation of network manager and Gutsy.

I have no desire to write a pile of routing scripts to work around this. If there is an alternate GUI app that will work with static IPs, great other wise I think I am hooped and need to wipe and reinstall Windows on this particular test computer as it is useless without VPN support.

In order to get Network Manager to display the VPN options you need to have "Enable roaming mode" set on the interface.. This clears any static IP values and the connection with it. The VPN options then appear but without the IP info there is no connection to VPN over.

---

### Post by CHFFriday on 2007-11-14
Look, give us some info on the type of machine you are using. I'm guessing it's a Laptop. What is the need for static IP? Your first post did not mention this.

I have Laptops out there using VPN from different Wireless hotspots. No problems. My question, if you moble way static IP?

CHFFriday

---

### Post by BagOBones on 2007-11-14
It is a test workstation sitting in my DMZ, the primary goal for the machine is to test connectivity from the outside world back into my network. As well as test outbound connections out side my internal filtering. This happens to include testing VPN connectivity.

There is NO DHCP running in this zone.


If you have all of the command line steps I would need to take to setup a VPN manually I might give it a shot, but I don't really have time to fiddle with this box much longer. Or if you can point me to a an early build of Network Manager 0.7 that might work.. That would help.

---

### Post by CHFFriday on 2007-11-14
Bones, I have just tested the VPN setup as you discribed. I now see what you have been up againest.

This is a bug as far as I'm concerned. I installed an update to NM and other network management stuff but it did not change.

Al of our Laptops are running in Roaming mode. There for no problems.

If I can get the VPN manager running from the command line, I will let you know.

Maybe some one can help with this.

CHFFriday

---

### Post by epiphani on 2007-11-16
I believe I am also experiencing this issue.

We have a wireless network that does not broadcast the SSID, so I have to set up the wireless manually.  Once connected, the wireless network drops us to a DMZ and we have limited access prior to connecting to a pptp vpn.  But I can't seem to figure out how to get the pptp configuration to work in this case.

So it sounds like I'm being hit with the same issue here.  If there is a workaround prior to getting a software fix for the network manager applet, t'would be appreciated.

---

### Post by CHFFriday on 2007-11-16
I heard that KVPNC is a good app. I have tried it at wotk but that is not a good test. I will try it a my lab.

You can get it Applacations-> Add and Remove->
Then go to Internet Search VPN
You will also need the PPTP Daemons.

CHFFriday

---

### Post by epiphani on 2007-11-19
I figured out my problem here:  when installing from scratch, as I was with gutsy, the file /etc/network/interfaces was configured to always search a specific wireless network - ie, the file contained:

auto lo
iface lo inet loopback
iface wlan0 inet dhcp
wireless-key <somekey>
wireless-essid <somessid>


The install media made this configuration.  After I removed the iface wlan0 and wireless- lines, I placed 'auto' there instead, and all the sudden my network manager applet was a totally different application - everything started working.  I was able to configure the network settings in ~/.gconf/system/networking/ using a collegue's settings as a template, and I got my config running.

It sounds like the network manager folks suffer from a lack of test cases.

---

### Post by CHFFriday on 2007-11-21
epephani,
Let me understand here: You are using a static IP address. Correct?

Also the interfaces file settings should change during every boot up. Correct?

CHFFriday

---

### Post by iansane on 2007-11-26
This whole thing is confusing to me.
Do I have to have one of the computers on the vpn acting as a vpn server or can two host at different locations have a basic link encryption vpn between them?  I found a howto on using openvpn. When I set it up it creates a bridge but I loose internet until I reboot. When I reboot, I have internet but the brige has dissapeared from my eth0 configuration. I set it up and loose internet again.

I just want my computer and my friends computer to think they are on the same network. I set up DMZ and a static IP on both ends. Just can't find how to set up vpn.

If anyone knows a good step by step howto for setting up a vpn in Gutsy, please post a link to it. Thanks for any one who can help.

---

### Post by iansane on 2007-11-28
I have installed PPTP, PPTP Linux, network-manager-pptp, and bcrelay. bcrelay installed along with pptp I think. Anyway, I now have vpn in the drop down from the network manager and I can create a vpn tunnel. My friend did the same thing and one time he connected to me, or so his computer said. I could not connect to him and after the one time, he could not connect to me again. Is there something we're missing? That's why I asked does there have to be an actual vpn server or can we just create a vpn between two computers? During the creation of the vpn tunnel we just left everything set on the default setting and entered the address and a name for the tunnel. It's a dyndns web address which gets routed through a DMZ. Should we use port forwarding instead of DMZ? Thanks.

---

