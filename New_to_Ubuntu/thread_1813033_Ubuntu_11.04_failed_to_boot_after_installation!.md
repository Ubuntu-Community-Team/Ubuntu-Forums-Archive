---
title: "Ubuntu 11.04 failed to boot after installation!"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by jude.mazen on 2011-07-27
helloo,

i have installed Ubuntu 11.04, I get a flicker of a screen on boot and then no graphics.
Error in dmesg | grep fb
[19.050227]fb: conflicting fb hw usage inteldrmfb vs EFI VGA – removing generic driver!!

anyone plz can assist?

---

### Post by jude.mazen on 2011-07-27
helloo,

i have installed Ubuntu 11.04, I get a flicker of a screen on boot and then no graphics.
Error in dmesg | grep fb
[19.050227]fb: conflicting fb hw usage inteldrmfb vs EFI VGA – removing generic driver!!

anyone plz can assist?

---

### Post by jude.mazen on 2011-07-27
helloo,

i have installed Ubuntu 11.04, I get a flicker of a screen on boot and then no graphics.
Error in dmesg | grep fb
[19.050227]fb: conflicting fb hw usage inteldrmfb vs EFI VGA – removing generic driver!!

anyone plz can assist?

---

### Post by amjjawad on 2011-07-27
> **jude.mazen said:**
> helloo,

i have installed Ubuntu 11.04, I get a flicker of a screen on boot and then no graphics.
Error in dmesg | grep fb
[19.050227]fb: conflicting fb hw usage inteldrmfb vs EFI VGA – removing generic driver!!

anyone plz can assist?

Hello and Welcome :)

Are you able to login to Ubuntu?
What do you get when you turn your machine on?
What's your Graphics Card?

More info will be much appreciated so that we can offer the best advice/suggestion :)

---

### Post by cariboo on 2011-07-27
Please don't create multiple threads on the same subject, I have merged your 3 threads.

---

### Post by jude.mazen on 2011-07-27
Dear [amjjawad]("http://ubuntuforums.org/member.php?u=941822"),

I'm not able to login to ubuntu.
when i turn my machine i got flicker screen white then after that i get message says "[19.050227]fb: conflicting fb hw usage inteldrmfb vs EFI VGA &#8211; removing generic driver"
I have built in graphic card intel82852.
plz note that i used to have Ubuntu 9 on the same machine before and it was working ok, but the next second i have upgraded to Ubuntu 11 I have encountered this issue!!

appreciate your soonest reply,
Thanks

---

### Post by amjjawad on 2011-07-27
> **jude.mazen said:**
> Dear [amjjawad]("http://ubuntuforums.org/member.php?u=941822"),

I'm not able to login to ubuntu.
when i turn my machine i got flicker screen white then after that i get message says "[19.050227]fb: conflicting fb hw usage inteldrmfb vs EFI VGA – removing generic driver"
I have built in graphic card intel82852.
plz note that i used to have Ubuntu 9 on the same machine before and it was working ok, but the next second i have upgraded to Ubuntu 11 I have encountered this issue!!

appreciate your soonest reply,
Thanks

You had Ubuntu 9 and you upgraded it to 11? or you did a fresh new installation? as far as I know, you can upgrade from 9.xx to 11.04 directly. Please be more specific :)

Your current problem happened directly after installing OR Upgrading? did it work before?

Do you still have the LiveCD or LiveUSB? if yes, can you please boot from that and report back what will happen? I'm trying to figure our what is going on as you are not providing much info here.

---

### Post by jude.mazen on 2011-07-27
I did fresh installation and i have Ubuntu 11 on CD, plz advise?

---

### Post by amjjawad on 2011-07-27
> **jude.mazen said:**
> I did fresh installation and i have Ubuntu 11 on CD, plz advise?

Boot your machine from the LiveCD and check everything and see if your hardware will work probably with Ubuntu. Don't install, you already did, just select "TRY without installation" from the first menu that will appear when you press any key once you see the small keyboard icon and that dark purple screen.

---

### Post by jude.mazen on 2011-07-27
Thanxx a lot, i will try and I'm gonna let u know the result.

---

### Post by amjjawad on 2011-07-27
> **jude.mazen said:**
> Thanxx a lot, i will try and I'm gonna let u know the result.

Take your time and you're most welcome :)

---

### Post by jude.mazen on 2011-07-27
I have tried ubuntu with Live CD and it's working properly without any problems as I'm writing this now from Ubuntu, so plz advise how can i now fix the installed version on my notebook?

Appreciated your reply,

---

### Post by amjjawad on 2011-07-27
> **jude.mazen said:**
> I have tried ubuntu with Live CD and it's working properly without any problems as I'm writing this now from Ubuntu, so plz advise how can i now fix the installed version on my notebook?

Appreciated your reply,

If you can not login to Ubuntu at all and can't even see the login screen, maybe it's good idea to format and install again BUT make sure to back up your important files if any.

While you are booting from the LiveCD, please run this command and post back the output but please, put "CODE" tags between [ ] and [/] or highlight the text (output) and click "#".

```
sudo lshw -C display
```

---

### Post by jude.mazen on 2011-07-28
Dear Amjjawad,

Formatting is not possible, i need to fix it without re installation, any ideas?

---

### Post by varunendra on 2011-07-28
Please provide the output of sudo lshw -C display as amjjawad asked.

Also, try press and holding 'shift' key while booting from hard drive. This should bring up advance grub menu. Select and boot into recovery mode and then choose **failsafeX** in the recovery menu. See if this lets you boot to the desktop. If you could, it'll make further troubleshooting much easier.

---

### Post by wildmanne39 on 2011-07-28
Hi, you can also look at this link and see if it helps, but it sounds like you need to run recovery at startup with root networking and then choose fix broken packages.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by amjjawad on 2011-07-28
> **jude.mazen said:**
> Dear Amjjawad,

Formatting is not possible, i need to fix it without re installation, any ideas?

As explained, we need to see the output of that command :)

Also, please have a look at varunendra's post and wildmanne39's post :)

---

### Post by jude.mazen on 2011-07-28
Dear Gentlemen,

I have tried with "failsafex" from recovery menu and got successful login to the Ubuntu but i got notification, the machine is running with low graphic option.
Plz fibd below the information i got from code "sudo lshw -c display" :

jude@jude-Latitude-D500:~$ sudo lshw -c display
^[I (sysfs)  
  *-display:0             
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:11 memory:f0000000-f7ffffff memory:faf80000-faffffff ioport:c000(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff memory:faf00000-faf7ffff

Plz advise how can i update my graphic card driver to get high graphic card resolution?

Thanks a lot for the help.

---

### Post by wildmanne39 on 2011-07-28
Hi, open synaptic click on edit,fix broken packages and see if it fixes your problem.

---

### Post by varunendra on 2011-07-29
> **jude.mazen said:**
> 
jude@jude-Latitude-D500:~$ sudo lshw -c display
^[I (sysfs)  
  *-display:0             
       description: VGA compatible controller
       product: **82852/855GM Integrated Graphics** Device
       vendor: **Intel Corporation**
....
....
       configuration: **driver=i915** latency=0
       resources: irq:11 memory:f0000000-f7ffffff memory:faf80000-faffffff ioport:c000(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
Your graphics adapter is pretty generic type and as such I think the generic driver can easily handle it (like the current one). So we need to know the name of the other module that was conflicting so that we can blacklist it. Or, a way to 'force' the generic one everytime your computer boots. Unfortunately, I don't know how find the first without it being loaded by the kernel nor do I remember how to force the other one. It most probably involves changing the Grub boot line to include acpi=off or something. Maybe someone else could help with it.

If the conflict message was stored in some log file (I've no idea where, maybe dmesg, kernel or syslog in /var/log directory ??) then maybe we can determine the 'module name' of the other driver (EFI). Then blacklisting it should be easier solution. Sorry for such a no-help reply.

BTW, it seems like a similar bug reported here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614085](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614085)
But it is marked as 'fixed' so may be updating or 'fixing broken packages', as wildmanne39 suggested, could fix it for you.

---

