---
title: "Brother 2170w &quot;not connected&quot;"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by Nitrosyncretic on 2011-01-22
I followed standard install for Ubuntu 10.10 to add my Brother 2170w wireless printer (already setup and working fine with other computers). I installed it from the network and it appeared as printer in the manager, but when I try to print the test page, it says "not connected."  I did the troubleshooting and it declared that it could find no solution.

Please help. I am completely at a loss.

Details:

Brother 2170W wireless printer that I have been using for years with other laptops in Windows XP.

I want to install it on my Dell XPS 15 withUbuntu 10.10. It's a dual boot setup. 
The printer is already working for the Windows 7 system on the machine.

---

### Post by cariboo on 2011-01-22
Can you ping the printer?

If you run:

```
sudo nmap -sP 192.168.1.0/24
```

Does the printer show up in the listing?

---

### Post by migs73 on 2011-01-22
> **Nitrosyncretic said:**
> I followed standard install for Ubuntu 10.10 to add my Brother 2170w wireless printer (already setup and working fine with other computers). 

?? What standard install ??

Are all the other computer running non linux OS's?

Have you had it working in the past on Ubuntu?

Please let us know how you installed the the printer driver/printer.

If your printer is not suported by the standard drivers in Synaptic, you will need to install the ones from the Brother website ([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html))

And follow their instructions including the 'Before the Installation' section on the top of the linked page.

Regards

Mike

---

### Post by Nitrosyncretic on 2011-01-22
The Brother is already setup for wifi and used by other windows machines. I installed it in Ubuntu using System > Administration > Printing. I used the Add button, selected Network, searched for my network SSID and the printer appeared in the list. I selected it. The next dialog offered to search and install and driver and apparently succeeded. The printer now appears as my default printer and I have a manager icon in the upper right of Ubuntu. However, when I print it produces "not connected." The computer is currently connected to my network and the printer shows the blue "ready" light.

I installed Ubuntu 10.04 using Wubi on Windows 7, then upgraded to 10.10.

==============================================

sudo nmap -sP 192.168.1.0/24 produces:

"sudo: nmap: Command not found"

---

### Post by Nitrosyncretic on 2011-01-22
Whoops. The icon in the upper right bar is no longer present. The printer manager says "Stopped -- Unable to locate printer 'BRW01..."

---

### Post by migs73 on 2011-01-22
Try the procedures set out in the link I posted above.

I don't know if Ubuntu just uses the Brother default drivers using the process you mentioned, which may not support your printer.

Mike

---

### Post by walt.smith1960 on 2011-01-23
> **Nitrosyncretic said:**
> 
.........................

I installed Ubuntu 10.04 using Wubi on Windows 7, then upgraded to 10.10.

==============================================

sudo nmap -sP 192.168.1.0/24 produces:

"sudo: nmap: Command not found"

I've never used Wubi.  I wonder if something about  Wubi is causing some sort of network communication problem with the printer?  My Brother printer network installs have been uneventful when the printer was found by Ubuntu. There might be something worth taking a look at.  Go to system> administration > printing and right click on the printer icon.  Select properties.  What's in the device URI box?  I have had issues with flawed entries there which result in the printer not being found.  I've taken to using the following entry
```
socket://192.168.1.110:9100
```
using your own printer's IP address.  This seems to enable the OS to find the networked printer consistently on my systems.

---

### Post by Nitrosyncretic on 2011-01-25
Thank you for the link, However I find the 'Before the Installation' instructions opague. How do I know whether to download a lpr or cups driver? How do I know which of the five scanner versions to try?

I guess I need more hand holding. Please help,

- Alan

> **migs73 said:**
> ?? What standard install ??

Are all the other computer running non linux OS's?

Have you had it working in the past on Ubuntu?

Please let us know how you installed the the printer driver/printer.

If your printer is not suported by the standard drivers in Synaptic, you will need to install the ones from the Brother website ([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html))

And follow their instructions including the 'Before the Installation' section on the top of the linked page.

Regards

Mike

---

### Post by walt.smith1960 on 2011-01-26
> **Nitrosyncretic said:**
> Thank you for the link, However I find the 'Before the Installation' instructions opague. How do I know whether to download a lpr or cups driver? **How do I know which of the five scanner versions to try?**

I guess I need more hand holding. Please help,

- Alan

Scanner?  This is just a laser printer, is it not?  I agree, the 'before you install' instructions are confusing. Brother has chosen to mix .deb & .rpm distro directions. Why they did this I'm not sure.  I found it somewhat helpful to print the directions out and circle the steps that are applicable. Many of the steps do not apply to debian/ubuntu or they are required for multifunction machines and do not apply to printers only.

Are you using this page for drivers?

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html)

For a printer, these are the two commands I enter before installing the .deb files

**1. "sudo aa-complain cupsd"** command is required before the installation.**2. "sudo mkdir /usr/share/cups/model"** command is required before the installation.I don't know if they're necessary but they don't appear to do any harm.

I've installed both the lrp & cups drivers, lrp first seems to be required. I tried just the cups driver and the installer complained, said I had to install the lrp driver first.

---

### Post by migs73 on 2011-01-26
> **Nitrosyncretic said:**
> Thank you for the link, However I find the 'Before the Installation' instructions opague.?

I guess I need more hand holding. Please help,

- Alan

You're right, they are not the most easy to follow instructions.

But as Walt says only those two commands should be required as a prerequisite.

The instructions on the License agreement page have a 'Note' section (see below) about how to download the files, just ignore this and click on the button, Ubuntu downloads the file and gives you the default option for unpacking/installing the drivers, which works. Saves a lot of hassle.

[B]EDIT.. If you are using a WUBI install and have a 64bit machine, you likely have the 64bit Ubuntu, the above tip I gave will not work in this case as you have to force Ubuntu to use the 32bit drivers and this requires arguments in the terminal, as described on the brother website below!!!!

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html)[/B]

---

### Post by criticalsmile on 2012-03-05
Brother 2170w will not work on my system unless I have some extra services running. I can't tell you which ones yet, but I can tell which caused my Brother 2170w to suddenly work over Ethernet.

udev
dmesg
cups 

I doubt that I deactivated cups. I think it starts when needed so I don't think that was the source of my problems. Just go to SYSTEM->ADMINISTRATION->BootUp-Manager (Install from Synaptic by searching for keyword BUM)  Then click ADVANCED and find the services that I mentioned above.

My Brother printer is printing just fine now. :-)

---

