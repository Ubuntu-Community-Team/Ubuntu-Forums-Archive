---
title: "Installing Linksys Notebook adapter Model WPC54G ver 7.1"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by BVS1938 on 2009-03-11
Having just installed Ubuntu Desktop 8.10 on an old laptop I need to install the above adapter.  I inserted the Adapter Installation CD whereupon the message 'This medium contains software intended to be automatically started. Would you like to run it?'  'The software will run directly from the medium "Set up Wizard". 
I clicked Run and promptly received a message 'Error auto running software. Error starting autorun program. Permission denied'.
I then reverted to clicking 'Open autorun Prompt' which produced the same messages given above.  I cannot connect to the Internet without this.  The adapter was working fine when it was running the previous Windows Software that I removed when installing Ubuntu :(
Any help would be much appreciated.  Regards.

---

### Post by samborambo on 2009-03-11
The autorun software is the driver and wireless tools and is intended for windows only. Some wireless cards don't have (mature) Linux drivers yet but, in such a case, the Windows drivers may be wrapped with ndiswrapper and used. There's plenty of Howtos on setting up ndiswrapper.

From what I can ascertain from a brief google search, your card should be natively supported in Ubuntu and won't require drivers. To test this, enable roaming mode in network manager and see if it finds your wireless network.

If it doesn't work straight out of the box, open a terminal window and enter the following commands:

```

sudo lspci -nnvv > dump.txt
sudo lsusb >> dump.txt
dmesg >> dump.txt
iwconfig >> dump.txt

```

Attach the dump.txt (in your home folder) to your reply.

---

### Post by lindsay7 on 2009-03-11
Samborambo,

Where is the network manager that you talk about in you post? And how do you enable roaming. I can not find where to do this.

---

### Post by wolfen69 on 2009-03-11
just left click the network icon on the taskbar. do you see a list of available networks?

---

### Post by lindsay7 on 2009-03-11
Ok, I am sure he is talking about the "Network Configuration" menu.  I thought I was missing a setting someplace else.

---

