---
title: "Trying to use Puppy linux to install 10.04"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by Diametric on 2011-03-25
Hello,

I put in a new HD and I am getting an error when attempt to install 10.04.  The error is "cannot mount to loop0"

So, I've got an .iso on a USB drive, and I'm using Puppy Linux cd now; how can I get 10.04 to install?   

I looked at Ubuntu site on how to make a usb startup, but it is only for MS, MAC and Ubuntu...and I don't know if that what I need to do...if so, how do i do via Puppy Linux.

thanks in advance!

---

### Post by wojox on 2011-03-25
Did you check the [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

Sounds like maybe a bad download or burn.

---

### Post by Diametric on 2011-03-25
Might be that.  I'll run another download and check.  Any info on how to make a usb startup using puppy linux?  I just found out that the Dell I bought a year ago off craigslist has a password set on the bios so I can't change the boot order.  Gotta love that!  I have no idea how to fix that.  Hopefully a google search yields some results

---

### Post by wojox on 2011-03-25
You could try downloading the .iso again and use the dd command. 

Plug in your usb stick and run 

```
dmesg | tail
```

It should show you your drive. Then something like

dd if=ubuntu.iso of=/dev/sdb

---

### Post by Diametric on 2011-03-26
Hey Wojox,

It was a bad download...two in fact.  On the third attempt I used a torrent to download instead and ran the md5sum and I'm in the middle of my 10.04 install now.  Thanks for your help...it's much appreciated.

Cheers,
-Dylan

---

