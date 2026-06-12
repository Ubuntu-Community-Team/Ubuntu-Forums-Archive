---
title: "Network controllers suddenly stopped working"
date: 2014-02-12
forum: Networking &amp; Wireless
---

### Post by nicholas9 on 2014-02-12
A couple of hours ago, I turned off my computer, and when I turned it back on again, my network controllers had stopped working. This was accompanied by some error message about Network Manager, and by the resolution of my screen being slightly off, making everything blurry. I have no internet on it as we speak, so I have no effective way to post the messages I get from different commands, but I can try to manually write all the relevant information. To begin with, from commands I found in several threads on the issue, I did "sudo lshw -C network", which shows that both of my network controllers are unclaimed. The wired one being an "AR8121/AR8113/AR8114 Gigabit or Fast Ethernet" from Qualcomm Atheros, and the wireless one being "PRO/Wireless 4965 AG or AGN [Kedron] Network Connection" from Intel. Pretty sure some of you will know more about what to look for here, just tell me whatever you need, I'll do my best to provide it (if you need larger logs, I guess I'll take a picture of the screen and upload it here or something).

---

### Post by tgalati4 on 2014-02-12
Why did you shut off your computer?  Did you perform some updates?  Was your system acting strange and you decided to reboot?  Let's work one problem at a time.  In your BIOS, there should be a setting to turn wireless off.  Try that.  Reboot to a rescue shell (root terminal).

In that terminal:

```
sudo lshw -C network
```

Now would be a good time to reboot your router and check it's health.  I presume you are using both wired and wireless at the same time from the same router?

There are a lot of network tools available:

```
apropos network
```

One of them is called *nm-tool*:

```
nm-tool
netstat -r
ping www.google.com
```

---

### Post by nicholas9 on 2014-02-12
I shut it off because I was packing it away, and rebooting it after putting it to sleep has never been working anyways. Where in the BIOS can I turn my wireless off? I see a "Network Boot" setting which is disabled, but there doesn't seem to be any settings specific to wireless. Also, how do I reboot to a rescue shell? Also, I don't know what the assumption about using both wired and wireless at the same implies, but I never use wired internet for my laptop, have always just been using wireless.

---

### Post by nicholas9 on 2014-02-12
Bump.

---

### Post by nicholas9 on 2014-02-13
Bump.

---

### Post by nicholas9 on 2014-02-13
Really, I need help with this, need to have a working laptop...

The worst thing is, when reading about similar problems, everyone is telling people to do sudo apt-get this and auso apt-get that, but I can't really do that with no internet...

---

### Post by steeldriver on 2014-02-13
What version of Ubuntu are you using? I don't know about the Atheros device, but the Intel wireless chipset should be supported out of the box. What happens if you try to load the driver manually

```
sudo modprobe -v iwl4965
```

Are there any relevant messages in the dmesg log?

```
dmesg | grep ^iwl
```

---

### Post by nicholas9 on 2014-02-13
Using 13.10. Yeah, have never really used the wired connection anyways, only wireless, but all of a sudden they both stopped working.

The first command yields: "FATAL: Module iwl4965 not found."

The second one doesn't return anything.

---

### Post by nicholas9 on 2014-02-13
Also, it looks like more drivers have also stopped working, judging by the poor resolution that accompanied it (graphics driver that has stopped working I guess) and that the computer no longer registers my USB mouse.

---

### Post by steeldriver on 2014-02-13
Sorry - I had a brainfart with the second command, it should not have included the line anchor (^), just

```
dmesg | grep iwl
```

---

### Post by tgalati4 on 2014-02-13
OK, it looks like you have several issues going on.  If this laptop travels frequently, then it is possible that you have a hard disk issue.  When a disk fails you get several misleading errors.  Sorry, that is just the way it is.  What was a network problem is really the inability to read critical files.

Open a terminal (if you can) and post the output of:

```
dmesg | tail -40
```

When you boot, hit the ecscape button or Alt-F1 and there should be a GRUB menu--a menu that allows you to select which system you want to boot into.  Select "Rescue Shell".

Don't install anything.  But do get a flash drive and start backing up critical data.  If you have problems with that then you are getting closer to the problem.

After the backup, then post the SMART status of the drive:

```
sudo smartctl -a /dev/sda
```

This is a volunteer support forum not a paid help desk, so bumping more than once per day is not encouraged.

---

### Post by nicholas9 on 2014-02-13
Not sitting by my desktop now, so only have internet on my Windows distro, so I have to change between the two to run commands and try the stuff you tell me.

"dmesg | grep iwl" also did not return anything.

I doubt that it is hard disk failure, as the only problem is drivers not working. I will still try what you said, but I don't really have any critical data to backup, would the procedure still work without backing anything up?

---

### Post by varunendra on 2014-02-13
> **tgalati4 said:**
> OK, it looks like you have several issues going on.  If this laptop travels frequently, then it is possible that you have a hard disk issue.  When a disk fails you get several misleading errors.
+1, especially when it says "module iwl4965 not found", it means at least the current kernel (or whole setup) is clearly broken, whatever be the cause.

Perhaps the best option is to immediately create a Live USB/CD while it is still alive. It will help in troubleshooting as well as an emergency OS to perform necessary tasks.

> This is a volunteer support forum not a paid help desk, so bumping more than once per day is not encouraged.
+10

---

