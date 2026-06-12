---
title: "XP and Ubuntu network do not share files and ICS"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by nanogeek on 2007-08-08
I am an Ubuntu newbie, having installed it about a week ago, so please be patient.
After a number of false starts I finally installed Ubunt 6.10 (edgy eft) on my Pentium II PC. I am trying to network it with my Windows XP machine. The XP-box has an external USB DSL modem that I use to connect to the Internet. I want to share files between the two machines and I want to use the internet connection and the printer on the XP machine from the Ubuntu machine. I connected the two machines with a crossover network cable and configured the two machines. The IP of the XP machine is set to 192.168.0.3 and the Ubuntu to 192.168.0.2  (I read somewhere on the Internet that the USB connection may have the address 192.168.0.1, so I skipped that one.) The submask is set to 255.255.255.0 on both. (I don't know what this means I did this becasue this is what I found you should do while searching for a "How To") I did not set any other parameters like default gateway or DNS. The Internet connection is set to automatically a accept a DNS from the ISP

I used the Windows network Wizard to “allow” printer, file sharing and Internet connection sharing (ICS)


Problems:
1.	The U-box sees the Windows files only intermittently (more later)
2.	The XP-box does not see the U-box at all.
3.	I cannot get to the internet from the U-box

I tried to access files on the XP-box from the U-box and experienced the following behavior.

Using Places->Network Services
I see (after a bit of time) a computer icon with the name “Windows Network”
Double clicking the icon shows me a document icon titled “mshome” – the name of the XP workgroup.
Double clicking the document icon gives me an error message:
Couldn’t display “smb:///mshome”, The location is not a folder.

_Sometimes_ after this the document icon changes to a computer, sometimes not, but if I back up to the Windows Network icon and double click it sometimes I get the computer icon. Be this as it may, after I get the computer icon named mshome and I double click it I get a document icon named “xyv123” which is the name of the XP computer.

Double clicking this icon gives me the same error message as above except that it says “smb:///xyz123” in place of  “smb:///mshome”

_Sometimes_ after this the document icon changes to a computer, sometimes not. Eventually I get a set icons representing the partitions on the XP_box as well as one for the shared folder. Each of these icons has a computer, some network icon thingy and the letters SMB. From here I can open the shared files. 

As I said above, from the XP box I do not see the U-box, and I can’t get on the Internet from the U-box.

I would appreciate help for all three of the above problems.
I have seen similar questions and solutions, but they all seem to have the Internet connection on the Ubuntu side,whereas my Internet connection is on the Windows side. I have tried to install the USB modem on the Ubuntu machine, which failed and everything I can find basically says “forget that idea” 

Since I do not have an Internet connection on the Ubuntu machine, I cannot install software. In addition, since I am very green, brief cryptic messages with a line of code may not be the most useful. Rule 10 of section II in the forum rules, “Always assume that the user is a green user unless you're certain the user is not. Please remember to give detailed instructions some users do not know how to get to a terminal yet.”, certainly applies to me!

Thanks for your patience and your help

 P.S. 
Can someone tell me what the difference between the forums and launchpad is, and where I should really post this question?
Is it impolite to post at both?
Is this a “bug” that should be/needs to be reported?

TIA

---

### Post by lgambett on 2007-08-08
I suggest you to move from an USB modem to an Ethernet-based router; it is cheap, it gives you basic firewall functions and will easily allow you to share files between your Ubuntu and Windows PCs. In my opinion what you reported is not a bug and should not be filed on Launchpad.

---

### Post by nanogeek on 2007-08-08
Wow! talk about fast turnaround time. Thanks for your suggestion.

I actually did buy an ethernet router, but it didn't work with my USB modem and I really didn't want to spend even more money on buying a new Ethernet modem too. (I will return the router for a refund). The fact that I am using a crossover cable and a pentium II machine might have been a tipoff that I am trying to save money. I would prefer not to have to buy more hardware if at all possible.

Intermittent viewing of network  assests is not a bug?

---

