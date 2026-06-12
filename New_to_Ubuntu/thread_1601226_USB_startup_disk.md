---
title: "USB startup disk"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by Messyhair42 on 2010-10-20
I'm want to use the Maverick ISO to turn a thumb drive (4GB) into a startup disk/mobile ubuntu setup. but i see the "create a USB startup disk" icon is gone from Lucid. how do i go about doing this now? my intention for the drive is more as an OS i can take from place to place, transfer documents and install programs, are there any changes i have to make in order to be able to modify the OS so it saves the changes?

---

### Post by StephenDavison on 2010-10-20
It looks like the Startup Disk Creator application can be installed from the Ubuntu repositories.  Try usb-creator-gtk or usb-creator-kde according to your flavor of Ubuntu.  UNetbootin would probably work too.

---

### Post by oregonbob on 2010-10-20
You will find a wealth of information on pendrivelinux.com

---

### Post by Messyhair42 on 2010-10-20
it looks like usb-creator-gtk is alrady installed, but i dont know how to open it, an application isnt displayed (even hidden) in /usr/share/applications or any of the other locations i think it might be, and i don't use terminals enough to know how to run it from there

---

### Post by beew on 2010-10-20
> **oregonbob said:**
> You will find a wealth of information on pendrivelinux.com

Pendrivelinux.com has almost no information if you use linux (say how to create a Fedora live usb with persistence in Ubuntu?) it is mainly for windows users and the apps only work in windows.

I remember I was pretty pissed off because of that. Everyone is catering to Windows.

---

### Post by beew on 2010-10-20
> **Messyhair42 said:**
> it looks like usb-creator-gtk is alrady installed, but i dont know how to open it, an application isnt displayed (even hidden) in /usr/share/applications or any of the other locations i think it might be, and i don't use terminals enough to know how to run it from there

It is called "Startup Disk Ceator". You should be able to find it under System > Administration.

If you can't find it go to System > Preference > Main Menu. Open up the Main Menu and on the left panel choose System > Administration. You should be able to find "Startup Disk Creator" on the right panel. If the box is not checked, check it. If it is checked already, uncheck it and recheck it. Then close Main Menu.

Now you should be able to find the Startup Disk Creator under System > Administration.

---

### Post by oregonbob on 2010-10-20
> **beew said:**
> Pendrivelinux.com has almost no information if you use linux (say how to create a Fedora live usb with persistence in Ubuntu?) it is mainly for windows users and the apps only work in windows. I remember I was pretty pissed off because of that. Everyone is catering to Windows.

Huh? You must be going to a different "pendrivelinux.com", go there now. Of course they do have a lot on Windows because 98% of the users out there run...Windows and many want to explore linux. So you determined because you can't make a stick with Fedora using Ubuntu therefore it is Windows? How many websites out there are going to tell you how to do that? It is a challenge just to make a Ubuntu 10.10 stick with Ubuntu 10.04 (at least a couple of weeks ago).

By the way, I have discovered that site has many technical how-tos that are not indexed on the front page. I found them by other sources.

Now at least offer up a single website you found that has much more on USB stick linux using various OS. One with more info than pendrivelinux.com .

---

### Post by tajiknomi on 2010-10-20
[SIZE=2]*Have a look at *[/SIZE][SIZE=2]***Usb-creater-gtk***[/SIZE]....([COLOR=black]**In synaptic**[/COLOR])

---

### Post by C.S.Cameron on 2010-10-20
You can always do a Full install to a 4GB flash drive.
After booting the Live cd run Install.
When you get to partitioning make sure you are installing the boot loader to the flash drive.
I can provide a step by step for 10.04 or 10.10 if you are interested.

---

### Post by The Big Green Machine on 2010-10-21
Sorry, I'm sure ubunto newbies like me can make things frustrating.

I have downloaded Maverick onto my PC, I'm preparing to create an ISO on a USB thumb drive. It is an 8 gig drive. Does it have to be a new empty drive or can I continue to use the data already on it?

If I have to, I will stop and get a new USB  thumb drive, because all of my personal stuff is on this one.

Thanks,

The Big Green Machine

---

### Post by k3lt01 on 2010-10-21
You could give [this a try]("http://ubuntuforums.org/showthread.php?t=1288604"), it is how I do it.

---

