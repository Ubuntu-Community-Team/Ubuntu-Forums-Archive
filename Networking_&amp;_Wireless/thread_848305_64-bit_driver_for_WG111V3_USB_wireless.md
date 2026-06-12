---
title: "64-bit driver for WG111V3 USB wireless"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by kenfeyl on 2008-07-03
Hi folks. I'm trying to use my NetGear WG111V3 USB wireless stick with Ubuntu. I'm on an AMD64 dual-core running Hardy. Here are the things that I've tried unsuccessfully:

[LIST]
[*]Following the steps in [http://ubuntuforums.org/showthread.php?t=732827](http://ubuntuforums.org/showthread.php?t=732827), which provides a link to the driver .inf files for use with ndiswrapper. Unfortunately, the main file it uses is a 32-bit driver -- after installing with ndiswrapper and modprobe'ing there's a "kernel is 64-bit but Windows driver is not 64-bit message" sitting in /var/log/syslog. It doesn't work. For the heck of it, I also tried using the Vista 64-bit .inf -- which didn't work, giving a bunch of "Bad Symbol" messages in syslog.
[*]From a separate Web site I found that WG111v3 is using the RTL8187B chipset. On the RealTek site I found a RTL8187B x64 driver, which I installed using ndiswrapper. It doesn't associate it with the stick in the USB drive. I forced it using ndiswrapper -a <devid> <module>. After modprobe'ing, bad news -- system freezes up and won't reboot with the stick in the drive. Computer's fine after removing the stick but the wireless is still not working.
[/LIST]

Okay, so I need some suggestions for how to get an x64 driver for my WG111v3 USB wireless stick. On the box it does claim to work for 64-bit XP, but since my box only has Vista, not 64-bit XP, I get only the Vista drivers when I install on Windows. Neither setup.exe /a nor CabExtract on the device setup file can get me that elusive x64 .inf file. Any suggestions?

---

### Post by the goat boy on 2008-07-09
bump

i am stuck here too

please help us!

---

### Post by dslecomber on 2008-08-09
Hi

I have successfully got my WG111v3 USB wireless to connect with Hardy and 64-bit.

Do not try ndiswrapper - 64-bit does not work, neither Vista64 nor regular drivers will do it.  I also locked up a 32-bit old Fedora machine trying ndiswrapper.

The steps to do this will only take a few minutes.  

This USB stick runs a Realtek 8187b.  There are drivers for this, but they're not ready for the standard kernel yet, the following website is from someone who has modified ones direct from Realtek to support the 8187b, along with another for the 2.6.24 kernel.

[http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/)

I had to make one further mod to the source beyond what was on this site 

The steps are:

  wget [http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz](http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz)
  wget [http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch](http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch)

  tar zxvf rtl8187b-modified-dist.tar.gz
  cd rtl8187b-modified
  patch -p1 < ../2.6.24.patch

Now insert a new line 98 into rtl8187/r8187_core.c 
	{USB_DEVICE(USB_VENDOR_ID_NETGEAR, 0x4260)},

[this adds recognizing the Netgear device]

And at line 2855 -- immediately above the "case 0x8189:" add the line:

 case 0x4260:

[this signifies the card to be an rtl8187b, not a rt8187]

then, from the directory you were (rtl8187b-modified) do

 chmod +x makedrv
 ./makedrv

 sudo cp */*.ko /lib/modules/`uname -r`/ 
 sudo depmod -a 
 sudo modprobe r8187

Now stick your USB key in (or pull out and re-insert if it's already in!)

Your machine should now work!  iwconfig will show the card, and from there, proceed as normal with your wireless configuration.

I'll be sending the maintainer of the tarballs above a proper patch file to make this easy, but for now the above will work.

Hope this helps you!

David

---

### Post by onfyreforjesus on 2008-10-29
even with the RC ubuntu intrepid, my wg111v3 doesn't work... will does this how to hold good with 2.6.27 kernel too?

---

### Post by Tony Flury on 2008-12-23
I tried this - on the 2.6.24-18-generic kernel - when i ran ./makedrv i got all sorts of warnings include a load of undefined symbol errors - it did however make a set of .ko files.

I attach a file containing the errors : 

when i ran the modprobe command i got this : 

```

tony@laptop:~/rtl8187b-modified$ sudo modprobe r8187
WARNING: Error inserting ieee80211_rtl (/lib/modules/2.6.24-18-generic/ieee80211-rtl.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting r8187 (/lib/modules/2.6.24-18-generic/r8187.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

there appeared to be nothing relevant in dmesg 

I don't know enough to know how to fix it - but i know that the usb stick works out of the box on both windows XP and 8.10 - on this same laptop.

---

### Post by linuxishard on 2009-01-03
hi, i have this same issue, its a real shame, this works first go with ndis on i386, but no hope with amd64, 
surely this has to have a fix soon, 
tried the fix posted above, but this wont seem to work on intrepid,
i really really need this to work,
i live in an location where the only internet access is shared wifi from a distance, and if this adapter wont work i don't have another that will work from this range. 

PLEASE HELP.
it sucks since this adapter is very common, anyone who buys a netgear wifi router will have one of these usb adapters, it comes with the box.

---

### Post by linuxishard on 2009-01-03
OK, had a good old google, and read what i can,

i think for me, right now, with this issue and all the others that me and my system face with 64bit, its time for i386 again,
i have to say its just not worth the fuss, 
we all know we can install and get online with our wg111v3 adapter, within 45mins from start to finish, no issues.

although, when this gets fixed, you bet ill be back on amd64, 
but for now, i need internet, and i NEED to scrap this windows..
i only installed it to write these posts, SO BYE BYE WINDOWS and BYE BYE AMD64 linux.. hello again i386.

---

### Post by ttalin on 2009-11-24
This is not a reply, but another question. I'm trying to have my WNDA3100 USB work under Ubuntu 8.04 on a dual boot 64-bit Vista. For a while, I could not get drivers to load under ndiswrapper; finally got net5211 driver to load, but still couldn't make it work. Then a few days back I came across your thread. 
     I meticulously followed dslecomber's instructions replacing 4260 with 9010, the proper Netgear ID for my USB. Everything ran smoothly, but I haven't been able to get it to work. I tried a few other things like copying the *.ko files to  /lib/modules/2.6.24-24-generic/net (as well as to the directory above); adding r8187 to /etc/modules etc. I was wondering if you had any suggestions. 
     One question I have is how do I check whether the USB is being detected by the modified code for r8187; ndisgtk is still detecting net5211, but I'm trying to get it to work without ndiswrapper and I don't know whether the modified r8187 code is recognizing the USB. I know that iwconfig is not showing any wireless networks. 
     Thanks, 
      Talin

---

