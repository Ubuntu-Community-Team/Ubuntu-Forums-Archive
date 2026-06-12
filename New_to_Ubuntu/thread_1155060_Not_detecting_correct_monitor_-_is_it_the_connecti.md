---
title: "Not detecting correct monitor - is it the connection??"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by jeepfreak2002 on 2009-05-10
Hello all.  Here are my 2 system:

Shuttle XPC Glamor PC's:

Athlon 64
nForce 4 integrated video
Viewsonic 18" Flat Screen

Athlon 64
nVidia GeForce 8600GT
Viewsonic 18" Flat Screen

I have the restricted drivers installed on the box with the 8600GT.  The card is detected perfectly, but the display is being detected as a CRT monitor limiting the resolution to 1024x768  (THE CORRECT RESOLUTION

On the integrated video box, the restricted drivers push the resoultion out of range, so I am settling for the generic drivers at an 800x600 resolution, again - on the "CRT display"

They are plugged in via an analog VGA cable.  Is it at all possible that a DVI cable would improve the ability of the system to detect the correct display???  I am running an Intel Core 2 Dou system with integrated video on another Shuttle system, and old 17" Mitsubishi LCD's on that system and the displays are detected perfectly. 

NOTE:  I do not want to edit the xorg.conf file, I want this to be displayed correctly out of the box.  I am ordering a cheap 8600GT for the one box that is using the integrated graphics, and I ordered 2 DVI cables to see if the digital connection improves the system's ability to detect the correct display, but other than that I have no other ideas...

Thanks,

Jeepfreak

---

### Post by presence1960 on 2009-05-10
I have a Nvidia 8600GT and an Acer 19" WS. System > Preferences > Display does not work properly. I have to use System > Administration > Nvidia X Server Settings to have my monitor properly detected. Hope this works in your case.

---

### Post by jeepfreak2002 on 2009-05-10
nope.  I knew to use the nVidia settings, and it refuses to detect the correct monitor.

---

### Post by presence1960 on 2009-05-10
sorry jeepfreak2002, i had similar problem and that fixed it. Even till today the System > Preferences > Display does not detect my monitor properly. I have to use the nvidia-settings. Hopefully someone will come alonng who knows a solution.

---

### Post by jeepfreak2002 on 2009-05-10
> **presence1960 said:**
> sorry jeepfreak2002, i had similar problem and that fixed it. Even till today the System > Preferences > Display does not detect my monitor properly. I have to use the nvidia-settings. Hopefully someone will come alonng who knows a solution.

yeah... that is why I'm thinking that a new DVI cable might resolve things....  we'll see.  It is a plug and play monitor...

---

### Post by CatKiller on 2009-05-10
> **jeepfreak2002 said:**
> NOTE:  I do not want to edit the xorg.conf file, I want this to be displayed correctly out of the box.

That doesn't give you much to work with. You already know that it doesn't work out of the box, and the only way to magically have something that does work out of the box is to buy all-new hardware that you already know does work in that way. If, instead, you'd like to configure the hardware that you already have so that it works properly, then you might have to actually do some configuring.

The **only** way that a monitor can be automatically detected and configured is through EDID. This is a mechanism whereby a monitor tells an operating system what its capabilities are; the refresh rates it can do, the amount of video bandwidth that it can process, and so on. A number of monitors don't advertise their capabilities through EDID. A number of monitors do advertise their capabilities, but the information that they give is garbage. It sounds like your monitors fall into one of these categories. It's normally a fairly straightforward fix, but you don't want to fix it.

---

### Post by jeepfreak2002 on 2009-05-10
> **CatKiller said:**
> That doesn't give you much to work with. You already know that it doesn't work out of the box, and the only way to magically have something that does work out of the box is to buy all-new hardware that you already know does work in that way. If, instead, you'd like to configure the hardware that you already have so that it works properly, then you might have to actually do some configuring.

The **only** way that a monitor can be automatically detected and configured is through EDID. This is a mechanism whereby a monitor tells an operating system what its capabilities are; the refresh rates it can do, the amount of video bandwidth that it can process, and so on. A number of monitors don't advertise their capabilities through EDID. A number of monitors do advertise their capabilities, but the information that they give is garbage. It sounds like your monitors fall into one of these categories. It's normally a fairly straightforward fix, but you don't want to fix it.

All I'm thinking is that the monitor may not be communicating this info through a VGA cable and a DVI adapter, and that a straight up DVI cable may resolve that.  You may be right, as both machines are using the exact same monitor, so maybe it is the monitor giving garbage info...  We shall see.

---

### Post by CatKiller on 2009-05-10
> **jeepfreak2002 said:**
> All I'm thinking is that the monitor may not be communicating this info through a VGA cable and a DVI adapter, and that a straight up DVI cable may resolve that.  You may be right, as both machines are using the exact same monitor, so maybe it is the monitor giving garbage info...  We shall see.

You're right, it's certainly possible. I know that KVM switches often eat that information. You've already ordered the cables, so I'd certainly be interested to know that it helps. EDID is 15 years old now. It's quite frustrating that so many monitors are still out there that don't use EDID properly.

---

### Post by jeepfreak2002 on 2009-05-10
The thing that bothers me is that the 7 year old Mitsubishi Monitor is detected perfectly on an integrated Intel graphics chip...  You have a discreet nVidia card with a 2 year old higher end Viewsonic, and there is no communication....  Ya know - It has to be the monitors...  I have an 8600GT at home and it ID's my Samsung monitor just fine.

---

### Post by jeepfreak2002 on 2009-05-14
Solved!!!!!!

It was the VGA cable!!!!  Once I plugged in a straight up DVI cable the monitor was automatically detected!!

How do I mark this thread as solved?

---

### Post by CatKiller on 2009-05-14
> **jeepfreak2002 said:**
> It was the VGA cable!!!!  Once I plugged in a straight up DVI cable the monitor was automatically detected!!

How do I mark this thread as solved?

Glad to hear it :)

You can't mark threads as solved any more, unfortunately. The best you can do is change the title of the first post in the thread.

---

