---
title: "Having problem connecting to internet using Ubuntu."
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by anksrivastava on 2007-10-02
I am an student studing in India. I have had previous experiences with Red Hat and Suse linux.
I have come across strange problem while trying to connect to the ADSL modem using Ubuntu linux. I have a DATAONE connection and UT-300R2U ADSL modem connected through ethernet port. After I installed Ubuntu on my pc it is refusing to connect to the net. The ethernet light on the modem does not glow, so probably connection is not being recognised. But the networking applet shows that Local Area Network is connected. The same internet setup worked out of the box in SUSE and works well in Windows XP which I have as dual boot with linux just for net use. I tried to set DHCP and static addresses using the networking applet in system menu. All my PPoE settings, user name & passwords are stored on modem. Can anyone please help me, I desperately need internet to work on the linux setup.

---

### Post by maduranga on 2007-10-02
Does the light that indicate the ADSL link active glow? your computer seems to be got connected to the ADSL modem but the modem don't have got linked. I suggest you to re-check all configuration of the modem, it will maybe help you.

---

### Post by greenstar on 2007-10-02
Open terminal and do:

ifconfig -a

Then copy & post the output here.

Greenstar

Edit: Also check your ethernet cable.

---

### Post by mips on 2007-10-02
Also post output of **lspci -v**

---

### Post by anksrivastava on 2007-10-02
The light of ADSL connection glows but the light for Ethernet link stays off

---

### Post by anksrivastava on 2007-10-02
i am presently connected in windows since internet works only on XP :(
I'll post those outputs once I restart my computer.

---

### Post by anksrivastava on 2007-10-20
Well, I just downloaded ver 7.10 of Ubuntu and the problem vanished. Thanks for the help to you all.

---

### Post by Vorticity on 2007-10-20
Same thing happens, should I post the ifconfig printout?

---

### Post by sam-c on 2007-10-23
> **greenstar said:**
> Open terminal and do:

ifconfig -a

Then copy & post the output here.

Greenstar

Edit: Also check your ethernet cable.

I am using ubuntu for first time and want to connect thru ADSL 
is ifconfig the command or a wizard??
Thanks
Sam

---

### Post by Stemp on 2007-10-23
> **sam-c said:**
> I am using ubuntu for first time and want to connect thru ADSL
If you are using an adsl modem check  : [ADSLPPPoE]("https://help.ubuntu.com/community/ADSLPPPoE")

---

