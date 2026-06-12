---
title: "Wired and wireless both non-functional on Averatec 3250 laptop"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by JordanW on 2007-11-10
All,

I have an Averatec 3250 laptop (circa 2004) with the RT2500 wireless chipset that I would like to get working as a stand-along Ubuntu machine, but I'm having serious problems.

[LIST]
[*]With Ubuntu Edgy, "wired" networking worked just fine. With Gutsy, it no longer works at all. I cannot load webpages or access the network. (I never got Feisty to successfully install on my machine -- it would lock up during installation.)
[*]Wireless networking does not work for me. I followed the HOWTO for the RT2500 chipset to get drivers going using ndiswrapper, but can now only "see" my wireless network -- not actually get a network connection through it. (The wireless connection works fine under Windows on another partition of the HD. In addition, the Windows install sees other "neighbourhood" wireless networks that Ubuntu does not.)
[/LIST]

The lack of a regular "wired" connection makes sorting things out difficult (I am typing this on my Windows machine) but would appreciate *step-by-step* help from the community to get this otherwise great OS working on my laptop.

Thanks in advance!

---

### Post by visentini on 2007-11-11
I have the same notebook and  the same problem :( !!! I can´t find any solution on the internet...please some one help us!!!:)

---

### Post by salefish on 2007-11-11
I have the same laptop and have the same problem. 

I believe i can solve your wired issue, at least this is how I did it.

Go to Accessories and open the Terminal then enter

[PHP]gksudo gedit /boot/grub/menu.lst[/PHP] 

enter your password. In the page that pops up add **acpi=noirq** to the following string, near the bottom of the page.

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a87de7c0-5109-4808-87e6-2676e4a0e894 ro **acpi=noirq** quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

hit save and reboot
I had to go to network and uncheck roaming, and add dhcp, but that is just my personal settings

As far as how to get the wireless working. I have no clue, If you find out please let me know. I have attempted to use the ra2500 Linux module from serial monkey and ndiswrapper with no luck. I am certain it is because of my inexperience with Linux. If you do figure it out let me know. Speak slowly and use small words when explaining it to me though, I am very new to Ubuntu.

---

### Post by JordanW on 2007-11-11
**salefish**, your fix for the wired network was spot-on. Thanks. Do you get the same behaviour with your wireless setup? (i.e. can see the networks, but can't connect?)

Anyone care to help us with the wireless network?

---

### Post by Bushido89 on 2007-11-11
> **JordanW said:**
> 
Wireless networking does not work for me. I followed the HOWTO for the RT2500 chipset to get drivers going using ndiswrapper, but can now only "see" my wireless network -- not actually get a network connection through it. (The wireless connection works fine under Windows on another partition of the HD. In addition, the Windows install sees other "neighbourhood" wireless networks that Ubuntu does not.)


I've got the same problem, I'm inclined to blame the APs (The ISP supplying them at my university is imfamous for unreliability), but I can't rule out that in my n00bishness I might have done something wrong.

---

### Post by salefish on 2007-11-14
Well, sometimes I can see them and sometime not. I have no idea why it is on and off again though.

---

### Post by seachnasaigh on 2007-11-14
I've had on again-off again responses from my wireless network locally through Ubuntu.
I do not have your hardware setup; mine is quite different. </caveat>

Some things I don't know about your wireless setup:
Is your SSID broadcast? (mine is not, for security reasons)
If not, like mine, you won't automatically "see" it under Ubuntu or any other OS. You have to set it up manually under your wireless config.
Do you have WEP or WPA encryption set up for your wireless network? (you should! and if you do, you will need to go under the network setups for Ubuntu and enter your WEP or WPA encryption keys; Ubuntu will (quite sanely) not automatically prompt you for this.)

I've had to manually instruct Gutsy several times in a row how to connect to my wireless network. After making major changes under Gnome I've also had to open a terminal and [/etc/init.d/network restart] to get it to accept the changes (you'll need to prepend "sudo" for that in Ubuntu!). 

--ckr

---

### Post by kazib on 2007-11-15
God it's good to know that other people have the exact same problem I have.   I'm not a complete noob (maybe a semi-noob),  but I have been living without wireless on this laptop for a long time now.

---

### Post by HeavyP on 2007-11-15
I also have a similar problem

When I freshly installed Gusty it shows that my wireless driver is not supported by Ubuntu community or so....

So, it kind 'of downloading a substitute driver which is very spectacular for me. [Since I have never experience any OS that correct all the driver problems by itself]

Any how, I can't put my laptop to hibernate because it won't re-register my wireless adapter again.

And sometimes I have to restart my computer to let the OS detect my wireless adapter.

Is there a way to fix this? [Mine works but just usually, how to make it always?]

---

### Post by JordanW on 2007-11-17
My SSID is broadcast. Windows machines with wireless access see my network. It is protected with WPA, but even when I turn off WPA, I can't connect. 

Any step-by-step instructions for diagnosing these network problems?

---

### Post by JordanW on 2007-12-02
Anyone able to help us through this?

---

### Post by salefish on 2007-12-02
Jordan can you see your network in the graphical interface?

---

### Post by JordanW on 2007-12-04
I've uninstalled the graphical interface (trying to follow the recommendations of a different thread, didn't help at all) but before I did, I could *intermittently* see my network. However, I couldn't see more than one or two of the ~6 other networks in my neighbourhood that show up nice and clear under WinXP.

---

### Post by wezlo on 2007-12-12
reinstall NetworkManager and then go in to "/etc/network/interfaces" and see if your wireless card is manually configured at all (mine is ra0).  If so, comment out those lines and restart network manager.  This is what finally got wireless working.  The "problem" is that the drivers for the rt25xx drivers are part of the kernel now and are able to work with network manager - so a lot of the old hacks won't work anymore.

---

### Post by salefish on 2007-12-13
Thanks for the heads up on the update. I have been working a lot and haven't had time to work on this issue.
If you are still wondering how to make it automatically reconnect when you reboot or hibernate I know how to do that.

---

### Post by salefish on 2007-12-14
Well that didn't work for me
I'm going to give it a serious effort today

---

### Post by JordanW on 2007-12-15
> **wezlo said:**
> reinstall NetworkManager and then go in to "/etc/network/interfaces" and see if your wireless card is manually configured at all (mine is ra0).  If so, comment out those lines and restart network manager.  This is what finally got wireless working.  The "problem" is that the drivers for the rt25xx drivers are part of the kernel now and are able to work with network manager - so a lot of the old hacks won't work anymore.

OK, this worked! Thanks **wezlo** for this tip. I'm now typing on my Averatec through a wireless connection. Amazing that the solution was so simple all this time.

The only remaining issues now are the weird behaviour on hibernation and standby -- but that's not an insurmountable problem.

Thanks again for your help.

---

### Post by agentbob88 on 2007-12-30
Thank you for the tip on how to get wired internet working. I just install ubuntu (1st time user) on my 3250, but I'm still not sure to get the wireless card to work. i have this setting when i open  up interfaces (/etc/network)

> auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0

any help would be greatly appreciated.

---

### Post by penguinv on 2008-01-14
I have an Averatec 3255 laptop.

I put in the liveCD and found where it said "wireless network" but it didn't see the local network that I wanted to sign in on or the others in the area. I tried putting in ours, a WEP network, but no go.

I have installed nothing special.

If Ubuntu is not going to be show me the active networks in the area I will lose my interest in Ubuntu on the laptop.

-------------------------------
My thread on partitioning my hard drive for ubuntu is Not Solved.

---

### Post by chestersimpson on 2008-02-06
The **acpi=noirq** change fixed my problem with wireless and wired comms.
Thanks.
:)

---

