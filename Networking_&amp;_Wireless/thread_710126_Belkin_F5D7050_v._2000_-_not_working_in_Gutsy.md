---
title: "Belkin F5D7050 v. 2000 - not working in Gutsy"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by BigMike007 on 2008-02-28
Hi,

Seen loads of posts regarding this USB adaper, but mainly seem to mention v. 3000 and 4000, not my 2000...

The moe I read, the more confused I get in terms of trying different solutions.. I'm newbie at this so simplistic help is needed if possible!!

Many thanks in advance,

BM

---

### Post by jhetrick62 on 2008-02-28
Just install ndiswrapper, build the driver from the WinXP driver and blacklist your current driver.

Follow this link,
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

Jeff

---

### Post by james_vanb on 2008-02-28
If you have the install cd, the following worked for me.  If you open the install cd and navigate to the drivers under xp and they are not the rt73, then replace as necessary in your commands:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands (If not using Xubuntu, substitute commands as appropriate):

sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb

I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (My default is mousepad) as follows:

sudo mousepad /etc/modprobe.d/blacklist

add rt2500usb and rt73usb to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".
Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following :

sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf

Insert the wireless adapter.

Now issue the following commands:

sudo depmod -a
sudo modprobe ndiswrapper

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows:

sudo mousepad /etc/modules

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

sudo ndiswrapper -m

Reboot

You should now have a connection. Roaming mode works sporadically, so I manually configure. Left click on the network manager at the upper right corner and enter manual configuration. Open wifi properties. Untick "enable roaming". Next to Network name, you should be able to click on the arrow and a drop down will show available networks, click on yours. Set Password type to WPA personal. Set Configuration to Automatic configuration (DHCP). I don't use WEP yet, but if you do, you may have to enter your password in Network password.

---

### Post by BigMike007 on 2008-02-28
james_vanb,

Many thanks for your post - your instructions worked a treat! :)

Big Mike007

---

### Post by BigMike007 on 2008-02-28
and thanks also to you jhetrick62 for the same solution!

---

### Post by james_vanb on 2008-02-28
My congratulations!!

Glad it worked for you.

---

### Post by jhetrick62 on 2008-02-28
Glad it worked.  

I hate to say this as I truly LOVE running Linux and pretty much only run Winblows on my work issued laptop, BUT, wireless support in Linux is very hit and miss.  Many, many of the posts on here asking for wireless advice, truly need to just blacklist the linux driver and run Ndiswrapper built modules as it is far less painful than all of the futile attempts to get linux drivers to work.

Now this doesn't help us much as a community with development, but it is far less painful for your average  non-power user.

Goodluck,
Jeff

---

### Post by Prefix100 on 2008-02-29
Are these the same for Ubuntu?

and what are the different commands then?

---

### Post by james_vanb on 2008-02-29
Should be the same comands.  However, your text editor may be different.  (xubuntu uses mousepad).  Replace as appropriate in commands.

---

