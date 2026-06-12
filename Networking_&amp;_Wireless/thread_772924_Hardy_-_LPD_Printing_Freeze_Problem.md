---
title: "Hardy - LPD Printing Freeze Problem"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by stansford on 2008-04-28
Hi,
I've just done a clean Hardy install and setup a printer to print via LPD to my 3com networked print server off which hangs my Epson R200 inkjet printer.

Under Gutsy this worked fine (and still does - I tried it with another pc) but under Hardy, after I have setup the ip address of 192.168.1.25 and a queue entry of "L1", selected the Epson R200 drivers  and clicked the "print test page", the instructions go to the printer, but the printer stops about 1/3 of the way through printing out the test page.

It's the same if I try and print from another source eg a web page, it just hangs.

The printer works fine from Gutsy and prints out the test page fully and any other page you care to try, but from Hardy, it just freezes.

My wife continues to print fine from her windows laptop, so I'm stuck...is it the driver used by Hardy which is: CUPS+Gutenprint v5.0.2 Simplified....or is there another reason for this

Can anyone help?

many thanks

---

### Post by nikogawa on 2008-05-01
I have exactly the same problem with a HP Deskjet 895cxi connected through usb with the driver "HP DeskJet 895C Foomatic/cdj880" on a clean Hardy install.

No matter what i print, the printer stops after about 1/3 of the page. However the test page is printed entirely.

---

### Post by stansford on 2008-05-02
> **nikogawa said:**
> I have exactly the same problem with a HP Deskjet 895cxi connected through usb with the driver "HP DeskJet 895C Foomatic/cdj880" on a clean Hardy install.

No matter what i print, the printer stops after about 1/3 of the page. However the test page is printed entirely.

Can I just clarify: is your printer attached to a print server or directly to your PC...and are you printing via LPD or just a normal printer driver?

I suspect it is the printer driver that's to blame, but I am surprised that there aren't more people suffering the same thing.
Any thoughts on how to get round it?

---

### Post by nikogawa on 2008-05-02
I forgot to mention. My printer is connected directly to my pc. But is doesn't matter which driver i use. When I use hpijs or cdj890, the problem persists.

---

### Post by martynf on 2008-06-01
I don't know if you've sorted this out yet but I have experienced the same problem:

Wired network of various Windows machines + one running Ubuntu 8.04.
Networked Edimax PS-1206U print server connected via USB to Epson Stylus Photo 750.
Windows machines print fine and Ubuntu 8.04 machine prints a portion of page then stops and goes no further.

The work around / solution described in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213081/comments/17](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213081/comments/17) fixes the problem with my Ubuntu 8.04 machine.

That is adding 
# Get printing over lan
net.ipv4.tcp_frto = 0
to the sysctl.conf file.

Also, see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213081](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213081) for full desciption.

Just thought I'd mention it in case this is of any use.

---

### Post by stansford on 2008-06-02
> **martynf said:**
> I don't know if you've sorted this out yet but I have experienced the same problem:

Wired network of various Windows machines + one running Ubuntu 8.04.
Networked Edimax PS-1206U print server connected via USB to Epson Stylus Photo 750.
Windows machines print fine and Ubuntu 8.04 machine prints a portion of page then stops and goes no further.

The work around / solution described in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213081/comments/17](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213081/comments/17) fixes the problem with my Ubuntu 8.04 machine.

That is adding 
# Get printing over lan
net.ipv4.tcp_frto = 0
to the sysctl.conf file.

Also, see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213081](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213081) for full desciption.

Just thought I'd mention it in case this is of any use.


martin - most kind to post this. I hadn't fixed the problem and so I will implement. thanks a lot!

---

### Post by stansford on 2008-06-18
> **martynf said:**
> I don't know if you've sorted this out yet but I have experienced the same problem:

Wired network of various Windows machines + one running Ubuntu 8.04.
Networked Edimax PS-1206U print server connected via USB to Epson Stylus Photo 750.
Windows machines print fine and Ubuntu 8.04 machine prints a portion of page then stops and goes no further.

The work around / solution described in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213081/comments/17](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213081/comments/17) fixes the problem with my Ubuntu 8.04 machine.

That is adding 
# Get printing over lan
net.ipv4.tcp_frto = 0
to the sysctl.conf file.

Also, see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213081](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213081) for full desciption.

Just thought I'd mention it in case this is of any use.


Martyn - looks like that solved it. I can now print and it has been working for a couple of weeks. Many thanks

---

### Post by tondunn on 2008-07-03
I had a similar problem since upgrading to Hardy.  My HP Laserjet 2300 connected via an HP Jetdirect card, would seem to timeout and I had to restart the printer each time I wanted to print.  The advice in the previous post fixed my problem.  It has taken me a few weeks to find a solution in the forums and I'm grateful that it is finally resolved.

---

