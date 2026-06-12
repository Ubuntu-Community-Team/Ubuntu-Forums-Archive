---
title: "network printing from Ubuntu to Vista"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by SVWander on 2009-07-10
I have tried for days to get the laptop running Ubuntu 9.04 to connect to a desktop system running Vista without any luck. I have tried to read Setting up Samba, read Network printing with Ubuntu and a few other posts trying to solve this problem. When I try to find the New Printer using Find New Printer using SAMBA I get the following error message:

There were no print shares found.  Please check that the Samba service is marked as trusted in your firewall configuration.

To do this, select System->Administration->Firewall from the main menu.

I have not installed a firewall on this laptop and none is shown in the System Menu.

I have the same problem on a netbook. Except that instead of getting the error message I get a list of computers on the network but when I click on the computer connected to the printer it shows nothing. On the same netbook I can boot into XP and connect to the network printer.

Any help would be appreciated . . . I'm always talking to people about the benefits of using Ubuntu so this is very embarrassing!

---

### Post by irv on 2009-07-10
question: Do you have your printer connected to your desktop or is in on your network? Is your laptop wireless on your network?

How I setup my printer: I have it on my network with a static IP address so I can print to it from anywhere on my network. I find this works the best because if anyone come over with there laptop they can print to my printer if they get on my network.

---

### Post by SVWander on 2009-07-10
> **irv said:**
> question: Do you have your printer connected to your desktop or is in on your network? Is your laptop wireless on your network?

How I setup my printer: I have it on my network with a static IP address so I can print to it from anywhere on my network. I find this works the best because if anyone come over with there laptop they can print to my printer if they get on my network.

The printer is connected to the desktop which runs Vista. I am at a friend's place. So I am connecting via a wireless router from both the netbook and this Dell Inspiron 1200 laptop. As I said the netbook dual boots into XP and in XP it can connect to the printer. So it must be a SAMBA or firewall setting. Or at least something within the Ubuntu operating system.

Tim

---

### Post by superprash2003 on 2009-07-10
you dont need samba to connect to a network printer.. hope this helps [http://www.prash-babu.com/2008/07/how-to-connect-to-network-printer-in.html](http://www.prash-babu.com/2008/07/how-to-connect-to-network-printer-in.html) .. basically specify the ip address of the vista machine and provide the full link than relying on ubuntu to search for it automatically

---

### Post by micgrideon on 2010-02-11
No, That did not help.

---

### Post by cjazz on 2010-02-11
Two questions, more for my clarity than anything else:

1. What is kind of printer is it?

2. Have you tried to set it up using the "New printer > Windows printer via Samba" option under System > Administration > Printing?

For a printer directly connected to a Windows computer, the entry smb://WORKGROUP/COMPUTER_NAME/printer_name tends to work very well for me, with WORKGROUP being your own workgroup name, COMPUTER_NAME being the name of the Windows computer to which the printer is connected and printer_name being the share name of the printer as set under Windows. Obviously the printer needs to be shared in Windows, and it often helps to turn off bi-directional printing.

---

