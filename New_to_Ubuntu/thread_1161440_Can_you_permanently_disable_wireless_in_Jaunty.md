---
title: "Can you permanently disable wireless in Jaunty?"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by RedMartin on 2009-05-16
PC: Acer Aspire 5920G

I use a wired connection at home and with 8.04 and 8.10 I could switch my wireless connection off with the button and it would remain off for all time. 

Now that I've upgraded to 9.04 it comes on every time I reboot.

I can't see any BIOS options to switch it on/off. How do I stop it from activating?

Thanks

---

### Post by RedMartin on 2009-05-18
Anyone?

---

### Post by Don1500 on 2009-05-18
I know there is a way, but I need my home computer to think in Ubuntu. Right now I'm in Windows and don't remember the way to do it. But look in System > Preferences, it should be there. 
Or...right click on the icon in the upper right (the one for your connection) select preferences and see if it's there. Keep playing, when you find it you'll never forget where it is.

---

### Post by jrox717 on 2009-05-18
Try rightclicking on the connection notification icon in the right part of the upper panel and uncheck 'enable wireless'?

---

### Post by RedMartin on 2009-05-19
I can do both of those suggestion no problem. What I'm after is a way of setting Ubuntu so that wireless isn't active EVERY time I boot.

In 8.04 and 8.10 once it was off it stayed off no matter how many times I rebooted or even unplugged my laptop. 

Vista *spit* doesn't activate the wireless when I boot. It's like it realise that I'm on a wired connection and that I originally (some months ago) switched the wireless off.

How do I get Ubuntu 9.04 to do the same?

---

### Post by billgoldberg on 2009-05-19
> **RedMartin said:**
> PC: Acer Aspire 5920G

I use a wired connection at home and with 8.04 and 8.10 I could switch my wireless connection off with the button and it would remain off for all time. 

Now that I've upgraded to 9.04 it comes on every time I reboot.

I can't see any BIOS options to switch it on/off. How do I stop it from activating?

Thanks

I would be very surprised if there isn't a bios option to do this.

---

### Post by 101011010010 on 2009-05-19
Have you tried this thread, it might help.[http://ubuntuforums.org/showthread.php?t=1114473&highlight=disable+pan0 ]("http://ubuntuforums.org/showthread.php?t=1114473&highlight=disable+pan0")

---

### Post by Didius Falco on 2009-05-19
Hi,

I'm looking through other threads that are about getting wireless to work, but I *may* have figured out a way to disable it.

Open a Terminal and type ```
sudo lshw -C network
```Look through the output for the module that controls your wireless and blacklist that module by typing ```
gksudo gedit /etc/modprobe.d/blacklist.conf
```and adding it to the bottom of the list.

On Edit: be sure and do it in this format: blacklist modulename. I'd also add a comment above it, so it'd look something like this:

```
#Die, wireless, die!!
blacklist modulename
``` <G>

Before doing that, I'd recommend doing ```
sudo cp /etc/modprobe.d/blacklist.conf /etc/modprobe.d/blacklist.conf.backup
```So if it gives you a problem, it'll be easy to reverse.

No guarantees with this, mind you - I don't use wireless. I've blacklisted other modules though, and it has worked fine for me.

I hope this helps...

Regards,

Didius

---

### Post by RedMartin on 2009-05-19
> **billgoldberg said:**
> I would be very surprised if there isn't a bios option to do this.

I only seem to have options for security, boot device order and a bunch of hdd options.

I'm not missing some hidden BIOS thing am I? I press F2 and that's it.

---

### Post by Old_Grey_Wolf on 2009-05-19
Try right clicking the Internet icon on the panel. Select "Edit Connections...", then select the "Wireless" tab. Select the network in the list, select "Edit". There should be a check box were you can deselect "Connect automatically". Select "Apply".

---

### Post by RedMartin on 2009-05-20
That didn't do anything. There are no wireless connections for it to find. I just want to be able to turn the damn card off permanently. 

I tried another hdd with 8.10 on it. It booted and the card was off. No light etc etc. This despite the fact that I hadn't used 8.10 for several days.

Put my 9.04 drive back in, booted and the light/card came back on. So, to my admittedly limited mind, that means there is some kind of persistent software switch in Intrepid (and Hardy) that is missing in Jaunty.

---

### Post by jama999 on 2009-06-01
> **RedMartin said:**
> That didn't do anything. There are no wireless connections for it to find. I just want to be able to turn the damn card off permanently. 

I tried another hdd with 8.10 on it. It booted and the card was off. No light etc etc. This despite the fact that I hadn't used 8.10 for several days.

Put my 9.04 drive back in, booted and the light/card came back on. So, to my admittedly limited mind, that means there is some kind of persistent software switch in Intrepid (and Hardy) that is missing in Jaunty.

Having the exact same problem here.  I have tried blacklisting (didnt work) - and there is no option in the network settings properties for wireless at all.  My light just comes on and sits there and blinks forever.  I can disable it per session like the OP said, but thats about all.

This CAN'T be that hard - Anyone?  Bump...

J

---

### Post by Old_Grey_Wolf on 2009-06-01
The people that have replied are users just like you are. They are not paid support from a help desk. They tried to understand your problem, and offered suggestions. 

Could you explain why you are concerned with having an wireless card scanning for a network, even though it is not allowed to connect automatically, is a problem. With additional information someone may be able to help.

---

### Post by lswb on 2009-06-01
If you can identify what driver module is loaded for your card, you may be able to find a boot-time option for it that will start with the card off. For instance, my laptop has an Intel Pro Wireless 2200bg wireless card, which uses the module "ipw2200" In a terminal I can type the command "modinfo ipw2200" and in the output of the command one line is

parm:           disable:manually disable the radio (default 0 [radio on]) (int)

My laptop does remember it's last power on/off setting accross reboots, but if it didn't and I wanted it to always be off when the system boots, I would add this line to the file /etc/modprobe.d/options

options ipw2200 disable=1

You could put this line in a separate file if you like and name it anything you want; all the /etc/modprobe.d/* files are processed at boot.

---

### Post by jama999 on 2009-06-01
> **lswb said:**
> If you can identify what driver module is loaded for your card, you may be able to find a boot-time option for it that will start with the card off. For instance, my laptop has an Intel Pro Wireless 2200bg wireless card, which uses the module "ipw2200" In a terminal I can type the command "modinfo ipw2200" and in the output of the command one line is

parm:           disable:manually disable the radio (default 0 [radio on]) (int)

My laptop does remember it's last power on/off setting accross reboots, but if it didn't and I wanted it to always be off when the system boots, I would add this line to the file /etc/modprobe.d/options

options ipw2200 disable=1

You could put this line in a separate file if you like and name it anything you want; all the /etc/modprobe.d/* files are processed at boot.

This actually worked.  Thanks for the help.

---

### Post by Percolator on 2009-06-13
That didn't work for me :(

The fact that Jaunty changes my Asus Eee bios setting from inactive WLAN to active WLAN and not being able to avoid this was so frustrating I gave up on installing Jaunty. That, the 60 second countdown screen on exit and not being able to have a simple password with passwd that is. Other annoyances I had yet to discover. Back to Intrepid :|

---

