---
title: "For those using the Broadcom STA wireless driver"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by Ayuthia on 2008-10-15
If you have to keep enabling the driver each time you boot into Ubuntu, please add the following (in the Terminal):
```
echo wl|sudo tee -a /etc/modules
```

For those who have an ethernet card that uses the b44 driver, please add the following (also from the Terminal):
```
echo -e '#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb ndiswrapper; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
```

---

### Post by vimota on 2009-01-27
Now, what exactly does this do? I have a problem with my Broadcom STA wireless driver, which shows up as enabled and all, but does not pick up any networks (which there absolutely is) and even manually configuring to a network does not work. Will this solve my problem? Thanks!

---

### Post by Henery on 2009-02-23
This worked for me been looking all day thank you! I could not find the answer till I found your post c&p your command line in terminal reboot and wifi works on boot up!):P

---

### Post by E1or0 on 2009-05-10
**Vimota, I had the same issue you were having, I was able to see my wireless network just fine right after I follow **Ayuthia's **Advise...:) I hope you were able to fix it... Have a good day everybody **:P

---

### Post by chobes68 on 2009-07-09
YOU ROCK!!!! Just installed Ubuntu on an Acer laptop, and for once I didn't have video card issues, but the wireless wasn't supported. Don't know how it works, and what exactly I was typing in, but I typed it in exactly as Ayuthia instructed, and I'm on the web!!

:guitar:

THANK YOU

---

### Post by t0mppa on 2009-07-09
To give a brief explanation of what the commands do, so no one needs to worry about running unknown commands: the first command adds wl (module for the STA driver) to the /etc/modules file, which means it will get automatically loaded during boots.

The second one is a workaround for the ssb module, used by the b44 wired driver and b43 wireless driver. It tends to hog the wireless, if b44 is used and even if b43 isn't. That disallows the wl from getting associated with the wireless interface and leads to wireless not working. It simply unloads the other driver modules, then loads up the wl, when the wireless interface is unclaimed and thus gets associated with the wl and then loads the b44 & ssb back, so the wired interface stays usable as well.

---

### Post by manaruli on 2009-09-25
I had the similar problem and it seems that Ayuthia's advice really helped.
 
Thanks!

---

### Post by jhereg2u on 2009-09-25
Had the same problem (couldn't see the wireless network) with a new install of Jaunty on an Inspiron 1720. Tried the above fix, rebooted and it worked!!...Thanks!

---

### Post by villejer on 2009-11-16
Also worked for me! Dell Inspiron 1440, BCM4315. this fix is perfectly short and helpful! thanks

---

### Post by cyclopse on 2009-11-16
Sorry it didn't work for me on the Dell Mini 9 with the Broadcom driver. Still no wireless option on clicking the icon.

---

### Post by tpkaznowski on 2009-11-16
> **Ayuthia said:**
> If you have to keep enabling the driver each time you boot into Ubuntu, please add the following (in the Terminal):
[/code]

How do you enable the driver in the first place? im really stuck with this wireless?

---

### Post by boz86 on 2009-11-16
> **Ayuthia said:**
> If you have to keep enabling the driver each time you boot into Ubuntu, please add the following (in the Terminal):
```
echo wl|sudo tee -a /etc/modules
```For those who have an ethernet card that uses the b44 driver, please add the following (also from the Terminal):
```
echo -e '#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb ndiswrapper; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
```

Didn't work for me, now can't connect at all using wireless. Can you provide the command to undo this?

Thanks, wish it worked for me.

---

