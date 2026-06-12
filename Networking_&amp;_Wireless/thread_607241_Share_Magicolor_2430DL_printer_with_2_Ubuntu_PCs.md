---
title: "Share Magicolor 2430DL printer with 2 Ubuntu PCs"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by peterthebike on 2007-11-08
My setup is [BT Voyager 210 router]("http://www.voyager.bt.com/wired_routers/voyager_210/product_info.htm") connected to [D-Link  DES-1005D switch]("http://www.dlink.co.uk/?go=gNTyP9CgrdFOIC4AStFCF834mptYKO9ZTdvhLPG3yV3oV458kP98f8p8M6tj5jkkBSrgzy9B/IsIAw==") with two PCs running Gutsy wired to it.

One PC (PC1) has a local Konica Minolta Magicolor 2430DL printer connected via USB which works OK. The second PC (PC2) does not see the printer even though PC1 has Share published printers connected to this system set, and PC2 has Show printers shared by other systems set.

Before purchasing a new PC1, I used PCLinuxOS on both PCs and was able to share the printer without any trouble. When I first purchased PC1 it was running Feisty and I could not share the printer. PC2 then had Feisty installed and that did not make any difference. Soon after purchasing PC1 Gutsy was released and both PCs have been upgraded, but I still cannot see the printer from PC2.

I have tried configuring the printer from PC2 by setting the connection URI based on [Network Printing with Ubuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#head-6a3af6eb770f1dbc388e0574599943e463608bed-2") as ipp://192.168.1.2/printers/mc2430DL but this has not worked. I used 192.168.0.2 because ifconfig gave  inet addr:192.168.1.2.

Any print sent from PC2 just sits in its print queue as processing.

Can anyone suggest how to resolve this please?

---

### Post by mpierce on 2007-11-08
I've found that setting up samba to share the printer seems to be the best ticket.

You can then add the printer using your web browser and the the smb protocol or kde/gnome's print manger

Hope this helps...

---

### Post by UrbanoFreitas on 2007-11-09
Hi.

I was just making a search, using [http://www.uboontu.com/](http://www.uboontu.com/), to see how I could share a HP 1510 printer, under my two machines running Gutsy, linked via wired connections, through a Thompson Speedtouch 580. And see your post.

So I went to the Ubuntu wiki see what kind of informations, were available, and by comparing the information that was available (only for Feisty) there and the dialog boxes that appear in Gutsy, I managed to get my printer shared.

So as result of my sucessfull experience, I decided to update the page, with a tutorial, of how to do it in Gutsy, based in previous explanations presented there.

So visit:
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#preview](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#preview)

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

Hope that work.
Urbano

P.S. - Note that the page could not be updated with the manual that I said, because We must wait for the original page creator give is approval;

---

### Post by peterthebike on 2007-11-09
Hi Urbano,

That is how I have tried to get the printer sharing to work, but on the Ubuntu Client Machine I do not see a network printer. That is why I am trying to use Samba which I have seen some other threads recommending it as a way to share a printer.

---

### Post by sipickles on 2007-11-09
We have a 2430DL printer at work, and its such a compliant network printer, windows, linux... macOS, it swallows all print requests with little config.

Why have you got your printer connected via USB? Its a network printer :)

Plug the Konica into your DLink switch via a network cable. Then use System>Printing to find the printers.

Thats about it.

PLUS, you don't need to have one puter on to print from the other, since the Printer has a Print Server built in.

Good luck!

---

### Post by peterthebike on 2007-11-10
> **sipickles said:**
> Why have you got your printer connected via USB? Its a network printer :)

Doh! :cry:

The best solutions are always the easiest! (just got to get another cable)

My excuse is when I first got the printer, I did not have a network so I had forgotten that it was a network printer. That almost sounds believable. :)

Thanks though, I think you may have stopped my wife wanting to divorce me!

---

### Post by sipickles on 2007-11-10
Wow I actually managed to help someone!

Made my day! :P

---

### Post by peterthebike on 2007-11-10
If you lived nearby I'd buy you a beer! =D>

---

