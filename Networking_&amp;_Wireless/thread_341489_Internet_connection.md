---
title: "Internet connection"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by DuaneR on 2007-01-18
I recently installed ubuntu and have not been able to connect to the internet.  I have a wireless provider.  I tried to connect using evolution.  When I try to send a message I get error message "error while fetching mail"  Host hookup failed.

---

### Post by Metaljaz on 2007-01-18
Are you able to use your web browser or is this just an email problem?

---

### Post by DuaneR on 2007-01-18
I am not able to get on the internet and can not use web browser.

---

### Post by Metaljaz on 2007-01-19
Okay..lets find out a few things. What version of Ubuntu  are you using? Are you
using a laptop and trying to use a pcmcia card, are you using a desktop
which is hardwired to the broadband modem, or a USB device? Tell us your setup and then we
can go from there.

post back

---

### Post by DuaneR on 2007-01-19
Thank you for your help.  Version 2.0    Using a laptop (Dell Inspiron)  The computer has a wireless card.  I used it wwhen I was using windows XP home

---

### Post by Metaljaz on 2007-01-19
From the terminal window type this command. Go all the way to the bottom of the
list and cut and paste the results of *network. Paste it here.

lshw

Also try this:
Under System>Administration>Networking>
Network Settings should now be displayed. 
What interface is active? eth0, ath0 or what? Is the active device also your default gateway device?
If there is none active but listed in the interface box activate it by clicking the activate button.
Click on the DNS tab and there should be ip addresses listed under DNS servers. The
search domain should be your isp.

---

### Post by DuaneR on 2007-01-19
Please excuse my stupidity but what do you mean by terminal window?

---

### Post by DuaneR on 2007-01-19
Interface that is active is eth1

I  clicked on the DNS tab and the DNS servers is blank and the Search Domains is blank also.

---

### Post by Metaljaz on 2007-01-19
ok..getting somewhere.
the terminal is under Applications>Accessories
Was there an active wireless connection?
Because this may take a little time can you allow private messages. Go into 
user CP and edit profile.

---

### Post by DuaneR on 2007-01-20
I opened *network and typed lshw

I can  not cut from my linux computer and paste to my windows computer.

this is what the last lines are at the bottom:  resources: ioport:18c8-10df irq:10
duane@duane-laptop:~$

I Systems>Administration>Networking>  I got Network Settings then Connections I clicked on  
Wireless connection then clicked on DNS and all everything is blank.

---

### Post by Metaljaz on 2007-01-20
After you type lshw in the terminal window i need to know what is the following three
entries. Should look something like what i have posted.

 *-network
          description: Wireless interface
          product: AR5212 802.11abg NIC
          vendor: Atheros Communications, Inc.

---

### Post by DuaneR on 2007-01-20
*-network:0 DISABLED
     description: Ethernet interface
     product: BCM4401 - B0  100Base - TX
     vender:  Broadcom Corporation

---

### Post by Metaljaz on 2007-01-21
Okay the information i was asking for basically tells you that your card is BCM4401 but the chipset is Broadcom. I have posted the link below which is a walk through for how to set the card up. I think the
guide is for a 4318 but i think if you read the entire thread it may work for you.
Post back if you have problems. 

product: BCM4401 - B0 100Base - TX
vender: Broadcom Corporation
Reply With Quote

[http://www.ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://www.ubuntuforums.org/showthread.php?p=1071920&mode=linear)

---

### Post by Metaljaz on 2007-01-21
The below link maybe more helpful to you or easier to follow:
Good Luck

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show)

---

### Post by DuaneR on 2007-01-22
Thank you.  I will give it a try.

---

### Post by DuaneR on 2007-01-22
I really do appreciate your effort to help me but I believe that the instructions that you referred me to are too complicated for me.  I do like using ubuntu but if I can not get online using it, it is not practical for me so will probably go back to Windows.

---

