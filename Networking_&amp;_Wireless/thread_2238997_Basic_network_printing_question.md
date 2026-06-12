---
title: "Basic network printing question"
date: 2014-08-11
forum: Networking &amp; Wireless
---

### Post by artshark on 2014-08-11
I'm sure this has been asked; sorry if it's a repost. I have a network printer I cant seem to add. I can visit the printer's local page for status, etc. It has TCP/IP set up. WHich parameters work best for the printer wizard? I'm on 14.04.
Thanks
Art

---

### Post by tgalati4 on 2014-08-11
What is the make and model of the printer?

Open a browser:  [http://localhost:631](http://localhost:631)

Make sure your printer is awake.

Open the Administration tab in the CUPS browser and see if it shows up under "Discovered Printers".

Otherwise, try to add the printer with different addresses:

socket://192.168.1.125/9100
ipp://192.168.1.125/

Internet Printing Protocol (ipp)
AppSocket/HP JetDirect
Internet Printing Protocol (ipps)
Internet Printing Protocol (ipp14)
Internet Printing Protocol (http)
LPD/LPR Host or Printer
Internet Printing Protocol (https)
Windows Printer via SAMBA
Backend Error Handler 

The one you choose depends on your model of printer.

---

### Post by chili555 on 2014-08-11
> **artshark said:**
> I'm sure this has been asked; sorry if it's a repost. I have a network printer I cant seem to add. I can visit the printer's local page for status, etc. It has TCP/IP set up. WHich parameters work best for the printer wizard? I'm on 14.04.
Thanks
ArtIs this network printer attached to a computer (computer A) on the network and you wish all other computers (computers B, C and D) to also print on it; OR is the printer attached to your router? The answer will differ depending on which connection you are using.

---

### Post by artshark on 2014-08-11
I believe router. I'm at my office so it's a shared device. I can pull off any non-IP info from the config sheet printout that may help.

---

### Post by chili555 on 2014-08-11
> I believe router.Assuming it is the router, the printer should have an IP address listed in the administration pages of the router. It may help to ask the router to reserve that IP address in the DHCP pool so as to avoid collisions; assuming the router has reservation capability.

Then, use the IP address you found to set up the printer on all the computers in the network. In Ubuntu, and, I assume other Linux versions, you'd set up like the attached. In most cases, the protocol is ipp://. In a very few cases, including mine, it only works with ipp14://. Try this if ipp:// doesn't work.

The final part, lp1 in my case, came from the print servers documentation. Check yours. lpr works well in many cases.

Then proceed forward and select the printer manufacturer, model and default driver. Be certain that Policies > Shared is checked.

Reference: [https://aur.archlinux.org/packages/cups-ipp14/](https://aur.archlinux.org/packages/cups-ipp14/)> If you ever upgraded your cups from 1.4 to 1.5 and up, and noticed that you cannot print anymore with a message like "missing validate job", you should be a victim of this "regression". Of course, first of all check out if the vendor has released an update to the driver in order to make it work with newer cups. If it's not the case, than this package that includes the old backend is your only reasonable choice.In Ubuntu 14.04, the cups version is 1.7.xx.

---

