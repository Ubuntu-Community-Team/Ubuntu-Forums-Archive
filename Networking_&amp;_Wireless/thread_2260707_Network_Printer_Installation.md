---
title: "Network Printer Installation"
date: 2015-01-14
forum: Networking &amp; Wireless
---

### Post by Senaka_Amarakoon on 2015-01-14
I have problems in installing neworked printers, all printers are installed in computers with windows xp or newer version, this is the only pc thats having ubuntu, i appricaite if some one could help me out please, please not that there are several brands of printers in the network

---

### Post by newbie-user on 2015-01-14
What printers do you have? Ubuntu will usually find all the network printers that are active on the network. It's just a matter of getting the right drivers.

---

### Post by Senaka_Amarakoon on 2015-01-19
One of the printer is canon lbp 6630, i downloaded the drivers from cannon as well still it didnt work

---

### Post by pdc on 2015-01-20
can we please clarify the model of your printer 

it is > [SIZE=5]LBP6630[/SIZE] ...........that is correct? If so, which country are you in please ...........to help us verify the drivers you have downloaded

.........could it be the LBP6300 instead?

---

### Post by SeijiSensei on 2015-01-20
Try this:

Point a browser on the Ubuntu box to the URL [http://localhost:631/](http://localhost:631/).  That will bring up the administration page for "CUPS," the printing system used by Ubuntu.  Choose "Administration" from the top menu, then press the "Find New Printers" button.  I have a Brother that's connected to my network, and it appears in the list using this method.

---

