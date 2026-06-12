---
title: "Install Vista from USB Flash Drive - UBUNTU"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by fremantle on 2010-06-24
Im on 9.10

take a loot at this tutorial [http://kurtsh.spaces.live.com/blog/cns!DA410C7F7E038D!1665.entry](http://kurtsh.spaces.live.com/blog/cns!DA410C7F7E038D!1665.entry)


can anyone tell me how to do this on ubuntu? I dont have a dvd, i have the .iso file. Does linux have any virtual drive programs (like magiciso) that i can use to mount the image file?

and also, terminal commands to do the formatting and copying.

thanks in advance (:

---

### Post by ronnielsen1 on 2010-06-24
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Unetbootin can do it

[http://jaxov.com/2009/09/install-windows-7-from-usb-stick-easily-unetbootin/](http://jaxov.com/2009/09/install-windows-7-from-usb-stick-easily-unetbootin/)

---

### Post by fremantle on 2010-06-24
thankx. but hey, i need to format my usb from fat32 to ntfs. how can i do that in linux???

---

### Post by wilee-nilee on 2010-06-24
> **fremantle said:**
> Im on 9.10

take a loot at this tutorial [http://kurtsh.spaces.live.com/blog/cns!DA410C7F7E038D!1665.entry](http://kurtsh.spaces.live.com/blog/cns!DA410C7F7E038D!1665.entry)


can anyone tell me how to do this on ubuntu? I dont have a dvd, i have the .iso file. Does linux have any virtual drive programs (like magiciso) that i can use to mount the image file?

and also, terminal commands to do the formatting and copying.

thanks in advance (:

It can be done but it would be much easier to just get a dvd and burn it. I have only been able to get a thumb loaded with a XP install from a MS environment using this
[http://wintoflash.com/download/en/](http://wintoflash.com/download/en/)
It was a legitamate ISO of XP if your is then this will work in widows probably

---

### Post by fremantle on 2010-06-25
for now im just going to try unetbootin. can anyone plz tell me how to format fat32 to ntfs in ubuntu?

---

### Post by ronnielsen1 on 2010-06-25
I believe unetbootin will automatically do this for you. I've never had a problem with it

---

### Post by fremantle on 2010-06-25
[FONT=Impact]ok
[/FONT]

---

### Post by wilee-nilee on 2010-06-25
> **fremantle said:**
> for now im just going to try unetbootin. can anyone plz tell me how to format fat32 to ntfs in ubuntu?

I don't think this is going to work, I don't think unetbootin will even load to a ntfs and even if it does I doubt if this will boot.

But if you want to change a partition type on a thumb use gparted in system-admin-gparted. You may have to install it since you don't seem to be aware of it in the terminal
```
sudo apt-get install gparted
``` If unetbootin does load it then make sure the partition on the thumb is set with the boot flag with gparted.

If you have at least 2 gigs of ram I think your going to be better off with Vista in the sun Vbox virtual the puel version.

MS has all there installs set to be very hard to load to a thumb, W7 will with the MS W7 DVD/Thumb Loader in a MS environment.

---

### Post by wilee-nilee on 2010-06-25
Just for reference here is a screenshot of the W7 install in sdc1 and Lucid in scd2. I used the MS loader for W7 though to load the thumb.

[ATTACH]161491[/ATTACH]

---

### Post by ronnielsen1 on 2010-06-25
[http://www.addictivetips.com/windows-tips/install-windows-7-from-usb-drive-requires-2-simple-steps/](http://www.addictivetips.com/windows-tips/install-windows-7-from-usb-drive-requires-2-simple-steps/)

[http://jaxov.com/2009/09/install-windows-7-from-usb-stick-easily-unetbootin/](http://jaxov.com/2009/09/install-windows-7-from-usb-stick-easily-unetbootin/)

[http://forums.mydigitallife.info/threads/7850-Installing-Windows-7-From-USB-Drive-3-Steps-Easy-Process](http://forums.mydigitallife.info/threads/7850-Installing-Windows-7-From-USB-Drive-3-Steps-Easy-Process)

---

### Post by wilee-nilee on 2010-06-25
> **ronnielsen1 said:**
> [http://www.addictivetips.com/windows-tips/install-windows-7-from-usb-drive-requires-2-simple-steps/](http://www.addictivetips.com/windows-tips/install-windows-7-from-usb-drive-requires-2-simple-steps/)

[http://jaxov.com/2009/09/install-windows-7-from-usb-stick-easily-unetbootin/](http://jaxov.com/2009/09/install-windows-7-from-usb-stick-easily-unetbootin/)

[http://forums.mydigitallife.info/threads/7850-Installing-Windows-7-From-USB-Drive-3-Steps-Easy-Process](http://forums.mydigitallife.info/threads/7850-Installing-Windows-7-From-USB-Drive-3-Steps-Easy-Process)

Just because a web link says it will; doesn't make it so, but hey if it works great. These are also W7 links not Vista. There is a MS W7 loader already anyway, it just has to be used in Windows.

---

### Post by fremantle on 2010-06-25
> **ronnielsen1 said:**
> [http://www.addictivetips.com/windows-tips/install-windows-7-from-usb-drive-requires-2-simple-steps/](http://www.addictivetips.com/windows-tips/install-windows-7-from-usb-drive-requires-2-simple-steps/)

[http://jaxov.com/2009/09/install-windows-7-from-usb-stick-easily-unetbootin/](http://jaxov.com/2009/09/install-windows-7-from-usb-stick-easily-unetbootin/)

[http://forums.mydigitallife.info/threads/7850-Installing-Windows-7-From-USB-Drive-3-Steps-Easy-Process](http://forums.mydigitallife.info/threads/7850-Installing-Windows-7-From-USB-Drive-3-Steps-Easy-Process)
  can u use microsofts tool to install vista?

edit:: nevermind. let me format my usb to ntfs

---

### Post by ronnielsen1 on 2010-06-25
I've never tried ms tool. I have tried the unetbootin method and it does work

---

### Post by wilee-nilee on 2010-06-25
> **ronnielsen1 said:**
> I've never tried ms tool. I have tried the unetbootin method and it does work

With what? Ithink if it worked with a MS install ISO you were just lucky, and had a thumb that worked. But as I said if something works thats graet, but I have used a hnadful of thumbs and only have been able to load a thumb with the MS tool or the link I provided.

---

### Post by fremantle on 2010-06-25
hy. i installed gparted and ntfsprogs. but the format to option is not active

---

### Post by wilee-nilee on 2010-06-25
From your screenshot.
[ATTACH]161495[/ATTACH]

If this doesn't unmount it use the disk utility to unmount the thumb. You can't ever adjust any thumb, or HD while mounted.

---

### Post by fremantle on 2010-06-25
> **wilee-nilee said:**
> From your screenshot.
[ATTACH]161495[/ATTACH]

If this doesn't unmount it use the disk utility to unmount the thumb. You cant ever adjust any thumb, or HD while mounted.

now thats something new... thanks! :)

---

### Post by fremantle on 2010-06-25
i lost like 43 mbs of space in the thumb.. now starting unetbootin

---

### Post by wilee-nilee on 2010-06-25
> **fremantle said:**
> i lost like 43 mbs of space in the thumb.. now starting unetbootin

May the force be with you.;)

---

### Post by fremantle on 2010-06-25
Perfectly done! Now i am wrinting this post from windows vista :D
 
thnks everyone!

---

### Post by wilee-nilee on 2010-06-25
> **fremantle said:**
> Perfectly done! Now i am wrinting this post from windows vista :D
 
thnks everyone!

I didn't pickup that the virus thread and this one was by you, glad you got it going. When you are doing multiple work the people get lost at least for me.

---

### Post by ronnielsen1 on 2010-06-25
> With what? Ithink if it worked with a MS install ISO you were just  lucky, and had a thumb that worked. But as I said if something works  thats graet, but I have used a hnadful of thumbs and only have been able  to load a thumb with the MS tool or the link I provided.Um, with windows 7 and unetbootin. It worked. I had a friend that also did it. Seriously.

---

