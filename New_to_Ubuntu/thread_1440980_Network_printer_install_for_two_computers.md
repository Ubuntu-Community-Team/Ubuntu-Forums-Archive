---
title: "Network printer install for two computers?"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by som1special2 on 2010-03-28
I just bought a new AIO printer and need some direction on how to make it a network printer for Windows, (which my wife uses) and Linux Mint, (I use). I will have it connected to an ethernet cord attached to the router. The rest is foreign to me and I need help. Could someone point me in the right direction as far as step-by steps or good reading??? Thanks in advance!!!

---

### Post by viper250 on 2010-03-28
you need to install it in windows with the software that came with it.
you can also go to control panel, add printer, select it from the list if it is in the list
or click have disk if you have the installation disk.
it will then do a serch for attached printers and should detect it.
you should select network printer

in mint Im not sure but you can use the help command and type install printer and it should get you the info but the same with windows select network printer
but with linux do not use the disk that came with the printer as linux uses universal drivers

---

### Post by garvinrick4 on 2010-03-28
Set up Windows workgroup network if you want in Windows and Samba in Linux if mint has it.
Just normal printer set-up in windows computer. Share printer in Windows, add printer in Linux.
Share whatever you want if you want to share devices on both computers. Takes a user password in
Windows to set up workgroup in windows. As long as you have to sign on in Windows that is good enough. 
It is a workgroup printer basically. No matter if you have 2 or 10 computers in the workgroup in Windows
and linux.

---

### Post by pbpersson on 2010-03-28
It would help if we knew what printer this is.

You said the ethernet cable connects directly to the router but an AIO printer means it includes a scanner so I am confused already.

We need way more details on this to help you.

My printer is connected to my Vista machine and all Windows and Linux machines in my house use that one printer.

---

### Post by linux6994 on 2010-03-28
Mint menu > Control Center > Printing > Server > New > Network Printer > LDP/PR Host Printer> then add the IP Address

The networked printer will have a network address assigned to it once its plugged in to your router. This address can be set automatically via router or before hand on printer device itself, either way you need to know what it will be.

On both Linux and Windows you can can add the printer indicating it's IP address.

Good Luck

---

### Post by som1special2 on 2010-03-28
HP Officejet 6500, AIO is "all in one" with fax. The ethernet connect to the back of the printer.

---

### Post by sgosnell on 2010-03-28
You don't need to do anything except find the printer on both computers.  I have the same setup, an HP printer connected to my router, and at work we have a Brother connected to the router.  In Linux, just install a new printer, and the wizard should find it and install the drivers.  If it's an HP, install HPLIP and scanning will work.  If it's something else, you may have to manually install the scanner driver.  In Windows, it should be the same, but you will have to run the install CD/DVD to get scanning to work, and perhaps to get printing to work.  My HP has never worked as a scanner in XP, even after hours on the phone to tech support in India, and receiving and running multiple new CDs.  It works out of the box under Ubuntu.

---

### Post by lyall on 2010-03-28
plug in the network cable to you printer and turn it on.
then you need to do is get a print out of the printer network configure.
look the the ipaddress on the print out.
you will need it when it asks you for the ipaddress

for the Windows setup 
add new printer
on the window that asks the connect select local
then create a new local port
on the new local port enter the ipaddress
after your local port is set then install the driver for the new printer (from CD)

at this time I can not remember all the steps, but it should get you started.

good luck and have fun learning

---

