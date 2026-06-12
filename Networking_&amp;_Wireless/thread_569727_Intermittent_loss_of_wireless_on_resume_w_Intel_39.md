---
title: "Intermittent loss of wireless on resume w/ Intel 3945ABG (ipw3945)"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by seldomshaven on 2007-10-07
I'm seeing a problem whereby the Intel 3945ABG wireless interface in my laptop sometimes won't/can't connect to the router on resume from standby or hibernate.  I can _usually_ restore it by running:

sudo /etc/acpi/suspend.d/55-down-interfaces.sh
sudo modprobe -r ipw3945
sudo modprobe ipw3945
sudo /etc/acpi/suspend.d/62-ifup.sh

Sometimes even that doesn't work, and I have to stop /etc/init.d/networking before executing the above, and re-start it afterwards.  The wireless gets into one of two states:

- "unassociated" to the SSID, frequency = nan.  Log repeatedly tried to associated with an SSID, but it seems to fail.
- seemingly associated, but with extremely low signal strength (as displayed by the network manager applet)

As I understand it, NetworkManager detects the card the moment it's re-inserted with modprobe, so neither the ifup nor networking stuff should be necessary for it to all work, but I'm obviously mistaken, since stopping & restarting stuff seems to fix things up.  I was also under the impression that the suspend/resume scripts already remove & reinsert the ipw3945 module automatically, as stated in /etc/default/acpi-support.  And I've tried adding networking to the list of services to be stopped & restarted on suspend/hibernate in /etc/default/acpi-support

Has anyone else seen this problem, or got any idea what might be wrong?

---

### Post by bdonkey on 2007-10-25
I've got the same problem, and I've also noticed something else: some of the times that ipw3945 wireless stops working, NetworkManager starts taking up 100% cpu time.

---

### Post by kay.one on 2007-11-03
> **bdonkey said:**
> I've got the same problem, and I've also noticed something else: some of the times that ipw3945 wireless stops working, NetworkManager starts taking up 100% cpu time.

I have the same exact problem on a thinkpad with Atheros Wireless card. any idea on how to fix this.

---

### Post by cvance090685 on 2007-11-07
Add me to the camp. IPW3945 with problems after suspend/resume.

---

### Post by seldomshaven on 2007-11-08
Having upgraded my system to Gutsy, I now see the following behaviour:

1.  When the system resumes from hibernate/sleep, the wireless often doesn't work, requiring the previously described steps.
2.  When the system boots & I log in, the wireless applet sits apparently attempting to authenticate to the router, but never actually does - the system logs repeated "geography ABG detected" messages.  To actually log on to the wireless LAN, I have to log out, and back in again, at which point it all works perfectly.
[3.  On the 3rd or 4th resume from sleep, the laptop usually doesn't - just sits there with a blank screen chewing battery...]

It seems like there may be two issues here - one with the handling of keys for the wireless LAN, and one with the actual wireless drivers or NetworkManager.

Does anyone involved in Ubuntu development have any handy suggestions for how to diagnose this further?

---

### Post by jellystones on 2007-11-09
Same problems as stated above. If I put my Dell 640m/E1405 into sleep mode, then wireless will usually stop working after resuming.

Wireless card: Intel 3945abg

Fresh install of Ubuntu Gutsy Gibbon

---

### Post by Jarmer on 2007-11-24
I'm having this same exact problem.  except with me it's intermittent.  I'd say it happens about 75% of the time.  I'm using a Compaq v6000 laptop.

Resume from standy and the wireless networking tool in the panel says I'm connected, and detects the local networks, but it really isn't connected.  And when I try and disconnect or connect to a different network, nothing happens.

only solution I've found is to restart.  So it kind of makes the Suspend mode on the laptop pointless if I can't connect to the net on resume.

thank goodness ubuntu boots fast!


anyone found a solution to this?  Or if not, is it a documented problem, and being worked on?

---

### Post by palletjackracer on 2007-11-26
I have the same issue w/Intel 3945ABG.

Has anyone got a fix for this yet?

---

### Post by palletjackracer on 2007-11-27
I'm not sure if anyone is still following this thread, but I did find a workaround.  It is not automatic but it does work.

1) Before suspending turn off the wireless card from external switch.
2) Suspend.
3) Turn wireless card back on (it doesn't matter if you do this before or after you unSuspend)
4) unSuspend

If anyone has an automatic workaround for this I'd love to hear it.  Thanks.

---

### Post by slartoff on 2007-11-27
Same problem here, Intel 3945ABG on a Toshiba A105 laptop.  Frustrating.

---

### Post by THLopes on 2008-01-14
I was having this same problem on a A105-S2081, Atheros AR2413 (AR5005G), 802.11b/g. The ath_pci (madwifi) driver is intermitent sometimes, other times are good. But in almost all, intermitent or failing. After installing NDISWRAPPER driver, it's working so good! :)

---

### Post by skinnie on 2008-01-14
has anyone come with a solution for this?

---

### Post by slestak on 2008-02-07
This worked for me.

[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/66266]("https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/66266")

---

### Post by bjtuna on 2008-05-19
I have the exact same problem as the original poster on my Dell e1405/640m on Hardy (for some reason it worked okay in Gusty).  All that stuff about suspend/hibernate is may, or may not, be a separate issue but the main problem for me is the intermittent wireless. Anybody know what's going on?

---

