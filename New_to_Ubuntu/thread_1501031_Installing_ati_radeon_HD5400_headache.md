---
title: "Installing ati radeon HD5400 headache"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by DrWood on 2010-06-03
I have been using 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

and

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat105-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat105-inst.pdf)

to show me the way to install a ati radeon HD5400 graphics card.

I have installed all the prerequisite libs and followed instruction.

After successfully installing fglrx using apt-get, I rebooted. However instead of the nice info that the webpage displays I get

> X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16


NOT the desired result.

I did try the command

> sudo sh ./ati-driver-installer-10-5-x86.x86_64.run --buildpkg Ubuntu/karmic

with the binary package on my desktop (for simplicity). The shell returns an error

> sh: Can't open ./ati-driver-installer-10-5-x86.x86_64.run

I am sure that the process isnt supposed to be so hard. But I am a newb, so slap me hard with the "Dooh" stick.

---

### Post by DrWood on 2010-06-04
:popcorn:

bump

---

### Post by alphacrucis2 on 2010-06-04
> **DrWood said:**
> :popcorn:

bump

System Administration Hardware Drivers

should get you catalyst 10.4, or if you really want 10.5 then download from [www.amd.com](www.amd.com) and follow their instructions.

---

### Post by DrWood on 2010-06-04
I tried but the destructions were inaccurate.

I just solved the issue by going to 

[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

and doing

Latest update to package is in Lucid Repositories.

```
sudo apt-get update
sudo apt-get install fglrx fglrx-amdcccle fglrx-dev fglrx-modaliases
```

If you get this message when running the apt-get install command:
Building for architecture x86_64

```
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
update-initramfs: deferring update (trigger activated)
```


Then you need the kernel source header package, so first you need to remove the fglrx and install source-headers and install fglrx again. Tidious I know :(

```
sudo apt-get remove fglrx
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install fglrx
sudo aticonfig --initial
```

Reboot

---

### Post by alphacrucis2 on 2010-06-04
> **DrWood said:**
> I tried but the destructions were inaccurate.

I just solved the issue by going to 

[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

and doing

Latest update to package is in Lucid Repositories.

```
sudo apt-get update
sudo apt-get install fglrx fglrx-amdcccle fglrx-dev fglrx-modaliases
```

If you get this message when running the apt-get install command:
Building for architecture x86_64

```
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
update-initramfs: deferring update (trigger activated)
```


Then you need the kernel source header package, so first you need to remove the fglrx and install source-headers and install fglrx again. Tidious I know :(

```
sudo apt-get remove fglrx
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install fglrx
sudo aticonfig --initial
```

Reboot

Interesting. I installed an earlier version just by installing via the hardware driver menu. After that all I have done is downloaded and run the ati installer to get more recent versions followed by the obligatory sudo aticonfig --initial -f

Probably my package manager still thinks the old version installed by the menu method is the one still in use.

One thing you may need to do if you want to run desktop effects with the fglrx driver is to install the xorg backclear patch otherwise you will probably suffer the dreaded slow window restore issue. You can get the backclear patch for your version of xorg from this ppa:

[https://launchpad.net/~k0ekk0ek/+archive/ppa]("https://launchpad.net/~k0ekk0ek/+archive/ppa")

More info here:

[http://www.phoronix.com/forums/showthread.php?t=21846]("http://www.phoronix.com/forums/showthread.php?t=21846")

---

