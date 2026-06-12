---
title: "ipv6 help"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by triplezero24 on 2009-11-13
Ok, so I'm an uber-noob.  I know this.  Heres my problem.  I know my wireless router does not support ipv6, so I am having trouble with the connections there.  I've seen how to disable ipv6 through the console as follows:

gksudo gedit  /etc/modprobe.d/aliases
 

Find the line: alias net-pf-10 ipv6
 

change to: alias net-pf-10 off


Ok, now when I run the first command an admin password box comes up, I type it in, hit enter, and nothing comes up, and nothing changes in the console. Sooo.. I guess I'm kind of lost here.


Thanks for your uber-patience.  :)

---

### Post by seeker5528 on 2009-11-13
Don't know why gedit is not coming up, you might try sudo instead:

```
sudo gedit /etc/modprobe.d/aliases
```

If it still doesn't come up try nano instead of gedit.

Also depending on how new the version of Ubuntu you installed is, it might be 'aliases.conf' instead of 'aliases'.

If you are running Karmic, the part of the kernel that handles IPv6 is compiled in to the kernel instead of as a separate module so the above won't work.

A different option that I think should work both with Karmic and older releases.

```
sudo gedit /etc/sysctl.d/60-ipv6.conf
```

This is a non-existant file so it should open gedit with a blank file named 60-ipv6.conf, to which you add the text....

```
#Disable IPv6
net.ipv6.conf.all.disable_ipv6=1
```

Then save the file. Since this is a file that is not managed by the system, you should not have to worry about doing this again because some update replaced the file. 

To activate the change without rebooting you should be able to type the command:

```
invoke-rc.d procps start
```

To see that IPv6 is actually disabled type the command:

```
cat /proc/net/if_inet6
``` 

If the above command does not show any output, then ipv6 is disabled.

Later, Seeker

---

### Post by wojox on 2009-11-13
You need to set it as a boot option. What are you using 9.10 or 9.04

---

### Post by kurtopia on 2009-11-14
Hello,
 
I am using 9.10 and I read the same as the OP however the aliases file doesn`t exist so I assume it is the boot option you speak of so if you could explain how that is done in 9.10 I would appreciate it.
 
Thanks,
 
Kurt

---

### Post by tquinn on 2009-11-16
I am no expert, but the way I disabled ipv6 is to edit my grub boot.

```
gksudo gedit /boot/grub/menu.lst
```
 

there you will see something like this:

```
title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		0eec5b6b-0010-410d-8007-7de9687bff23
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=0eec5b6b-0010-410d-8007-7de9687bff23 ro quiet ipv6.disable=1 splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet
```

In the line that begins with "kernel" you need to add "ipv6.disable=1" between "quiet" and "splash".

This is a boot time argument that will disable ipv6. Reboot, and it should be disabled.

---

### Post by seeker5528 on 2009-11-16
If this was a fresh install, then you should be using grub2, in which case you should edit '/etc/default/grub'

There is a line the reads:

```
GRUB_CMDLINE_LINUX=""
```

Where you add the kernel arguments.

If you have the legacy grub package and edit menu.list, you should edit the upper section:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```

add it to the defoptions line:

```
# defoptions=quiet splash ipv6.disable=1
```

In both cases you should then open a terminal window and type:

```
update-grub
```

to activate the configuration.

Personally I still think it is a better solution to create the '/etc/sysctl.d/60-ipv6.conf' file as I posted earlier in the thread.

Later, Seeker

---

### Post by skotos on 2009-11-17
And to avoid Firefox trying to ask the router (that might have been set up as a LAN DNS server) to solve any ipv6, I would run Firefox and type in the address bar:
```
about:config
```Then, in the filter field of the new window, just type```
ipv6
```That will filter out everything but (currently) just two lines. Double click on```
network.dns.disableIPv6
```to set it to **true**.
From now on, even Firefox will not try to secretly(?) annoy you or your network with any ipv6 query.

---

