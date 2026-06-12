---
title: "Printing from windows to linux box"
date: 2014-02-27
forum: Networking &amp; Wireless
---

### Post by Bicly on 2014-02-27
Hello, I have successfully installed a printer server on my linux box using CUPS. I can print from my Windows box fine. However when I get a new Windows box onto my network and add the linux box printer it cannot find a driver and I have to manually select the model of printer from a large generic list. Is there a way to bypass this? Maybe like a printer driver on the linux server to be pushed to the new Windows box when adding a printer?

Thank you

---

### Post by SeijiSensei on 2014-02-27
If you are using Samba to share the printer, read this: [https://wiki.samba.org/index.php/Samba_as_a_print_server#Associating_a_shared_printer_with_a_driver_and_preconfiguring](https://wiki.samba.org/index.php/Samba_as_a_print_server#Associating_a_shared_printer_with_a_driver_and_preconfiguring)

---

