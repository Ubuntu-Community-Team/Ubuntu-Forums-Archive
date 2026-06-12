---
title: "Help with Acer Aspire One AOA150 wireless"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by Polydeuces on 2010-04-26
I can't seem to find an answer to this anywhere. I'm trying to decide what the deal is with my wireless internet (it drops all the time) I'm using an Acer Aspire One AOA150 with the AR5001 Atheros Wireless adapter. Knowing this might help a lot!

---

### Post by snowpine on 2010-04-26
32 bit is the default, but 64 bit is possible too.

You should choose the default 32 bit (i386) for your Acer.

edit: :)

---

### Post by bville09 on 2010-04-26
Is it wireless or mobile internet? I've always had problems with mobile internet dropping out, it's because of interference from cell phones and other mobile users, as well as street traffic and things like that.

The only way I could fix it was to ensure that it was always sending or receiving information. The easiest way to do this was to get a torrent, and limit it to 1.0kb/s upload and download.

As for a wireless network, that usually drops out because of bad reception between devices (like a brick wall between the laptop and the router, or something).

---

### Post by 3rdalbum on 2010-04-26
I think my Aspire One has the same wireless chipset. I've only ever used Ubuntu 10.04 on it, but I've never had any trouble; even downloaded multiple gigabytes of data from my network onto it.

Maybe try 10.04, and if you still have problems then the wireless card itself might be sus.

---

### Post by speedwell68 on 2010-04-26
> **Polydeuces said:**
> I can't seem to find an answer to this anywhere. I'm trying to decide what the deal is with my wireless internet (it drops all the time) I'm using an Acer Aspire One AOA150 with the AR5001 Atheros Wireless adapter. Knowing this might help a lot!

It sounds as if you are having the same problem I had with my A150.  The solution that I came up with was to use an alternative network manager, in this case I used WICD.  WICD is in the Ubuntu repositories.  You can install it by going into the Synaptic Package Manger and searching for WICD or more easily through the terminal by using this command...

```
sudo apt-get install wicd
```

During the installation process it will terminate and un-install the existing network-manager applet.  I have found it prudent to do a full restart before you start using WICD.

Hope that sorts it for you.

---

### Post by edubski on 2010-05-08
I also have an Acer Aspire One AOA150 and my wireless card stopped working with Network Manager.  I got anywhere between no wireless device detected to my wireless device being detected but no available wireless networks.  Well, enough rambling.  I un-installed and reinstalled Network Manager, rebooted the computer, grabbed a beer and was ready to spend countless hours looking at mindless stuff on the Internet. 

Oh yeah, I was running 9.10 and recently upgraded to 10.04 on April 29.  The wireless card malfunction didn't happen until 10.04.  

Just a note:  I like Ubuntu, but I shouldn't have to do the ol'  Windows software application fix...uninstall-reinstall-reboot and BING, IT WORKS!  :lolflag:

---

