---
title: "Help: linksys wpc54gx ver.2"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by tkon1567 on 2007-10-10
I've just installed dapper drake 6.06.1 and I'm having trouble setting up my wireless card?  I'm a greenhorn--- so any replies would be great!!!!!

---

### Post by kevdog on 2007-10-10
Open up a command terminal and type

lspci -nn
lshw -C network

Post the output here.

---

### Post by tkon1567 on 2007-10-10
I no longer have the orginal driver and I have been searching for the right installation download..... but, I can't seem to find it.

---

### Post by kevdog on 2007-10-10
Go to the linksys website, and download the windows xp drivers for your product.  Once you done that tell me what you got!

Any reason for installing Dapper??  Its fairly old.

---

### Post by tkon1567 on 2007-10-10
I'm using a separate computer that has connection, how would I go about getting the driver loaded use an ethernet cable?
I installed dapper because I have an older machine, is there any major differences?  Could I upgrade easily?

---

### Post by kevdog on 2007-10-10
Thats the problem --- upgrades in the future will be limited.  Yes there will be an upgrade from Dapper LTS to the next LTS, but I dont know when that will be (meaning I dont know when the next LTS will be released).  You cant however upgrade from Dapper to Feisty, or from Dapper to Gutsy.

Just download the driver, burn it onto a cd or put it on a usb stick, and then bring it over to the ubuntu computer.  If its an .exe file, first extract the winxp drivers first, before bringing it over to XP, since all we want are the .sys and .inf files.

What is your chipset of the device???
Type lspci -nn at the command line, and look for your networking device.  Its going to say broadcom, atheros, realtek, rtxxxx, or something like that.  Most likely broadcom.

---

### Post by tkon1567 on 2007-10-10
I put that command in the terminal and all that came up was, about ten lines of numbers no chipsets?

I am having trouble burning the driver to  a disk......

---

### Post by kevdog on 2007-10-10
I cant help you with some of your problems such as CD burning.  

lspci -nn | grep Network

What comes up??

---

### Post by tkon1567 on 2007-10-10
i took out all the files except for the sys. and inf. and burnt them to a cd ..... the terminal command is not found?? lscpi -nn grep Network

---

### Post by kevdog on 2007-10-10
You didnt type it correctly

---

### Post by tkon1567 on 2007-10-10
When I upload the driver the only part of it I need to use are the sys. and inf. parts??

---

