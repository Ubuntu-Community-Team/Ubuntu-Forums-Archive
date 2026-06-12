---
title: "Solution to Many Wireless Problems"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by gilf on 2007-11-04
If you are having problems connecting to a wireless network with NetworkManager try this:

1.) ***Boot from a LiveCD of the version of Ubuntu that you use*** (this works for Kubuntu, too). Note: You should boot from the LiveCD to eliminate any problems you may have caused by altering settings inadvertently in the network manager in a hard drive installation. This is easy to do.

2.) Click on the Networkmanager icon in the taskbar (upper right of screen in Ubuntu, lower right in Kubuntu). In Ubuntu, it should look like a small black monitor(square) with a red spot on it.

3.) After clicking on that icon,  a panel should open up showing a list of available wireless networks. These networks are displayed by name (essid) in a line with an orange horizontal bar showing relative signal strength. ***Click on the network's orange bar  line that you would like to connect to.*** If the network requires a password, a password dialog will open up and you should fill in the password to connect. (Note: **be sure to select the right type for your router's encryption method**  WPA type, WEP-128 bit, WEP-64 bit, passphrase or hex, etc). 

After you enter that password, you may be asked if you want to add the password to your keyring (Ubuntu) or Kwallet (Kubuntu). It's a good idea to do that, because it makes auto-connecting in the future easier.

With the password or passphrase entered for the wireless encryption, you should see the network icon become two small circulating dots. This indicates the password is being authenticated and a connection attempt is being made. If authentication occurs correctly the icon will turn to a blue 4 column vertical bargraph (for WPA connections, at least), and you are connected.

If you do not see any orange horizontal bar network lines when you first open network manager, there are two possibilities:

a.) There are no networks of sufficient signal strength in your area (if at home, your wifi router may be turned off). Solution: move to an area where there are networks, or turn on your router.

b.) Your network wireless card is not working with your ubuntu system. In this case you will have to delve into the requirements for your wireless card -- drivers, etc. this is covered elsewhere in wikis and documentation online.

Note: if you do see network lines and orange bar graphs when opening NetworkManager from LiveCD, it is very likely that you do have proper card drivers installed (because they are properly seeing networks and communicating to your computer), and you probably should not try to troubleshoot card drivers.

Note: if you see two **lines with the same ESSID**, Network Manager may not behave properly when trying to connect to one of them (see [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/129908](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/129908) ). 

4.) If you are able to successfully connect to a network by clicking on the particular network line you want in LiveCD mode, but you are unable to see those same networks from an installed hard drive version of Ubuntu, the most likely cause of the problem is an altered file called /etc/network/interfaces

To solve this:

a.) if you are using version 7.10 check the contents of the file against the following.

> auto lo
iface lo inet loopback

If your file doesn't look like this, you can save a backup, edit it and try it with the new contents (see editing instructions below)

b.) if the 7.10 version doesn't work, or you are using 7.04, try this file  (file contributed by user elabranche) :

> auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto ath0                                                                    
#iface ath0 inet dhcp

If the file doesn't look like either version above, "save as" a version of your old file with a .bak extension, so you can restore it if you need to, edit the original file  and change it to one of the versions above, (copy and paste the above in place of what is there). (**new note**, *see my post below about the **ath0** device name -- yours may vary*)


Then reboot. The NetworkManager should now behave as the CD version did.
[B]
How to edit the interfaces file:[/B]
> In a terminal window, type

**gksudo gedit /etc/network/interfaces**

The gksudo part means that you are entering the program with root (superuser) priveleges. You need those privileges to edit and save a file in the system area of your Ubuntu installation.

Gedit is a graphical editor program.

The slash ahead of the etc means that etc is located in your root directory (/) which is higher in the directory tree than you are when you open the terminal (you are in your personal home directory).

When you first open gedit, please save a backup of your /etc/network/interfaces file with a file extension (like interfaces.bak) so you can restore it if you mess up the edited file.

Then perform your edits and save them as /etc/network/interfaces.


5.) If for some reason this does not solve your NetworkManager problems, you may need to uninstall and re-install NetworkManager (I did because mine had gotten corrupted in a power outtage during a save).

Note that if you uninstall it, you may not be able to connect to the internet to re-install it, depending on what other network software you have available -- or your skills in connecting via the console. Or whether a wired connection is also available to you.

I solved the disconnect problem at home by temporaraily setting my router to unencrypted and no WPA, and typing the following into the console of my ubuntu machine:

sudo ath0 essid *your network's name here*
sudo ath0 channel *your network's channel number here*
sudo dhclient ath(0)

(Note: Substitute wlan0 for ath0, above, if your wireless card doesn't use Atheros chips -- as mine does).

I don't know if the channel is necessary -- but it resolved faster for me. Likewise use dhclient only if your router is set up for DHCP assignment.t.

If you want info on your network's name (router name or essid) use the following command

sudo iwlist ath0 scanning

6.) After you are connected you can reinstall Networkmanager using Adept or any other package manager you normally use. Don't forget to re-set your router to the encryption method and passwords you normally use after you have downloaded and re-installed your network manager.


Notes:

Many of the problems occur because people do not realize that the way to connect is by clicking a bar-graph network line when first opening the Networkmanager icon. Clicking the signal graph display is a non-intuitive way of adding a password.. They try other options in the drop down preferences list to try to connect and/or add WPA passwords etc. -- sometimes by turning off roaming, and adding entries manually. Then they try to save this new configuration for loading when Ubuntu starts up. The effect of this change is to alter the etc/network/interfaces file so that auto-scanning of networks is now disabled. The program now tries to open only the connection they specified manually -- no other networks are visible, and often the one they specified was incorrectly set up or they have moved their location and it is no longer available. Restoring the interfaces file as above removes the saved manual entry, and auto scanning is restored.

People also often assume that because they see their preferred network in the drop down list, but aren't yet connected, that they have problems with their wifi network card drivers. So they attempt to add ndiswrapper drivers, etc.This can make things worse.

Most of these user problems are NOT due to driver problems, but a simple misunderstanding of how to use the program to connect to a wireless netwok.

---

### Post by BombDiggity on 2007-11-28
Holy Crizap!  I've been looking for a fix all night thank you so much, it worked perfectly!

---

### Post by gilf on 2007-12-13
You're welcome.

I'd like to expand the above a little -- in the network/interfaces file given above,  the line:

auto ath0
#iface ath0 inet dhcp

applies mainly to wireless cards (like mine) that use the Atheros chipset. 

If your card uses a different chipset, a LiveCD install interfaces file may use a different device name for the wireless card than "ath0" -- if so, just substitute your own card's device name for the "ath0" above. (I've since seen wifi0 and some others).

If you don't know what it is, you should be able to see the correct device name in /etc/network/interfaces file of a LiveCD session. Basically you're trying to duplicate that "fresh" install network/interfaces file in your installed system. 

The really important thing is to make sure the "auto" parameter is specified, and that you then try to logon using the method of clicking on the bargraph line in network manager, rather than trying to enter network setup and password entries manually.

As far as I know the above procedure is the only way to restore "automatic" connections to network manager.

---

### Post by Lostincyberspace on 2007-12-13
This is really good of you to do gilf, thank you for all those that will need the help.

---

### Post by ubutufan on 2007-12-13
Gilf this is a great work.
Indeed the interfaces file messes up the connections, especially the wireless.
A few weeks ago having problems to connect wirelessly, I changed to wicd. Beautiful program. I was able to connect to wireless and or wired. But...
When I tried connecting to my home's wireless it was not possible. The problem lied in the interfaces file. I had to do what you beautifully described and everything was up and running again.
In short your remedy works for network manager and wicd as well.

---

### Post by lkplnx on 2007-12-13
Well It worked for me. After working for a solid week to get my wireless to work, I followed your suggestion and it worked.

I guess the question will be after I turn the computer off then on tomorrow, will it still connect, but tonight I'm happy!

Thanks for the help!

---

### Post by gilf on 2007-12-13
You're welcome,

and please let us know if it doesn't work tomorrow. I doubt it can change without the user actually making a manual change. But if it does, we will figure out why.

The critical things needed to make Network Manager work well for most people are quite simple, and I hope the developers will notice this thread.

They are:

1.) Provide a network connection button for people to push that is obvious and intuitive. The present network icon in the top right corner of the panel is interpreted by many people as a STATUS icon, [I]not a means of connecting to a network.
[/I]
2.) Pressing the button presents the user with a list of found and available networks. Next to each of these should be a button which clearly and obviously states "Click to connect to (essid) ". Again, many people interpret the present bar graph as a STATUS display, *not a clickable way into the network.*

3.) Provide a clear and detailed help documentation. (I'd be willing to write this ). It should especially explain the way WPA and WEP passwords are entered (through the connection dialog). And how the automatic feature of the program is designed to work

4.) Provide a button to restore default automatic Network Manager operation without requiring manual editing of the /etc/network/interfaces file. This is particularly important when users inadvertently change their manual configurations, save them and enable them during boot. At present, such an action locks users out of restoring automatic operation.

5.) Provide a feature which reports whether a wireless card is recognized and operational, or whether drivers are absent or inoperable.  If users are reassured that their cards are recognized, they will not try to alter drivers unnecessarily, as is frequently happening now, as a stab-in-the-dark to get connectivity. 

Likewise if the program reports a problem with a card driver, users will not try to unnecessarily change manual program settings, but can concentrate on obtaining and installing proper card drivers..

Please note that in almost all of the problems addressed by the changes above, theoverall issue with network manager is not programmatic, but simple user misunderstanding of the operation of the program interface.

Users tend to approach the program with an expectation of entering a profile (including WPA or WEP keys before attempting to connect. Network Manager inverts this order and requires an attempt at connection before asking for keys. The means of sending commands to connect to the program are not intuitive, and manual changes are not easily reversible. Lack of documentation prevents recovery from these problems.

---

### Post by Tyche on 2007-12-14
THANK YOU!! THANK YOU!!! THANK YOU!!!!

And that still feels like insufficient thanks.  Your instructions just did, in about 10 minutes, what it's taken me 2 days to realize that I didn't know how to do, despite numerous printed instructions from the net.

My wife has a computer with a LinkSys WMP54GS wireless card (Broadcom 4318 chip).  She has had WindowsXP on it since she got it, and recently got disgusted enough to allow me to install Ubuntu 7.10 (Gutsy Gibbon) as a dual boot.  Aside from having to wipe the first installation (Not your fault, it was mine.  I messed up too much for your instructions to be effective with that installation), and re-install, completing the connection using your instructions took about 10 minutes.  Right now, the machine is ON THE NET, downloading about 146 updates through Synaptic.  And I feel like crowing.

Thank you so much for your help, and your very clear and detailed instructions

---

### Post by gilf on 2007-12-14
You're welcome.

---

### Post by Lostincyberspace on 2007-12-15
Keep up the good work.

---

### Post by Lorac1949 on 2007-12-16
> **gilf said:**
>  <<snip>>

4.) If you are able to successfully connect to a network by clicking on the particular network line you want in LiveCD mode, but you are unable to see those same networks from an installed hard drive version of ubuntu, the most likely cause of the problem is an altered file called /etc/network/interfaces

To solve this (thanks to user elabranche!), check the contents of the file against the following. The file SHOULD read this way on a fresh CD install:

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto ath0                                                                    
#iface ath0 inet dhcp

If the file doesn't look like this, "save as" a version of your old file with a .bak extension, so you can restore it if you need to, edit the original file  and change it to the above, or copy and paste the above in place of what is there. (**new note**, *see my post below about the **ath0** device name -- yours may vary*)

I'm a newbie to Ubuntu and need to ask how you edit the "interfaces" file.  I opened the file and typed in the above changes.  However, I got the error message:

"Could not save the file /etc/network/interfaces.  You do not have the permissions necessary to save the file.  Please check that you typed the location correctly and try again."

If I can't edit the file in Text Edit mode, can I edit it as sudo in terminal?  What do I need to do?

I also have 2 "interfaces" files.  One is "interfaces" and the other, larger file is "interfaces.orig"  Which one do I edit?

---

### Post by DocForbin on 2007-12-16
> **Lorac1949 said:**
> I'm a newbie to Ubuntu and need to ask how you edit the "interfaces" file.  I opened the file and typed in the above changes.  However, I got the error message:

"Could not save the file /etc/network/interfaces.  You do not have the permissions necessary to save the file.  Please check that you typed the location correctly and try again."

If I can't edit the file in Text Edit mode, can I edit it as sudo in terminal?  What do I need to do?

I also have 2 "interfaces" files.  One is "interfaces" and the other, larger file is "interfaces.orig"  Which one do I edit?

If you want a graphical editor use sudo gedit etc/network/interfaces

The file is just 'interfaces' with no extension.

---

### Post by gilf on 2007-12-16
> If you want a graphical editor use sudo gedit [COLOR="Red"]etc[/COLOR]/network/interfaces

**WRONG**

lorac1949 

Don't forget the slash before /etc.

I use gksudo instead of sudo, thus:

**gksudo gedit /etc/network/interfaces**

In either case the --sudo part means that you are entering the program with root (superuser) priveleges. You need those priveleges to edit and save a file in the system area of your Ubuntu installation.

Gedit is an editor program. 

The slash ahead of the etc means that etc is located in the root directory (/) which is higher in the directory tree than you are when you open the terminal (you are in your home directory).

When you first open gedit, please save a backup of your /etc/network/interfaces file with a file extension (like interfaces**.bak**) so you can restore it if you mess up the edited file.

Then perform your edits and save them as /etc/network/interfaces .

---

### Post by Lorac1949 on 2007-12-16
> **DocForbin said:**
> If you want a graphical editor use sudo gedit etc/network/interfaces

The file is just 'interfaces' with no extension.

This didn't work.  When I entered the sudo command in Terminal a new window opened in gedit.  It was blank.  I pasted in the information from your original post and tried to save the file.  Here's the gedit error message:

Could not save file home/[name]/etc/network/interfaces.  Unexpected error: file not found.

I went back to Terminal.  Here's what I entered and here's the error message:

[name]@[name]l-laptop:~$ sudo gedit etc/network/interfaces

** (gedit:8274): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

The file DOES exist.  I can see it and its contents when I go to Places, Computer, File System, etc/network/interfaces

Waz up?

---

### Post by gilf on 2007-12-16
you need the slash before the etc:

/etc

please see my post immediately before your last one

---

### Post by Lorac1949 on 2007-12-16
> **gilf said:**
> you need the slash before the etc:

/etc

Got it.  I successfully created the *.bak file and a new interfaces file.  However, upon rebooting I've lost not only the wireless bars visible in Network Manager, but my wireless connection as well.  This post is being sent via the Windows side of my laptop (via wireless, BTW).  Go figure.

Since I can't use either cable or wireless in Ubuntu, what should be my next step?  Talk about learning patience.  I've been at this off and on for a couple weeks now.

---

### Post by gilf on 2007-12-16
Boot from the live CD.

You should have network connectivity there.

You can also revert to your saved interfaces file.

If you want to do it using gedit again,

gksudo gedit /etc/network/interfaces

then save it as /etc/network/interfaces/bad   (so we can look at it for errors)

then open  /etc/network/interfaces/bak

save it as  /etc/network/interfaces

then reboot

---

### Post by gilf on 2007-12-16
Please paste here the contents of the original file and the interfaces.bad file

---

### Post by Lorac1949 on 2007-12-16
gilf - Thanks for your time and patience.  I'm rebooting and headed back to Ubuntu.  Will follow your instructions and touch base when I can.

---

### Post by Lorac1949 on 2007-12-16
> **gilf said:**
> Please paste here the contents of the original file and the interfaces.bad file

Here is interfaces:

auto lo
iface lo inet loopback

Here is interfaces.bad:

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto ath0
#iface ath0 inet dhcp

As a bonus, here is interfaces.orig (the interesting thing here is that 3SOV1 is NOT the network; it was renamed wifi when I had Windows wireless issues):

auto lo
iface lo inet loopback


iface eth1 inet dhcp
wpa-psk df103ee13088149967ef9a2eb9070d4f565e35078ede2aaa94735bfa270a2d52
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid 3S0V1

auto eth1

I'm going to log off for dinner now.  I'll check back later.

---

### Post by gilf on 2007-12-16
I have a lot of questions,

but the first one is, can you connect via a LiveCD session by clicking on the network icon in the top right of the screen, and then click on the bar graph line for your network named "wifi". It should then ask you for a WPA password.

Does that happen?

---

### Post by Lorac1949 on 2007-12-16
> **gilf said:**
> I have a lot of questions,

but the first one is, can you connect via a LiveCD session by clicking on the network icon in the top right of the screen, and then click on the bar graph line for your network named "wifi". It should then ask you for a WPA password.

Does that happen?

No.  When I booted from the CD, the wifi light on my laptop didn't come on.  It usually comes on when I turn the computer on; however, it remained off.  The Network Manager icon only showed the cable connection.

---

### Post by gilf on 2007-12-16
That was going to be my next question -- you are running both a wireless and a wired connection right now?

---

### Post by Lorac1949 on 2007-12-16
> **gilf said:**
> That was going to be my next question -- you are running both a wireless and a wired connection right now?

Correct.  I'm using the cable on Ubuntu (what I'm running now).  If I reboot and choose Windows, I'm on the wireless.

---

### Post by gilf on 2007-12-16
I'm assuming you have two network cards present when you are trying to boot Ubuntu. If the cable is also connected, Ubuntu is going to choose the cable interface before the wireless.

Did you remove the cable when you booted into LiveCD mode? If not, would you try that now and try to connect to the network by clicking the little icon in the top right corner of the screen, and selecting the bar graph line with your network name on it (wifi)?

---

### Post by Lorac1949 on 2007-12-16
> **gilf said:**
> I'm assuming you have two network cards present when you are trying to boot Ubuntu. If the cable is also connected, Ubuntu is going to choose the cable interface before the wireless.

Did you remove the cable when you booted into LiveCD mode? If not, would you try that now and try to connect to the network by clicking the little icon in the top right corner of the screen, and selecting the bar graph line with your network name on it (wifi)?

Will do.  I'm trying that now.  I'll let you know what happens when I connect again.

---

### Post by Lorac1949 on 2007-12-16
Here's the run down.  I'm back on Ubuntu via the cable.

**Cold boot from CD with the cable detached:**

The wifi light on the laptop was **OFF**

Saw 2 error messages briefly as Ubuntu went through system checks.  What I could write down before it blinked off the screen was "bcm43xx microcodes not available . . . failed"

When I clicked on the Network Manager icon "Wired Network" was grayed out; no Wireless Networks were present

After I shut down the CD boot and came up via the HD boot, the cable was still disconnected

I brought up Windows and as it started (before login screen) the wifi light came **ON;** I restarted and went into Ubuntu and the light remained **ON**

When I clicked on the Network Manager icon "Wired Network" was grayed out; however, my networks and others were there.

I tried to connect to my network, but it didn't connect.

---

### Post by gilf on 2007-12-16
Okay, then the problem is probably that you need a driver for the broadcom 43xx chips for your wireless card. That's what the liveCD seems to need. If you haven't installed these, see the forum posts on the broadcom drivers -- I believe there's a sticky

Now since you say you've worked on this problem for a week, it's possible you installed these already, and a LiveCD naturally ignores these. Is that ptrue?

---

### Post by Lorac1949 on 2007-12-16
> **gilf said:**
> Okay, then the problem is probably that you need a driver for the broadcom 43xx chips for your wireless card. That's what the liveCD seems to need. If you haven't installed these, see the forum posts on the broadcom drivers -- I believe there's a sticky

Now since you say you've worked on this problem for a week, it's possible you installed these already, and a LiveCD naturally ignores these. Is that ptrue?

Yup.  I've followed the guidelines of a couple of the Broadcom bcm43xx posts - here and at the Dell Linux Forum.  For a long time I couldn't see the networks.  What seems to be the problem is sending, not seeing.  I enter the passphrase and the system keeps asking for it - like the router never receives it.

At this point, I'm ready to buy an Ubuntu compatible wireless card and be done with this.  But, that brings up another question.  Is there a list of wireless cards?

---

### Post by Tyche on 2007-12-16
> **Lorac1949 said:**
> Yup.  I've followed the guidelines of a couple of the Broadcom bcm43xx posts - here and at the Dell Linux Forum.  For a long time I couldn't see the networks.  What seems to be the problem is sending, not seeing.  I enter the passphrase and the system keeps asking for it - like the router never receives it.

At this point, I'm ready to buy an Ubuntu compatible wireless card and be done with this.  But, that brings up another question.  Is there a list of wireless cards?

I ran into this problem myself.  I ended up just reinstalling, to clean up the mess I made.  Then first think, installed the BCM43xx-fwcutter_006-3_i386.deb and went to System -> Administration -> Restricted Drivers Manager and installed the wl_apstk-3.130.20.0.o driver that I had on a CD.  Then rebooted and went to the network manager.  Worked like a charm.

---

### Post by gilf on 2007-12-17
I'd like to try one more thing if you have installed those drivers...... if you're willing?

---

### Post by gilf on 2007-12-17
You mentioned that you had changed your router essid to wifi, did you also change your wpa password at that time?

---

### Post by Lorac1949 on 2007-12-17
> **Tyche said:**
> I ran into this problem myself.  I ended up just reinstalling, to clean up the mess I made.  Then first think, installed the BCM43xx-fwcutter_006-3_i386.deb and went to System -> Administration -> Restricted Drivers Manager and installed the wl_apstk-3.130.20.0.o driver that I had on a CD.  Then rebooted and went to the network manager.  Worked like a charm.

Thanks for the tip.  A friend of mine had to reinstall, too, before his wireless worked.

With a reinstall, I suppose I would have to fix the other things that didn't work (sound, OpenOffice, etc.) all over again.  What about files?  I've done backups of documents, photos and music with Simple Backup Config.  Would Simple Backup Restore put them back?  What about bookmarks in Firefox?  Passwords in KeePassX?

---

### Post by Lorac1949 on 2007-12-17
> **gilf said:**
> You mentioned that you had changed your router essid to wifi, did you also change your wpa password at that time?

No.

---

### Post by Lorac1949 on 2007-12-17
> **gilf said:**
> I'd like to try one more thing if you have installed those drivers...... if you're willing?

Sure.  I'm gonna hit the hay soon.  Shoot.

---

### Post by gilf on 2007-12-17
from installed system, unplugged cable tryt interfaces file as follows:

auto lo
iface lo inet loopback


iface eth1 inet dhcp
wpa-psk df103ee13088149967ef9a2eb9070d4f565e35078ede2aaa94 735bfa270a2d52
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid [COLOR="Red"]wifi[/COLOR]

auto eth1


Note: make a backup first and aalso check that I have the proper case for "wifi" lower case or caps or whatever

---

### Post by Lorac1949 on 2007-12-17
> **gilf said:**
> from installed system, unplugged cable tryt interfaces file as follows:

auto lo
iface lo inet loopback


iface eth1 inet dhcp
wpa-psk df103ee13088149967ef9a2eb9070d4f565e35078ede2aaa94 735bfa270a2d52
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid [COLOR="Red"]wifi[/COLOR]

auto eth1


Note: make a backup first and aalso check that I have the proper case for "wifi" lower case or caps or whatever

Made the *.bak and created a new inferfaces.orig file.  Rebooted without the cable and the networks showed up.  However, after entering passphrase, still no connection.  I'm back on cable again to send this.

If you think of anything else, let me know.  I'm signing off for tonight, but will check back tomorrow.

---

### Post by gilf on 2007-12-17
I think there's a conflict between the hard coded wpa info and the auto section.

I don't see the reason for the hard-coded section, you should just be able to enter the wpa in the dialog,

so let's try:



auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

---

### Post by gilf on 2007-12-17
Also when you say you are seeing the networks but "no connection," do you mean that the icon on the top right of the screen still has an x in it, or do you see an icon with two little black screens superimposed (meaning connected)?

If by no connection you mean you can't pull up pages in Firefox,  it's possible that the problem is in Firefox's settings for your internet connection. In other words we may have the other stuff (driver, interfaces, network manager) correct but you aren't "connecting" simply because Firefox isn't configured for your setup.

In that case try:

Open Firefox, click on Edit at the top of the screen, select Preferences, pick the Advanced tab at the top of the window, select the Network tab, click on Settings, try first "direct connection to the internet". If that doesn't work, try "auto detect proxy settings". If that doesn't work, be sure to return Firefox to its original setting.

Edit:

On second thought, that can't be the problem, since Firefox works via cable --- unless your cable and wireless networks are set up very differently. Tough to know what's there without seeing a physical setup......


.

---

### Post by Lorac1949 on 2007-12-17
> **gilf said:**
> I think there's a conflict between the hard coded wpa info and the auto section.

I don't see the reason for the hard-coded section, you should just be able to enter the wpa in the dialog,

so let's try:



auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

Should I make the changes to "interfaces" or "interfaces.orig" [the one I changed last night]?

---

### Post by Lorac1949 on 2007-12-17
> **gilf said:**
> Also when you say you are seeing the networks but "no connection," do you mean that the icon on the top right of the screen still has an x in it, or do you see an icon with two little black screens superimposed (meaning connected)?

Sorry.  I was a bit out of it last night. :???:  What I should have written is that when I clicked on "wifi" and it asked me for my passpharse the following happened:  1] I entered the passphrase and clicked the button to connect to the network, 2] the Network Manager icon changed to the 2 dots with the swirl, 3] this continued for some time, 4] the system asked for the passphrase again and 5] at that point I closed the dialog box and plugged the cable in.

> **gilf said:**
> On second thought, that can't be the problem, since Firefox works via cable --- unless your cable and wireless networks are set up very differently. Tough to know what's there without seeing a physical setup......

Nope.  I believe the cable and wireless are the same.  The cable plugs into the wireless router.

---

### Post by Lorac1949 on 2007-12-17
gilf,

I found the following at the Ubuntu web site.  Does this shed any light on my wireless issue?

Network Manager

    *

      In Ubuntu 7.10, network-manager only manages interfaces that are marked for roaming. Thus, all interfaces that were previously managed by network-manager will be set to roaming mode during upgrade. Technically, this takes any interface stanzas using the dhcp method with no options and that are marked auto, and removes them from /etc/network/interfaces. If you rely on your interfaces being started by ifupdown when the system starts up, you need to re-enable them in /etc/network/interfaces manually, or disable roaming in System -> Administration -> Network.

---

### Post by gilf on 2007-12-17
Actually it sounds to me like everything is working and you have entered the wrong passphrase.

Try turning off wpa on your router and see if you can connect through Ubuntu. If so you've just eliminated most of the other possibilities.

---

### Post by gilf on 2007-12-17
Are you filtering MAC addresses in your router or doing anything else that would block your wireless network card?

The MAC address will be different for the wireless card than the wired nic.

Edit:

Thinking about it however If you are able to successfully connect through windows with the wireless card, that would mean the router accepts the MAC


2. Another question, what kind of WPA passphrase are you using, wpa-psk? Are you certain you are set up for wpa and not WEP , etc

3. Finally the name wifi for your network essid may have special signifigance for the ubuntu networking components since one standard device name is wifi0, you might try a different network name like lorac, or anything.

---

### Post by gilf on 2007-12-17
Sorry for the bunch of posts -- and now a little out of order.

I just noticed your question:

"Should I make the changes to "interfaces" or "interfaces.orig" [the one I changed last night]?"

The only file that has any effect on the operation of networking is the interfaces file.

interfaces.orig is (as a guess)  probably just a backup. I haven't suggested changing that one anywhere in this thread. I do suggest you keep a backup of your first interfaces file.

Now I'm not sure what interfaces file you are using when you get the problem with the wpa password.  Is it the one with the hard coded wpa info in it, or is it the later simpler one?

If it is the former, then try the latter.

The earlier one looked like it might have a conflict in it, since it seemed to be specifying WPA parameters, and also enabling the auto mode..

---

### Post by Lorac1949 on 2007-12-17
> **gilf said:**
> Are you filtering MAC addresses in your router or doing anything else that would block your wireless network card?

The MAC address will be different for the wireless card than the wired nic.

Edit:

Thinking about it however If you are able to successfully connect through windows with the wireless card, that would mean the router accepts the MAC


2. Another question, what kind of WPA passphrase are you using, wpa-psk? Are you certain you are set up for wpa and not WEP , etc

3. Finally the name wifi for your network essid may have special signifigance for the ubuntu networking components since one standard device name is wifi0, you might try a different network name like lorac, or anything.

Good evening.  I just left the router web page.  WPA is marked as N/A.  It has WEP 64-bit protection.

As for suggestion 3. is it possible for me to change the network name?  That's probably a dumb question since the Dell rep DID change it.  Only wrinkle is there are 4 computers connected to the Internet via the wireless.  Do we need to shut them down when I change the network name?  It wasn't an issue the other day because I was the only one home.

Now on to your next post . . .

---

### Post by Lorac1949 on 2007-12-17
> **gilf said:**
> Sorry for the bunch of posts -- and now a little out of order.

I just noticed your question:

"Should I make the changes to "interfaces" or "interfaces.orig" [the one I changed last night]?"

The only file that has any effect on the operation of networking is the interfaces file.

interfaces.orig is (as a guess)  probably just a backup. I haven't suggested changing that one anywhere in this thread. I do suggest you keep a backup of your first interfaces file.

Now I'm not sure what interfaces file you are using when you get the problem with the wpa password.  Is it the one with the hard coded wpa info in it, or is it the later simpler one?

If it is the former, then try the latter.

The earlier one looked like it might have a conflict in it, since it seemed to be specifying WPA parameters, and also enabling the auto mode..

The file I changed last night was the *.orig file because it was the only one that matched what you typed - with the exception of the "wifi" change.  Based on what you've written above, should I make the "interfaces" [no extention] look like this:

auto lo
iface lo inet loopback


iface eth1 inet dhcp
wpa-psk df103ee13088149967ef9a2eb9070d4f565e35078ede2aaa94735bfa270a2d52
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid wifi

auto eth1

---

### Post by gilf on 2007-12-17
Okay,

If you are using WEP 64 bit on the router, you are NOT using WPA.

These are two different methods of encoding wireless network traffic.

You should be entering a WEP password, not a WPA password.

Therefore your first interfaces.orig file was wrong. It specifies WPA parameters.They are hard coded in. I have no idea where that file came from unless somebody hard coded wpa info into it, and then saved it as a backup. Possibly the technician changed your old system from WPA to WEP when he changed the network name -- I don't know.

Therefore, you don't want to use it, or the slightly modified version of it with the "wifi" change.

In your present system, as is, Please check that when you click on a network line it asks for a WEP password, not a WPA password. Because I've lost track of what your present Interfaces file looks like, please copy it here. (when I say interfaces file I mean /etc/network/interfaces with no extension.)

Thanks

---

### Post by gilf on 2007-12-17
"As for suggestion 3. is it possible for me to change the network name? That's probably a dumb question since the Dell rep DID change it. Only wrinkle is there are 4 computers connected to the Internet via the wireless. Do we need to shut them down when I change the network name? It wasn't an issue the other day because I was the only one home."

No, don't do that yet. And if we did, it would be temporary.

---

### Post by Lorac1949 on 2007-12-17
> **gilf said:**
> "As for suggestion 3. is it possible for me to change the network name? That's probably a dumb question since the Dell rep DID change it. Only wrinkle is there are 4 computers connected to the Internet via the wireless. Do we need to shut them down when I change the network name? It wasn't an issue the other day because I was the only one home."

No, don't do that yet. And if we did, it would be temporary.

WILCO.  I will respond tomorrow to the post you wrote just before this one.  I have a deadline to meet for my editor, so need to focus on meeting that.  I'll be back to this forum in the morning.  Thanks again for your help.

---

### Post by Lorac1949 on 2007-12-18
> **gilf said:**
> Okay,

If you are using WEP 64 bit on the router, you are NOT using WPA.

These are two different methods of encoding wireless network traffic.

You should be entering a WEP password, not a WPA password.

Therefore your first interfaces.orig file was wrong. It specifies WPA parameters.They are hard coded in. I have no idea where that file came from unless somebody hard coded wpa info into it, and then saved it as a backup. Possibly the technician changed your old system from WPA to WEP when he changed the network name -- I don't know.

Therefore, you don't want to use it, or the slightly modified version of it with the "wifi" change.

In your present system, as is, Please check that when you click on a network line it asks for a WEP password, not a WPA password. Because I've lost track of what your present Interfaces file looks like, please copy it here. (when I say interfaces file I mean /etc/network/interfaces with no extension.)

Thanks

gilf - We've done it!! \\:D/ Strike up the band! :guitar: This reply is coming via wireless - in Ubuntu!  Hooray!  I read through your post again and something clicked.  "64 bit"  I was logging in with the 128 bit passphrase option.  Duh!!  As soon as I choose the "64 bit Hex" option, in a matter of seconds the Signal Strength icon appeared.  I unplugged the cable; closed Firefox and TBird.  Then I reopened Firefox and Viola! 

I can't thank you enough for your patience!  Out of everything I had previously run across in the forums, you got me on the right track.  Merci!  Gracias!  Danke!  Now I'm on to other things.

---

### Post by gilf on 2007-12-18
Great!

Now a few things to bring away from this for the rest of us:

1.) Ubuntu and Nertwork Manager were acting correctly in this case.

Many, many posts in this forum assume that they are "buggy"t and suggest a variety of programmatic and manual changes which actually cause more problems. Many new users focus on these programmatic changes.

Many, many wireless  problems are being caused by connection misunderstandings, not bugs.

The procedure I outlined at the beginning of this thread is intended to allow you to troubleshoot your system by temporarily reverting to a clean system and methodically eliminating the 3 primary reasons for a lack of connection. No Networks present, No driver for the card, Problems with a user modified system. If you follow that troubleshooting tree you should arrive at a cause (and solution).

2.) It is important in describing a problem with connectivity to give the exact symptoms of the small network icon(s) at the top right of the screen. In this case it showed that the card drivers were working (network essid lines showed up) it then asked for a password (everything is still working) but failed when the password was actually entered. This eventually led to the discovery of what was wrong.

3.) Finally, lorac, just a personal suggestion, if you want a protected system WEP 64 bit is woefully inadequate and outdated. WEP 128 is marginally better but basically easily intercepted and decoded. WPA is considered the norm now. However in your case it would require that all of your wireless cards are compatible with it, as well as the router. And then you would have to set all of the computers to use it. That might be more than you want to tackle now that you have things working -- but something to think about in the future.

Happy computing with Ubuntu, anyway!:)

---

### Post by Lorac1949 on 2007-12-18
> **gilf said:**
> <<snip>>

3.) Finally, lorac, just a personal suggestion, if you want a protected system WEP 64 bit is woefully inadequate and outdated. WEP 128 is marginally better but basically easily intercepted and decoded. WPA is considered the norm now. However in your case it would require that all of your wireless cards are compatible with it, as well as the router. And then you would have to set all of the computers to use it. That might be more than you want to tackle now that you have things working -- but something to think about in the future.

Happy computing with Ubuntu, anyway!:)

This is good to know.  The computers that use the wireless router are currently *not* networked together; however, it's something we will probably do in the near future.  When we do, we'll be looking for the best security available.

Thanks again.

---

### Post by rad_sci_guy on 2007-12-18
I also want to say thanks to gilf.

I tried the Live CD test and lo and behold my laptop had wireless access for the first time ever.  I changed the interfaces file to the default ones you suggested but alas no wireless on the gutsy install on the acer 5040.

I wonder if the problem I am having is that because I was one of those people that immediately went to download drivers and such that they may be interfering with the interfaces correction.  If I remove these other drivers will that solve the problem?

If not is my only option to do another clean install and see if that works?  I don't mind doing the clean install as I just did one last week when I installed ubuntu on the laptop for the first time.

---

### Post by gilf on 2007-12-18
> The computers that use the wireless router are currently *not* networked together; 

Examples of data that can be intercepted and decoded even in an internet-only wireless system with poor encryption:

your isp username and password
your mail server username and password
your email adresses
depending on the vendor's https security, financial information you use in ordering something, including credit card and address information.
usernames and passwords to websites you sign up for

as well as any other traffic you engage in on the internet

This can all be recorded from the wireless  transmissions onto a hard drive and later decrypted. None of this requires that the observer logon to a home network. It's all passive interception.

The same is true of public unencrypted sites like libraries, internet cafes etc.

If you're at home and a wire is available, you may want to use that in preference to wireless for financial transactions, since you have WEP-64.

---

### Post by gilf on 2007-12-18
> I wonder if the problem I am having is that because I was one of those people that immediately went to download drivers and such that they may be interfering with the interfaces correction. If I remove these other drivers will that solve the problem?

If not is my only option to do another clean install and see if that works? I don't mind doing the clean install as I just did one last week when I installed ubuntu on the laptop for the first time.


rad_sci_guy,

I haven't seen a situation yet where wireless worked on the liveCD and didn't work on the HD instaled version from that CD UNLESS the user has made changes.

Applying the /etc/network/interfaces file I gave can solve some but not all of that kind of problem -- so it's not a sure thing. I'd like to improve that score, but it will take more information about what a clean installed interfaces file looks like on a variety of systems.

As a last ditch suggestion, you might try copying down what the interfaces file says in your working LiveCD session, and trying to plug that into your HD installed interfaces file.

If that doesn't work you have a messed up system with unknown changes, and you may want to reinstall.

Let us know what you interfaces file says then, if it works, so I can update the first post with additional information.

Thanks for your help.

---

### Post by Lorac1949 on 2007-12-18
> **gilf said:**
> This can all be recorded from the wireless  transmissions onto a hard drive and later decrypted. None of this requires that the observer logon to a home network. It's all passive interception.

If you're at home and a wire is available, you may want to use that in preference to wireless for financial transactions, since you have WEP-64.

How do firewalls fit into the picture?  In Windows, I have a firewall.  My router has a firewall.  In Ubuntu, I'm using the Firestarter firewall.

---

### Post by Ghost_Dog on 2007-12-18
How do you get WPA encryption to work in feisty fawn
as I cannot connect to networks with this sort of encryption.

---

### Post by gilf on 2007-12-18
> **Lorac1949 said:**
> How do firewalls fit into the picture?  In Windows, I have a firewall.  My router has a firewall.  In Ubuntu, I'm using the Firestarter firewall.

Lorac 

A firewall is a way of preventing other computers from accessing your computer. That means directly affecting your computer or accessing it's internal or connected devices through a network.

A wireless network broadcasts radio signals which anyone can receive who is in range. So that basically defeats one  purpose of a firewall. These signals are the communications between your wireless router and your computer's network card. It is basically a broadcast of your operational traffic with the Internet by radio.

The only way to stop someone else from receiving this information is to encrypt it so it is hard to understand (decode).

With poor encryption, it can be decoded.

As an example of what is routinely sent: every time you ask your email program to "get mail" your computer sends your mail username and password out through a radio transmission.

A firewall in a wireless system may  prevent another computer from attacking your computer through a wire, but it cannot prevent another computer (in radio range) from reading the traffic you are generating over the air. Only encryption can prevent that information from being useful to the outsider.

It can get a little more complicated than that, because if a passive listener can get your user and network information by decoding your wireless  transmissions, they may then be able to use that information to mimic your identity to the firewall and or router, and so change those settings to allow direct access to your computer over the network.

Imagine two homes connected by a sidewalk. The houses are the computers, the sidewalk is the network Each house has a doorman who only lets in certain people using the right password through certain special doors. The doormen are the firewalls.

Suppose the doormen have walkie talkies and they communicate information to people in the house with these.  Anybody standing outside the homes can use a walkie talkie to hear their conversations, though they can't gain access to the home. Some of their conversations include passwords. 

With the passwords an intruder can issue spam all over the internet using the family's mail account, or possibly even gain entry to the house by fooling the doorman.

---

### Post by gilf on 2007-12-18
> **Ghost_Dog said:**
> How do you get WPA encryption to work in feisty fawn
as I cannot connect to networks with this sort of encryption.

Ghost_dog you haven't said how you have tried to connect using WPA. And therein probably lies the problem.

I suggest reading the very first post in this thread -- the part about using a LiveCD session, and trying to connect by clicking on the network bar graph lines. See if that works for you.

My guess is that you have tried to enter WPA passwords manually before trying to connect to a network -- you can't. You have to try to connect first (by the method outlined) then a dialog will open up asking for your wpa password.

On the other hand, if you are asking how to set a router up for wpa -- you will have to refer to your wireless router's instruction book.

Oh, also, one more thing -- you have to have a wireless card that works with WPA -- these are often referred to as 802.111G compatible  types -- the important type is the G part.

---

### Post by Lorac1949 on 2007-12-18
> **gilf said:**
> Lorac 

A firewall is a way of preventing other computers from accessing your computer. That means directly affecting your computer or accessing it's internal or connected devices through a network.

A wireless network broadcasts radio signals which anyone can receive who is in range. So that basically defeats one  purpose of a firewall. These signals are the communications between your wireless router and your computer's network card. It is basically a broadcast of your operational traffic with the Internet by radio.

The only way to stop someone else from receiving this information is to encrypt it so it is hard to understand (decode).

With poor encryption, it can be decoded.

As an example of what is routinely sent: every time you ask your email program to "get mail" your computer sends your mail username and password out through a radio transmission.

A firewall in a wireless system may  prevent another computer from attacking your computer through a wire, but it cannot prevent another computer (in radio range) from reading the traffic you are generating over the air. Only encryption can prevent that information from being useful to the outsider.

It can get a little more complicated than that, because if a passive listener can get your user and network information by decoding your wireless  transmissions, they may then be able to use that information to mimic your identity to the firewall and or router, and so change those settings to allow direct access to your computer over the network.

Imagine two homes connected by a sidewalk. The houses are the computers, the sidewalk is the network Each house has a doorman who only lets in certain people using the right password through certain special doors. The doormen are the firewalls.

Suppose the doormen have walkie talkies and they communicate information to people in the house with these.  Anybody standing outside the homes can use a walkie talkie to hear their conversations, though they can't gain access to the home. Some of their conversations include passwords. 

With the passwords an intruder can issue spam all over the internet using the family's mail account, or possibly even gain entry to the house by fooling the doorman.

Excellent explanation!  Since I've had some time on my hands this afternoon I did some research into our router.  Turns out the encryption CAN be set to WPA.  What would I need to do on my computer so that it's signal would connect to the router?  I suppose this is a basic question, but when it comes to Ubuntu, I've discovered that I can't assume anything.

---

### Post by Lorac1949 on 2007-12-18
gilf,

In reading another one of your posts, I notice that the networking cards in my Dell are 802.11G.  Does that meet the WPA criteria?  Now we need to check the other 3 that connect via wireless.  The beat goes on . . .:guitar:

---

### Post by gilf on 2007-12-18
> **Lorac1949 said:**
> Excellent explanation!  Since I've had some time on my hands this afternoon I did some research into our router.  Turns out the encryption CAN be set to WPA.  What would I need to do on my computer so that it's signal would connect to the router?  I suppose this is a basic question, but when it comes to Ubuntu, I've discovered that I can't assume anything.

Heh, in Ubuntu (NetworkManager), if networking is functioning normally it would be handled automatically!

After making the changes in the router and re-starting it, Just click on the same network line in Ubuntu networkmanager and it should ask you for a (wpa) password. Just like for WEP

See -- it detects the router's transmissions first, determines that a password is needed, then asks you for it.

That's how it works on my system -- with no manual configuration. Systems that have been modified by the user may not behave this way.

HOWEVER -- for windows -- well it depends on your windows system type (9x,xp,vista, etc) your setup, and your card manufacturer's driver and network connection program and the profiles it may need. A lot of variables there!

Also, of course -- your wireless cards must all be WPA compatible (802.111g)

---

### Post by rad_sci_guy on 2007-12-18
> **gilf said:**
> rad_sci_guy,

I haven't seen a situation yet where wireless worked on the liveCD and didn't work on the HD instaled version from that CD UNLESS the user has made changes.

Applying the /etc/network/interfaces file I gave can solve some but not all of that kind of problem -- so it's not a sure thing. I'd like to improve that score, but it will take more information about what a clean installed interfaces file looks like on a variety of systems.

As a last ditch suggestion, you might try copying down what the interfaces file says in your working LiveCD session, and trying to plug that into your HD installed interfaces file.

If that doesn't work you have a messed up system with unknown changes, and you may want to reinstall.

Let us know what you interfaces file says then, if it works, so I can update the first post with additional information.

Thanks for your help.

Hi gilf

I did try and copy the interface from the cd but it did not work either.  The install interface only had the first 2 lines in the default file.  I did a reinstall of ubuntu just now and everything is working well. 

I feel like a fool for not checking the network manager before deciding that the drivers were screwed up and I needed to download something to fix the problem.  I hope others see this thread before they start command line edits like those given in other posts.

I do notice that the wireless connection with ubuntu is slightly slower than the one I have when I log into windows.  Are there some tweaks to speed it up?

Once again, thank you very much gilf.   I think this post should become a sticky in this thread.  You just saved me another week of frustrations.

---

### Post by gilf on 2007-12-18
Congratulations!

> I feel like a fool for not checking the network manager before deciding that the drivers were screwed up and I needed to download something to fix the problem. I hope others see this thread before they start command line edits like those given in other posts.

ps. You're no more a fool than I am -- I had the same initial problems you did. It took a long time to figure it all out. 

Now, would you mind posting here your current (working) installed /etc/network/interfaces file?

I'm extremely curious to see if there is any variety to these after fresh working  installation on different systems.

Thanks!


oh, also:

re internet speed ... do a search for ipv6 settings in Firefox in the forums.

---

### Post by rad_sci_guy on 2007-12-19
Bad news.

Today I turned on the laptop and the wireless light did not go on and Network Manager did not have a wireless option.  I looked at the interfaces and It only has two lines:

auto lo
iface lo inet loopback

This is what the content was when I had the problems before trying your solution gilf.

I installed all the ubuntu updates last night after I got the wireless working.  I didn't note the interfaces content till I read your request gilf.  I'm wondering if one of the updates has altered something that has stopped my wireless card from activating.

Right now I'm using windows on the laptop to reply.  The card is working normally (light on).

I've tried copying the Live CD interfaces onto my install but the wireless option is still not available on the network manager.

I guess I'm back to square one.

---

### Post by gilf on 2007-12-19
> **rad_sci_guy said:**
> Bad news.

Today I turned on the laptop and the wireless light did not go on and Network Manager did not have a wireless option.  I looked at the interfaces and It only has two lines:

auto lo
iface lo inet loopback

This is what the content was when I had the problems before trying your solution gilf.

I installed all the ubuntu updates last night after I got the wireless working.  I didn't note the interfaces content till I read your request gilf.  I'm wondering if one of the updates has altered something that has stopped my wireless card from activating.

I guess I'm back to square one.

Well this shouldn't be too hard to track down and we should learn a lot from it.

Two possibilities come to mind:

1.) If you had a wired card as well as a wireless card and the cable was connected either during the initial install, or during the updates, that might be an appropriate interfaces file for the wired connection.

2.) A fresh install on Feisty yields the interfaces file I posted at the beginning of this thread, while a fresh install or upgrade in Gutsy might produce just the two lines you have found in the interfaces file. BUT Certain cards or installed or upgraded programs require a file LIKE the earlier one with individual stanzas for auto enabling devices. 

One major difference I've noticed (besides the removal of individual auto device stanzas) is the removal of the second two lines in the present interfaces version.

So, If you don't mind experimenting, would you try the following in your present system:

gksudo gedit /ect/network/interfaces

back up your present interfaces file with a .bak extension.

then open again /etc/network/interfaces

paste in:

> auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto ath0
#iface ath0 inet dhcp


Save and try that. If it doesn't work, edit it again and delete  the third and fourth lines:

[COLOR="Red"]address 127.0.0.1
netmask 255.0.0.0[/COLOR]

save that, and try again.

If that doesn't work, and you decide to reinstall your system, make sure it works and please save a copy of the interfaces file *before you update anything* and post it here.



Sorry about all the trouble you are having. But this will help in understanding the problems others may experience as well.

---

### Post by gilf on 2007-12-19
Oh, also one other thing -- are the symptoms you are seeing:

1.) Lack of detection of networks (no ESSID named network bargraph lines to choose when clicking on the network icon, upper right of screen)

2.) Inability to connect (a line or lines for networks are present, but clicking on one doesn't cause the network icon to change from an x'ed disconnected icon a connected large single signal bar graph.)

3.) Connection but unable to open a webpage (big bargraph icon present at upper right, but webpage not found in Firefox)

EDIT:

Thinking about this further

Looking back at your post, you did answer this -- no network lines and no light on the card. That sounds like a driver problem. The problem is, your card worked from LiveCD, and from initial install. It stopped after an upgrade.

 I would try to go to LiveCD again and see if operation is restored. The same with a reinstallation. If so I'd resist upgrading for awhile. Work with the system for a week, turn it off and on frequently. Try to see if you can get it to fail that way -- indicating an intermittent or flaky problem. I suppose chips could be iffy with a particular chip driver, as some others have suggested..

On the other hand if operation is solid over time with a fresh install, and an upgrade breaks it, a reasonable conclusion is that the upgrade altered the chip driver. We'd have to prove that. But I suppose it's possible. If so, after an upgrade you could try to install a new driver to try to correct the problem.

But we want to also be sure to have the same network/interfaces file contents that we did when your initial install was working. That's why it is important to save that and record it here. If it changes during an upgrade it will complicate things (if it isn't in fact responsible for the problem)

Thanks.

---

### Post by rad_sci_guy on 2007-12-20
There seems to be a pattern developing.

The interfaces file only contains the 2 lines below on a clean install.

auto lo
iface lo inet loopback

The wireless network works on the first boot of the install but after a computer shutdown the wireless option in the network manager disappears even when I don't do any updates.

The wifi card light will only come back on if i install acer-acpi from the following link:

[http://code.google.com/p/acer-acpi-deb/](http://code.google.com/p/acer-acpi-deb/)

however the wireless option does not return in the network manager.

It looks as though operating system loses track of the wireless connection settings after turning the computer off and after starting up again there is no way to select a wireless setting.

On a side note, the reason my internet access was so slow was because I had reset the wifi router a couple of days ago and I forgot to enter the Open DNS values which makes a huge difference for my system.  It also makes my XP access much faster too.  I got so focused on fixing the laptop wifi I didn't notice that the desktop was slow too until last night when I was updating some windows software and I couldn't complete the download.

---

### Post by Zip247 on 2007-12-20
As many others have said before, thank you for mentioning the interfaces file.  Mine was quite messed up. I was trying to get a belkin wireless usb running to no avail.  I had tried a guide on zd1211rw driver and it did not work.  Making my interfaces file mirror the one you have posted and a reboot and MAGIC.  Thank you 
:):):)

---

### Post by darkrider2k6 on 2007-12-20
I was having the same problem mentioned by the first post in this thread, where I can see and connect to wireless networks, but I can't get online. The internet did work when I booted from the LiveCD, though. 

After a while, I decided to reinstall Ubuntu, but somehow that made the situation worse. Now, I run into the problem both when I boot from the LiveCD and when I boot from the fresh hard drive installation. 

So I edited the interfaces file to look exactly as posted, but I'm still getting the same problem.

I know that the wireless network works for three other laptops running Windows, and there's no encryption. It's also not an IPv6 issue--I can't download download updates, pings don't work, and websites don't load.

What do you think the problem might be? Have I missed something?

---

### Post by gilf on 2007-12-20
> **rad_sci_guy said:**
> There seems to be a pattern developing.

The interfaces file only contains the 2 lines below on a clean install.

auto lo
iface lo inet loopback

The wireless network works on the first boot of the install but after a computer shutdown the wireless option in the network manager disappears even when I don't do any updates.

The wifi card light will only come back on if i install acer-acpi from the following link:

[http://code.google.com/p/acer-acpi-deb/](http://code.google.com/p/acer-acpi-deb/)

however the wireless option does not return in the network manager.

It looks as though operating system loses track of the wireless connection settings after turning the computer off and after starting up again there is no way to select a wireless setting.

On a side note, the reason my internet access was so slow was because I had reset the wifi router a couple of days ago and I forgot to enter the Open DNS values which makes a huge difference for my system.  It also makes my XP access much faster too.  I got so focused on fixing the laptop wifi I didn't notice that the desktop was slow too until last night when I was updating some windows software and I couldn't complete the download.

Acpi is power management. 

I believe It is possible to turn off acpi from a typed in Grub command at startup. I wonder if you turn off acpi temporarily for a session if the card will work. I forget if the command is acpi=off or if it is noacpi=true -- anybody? I'll look into this and get back to you.

---

### Post by gilf on 2007-12-20
> **darkrider2k6 said:**
> I was having the same problem mentioned by the first post in this thread, where I can see and connect to wireless networks, but I can't get online. The internet did work when I booted from the LiveCD, though. 

After a while, I decided to reinstall Ubuntu, but somehow that made the situation worse. Now, I run into the problem both when I boot from the LiveCD and when I boot from the fresh hard drive installation. 

So I edited the interfaces file to look exactly as posted, but I'm still getting the same problem.

I know that the wireless network works for three other laptops running Windows, and there's no encryption. It's also not an IPv6 issue--I can't download download updates, pings don't work, and websites don't load.

What do you think the problem might be? Have I missed something?

Dark, is it possible that the LiveCD you were using when things worked was an earlier download than the HD installed version you did afterwards? Or did you install from the same CD? Did you do any updates or did updates happen automatically after you reinstalled?

I

---

### Post by darkrider2k6 on 2007-12-20
Everything I've done has been on 7.10. I installed from the same cd that I'm booting from. Also, I haven't downloaded any updates--after all, I'd first need a working internet connection.

---

### Post by gilf on 2007-12-20
> **wdecker said:**
> As many others have said before, thank you for mentioning the interfaces file.  Mine was quite messed up. I was trying to get a belkin wireless usb running to no avail.  I had tried a guide on zd1211rw driver and it did not work.  Making my interfaces file mirror the one you have posted and a reboot and MAGIC.  Thank you 
:):):)

Thanks wdecker. Wish it worked for everybody.

It looks like there has been a change in the normally installed /etc/network/interfaces file as of version 7.10 (Gutsy) , and I believe the one I gave in the first post is the 7.04 (Feisty) version. My best guess now is that some systems still require the earlier interfaces file version, while others work well with the present version. A quote posted by Lorac seems to bear this out:

> In Ubuntu 7.10, network-manager only manages interfaces that are marked for roaming. Thus, all interfaces that were previously managed by network-manager will be set to roaming mode during upgrade. Technically, this takes any interface stanzas using the dhcp method with no options and that are marked auto, and removes them from /etc/network/interfaces. If you rely on your interfaces being started by ifupdown when the system starts up, you need to re-enable them in /etc/network/interfaces manually, or disable roaming in System -> Administration -> Network.

Of the two choices, disabling roaming causes big problems for people if they enter manual configurations that aren't quite right. I made that mistake initially and lost auto connect capability when I saved this faulty config for startup. Couldn't see any networks after that. Also I don't think it is possible to enter WPA passwords manually. So I would suggest to newcomers to Ubuntu particularly NOT to disable roaming in Network Manager.

**Anyway wdecker, great news,**  Happy Ubuntuing!

---

### Post by gilf on 2007-12-20
> **darkrider2k6 said:**
> Everything I've done has been on 7.10. I installed from the same cd that I'm booting from. Also, I haven't downloaded any updates--after all, I'd first need a working internet connection.

But if you boot from LiveCD now the system works, and that is repeatable?

---

### Post by gilf on 2007-12-20
> **gilf said:**
> Acpi is power management. 

I believe It is possible to turn off acpi from a typed in Grub command at startup. I wonder if you turn off acpi temporarily for a session if the card will work. I forget if the command is acpi=off or if it is noacpi=true -- anybody? I'll look into this and get back to you.

Radsci,

You might want to try to turn off acpi advanced power management temporarily to test whether it is interfering with the card startup.

The way to do that is outlined here:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

> As the machine starts to boot you get a Grub message, at this time press the ESC key. This drops you to a text menu. Choose the boot option you want to work with. Navigate using the the up and down arrow keys. (Cursor key.)

When you have selected the menu item press 'e'.

Then you will be presented with a "root" line on the first line. You must then move to the "kernel" line one down from there with the down arrow. then again you press 'e'.

Go to the end of the line (ctrl-E) and add the command to the end of the line of boot options


> acpi=off

> Press the enter key when you are done with the changes, and finally press 'b' to boot.

This will start a one time session without using ACPI. If your card starts up,  please let us know.

If that doesn't work, just reboot and you will have normal ACPI support again.

ps.

Please carefully note the spelling of acpi.

---

### Post by darkrider2k6 on 2007-12-20
> **gilf said:**
> But if you boot from LiveCD now the system works, and that is repeatable?

No. It doesn't work when I boot from the LiveCD, and it doesn't work when I boot from the HD installation. 

The strange thing is that it used to work when I booted from the LiveCD, but after I reinstalled Ubuntu on my HD, it stopped working in both methods. I'm not sure whether the problem is related to the reinstallation, but it shouldn't be, right? I mean, booting from the LiveCD should be totally unrelated to whatever's on my hard drive, right? I guess I must be missing something.

---

### Post by gilf on 2007-12-21
Nope that doesn't make sense unless it is a flaky hardware problem. That may be exaggerated by a stock driver, so if you want to stick with this card, you could try other drivers  -- posted in threads elsewhere.

But you just may find the problem is a hardware failure. Flaky stuff often is.

I recently helped a neighbor with something similar. In her case Windows 2000 wouldn't even boot. Used a Ubuntu liveCD to check things out. It WOULD boot, even if windows wouldn't. Eventually worked my way down to her wired network card. I pulled it out of the computer -- lots of dust in the computer and dull contacts on the board. A minute with a pencil eraser shined them up. I put it back in a different slot just for good measure.

The thing then booted in windows fine.

I had however also installed Ubuntu for her to dual boot, at her request. :)  She liked the fact that it worked when windows choked on a network card problem and was curious to try it out. She's since started to move picture files over to Ubuntu and is having fun learning it.

In your case, besides the flaky hardware possibilities in the computer, you may want to check the router, etc.

Then it's possible to just get a bad network card. I had a wireless card in a windows machine that would work sometimes, and then not others. Using the manufacturers drivers. I put it in a different laptop with the exact same card, and it worked fine. Switching that laptops card back to the first one worked, fine too. Wireless nics aren't perfect and they do have to interact with the computer's software and hardware. Sometimes some cards of the same type act differently.

So try some other card drivers if you want to stick with that card. If that doesn't work, I'd get a new card that was listed as compatible with Linux -- some actually have manufacturer supplied linux drivers.

---

### Post by darkrider2k6 on 2007-12-21
You make a good point about flaky hardware. Since I have the exact same problem when I try using a wired connection, though, I don't think that hardware is the issue in this case. I know that the router is also fully functional, since I'm using it to post right now from another laptop. What other possible issues do you think might be causing this problem?

---

### Post by gilf on 2007-12-21
Well if you have the same problem with a wired connection it can still be a hardware problem, just not a card hardware problem -- unless both are bad (extremely unlikely) . What is controlling the cards? Hardware and software. Either one of which can have problems.

If you dual boot, is Windows working okay with the cards?

Is the router set to allow these cards (their MAC addresses)?

Have you tried the wired side of it on another wired network ( a friend's house, work, etc)?

If networking isn't working in general, I would focus on why the wired side isn't working first. Forget about wireless until you solve that -- wireless is more complicated. Simplify your variables.

Also, if you can, try the cards in a different computer running the Ubuntu LiveCD. Does this work consistently at home. If so, we start to suspect your computer, not the cards and not the software.

Hope these suggestions help.

---

### Post by gilf on 2007-12-21
Also,

try one card in the computer at a time with liveCD session. If both are in the computer at the same time, maybe  there's a software or hardware conflict.

---

### Post by gilf on 2007-12-21
Is your router set up for DHCP or do you assign fixed IP addresses?
Have you changed any router settings recently?


CDs can go bad -- have you done a checksum check on the LiveCD recently?

---

### Post by darkrider2k6 on 2007-12-21
OK, lots of questions, so I'll tackle them one at a time.

> If you dual boot, is Windows working okay with the cards?

Yes, wired and wireless connections work perfectly in Windows.

> Is the router set to allow these cards (their MAC addresses)?

Yes. These cards have never had problems with my router, either. 

> Have you tried the wired side of it on another wired network ( a friend's house, work, etc)?

I haven't tried making a wired connection to another network while in Ubuntu, but wireless connections in Ubuntu to other networks also present the same problems. I can see and connect to other networks, but I cannot access the internet.

> Also, if you can, try the cards in a different computer running the Ubuntu LiveCD. Does this work consistently at home. If so, we start to suspect your computer, not the cards and not the software.

> try one card in the computer at a time with liveCD session. If both are in the computer at the same time, maybe there's a software or hardware conflict.

So taking the ethernet and wireless cards out of my laptop would be quite a difficult process for me and might actually be more likely to cause problems than fix them, especially since I am rather inexperienced with assembling and disassembling laptops.

> Is your router set up for DHCP or do you assign fixed IP addresses? Have you changed any router settings recently? 

The router is set up for DHCP. The router settings haven't been touched in a long time.

> CDs can go bad -- have you done a checksum check on the LiveCD recently?

I didn't think of that. I checked just now, though, and the CD is still good. 

So, since these cards did work just two nights ago with the LiveCD, and since the network settings haven't changed since then, I feel like my current problem most likely isn't being caused by my hardware. Of course it's entirely possible that my intuition is wrong, but I feel like considering other possible solutions may also be useful. What are your thoughts?

---

### Post by gilf on 2007-12-21
> I haven't tried making a wired connection to another network while in Ubuntu, but wireless connections in Ubuntu to other networks also present the same problems. I can see and connect to other networks, but I cannot access the internet.


I thought you said you couldn't see other networks!

If you can indeed see and connect to networks but can't get internet access, then try the Auto detect proxy option in Firefox.  Look back a bunch of posts in this thread it's there somewhere.

---

### Post by darkrider2k6 on 2007-12-21
> I thought you said you couldn't see other networks!

Oh, sorry about the miscommunication. I think I was fairly clear about stating my problem in the first sentence of my first post in this thread, but the specifics of my situation may have gotten confused with the problems that other people in this thread are having.

I set Firefox to auto-detect proxy settings for the network, but no luck. At any rate, I don't think it's a Firefox issue or an issue that changing Firefox settings can fix. I can't connect to the internet regardless of the application I try to use--pings don't work, I can't download Ubuntu updates, and no websites load in any browser.

---

### Post by FoxOne on 2007-12-21
wow, that solved all my wireless problems (except having wifi on and connect at log in see [http://ubuntuforums.org/showthread.php?t=633806](http://ubuntuforums.org/showthread.php?t=633806)) 

Can we make this a sticky?

---

### Post by gilf on 2007-12-21
[QUOTE=]snip....but the specifics of my situation may have gotten confused with the problems that other people in this thread are having.[/QUOTE]

Dark,

Probably I did confuse them. Sorry.

Okay so, as evidence of the fact that you can connect, you are able to access other computers on your LAN, and you see an icon of two little black screens superimposed in the top right of the screen  when you are in LiveCD and on a wired network?

---

### Post by gilf on 2007-12-21
> **FoxOne said:**
> wow, that solved all my wireless problems (except having wifi on and connect at log in see [http://ubuntuforums.org/showthread.php?t=633806](http://ubuntuforums.org/showthread.php?t=633806)) 

Can we make this a sticky?

Glad you were successful, Fox!

I don't know how stickies are determined.

Anyway, Happy Ubuntuing!

ps, Fox, I looked at your thread -- I believe network manager if run in its stock mode with roaming enabled on a stock system and using the keyring to store router passwords *should*
try to connect automatically to your last known good connection, if it is found. It would then only ask you for your keyring password.

If you try to run it manually with a profile, there is no place to enter a WPA password, though I believe you can enter WEP types.

---

### Post by antimate on 2007-12-21
Hi.

I too have had problems with wifi in ubuntu, and this thread helped me understand that it's a bad idea to try and override the automation ubuntu comes with (I'm not really going to use this flavour for long, LFS full-time user).

Anyways, here's how I got around to fixing this:

In the System -> Administration -> Network panel there should be all your currently active (that is drivers loaded) interfaces. Since this is an all-automagic distro, you should set them ALL to roaming mode. Simply click preferences and tick the box in the upper left of the resulting screen for each of your ifaces.

Now, if you don't see a wireless card in Network panel, it means there's no driver present, that is a whole different story and I don't want to go into details of my battles with making that part work.

Anyways, once you have the interfaces set to roaming your /etc/network/interfaces file should only have the loopback iface in it. At least that's what happened when I did what I am now writing.

Next step is the icon with two computer screens in the upper right. If after left-clicking on it there's your wireless network ESSID with a bargraph and all present, click on that, if not, click on "Connect to Other Wireless Network..." and fill in the ESSID, encryption and password fields (correctly). After that you should get a connection. The current active connection is marked with a dot in a radio button on the left of that panel.

I think that any other problems (signal quality, drivers) are not connected to NetworkManager. If you're having those, don't blame NM for it.

So, my version of the story, please comment on it as you see fit.

---

### Post by gilf on 2007-12-21
I recommend the procedures outlined in my first post in this thread.

---

### Post by graabein on 2007-12-22
Hi, thanks to **gilf** and others for this great thread! Have you considered writing up a ubuntu wiki page on this?

I am having some problems with wireless on my xubuntu 7.10 install. When I run **iwconfig** I get the following information:

```
lo      no wireless extensions.

wlan0   IEEE 802.11b+/g+ ESSID:"mynetwork" Nickname:"mynickname"
<snip>
        Retry min limit: 7   RTS thr:off
        Power management:off
        Link quality=35/100  Signal level=9/100  Noise level=0/100
```

I am writing this on a laptop right next to my computer so the signal should be good enough and I was connected to the internet earlier today from my computer.

> **gilf said:**
> Oh, also one other thing -- are the symptoms you are seeing:

1.) Lack of detection of networks (no ESSID named network bargraph lines to choose when clicking on the network icon, upper right of screen)

2.) Inability to connect (a line or lines for networks are present, but clicking on one doesn't cause the network icon to change from an x'ed disconnected icon a connected large single signal bar graph.)

3.) Connection but unable to open a webpage (big bargraph icon present at upper right, but webpage not found in Firefox)

The network manager icon displays two computers with blank screens. Clicking it with left mouse button shows one line with **Manual configuration...** and I get *Problem loading page* on Firefox.

Btw is there a console command I can use to check internet connectivity easier than opening Firefox and typing some random URL? 

Running **sudo apt-get update** gives me no connections either...

Is there a command to try reconnecting to the internet?




**Additional information**: I recently screwed up the file rights on my system trying to reset users <----> old /home directories after reinstall of system. What files should I check for own/group rights you think?? I have set /etc/network/interfaces back to root:root with no result so far... 

Trying a reboot...

Screw this, I'm reinstalling the system and reading up on matching /home catalogs with new users this time around. LOL. Wish me luck.

---

### Post by m0p on 2007-12-22
my problem is that 
i cant see the wireless option in the network manager 

i think editing the etc/network/interfaces would solve it but   i'm having the same problem as graabein   with the file permissions 
i cant edit anything in the file system.

i tried reinstalling ubuntu 
but still no use 
i tried editing from the live cd but  still it doesnt allow 
it says i dont have permissions to do that

---

### Post by gilf on 2007-12-22
I appreciate the recent posts in this thread, but it's impossible to answer every question here. The original purpose of this thread was to provide a particular line of troubleshooting that I developed for a particular type of problem with wireless network cards. 

Unfortunately as this thread has lengthened ,that original purpose may have become obscured, and I'm afraid that the people who would benefit from that original method may never see it. There is often a tendency to go to the end of a long thread to find the "conclusion" or latest information, without looking at the first post.

I hope that anyone with wireless network connection problems will look at the first post in this thread, and will try the troubleshooting procedure outlined there. I continually update it as I learn more from exchanges in this and other threads.

If you have problems with how to edit files, how to set user permissions in programs, general networking questions (other than wireless connection), please consider asking your question in an appropriate forum area by opening your own thread -- you will get far more helpful responses from a greater variety of people -- many of whom are more knowledgeable than I am! That will help keep the focus in this thread on its original purpose.

I also look at many network problem threads and try to help there -- so I can still help you and others with specific problems in your own thread.

I'd still like to hear in this thread from those who this method works for -- just to get some idea how effective it is, and those for whom it doesn't and who have additional useful information to add to the specifics of the troubleshooting method I suggest in the first post. I'd like to improve the first post to be more widely effective than it already is.

Several interesting areas for exploration have suggested themselves to me through these posts -- one which I think may be critical is the relation of ACPI power management to certain wireless chips (Unfortunately that question has lapsed without a response so far) and the possible role of router DHCP leases from service providers, DNS entries, and IPV6 effects on user problems. Many of these appear individually scattered in other threads, but I'd like to refine a comprehensive troubleshooting procedure for all of these. 

One of the biggest problems users face is in locating the SINGLE bottleneck problem they have, without making multiple changes to their system by the stab-in-the-dark method, and hearsay. 

Often systems are made worse by the cures than they were to begin with. In fact, one of the most frequent (and most ironic) problems faced by users has been simply not knowing how to connect using Network Manager, rather than any system deficiency or bug. The primary purpose of the first post was to solve that, and I've tried to do that in threads elsewhere in the forum, as well. 

Finally, nothing in this message is meant to discourage anyone from communicating their specific problems, but if it doesn't advance the purpose of developing a troubleshooting methodology along the lines I've outlined here, I hope you will consider opening a thread of your own  to ask the whole community for help. 

Thanks very kindly!

---

### Post by gilf on 2007-12-23
The first post in this thread now contains how-to edit a file information. 

That information was also originally posted on page 2, post #13 of this thread.

---

### Post by gilf on 2007-12-23
rad_sci_guy, if you are still visiting this thread:

I believe that shutting off ACPI may well prove this as the problem with your wifi card.

see  post number 72 and number 77 in this thread on page 8.

see also page 2 of thread:

[http://ubuntuforums.org/showthread.php?p=4002746](http://ubuntuforums.org/showthread.php?p=4002746)

where I think I've got evidence of ACPI interfering with wireless connection using the test I mentioned.

This could have significance for many wireless problems that have been difficult to track down using the troubleshooting method I show in the first post here.

EDIT: 

It looks like the ACPI problem may be closely related to this bug:

[https://bugs.launchpad.net/ubuntu/+s...ger/+bug/40125](https://bugs.launchpad.net/ubuntu/+s...ger/+bug/40125)

---

### Post by gilf on 2007-12-23
darkrider2k6, if you are still viewing this thread.

There is a possibility that though your wireless router may not be filtering for MAC addresses, if you are using a cable modem/router as well, it may be set for specific MAC addresses by your cable company.

See:

[http://ubuntuforums.org/showthread.php?p=4003907](http://ubuntuforums.org/showthread.php?p=4003907)

---

### Post by n4lne on 2007-12-26
Thanks for the help. I was about to throw the whole thing out the window and use it for target practice. Your cure is great thanks again.

Phil
N4LNE

---

### Post by alexmoon on 2007-12-26
The problem (or at least one of the most obvious problems) that I have is that there is no "wireless" option under network manager. When I make these changes, the "wired" option disappears too. So I guess I've done something silly along the way that I need to fix - pity, it looks like this worked well for a lot of other people!

---

### Post by gilf on 2007-12-27
Alexmoon:

Not sure  -- when you say *make  these changes* -- what was meant.

The troubleshooting method in the first post of this thread suggests that you boot from LiveCD, and make no changes.

Did you try that -- what did you see when you followed the suggested method of connecting?

Thanks.

---

### Post by johngonewbie on 2007-12-27
Newbie question.

seems like a good solution. How do I change permissions to write the new interface file?

---

### Post by johngonewbie on 2007-12-27
also gedit doesn't work. no internet connection until I resolve this. 
How do I edit the interface file in terminal mode? I am using xubuntu.

---

### Post by johngonewbie on 2007-12-27
ahhh.I am enlightened. I 
gksudo mousepad0.2.12 /etc/network/interfaces 
 it worked that way.

New to all this.

---

### Post by gilf on 2007-12-27
good job!

---

### Post by johngonewbie on 2007-12-28
I had to revert to ndiswrapper for a WUSB300N. 
The driver isn't permanent. I have to type
sudo modprobe ndiswrapper 

everytime. 

The startup screen has a host problem. I installed the Xubuntu 
with a bogus host or domain name and I'm unsure of how to 
resolve it. 

sudo ndiswrapper -m is supossed to install the wireless driver.

Manual configuration of the wireless net work freezes.

I am using a linksys router hub with passwords.

anyhelp would be super.

I might start a new thread.

---

### Post by juniorsonny on 2007-12-28
I finally got my WMP54G (Ver 4.1) going.  But, what caused me trouble was not correctly unstalling the old drivers.  I had all the restricted rt61, the serial monkey rt61, ndiswrapper rt61 and the original rt61pci all still loading up and or conflicting with each other.  I renamed drivers and edited files so only the ndiswrapper driver would load.  I also clicked off the network manager from start up because it locked my computer up and using Rutilt.  I want to go back using the serial monkey drivers but i still have to lots of driver cleaning up to make sure they work properly.

---

### Post by tdmoore on 2007-12-28
gilf,

I tried to get my Linksys WUSB54G working and had much help from the community..as a Newb found it frustrating but decided to take my bottles back for the deposit money and spend $39 on a Belkin F5D7050tt adapter that worked with Gutsy right out of the box!  (just had to put in my WPA settings).

Problem I have is that it seems to be running at 24mbps as the top speed even though it's a G router.  (I do get up to 54 in Windows).

When I right click on the "bar icon" and click on the connection information it always says 24.

Is there any way of speeding this up?

Gutsy 7.10 user.

Appreciate what you are doing for all of us Newbs and running wireless...thanks in advance for your assistance with this.

PS. I am truly lousy with commands unless copy and paste and with all the crap some of these people are doing with the rm command am getting leery....

---

### Post by gilf on 2007-12-28
The first thing anyone should establish is whether he or she NEEDS custom drivers for their network card.

The way to do this is to start from a LiveCD session, and look for the network icon in the upper right of the screen. If it is there, click on it. If it opens up showing network(s) (with their names and a signal strength indication)  that are available, your card is communicating properly, and you DON'T need special card drivers!

If things do not work this way from LiveCD,  IT STILL DOESN'T necessarily mean you need special card drivers.

It could just mean that you don't have a router nearby that is broadcasting.

I'm afraid I can't help people with driver problems -- I don't have the knowlege. there are many sources for drivers and information on how to install them in this forum and elsewhere. 

This thread is mainly devoted to getting Network Manager working with your system. And in clarifying how to use it to connect (not obviouis). And how to restore its operation if you have inadvertently messed up your system with lots of changes. The LiveCD method brings your system back to square one -- eliminating the mess temporarily, to see if it was all unecessary..

---

### Post by gilf on 2007-12-28
johngonewbie-

My first question to you would be -- did you try the procedure I outlined from the liveCD and what was the result?

juniorsonny-

Same question.

tdmoore-

I don't know about how to speed up wireless communications in Ubuntu.

If I were you I would open a thread on the subject. Many people will tell you to change IPV6 settings, but they are probably incorrect for your particular problem, as you are talking strictly about the speed of card to router transmission, not internet address resolution. So I would personally ignore that advice. You want info on the transmissions themselves -- maybe packet size or error checking or DMA or interrupt handling to your card or something at a strictly low level for this.

One other thought -- encryption speeds may be affecting things -- as a test you might try to see if turning off encryption speeds it up. If so, the part of the program that handles encryption is the bottleneck. Focus there with a thread.

Also when comparing windows to ubuntu speed -- I hope you checked both of these with the new card -- in case it is just the new card that is slower.

You might also contact the card manufacturer -- maybe they will have an insight into why their driver is fast compared to the Ubuntu driver -- they probably tuned things for windows -- and they might be interested in the fact that a market exists for their cards in linux -- it always helps to show them the linux connection to product sales. They might even have a linux tech in their support staff.

---

### Post by m3topaz on 2007-12-29
Great post, thank you, just what I finally needed for my system to work with WEP. Let me elaborate:
I have a Dell Inspiron 6400 (Dual core 1.73GHz/2GB/7200rpm 80GB HDD/Bluetooth/DVD-RW), with Broadcom WiFi:
===============
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
        Subsystem: Dell Unknown device 0007
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at efdfc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
================
The PC received a Gutsy install, via USB, yesterday. The WiFi didn't immediately work with WEP: I updated the install and then did two things only to make it work:
1) Enabled the firmware from Restricted Devices Manager, downloading from the suggested location; (at this stage WLAN/WEP still didn't work)
2) Changed the etc/network/interfaces file exactly as suggested in this post.
I'm using a BT Home Hub, with 13 character WEP key, SSID shown. This Dell automatically connects on restart so it works just great.
Thanks once again!

---

### Post by alexmoon on 2007-12-29
Ok, I just reinstalled the whole thing from scratch and now I have "wireless networks" as an option again...although Network Manager and Wifi-radar aren't picking up any networks. Editing /etc/network/interfaces to look similar to the version on the first post of this thread still just results in more problems (all options disappearing from network manager apart from 'manual configuration'), but thanks for the help anyway.

---

### Post by gilf on 2007-12-29
Alexmoon,

Sorry to hear about the problems, but you indicated that you had "reinstalled" Ubuntu and you have installed "Wifi Radar".
 
My first question to you several posts ago was whether you had opened a LiveCD session and then followed the method for connecting outlined in the very first post in this thread.

If you had done that you would have either seen wireless networks with bargraphs  (meaning your card driver was okay) or not (probably meaning you need to install a custom card driver).

Reinstalling Ubuntu, adding a second network program, and changing the /etc/network/interfaces file is NOT the sequence I have suggested in this thread to troubleshoot wireless problems. If your problem is a card driver problem, none of that will solve it, and it will likely just complicate matters.

It is important to follow the procedure I mentioned in the first post in this thread, using a LiveCD session. If you do that you will be troubleshooting, rather than simply trying random solutions.

---

### Post by alexmoon on 2007-12-29
Sorry Gilf, I was unclear there and it was unhelpful. I tried the advice you gave, booting from a liveCD, but could not even connect to the wired internet from the CD, let alone wireless. With the live CD, there were only two lines in my /etc/network/interfaces file, and my wireless drivers weren't recognised - I had to install bcm43xx.

Looking around, it seems there are a few people with a broadcom chipset and similar problems to mine.

Thanks for the help.

---

### Post by ososxe on 2007-12-29
I have a weird problem with my Broadcom 4318 card, is a bit long to explain here, and I had already a post open with all the information, but sadly, no responses.
here's the link, if anyone's interested on it:

[http://ubuntuforums.org/showthread.php?p=4037552](http://ubuntuforums.org/showthread.php?p=4037552)

To make a resume, my card is being detected but does not show up on the network manager, not on wicd, not on anything I tried... and I'm lost :(

---

### Post by gilf on 2007-12-29
With Broadcom chipsets the problem is almost certainly a driver or firmware problem.

Below is a link to a fairly long explanation of wireless principles and troubleshooting methods. It goes far beyond the scope of what I suggest here. My main focus is how to use the LiveCD and Network Manager to test a system  [COLOR="Red"]simply[/COLOR] .

A large number of non-driver wireless problems are due to misunderstandings of Network Manager's operation. *These are often mistaken as driver problems or bugs in Network Manager software*, and many people have complicated their problems by applying driver changes or network software changes unnecessarily. The liveCD method works to either tell you you have a driver problem, *or not*, and what to do in the latter case to get Network Manager to connect for you. It does not try to cover driver problems.

[COLOR="Red"]The link below also includes some fairly clear information about Broadcom chips[/COLOR] and what is required for them.

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking)

See especailly the section entitled, ***Configuring Linux with Incompatible Wireless NICs***

---

### Post by rad_sci_guy on 2008-01-16
Hi again

I took a bit of a ubuntu laptop breather during the Christmas holidays but it's a new year and I really wanted to make this work.

I have tried all the suggestions  listed in this thread as well as some other threads in the forums and I finally have something that seems to sort of work.

I could not activate the wireless card (turn on the wireless light on my acer) unless acer-acpi was installed.

I have ndiswrapper running the windows atheros driver and I can get ubuntu to automatically connect to my wifi.

However if i turn the computer off, the next boot up I get the wireless card light to light up, but I lose the wireless options in the Network manager.  If I then do a restart, the wireless light stays on and after ubuntu starts up again I now have auto connection to my wifi.

It looks like unless the wireless light is lit before ubuntu starts to load I won't get wireless options on the network manager.

My question now is how do I get the wireless light to come on before ubuntu starts up or  how do I get ubuntu to check for the wireless adapter only after the wireless light turns on on the Acer.

I remember reading something about that in another thread months ago, but I can't find it again when I search.  If anyone knows how to fix this or has a link to that post I'd appreciate it if you could help me out.

---

### Post by gilf on 2008-01-17
Hi RadSci

Sorry, I can't help you there.

Try opening  a new thread entitled:

**How can I delay Network Manager start at boot time?**

and copy your problem description there.

Then edit your last post here to provide a link to your thread for others with a similar problem.

Good Luck!

---

### Post by Kulgan on 2008-01-18
For some reason, if I go into the manual settings, the drop-down list from the icon disappears. I got it back by removing any mention of interface definitions in /etc/network/interfaces ("auto ethX" and "iface ethX..." leaving only the loopback interface lines in there. Network manager now works perfectly. 

@rad_sci_guy:
I'm not sure if this is quite what you are looking for, but it seems to do something similar to what you are looking for: 
[http://ubuntuforums.org/showthread.php?t=667429](http://ubuntuforums.org/showthread.php?t=667429) (second post)

All he says is add the line 
```
pre-up sleep 20
```
to the interfaces file. I'm taking it that "pre-up" commands are run before a ifup ethX command, so "sleep 20" would cause the script to pause before continuing. I guess in theory the rest of the OS should have booted by that time. 
Another alternative would be to have an executable bash script in /etc/network/interfaces/if-pre-up.d/ containing 
```
#!/bin/bash
sleep 20
```

Hope that helps...

---

### Post by m1k3uk on 2008-01-18
Hi gilf my problem is the same using both the live cd and full install.  When i click network manager i see a list of networks and when i click mine it prompts me to insert the key.  I put the correct key in which is a 64bit hex wep key and click connect.  the two circles with a swirl around them at the top move round and the lower circle turns green however the upper one doesnt, also the light blinks on my wireless adapter.  After a minute or so the prompt to enter the key just reappears.  Ive tried taking all the security off the router but that doesnt change anything??

Any ideas to how id solve this problem????  thanks

---

### Post by Kulgan on 2008-01-18
Sounds like auth error. 

Are you using WEP Passphrase or WEP Hexadecimal in the dropdown? For ages I never even knew there was more than one WEP option...

---

### Post by m1k3uk on 2008-01-18
its wep hex im using but tryed all combinations and even turned security off because i thought that was the problem but it still does the same thing :(  ive also tryed it using wicd network manager but tht does the same thing it just appears to halt when it says obtaining ip address.  Do you think this could be a possible driver problem because it refuses to connect?

If anyone else has any ideas please help me because im really interested in using ubuntu but if i cant use the internet its not much use to me.

---

### Post by Kulgan on 2008-01-19
> If anyone else has any ideas please help me because im really interested in using ubuntu but if i cant use the internet its not much use to me.
Yeh, I know what you mean. I experienced similar frustration with 6.06. 

I don't think this has anything to do with drivers, though. If that were the case, you wouldn't be seeing the network in the first place, and the wireless interface wouldn't show up in the network manager. In the past, however, I have had some dodgy connections, both with wireless and wired connections. If I was too far away, I couldn't connect, even if I could see the network at 50-60%. 

What's your terminal output from 
```
iwlist scanning
```
and 
```
lspci
```

And what is the name (essid) of your network?

Hope we'll be able to sort things out :D

---

### Post by m1k3uk on 2008-01-19
Ive been messing with this for hours and im so frustrated with it now.  Here are the outputs from terminal:

BTW my ssid is "BTHomeHub-C80E"

```
mike@mike-desktop:~$ sudo iwlist scanning
[sudo] password for mike:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results


```

and 

```
mike@mike-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
mike@mike-desktop:~$ 

```

and i tried this one too

```
mike@mike-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"BTHomeHub-C80E"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:14:7F:80:F0:96   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

hope this sheds some light on what my problem maybe??
Thanks

---

### Post by m1k3uk on 2008-01-19
Hi thankyou very much for all your help getting the wireless setup but im made up to say ive managed it.  I just about managed to plug it into the wall and download a gui for the ndiswrapper software and extracted my windows wireless drivers and ran it all and hey presto it worked.  i just needed to blacklist the ubuntu driver and change the interfaces file like in this thread and it worked.  Was just a strange phenomenon how i could see the ssids but it wouldnt connect???  Anyways im off to download some packages!!

Thanks

---

### Post by Kulgan on 2008-01-20
Very happy it all worked out for you! It was a driver problem after all, then. I guess the ubuntu driver could see networks but not do anything useful with them... 

Could you post what you did here, just so that when somebody else comes along with the same problem, they know what to do?

---

### Post by gilf on 2008-01-20
I wonder if you also changed a fixed IP address setting to DHCP, or vice versa (depending on which was appropriate)  in installing new drivers, and that was part of the actual problem.

To eliminate any curiosity on this point, you might want to try a liveCD connection attempt with your router encryption (WEP/WPA) turned off, and the router set to DHCP.

---

### Post by gilf on 2008-01-20
> **m1k3uk said:**
> its wep hex im using but tryed all combinations and even turned security off because i thought that was the problem but it still does the same thing :(  ive also tryed it using wicd network manager but tht does the same thing[COLOR="Red"]** it just appears to halt when it says obtaining ip address**[/COLOR].  Do you think this could be a possible driver problem because it refuses to connect?

If anyone else has any ideas please help me because im really interested in using ubuntu but if i cant use the internet its not much use to me.

This is the part that makes me think you might have simply been using the wrong IP address, or that your router was set for static addresses while your Ubuntu installation was looking for a DHCP address assignment.

---

### Post by Kulgan on 2008-01-20
> **gilf said:**
> This is the part that makes me think you might have simply been using the wrong IP address, or that your router was set for static addresses while your Ubuntu installation was looking for a DHCP address assignment.

Might also have been set not to accept new wireless devices (my router at least has that function). But that doesn't explain how installing a new driver would affect any of the settings on the router.

---

### Post by gilf on 2008-01-21
He seems to have made many concurrent changes. He may have reset the IP method or address  manually, during driver installation, or by his method of use. He has changed network management programs as well. He may have noticed and changed a router setting.

It would simply be interesting to see if he tried it from liveCD with the DHCP router settings I gave above, whether he could connect.

The stage he reached with the network icon earlier and receiving the password query tends to indicate that the drivers were actually working at that stage. To get to that point they had to have functioned with the wireless hardware in:

1.) intercepting broadcasts, 
2.) determining channel
3.) determining ESSID,
4.) determining the need for a password. 

After it was entered, authentication simply failed. This is almost always a function of matching router requirements at that stage, rather than an inability of the card to receive and decode. The fact that it threw a message about IP address, also tends to indicate that the password authentication stage had  completed properly, and the IP address negotiation was in progress -- in other words, he was connected wirelessly, but not routed into the network.

That could simply be mismatched IP assignment expectations. The most likely of which is a static router while the client expects DHCP assignment. Or there could be a MAC address filter on. There are plenty of causes of routing failures.

It just really sounds like the wireless functions had progressed through their authentications already when the bottleneck occurred.

Not a certainty, of course, nothing is. But it would be good to clear up this point with a simple test.

---

### Post by buuu2 on 2008-01-26
Hello folks.  I tried the suggestions posted by gilf and I have to say thanks because it got me hopeful and led me to what turned out to be a simple solution.  The changes suggested did not work for me.  BUT, i ran off a live CD and then went into the interfaces file (through gksudo gedit as posted in the directions even though i was not going to edit it).  I did this to see what the heck the settings were on the live CD that was making it run network mgr the way it should.  it showed two lines:

auto lo

iface lo inet loopback

So, i restarted off my hard drive and started back with gilfs instructions but replaced everything with the two lines you see above.  it worked!
 so maybe if you copy the interfaces file while up and running off the cd you will find your answers.

---

### Post by gilf on 2008-01-27
That's the normal install in a 7.10 system. So basically you reverted to the clean 7.10 version from what you probably had changed at some stage of setting up your wireless configuration.. 

That works for some installations, but not others. The /etc/network/interfaces file given at the beginning of this thread is apparently what 7.04 installed clean, and that one seems to work for others -- and possibly a greater variety of wireless configurations.

I think the best policy would be to:

1.)Test with LiveCD using the connect method detailed in the first post in this thread.
2.) If that works AND if the CD is a 7.10 version, install the simpler file listed above
3.) if it doesn't, try the /etc/network/interfaces file given int the first thread.

Always make backup copies of your original /etc/network/interfaces file before editing it. And always revert to it if the edited version doesn't immediately clear up your problem.

---

### Post by Kulgan on 2008-01-27
Exactly what I did. Guess it gives network-manager a fresh start :D

---

### Post by akhyarsi on 2008-01-30
I have same problem with m1k3uk.
I can see the bar, entered the password,  see signal strength, but the internet is not working.

What should I do?

I attach the screenshot of my monitor.

---

### Post by markhorrocks on 2008-01-30
This worked for me, it finds the network and connects to it. However, if I then go to System |Admin | Network I see that roaming is selected. If I try to alter this at all the network becomes disabled. Nothing I can do will get it back except a reboot. Currently, I am just booting from LiveCD. Should I just leave it set at roaming? This really isn't intuitive. A better default setting would be to prompt the user that a network is found and invite connection, just like Windows!
Anyway thanks for this enlightening post, I would probably have wasted several more days trying to figure this out but for this thread. Moddy, please amke this a sticky! It will save man years of wasted time!

---

### Post by gilf on 2008-02-02
> Should I just leave it set at roaming? This really isn't intuitive. A better default setting would be to prompt the user that a network is found and invite connection, just like Windows!

I have a laptop and so I leave it on roaming.

The way that works is that if you are in an area where several networks are available, they all do show up if you click on the network icon in the top right. You can then select the one you want to connect to by clicking on it. If it requires a passphrase, you will then be asked for it.

This is at least as easy as Windows.

You should then also be asked if you want to save that passphrase in the keyring. I personally say yes. Then you will get automatic connections to networks you have set passphrases for. 

On subsequent boot ups you will be asked for your keyring password ( a master password) which allows it to supply the appropriate passphrases to the networks you connect to. Remember that your keyring password is (usually) different than your connection passphrases. You set that master password when you first run the keyring. In kubuntu the Kwallet is similar.

If you unclick roaming, network manager will not try to automatically connect. This would probably only be appropriate if you never moved the wireless computer -- as in a desktop. Then you would set up the connection parameters manually.

---

### Post by gilf on 2008-02-03
**I found a new problem on my own home network** that had me puzzled for awhile. This may apply to others with similar symptoms.

I could see my network after clicking on the upper right icon, and it would appear to connect. Yet I was never connected in fact -- nothing would work, pings to the router, nothing. Actually, sometimes it would work and sometimes it wouldn't

This was really driving me crazy until I noticed that a small wireless print server I had hooked up recently was set to ad hoc mode (no encryption) and had the same ESSID as the main wireless route (wpa encryption)r. This created two wireless access points, with the same name.

This same situation can occur in places like schools with student computers set to ad hoc, or anywhere where there are multiple access points with the same name.

I was in fact connecting with the printer server (so the network  icon showed connection) but not with the wireless router. Probably if I'd pinged the printer server insted of the router, I'd have had replies.

It was not possible to connect to the wireless router in preference to the printer. What I finally had to do was rename the printserver ESSID to a different name from the wireless router.

After figuring this out, I did find bug reports on the multiple ESSID problem with Network Manager.

However, I haven't seen much discussion of the symptoms, and this may explain another group of connection problems.

While it isn't possible to cure multiple paired  ESSIDs in a public place, you can often do it at home by simply changing a name, or eliminating ad hoc connections, if they exist. 

In a public place, you may be able to choose an access point that is unique, rather than one of a pair.

Some users have reported that symptoms include not only bad connections (though apparently shown as connected) but also intermittent, and changing connections and dropouts while connected as a result of this problem.

---

### Post by gilf on 2008-02-03
> **akhyarsi said:**
> I have same problem with m1k3uk.
I can see the bar, entered the password,  see signal strength, but the internet is not working.

What should I do?

I attach the screenshot of my monitor.

This one looks a little like the multiple essid problem I had -- what do you see if you click on the network icon in the upper right -- if you see two networks with the same name that may be it. If not, it could still be a dual essid if you earlier did something to eliminate one of them (I did that, but don't recall the steps -- possibly "create new network".

If this isn't the problem, another possibility (since the icon seems to show that you are connected but you don't have a network address) is that you either don't have DHCP configured on the router or client (or static addressing set up properly if you use that).

---

### Post by rangi500 on 2008-02-20
Thank you!

---

### Post by jairichard on 2008-02-21
I tried for ages to get ndiswrapper to make my WUSB54G work without success despite a huge amount of reading from this forum. I did a reinstall of Ubuntu 7.10 and  bought a Sweex LW053 USB device with a ralink chipset which device manager found but wireless never connected. I eventually found from dmesg run just after replugging the USB wifi device that the rt2500usb driver had failed to initialise. Today I found this thread and really hoped this would be my solution. Booting the Live CD connected just fine with WEP64 too. returning to the hard drive installation and editing interfaces as suggested did not help. I read the whole thread but that did not help either.
If it is a driver initialisation problem that is responsible what can I do about it? I thought of trying the other driver rt73 but searches for remove driver etc don't seem to offer any help I can understand. Or do i have to give in and try ndiswrapper despite my live experience?
I am very new to Linux and Ubuntu and really need explicit type instruction like appears in this thread.
Hoping for a Little help here on the very steep learning curve:)
Richard.

---

### Post by jairichard on 2008-02-21
Solved! by replacing the rt2500usb driver with the rt73 one using Wieman01's most excellent thread at [http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547). I blacklisted the rt2500usb driver hoping that was a correct thing to do.
Everything now working in automatic withh blue signal strength icon too. So very pleased now as this has been bugging me for over a week now.
:popcorn::guitar:

jairichard.

---

### Post by gilf on 2008-02-26
Sorry I missed your first post -- glad you solved your driver problem. This thread is mainly devoted to  identifying common  non-driver network manager issues -- the main one being a lack of new user understanding (and NM documentation) of how to use and interpret NM -- basically a description of what to do and what to expect when connecting, And how to determine if you've negatively altered your system.

The tipoff that it is an installation problem is in trying it out on LiveCD. If it works there, the next step is tracking down what is different with your HD  installation.

Many people, when they experience problems in an HD installation, never think to try out a LiveCD session again. In fact some assume they can't.

In factLiveCD is a very important troubleshooting tool, and can help you focus on where the actual problem lies. Much blame for wireless  problems was formerly heaped on NM. A large proportion of that was due to misunderstanding of how it worked, and what to do in it if you didn't connect.

Trial alterations of NM settings would complicate the problems, when in fact connection would have worked if the right procedural steps were followed. This was complicated by people changing drivers and network programs without actually determining if these changes were actually needed. In the end many systems suffered from multiple problems compounded by the remedies.

That is not to say that there aren't legitimate driver problems at times, like yours, or that NM doesn't have some bugs. But generally it works quite well IF, and only if, a user understands how it works, how to use it, and what it expects.

That was the function of this thread, and LiveCD was one of the tools it used to temporarily stand  back from possibly unnecessary user setup complications and identify what is wrong.

You were a little unlucky in choosing two difficult wifi cards. The first one mentioned, I own as well, and haven't bothered to try to get working (I also have 2 Atheros D-link cards that work fine) and the second was a USB card -- these generally are more difficult to get working.

Very glad you are Ubuntuing now, though! Happy connections.

---

### Post by mrobinson_sr on 2008-02-29
Wireless is working (with no encryption) but cannot find anywhere how to correctly input WEP.

I go into System Settings/Network Settings (KDE) and input the WEP key, change ASCII to Hexidicimal, click apply, the network restarts, and no connection.  I go back into the network settings and the WEP information does not hold, it changes back to no key and ASCII.  I've tried changing from Automatic to Manual, which does hold the key but  will not connect to the network, because everything else on the network is DHCP.  

I loaded WICD Manager, it shows the network, shows that it is WEP protected but there's nowhere to input the key, the fact that it's open, or that it's 64 or 128 bit (unless the operating system assumes the bit rate due to the length of the key).

Do any of you Linux wizards have experience with WEP setup:).

Thank you

---

### Post by Dngrsone on 2008-02-29
In wicd, you need to assign a static address, then it will allow you to assign a key.

---

### Post by gilf on 2008-02-29
Please go to the first post in this thread and follow the exact directions there for connecting using a LiveCDsession  through KnetworkManager (if you are using Kubuntu).

When you click on the network name of the network you want to connect to (essid) the dialogue for entering the WEP occurs automatically, if your access point reqires a WEP key. The dialogue that pops up allows you to select whatever key type (ascii, hex, 64 bit, etc) you want to enter. 

I'm unclear also about your mention of DHCP -- are you trying to connect with a static address, or with a DHCP assignment? If DHCP, you don't have to do anything, it's all handled automatically.

If you need to enter a static address, write back.

---

### Post by Northsider on 2008-03-01
:-[  Wireless worked on live-cd, not after install

This what my original file looked like:
> auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



I edited it to this:
> auto lo
iface lo inet loopback

Still not working.

---

### Post by gilf on 2008-03-01
Northsider:

The first file looks like a 7.04 install default, and the second looks like a 7.10.

When you say "original file" -- please describe in what:

How recent an install, what version of K(ubuntu), and has this install been "modified" (ie have you set any network parameters manually, changed drivers from stock, changed network manager apps, or is this a brand spanking new fresh install).

When in LiveCD session, what does your /etc/network/interfaces file look like?

Sorry -- going to bed now but will check answers tomorrow.

---

### Post by Northsider on 2008-03-01
gilf, I installed 7.04 and then upgraded to 7.10 very recently.

I have not changed anything with my Kubuntu install.  I will load up the live 7.04 cd and edit this post.


EDIT:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-essid dlink
wireless-key 0123456789

auto wlan0
iface wlan0 inet dhcp


---

### Post by courgette18 on 2008-03-01
Hi
I have a a problem connecting my Belkin FD7050 USB wireless adapter in 7.10.  It worked fine in 7.04.  What happens is the same for the live CD and the hard drive version (which I installed from the live CD).  I can see my wireless network using the icon in the task bar.  When I select it to connect, it asks me for my 128 bit WEP key.  I enter it and the two small circles appear.  The lights flash on the USB adapter and the bottom circle goes green.  Then after a while it just prompts for the key again and hasn't connected.  I've tried passphrase and hex key and both give the same result.  Anyone got any ideas?  I'd really appreciate some help to get this going.  Otherwise, I think it will mean going back to 7.04.

Thanks :)

---

### Post by mrobinson_sr on 2008-03-01
:)> **Dngrsone said:**
> In wicd, you need to assign a static address, then it will allow you to assign a key.

Thank you.  What i didn't realize was that by clicking the small arrow, beside SSID name, would open the other settings.  I had been looking for these settings and couldn't find any, and just by chance I clicked this arrow and it expanded the box to allow for the static IP, router, SSID and encryption method.

Thank you, now I can move on to the next hurdle.\\:D/

---

### Post by mrobinson_sr on 2008-03-01
> **gilf said:**
> Please go to the first post in this thread and follow the exact directions there for connecting using a LiveCDsession  through KnetworkManager (if you are using Kubuntu).

When you click on the network name of the network you want to connect to (essid) the dialogue for entering the WEP occurs automatically, if your access point reqires a WEP key. The dialogue that pops up allows you to select whatever key type (ascii, hex, 64 bit, etc) you want to enter. 

I'm unclear also about your mention of DHCP -- are you trying to connect with a static address, or with a DHCP assignment? If DHCP, you don't have to do anything, it's all handled automatically.

If you need to enter a static address, write back.


Thank you.  I got it working with WICD and a static IP.  for some reason Knetwork manager was not loaded, perhaps I had to select it as a separate application, that's when I found an instruction set for WICD.  But I've bookmarked this incase I need to go back.  Thank you again.:)

---

### Post by Prefix100 on 2008-03-01
nice, thanks alot man, this was the first step in fixing my wireless issues.

---

### Post by gilf on 2008-03-01
> **Northsider said:**
> gilf, I installed 7.04 and then upgraded to 7.10 very recently.

I have not changed anything with my Kubuntu install.  I will load up the live 7.04 cd and edit this post.


EDIT:

Northsider,
You need to test with a LiveCD of the version you are using. In other words, if you've upgraded to 7.10 on your HD then test whether you have connectivity in a 7.10 LiveCD session.

---

### Post by gilf on 2008-03-01
> **courgette18 said:**
> Hi
I have a a problem connecting my Belkin FD7050 USB wireless adapter in 7.10.  It worked fine in 7.04.  What happens is the same for the live CD and the hard drive version (which I installed from the live CD).  I can see my wireless network using the icon in the task bar.  When I select it to connect, it asks me for my 128 bit WEP key.  I enter it and the two small circles appear.  The lights flash on the USB adapter and the bottom circle goes green.  Then after a while it just prompts for the key again and hasn't connected.  I've tried passphrase and hex key and both give the same result.  Anyone got any ideas?  I'd really appreciate some help to get this going.  Otherwise, I think it will mean going back to 7.04.

Thanks :)

As in mrobinson's problem, have you noticed the little selection arrow (triangle) beside the place where you enter your key? It allows you to select the type of key to enter.

This type, and the exact word/phrase/hex/asii WEP key must match what your router expects. Also be sure your router doesn't exect a WPA key instead of a WEP key. Apologies if you already know all this -- I have no way of telling.

Also, one other possibility -- are there two network essids in  your area with the same name? Example: a school with a lot of laptops owned by students set to ad -hoc using the same essid?

---

### Post by gilf on 2008-03-01
Prefix100, you're welcome! Have a good time with Ubuntu.

---

### Post by Northsider on 2008-03-02
> **gilf said:**
> Northsider,
You need to test with a LiveCD of the version you are using. In other words, if you've upgraded to 7.10 on your HD then test whether you have connectivity in a 7.10 LiveCD session.
Hmm, ok I will try that.  Thanks again.


EDIT:  This is what my /etc/network/interfaces files looks like with the 7.10 live-cd, wireless works perfectly:

> auto lo
iface lo inet loopback


However I have a few new folders in my network folder: 
[IMG]http://i32.tinypic.com/j79b0y.png[/IMG]

^^ I don't believe these exist in my installation.

---

### Post by courgette18 on 2008-03-02
> **gilf said:**
> As in mrobinson's problem, have you noticed the little selection arrow (triangle) beside the place where you enter your key? It allows you to select the type of key to enter.

This type, and the exact word/phrase/hex/asii WEP key must match what your router expects. Also be sure your router doesn't exect a WPA key instead of a WEP key. Apologies if you already know all this -- I have no way of telling.

Also, one other possibility -- are there two network essids in  your area with the same name? Example: a school with a lot of laptops owned by students set to ad -hoc using the same essid?


Thanks for the reply.  I'm very much a Linux newbie, but yes, I have checked all the WEP stuff and it looks correct  I think this is the only network in the area with this essid name.  We have a couple of laptops running windows that connect to it no problem.

I also noticed that the Ubuntu PC does appear on the router's DHCP client list with an IP address assigned.  So it seems to be getting so far, but no further...

Any other ideas much appreciated!  :)

---

### Post by gilf on 2008-03-02
Northsider,

I'm afraid I'm going to be saying the obvious without much specific assistance, but your upgrade and a new install/liveCD session are somehow different, and that difference is what is causing your problems.

If you can determine what the differences are (iit looks like you are trying to do that) you may be able to correct it.

One thing is clear -- a stock 7.10 installation using NetworkManager does work with your card and computer. But how get there is the problem. It's going to take some hunting down.

---

### Post by gilf on 2008-03-02
Courgette18,

Weird -- you're assigned a DHCP address, but supposedly aren't connected.

Well lets try something:

Sometimes the first time you try to connect things are messed up, or somebody with another laptop happened to be in ad hoc mode on the same network. This gets saved as a configuration -- lets just try to remove any faulty configuration that may have gotten saved.

If you type into the terminal:

gconf-editor

a configuration screen will open up.

Navigate by clicking on twisties in the left panel to 

 system>networking>wireless>networks

Do you now see in the left pane your network name listed?

If so, click on it. It will show in the right pane several configuration lines. One of them will be labeled bssids.

Double click on it and a small window will open up showing a list of one (or several) bssids (lines of 6 pairs of hex codes separated by colons) for that network

How many bssids (hex code lines) are there?

If more than one, try removing all but one of them and restarting your computer and using the connection instructions in the first post in this thread.

If that doesn't work, or there was only one to begin with, delete all of the bssids for your network, restart and try to connect.

---

### Post by Northsider on 2008-03-02
> **gilf said:**
> Northsider,

I'm afraid I'm going to be saying the obvious without much specific assistance, but your upgrade and a new install/liveCD session are somehow different, and that difference is what is causing your problems.

If you can determine what the differences are (iit looks like you are trying to do that) you may be able to correct it.

One thing is clear -- a stock 7.10 installation using NetworkManager does work with your card and computer. But how get there is the problem. It's going to take some hunting down.

Bogus...looks like I'll just have run a cable and connect directly.  Thanks.

---

### Post by gilf on 2008-03-02
Northsider,

I'm assuming that you tried adding the new /etc/network/ folders in the LiveCD session to your installed system, and that didn't work. If not you might give it a try. I'd also suggest posting a topic here on the forums, like "Upgrade to 7.10 breaks wireless" and describe your exact upgrade steps, and the fact that from a LiveCD your system works out of the box. Someone out there will probably be able to help better than I can on upgrade issues.

I wouldn't give up, if it works on liveCD there's absolutely no reason it can't on your installation.

---

### Post by Northsider on 2008-03-02
> **gilf said:**
> Northsider,

I'm assuming that you tried adding the new /etc/network/ folders in the LiveCD session to your installed system, and that didn't work. If not you might give it a try. I'd also suggest posting a topic here on the forums, like "Upgrade to 7.10 breaks wireless" and describe your exact upgrade steps, and the fact that from a LiveCD your system works out of the box. Someone out there will probably be able to help better than I can on upgrade issues.

I wouldn't give up, if it works on liveCD there's absolutely no reason it can't on your installation.

Thanks buddy.  I did try copying the folders from the live-cd, but I didnt have permissions and it wouldn't let me.  I won't give up, but it's not that big of a deal.  Thank you for all your help.

---

### Post by martov on 2008-03-02
Hi. 

Could you help me out?

When I click on the  Networkmanager icon , I see the ESSID name and a bar next to it, that means the card is working fine.

But, the bar is completely grey, even though the computer is right next to the router (right next to another computer with the same wireless card model on, actually).

And when I click on the bar, the window closes, and then the  Networkmanager icon disappears. And nothing else happens.

I´m running Xubuntu, and I´ve been trying different stuff for days, I´m downloading Ubuntu to see if it works. The card model is MSI PC54G3.

I´d really appreciate a hand :KS.

---

### Post by gilf on 2008-03-03
Do you mean you are trying to connect to a router or just another computer ad hoc?

I'm not familiar with xubuntu -- don't even know if it uses Network-Manager.Sounds like it does from what you say.

However if the applet icon disappears entirely after you click on it, I'd say it crashed silently.

Also sounds like you have a new installation -- a crashing app can simply mean that your installation CD was bad.

Run the LiveCD and in the boot menu select the option to check the CD for errors.

If you have a good CD, try to do the connection steps listed in the first post in this thread while in a LiveCD session. Try not to configure anything manually at first, unless you have to (static IP requires it) Ideally you'd be trying this with a router set to DHCP and no encryption to start. If you can connect then, move on to encryption. Finally if that works, move on to manual configuration of static IP -- if that's what you want.

In other words, try to break down the problems into manageable chunks, using the least configuration possible.

---

### Post by gilf on 2008-03-03
Northsider,

I don't know your drive names or partitioning structure, but for a quick and dirty way to get permissions for a newbie in graphic mode, just do a: 

sudo nautilus

That will allow you to graphically use your normal file manager in superuser mode. You can then copy files to the cli[pboard and navigate back to the folder you want to put them in and paste them there.

Remember that you have to navigate in the same window to where you want to go -- if you go outside of it and click Places above your window, you'll be out of super-user mode, and will lack permissions to cut and paste these files.
so, roughly step by step:

1.) sudo nautilus
2.) go up the window chain one step (up arrow at top of screen)
3.) navigate to /etc/network/ 
4.) ctrl left click on all the files you want (to hilight them)
5.) rt click edit>copy (them to clipboard)
6.) go up the chain again two levels to /
7.) open /media
8.) pick your hard drive and navigate to /
9.) pick /etc
10.) pick/network and paste your files there.

ps. Don't tell anybody I said to to a sudo nautilus. Learn the terminal commands and forget you ever did it. This will be our little secret.

---

### Post by Northsider on 2008-03-03
> **gilf said:**
> Northsider,

I don't know your drive names or partitioning structure, but for a quick and dirty way to get permissions for a newbie in graphic mode, just do a: 

sudo nautilus

That will allow you to graphically use your normal file manager in superuser mode. You can then copy files to the cli[pboard and navigate back to the folder you want to put them in and paste them there.

Remember that you have to navigate in the same window to where you want to go -- if you go outside of it and click Places above your window, you'll be out of super-user mode, and will lack permissions to cut and paste these files.
so, roughly step by step:

1.) sudo nautilus
2.) go up the window chain one step (up arrow at top of screen)
3.) navigate to /etc/network/ 
4.) ctrl left click on all the files you want (to hilight them)
5.) rt click edit>copy (them to clipboard)
6.) go up the chain again two levels to /
7.) open /media
8.) pick your hard drive and navigate to /
9.) pick /etc
10.) pick/network and paste your files there.

ps. Don't tell anybody I said to to a sudo nautilus. Learn the terminal commands and forget you ever did it. This will be our little secret.

lol.  I'll try this when I get home.  I won't tell anybody.  :)


EDIT: I get this: "error, operation not permitted while copying /etc/network...asupplicant.  Would you like to continue?"  Wont let me do it.

Also tried terminal commands:
> ubuntu@ubuntu:~$ cp /etc/network/* '/media/2GB FLASH/Network' 
cp: omitting directory `/etc/network/if-down.d'
cp: omitting directory `/etc/network/if-post-down.d'
cp: omitting directory `/etc/network/if-pre-up.d'
cp: omitting directory `/etc/network/if-up.d'
ubuntu@ubuntu:~$ 


---

### Post by gilf on 2008-03-03
hmm, maybe try the terminal commands in Recovery Mode (when you boot the LiveCD, choose it instead of the full program). You'll be root there right at the start.

---

### Post by Northsider on 2008-03-03
EDIT:  This is too much trouble than it's worth.  Plugging in ethernet now...

---

### Post by pbags on 2008-03-04
Gilf, I'm trying to solve this wireless problem too. You say in your guide:

"With the password or passphrase entered for the wireless encryption, you should see the network icon become two small circulating dots. This indicates the password is being authenticated and a connection attempt is being made. If authentication occurs correctly the icon will turn to a blue 4 column vertical bargraph (for WPA connections, at least), and you are connected."

I do get this far, but then cannot get any network access anyway. Any thoughts? I have an Atheros wireless card in my Acer laptop. I installed Ubuntu 7.10 plus upgrades yesterday.

---

### Post by bred on 2008-03-05
> **gilf said:**
> If you are having problems connecting to a wireless network with NetworkManager try this:

1.) ***Boot from a LiveCD of the version of Ubuntu that you use*** (this works for Kubuntu, too). Note: You should boot from the LiveCD to eliminate any problems you may have caused by altering settings inadvertently in the network manager in a hard drive installation. This is easy to do.

2.) Click on the Networkmanager icon in the taskbar (upper right of screen in Ubuntu, lower right in Kubuntu). In Ubuntu, it should look like a small black monitor(square) with a red spot on it.

3.) After clicking on that icon,  a panel should open up showing a list of available wireless networks. These networks are displayed by name (essid) in a line with an orange horizontal bar showing relative signal strength. ***Click on the network's orange bar  line that you would like to connect to.*** If the network requires a password, a password dialog will open up and you should fill in the password to connect. (Note: **be sure to select the right type for your router's encryption method**  WPA type, WEP-128 bit, WEP-64 bit, passphrase or hex, etc). 

After you enter that password, you may be asked if you want to add the password to your keyring (Ubuntu) or Kwallet (Kubuntu). It's a good idea to do that, because it makes auto-connecting in the future easier.

With the password or passphrase entered for the wireless encryption, you should see the network icon become two small circulating dots. This indicates the password is being authenticated and a connection attempt is being made. If authentication occurs correctly the icon will turn to a blue 4 column vertical bargraph (for WPA connections, at least), and you are connected.

If you do not see any orange horizontal bar network lines when you first open network manager, there are two possibilities:

a.) There are no networks of sufficient signal strength in your area (if at home, your wifi router may be turned off). Solution: move to an area where there are networks, or turn on your router.

b.) Your network wireless card is not working with your ubuntu system. In this case you will have to delve into the requirements for your wireless card -- drivers, etc. this is covered elsewhere in wikis and documentation online.

Note: if you do see network lines and orange bar graphs when opening NetworkManager from LiveCD, it is very likely that you do have proper card drivers installed (because they are properly seeing networks and communicating to your computer), and you probably should not try to troubleshoot card drivers.

Note: if you see two **lines with the same ESSID**, Network Manager may not behave properly when trying to connect to one of them (see [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/129908](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/129908) ). 

4.) If you are able to successfully connect to a network by clicking on the particular network line you want in LiveCD mode, but you are unable to see those same networks from an installed hard drive version of Ubuntu, the most likely cause of the problem is an altered file called /etc/network/interfaces

To solve this:

a.) if you are using version 7.10 check the contents of the file against the following.



If your file doesn't look like this, you can save a backup, edit it and try it with the new contents (see editing instructions below)

b.) if the 7.10 version doesn't work, or you are using 7.04, try this file  (file contributed by user elabranche) :



If the file doesn't look like either version above, "save as" a version of your old file with a .bak extension, so you can restore it if you need to, edit the original file  and change it to one of the versions above, (copy and paste the above in place of what is there). (**new note**, *see my post below about the **ath0** device name -- yours may vary*)


Then reboot. The NetworkManager should now behave as the CD version did.
[B]
How to edit the interfaces file:[/B]



works great!
thank you!

---

### Post by sarah.love on 2008-03-05
2.) Click on the Networkmanager icon in the taskbar (upper right of screen in Ubuntu, lower right in Kubuntu). In Ubuntu, it should look like a small black monitor(square) with a red spot on it.

3.) After clicking on that icon, a panel should open up showing a list of available wireless networks. These networks are displayed by name (essid) in a line with an orange horizontal bar showing relative signal strength. Click on the network's orange bar line that you would like to connect to. If the network requires a password, a password dialog will open up and you should fill in the password to connect. (Note: be sure to select the right type for your router's encryption method WPA type, WEP-128 bit, WEP-64 bit, passphrase or hex, etc). 



I have a Dell 1505 Wireless card, and have just installed ubuntu 7.10. There is no Networkmanager icon on my taskbar that has a black screen with a red spot and there is also no list of available wireless networks.

Where should I begin, it appears that my wireless card is not even recognised!!

---

### Post by courgette18 on 2008-03-06
> **gilf said:**
> Courgette18,

Weird -- you're assigned a DHCP address, but supposedly aren't connected.

Well lets try something:

Sometimes the first time you try to connect things are messed up, or somebody with another laptop happened to be in ad hoc mode on the same network. This gets saved as a configuration -- lets just try to remove any faulty configuration that may have gotten saved.

If you type into the terminal:

gconf-editor

a configuration screen will open up.

Navigate by clicking on twisties in the left panel to 

 system>networking>wireless>networks

Do you now see in the left pane your network name listed?

If so, click on it. It will show in the right pane several configuration lines. One of them will be labeled bssids.

Double click on it and a small window will open up showing a list of one (or several) bssids (lines of 6 pairs of hex codes separated by colons) for that network

How many bssids (hex code lines) are there?

If more than one, try removing all but one of them and restarting your computer and using the connection instructions in the first post in this thread.

If that doesn't work, or there was only one to begin with, delete all of the bssids for your network, restart and try to connect.

Thanks for these ideas.  However, I've solved the problem in a different way.  My Belkin USB adapter was shown as version 1.  I also had a version 4 adapter.  I tried this and, hey presto, the connection was made straightaway.  So I'm guessing 7.10 doesn't like the v.1 chipset.  Hope this may be of use to someone else.  Thanks for your time and thoughts.

---

### Post by gilf on 2008-03-06
> **sarah.love said:**
> 2.) Click on the Networkmanager icon in the taskbar (upper right of screen in Ubuntu, lower right in Kubuntu). In Ubuntu, it should look like a small black monitor(square) with a red spot on it.

3.) After clicking on that icon, a panel should open up showing a list of available wireless networks. These networks are displayed by name (essid) in a line with an orange horizontal bar showing relative signal strength. Click on the network's orange bar line that you would like to connect to. If the network requires a password, a password dialog will open up and you should fill in the password to connect. (Note: be sure to select the right type for your router's encryption method WPA type, WEP-128 bit, WEP-64 bit, passphrase or hex, etc). 



I have a Dell 1505 Wireless card, and have just installed ubuntu 7.10. There is no Networkmanager icon on my taskbar that has a black screen with a red spot and there is also no list of available wireless networks.

Where should I begin, it appears that my wireless card is not even recognised!!

You have a driver problem. You/ve opened another thread on this.

---

### Post by gilf on 2008-03-06
> **pbags said:**
> Gilf, I'm trying to solve this wireless problem too. You say in your guide:

"With the password or passphrase entered for the wireless encryption, you should see the network icon become two small circulating dots. This indicates the password is being authenticated and a connection attempt is being made. If authentication occurs correctly the icon will turn to a blue 4 column vertical bargraph (for WPA connections, at least), and you are connected."

I do get this far, but then cannot get any network access anyway. Any thoughts? I have an Atheros wireless card in my Acer laptop. I installed Ubuntu 7.10 plus upgrades yesterday.

If you are getting the 4 blue vertical bars you're connected wirelessly. Whether you're accepted into the network or not depends on other network settings than your wireless connection.

The following all need to be set up according to the needs of your specific network: DHCP or if static adress, DNS adresses, gateway address for internet access, proxy, if any, and your browser also needs to be set up right.

In addition some open wireless providers have authentication screens to sign in on.

For all of these your ISP, or network administrator, or your router manual will need to be consulted for the specific  requirements of your network

---

### Post by gilf on 2008-03-06
> **bred said:**
> works great!
thank you!

You're welcome! Happy Ubuntuing.

---

### Post by Miljet on 2008-03-07
Thank you so very much!! I have been connecting by manual configuration for over a month until I found this post. The fix was so simple that it was scary. Thank you again gilf.

---

### Post by gilf on 2008-03-07
You're welcome Miljet! Glad it's working for you.

Network Manager's automatic operation actually works quite well.

What is badly needed is documentation.

---

### Post by Wolverine-40 on 2008-03-07
My laptop connects to the router every time with 4 bars. Firefox doesn't do anything once connected though, it times out every time I've tried to use it.

The internet connection to the router is fine (I'm writing this on my other laptop on XP), any suggestions why it doesn't work?

---

### Post by gilf on 2008-03-07
Have you set up firefox for your network?

Edit>Preferences>Advanced>Network>Settings?

Try "auto detect proxy settings" If that doesn't work switch back to direct connection

Are you using static addressing? Have you set a gateway or DNS adresses?

You also ought to try to ping your other laptop. If this works, you have really confirmed that your network is up, and this isn't a wireless problem.

To reiterate -- Inability to connect to the internet through a browser is not actually a wireless problem -- it is a general networking problem, usually a matter of setting your configurations properly. Try to check these against what your internet service provider suggests. If you own the router, you should check that you have set it up not to filter out your new computer's MAC address, etc.

---

### Post by Wolverine-40 on 2008-03-07
Hi,
I've tried the first part of your suggestion, changing the settings in Firefox didn't make any difference, still no connection to the internet. 
After that I'm a bit lost, I've no idea what DNS or pinging is, the internet connection has just worked so have had no need to do this. Can you put it in simple terms please?

---

### Post by gilf on 2008-03-07
> **Wolverine-40 said:**
> Hi,
I've tried the first part of your suggestion, changing the settings in Firefox didn't make any difference, still no connection to the internet. 
After that I'm a bit lost, I've no idea what DNS or pinging is, the internet connection has just worked so have had no need to do this. Can you put it in simple terms please?

To learn more about networks, try to look up a general article on setting up internet connections in Ubuntu -- check the wikis. It would be helpful for you to understand basic networking.

For the specifics, of getting connected right now, have you called your Internet Service Provider for instructions, yet? Or checked out the ISP support website for their how-to's? Unfortunately every network is different. eg. Some cable modems don't allow more than one local IP address -- there could be a million reasons why you aren't seeing the internet from your browser. But the first thing you need to do is check with someone who knows your internet connection requirements. That is almost always your ISP. If you don't learn those ISP-specific  requirements, nobody can help you.

---

### Post by gilf on 2008-03-09
I'm going to over simplify here, but it seems like it might be generally helpful to people totally unfamiliar with networking terms to try to explain some of them. I'll try to do it one post at a time.

DNS:

DNS refers to domain name service. A domain name server is another computer that acts like an auomated telephone book for your computer. It looks up the place you say you want to visit (let's say it's [www.google.com](www.google.com)) and gives back the actual "telephone number" (IP address) of [www.google.com's](www.google.com's) server, so you computer can "dial" it.

A current typical IP address looks something  like this: 192.168.113.220 with 4 sets of digits separated by dots. (That is in the process of changing, but for now that's al you need to know.) The largest acceptable group of 3 numbers is 255, the smallest is 0. 

The domain nameserver itself has an IP address, and your computer needs to know what that is before it can contact the nameserver to look up other internet addreses. In fact you usually give your computer two "phone numbers" for domain nameservers so that in case one is "busy" or down, the other can be contacted.

How do you know what the IP address (telephone number) of the domain servers is? Usually your ISP will provide you with that information somewhere on their support website -- or will talk you through the process of entering it over the phone. Unfortunately some ISPs are not familiar wth Ubuntu, and may not know where to enter it.

In a stock Ubuntu 7.10 installation the location for entering DNS adresses is at System>Administration>Network>DNS tab.

Some additional things to know:

1.) if you are working with a wireless notebook computer, you may want to connect to different ISPs while traveling. In this case the DNS address is usually furnished automatically, you don't enter it manually. This automatic mode of operation is usually included as part of the service for what is called  DHCP and in your Network Manager program on Ubuntu you are usually in Roaming mode in order to use it. You normally only enter DNS server numbers when you have a fixed location for your computer, and are also using static addressing for that computer. Static addressing and DHCP will be explained in another post.

2.) even if you don't travel or use a wireless computer, you may be obtaining your DNS addresses automatically -- this might be  the case in a business network maintained by a network administrator. In a managed network setting, you wouldn't be entering DNS information, of course, your admin would.

3.) you may have set up your home network with a router and set that to provide DHCP addressing. In this case the router rather than the individual client computers is usually given the two DNS numbers. Again, this would usually be provided by your ISPs support website or over the phone talking with a tech support person. That person can also explain where to put the DNS addresses -- either in the router, or your computer, or possibly in both. You should also be familiar with your router's manual -- and understand the section on entering DNS numbers, if required.

4.) if you are unable to obtain a DNS pair of addresses, or feel your lookups are slow, it is possible to use other publicly available DNS servers such as those at OpenDNS -- you can look that organization up through a Google search. 

5.) I realize this explanation is not complete, but it is just a general explanation to make the term DNS more than a collection of three letters for people new to networking. 

6.) Unless you know that you need to enter DNS numbers manually in Ubuntu, you should only do so with the help of your ISP or network administrator. For beginners, sometimes the best setup is the automatic one provided by a router and computer set to DHCP.

---

### Post by gitfiddler on 2008-03-12
gilf,

I want to add my thanks to you for this information. I spent a "lost weekend" trying to get wireless to work on an old laptop, and it turns out I was was simply using the wrong method to connect.

For the benefit of anyone searching this forum, I have a Netgear WG511T card. Ubuntu reports that it's an Atheros 5212 chipset. I disabled the restricted driver that was installed during installation of 7.10, and uninstalled madwifi. Despite that, I can connect to my wireless network by double-clicking on the network icon and choosing my network.

This is a great forum. Thanks again.

---

### Post by gilf on 2008-03-12
You're welcome gitfidler.

Often Network Manager takes the blame for what are actually a.) poor documenatation and interface for a newbie and b.) driver capability issues. 

I'm no defender of NM -- I'd use any program that gets the job done satisfactorily, and alternatives are fine with me. And I'm aware of some legitimate bugs in it, as there are in any software.

My reason for writing this thread is simply to solve a.) for folks who want to use it for whatever reason.

The strongest reason for using it, as far as I'm concerned, is that it is the standard that is shipped with Ubuntu. Personally, wherever possible, I try to keep my system standard -- there's just less to try to keep configured and updated that way, and solutions to problems I might enounter are more likely going to be available in an online search, or by people in forums with the same configuration.

That doesn't mean I don't have alternative software, where I'm not satisfied with the standard. But usually I try to get the standard working first, before complicating life and branching off into an alternative application. That way I can compare performance and justify a preference for one or the other.

 If you encounter a problem with NM, and never get it working, you don't know a.) why it didn't work (wrong usage, wrong setup, wrong driver, other network problems, etc) and even if you get an alternative working -- you may have preferred the features of the original program, but will never know what those were.

Now for some specifics re the Atheros chips -- I also have the 5212 set in a D-link DWL-G650 PCMCIA card running on a hopped up (re-processored and overclocked) Thinkpad 600e [(details)]("http://www.wimsbios.com/phpBB2/topic4046-855.html"). I've tried both the stock madwifi driver and ndiswrapper with the D-Link Win drivers.

 I found that the latter used up a LOT of my available processor time (atheros chips are very basic and require the driver to do a lot of work -- including RF output limiting). This was particularly visible when running  DVD's if wireless networking wasn't shut down. Frame rates suffered. Presumably the extra processing needed to emulate the windows NDIS environment added to the D-Link win drivers required more processing time than the more streamlined native Madwifi driver.

On the other hand, when I ran the stock Madwifi driver, performance was excellent at home, where my wireless router puts out a strong clean signal, but performance suffered when I was at work, trying to pick up a somewhat marginal ISP wireless access point -- the only one available. 

My computer can dual-boot into XP, and so I can test the same system using the stock D-link drivers without ndiswrapper. In that case wireless networking was very good and the signal strength and quality were much improved. In Ubuntu with Madwifi, the signal strength graph showed poor signal reception, and frequent dropouts.

Network Manager seems to get blamed for this kind of problem, but I would say that it is simply having a hard time staying connected (as an automatic scanning program) with the reduced sensitivity of the Madwifi driver. The ndiswrapper driver puts additional processor load on the whole wireless throughput chain, so causes different kinds of problems.

If we really want to solve wireless problems we need a deeper understanding of the root causes of those problems, rather than just making blanket generalized statements about applications being "good" or "bad"..

Network Manager works very well for me, and would undoubtedly work even better with a card that had better available drivers. So my focus is not on trying replacements for NM, but finding a card wth a good low overhead driver. This will card work better with ALL network programs.

---

### Post by bred on 2008-03-15
thx dude!
works fine on kubuntu

---

### Post by gilf on 2008-03-17
Your welcome Bred.
Happy Ubuntuing!

---

### Post by wordsmithereens on 2008-03-31
THANK YOU!

My hair turned gray and was ready to fall out trying to solve my intermittent network connectivity with wireless.  I appreciate your time and effort to clearly state a workable fix.

wordsmithereens    8)

---

### Post by gilf on 2008-03-31
Thank you, too, wordsmithereens.

Hair which turns gray and falls out over network problems is luckily reversible. Once connectivity is established, generally speaking it comes back in your natural shade.

Happy Ubuntuing!

---

### Post by Sokac on 2008-04-11
I have problem with my Dlink DWL-G510 c2. With Live 8.04 Beta works wireless just fine. After install it doesn't seen ssid, with iwlist scan too.

I tried with wicd - scan work, but cannot connect. I tried with your solution - it see ssid ask password (it's wep) - after 1 min ask again for passwd (passwd is enter correctly).

---

### Post by Lazy-buntu on 2008-04-11
I also could use some help @ [http://ubuntuforums.org/showthread.php?t=751665](http://ubuntuforums.org/showthread.php?t=751665)

---

### Post by gilf on 2008-04-11
Well, I haven't tried 8.04 Beta, so I can only say the usual things for 7.10 and 7.04. I probably won't upgrade until there's a stable version. I have enough work to do in bringing up all the hardware and software on a stable version installation.

So here's the usual advice:

Make sure that you have selected the right kind of WEP password from the dropdown list before entering the password. The list can be clicked on to change it. There are many different types of WEP password.

When you say you are able to connect through the 8.04 liveCD, but not with an installed version, is the install a brand new installation? If it's not, and you have tried various alternatives like wicd and altered settings, you may have somesystem alterations that are stopping you.

You may want to try a brand new installation, if that's possible, and immediately try out the wireless, without chaning anything.

If that doesn't work, and you can verify that it does work on the livecd, sounds like it's time to raise a bug report on 8.04 beta for the problem.

An installed version should work as well as the livecd.

---

### Post by Sokac on 2008-04-11
The installation was new and partitions was formated. It is original CD downloaded via torrent from ubuntu.com. After installation I tried connect with router but doesn't work. Key was 100% right. I had same problem in 7.10.

Now I again install 8.04. While installing, I'm connected with wlan. After install I'll try connect with router.

---

### Post by spawnywhippet on 2008-04-19
I have decided to make the leap from Windows XP to Linux instead of Vista. (I am a _total_ novice with any form of Linux or UNIX, but am very experienced with Windows and reasonably familiar with networking.)

I installed Ubuntu 7.10 on an old IBM Thinkpad T30 with an Intel 'High Rate Wireless LAN Mini PCI 802.11b' (Prism 2.5 Wavelan chipset). This works perfectly with WPA-PSK TKIP in Windows XP.  I tried the LiveCD, connected to the internet using the ethernet cable, then installed to HD.
After the install, my wireless card detected my WLAN (which uses WPA-PSK) and the neighbours WPA network but cannot connect. I am only offered WEP 64, 128k and LEAP connections, not WPA. I looked at the interfaces file, it showed just the 2 lines mentioned in the first post. I then went through the sticky on HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc. by wieman01 with no success.
Another forum suggested I needed the latest firmware and drivers, so I put an XP drive in the machine, upgraded the station firmware from 1.7.0 to 1.7.4 and downloaded a 'hostap-0.5.10' driver. I refitted the Ubuntu disk but there was no change. I have no idea how to apply the driver and test it - the documentation was totally incomprehensible to me as it was written by a Linux expert for another expert, not the novice who is most likely to need it.

Any suggestions would be appreciated, as I've spent 2 days trying to get this working and to be honest, even Vista is looking tempting at this point.

---

### Post by hbuch on 2008-04-20
Hi Gilf,

Thank you very very much for this helpful post. It worked for me!!!!

Heather Buch

---

### Post by gilf on 2008-04-20
> **spawnywhippet said:**
> 

I installed Ubuntu 7.10 on an old IBM Thinkpad T30 with an Intel 'High Rate Wireless LAN Mini PCI 802.11b' (Prism 2.5 Wavelan chipset). This works perfectly with WPA-PSK TKIP in Windows XP.  I tried the LiveCD, connected to the internet using the ethernet cable, then installed to HD.
After the install, my wireless card detected my WLAN (which uses WPA-PSK) and the neighbours WPA network but cannot connect. I am only offered WEP 64, 128k and LEAP connections, not WPA. I looked at the interfaces file, it showed just the 2 lines mentioned in the first post. I then went through the sticky on HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc. by wieman01 with no success.
Another forum suggested I needed the latest firmware and drivers, so I put an XP drive in the machine, upgraded the station firmware from 1.7.0 to 1.7.4 and downloaded a 'hostap-0.5.10' driver. I refitted the Ubuntu disk but there was no change. I have no idea how to apply the driver and test it - the documentation was totally incomprehensible to me as it was written by a Linux expert for another expert, not the novice who is most likely to need it.

Any suggestions would be appreciated, as I've spent 2 days trying to get this working and to be honest, even Vista is looking tempting at this point.

Okay first off, you are asking several questions at once and are mixing a lot of approaches and recommendations of other posts.

Proceed in order from a simple, basic, uninstalled system (LiveCD). 

First off I read above that you tried the live CD and a WIRED connection, then installed.

In the first post of this thread it outlines a method of booting up your present system using the liveCD again, to try a WIRELESS connection.  Even though you installed it to HD, boot from the liveCD, and then try to connect to your router normally. If you are unable to do that from the liveCD, using the method specified, it is most likely a driver problem. This thread is NOT oriented to resolving chipset driver problems. These are discussed in specialty locations devoted to the chipsets.

If you do have a driver problem, and you need to install drivers which you've located elsewhere, usually you can do a general search on Google for the chipset driver (search for Ubuntu + your chipset + driver) and find someone who has posted clear instructions (not necesarily here on the Ubuntu Forum)  for installing them.

But certainly make sure you actually NEED aditional drivers by following the liveCD method in this thread FIRST.

Now, an explanation for why Ubuntu and Linux may not seem to be able to handle your wireless card "as well as Windows" or automatically, out of the box.

1.) There are literally thousands of wireless cards, many of them with varying chips and internals EVEN with the same brand and model number.

2.) The manufacturer of the card writes a driver for the card for Windows or Mac OS, and optimizes the driver. Generally (though not always) they DO NOT write one for Linux. They supply these drivers to Microsoft for inclusion in late OS, as well as package it in the retail box with the card. This helps them sell cards.

3.) Because the manufacturer writes the driver and packages it with the card, even the same model card may have different chips inside, as long as a suitable driver is packaged with it. Therefore drivers are specific to card model VERSIONS or REVISIONS.

4.) Many manufacturers do not or will not supply information about their drivers to volunteer Linux developers trying to create a driver for the card. These cards must be reverse engineered, and often a driver is created with limited or fewer functions. These may or may not improve over time, depending on the currency of the card and willingness of others to volunteer research and program time to improving the drivers. Often documentation is lacking or difficult for a newbie to implement. Nevertheless help is almost always available from others in this community if you search hard enough or ask questions in the right places.

5.) The best solution is to only buy a card from a manufacturer who DOES supply Linux drivers for their cards. Then you can totally avoid all the problems, as well as be assured that the card will perform optimally. Purchasing such a card will also encourage the manufacturer in maintaining a Linux version, as well as encourage others to start including Linux drivers with their cards. Manufacturers know best how to write drivers for their own cards -- they want them to perform competitively, and they know what their designs consist of.

6.) Windows is not BETTER at handling a specific wireless device than Ubuntu. Microsoft simply relies on a custom driver from the manufacturer of the chipset or wireless device. It is in fact, not part of Windows. It's just a manufacturer's device driver which has been designed to work with Windows specifications. It may or may not be supplied with a Windows installation, or separately on CD with the card or device.

7.) So when people say "Windows worked flawlesly with my wireless card"  they are forgetting that Windows *doesn't work at all *with their card, the manufacturer's driver does. And naturally it's flawless (one hopes) since it was designed to interface the card with Windows.

I hope you find the LiveCD actually allows you to connect via WPA, and that adding a driver is unnecessary. (Also be sure to try clicking on the little twistie next to the WEP choices dropdown window -- maybe you're just not seeing the WPA choice).  If you do need to add a new driver, please find a site or someone with experience with the card to help you install it. Or best of all, if you can afford it, get a card with linux drivers and support, as well as windows drivers. Then you should find things much easier now and in the future.

---

### Post by gilf on 2008-04-20
> **hbuch said:**
> Hi Gilf,

Thank you very very much for this helpful post. It worked for me!!!!

Heather Buch

You're welcome Heather, Happy Ubuntuing!

---

### Post by tropdoug on 2008-04-24
Gilf

before I try your excellent solution, I want to clarify whether this is actually the problem.

I have recently installed gutsy onto my desktop, with great results. I also have a vista laptop, (unfortunately). Now the thing is, from my desktop I can access the vista shared files through the ad hoc network 'OurOffice'. However now that I have installed gutsy onto the laptop, I cannot access the home network the other way, using gutsy. But the wireless setup enables me to send emails, and connect (at lightning speed HOOORAY) to the internet. 

So I am a little confused, as on the one hand, I have a working wireless connection, but cannot see the home network. 

If you could advise, I would be very greatful

Thanks in advance

---

### Post by gilf on 2008-04-24
If you are connecting to the Internet and sending mail, you don't have a wireless problem. No need to use the Live CD method in the first post of this thread.

You have a normal networking problem which has nothing to do with wireless or non-wireless connection.

Since your problem is in connecting to a local Ubuntu machine from another local Ubuntu machine, the things to check are firewall settings on both machines (Firestarter, probably), and your router settings (mac address filtering, static IP, or DHCP, etc.).

If you are trying to use Samba to transfer files, you should also read up on Samba networking elsewhere in these forums.

But (from your description) you shouldn't spend time trying to troubleshoot or alter the wireless performance side of things. In fact if you do change that, you may be creating problems.

---

### Post by EamonR on 2008-04-24
Hi, I've just installed the Release of Ubuntu 8.04 today, I previously had the beta installed and at some point during use of the beta (after some update), my wireless stopped working. I thought the new release today would have fixed that but no luck. Clean install too.

I'm using a HP Compaq 6715b laptop, it had a Broadcom 4312 wireless card I believe.

The b43 driver doesnt come up under restricted drivers, I installed the fwcutter and everything manually but no luck, under dmesg there is no error I can see and under lspci the only Broadcom device is "Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)"
which obviously doesn't appear to be my wireless card.

If anyone knows what I can do with this that'd be fantastic, been without wifi for ages now :(

Oh, my blue wireless light was not on when I was inside the LiveCD either.

Apologies if this is the wrong thread but I tried to make a new thread and it said I didn't have permission :/

---

### Post by s1337m on 2008-06-21
I am an Ubuntu newbie, so please be patient...

Im on hardy 8.04 and have my card working, for the most part.  I can see all networks and can connect to just WEP and unsecured.  When I try to connect to my WPA network through NM, NM just spins around and quits.  I read in this thread that NM is often misused and not incorrect; but, when I edit the interfaces file, all wireless networks disappear from NM.  How should I proceed?

---

### Post by gilf on 2008-06-21
As I've pointed out earlier, I have not moved to 8.04 so can't advise on any specific problems with Network Manager in that version.

The first post gives suggestions for trying to connect via live cd first before doing anything else. You haven't indicated if you tried that.

I wouldn't suggest modifying the interfaces file on 8.04. The advice given was for 7.04 and 7.10.

I would find out why you can't open a new thread, fix that and then ask for help in a new thread.

---

