---
title: "Wireless disconnection problem"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by wishingstar on 2011-02-06
Dear ubuntuforums users,

I have been facing a very strange problem. I have a 3.5" Seagate external hard drive, and I have "Spin down hard drives" unchecked. But my seagate seems to have a built-in feature to spin down on its own. And EVERY TIME it does that, my wireless connection just dies and refuses to start again. I tried to used the command:

```
sudo ifconfig wlan0 up
```

but it didn't work, it gave me an error, and now the only way to get my connection back is to restart the whole system, which beats the purpose of using linux :(

I am using Ubuntu maverick with a realtek wireless card, in case that info is needed.

Any help is appreciated,
Wishing Star

---

### Post by fabricator4 on 2011-02-06
Do you have any problems if the Seagate drive is not plugged in?  I'm wondering if the drive is spiking the system when it powers down and this is taking out other peripherals such as the wireless card.

Chris

---

### Post by wishingstar on 2011-02-06
> **fabricator4 said:**
> Do you have any problems if the Seagate drive is not plugged in?  I'm wondering if the drive is spiking the system when it powers down and this is taking out other peripherals such as the wireless card.

Chris

Actually that's a possibility Chris, I don't have any problems when the Seagate drive is not connected. And sometimes my laptop gives off weird noises that come from the area of the USB ports where i usually connect it. Could those spikes, if indeed that was the reason for the behavior, have damaged my laptop in some way?

Note: I have a dual boot system, with Win7, and when the drive is connected through Win7, it does spin down, but immediately reconnects with no change in wireless behavior.

---

### Post by fabricator4 on 2011-02-06
The "spikes" won't be anything you can hear.  The noises you are hearing are puzzling however.  If it happens every time the drive spins down under Ubuntu but not windows, then it's something you need to find out about.

Do you always plug the drive into the same port?  It's a long shot but try plugging it into a different port.  I'm still thinking there's a hardware reason for the problem, but it should also occur under Windows.

Chris.

---

### Post by wishingstar on 2011-02-06
> **fabricator4 said:**
> The "spikes" won't be anything you can hear.  The noises you are hearing are puzzling however.  If it happens every time the drive spins down under Ubuntu but not windows, then it's something you need to find out about.

Do you always plug the drive into the same port?  It's a long shot but try plugging it into a different port.  I'm still thinking there's a hardware reason for the problem, but it should also occur under Windows.

Chris.

Thanks Chris for getting back to me so quickly.

Actually I use different ports depending on the way I have my desk set up at any given time, so i'm not always using the same port.
The problem doesn't occur under windows, as i said, the drive spins down and immediately spins back up, for ubuntu, it spins back up, but disconnects the wireless in the process and nautilus reopens a window with the drive.
It's a puzzling issue, i know, but if there is a way to restart the wireless card without having to restart the entire system I would be content for now.

---

### Post by fabricator4 on 2011-02-06
> **wishingstar said:**
> ...and nautilus reopens a window with the drive.
.

This indicates to me that the device is going into a complete powersaving mode and being unmounted under Ubunut.  When it spins back up it gets mounted again and that is why Nautilus opens up a new window.

Next question: Do you have an external power supply for the drive, or is it being powered off the USB port alone.  If so, do you have a single or a double USB plug on the drive?

Chris.

---

### Post by wishingstar on 2011-02-06
> **fabricator4 said:**
> This indicates to me that the device is going into a complete powersaving mode and being unmounted under Ubunut.  When it spins back up it gets mounted again and that is why Nautilus opens up a new window.

Next question: Do you have an external power supply for the drive, or is it being powered off the USB port alone.  If so, do you have a single or a double USB plug on the drive?

Chris.

The drive is 3.5", so it has its own power supply, and it has a single plug.

---

### Post by fabricator4 on 2011-02-06
OK, if the drive has it's own power that kind of eliminates a USB power supply problem.  Not completely, but certainly "kind of".

You say it spins down and immediately spins back up again?  Is this with no intervention on your part?  It's starting to sound like the drive is resetting, and it may be doing it both under Ubuntu and Windows.  I still have no idea why it's causing a wlan problem under Ubuntu though.

Check the drive to see if there's a jumper to disable any power saving modes.  If you've got another plug pack of a suitable type try using that on the drive - only do this if you are totally sure that the voltage, current requirements, and polarity of the plug pack are suitable.

I am starting to think there may be fault with the drive, if it keeps resetting periodically.  If it's got it's own power I wouldn't expect that to be normal behaviour. 

One thought on getting the wlan to work after it's been disabled is that you could try unloading and loading the driver module with modprobe and see if that kicks it into life.

Chris

---

### Post by wishingstar on 2011-02-06
> **fabricator4 said:**
> Is this with no intervention on your part? 

Yes, it does everything on its own.

> **fabricator4 said:**
> Check the drive to see if there's a jumper to disable any power saving modes.

There are no jumpers for the drive, it is in a locked case (i didn't connect it using my own case).

 > **fabricator4 said:**
> If you've got another plug pack of a  suitable type try using that on the drive - only do this if you are  totally sure that the voltage, current requirements, and polarity of the  plug pack are suitable.

I tried using a different cable, same behavior, However, I think the  8-port power pad (where you connect more than one plug to the same pad)  is old, i might try replacing that next.

> **fabricator4 said:**
> One thought on getting the wlan to work  after it's been disabled is that you could try unloading and loading the  driver module with modprobe and see if that kicks it into life.

How do i use modprobe? one thing i found while looking at askubuntu.com is to try and use wicd, do you recommend that?

---

### Post by fabricator4 on 2011-02-06
> **wishingstar said:**
> Yes, it does everything on its own.

So...  it appears to spontaneously do a reset on its own in both Windows and Ubuntu...  but the behaviour under Ubuntu causes other unexpected problems.

> There are no jumpers for the drive, it is in a locked case (i didn't connect it using my own case).


Yeah, I was grasping at straws there...

> 
I tried using a different cable, same behavior, However, I think the  8-port power pad (where you connect more than one plug to the same pad)  is old, i might try replacing that next.


You mean like a power board?  I wouldn't expect it to cause any problems unless the contacts inside were really dirty and manky.  I have seen corroded crimp connectors cause problems however.

I would definitely try a whole new plug pack.  There must be some reason the drive is resetting.  Or hang, you said cord?  Does the mains power plug straight into the drive case?  This would indicate that the case has it's own internal power supply.

> How do i use modprobe? one thing i found while looking at askubuntu.com is to try and use wicd, do you recommend that?

I've never used wicd, since I don't have a serious problem with network manager.  It's not broken so I never tried to fix it :-)

To use modprobe:

```

sudo modprobe -r drivername

```

to remove the driver from memory. to install it again, just

```

sudo modprobe drivername

```

will put it back.  If it's simply a software problem this may kick it off again.  If the device itself is locked up it probably won't work.

Chris

---

### Post by whatthefunk on 2011-02-06
Sounds like a Network Manager problem (again).

Might want to try Wcid.

---

### Post by wishingstar on 2011-02-06
Thank you Chris and whatthefunk, I tried suggestions, sadly to no avail :(

I carried out a testing session with the seagate external drive (mine  has music on it), so i listened for a while and then let the drive spin  down, and sure enough, it unmounted and started back up again, reopening  a nautilus window. I then tried to "safely remove drive" when it spun  down again, and the wireless disconnected within 2 seconds of unmounting  the drive. I had already installed wicd, but it couldn't find anything,  I also tried the modprobe commands, and it spat out a "FATAL wlan0 not  found" error!!

I have no idea what is happening with these hard drives (I only face  this with the 1TB and 2TB seagate ones, I have another 500GB Lacie drive  and I don't have that issue with it!)

Still, thanks guys for the help, and awaiting other suggestions...

---

