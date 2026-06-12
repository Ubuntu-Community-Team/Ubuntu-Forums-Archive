---
title: "Configuring  Hp C7200 Printer"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by bullet311 on 2010-02-16
I am looking for a way to hook this printer up wirelessly with this Ubuntu machine. The cd calls for Windows or Mac but I am sure there is a way to get this network hooked up so I don't have to transfer files to my other computer just to print. Anyone know any answers or where to start at least? I am new to ubuntu but not new to computers. 

Thanks

---

### Post by j.bell730 on 2010-02-16
You're probably going to need to use CUPS (short for _C_ommon _U_nix _P_rinting _S_ystem).

First, go to **System** > **Administration** > **Printing**.
A dialog should have popped up, from which you should click **New**.

That should give you an easy to use wizard, so you can easily set up your printer. You know your printer better than I do, so unfortunately, I cannot help you any further.

Hope that helps!

---

### Post by HappyFeet on 2010-02-16
Read [this]("http://www.linuxforums.org/forum/ubuntu-help/147861-install-hp-c7280-photosmart-wirelss-printer.html") thread. Aggy22 got it working.

---

### Post by bullet311 on 2010-02-16
Thanks both of you guys for the help. 

So using both posts I did indeed find the info and steps needed to load the correct drivers. 
Step 2: Get it connected. 

From what I have learned i am going to have to find the ip adress of my printer which I can then add in the printing manager (System-Admin-Printer) which should successfully connect my printer to this computer.

:My printer is connected to its own port in the modem so it would have its own ip adress right, or would it be the same as the computer itself. Regardless if nobody has an answer than Ill google it. :) 

Thanks

---

### Post by HappyFeet on 2010-02-17
> **bullet311 said:**
> 
:My printer is connected to its own port in the modem so it would have its own ip adress right

Yes, it will have its own IP address.

---

### Post by j.bell730 on 2010-02-17
Nowadays, printers will have their own built-in interface, from which you can print a report, directly from the printer. If you do this, the printed out page will probably have the IP address of the printer on it.

---

### Post by bullet311 on 2010-02-17
Thanks for all the help! 

I dug around in my printers interface and did finally find the Ip. I then went to the printer manager and added a new printer with the right addresses and printed a test page and wa-la! Test page is hanging on my wall! 

Thanks!

---

