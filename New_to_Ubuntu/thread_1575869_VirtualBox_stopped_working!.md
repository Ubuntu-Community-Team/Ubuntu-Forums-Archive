---
title: "VirtualBox stopped working!"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-09-16
Hello:

I just completed the daily update and then tried to use VirtualBox and received this error msg that said to install 'virtualbox-ose-dkms' and then to do a 'sudo modprobe vboxdrv'

I re-installed 'virtualbox-ose-dkms' using Synaptic.

When I did 'sudo modprobe vboxdrv' in the terminal, I got this:

"Module vboxdrv not found"

Any suggestions?

Thanks,

---

### Post by CharlesA on 2010-09-16
When you reinstalled, it should have added those kernel modules automatically.

Did it do that?

Maybe it's different between the non-free version and the OSE one.

---

### Post by Robert.Thompson on 2010-09-16
> **CharlesA said:**
> When you reinstalled, it should have added those kernel modules automatically.

Did it do that?



How would I know? (How would I determine if it did that?)

---

### Post by M93 on 2010-09-16
yes it happened to me before all i did was downloaded it again from [here]("http://www.virtualbox.org/wiki/Linux_Downloads")
re-installed it, and everything went fine
maybe it would work for u too :)

---

### Post by pricetech on 2010-09-16
I ran into this a few times with the OSE version under Hardy.  I just changed my kernel back to the previous one until the kernel headers for vbox got updated.

Workaround rather than a solution, but it works.

---

### Post by jeremy96 on 2010-09-16
[FONT=Comic Sans MS][SIZE=2]Try reinstalling VirtualBox by going into the terminal and typing in:

1st. sudo apt-get remove virtualbox-ose

2nd. sudo apt-get install virtualbox-ose

It should now work! :)
[/SIZE][/FONT]

---

### Post by Robert.Thompson on 2010-09-16
> **pricetech said:**
> I ran into this a few times with the OSE version under Hardy.  I just changed my kernel back to the previous one until the kernel headers for vbox got updated.

Workaround rather than a solution, but it works.

How do I do this?

Thanks

---

### Post by Robert.Thompson on 2010-09-16
> **M93 said:**
> yes it happened to me before all i did was downloaded it again from [here]("http://www.virtualbox.org/wiki/Linux_Downloads")
re-installed it, and everything went fine
maybe it would work for u too :)

Tried it but got: Conflicts with the installed package 'virtualbox-ose' when I tried to install.

Thanks

---

### Post by Robert.Thompson on 2010-09-16
> **jeremy96 said:**
> [FONT=Comic Sans MS][SIZE=2]Try reinstalling VirtualBox by going into the terminal and typing in:

1st. sudo apt-get remove virtualbox-ose

2nd. sudo apt-get install virtualbox-ose

It should now work! :)
[/SIZE][/FONT]

Tried it but still got the same error msg. Tried the above for virtualbox-ose-dkms but still got the same error msg.

Thanks,

---

### Post by sandyd on 2010-09-16
> **Robert.Thompson said:**
> Tried it but got: Conflicts with the installed package 'virtualbox-ose' when I tried to install.

Thanks
you have to remove the OSE (open source edition) of virtualbox first, they cannot be installed at the same time.

```

sudo apt-get remove virtualbox-ose
sudo apt-get autoremove
```

---

### Post by wilee-nilee on 2010-09-16
I use the puel version but I just use the native dkms.

---

### Post by Robert.Thompson on 2010-09-16
> **sandyd said:**
> you have to remove the OSE (open source edition) of virtualbox first, they cannot be installed at the same time.

```

sudo apt-get remove virtualbox-ose
sudo apt-get autoremove
```

Tried this and got:

Breaks existing package 'virtualbox-guest-additions' that conflict: 'virtualbox'. But the '/home/rob/Downloads/virtualbox-3.2_3.2.8-64453~Ubuntu~lucid_i386.deb' provides it via: 'virtualbox' 

Thanks,

---

### Post by Robert.Thompson on 2010-09-16
> **wilee-nilee said:**
> I use the puel version but I just use the native dkms.

English please!:)

---

### Post by Robert.Thompson on 2010-09-16
Should I just completely uninstall VB and then re-install it?

If I do this, all my virtual linux machines will be toast, right?

Thanks,

---

### Post by sandyd on 2010-09-16
> **Robert.Thompson said:**
> Tried this and got:

Breaks existing package 'virtualbox-guest-additions' that conflict: 'virtualbox'. But the '/home/rob/Downloads/virtualbox-3.2_3.2.8-64453~Ubuntu~lucid_i386.deb' provides it via: 'virtualbox' 

Thanks,
```

sudo apt-get remove virtualbox-guest-addons virtualbox virtualbox-ose virtualbox-guest-additions

```

---

### Post by wilee-nilee on 2010-09-16
> **Robert.Thompson said:**
> Should I just completely uninstall VB and then re-install it?

If I do this, all my virtual linux machines will be toast, right?

Thanks,

I don't think you would have been advised to reinstall if this endangered the OS in it. I have reinstalled, I just had to add the vdi(=vbox hard drive name) in .virtualbox in home back into the list, I think you're okay here, but lets get some other opinions.

You might consider the version that allows USB support and just install the Ubuntu dkms. There is a little more work to get USB working in the Vbox, ask if you go this route. The nice thing about this version is that you can use gdebi to unpack it and right on the gui of gdebi it will tell you what dependencies are missing.
[http://www.virtualbox.org/](http://www.virtualbox.org/)
Here is the guest additions pre-release.
[http://ubuntuforums.org/showthread.php?p=9810144](http://ubuntuforums.org/showthread.php?p=9810144)

---

### Post by Robert.Thompson on 2010-09-16
> **sandyd said:**
> ```

sudo apt-get remove virtualbox-guest-addons virtualbox virtualbox-ose

```

I tried this and got:

Breaks existing package 'virtualbox-guest-additions' that conflict: 'virtualbox'. But the '/home/rob/Downloads/virtualbox-3.2_3.2.8-64453~Ubuntu~lucid_i386.deb' provides it via: 'virtualbox' 

Thanks,

---

### Post by sandyd on 2010-09-16
> **Robert.Thompson said:**
> I tried this and got:

Breaks existing package 'virtualbox-guest-additions' that conflict: 'virtualbox'. But the '/home/rob/Downloads/virtualbox-3.2_3.2.8-64453~Ubuntu~lucid_i386.deb' provides it via: 'virtualbox' 

Thanks,
sorry. ive lost my spelling ability

---

### Post by CharlesA on 2010-09-17
Wow, that's strange. You could try this:

```
sudo apt-get purge virtualbox-ose --force-yes
```

The --force-yes switch is a tad dangerious, since it will cause apt-get to ignore warnings, but if you are just going to reinstall virtualbox, it shouldn't hurt anything.

---

### Post by Robert.Thompson on 2010-09-17
Thanks to all! :)

I opted to re-install Ubuntu completely - I am certain that I have screwed things up over the last 6 weeks, being a newbie and all.

I want a fresh start because I really like Ubuntu and never want to go back to Windows.

---

