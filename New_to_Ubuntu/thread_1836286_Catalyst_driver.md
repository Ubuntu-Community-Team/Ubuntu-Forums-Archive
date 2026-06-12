---
title: "Catalyst driver"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by peterson43 on 2011-08-30
I've been having some issues with my computer that I suspect might have something to do with the graphics card and/or driver. 

I recently bought a Dell 790 Optiplex (N series) and installed Ubuntu 11.04. My computer has a 512MB AMD RADEON HD 6350 graphics card, and when I did the Ubuntu installation I chose to use the proprietary driver. 

As I said, I've been having a couple of issues and I have the following questions regarding the drivers. 

1) Is the proprietary driver that I have installed the latest version of the Catalyst driver, or is it somehow different from the drivers on the AMD website? How can I tell? 

2) If I remove the Catalyst Driver using the 'Additional Drivers' tool in System Settings, do I need to install the open source drivers or will they be there automatically? 

3) Does anyone have a preference for the open source drivers over the proprietary drivers? I don't do any gaming, I just thought I would get the graphics card so that I could handle 3D graphics if I ever needed to. 

Thanks.

---

### Post by el_koraco on 2011-08-30
1) The version you installed via Additional drivers is Catalyst 11.4, the current version on the website is 11.8
2) You don't need to install anything else if you remove Catalyst
3) The open source drivers are better for regular use, on par with regard to a lot of 3D stuff, but lack in heat management, which might be a problem when using a laptop

---

### Post by alphacrucis2 on 2011-08-30
It's definitely worth installing the 11.8 version from AMD. There are a lot of bug fixes since 11.4. Download the 11.8 installer from the AMD website. Install using the buildpkg method. The guide for doing this is in the ubuntu ATI driver binary howto. You will need to adjust the commands given to match your ubuntu version and the file name of the installer (the name includes the version number).

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI  ]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI")

General procedure.

1. Download the latest linux driver installer from AMD (32 or 64 bit as per your Ubuntu version)
 
2. Completely erase the old Catalyst:

```
sudo apt-get --purge remove fglrx*
```

3. Install the driver via the buildpkg method as per the wiki.

4. Run aticonfig

```
sudo aticonfig --initial -f
```

5. Reboot.

---

### Post by peterson43 on 2011-08-30
> **alphacrucis2 said:**
> 
3. Install the driver via the buildpkg method as per the wiki.


I looked at the wiki giving the installation instructions. In step 11 the instructions say to type
```
sudo sh ati-driver-installer-11-2-x86.x86_64.run --buildpkg Ubuntu/maverick
```
I have 11.04 so do I replace "maverick" with "natty" at the end of the line?

---

### Post by Redblade20XX on 2011-08-30
In addition to the wiki that was given, here is another wiki for any supplementary questions!:p

[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

-Red

---

### Post by alphacrucis2 on 2011-08-30
> **peterson43 said:**
> I looked at the wiki giving the installation instructions. In step 11 the instructions say to type
```
sudo sh ati-driver-installer-11-2-x86.x86_64.run --buildpkg Ubuntu/maverick
```
I have 11.04 so do I replace "maverick" with "natty" at the end of the line?

Yes. For Natty the command will be:

```
sudo sh ati-driver-installer-11-8-x86.x86_64.run --buildpkg Ubuntu/natty

```


Note also the -11-2 has to be changed to -11-8 

AMD release an update every month hence 11-8 means 2011 August.

The command will cogitate for a while and when it finishes you should find it has created some deb files. You install them via sudo dpkg -i *.deb. The reason for doing it this way is to make sure the package manager knows that you have fglrx installed and also which version.

---

### Post by peterson43 on 2011-08-31
In the end I decided to go with the open source drivers. I did first replace the older Catalyst driver with the new Catalyst driver, but I still had the same problems (for instance when I would run glxgears in a terminal the gears would turn a few steps and then freeze for about 5 seconds and never run smoothly). 

I removed the Catalyst driver and went with the open source drivers and things seem to be working fine. In particular, now the glxgears command works smoothly.

---

### Post by marin123 on 2011-08-31
You might want to check this out, to see what you can expect from your graphic card in the future :)
[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

You can get your card name by typing:

```
lspci | grep VGA
```

If it isn't on the list, google it, because mine is Radeon HD 5650 and it says Redwood, but it's Evergreen platform. I hope I have been clear.

---

