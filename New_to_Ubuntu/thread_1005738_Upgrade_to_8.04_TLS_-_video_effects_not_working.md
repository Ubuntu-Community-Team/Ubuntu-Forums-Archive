---
title: "Upgrade to 8.04 TLS - video effects not working"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by josh6847 on 2008-12-08
I just upgraded to Ubuntu 8.04 TLS from 7.10.  Since then, compiz is not working because I am unable to select Extra effects on the Appearance Preferences in Visual Effects tab.  Does anyone know what I can do to get my video driver working again?

Thanks,

Josh

---

### Post by gettinoriginal on 2008-12-09
System > Admin > Hardware Drivers  see if your driver is still enabled.  Sometimes during and upgrade, it resorts to default. Activate the driver or if a search window comes up, click ok.  After this, you should be able to set Xtra or custom as you desire. Good luck :p

---

### Post by Michael.Godawski on 2008-12-09
hi josh6847,

gettinoriginal is right, check your hardware drivers if they are activated. 

It would also help us if you give us some info about your graphic card:
```

sudo lshw -C display
```

---

### Post by josh6847 on 2008-12-09
Under System >> Admin >> Hardware Drivers I only have two entries: Atheros hardware and my wireless card...

This is what I get when doing a sudo lshw -C display

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon Mobility M7 LW [Radeon Mobility 7500]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
       configuration: latency=66 mingnt=8

Are there any modules I need to install?

Thanks guys,

Josh

---

### Post by overdrank on 2008-12-09
> **josh6847 said:**
> Under System >> Admin >> Hardware Drivers I only have two entries: Atheros hardware and my wireless card...

This is what I get when doing a sudo lshw -C display

  
       product: Radeon Mobility M7 LW [Radeon Mobility 7500]
     
Thanks guys,

Josh

Hi and I have the same graphics card working on Hardy. Have you tried the xfix option when booting into recovery mode. This may correct the driver issue as the driver that comes with Hardy should work well.

---

### Post by josh6847 on 2008-12-09
I tried running xfix and that still did not fix the problem. I'm thinking I should just downgrade back to 7.10.  Any other suggestions??

Thanks for everyones help.

---

### Post by gettinoriginal on 2008-12-10
The problem is that your system is not picking up your video card, not which package you are running.  And sorry, I do not know how to make your system recognize it.  But good luck.:p

---

### Post by gettinoriginal on 2008-12-10
Before you do anything really drastic, try this:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=979349](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=979349)

---

### Post by mc4man on 2008-12-10
I don't have any ati cards any more but here's an old post from when hardy came out.
You could use it for a starting point and see if your card is still blacklisted and if so, look for  workarounds.

[http://ubuntuforums.org/showthread.php?t=750551](http://ubuntuforums.org/showthread.php?t=750551)

I wouldn't hesitate trying to install compizconfig-settings-manager anyway and trying to enable some effects thru there. (preferences -> advanced desktop effects .. (staying away from the appearances menu and assuming compiz is installed

---

### Post by overdrank on 2008-12-10
> **josh6847 said:**
> I tried running xfix and that still did not fix the problem. I'm thinking I should just downgrade back to 7.10.  Any other suggestions??

Thanks for everyones help.

Ok you may try the command ```
gksu displayconfig-gtk
``` and setup there as you will need to use the ATI as the driver.

---

