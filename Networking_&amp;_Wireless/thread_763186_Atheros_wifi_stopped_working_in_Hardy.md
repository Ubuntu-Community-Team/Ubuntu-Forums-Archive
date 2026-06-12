---
title: "Atheros wifi stopped working in Hardy"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by osarusan on 2008-04-22
I have a Fujitsu Stylistic ST5112 Tablet PC that was working fine in Gutsy. I upgraded to Hardy the other day when the Release Candidate came out, and now the wireless doesn't work! :-(

After I upgraded, Hardy found my Atheros wifi card and hardware abstraction layer drivers. Before then, in Gutsy, I'm not sure which drivers I was using actually... but I guess not the Atheros ones. Anyway, now I can see the wireless networks with my cards, but I can no longer connect to them. When I try, the icon just spins around for 30 seconds or so and then gives up. I've tried disabling the new Atheros restricted drivers but all that does is make me unable to do anything with wireless.

Does anyone know what might be going wrong, or how I might fix it?

Thanks!

---

### Post by kevdog on 2008-04-22
Boot into the old kernel and download the madwifi sources.

Boot back into the new kernel (or simply download the madwifi sources and transfer them from another computer to the hardy computer).  

Install the build-essential and linux-header files from the installation disk.

Compile and manually install the madwifi drivers.  modprobe the madwifi kernel module, use it -- Enjoy!!!

Get back to me if you need specific instructions.

---

### Post by nigj on 2008-11-23
I'm not sure, but I think that I have experienced something similar when I tried me on the Mint 6. edition. My network card was visible and apparently active. But it did not connect up.:(
My question is: how to download madwifi sources to a place where I can find it again so that I can add files to a usb stick. 
:confused:
And of course, how to find it again in the terminal window so that I get the error corrected when the new os is installed.
:popcorn:
Hope it is ok for me to interfere like this:)

---

### Post by eks on 2008-11-23
It broke on the upgrade to Hardy because you would have to compile again the driver.

If you upgrade to Intrepid now and use the builtin driver you shouldn't worry about it anymore. Take a look at the wiki:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

