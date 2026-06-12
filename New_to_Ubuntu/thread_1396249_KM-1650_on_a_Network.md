---
title: "KM-1650 on a Network"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by doctorj on 2010-02-01
Hi,

I have just installed a Kyocera KM-1650 printer on my Kubuntu 9.10 machine. I now want to make the printer available to others on my network but cannot see how to do this. I downloaded the drivers direct from Kyocera and it seems that it does not use the CUPS system. Does anyone know what can I do?

---

### Post by djchandler on 2010-02-01
Have you shared the printer on the network using System>Administration>Printing by changing the properties on the KM-1650? What is your network protocol?

If you can't share the printer in the conventional way because you are not using an open source driver, you need to request support from Kyocera since they supplied the proprietary driver.

Just so others who may try to help know, this is not simply a printer, but is a multi-function device (scanner, fax, copier, printer). The question being asked could easily be beyond the scope of anyone's resources here unless they just happen to have the same device shared over a network using the same protocols and using the same drivers as the OP is. The chances of that being the case are not very good.

As this appears to be a postscript printer, it's possible that the printer function might be able to be shared using a generic PostScript driver and the correct PPD file if the OP can make it visible to others on the network.

I'm out.

---

### Post by doctorj on 2010-02-01
Thanks for the reply. I will follow up with Kyocera and see if they are any help. It seems to me that Kyocera and not really into Linux the same way that HP are and seems to me that they support printing only from one computer and now sharing a printer on the network.

If any other person has ideas, I welcome it.

---

### Post by doctorj on 2010-02-01
When you asked my Network Protocol? I don't understand. Unless you are talking about SAMBA? We are networking a Windows machine with a Kubuntu machine setting shared files through Nautilus.

---

### Post by djchandler on 2010-02-02
> **doctorj said:**
> When you asked my Network Protocol? I don't understand. Unless you are talking about SAMBA? We are networking a Windows machine with a Kubuntu machine setting shared files through Nautilus.

Yes, knowing that you are using Samba to connect to a Windows network helps.

If you share your printer in Samba, it should show up on the Windows screen when it open your Shares in Windows Explorer. If the Windows driver for the printer is installed, they should be able to print to it.

The easiest way to do this is install **system-config-samba** with Synaptic. Samba will show up in your System folder in the main menu. Run it. The printer should be shared by default. Add your folders to share and that should work. It automatically rewrites the smb.conf file as items are added or deleted. Be sure to change the preferences tab to reflect the appropriate workgroup name.

If the Windows box is running Vista or Windows 7, make sure the Windows box is set up to connect to an office or work network, not a home network. If you do the Home thing on the Windows box, it assumes it's talking to Vista or Windows 7.

To mount the Windows shares in Kubuntu, you may have to use **Connect to Server**. That's what I have to do when mounting shared folders on my wife's Windows 7 box.

---

