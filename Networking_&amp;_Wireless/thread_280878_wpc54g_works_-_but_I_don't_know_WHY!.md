---
title: "wpc54g works - but I don't know WHY!"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by phreakshew on 2006-10-20
Sooo, I finally got my Linksys WPC54G wireless card to work in my old HP Pavilion lappy - YAY!

BUT- I am still unsure of WHY it works! I had tried several different things earlier in the day, but here are the final steps that I took that seemed to do the trick:

Using Synaptic Pkg Mgr, I searched for "ndis" and installed "ndisgtk" and "ndiswrapper-utils". 

The drivers that came with the CD for the card did not work, (too old?) so I had to download the .zip file to my desktop and extract the files to a separate folder.

I then went to System / Administration / Windows Wireless Drivers / Install New Driver.  Since I could not install the drivers from the folder I had created,(?) I had to put the ones I wanted on a floppy and then install from there.  I copied both lsbcmnds.inf and lstinds.inf to the floppy and then I was able to install them both. I am unsure of why I had to put them on a removable media.

I then clicked on "Configure Network", and made sure my Default gateway device showed "wlanO".  Then I highlighted my Wireless connection, and clicked "Properties". I made sure that "Enable this connection" was checked, and clicking on the drop down arrow under Network Name (ESSID), I chose my belkin54g router. I left the Key as Hexedecimal, and the Configuration as DHCP.

I typed "sudo modprobe ndiswrapper" in a terminal, and tried Firefox.

It WORKS!!!

Interestingly though, when I type "sudo ndiswrapper -l" in a terminal, I get: Installed ndis drivers:
lsbcmnds        invalid driver!
lstinds invalid driver! 

What's more, going to System / Administration / Windows Wireless Drivers 
shows lsbcmnds and lstinds, but they both say "Hardware present: No."

Soooo, I am confused. (As per usual.) Why is my WIFI card working when my system says that the drivers are invalid and that my hardware is not present??? :-k 

These are the links I had followed:
[http://www.ubuntuforums.org/archive/index.php/t-99490.html](http://www.ubuntuforums.org/archive/index.php/t-99490.html)
[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)
[http://www.tuxmagazine.com/node/1000167](http://www.tuxmagazine.com/node/1000167)

thanx and good luck to all!

---

### Post by wieman01 on 2006-10-20
Do this, then post the output, and I'll let you know why it worked. Linux comes with a native driver for this model:
> iwlist scan

---

### Post by intangir1999 on 2006-10-20
phreak,

how did you enter your hex key, was it xxxx:xxxx: or xxxxxxxx, i don't think it's case sensitive but just curious.

---

### Post by intangir1999 on 2006-10-20
Nevermind, as per this thread:

[http://www.ubuntuforums.org/showthread.php?t=281001](http://www.ubuntuforums.org/showthread.php?t=281001)

---

### Post by pregoeater on 2006-10-20
what i dont understand is why my wireless card does not work for my laptop but it does for my desktop same card just one is pci and one is laptop card....



pre

---

### Post by intangir1999 on 2006-10-20
Try this thread, I'm gonna try using this solution when I get home but I think it has something to do with the way the manufacturer firmware was made for laptop cards. 

[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

Let me know if this works if you're attempting at the moment.

---

### Post by phreakshew on 2006-10-21
iwlist scan shows:

$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:30:BD:9A:39:96
                    ESSID:"belkin54g"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/100  Signal level=15/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:54 Mb/s

sit0      Interface doesn't support scanning.


what does this tell us, wieman?

---

### Post by wieman01 on 2006-10-21
Now I am confused... Thought perhaps the native Linux driver would still run somehow. But you have successfully installed "ndiswrapper", deployed the Windows driver, and still got these funny error messages. Ok, beats me.

---

### Post by intangir1999 on 2006-11-28
Phreakshew,

You need to enter it as so:

iwlist scan wlan0

that way you only get that device to scan and not all of them, it looks like it picked up an access point but the next step is to configure it to connect to it using iwconfig.  do a "man iwconfig" for more info on your terminal.

---

