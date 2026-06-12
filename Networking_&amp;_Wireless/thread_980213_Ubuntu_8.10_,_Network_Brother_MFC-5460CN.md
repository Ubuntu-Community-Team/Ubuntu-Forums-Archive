---
title: "Ubuntu 8.10 , Network Brother MFC-5460CN"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by xobo on 2008-11-12
New to Linux. Just install Ubuntu 8.10 , trying to make the  Network printer Brother MFC-5450CN work. I have looked into some old titles. I realized that this fax-scanner-printer is not in the 8.10 packages. I have downloaded and installed from brother site the package
[COLOR="Red"]mfc5460cncupswrapper-1.0.1-1.i386.deb[/COLOR] 
also install the package
[COLOR="Red"]mfc5460cnlpr-1.0.1-1.i386.deb[/COLOR]

Now my problem is that after installing the above packages CUPS can see the printer on the network but, it can not see the new printer (driver)packages because it is still not in the list. I do not know how to add the new driver into the CUP list. Cups listing shows many Brother MFC-printers, but not the MFC-5460CN. The same apply  when I go to SYSTEM-ADMINISTRATION-PRINTING. It is not in the list and I am trying to change it to direct to these packages (which are on my desktop) but it give me an errors.

Anyone can please help.

---

### Post by xobo on 2008-11-15
Any reply (testing)

---

### Post by imperius1 on 2008-11-25
Hey xobo, I have the same printer and set it up by following the steps in this post: [http://ubuntuforums.org/showthread.php?t=702105]("http://ubuntuforums.org/showthread.php?t=702105"). Hopefully this helps.

---

### Post by volkswagner on 2008-11-25
Are you sure it is not on the list?  I recall installing a MFC-5440cn.  I followed the steps to add the "pid" (can't remember exact name).  I tried several times, yet the file never was on the list.
Problem was... The file was added to the bottom of the list, not alphabetical with the other brother files.

---

### Post by xobo on 2008-12-06
Sorry for not responding in time. Thank you for your help. I followed the steps that you've suggested. But again, in cups - when I try to install it,there is not any option for that specific printer (mfc5460nc or mfc5460 CUPS V1.1) in it suggested in this link.
[COLOR="Yellow"]PRINTING
   1. Download the Brother LPR package HERE and the CUPS wrapper HERE. Simply install using GDebi by double clicking the file.
   2. Go to the CUPS config. [http://localhost:631](http://localhost:631)
   3. Select Printers. Select Modify printer. Enter a a location and name this is for human readable detail. Select Continue.
   4. Click on the drop down box and select the Brother MFC-5460CN XXX.XXX.XXX.XXX and select continue.
   5. Select Brother for make select continue.
   6. Select the Brother MFC-5460CN CUPS V1.1 for the model and select Modify printer. You can now print a test page from System > Administration > Printing. Right click on the MFC5460CN print and select Print test page.
[/COLOR]

In cups it ask to select model/driver for MFC5460cn.   But as I said, it  is not in  the CUPS list of the brother printers. it give me option to:-
[COLOR="Yellow"]or Provide a PDD FILE[/COLOR]. But I do not know how to provide that file form the download  of the LPR or CUPS that was suggested.
So I am back to the same problem.
Thank you  again for your respond

---

