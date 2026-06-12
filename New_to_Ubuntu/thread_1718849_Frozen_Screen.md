---
title: "Frozen Screen"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by Oz Mercy on 2011-03-31
I have a windows based 32 bit laptop running windows 7 - I decided to try Unbuntu to see what it was like so I downloaded an virtual machine (VM Ware) and placed Ubuntu in the virtual machine - I have down losded some programs and am playing with Ubuntu.
 
I have a screen freeze I cannot fix. I am in firefox on a web page that is no longer there the scren is frozen and I cannot get rid of the page, close firefox or get back to the Ubuntu desk top there is an unresponsive scriptwarning on the page that I presume will close firefox but the mouse will not click it - the cursor just disappears when you click - any suggestions?

---

### Post by Hedgehog1 on 2011-03-31
> **Oz Mercy said:**
> I have a windows based 32 bit laptop running windows 7 - I decided to try Unbuntu to see what it was like so I downloaded an virtual machine (VM Ware) and placed Ubuntu in the virtual machine - I have down losded some programs and am playing with Ubuntu.
 
I have a screen freeze I cannot fix. I am in firefox on a web page that is no longer there the scren is frozen and I cannot get rid of the page, close firefox or get back to the Ubuntu desk top there is an unresponsive scriptwarning on the page that I presume will close firefox but the mouse will not click it - the cursor just disappears when you click - any suggestions?

You need to install user additions in the Ubuntu Guest OS:

[IMG]http://img855.imageshack.us/img855/9451/vboxuseradd01.png[/IMG]

[IMG]http://img189.imageshack.us/img189/2020/vboxuseradd02.png[/IMG]

[IMG]http://img845.imageshack.us/img845/5472/vboxuseradd03.png[/IMG]

Click the 'autorun' prompt and let the virutal CD install the mouse and screen drivers.

When it's done, you can reboot the VM and you should be operational without 'freezing' and mouse pointers disappearing. :D


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-01
One more-

To force a safe shut down of **any** vbox guest os - choose ACPI shutdown:

[IMG]http://img190.imageshack.us/img190/7310/vboxuseradd04.png[/IMG]


***The Hedge***

:KS

---

### Post by Oz Mercy on 2011-04-01
Thanks for that but I cannot get the cursor to sit on any of the menu buttons I click and it disappears.

---

### Post by Oz Mercy on 2011-04-01
Just got it. I went into VM Ware preferences and told it to power off the VM when I exited - this rebooted everything and when I logged on - everything restarted and went back to the desk top. Thanks for taking the time to answer my question I really appreciate it.

---

### Post by Hedgehog1 on 2011-04-01
Happy to help!

If you have not already, be sure to install the guest additions.  it allows screen resizing and better mouse pointer behavior.

I find VBox to be a very valuable tool:

[IMG]http://img219.imageshack.us/img219/455/vbox01.png[/IMG]

It is like having a room full of computers...

***The Hedge***

:KS

---

