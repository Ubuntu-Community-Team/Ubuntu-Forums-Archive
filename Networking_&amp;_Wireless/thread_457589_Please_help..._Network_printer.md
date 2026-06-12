---
title: "Please help... Network printer"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by linnerd40 on 2007-05-28
Hello.
Please help me. I have searched long and hard... and I have nowhere found a friendly guide on how to access a printer connected to a Windows computer in my house. I have set the printer to be shareable under windows, and have used the network setup tool in Windows to setup a network to share files and such. I just need **step by step** instructions on how to access the printer... I have not found a good guide ANYWHERE, or at least none that make sense. I am not a complete linux n00b so you can go a bit advanced... but I find it sad that I wasn't able to find anywhere online how to set up printer sharing. Nothing worked... 
If you can, just assume that I have not done anything, and that I am starting from scratch. I know it is a lot to ask for, but can someone just please take me through what I need to do on the windows pc and on my Ubuntu system. The printer is a samsung ml 2010.
Please help. Thanks.

---

### Post by turinglabs on 2007-05-28
If the printer is already shared from the windows side it should be easy - try System->Administration->Printing, when the dialog pops up, double-click on 'New Printer'. Select 'Network Printer' and 'Windows Printer (SMB)' from the dropdown. Fill in the host, windows printer name, username and password. That should get you started.

---

### Post by linnerd40 on 2007-05-29
Thank you.
I think this will work, however, where do I get the host name and such? And where would I have set the password? Sorry if this is a dumb question...

Thanks!

---

### Post by linnerd40 on 2007-05-29
I think progress has been made!
Under "Network Places" I can see the other computer on my network. However, when I click on the icon to access it... it takes forever and then tells me that the content of the folder could not be displayed. 
Also, when I go to add a printer, it sees MSHOME (the workgroup or something I created from Windows), and for the host I chose the computers name that is connected to the printer. I click through the stuff, but then when it is done... there is no new printer.

Thanks for any help you can give me!

---

### Post by turinglabs on 2007-05-29
Yes, the hostname would be the IP address or hostname of the windows box, the windows printer name would be the netbios name of the printer, according to windows, and the username and password would be any windows user that had permission to access the shared printer.

I'm afraid I can't help much with the windows end, sorry.

Perhaps a better alternative (if your printer supports it) is to use jet-direct, on port 9100 tcp. This is typically on HP printers, but it's implemented on other brands, as well, if they are network-enabled printers (i.e., with a network jack). You could also connect the printer to your Ubuntu box and share it out to the windows box using Samba.

---

### Post by jdmrsx05 on 2007-05-30
I'm having a similar problem.  However, the username/password I use get blanked out when I go to check the printer properties.  Any idea?

---

