---
title: "Laptop getting heated"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by PraveenP on 2011-05-14
I was using 10.04. Yesterday I install natty (fresh install). While using unity for atleast 30 mins laptop gets heated and atlast it automatically shutdown. There is no such problem in ubuntu classic mode. I remember this happened a couple of times in 10.04 while playing flash movies from web. Laptop is an old one Lenovo Y410.

Advance thanks for any help

---

### Post by kaldor on 2011-05-14
Classic mode doesn't use 3d-acceleration. I notice the same thing on my laptop on Compiz with all releases.

If you want Unity, try using Unity 2d:

```
sudo apt-get install unity-2d
```

It's a more basic version of Unity.

---

### Post by wildmanne39 on 2011-05-16
> **PraveenP said:**
> I was using 10.04. Yesterday I install natty (fresh install). While using unity for atleast 30 mins laptop gets heated and atlast it automatically shutdown. There is no such problem in ubuntu classic mode. I remember this happened a couple of times in 10.04 while playing flash movies from web. Laptop is an old one Lenovo Y410.

Advance thanks for any help
Hi, laptops do run a lot hotter then desktops, I recommend using one of the cooling pads with the fans to set it on, plus it probably needs to be cleaned out.:)

---

### Post by Hedgehog1 on 2011-05-16
Another option (it keeps my HP laptop running comfortably in Natty):

To improve the function of the laptop fan using 'current' grub options:

```
gksudo gedit /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT=**"**quiet splash **acpi_osi=\\\"Linux\\\""**
```

There are a total of **4 double quotes** in this line (2 side-by-side at the end)

Then do:

```
sudo update-grub
```

**And reboot. The operation of this will keep your computer running cooler.**

In case you are wondering WHY all these slashes, it is because this text string gets processed twice before it is used to boot the kernel:

In /etc/default/grub it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
```

Which gets converted by the update-grub in /boot/grub/grub.cfg as:
```
linux /boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi=\"Linux\"
```

The command is then passed to the kernel when run by grub as:
```
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi="Linux"
```

See how easy that (isn't) to follow?


***The Hedge***

:KS

---

### Post by seawolf167 on 2011-05-16
Also check some basic physical things like blowing out the dust accumulation in the fans and heatsinks. If the laptop is really old you may need new thermal paste between the heatsink/fan and cpu (it can burn up after a long time and become worthless).

Make sure there is adequate air circulation around the laptop so it can vent properly.

---

### Post by PraveenP on 2011-05-19
Thank you all! I did almost all things including cleaning laptop and now it is much better. I don't know which one really worked :) Now default unity (not 2d) also works well. But I think, machine is little hotter than old 10.04 installation.

---

### Post by wildmanne39 on 2011-05-19
> **PraveenP said:**
> Thank you all! I did almost all things including cleaning laptop and now it is much better. I don't know which one really worked :) Now default unity (not 2d) also works well. But I think, machine is little hotter than old 10.04 installation.

Hi, it probably is I think unity is a little more resource hungry.

---

### Post by chah on 2011-05-19
If you think that the heat might be coming from your HDD, you can set it to spin-down more aggressively to conserve power and reduced heat:

```

sudo hdparm -S 4 /dev/sda

```

If /dev/sda is your hard drive. This will set it to spin down in 4 sets of 5 seconds, or 20 seconds (but see the man page for details). Note that you'll experience more lag when you want to access the drive after it's spun down.

---

### Post by seawolf167 on 2011-05-19
> **PraveenP said:**
> Thank you all! I did almost all things including cleaning laptop and now it is much better. I don't know which one really worked :) Now default unity (not 2d) also works well. But I think, machine is little hotter than old 10.04 installation.

Nice, glad it helped. I know I had a laptop at work I was fixing and it kept shutting off with the automatic temp. shutoff; cleaned the fans, new thermal paste and it worked like new.

---

### Post by cbennett926 on 2011-08-03
Ok, where do I paste the gedit code?

---

### Post by wildmanne39 on 2011-08-04
Hi, you add this 
> acpi_osi=\\\"Linux\\\""
to this 
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash
and it will look like this
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
then run this command
```
sudo update-grub
```
and you are done.

---

### Post by beew on 2011-08-04
I am interested in Hedgehog1's solution as I have an old laptop that can use some cooling. :)

Can someone explain what those codes do and if there is any potential side effect that I should be aware of?

Thanks.

---

### Post by wildmanne39 on 2011-08-04
Hi, this is what I found on the subject.
> Disable the check of power state or changes the OS compatibility reported to the BIOS. Necessary on some broken BIOSes to make temperature/fan control work. 

It is possible that it might run at full speed all the time but it only happens on a few systems.

---

### Post by beew on 2011-08-04
> **wildmanne39 said:**
> Hi, this is what I found on the subject.


It is possible that it might run at full speed all the time but it only happens on a few systems.

Thanks for the explanations!

---

### Post by wildmanne39 on 2011-08-04
Hi, your welcome!

---

### Post by romanegloo on 2011-10-28
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""

So what is this actually doing? Tell the OS that this laptop is running on Linux? Can anyone inform me?

---

### Post by sadaruwan12 on 2011-10-28
> **wildmanne39 said:**
> Hi, this is what I found on the subject.


It is possible that it might run at full speed all the time but it only happens on a few systems.

> **romanegloo said:**
> So what is this actually doing? Tell the OS that this laptop is running on Linux? Can anyone inform me?

I think wildmanne39 did answer your question it tells the BIOS to keep the fan running at full speed with out stopping.

Normally in my experience I've seen laptops cooler fans have this tendency to get slower when they age even a a PC cooler will do this but much easier to replace than a laptop.

What I suggest is that to get a vacuum type cooler which can suck the hot air out I've seen such a device in ebay and if your could search for it you can find it and this will help you to ease up the heating issue.

(I'm not trying sell anything I found this while I was searching for a cooler fan my self thought might help this person thank you)

---

