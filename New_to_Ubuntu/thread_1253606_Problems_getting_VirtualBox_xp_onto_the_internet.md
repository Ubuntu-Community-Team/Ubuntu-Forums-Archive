---
title: "Problems getting VirtualBox xp onto the internet"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by hnarwan on 2009-08-30
Hi All,

I'm running VirtualBox OSE on Ubuntu Jaunty.

I've installed XP on virtualbox but cant connect to the internet from that image.

The ethernet card doesnt have drivers installed but i'm unsure how to fix this.

I went onto the Sony Vaio website, got ethernet drivers, burnt them on CD which i could access from the xp image but i'm unable to install them.

Either the drivers are bad ([http://support.vaio.sony.eu/computing/vaio/downloads/info/info.aspx?l=en_GB&url=Vaio/Original/Ethernet%20Driver%20Marvell_10.57%20VF_10.57.3.3.zip&m=VGN-NS20E_S&ip=Preinstalled_Drivers.htm](http://support.vaio.sony.eu/computing/vaio/downloads/info/info.aspx?l=en_GB&url=Vaio/Original/Ethernet%20Driver%20Marvell_10.57%20VF_10.57.3.3.zip&m=VGN-NS20E_S&ip=Preinstalled_Drivers.htm)) or i'm doing completely the wrong thing.

Any ideas would be welcome.

thanks
Hardeep

---

### Post by Copernicus1234 on 2009-08-30
Sounds like you are doing what you should. What does the control panel / System show for your network card? Any errors?

---

### Post by NoaHall on 2009-08-30
Under Virtual Box, you don't need to install any drivers. It uses a interface between the parts in the Host and the Guest. Try "instaling guest additions" which is somewhere on the top menu when you are running a VM.

Also, click on settings when it isn't running and make sure that "enable internet access" is choosen.

---

### Post by hnarwan on 2009-08-30
Hi Copernicus1234, 

I've attached a screenshot of the problems in Device manager, i'm not sure if that's what you were after?

I'm unable to create any network connections as there's a problem with the hardware, i'm just stuck with these drivers. I guess that's the issue?

The drivers from Sony for this laptop dont look right, the folder i downloaded (from the link in my original post) only contain .info, .cat, .inf and .sys files. 

I was hoping for an .exe i could run, i tried to point device manager to that cd (containing all the drivers for this laptop on the Sony website) - it doenst find anything.

Not sure where else to go from here...

---

### Post by NoaHall on 2009-08-30
Like i said, you do not need to install the drivers! Go to machine or devices, and click install guest additions! Make sure under the settings menu of the start up screen of Virtual Box that internet access is accepted! Do not install the drivers! They won't get you anywhere

---

### Post by Ichtyandr on 2009-08-30
And also make sure to install the "guest additions" as an Administrator under XP guest

---

### Post by hnarwan on 2009-08-30
thanks guys.

I've installed 'installing guest additions' but i cant find 'internet access is accepted' in settings while the image is stopped.

installing guest additions alone didnt fix the issue, i'm still unable to access the internet, the ethernet card still doesnt have drivesrs installed.

thanks for the help fellas.

---

### Post by whitethorn on 2009-08-30
hi,  I'm not quite sure this is the same because I don't use the OSE version, I have a version from the VirtualBox webpage, you need to click on settings when xp is off then go to the network tab and tick activate Network Adapter.  Then you can choose a certain mode for it, then you need to choose a certain type, on mine it has a list called Attached to   I choose bridged network.  Then try starting xp again, because you have the OSE version you might also need to set up a bridge in ubuntu so you can connect to it from virtual box.

---

### Post by earthpigg on 2009-08-30
most people that are serious about using VMs end up using the proprietary version of vbox from virtualbox.org and not the OSE (Open Source Edition).

this, of course, is how Sun makes its money off of vbox -- giving away a handicapped 'open source edition', giving the proprietary version away to home users (minus the 4 fundamental software freedoms), and selling it to business users.

---

### Post by hnarwan on 2009-08-30
Hi guys,

I've attached the options i get with Virtualbox OSE. I've played around with adding additional ethernet adapters, NAT, Host only etc but i cant seem to make any difference to the image in terms of accessing the internet.

Ideally i needed to run xp on this ubuntu install and access the internet + my local network, are we saying i need to buy the full version of Virtual box to do that?

I assume there's a way to get this working on the OSE version, if the full version gives me additional benefits (which i cant think of right now) i may do it anyway.

At work i use VMware, if i'm paying would it be best to install that instead? Sorry to change the subject of this thread but if i cant get Virtualbox OSE working then i'd be interested to know which virtualization software to pay for.

---

### Post by NoaHall on 2009-08-30
No, you don't need to pay for it, it's free, just download it from the official site. Version 3 is the latest.

---

### Post by whitethorn on 2009-08-30
Here have a look at this page it explains the differences between the OSE and the closed source version of virtualbox

[http://www.virtualbox.org/wiki/VirtualBox_PUEL](http://www.virtualbox.org/wiki/VirtualBox_PUEL)

---

### Post by hnarwan on 2009-08-31
thanks guys, i just installed it from [http://download.virtualbox.org/virtualbox/3.0.4/virtualbox-3.0_3.0.4-50677_Ubuntu_jaunty_i386.deb](http://download.virtualbox.org/virtualbox/3.0.4/virtualbox-3.0_3.0.4-50677_Ubuntu_jaunty_i386.deb) but i still dont see any new settings for internet access in the vm. 

Can someone point me in the right direction?

---

### Post by The Cog on 2009-08-31
What version of XP are you trying to install? I ask because I have never had any problem installing XP2 into virtualbox. But now that MS wants to get into the VM market, I wonder if they have doctored XP SP3 to make sure it doesn't work in their competitors VMs.

So things to try, are:
* Try emulating different adapter types in the VB network settings
* Try XP SP2 if you're on a later version now.

---

### Post by hnarwan on 2009-08-31
thanks, yes its SP3, i'll give SP2 a shot and play around with the Network adapter settings (NAT etc) to see if that helps.

I'll report back when that's done, if anyone has any other ideas i'm all ears.

---

### Post by niteshifter on 2009-08-31
Hi,

There's no problem with XP SP3 in Virtualbox, I've been using it for about a year now, with the same virtual adpater you show in the screenshots. The Virtualbox forums are pretty quiet on the subject of XP SP3 also.

Are you attempting to use the VM you started out with, the one you installed drivers for? If so, delete that VM and install XP again.

---

### Post by hnarwan on 2009-09-17
thanks, i've tried again but the same thing happens. Not sure why it's not installing the network adapters?

---

### Post by pricetech on 2009-09-17
XP SP3 works for me also.  Mine just plain worked from the very beginning.

---

### Post by corncob on 2009-09-17
> **pricetech said:**
> XP SP3 works for me also.  Mine just plain worked from the very beginning.

ditto.  I did go through that connect-to-the-Internet thing that came up when I first installed XP.

---

### Post by hnarwan on 2009-09-18
that would have been nice....and i'm a good person so it should have happened for me also.

the problem is my network hardware isnt installed and i dont know how to do it...any ideas?

---

### Post by hnarwan on 2009-09-20
Hi Guys,

Any ideas on this one? I'm completely stuck with trying to get this xp image to see the outside world. 

It's the damn ethernet controller that's the problem but i dont know how to fix it.

---

