---
title: "LXDE Ubuntu running on IGEP Board - Mobprobe fatal error?"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by encima on 2011-02-21
Hi All,

New to this forum, and linux. Kinda having to become a Linux expert for my PhD!

 Just starting to get to grips with the terminal and I am getting some weird error. I also get the error on startup. Essentially, I am trying to install my wireless chips driver but to no avail.
When I run the modprobe command, I get a FATAL error:

Could not load /lib/modules/2.6.35.7/modules.dep

I have checked in that directory and I cannot see anything within /lib/modules.

I have followed the general advice on this forum (editing the initramfs-tools.conf etc) but nothing has worked, any ideas anyone?

Many Thanks in Advance

---

### Post by godspeedmav on 2011-02-23
> I have followed the general advice on this forum (editing the initramfs-tools.conf etc) but nothing has worked, any ideas anyone?

I don't know which advice you've followed but I've seen this guide that solved that kind of errors. But give it a try if you haven't done it already!! :)


Open up a terminal; Go to the **Menu** > **Accessories** > **LXTerminal**

1) Make a back up of the original .conf file;

```
sudo cp /etc/initramfs-tools/initramfs.conf /etc/initramfs-tools/initramfs.conf.backup 
```

2) Edit that initramfs.conf file;

```
gksudo leafpad /etc/initramfs-tools/initramfs.conf 
```

Press Enter

3) Replace

```
MODULES = most
``` to ```
MODULES = dep
```

4) Save the file and close.

5) Now to reinstall initramfs-tools;

```
sudo apt-get install --reinstall initramfs-tools
```

6) Close the terminal after the process/reinstallation. Try a reboot and see if the error still shows up or not.

**[COLOR="Red"]NOTE:[/COLOR]** if there is a problem restore the original initramfs.conf by doing this;

```
sudo mv /etc/initramfs-tools/initramfs.conf.backup /etc/initramfs-tools/initramfs.conf 
```

---

