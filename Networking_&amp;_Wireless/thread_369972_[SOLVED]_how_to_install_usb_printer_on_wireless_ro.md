---
title: "[SOLVED] how to install usb printer on wireless router (siemens gigaset sx541)?"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by doncristobal on 2007-02-25
hello everyone

do you know how i can print on my hp laserjet 1200 that's plugged in the usb port of my siemens gigaset sx541 wireless router? 

i have xubuntu edgy (parallel installation with windows xp). 

wireless and internet work perfectly on both linux and windows. 

i made the printer work on windows following the instruction here: [http://gigaset.siemens.com/shc/0,1935,hq_en_0_23014_rArNrNrNrN_prodId%3A80487,00.html](http://gigaset.siemens.com/shc/0,1935,hq_en_0_23014_rArNrNrNrN_prodId%3A80487,00.html) (sorry, i only find it german, see p. 121 of the full version).

but on linux, i simply don't have the slightest idea how to install the printer. 

thank you very much for helping!

---

### Post by doncristobal on 2007-02-25
additional info: the administration tool of the router does not give very much information about how to access the printer (see the attached image). it just says that the print server is switched on, that the ip address is 192.168.2.1 (that's the router's address), and that a usb printer is connected.

---

### Post by sdide on 2007-02-25
Hey,
my German is not great, but from what I can decipher it works just like a normal networkprinter (which in windows terminology is a "local printer on a tcp/ip port" - doh.)

So you just startup cups - you can use: 

$ gnome-cups-manager

->"New Printer" 
Choose network printer, JetDirect. type in the ip of the Siemens router and leave port at 9100

---

### Post by doncristobal on 2007-02-25
thanks for helping!

there was no gnome-cups-manager on my xubuntu, but i managed to install it, along with hplip and 10'000 tons of printer ppd files. 

however, it did not work as AppSocket/JetDirect with address socket://192.168.2.1:9100

i am trying now without ":9100" but it still does not work. 

what should i do? i am new to linux and feel slightly helpless :-(

poor don cristobal

---

### Post by doncristobal on 2007-02-26
i've tried it with a direct usb connection to my computer and a pxlmono ppd. this work perfectly. 
via the printserver it still does not work 
:-(
can anybody help? this would be very nice :-)

---

### Post by doncristobal on 2007-07-07
Still nobody has an idea?

i would be soooo happy if i did not need to carry my laptop to the printer's usb cable every time i need to print a file from my nice little linux. :confused:

Thank you for any kind of helpful hint!

---

### Post by Fitzcarraldo on 2007-07-08
*doncristobal*, have you tried configuring Ubuntu to print to a remote Unix printer (LPD)? I have a different manufacturer's wireless router and a different model of printer, but perhaps you could try the procedure that I used -- with IP address modified to suit your router -- and see if it works:

[http://ubuntuforums.org/showthread.php?t=363729](http://ubuntuforums.org/showthread.php?t=363729)

---

### Post by doncristobal on 2007-07-08
Thank you, Fitzcarraldo. 

Your hint finally guided me to the solution of this apparently extremely stupid problem. Installation was in fact much simpler than on window$ - if only siemens had given the tiny little bit of information that's needed for the lpd/lpr support on linux!

So, what i did:
(this applies to xubuntu 7.04 and probably to other xfce distributions, too) 
- I went to Applications, Settings, Printing
- I chose New Printer
- I gave my wirelessed printer a nice name
- under "Select Connection" / "Devices", i chose "LPD/LPR Host or Printer"
- I specified the hostname: "192.168.2.1"
- [COLOR="Red"]I specified the printername: "LPT1" [/COLOR](THIS was the crucial point! How could i have guessed that LPT1 had to be typed as a printername??? See also one of the attachments (win-instruction_de.png), maybe your router's windows-only instruction gives similar information)
- I chose my printer manufacturer (hp) and model (laserjet 1200)

... and there i was. As simple as that, no special software, no special knowledge, just the weird idea to type the "protocol" (for windows) as the "printername". 

In the end, the printer configuration told me the device URI was lpd://192.168.2.1/LPT1

I hope this helps other users too!

---

### Post by Alibabac on 2007-08-03
It doesn't work for me, altough I have Siemens Gigaset SE 555 with Canon i350 attached. It works fine in Windows, but I want to experience Kubuntu power. One thing;nmap reports that printing service on this router goes on port 515, not 9100. Where is the problem than? KJobviewer reports the page is gone, but the printer doesn't move.Should I specify : lpd://192.168.0.1:515/LPT1 , instead lpd://192.168.0.1/LPT1 ???
Or the driver makes the issue ? I've put BJ-20, because I couldn't find appropriate driver for i350.

---

### Post by wislon32 on 2007-08-12
Amazing but LPT1: works for the HP5940 as well.  The instructions given by Draytek didn't work, but this was spot on.  Thanks!

---

### Post by ymai on 2007-11-21
This thread helped me. Just for information with my hard and software:

Ubuntu 7.10
Draytek 2900G
Right click on my HP 1022 printer icon
Connection 
Network printer
Host: 192.168.1.1 // my router IP
Queue: p1

Feel lucky.

---

### Post by prasopsuk on 2007-12-03
> **doncristobal said:**
> Thank you, Fitzcarraldo. 

Your hint finally guided me to the solution of this apparently extremely stupid problem. Installation was in fact much simpler than on window$ - if only siemens had given the tiny little bit of information that's needed for the lpd/lpr support on linux!

So, what i did:
(this applies to xubuntu 7.04 and probably to other xfce distributions, too) 
- I went to Applications, Settings, Printing
- I chose New Printer
- I gave my wirelessed printer a nice name
- under "Select Connection" / "Devices", i chose "LPD/LPR Host or Printer"
- I specified the hostname: "192.168.2.1"
- [COLOR="Red"]I specified the printername: "LPT1" [/COLOR](THIS was the crucial point! How could i have guessed that LPT1 had to be typed as a printername??? See also one of the attachments (win-instruction_de.png), maybe your router's windows-only instruction gives similar information)
- I chose my printer manufacturer (hp) and model (laserjet 1200)

... and there i was. As simple as that, no special software, no special knowledge, just the weird idea to type the "protocol" (for windows) as the "printername". 

In the end, the printer configuration told me the device URI was lpd://192.168.2.1/LPT1

I hope this helps other users too!

--------------------------------------------------
Thank so much for you suggestion.
it a nice tips.
my report printer tcp port worked.

---

### Post by mottl_tirol on 2008-06-18
> **Alibabac said:**
> It doesn't work for me, altough I have Siemens Gigaset SE 555 with Canon i350 attached. It works fine in Windows, but I want to experience Kubuntu power. One thing;nmap reports that printing service on this router goes on port 515, not 9100. Where is the problem than? KJobviewer reports the page is gone, but the printer doesn't move.Should I specify : lpd://192.168.0.1:515/LPT1 , instead lpd://192.168.0.1/LPT1 ???
Or the driver makes the issue ? I've put BJ-20, because I couldn't find appropriate driver for i350.

hi,

you have to enter "lpd://YourIP/LPT1?reserve=rfc1179" and than you are able to use Gigaset SE 555 print server with ubuntu :)

---

