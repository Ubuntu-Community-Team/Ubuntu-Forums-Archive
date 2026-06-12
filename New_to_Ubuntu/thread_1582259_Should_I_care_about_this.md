---
title: "Should I care about this?"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by Jolicoeur on 2010-09-26
I upgraded from 8. version all the way to 10.04.1
When I boot I have to press Esc to choose kernel or it won't boot.
Choices are from 2.6.33, 2.6.32, 2.6.31 and so on down in number.
Nothing works except 2.6.32. [COLOR=Red][U]MISTAKE I meant to write nothing works except 2.6.31!!
[/U][/COLOR] 
Is this ok?

I wonder if my machine is missing out on anything stuck at 2.6.31
for example I cannot create a virtual box drive, states a kernel problem.

What do you think?:confused:

---

### Post by howefield on 2010-09-26
> **Jolicoeur said:**
> I wonder if my machine is missing out on anything stuck at 2.6.32

I wouldn't think so in as much as the current kernel for 10.04.1 is 2.6.32.24, although you should be able to create virtual machines.

Have you been playing around with installing kernels manually ?

---

### Post by CharlesA on 2010-09-26
Can you post the output of this command:

```
ls /boot
```

That'll tell us if you are missing those old kernels or not.

How are you creating this "virtual box drive?"

---

### Post by Jolicoeur on 2010-09-26
here is the output:

abi-2.6.28-19-generic               memtest86+.bin
abi-2.6.31-22-generic               System.map-2.6.28-19-generic
abi-2.6.32-24-generic               System.map-2.6.31-22-generic
abi-2.6.33-02063305-generic         System.map-2.6.32-24-generic
config-2.6.28-19-generic            System.map-2.6.33-02063305-generic
config-2.6.31-22-generic            vmcoreinfo-2.6.28-19-generic
config-2.6.32-24-generic            vmcoreinfo-2.6.31-22-generic
config-2.6.33-02063305-generic      vmcoreinfo-2.6.32-24-generic
grub                                vmlinuz-2.6.28-19-generic
initrd.img-2.6.28-19-generic        vmlinuz-2.6.31-22-generic
initrd.img-2.6.31-22-generic        vmlinuz-2.6.32-24-generic
initrd.img-2.6.32-24-generic        vmlinuz-2.6.33-02063305-generic
initrd.img-2.6.33-02063305-generic

---

### Post by CharlesA on 2010-09-26
It looks like you have the old kernels there, but if the current one is working fine, you shouldn't need to reboot into the old ones.

You can probably safely remove them if you want.

---

### Post by theozzlives on 2010-09-26
Some of those kernels don't look like standard Ubuntu Kernels. Have you installed any 3rd party kernels?

---

### Post by CharlesA on 2010-09-26
> **theozzlives said:**
> Some of those kernels don't look like standard Ubuntu Kernels. Have you installed any 3rd party kernels?

The only one that looks different is the one here:

```
vmlinuz-2.6.33-02063305-generic
```

I believe it's a mainline kernel.

---

### Post by Jolicoeur on 2010-09-26
I have not installed any

---

### Post by desnaike on 2010-09-26
The time it takes to get help, find the problem repair the problem you could do a clean install add all your apps and configurations and be up and running in 2-3 hours yesterday.

Distro upgrades are 50-50

---

### Post by Jolicoeur on 2010-09-26
I agree, but I have not been able to install any version after the 8. version.  I have to load 8. and then upgrade to 10.04. Did it twice now, same result, older kernel.

---

