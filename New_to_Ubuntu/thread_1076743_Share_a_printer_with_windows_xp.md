---
title: "Share a printer with windows xp"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by kcr-By-Tor on 2009-02-21
Can someone give me a step by step on how to find and share the printer that I have hooked up to a windows xp machine with my newly installed Ubuntu 8.10 machine?.  I am using a wireless network and I believe I have already installed samba, but I am not quite sure how to check.  I am really new to this.  Can anyone help?

---

### Post by kcr-By-Tor on 2009-02-21
Ok. I do have samba installed and I went to places > network and opened the Home Office network I received an error message, Unable to mount location. Failed to retrieve share list from server.  

How do I find my network in Ubuntu?

---

### Post by rafac24 on 2009-02-21
This is what worked for me when I had a network printer installed on a Windows XP machine and I was trying to print from Ubuntu:

On Ubuntu:
System => Administration => Printing
Click to 'Add' New Printer
Then click the 'Windows Printing via Samba' 
In the 'SMB' text box type in the specifications of your network and network printer, for example:

Network/Computer/Printer_Name

where, 'Network' represents your home network name / 'Computer' represents the computer network name assigned to the computer running windows and the windows printer / and 'Printer_Name' is the assigned name of the printer when it was shared through Windows. 

Hope that helps.

---

### Post by cariboo on 2009-02-21
You don't need samba to share a printer connected to a windows computer with Ubuntu.

The above poster was partially right, he just missesd a few steps. 

[list=1]
[*] Go [here]("http://www.openprinting.org/printer_list.cgi") to make sure your printer is supported.
[*] If you printer is supported ,on your windows computer go to Start-->Printers and Faxes, and right click your printer, and click the sharing tab
[*] See screenshot1. Make sure Share This Printer is Selected and make sure your printer name doesn't have any  spaces in it.
[*]On your Ubuntu computer go to System-->Administration-->Printing and select New Printer.
[*] In the New Printer window click on Network Printer and select Windows Printer via SAMBA.
[*] click the browse button and select you printer from the list. See screenshot2
[*] click forward, and just follow the prompts from there
[/list]

---

### Post by kcr-By-Tor on 2009-02-21
> **rafac24 said:**
> This is what worked for me when I had a network printer installed on a Windows XP machine and I was trying to print from Ubuntu:

On Ubuntu:
System => Administration => Printing
Click to 'Add' New Printer
Then click the 'Windows Printing via Samba' 
In the 'SMB' text box type in the specifications of your network and network printer, for example:

Network/Computer/Printer_Name

where, 'Network' represents your home network name / 'Computer' represents the computer network name assigned to the computer running windows and the windows printer / and 'Printer_Name' is the assigned name of the printer when it was shared through Windows. 

Hope that helps.
Once i figured out the names of my network, shared computer and printer your instructions worked perfectly.  Thanks for your help!!!!

---

### Post by kcr-By-Tor on 2009-02-21
> **cariboo907 said:**
> You don't need samba to share a printer connected to a windows computer with Ubuntu.

The above poster was partially right, he just missesd a few steps. 

[list=1]
[*] Go [here]("http://www.openprinting.org/printer_list.cgi") to make sure your printer is supported.
[*] If you printer is supported ,on your windows computer go to Start-->Printers and Faxes, and right click your printer, and click the sharing tab
[*] See screenshot1. Make sure Share This Printer is Selected and make sure your printer name doesn't have any  spaces in it.
[*]On your Ubuntu computer go to System-->Administration-->Printing and select New Printer.
[*] In the New Printer window click on Network Printer and select Windows Printer via SAMBA.
[*] click the browse button and select you printer from the list. See screenshot2
[*] click forward, and just follow the prompts from there
[/list]
I did have spaces in the names of my computer, which is what kept me from connecting. once i figured that out i manually put the names of the path in the browser.  For some reason when i searched for the shared printer through the browser button ubuntu did not find it.  Thanks for your help!  It's great to have access to this coomunity for help.

---

### Post by rafac24 on 2009-03-08
Same exact thing happened to me. It took me quite a while to get the correct names for my network, computer and printer.

Funny how, in retrospect, it's very simple to get the network printing working!

---

### Post by gibxam on 2009-03-08
:) success! I'll be honest I'm not completely sure what I did ;) but I have been able to connect to my home network and can now print thanks to this thread. Thank you I'm sure I'll be around with more questions.

Max

---

