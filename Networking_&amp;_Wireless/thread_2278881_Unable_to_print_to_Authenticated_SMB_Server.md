---
title: "Unable to print to Authenticated SMB Server"
date: 2015-05-19
forum: Networking &amp; Wireless
---

### Post by eric_miller3 on 2015-05-19
Hi All,

I'm attempting to print from a network printer hosted by an SMB server which requires some authentication.  The Windows instructions are presented here: [http://www.sdsmt.edu/Campus-Services/ITS/How-Do-I/Install-a-Network-Printer/](http://www.sdsmt.edu/Campus-Services/ITS/How-Do-I/Install-a-Network-Printer/).  
I can access the printer maintenance webpage using my username/password, so I know that this is not the issue.  I've also verified the correct domain.  

I'm running Ubuntu 14.04.  The steps I've taken are:
Printers
Add
Network Printer
Windows Printer via SAMBA
Enter printer location after smb://
Select Prompt user if authentication required. 
Hit "Verify"

An authentication window pops up.  I enter my username/password and the domain I obtained from the local IT dept.  I get the result "Not Authorized.  The password may not be correct."  

What am I doing wrong here?  

Thanks,
Eric

---

