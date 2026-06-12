---
title: "ndiswrapper and DWL-G132"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by mevets on 2007-05-18
i just installed my win drivers using ndiswrapper and it doesnt seem to work. I followed this example:
[http://www.linuxquestions.org/questions/showthread.php?t=540809](http://www.linuxquestions.org/questions/showthread.php?t=540809)

When i run ndiswrapper -l i get:
```

athfmwdl  driver present
neta5agu driver present

```
I read another example when it explain that it should also say hardware present.

dmesg:
```

[4295079.259000] usb 4-1: USB disconnect, address 2
[4295086.965000] usb 4-1: new high speed USB device using ehci_hcd and address 5

```
Is there anything more I should be doing?

---

### Post by mevets on 2007-05-19
no ideas anyone?

---

### Post by sunexplodes on 2007-08-09
this is an old thread, but maybe this will still help: 

uninstall both of the drivers you have there, then delete the /etc/modprobe.d/ndiswrapper directory. 

download the most recent driver for the device from the dlink website.

use ONLY the NetA5AGU driver, not the other. Install as normal:

cd /wherever/neta5agu/is
sudo ndiswrapper -i NetA5AGU.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper


You'll have to unplug the device when you reboot, and then plug it back in when you reach the GDM logon screen.

---

### Post by igor54 on 2007-08-09
I've been trying this for a while.
All goes well until I get to the modprobe part - then the laptop freezes, and I have to do a hard shutdown.
I tried again today, and now it freezes the moment I insert the adaptor (didn't used to do that!).
I'll keep going with it (simply because it's become a combat-thing between us, now :mad:

There are a few places on the web that mention it, but one to steer clear of is the ndiswrapper forum. The moderator (or one of them, at least) considers Ubuntu users to be dumbasses who can't read. The fact that he gets so many having problems with his app should be a trigger to say "Hmm, wonder if there's something happening here?"

If I figure it out, I'll let you know. Could be a while, though - it's been a few years since I used Linux, so I'm having to refresh the old brain cells a fair bit :)

Regards
Igor

---

### Post by sunexplodes on 2007-08-09
might be worth trying

modprobe -r ndiswrapper

---

### Post by igor54 on 2007-08-09
Looked promising - - but!!!
After doing the above, I ran ndiswrapper -l and got nothing.
Plugged in the beastie - no problem (fingers crossed at this point)
Ran the install, and got some stuff I'd never seen before - 
Quote:
forcing parameter MapRegisters from 256 to 64
End quote: (This was repeated 8 times)
Did the "-m" thing, & got ;
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
Still with fingers crossed, ran 'sudo modprobe ndiswrapper' - system lockup again!!!

GRRRR!!!
About 10 years ago, I got a sound card working under FreeBSD (Ver 3.2 from memory), so this ain't gonna beat me! Besides, there's a weekend coming up, so enough beer, anything can happen!

Thx for your help so far, sunexplodes - it's got me further than anything else I've found :)

---

### Post by sunexplodes on 2007-08-09
Man, you're SO close!

The forcing MapRegisters thing is a really good sign, and as soon as you do the modprobe command, the lights on the device should come on. 

Now, I have had the little ******* cause lockups for me in the past, so try this: 

Unplug the device, reboot. Don't plug it in until you've already entered the modprobe command. See if that does you any good.

---

### Post by igor54 on 2007-08-09
Ran modprobe without the device - no worries, took ..like ..2 seconds to return to prompt.
Plugged device in - lockup!
Link light came on - then it locked. Seemed like there was ---maybe a second or so -- the light flickered before it locked.

---

### Post by igor54 on 2007-08-09
If we keep this up, and actually solve this issue - we will be the Gooorooos of DLink!!!
#
#
#
Sorry, just the irony of the whole thing getting to me! ](*,)

Thanx
Igor

---

### Post by sunexplodes on 2007-08-09
HRmmmmmm

I'm running low on ideas at this stage. Try this:  

Delete the /etc/modprobe.d/ndiswrapper file.  reboot the computer. After you reach the GDM login, plug the device in. after that, re-enter the ndiswrapper -m and modprobe -r ndiswrapper lines, and see if that makes a difference.

---

### Post by vojkan on 2007-09-18
> **sunexplodes said:**
> this is an old thread, but maybe this will still help: 

uninstall both of the drivers you have there, then delete the /etc/modprobe.d/ndiswrapper directory. 

download the most recent driver for the device from the dlink website.

use ONLY the NetA5AGU driver, not the other. Install as normal:

cd /wherever/neta5agu/is
sudo ndiswrapper -i NetA5AGU.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper


You'll have to unplug the device when you reboot, and then plug it back in when you reach the GDM logon screen.

Thank you so much for this!!! After 2 days of trying I was almost ready to give up.

---

### Post by DraK on 2007-10-09
Hi,

I downloaded latest driver from dlinks website but it only has one .inf file and its not the NET5 one, its the ATh***.inf file.

Can some give me a link to a zip with working drivers?

Thanks

---

### Post by Xyphius on 2008-04-30
not to start up an old thread...
but I seem to be having issues with my ndiswrapper...

I've recently installed Kubuntu 8.04 on my desktop computer.
However all I have available to connect to the internet is my D-link WUA-2340 USB ethernet adapter. 
After installing ndiswrapper (using a laptop with internet and a usb device to transfer packages from the ubuntu packages site)
I installed the device as per the instructions on the previous page...
and yet I still don't have any lights on my adapter.

---

