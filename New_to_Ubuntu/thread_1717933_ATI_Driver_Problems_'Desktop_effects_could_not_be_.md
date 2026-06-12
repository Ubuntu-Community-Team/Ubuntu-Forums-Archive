---
title: "ATI Driver Problems 'Desktop effects could not be enabled' (how often do you backup?)"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by giddyup306 on 2011-03-30
I did something stupid yesterday, and messed up my computer to the point where I couldn't fix it.  I might have been able to revive it, but my internet was down, and just decided to install a distro copy that I made back in November.  Since this was not a clone, I spent all day yesterday, and all day today getting everything back to the way it was before I messed up my system.  For all the other problems, a simple google search yields me with results in a few searches, but I am still unable to get my Compiz working again (it worked before).  

I didn't find an answer to my problem, but I found a lot of info.  I have an ATI Rdeon 5870 card, and it looks like the proprietary driver won't allow me to enable "custom" or "extra" under the "Visual Effects" settings.  

I found this but it makes no sense to me.

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide) 

I then found this.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Which lead me to this...

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

I then ran...

```
  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```

After all that I went back to the previous page, and it looked like everything should have been installed, and the rest was just configuring.  Compiz still doesn't work, and under System > Administration > Additional Drivers, it shows that there aren't any drivers installed.  

What am I missing?

Oh, and if anyone is curious as to what I was doing, I was making a backup with remastersys.  I accidentally typed in the command to do a clone rather than a dist copy, and I didn't have enough room on my drive.  Oh well.

So how often do you backup?  Like I said, my last one was from November...

---

### Post by alphacrucis2 on 2011-03-30
> **giddyup306 said:**
> I did something stupid yesterday, and messed up my computer to the point where I couldn't fix it.  I might have been able to revive it, but my internet was down, and just decided to install a distro copy that I made back in November.  Since this was not a clone, I spent all day yesterday, and all day today getting everything back to the way it was before I messed up my system.  For all the other problems, a simple google search yields me with results in a few searches, but I am still unable to get my Compiz working again (it worked before).  

I didn't find an answer to my problem, but I found a lot of info.  I have an ATI Rdeon 5870 card, and it looks like the proprietary driver won't allow me to enable "custom" or "extra" under the "Visual Effects" settings.  

I found this but it makes no sense to me.

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide) 

I then found this.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Which lead me to this...

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

I then ran...

```
  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```

After all that I went back to the previous page, and it looked like everything should have been installed, and the rest was just configuring.  Compiz still doesn't work, and under System > Administration > Additional Drivers, it shows that there aren't any drivers installed.  

What am I missing?

Oh, and if anyone is curious as to what I was doing, I was making a backup with remastersys.  I accidentally typed in the command to do a clone rather than a dist copy, and I didn't have enough room on my drive.  Oh well.

So how often do you backup?  Like I said, my last one was from November...

With the 5870 you will definitely want the proprietary Catalyst fglrx driver. The one from the repos (hardware drivers) might be a bit old. AMD just released catalyst 11.3 yesterday so I would download that from AMD's website. You will want to install it using the buildpkg method as described in the binary driver howto.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

Note that the howto is for Cat 11.2 so you will have to modified the buildpkg command slightly to reflect 11.3

The general steps are:

1. Erase the existing fglrx from your system

sudo apt-get remove --purge fglrx*   (you already did this).

2. Generate the driver deb files from the downloaded driver installer from AMD as per the binary driver howto.

3. Install the driver deb files

sudo dpkg -i *.deb

4. Initialise the config

sudo aticonfig --initial -f

5. Reboot

---

### Post by giddyup306 on 2011-04-03
Yay!  I have my wobbly windows and desktop cube back!  BTW I just had to extract the .run file.  Didn't have to do all the other steps.

---

