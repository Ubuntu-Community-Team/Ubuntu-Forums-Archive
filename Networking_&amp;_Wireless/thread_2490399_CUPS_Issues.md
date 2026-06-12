---
title: "CUPS Issues"
date: 2023-09-02
forum: Networking &amp; Wireless
---

### Post by sabale on 2023-09-02
Hello, 

I have been trying to instal a Canon MG6120 printer in my computer and I am not able to do it. Currently, I have Ubuntu 22.04.03 LTS jammy.

If I try to add my printer from configuration / printers, I get "the printing system service seems to be unavailable". 

Then, If i try to to start cups with the command (sudo systemctl start cups) I get this "Job for cups.service failed because the service did not take the steps required by its unit configuration. See "systemctl status cups.service" and "journalctl -xeu cups.service" for details".

Finally, I tried to go through [http://localhost:631/](http://localhost:631/) but it impossible to do so. I got this "ERR_CONNECTION_REFUSED"

What should I do in order to install my printer?  Is it possible to restart CUPS configuraton? 

Thanks so much. 





[COLOR=#202124][FONT=arial]the printing system service seems to be unavailable.[/FONT][/COLOR]

---

### Post by sabale on 2023-09-03
[COLOR=#000000]Hello,[/COLOR]

[COLOR=#000000]I managed to go trough [/COLOR][http://localhost:631/](http://localhost:631/)[COLOR=#000000] and see the printrer installed. Unfortunatelly I still have the same problem. I am not able to print becouse it is look like the printer is disable. At the [/COLOR][http://localhost:631/](http://localhost:631/)[COLOR=#000000] webpage I can see:[/COLOR]


[COLOR=#000000][TABLE="class: cms_table_list, width: 1414"]
[TR]
[TD][MG6100]("http://localhost:631/printers/MG6100")[/TD]
[TD]Canon MG6100 series[/TD]
[TD][/TD]
[TD]DYMO Label Printer[/TD]
[TD]Idle - "Rejecting Jobs"[/TD]
[/TR]
[/TABLE]
[/COLOR]

[COLOR=#000000]Any ideas?[/COLOR]

[COLOR=#000000]Thanks so much.[/COLOR]

---

### Post by sabale on 2023-09-03
[COLOR=#000000]Any ideas? 

Thanks[/COLOR]

---

### Post by coffeecat on 2023-09-03
Duplicate of [https://ubuntuforums.org/showthread.php?t=2490408](https://ubuntuforums.org/showthread.php?t=2490408) . Thread Closed.

Please do not post duplicates in different parts of the forum. Thanks. This dilutes community effort and causes confusion.

---

