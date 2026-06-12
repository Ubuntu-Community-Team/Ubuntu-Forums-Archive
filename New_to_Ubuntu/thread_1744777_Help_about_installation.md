---
title: "Help about installation"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by NARWH4L on 2011-04-30
I have recently been trying to install Ubuntu 11.4 on my Desktop Computer. It is a Dell Dimension E310. I Download the Natty .iso file and the "Universal USB Installer" reccommended on Ubuntu's Website. I put the .iso on my 8GB Flash Drive (SanDisk), and went to boot from it by pressing "F2" and entering the Boot Startup Selections screen where I changed the values so it would Boot from the Flash Drive instead of my HD. When I saved changes and booted the Comp, it just said "Boot Error".
 
What did I do wrong?

---

### Post by TeoBigusGeekus on 2011-04-30
What do you mean by "I put the iso in my flash drive"?
Did you just copy it in there?

---

### Post by corncob on 2011-04-30
> **NARWH4L said:**
> I have recently been trying to install Ubuntu 11.4 on my Desktop Computer. It is a Dell Dimension E310. I Download the Natty .iso file and the "Universal USB Installer" reccommended on Ubuntu's Website. I put the .iso on my 8GB Flash Drive (SanDisk), and went to boot from it by pressing "F2" and entering the Boot Startup Selections screen where I changed the values so it would Boot from the Flash Drive instead of my HD. When I saved changes and booted the Comp, it just said "Boot Error".
 
What did I do wrong?

Try something different.  Burn the contents of the iso to a CD and boot from that.  If you're using Windows you need to right click on the iso and select burn contents.  Using the windows CD writer (or whatever they call it) will only copy the iso file and it won't work.  If it still gives a boot error try downloading it again and starting over.

---

### Post by NARWH4L on 2011-04-30
> **TeoBigusGeekus said:**
> What do you mean by "I put the iso in my flash drive"?
Did you just copy it in there?
 
I put the file in via the USB Program I mentioned.
 
 
I don't have any 2GB CD-ROMs, so I have to use a Flash Drive.

---

### Post by oldos2er on 2011-04-30
[https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows](https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows)

---

### Post by TeoBigusGeekus on 2011-04-30
2gb? Where did you get it from?
Go [here]("http://www.ubuntu.com/download/ubuntu/alternative-download#bt"), select the torrent that corresponds to your system, download it and burn it to a cd.

---

### Post by NARWH4L on 2011-04-30
> **TeoBigusGeekus said:**
> 2gb? Where did you get it from?
Go [here]("http://www.ubuntu.com/download/ubuntu/alternative-download#bt"), select the torrent that corresponds to your system, download it and burn it to a cd.
 
Ubuntu's site says when downloading their OS you'll need a CD of over 2GB in Memory.

---

### Post by TeoBigusGeekus on 2011-04-30
Can you give us a link with this quote?

---

### Post by Dutch70 on 2011-04-30
The live "cd" download obviously is made to fit on a cd so it's less than 700MB. 
*(unless there is a bug, which I've seen happen, but then it was 710MB)*

I would use the usb though. It's easier, faster, cheaper & more environment friendly.

Try using unetbootin to put it on the usb stick.
[[COLOR="RoyalBlue"]http://www.pendrivelinux.com/using-unetbootin-to-create-a-live-usb-linux/[/COLOR]]("http://www.pendrivelinux.com/using-unetbootin-to-create-a-live-usb-linux/")

Also, you need to check the md5sum of the downloaded iso.
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")

and check the cd/usb for defects.
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

If those last 2 things are bad, it won't matter what you put it on.

---

### Post by NARWH4L on 2011-04-30
> **TeoBigusGeekus said:**
> Can you give us a link with this quote?
 
 
 [https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows](https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows)
 
Under the Prerequisites.

---

### Post by TeoBigusGeekus on 2011-04-30
I stand corrected - the usb drive has to be 2gb (why though?)
But the cd doesn't have to. Just grab a normal 700mb one, burn the iso and boot with it.

---

### Post by Dutch70 on 2011-04-30
> **TeoBigusGeekus said:**
> I stand corrected - the usb drive has to be 2gb (why though?)
But the cd doesn't have to. Just grab a normal 700mb one, burn the iso and boot with it.

That is wrong! 

I know that's what the site says, but I can verify that it is wrong. 
You can use a 1GB usb stick. The only reason you can't use a 700mb usb stick, is probably because they don't make one. :)

---

### Post by dniMretsaM on 2011-04-30
> **NARWH4L said:**
> [https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows](https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows)
 
Under the Prerequisites.

That's a 2GB /USB stick./ Not a CD. The Live CD image is just under 700MB.

---

### Post by TeoBigusGeekus on 2011-04-30
> **Dutch70 said:**
> That is wrong! 

I know that's what the site says, but I can verify that it is wrong. 
You can use a 1GB usb stick. The only reason you can't use a 700mb usb stick, is probably because they don't make one. :)

Thank god, I thought I was going nuts.

---

### Post by Dutch70 on 2011-04-30
> **TeoBigusGeekus said:**
> Thank god, I thought I was going nuts.

LOL
Yeah, I was helping a guy that said he used a cd, because he only had a 1GB usb stick. Not knowing what the website recommended. 
I advised him that a 1GB usb stick is bigger than a cd. 

Short story, we got a good laugh out of it, and he successfully installed Ubuntu with a 1GB usb stick.
*(of course you have to download the live cd iso) *

I've been looking for the thread, but couldn't find it.

---

### Post by corncob on 2011-04-30
> In order to install a fully working Ubuntu operating system on your USB flash drive make sure that:

    Your flash Drive has more than 2GB of memory
    Your flash Drive is bootable
    Your flash Drive has a high read/write speed and is USB 2.0 enabled 
Aren't they talking about a fully functional persistent Ubuntu installation and not just a drive holding the contents of the iso so as to be used to install Ubuntu on a computer like you would from a CD?  (I don't know if I'm making myself clear :confused:)

---

### Post by Dutch70 on 2011-04-30
> **corncob said:**
> Aren't they talking about a fully functional persistent Ubuntu installation and not just a drive holding the contents of the iso so as to be used to install Ubuntu on a computer like you would from a CD?  (I don't know if I'm making myself clear :confused:)

Yes they are corncob, if you read exactly where the link leads you. However if you go to the top of the page, then click "prerequisites" it tells you that you need a 1GB stick for a netbook or a 2GB stick for a Desktop.

---

### Post by NARWH4L on 2011-04-30
I managed to get Ubuntu 11.4 on my computer, thus this thread is not needed anymore.

---

### Post by dniMretsaM on 2011-04-30
Glad you got it to work! It'd be awesome if you marked this thread solved.

---

### Post by Quackers on 2011-04-30
Just as an extra possibility, it may be that your 8GB flash drive (due to its size) is being recognised by your bios as a USB HDD. One of my flash drives is recognised that way. You may need to choose that option to boot from rather than the flash drive option. It's worth a try.

oops too late I see :-)

---

