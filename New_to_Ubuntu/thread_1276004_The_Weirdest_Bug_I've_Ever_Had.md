---
title: "The Weirdest Bug I've Ever Had"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by regomodo on 2009-09-26
#

---

### Post by rockstarrem on 2009-09-26
Yeah, that's really weird. I'm on an HP and there were a lot of programs with a dual boot of Vista and Ubuntu on this PC, I had to choose one, and I chose Ubuntu so yeah, I'm sure there's a way to figure it out, maybe someone else can help, but it could have something to do with the dual boot and HP.

---

### Post by regomodo on 2009-09-26
#

---

### Post by QIII on 2009-09-26
I believe your machine has in Intel video chipset.

You might have a look here for some possible solutions:

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

and take a look at the Intel video regression section.

 You may have to boot in recovery mode and drop to the terminal to make any needed changes.

By the way:  The frequent problems encountered with hibernation, in particular, are often associated with the size of the swap partition.  If it is less than the amount of RAM, the RAM state cannot be saved to disk (hibernation is often called "suspend to disk") and the state returned to the RAM on reactivation is garbage.

---

### Post by regomodo on 2009-09-26
#

---

### Post by scorp123 on 2009-09-26
> **regomodo said:**
> Suspend and hibernate don't work of course but that's usual for Linux. Uhhhm no, in fact it's not. :D  Not anymore.

> **regomodo said:**
>  However, if the laptop is turned on whilst on Battery nothing happens unless I repeatedly press the escape key ...

[edit] I've just gone to turn off the laptop and it does a similar thing. I have to press escape at least once whilst the slider moves just to get it moving gain. Then it drops to a blank console and does nothing. Hit escape and the HDD powers down. Then the laptop sits there unresponsive so I have to power off it by holding the power button. 

Sounds to me like these two problems are related. Your Linux kernel is not recognizing the laptops power management correctly and hence it acts weird. In layman's terms: it can't sleep properly, but neither can it properly "wake up" and become active.

According to my Google searches you're not the only one having troubles with the dv6500 .... In this thread one poster suggests using the "noapic" option:
[http://forum.notebookreview.com/showthread.php?t=154203](http://forum.notebookreview.com/showthread.php?t=154203)

Other threads:
[http://ubuntuforums.org/showthread.php?t=845104](http://ubuntuforums.org/showthread.php?t=845104)
[http://ubuntuforums.org/showthread.php?t=870575](http://ubuntuforums.org/showthread.php?t=870575)
[http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops](http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops)

---

### Post by regomodo on 2009-09-27
#

---

### Post by regomodo on 2009-09-27
#

---

### Post by philinux on 2009-09-27
Give karmic a go from a livecd.

It might be better for your hardware.

---

### Post by scorp123 on 2009-09-27
> **regomodo said:**
>  About the suspending/hibernating. I've tried ubuntu hardy and jaunty on 5 different systems. Only a Thinkpad sort of works. The rest do not want to play ball. I have to live without sus/hib on my laptop ... Honestly, I haven't had that problem in ages. All the Compaq and HP laptops I ever had usually worked tip top with Linux. Right now I am typing this on my dv2108ea which I just woke up from suspend. 

Maybe the hardware in that laptop is too new? Another thing I'd try: a different Linux distro maybe?

Did you ever try OpenSUSE? It's quite polished and does a very good job at hardware recognition. They also have a live CD which can used for installation. Or you go for their DVD release which contains everything + the kitchen sink.

Other candidates with the reputation of having excellent hardware recognition would be Mandriva and Fedora ... Maybe you could try them as well?

---

### Post by regomodo on 2009-09-27
#

---

### Post by scorp123 on 2009-09-27
> **regomodo said:**
> Nope, nothing's new. That HP is 2/3yrs old Something else that just came to my mind: Did you upgrade the BIOS on that laptop?

Shortly before Vista came out HP released a BIOS update for many of their desktops and laptops. So I upgraded the BIOS on my dv2108ea. As my laptop is from late 2004 / early 2005 I thought "Hmmm ... why not?". 

Bad idea.

After that nothing would work under Linux anymore. The extra-keys above the normal keyboard (multimedia controls, volume, etc.) stopped working. My remote control stopped working.

So I reverted back to the original BIOS release (the one before Vista was officially released) and lo' and behold: Everything is working again.

Hence my question ... Could it be that you did a BIOS upgrade at some point?

Maybe it would be worth trying out a pre-Vista BIOS release? (please: only do this if you understand the risks and if you're comfortable with it -- don't brick your computer!)

---

### Post by regomodo on 2009-09-27
#

---

### Post by doas777 on 2009-09-27
try tapping the power button once, instead of holding ctrl or escp. I have a simmillar issue with a couple dv9000s. it started with Hardy. got better in intrepid but was still there. still in jaunty.

heres to high hopes for karmic.

---

### Post by regomodo on 2009-09-29
#

---

