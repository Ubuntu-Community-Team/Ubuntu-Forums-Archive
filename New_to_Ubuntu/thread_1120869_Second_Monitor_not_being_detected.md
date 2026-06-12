---
title: "Second Monitor not being detected"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by suomalainen on 2009-04-09
Ubunteros,

I'm running 8.04LTS 64 bit and want to set up dual monitors. I'm getting the following message as stated in the attached picture.

I don't understand why the display isn't being seen/detected. I have it turned on and even swapped cables to see if that was the issue. All to no avail.

Any one have any good suggestions???

Thanks!

---

### Post by PreviousN on 2009-04-09
First of all, what kind of graphics card to you have? Do you have the drivers for it installed?

---

### Post by mdsmedia on 2009-04-09
This might seem a little obvious, and I've had little experience with dual monitors, but do you have a card which supports dual monitors?

---

### Post by suomalainen on 2009-04-09
Hello PreviousN,

I have a EVGA 256-P2-N761-TR GeForce 8600 GTS 256MB 128-bit GDDR3 PCI Express x16 HDCP Ready SLI Supported Video Card - Retail

I installed EnvyNG and then the drivers for it.

What next???

Thanks

---

### Post by PreviousN on 2009-04-09
Good job! You're halfway there!

press alt+f2 and type "nvidia-settings" then hit enter. You should be greeted by a beautiful nvidia settings configurator. A link to this manager lives *somewhere* in the Applications/Systems menu. I'm currently away from my nvidia computer so I don't remember where. 

Anyways, once you open it up, you'll be able to configure dual displays through a simple click of your mouse!

Edit: it lives in Applications--> System tools --> Nvidia settings

---

### Post by TheBuzzSaw on 2009-04-09
To make it permanent, you should run **sudo nvidia-settings** and then click the **Save to X Configuration File** after setting everything up how you'd like it.

If for some odd reason you don't have nvidia-settings (this happened to me once despite having the Nvidia drivers and everything), you should be able to just add it using the package manager.

---

### Post by Hospadar on 2009-04-09
If you want to make the settings in nvidia-settings permanent, you'll need to run it as "gksu nvidia-settings" and then click the "save to xorg.conf" (I think it's called) button at the bottom of the window where you configure your dual monitors.

---

### Post by suomalainen on 2009-04-09
Hello Again!

I don't know what the deal is here???? If I set things  up using the "Twin View" option, this only increases the desktop amongst two separate screens/displays...

I'd like to have two desktops separate to each display. It doesn't look nice when I open a word file and it is divided between two monitors.

Is this possible?

---

### Post by TheBuzzSaw on 2009-04-09
> **suomalainen said:**
> Hello Again!

I don't know what the deal is here???? If I set things  up using the "Twin View" option, this only increases the desktop amongst two separate screens/displays...

I'd like to have two desktops separate to each display. It doesn't look nice when I open a word file and it is divided between two monitors.

Is this possible?
I had that problem for a while. Try this.

For your left monitor, set the Position to +0+0, and check off **Make this the primary display for the X screen**. For the right monitor, set the position to **Right of**, and choose the left monitor in the next box. Click Apply. Then click **Save to X Configuration File**. It may still misbehave; simply do a soft reboot at this point: CTRL+ALT+BACKSPACE. Lemme know how that works out.

---

### Post by suomalainen on 2009-04-09
Hello Ubunteros!

Attached is a pic from both settings of both displays. The situation where I stand now is that I have two displays which present the exact same real time information simultaneously.

I may have misunderstood so I'd like to ask the question again but:

Is it impossible to have two separate desktops/work spaces in Ubuntu 8.04LTS???????

I want to be able to gather data via the internet through one monitor and use a speadsheet to enter it in another monitor....

Perhaps I'm expecting too much????

Thank You!

---

### Post by Jakey_TheSnake on 2009-04-09
Turning some kind of "Mirror Screen" or "Clone Screen" option off would fix that, surely?

What's under "Advanced?"

---

### Post by suomalainen on 2009-04-09
Yes Jakey_TheSnake this is real strange such features as you noted do not exist in NVIDIA X Server Settings. They do in screen resolution but it is left unchecked.

Do you have NVIDIA X Server Settings? Where exactly is the option you are speaking about?

---

### Post by suomalainen on 2009-04-09
Does anyone know if dual monitor/display is possible while each has own deaktop???

---

### Post by PreviousN on 2009-06-12
I hear it is possible, but not easy. I would just not even try, it doesn't seem worth the headache. 

But you can go ahead if you want!

---

