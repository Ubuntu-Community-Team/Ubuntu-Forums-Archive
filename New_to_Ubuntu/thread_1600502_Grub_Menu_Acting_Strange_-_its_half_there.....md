---
title: "Grub Menu Acting Strange - its half there...."
date: 2010-10-19
forum: New to Ubuntu
---

### Post by listerdl on 2010-10-19
When I start my dual boot machine it lists everything as normal, i.e. the last kernels Windows 7.

All good but linux has reverted to make itself the primary boot option. 

But, I prefer to boot into windows by default, (I have to use windows for work unfortunately) and when I went to change the Login Settings in Ubuntu - Windows 7 wasnt even listed??

I think that when I recently did a tidy up using the ubuntu in built system I might have removed part of the grub program?

Basically I just need to have windows listed in the login program any idea how to do that? THANKS!!

Hi, I have a dual boot and when I recently did a "tidy up" from the Ubuntu Settings I think that it must have removed the full grub settings

---

### Post by jtarin on 2010-10-19
[Your answer can be found here]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by tajiknomi on 2010-10-19
[SIZE=2]*Open the file (menu.list)*[/SIZE] **/var/lib/dpkg/info**..

[SIZE=2]**Remove comment from Win 7 title**[/SIZE].........

---

### Post by listerdl on 2010-10-19
OK, seems all very complicated tbh.

How long has Grub2 been the "standard"

Is this generally due to a bug upgrading from Grub 1 to 2?

Thanks

---

### Post by jtarin on 2010-10-19
Grub2 is the standard install for 10.04.

---

### Post by listerdl on 2010-10-19
> **jtarin said:**
> Grub2 is the standard install for 10.04.

Hey thanks for that.

If I installed on the windows partition the EasyBCD as per your signiture - would that create a conflict with Grub2?

Thanks!

---

### Post by jtarin on 2010-10-19
Grub2 would need to be reinstalled to the / partition of your ubuntu install. I'm at work now and don't have all the links and particulars to give you, but if you can wait until tomorrow (it's 8pm here)I can get you setup.

---

### Post by listerdl on 2010-10-19
> **jtarin said:**
> Grub2 would need to be reinstalled to the / partition of your ubuntu install. I'm at work now and don't have all the links and particulars to give you, but if you can wait until tomorrow (it's 8pm here)I can get you setup.

Hey thanks - yeah that would be great.

Its 6pm with me so we must be in a similiar time zone, im in Tokyo.

Thanks again!

---

### Post by jtarin on 2010-10-19
I'm in Vladivostok. :) Just across the way.
[Here's]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") something to read in the meanwhile so you can prepare for the change. Scroll down to method #3 CHROOT. Steps 9 and 10 wil be modified to read.
```
9.Reinstall GRUB 2:
 Substitute the correct device - sda, sdb, etc. **_Do specify a partition number._**
```Grub will complain about this ```
If the user attempts to run the command with a specific partition (example: sudo grub-install /dev/sda6 ) a warning will be issued. Specifying a partition is not recommended due to the use of blocklists, which the developers consider unreliable. An option is provided on how to override this recommendation if the user still wishes to do so.
``` so you will have to use the --force command as your readout from the terminal will give you as an example

```
10. Skip this step (or Grub will reinstall itself to the MBR)
```At this time run update-grub

You can go ahead and install EasyBCD 2.X in Windows in the meanwhile and I will get you the documentation on how to set it up.

---

### Post by listerdl on 2010-10-19
Great! Thanks very much for all the help!

Can I ask you, is the Windows Boot Loader preferable in your opinion?

---

### Post by amjjawad on 2010-10-19
Isn't this code suppose to fix it?

```

sudo update-grub

```

I think you could use GRUB and boot Windows by default. Not sure how to do that but with Fedora (for example), during the installation, you are able to choose with OS to boot by default but I know Ubuntu does not do that.
Still didn't learn how to tweak GRUB2 and didn't go deep with it yet.

I'm just curious about this and thought update-grub could fix it.

---

### Post by amjjawad on 2010-10-19
Isn't this code suppose to fix it?

```

sudo update-grub

```

I think you could use GRUB and boot Windows by default. Not sure how to do that but with Fedora (for example), during the installation, you are able to choose with OS to boot by default but I know Ubuntu does not do that.
Still didn't learn how to tweak GRUB2 and didn't go deep with it yet.

I'm just curious about this and thought update-grub could fix something then with some commends he could set Windows to boot by default.

---

### Post by Quackers on 2010-10-19
You could look in Synaptic Package Manager for Startup Manager, install it and then you can set the default OS yourself with a GUI.

---

### Post by jtarin on 2010-10-19
> **listerdl said:**
> Great! Thanks very much for all the help!

Can I ask you, is the Windows Boot Loader preferable in your opinion?I prefer it when I dual boot. Before EasyBCD and Vista/Win7 there were other ways to dual boot using boot.ini from Windows.

---

### Post by amjjawad on 2010-10-19
> **Quackers said:**
> You could look in Synaptic Package Manager for Startup Manager, install it and then you can set the default OS yourself with a GUI.

That's a good advice :)

---

### Post by jtarin on 2010-10-20
@listerdl  .....I have sent you a PM.

---

