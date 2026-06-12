---
title: "Ubuntu on iMac 27 inch"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by chillyperson23 on 2009-11-29
Ive been trying to install Ubuntu on my new iMac.  When I tell it to install, it will show a list of things that its doing, then it stops and the screen starts flashing. Then it shows ubuntu@ubuntu  as if its asking what to do next. 

The only way to get it to install anything is to press F4 and run it in safe graphics mode. The problem with that is that I cant get the screen resolution to be in 16:9 or anything close, so everything is stretched.  

Also when it is up and running, I cant turn it off or put it to sleep. It says "The system is going down for reboot... NOW!" and nothing els happens. 

Anybody els have this problem or know how to fix it?

---

### Post by coffeecat on 2009-11-29
The ubuntu@ubuntu is a bash shell where the GUI has failed. If you're getting that, it sounds like a video card/driver problem. The video card on your 27" iMac is either an ATI Radeon HD4670 or HD4850 depending on the iMac model. Which means that the live CD will be using the open-source radeon driver. The resolution on that enormous screen is 2560x1440. I don't know, but I wonder if the radeon driver simply can't support that resolution.

You might find an answer in [the Apple Users subforum]("http://ubuntuforums.org/forumdisplay.php?f=328"). You could start a thread there if no one else can give a better answer in this thread.

You might also want to consider installing Ubuntu into a virtual machine with MacOS as the host. Have a look at [http://www.virtualbox.org/](http://www.virtualbox.org/) . Once you've got the guest additions installed in Ubuntu, that might solve your display problem.

---

### Post by cmaes on 2009-11-30
I had success getting the full 2560 x 1440 resolution on the 27'' iMac with the ATI/AMD proprietary FGLRX graphics driver. This driver is easily enabled under System > Administration > Hardware Drivers.  

For reference my machine has the ATI Radeon HD4850 and I am using Ubuntu 9.10.  I tried 9.04 first but had the same flashing issues reported by the OP.

---

### Post by Kobalt on 2009-11-30
Try to install the driver from the shell you have : 
```
sudo aptitude install xorg-driver-fglrx
```

---

### Post by mortenb on 2009-12-02
What kind of performance are you experiencing from that ATI card under ubuntu? I've been looking at getting the 27" imac but the ATI gfx has been holding me back.. Any problems with hardware acceleration or anything like that?

---

### Post by oneb on 2009-12-09
> **Kobalt said:**
> Try to install the driver from the shell you have : 
```
sudo aptitude install xorg-driver-fglrx
```

Hi,

I have the same problem. I can run the install of the gfglrx driver but then I get

```
update-initramfs is disabled since running on read-only media
```

and a bit later

```
ldconfig deferred processing now taking place
```

and the blinking goes on and I'm back at ubuntu@ubuntu...

Is there anything one can do about htis?

Thx,
oneb

---

### Post by Sand &amp; Mercury on 2010-02-16
I am a bit late responding to this but since I had the same problem...

At the boot options screen, hit F4 and choose 'safe graphics mode' -- then launch as usual. The generic ATI driver doesn't like the 27-inchers. If you want to get Compiz and other 3D stuff working during your LiveCD session, install the proprietary driver through the Administration menu once your session boots; after it's installed, simply log out and back in (using 'ubuntu' as the username and with no password) -- sit back and enjoy! 

... until the bloody thing overheats and freezes xorg because the cards in these particular iMacs are underclocked in Snow Leopard because the casing isn't dissipating the heat well enough to run the card at full pelt. **** this!

---

### Post by niffcreature on 2010-02-16
ubuntu@ubuntu? isnt that running off a live cd? youd probably have better luck actually installing it huh?
edit
sorry, didnt read the whole thread. 

since i already posted, i have to say what the HELL how can you mess up cooling in a 27 inch laptop? it has less than a few of these pieces of hardware right?
...and what does the unintended pun snow leopard at full pelt mean?
oh the unanswerable questions

---

### Post by Sand &amp; Mercury on 2010-02-20
> **niffcreature said:**
> since i already posted, i have to say what the HELL how can you mess up cooling in a 27 inch laptop? it has less than a few of these pieces of hardware right?
The aluminium casing is supposed to do some of the job with getting rid of heat; I guess they prefer it over using fans, since fans get noisy. Macs aren't made for games, so they toned down the clock speed of the card through drivers, as far as I understand. That makes sense, unless you want to, you know, use anything apart from OS X on it.

> **niffcreature said:**
> ...and what does the unintended pun snow leopard at full pelt mean?
oh the unanswerable questions
Full pelt = Full speed

---

