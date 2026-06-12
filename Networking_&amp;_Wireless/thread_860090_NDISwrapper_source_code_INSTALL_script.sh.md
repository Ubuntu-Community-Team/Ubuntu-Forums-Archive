---
title: "NDISwrapper_source_code_INSTALL_script.sh"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by jingo811 on 2008-07-15
|


[SIZE="4"][FONT="Impact"][CENTER]NDISwrapper_source_code_INSTALL_script.sh - [COLOR="Sienna"]Alpha 01.10[/COLOR] - [COLOR="Red"]Project TERMINATED[/COLOR][/CENTER][/FONT][/SIZE]

> 
[CENTER]*************************************
           Who is this for?
*************************************[/CENTER]

This bash script is for people owning Wireless devices without native Linux driver support.


If you don't trust automated scripts then you can achieve the same results by following my **Ndiswrapper_Quicksheet.txt** but then you have to fill in the blanks by yourself.
When I say Chapters then I refer to my [tutorial]("http://virtualseafarer.com/witch/ndiswrapper/index.html")

> [CENTER]**Room for Improvements**[/CENTER]

I would like to improve this script since I have only tested it on an USB NIC.  So I don't know how it behaves with built-in NICs and supported native Linux drivers.  Also I haven't been able to test it on all the Ubuntu distros.
If you discover something bad then tell me here so I can fix it, tnx!!

> [CENTER]**Unexpected side effects**[/CENTER]

Either my script causes Ubuntu to shutdown improperly or the NDISwrapper module is causing shutdown problems.
The problem is that Ubuntu freezes when it says "Will shut down now" when you've used Wireless for a couple of hours.

I haven't observed any data loss at this time usually a Ctrl+Alt+Del and then powering off the PC during the GRUB menu stage helps.
But you could try to unload the NDISwrapper module every time before shutdown that might also be of help.
```
$ sudo modprobe -r ndiswrapper
```


[RIGHT]**This script was tested on:**

Debian Etch 4.01
Ubuntu Feisty 7.04[/RIGHT]

---

### Post by jingo811 on 2008-07-15
You only need to place the 2 components ([COLOR="Sienna"]ndiswrapper-Some.Version.tar.gz[/COLOR] and [COLOR="Sienna"]wireless Windows XP folder[/COLOR]) into the [COLOR="Red"][SIZE="4"]Tourist[/SIZE][/COLOR] folder and then execute the script from terminal.  The below is just an example of what the WINXP wireless folder might contain.  These 2 particular files are the most important:
[LIST]
[*][COLOR="Purple"]Some_Driver.inf[/COLOR]
[*][COLOR="Purple"]Some_Driver.sys[/COLOR]
[/LIST]

[IMG]http://i33.tinypic.com/ap8pk7.png[/IMG]

---

### Post by jingo811 on 2009-10-29
[CENTER][FONT="Arial Black"][SIZE="5"][COLOR="Red"]Project permanently TERMINATED[/COLOR][/SIZE][/FONT][/CENTER]



For my eyes only if I still remember what I did with it a few years ago. :)
Study it if you want to waste your time but it's pretty much useless today.

---

