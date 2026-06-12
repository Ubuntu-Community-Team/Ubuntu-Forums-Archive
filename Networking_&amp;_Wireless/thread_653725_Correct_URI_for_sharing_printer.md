---
title: "Correct URI for sharing printer"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by Ebuntor on 2007-12-30
Hi,

I'm trying to share a printer between several Ubuntu computers on a LAN, all of them running Gutsy.
I understand that the correct URI to connect to a printer is: ```
ipp://<computer's IP>/printers/<name printer>
```With my previous printer the URI was (on the computer that was directly connected): ```
usb://Canon/iP4000
``` so to connect I entered: ```
ipp://<ip address>/printers/iP4000
```That did work.

With my new printer, a HP Deskjet D4100, the URI on the computer that is directly connected is: ```
hp:/usb/Deskjet_4100_series?serial=TH6G842GH04D6
```I tried: ```
ipp://<ip address>/printers/Deskjet_D4100_series
```but that didn't work. I tried it with the whole serial code and without but still nothing. The URI compared to my old printer is a bit different of course. My old Canon was usb:// with my new HP it's hp:/usb/  so that's quite a difference. Is there some special way to connect HP printers? 

What am I doing wrong?

Thanks in advance

EDIT: I just installed gnome_cups_manager, when I go to the printer's properties the status is: "Ready: Unable to get printer status (Forbidden)!" Maybe this is the problem, or part of it.

---

### Post by Ebuntor on 2007-12-30
*bump*

---

### Post by ModelM on 2007-12-30
If CUPS is set up & running properly on whichever machine is the print server, the other networked computers should "see" the broadcast printer availability. You shouldn't need to tell the other computers where the printer is, you should be able to simply select it in the CUPS control.

You probably know this but the CUPS control is accessed by pointing your web browser to:

127.0.0.1:631

You might check the CUPS control on the server & make sure it is set to broadcast the printer availability.

---

### Post by Ebuntor on 2007-12-31
> **ModelM said:**
> If CUPS is set up & running properly on whichever machine is the print server, the other networked computers should "see" the broadcast printer availability. You shouldn't need to tell the other computers where the printer is, you should be able to simply select it in the CUPS control.

You probably know this but the CUPS control is accessed by pointing your web browser to:

127.0.0.1:631

You might check the CUPS control on the server & make sure it is set to broadcast the printer availability.

Thank you, I completely forgot about being able to access CUPS directly via a browser. For some unexplainable reason it worked after I printer a test page in CUPS control and after that it worked in the GUI's too.

```
 ipp://<ip address>/printers/Deskjet_D4100_series
```
Was correct after all. 


I don't know why but none of my printers show up  on the network even if I publish them. Whatever the problem was it 's all working now. 

Thanks for the tip. 

Happy 2008 :)

---

