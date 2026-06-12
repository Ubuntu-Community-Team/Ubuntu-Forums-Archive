---
title: "Trying to access printer on a WinXP Network"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by longtom on 2009-02-06
Hi

after some heavy headscratching and with the invaluable help and advice from members of the board like Voland and especially hyper_ch, to name but a few, I got my mixed network going and I can see all WinXP machines, and the XP machines see my Ubuntu machine.  Thanks for that again!

Now...

One of these WinXP machines has a shared Canon Pixma 4500 connected to it. How can I convince my Ubuntu machine, firstly, recognise this printer, and than print to it.

I can see all shared folders on all XP machines, however, I can't see any shared printers.

regards

longtom

---

### Post by hyper_ch on 2009-02-06
check if it's supported: [http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)

---

### Post by longtom on 2009-02-06
Heureka....

the first time I got something going myself.  But for the record - that's what I did:

Went to:  
> System > Administration > Printing
> New
> "Windows Printer via Samba

On the right hand side under "SMB Printer" click "Browse"

Choose the machine and the connected and shared printer as you would in Windows 

> Forward

@ "Select printer from Datasource" choose your make

> Forward

Choose your model and the recommended driver

> Apply

DONE

rightclick on the printer and print a testpage

Be proud of yourself....until the next time.

longtom

---

