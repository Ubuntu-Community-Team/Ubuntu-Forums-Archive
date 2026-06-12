---
title: "Newbie - Keyboard Driver error in Narky"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by rich_hemmings on 2011-09-01
Hi All,

Total newbie here!
My goal: lightweight OS with Win7 dual boot, both set up as media centres - Win7 has Media Centre, and I'm currently installing XBMC under Natty. 
Current stumble... my keyboard (RF, touchpad integrated)
see here: 
[http://www.ebuyer.com/135103-nexos-2-4ghz-wireless-multimedia-entertainment-keyboard-with-touchpad-usb-kb-1000](http://www.ebuyer.com/135103-nexos-2-4ghz-wireless-multimedia-entertainment-keyboard-with-touchpad-usb-kb-1000)

Doesn't seem 100% at boot. The touchpad wont work until I unplug, and re-plug the RF receiver. 
Any clues? 

Really want to make a go of Ubuntu, but this sort of bug is damn frustrating!

Thanks in advance.


<ramble>
FYI: I'm running ubuntu 11.04 x86-32 as a Windows 7(x86-64) install on advice of a more 'linux-savvy' friend. Are there any limitations to this? 
I'm not a total I.T n00b, and am OK with partitioning etc and installing OS's, set up my WNDA1300v2 yest with some community support :) 
Currently have a 60Gb partition for Win7, and Ubuntu (20Gb allocated to each, with 20Gb spare), and will use the rest of the 1Tb drive split for Apps, Media, Docs etc. In time with a baby NAS, or extUSB 
</ramble>

---

### Post by cariboo on 2011-09-01
I have a pure Linux media center pc running XBMC on top of Natty. I use a [Logitech EX110]("http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=1543169&CatId=1482"), with zero problems.

The XBMC interface is very mouse friendly, so basically any wireless mouse should work, there really isn't a need for a keyboard. I only use the system for watching ripped dvds, recorded tv shows, watching podcasts and listening to music. All administration is done remotely using ssh.

I have a server with all my media in my garage, it's to noisy to be in the house, right now all the drives are mounted using [NFS]("http://en.wikipedia.org/wiki/Network_File_System_(protocol)"), but I'm playing with a [dlna]("http://en.wikipedia.org/wiki/Digital_Living_Network_Alliance") server

---

### Post by rich_hemmings on 2011-09-02
Cheers for the reply cariboo907, I painstakingly did all updates over night and all drivers seem good now! 
XBMC went in fine :) got home and was installed (just laggy due to no nvidia driver) - how gorgeous is the UI! :) 
Installed nvidia (sort of) via cli, then enabled in 'Additional Drivers'

Thanks for the suggestion, is the sort of thing I'll be working towards :)

---

### Post by rich_hemmings on 2011-09-05
Hey guys and girls,

Since my last post, I've noticed that perhaps the problems wasn't resolved!
The last 5 boots, the keyboard hasn't been working properly, which is REALLY weird as unplugging and re-plugging the RF adapter does the trick.
Is there any way of grabbing the config files/drivers that loads when I do this and installing them as default or something?

Also, being a total n00b to Linux, what's the best way to look at device config/management... converting from Win7, so a tool like 'Device Manager' would be awesome :) 

Thanks 

Rich

---

### Post by rich_hemmings on 2011-09-12
Solved - Looks like this was just a dodgy driver.
Re-Install of Linux on its own partition and having no problems.

Marking topic as SOLVED.

Thanks to those who contributed.

---

