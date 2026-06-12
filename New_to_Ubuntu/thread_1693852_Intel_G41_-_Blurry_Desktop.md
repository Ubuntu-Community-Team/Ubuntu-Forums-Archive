---
title: "Intel G41 - Blurry Desktop"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by Nico34 on 2011-02-23
Hi everyone,

I am currently making a test to see how the Intel G41 works as a video card; I previously used an additional ATI Radeon HD4550 (that now is unplugged from the system).

Everything works fine (it plays HD videos very well) but the screen is blurry; not that dramatic, but I can definitely see the difference with when the HD4550 was plugged.

There don't seem to be any installable drivers.

I'm using Compiz with high desktop effects; the resolution is the correct monitor's native, 1440x900.


How can I fix that?


Thanks :)

---

### Post by robsoles on 2011-02-23
I can only suggest perhaps 'refresh rate' is far from optimal - can you access 'System'->'Preferences'-'Monitors' and see refresh rate option(s) there?

Bit of a longshot - modern monitors usually 'whinge' when the refresh rate (or set display size) is not optimal.

---

### Post by Nico34 on 2011-02-23
Hi Robsoles,

thanks for the tip; I have checked the Monitor menu and everything looks fine.


Actually I have found this: [http://www.intel.com/support/graphics/sb/CS-030332.htm](http://www.intel.com/support/graphics/sb/CS-030332.htm)

It seems that G41 graphics doesn't support my 1440x900 resolution.

It can be fixed with a driver update but I can't find any for Ubuntu.
I have tried with a Live CD to see if maybe there was something missing in my installation but I got the same blurry desktop.

---

### Post by Nico34 on 2011-02-24
Up :)

Anybody knows where to find the drivers/how to fix this issue?

---

### Post by heyho on 2011-02-24
> **Nico34 said:**
> Up :)

Anybody knows where to find the drivers/how to fix this issue?

Do you mean that you cannot select that res?  The link suggests that it would not even be available to use.

I have a G41 chipset, and can select 1440x900, and 1920x1080 with no problems.  As you point out, all of those drivers are for windows.

---

### Post by hansolo4949 on 2011-02-24
What is the native resolution fir the monitor? If it is displaying below it's native resolution, it is often rather blurry. Go to system>preferences>monitor (or something like that) then select the highest resolution you can. That should fix your issue!


Update:oops, I saw that you do have it at the native resolution. Try enabling one of the restricted drivers and see if that helps, if there are any.

---

### Post by Nico34 on 2011-02-24
The native resolution of my monitor is 1440x900; it works flawlessly with the Radeon HD4550 plugged and open drivers.

If I unplug the VGA and start Ubuntu with only the integrated G41 graphics the desktop seems to look fine, everything has the right proportion (I mean not stretched, or extended or too little/small like when you set to a non-native resolution), but it's all blurry.
System>Appearance>Monitor is correctly set to 1440x900.

So I guess that Ubuntu identifies and sets resolution to 1440x900 but then G41 is not able to display it correctly, as suggested in the above link: [http://www.intel.com/support/graphics/sb/CS-030332.htm](http://www.intel.com/support/graphics/sb/CS-030332.htm)

Ubuntu restricted drivers are installed and in Ubuntu Software Center I have looked for "intel", "G41" or "X4500" but didn't find anything.
I tried with a Live CD and got the same result.
I disabled all the desktop effects but nothing changed.

---

### Post by robsoles on 2011-02-24
Specifically, about refresh rate: Did you find out, from any materials about the monitor, what refresh rate the monitor uses as 'optimum refresh rate' and then exactly what refresh rate your system is actually using on the monitor?

The only way I've gotten a blurry picture out of any of my setups, while the resolution was set to the monitor's native res, was by using a non-optimal refresh rate - all my modern monitors 'complain' when I do that...

---

### Post by hansolo4949 on 2011-02-24
Yes, if that is happening, perhaps you should set the screen to a lower res, that doesn't look blurry. Experiment!:)

---

### Post by Nico34 on 2011-02-24
Ok, I've tried different combinations of resolutions/refresh rate:

- Radeon HD4550: the only perfect is 1440x900/60Hz, all other setups look blurry (even 1440x900/75Hz)

- G41: all setups from 720x400 to 1440x900 look blurry; switching refresh from 60Hz to 75Hz has no effect

---

### Post by robsoles on 2011-02-24
> **Nico34 said:**
> ...

... switching refresh from 60Hz to 75Hz has no effect

That makes it sound like the refresh rate setting in Ubuntu isn't actually being used - that is to say that no matter what setting you set it uses 75Hz and as shown using the HD4550 only 60Hz looks good.

It's a pity I cannot get at your setup with an oscilloscope - I could prove whatever refresh rate is being used on the monitor that way.

Would you please post your /etc/X11/xorg.conf file contents for us to have a squiz at.

---

### Post by Hedgehog1 on 2011-02-25
> **Nico34 said:**
> 

- Radeon HD4550: the only perfect is 1440x900/60Hz, all other setups look blurry (even 1440x900/75Hz)

- G41: all setups from 720x400 to 1440x900 look blurry; switching refresh from 60Hz to 75Hz has no effect

I know this is out of left field here, but were you using a DVI cable from the Radeon, but a VGA cable from the G41?

I converted to all DVI because I saw a slight blur using VGA compared to DVI.

Just a thought...

:KS

---

