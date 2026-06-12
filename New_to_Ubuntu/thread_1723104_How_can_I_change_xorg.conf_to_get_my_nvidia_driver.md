---
title: "How can I change xorg.conf to get my nvidia driver running"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by JorgeABC on 2011-04-06
EDIT : the best answer I found here : [http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

I have this notebook : [http://www.asus.com/product.aspx?P_ID=Gjsm3Kp4pjz9iJM1](http://www.asus.com/product.aspx?P_ID=Gjsm3Kp4pjz9iJM1)
It has a nvidia graphic controller and a integrated intel graphic controller.
Of course, I tried to install the latest nvidia proprietary driver package in ubuntu 10.10 ... but with no good result.

Before activating the nvidia driver I generated the xorg.conf file and it look like this:

[I] Section "Device"
    Identifier  "Card0"
    BusID       "PCI:1:0:0"
    Driver    "[COLOR=Red]nv[/COLOR]"
    Option    "NoLogo"    "True"
EndSection

Section "Device"
    Identifier  "Card1"
    BusID       "PCI:0:2:0"
    Driver    "[COLOR=Red]intel[/COLOR]"
    Option    "NoLogo"    "True"
EndSection[/I]

After rebooting everything worked has usual.
Then I activated the nvidia driver and the xorg.conf file changed to:

[I]Section "Device"
    Identifier  "Card0"
    BusID       "PCI:1:0:0"
    Driver    "[COLOR=Red]nvidia[/COLOR]"
    Option    "NoLogo"    "True"
EndSection

Section "Device"
    Identifier  "Card1"
    BusID       "PCI:0:2:0"
    Driver    "[COLOR=Red]nvidia[/COLOR]"
    Option    "NoLogo"    "True"
EndSection

Then I rebooted but I got a black screen. I could hear the sound of the graphical environment but couldn't see it. Hiting Ctlr+Alt+F1 took me to the text prompt.
Then I changed the xorg.conf file to :

Section "Device"
    Identifier  "Card0"
    BusID       "PCI:1:0:0"
    Driver    "[COLOR=Red]nvidia[/COLOR]"
    Option    "NoLogo"    "True"
EndSection

Section "Device"
    Identifier  "Card1"
    BusID       "PCI:0:2:0"
    Driver    "[COLOR=Red]intel[/COLOR][/I][I]"
    Option    "NoLogo"    "True"
EndSection[/I][I]

...And rebooted. This time I got the white and pinkish ubuntu background but no loggin window. Just an empty background. What does this mean ? Does this mean that the driver isn't suitabel for my controller?

btw I get this warning during booting :

[/I]fb: conflicting fb hw usage intel drmfb vs VESA VGA -removing gen[I]eric driver

Thanks for the attention,
Jorge
[/I]

---

### Post by cbowman57 on 2011-04-06
Can't help you exactly but if you delete your xorg.conf you should at least be able to get back to the desktop.

sudo rm /etc/X11/xorg.conf

---

### Post by JorgeABC on 2011-04-06
Thanks cbowman57

Just installed the nouveau nvidia driver ... worked fine ... but it isn't what I want.

---

### Post by SeijiSensei on 2011-04-06
Search the forums for "optimus nvidia".  You *might* be able to do what you want, but it depends on which generation of Optimus your machine has.

---

### Post by BicyclerBoy on 2011-04-06
Your laptop has a form of optimus.
This do not have any nvidia support in linux.
Your nvidia GPU is a not listed as supported in the driver notes but it is a re-badged 435M which is/was supported. (I think)

[http://ubuntuforums.org/showthread.php?t=1691979](http://ubuntuforums.org/showthread.php?t=1691979)

check out vga_switcheroo

[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)
[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)

Other people seem to have got your model laptop working with vga_switcheroo.
This prog allows you to get the power saving & performance with manual switching.

I do not know if you need to load intel & nvidia GPU drivers to just use the nvidia, you may as the nvidia GPU writes into the intel framebuffer to output..(depends on h/w arrangement AFAIK).

The vga_switcheroo users will have all the answers (& more questions)..
Looks like kernel support for this switching is available 2.6.35 on..

---

### Post by beew on 2011-04-06
> **BicyclerBoy said:**
> Your laptop has a form of optimus.
This do not have any nvidia support in linux...

Other people seem to have got your model laptop working with vga_switcheroo.
This prog allows you to get the power saving & performance with manual switching.

.

I think by "working" they mean turning on the Nvidia card and use the Nouveau driver. If that is the case that would be better than nothing but not really "working" as nouveau can only access basic functionalities of the card. In fact I am not sure if using nouveau driver would be better than just turning off the Nvidia card (an expensive paper weight it would become, but at least doesn't drain the laptop's resource) and use the Intel card exclusively.

In the meantime OP can add his voice to the chorus.
[http://ubuntuforums.org/showthread.php?t=1712278](http://ubuntuforums.org/showthread.php?t=1712278)

I don't think Nvidia would support Optimus for Linux, but it shouldn't be too much to ask them to provide a way to just use their video cards which the users paid for, and Nvidia 'supports' with Linux drivers.

---

### Post by BicyclerBoy on 2011-04-06
> I think by "working" they mean turning on the Nvidia card and use the Nouveau driver.

I think you are right..the successful vga_switcheroo users seem to be ATI/intel or using nouveau with nvidia/intel.
I don't blame nvidia for this mess..

Depending on the optimus h/w arrangement in the laptop..The OP may be able to switch GPU in BIOS & run the nvidia discrete graphics only..(or the intel IGP only).

The "better" designed laptops/netbooks have provided a BIOS controlled mux that can bypass the intel IGP completely.

---

### Post by beew on 2011-04-07
> **BicyclerBoy said:**
> 
The "better" designed laptops/netbooks have provided a BIOS controlled mux that can bypass the intel IGP completely.

Unfortunately it is hard to find laptops that have the BIOS mux. The only ones I know are the Thinkpads (there are probably others, there should probably a sticky for a list in the general support forum). Meanwhile the morons at DELL actually went out of their way to remove the mux from the BIOS in their "upgrade".

---

### Post by JorgeABC on 2011-04-07
Thank you guys, now I have a bit of information to chew on, "optimus" being the key word.

---

### Post by beew on 2011-04-07
@OP

You may want to check out this thread.  Only works for his laptop but it is an Asus, so may be you can get some useful insight or feedback from the guy.

[http://ubuntuforums.org/showthread.php?t=1677780](http://ubuntuforums.org/showthread.php?t=1677780)

---

