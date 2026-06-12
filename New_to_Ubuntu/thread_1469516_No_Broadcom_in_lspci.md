---
title: "No Broadcom in lspci"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2010-05-02
I installed Lucid yesterday and everything went fine until I hit suspend. When I resumed my system could no longer see my broadcom wireless chip. I tried lspci, lshw, I even reinstalled Vista to check device manager but it wasn't there. I have Lucid reinstalled but still no wireless. I have a Compaq laptop so support is useless because (and anyone with an HP/Compaq will agree with this) HP support personnel know virtually nothing (my apologies to the .000001% who know something about computers). I am at a loss here. I have tried removing the battery and holding the power button as it seems to reset the card which has some kind of a failsafe but that only worked once and then broke next time I suspended. I even removed the door on the bottom of my computer and disconnected and reconnected the leads to the chip itself to see if it would reset, to no avail. This computer is virtually useless without wireless for me. I would really appreciate a response.

---

### Post by Xbehave on 2010-05-02
If the card isn't showing up under windows either, then check the physical switch and your bios.

---

### Post by lkraemer on 2010-05-02
As a Compaq Laptop user/lover lets' try and get your baby working......

If you previously installed Vista, or XP and your Wifi had problems
maybe the Wifi card is defective.  That could be one of the first
things to try.  Then when it is working leave it ENABLED and exit
Windows as you normally would.  From that point on don't touch
the Wifi Button, or whatever toggles it ON/OFF.

Now, We need more information.....
What Version of Ubuntu? 32 Bit or 64 Bit?

Open a Terminal Window and use these commands to get
more information on your hardware, wireless, Windows loaded drivers,
and Linux drivers that are currently blacklisted. You MUST use the
Proper Windows brivers for 32 or 64 Bit to match the 32 or 64 Bit
Version of Ubuntu. You need the .inf and .sys files.......

Use copy & paste to prevent typos!
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf 
iwconfig

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
Post the output of each command listed above ........

Your options that can be used:
1. Ndiswrapper and a Windows Driver....bcmwl5.inf & sys
2. bcm43xx module and some Firmware.... B43 & B43legacy *.fw
3. b43 and some Firmware that was downloaded/extracted when you
enabled the Driver.

For your machine and 10.04 Option #3 is probably the best, unless
you just want to use the Windows Drivers.

So, chop, chop let's get going.......

Follow along on:
[http://ubuntuforums.org/showthread.php?p=9217561#post9217561](http://ubuntuforums.org/showthread.php?p=9217561#post9217561)
Posting #7 and Posting #2.

lk

---

### Post by Martin Marshalek on 2010-05-03
Well, I just noticed that everyone responded to the post. Thanks guys. Anyway, I just got home so I can now go to trying some things. I don't know if it's a driver issue though as I did install the Broadcom STA driver and it worked fine for a little while. I've never had a problem with this driver and I've been using it since Intrepid. As for my current version, I have 64 bit Lucid. I can't seem to get it to work in Windows when I reinstall it so I've been focusing on Ubuntu. For me, it seems to work fine until I enter suspend mode and it stops functioning after resume. This worked without disabling the card a few times but then it just stopped working after it came back from resume. It simply does not show up in lspci or lshw. I even went so far as to open up the laptop and remove the leads to the chip to try to reset it (I'm pretty sure that I didn't break anything though as it worked after I tried it the first time the other day). I am curious to check my blacklist file though. I will report back after I try a few of your recommendations.

---

### Post by randolf_ambrose on 2010-05-03
my friend used to have similar issues...

but for him, the real problem was with the wifi button... sometimes even when you slide the button, wifi wont be activated... it'd still be red instead of blue!!!

but as i see it, your case if different...

do mention if you manage to rectify it... i sure would like to know what happened!!!

i also recommend that you check the button again!!!

---

### Post by Martin Marshalek on 2010-05-03
Well, I did find out something new about my computer. The wireless adapter isn't actually part of the motherboad. It actually uses Mini-PCI Express (the laptop equivalent of PCI Express) which makes it easy for me to buy a new card and try that out. My question is, are there any retail stores (like Radioshack or BestBuy) that would carry that kind of stuff?

---

