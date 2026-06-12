---
title: "Live USB Files Not on Flash Drive"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by hopeididgood on 2009-07-21
I wanted to make a live usb drive.  Got UNetBootin from Applications > Add/Remove and downloaded the iso.  Ran the GUI -- most definitely selected the correct USB drive -- and thought it was successful.  I tried to boot from the flash drive and got an error saying that the kernel wasn't there...  Rebooted back into Ubuntu, checked it out and sure enough no files on the flash drive.  

Then I notice, that UNetbootin somehow created a new usb directory in my media directory (media/USB\040DISK) and all the files are there, instead...  This new USB directory is locked, permission for root only...  

Is it safe to log in as the root user and just delete this file?  (And what is the best/safest way to go about doing this?) 

Any ideas for why it failed to end up on my flash drive?

And suggestions for how to avoid this issue in the future -- and get the files actually onto the flash drive?

Thank you for any advice!

---

### Post by jeppewinther on 2009-07-21
I am guessing that mountpoint is where your USB drive mounts to. Was it mounted when you tried to create the Live USB stick?


You can safely remove the files, no problem. One idea might be to simple move them onto your USB drive though, since it sounds like it created a viable Live Stick, just not on an actual USB drive.

---

### Post by pizza-is-good on 2009-07-21
Try using the Ubuntu USB Startup disk creator.

---

### Post by hopeididgood on 2009-07-21
> **jeppewinther said:**
> I am guessing that mountpoint is where your USB drive mounts to. Was it mounted when you tried to create the Live USB stick?


You can safely remove the files, no problem. One idea might be to simple move them onto your USB drive though, since it sounds like it created a viable Live Stick, just not on an actual USB drive.

Yes, it probably was mounted...  Should I have unmounted the volume before starting the program?  

Thanks for mentioning that I can safely remove or move the files... 
What is the best way for me to do that?  Terminal gksudo nautilus?  


Thank you for your help!

---

### Post by hopeididgood on 2009-07-21
> **pizza-is-good said:**
> Try using the Ubuntu USB Startup disk creator.

I went with uNetBootin as I've used it (successfully!) before...  Definitely going to go with Ubuntu USB Startup Disk Creator in the future.  

Thank you for the suggestion!

---

