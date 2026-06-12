---
title: "macbook to desktop??"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by FetalShinobi on 2009-06-01
im running ubuntu 8.04 on both a macbook (2,1) and a desktop (which is quite crappy) im neither new nor experienced but i was wondering. since the screen on my macbook is 75% damaged (thanks to my 2 yr old) is there a way i can transfer files to my desktop using a ehternet cable? usb cable? any help will be greatly appreciated.

---

### Post by aeiah on 2009-06-01
are both machines on the same network? (ie, do you connect both to a router in your house to access the internet for example?) if so you can look into either remote desktop or ssh & scp.

---

### Post by FetalShinobi on 2009-06-01
at the moment in time my net is down. my neighbor kindly lets me use his wifi network for 10$ amonth. i have a wifi card on the desktop and a builtin wifi on the macbook. i was thinking more along the lines of a direct offline transfer. straight from a ethernet or usb if possible.

---

### Post by DGortze380 on 2009-06-01
> **FetalShinobi said:**
> at the moment in time my net is down. my neighbor kindly lets me use his wifi network for 10$ amonth. i have a wifi card on the desktop and a builtin wifi on the macbook. i was thinking more along the lines of a direct offline transfer. straight from a ethernet or usb if possible.

Yes, you can.

You MacBook should have an auto-sensing NIC which will allow you to use a regular straight through CAT V network cable to connect the two machines.

You'll need to all Remote Access (SSH) or Remote Desktop on the MacBook to connect back and move files though. You need to do this on the MacBook from Preferences -> Sharing before you can connect over the network cable. You'll also need to manually assign IP Addresses to both machines (as neither will hand out DHCP in the configuration you're talking about).

---

### Post by FetalShinobi on 2009-06-02
thanks. can u be a little bit more detailed on how to go about it cause i went to the remote access (applications, internet, remote desktop viewer) and although it shows me the laptop and i have sharing enabled it wont connect.

---

### Post by DGortze380 on 2009-06-03
> **FetalShinobi said:**
> thanks. can u be a little bit more detailed on how to go about it cause i went to the remote access (applications, internet, remote desktop viewer) and although it shows me the laptop and i have sharing enabled it wont connect.

On my MacBook with Tiger (10.4), this is how I'd do it.

Open Preferences -> Sharing
Select Windows File Sharing
Click the Accounts Button and Select an Account to Allow Sharing for.
Plug an Ethernet Cable into the MacBook and Your Windows Machine
You Should be able to see your MacBook in your Network Neighborhood
Double Click and Connect with you User Name and Password for the Account you chose.

If that doesn't work, post back and I'll go through setting up all the networking information (Static IPs, etc.).

---

### Post by LewRockwell on 2009-06-03
an alternate method would be to purchase something like this:
([http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062))
([http://www.coolmaxusa.com/productDetails.asp?item=CD-350-COMBO&details=overview&subcategory=converter&category=converter](http://www.coolmaxusa.com/productDetails.asp?item=CD-350-COMBO&details=overview&subcategory=converter&category=converter))

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

of course, that option would work best if you were done using the laptop

you could always connect an external monitor to continue to use the laptop

---

### Post by FetalShinobi on 2009-06-03
i cant get to the screens cause the macbook screen is 75% broken. im running ubuntu on both computers (windows is gettin too annoying for me) and i have used the remote desktop and the laptop is found but it wont connect. i thought i had it down packed but it still wont work.

---

### Post by FetalShinobi on 2009-07-13
ok so i finaly got the remote access to work but i cant transfer files....anyone know why? :-D

---

