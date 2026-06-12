---
title: "excel macros in oo calc or other?"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by Brandon_oma#692 on 2010-02-03
Hi all,
 
I use excel at workand would like to work on the files at home. When opened in open office calc everything looks fine but my macros do not function properly. I think paste special paste as values is the part messing up since it is pasting the formula instead of the value. I do not have ms office at home. I am using ubuntu and am just learning about it. Is it possible to get this file to work both in excel and OO calc? Also does something else exist that may work instead of OO calc? The file would be used in excell also so it needs to still work that way.
 
(is all variants correct for this question)
 
Thanks

---

### Post by audiomick on 2010-02-03
Hi.
I have heard that there has been some progress, but I know that macros are an issue. I have the problem myself with a spreadsheet for calculating the hang angles for a particular loudspeaker system.

If the worst comes to the worst, you might have to put an excel on your Ubuntu machine with wine. I haven't done that myself, but am sure that excel works well in wine.

---

### Post by Brandon_oma#692 on 2010-02-04
can someone help me make a macro in oo calc that does what this excel one does?
 
starts on sheet "calc" goes to sheet "list" copies pastes copies again pastes again inserts a row then returns you to sheet "calc"
 
Sub copyb()
'
' copyb Macro
' Macro recorded 2/2/2010 by bwise
'
'
    Sheets("LIST").Select
    Range("A1:J1").Select
    Selection.copy
    Range("A11").Select
    Selection.PasteSpecial Paste:=xlPasteValues, Operation:=xlNone, SkipBlanks _
        :=False, Transpose:=False
    Application.CutCopyMode = False
    ActiveWindow.ScrollColumn = 2
    ActiveWindow.ScrollColumn = 3
    ActiveWindow.ScrollColumn = 4
    ActiveWindow.ScrollColumn = 5
    ActiveWindow.ScrollColumn = 6
    ActiveWindow.ScrollColumn = 7
    Range("AA1:AB1").Select
    Selection.copy
    Range("AA11").Select
    ActiveSheet.Paste
    Application.CutCopyMode = False
    Range("AA14").Select
    ActiveWindow.ScrollColumn = 6
    ActiveWindow.ScrollColumn = 5
    ActiveWindow.ScrollColumn = 4
    ActiveWindow.ScrollColumn = 3
    ActiveWindow.ScrollColumn = 2
    ActiveWindow.ScrollColumn = 1
    Rows("11:11").Select
    Selection.Insert Shift:=xlDown
    Range("A16").Select
    Sheets("CALC").Select
End Sub

---

### Post by dondiego2 on 2010-02-04
> **Brandon_oma#692 said:**
> Hi all,
 
I use excel at workand would like to work on the files at home. When opened in open office calc everything looks fine but my macros do not function properly. I think paste special paste as values is the part messing up since it is pasting the formula instead of the value. I do not have ms office at home. I am using ubuntu and am just learning about it. Is it possible to get this file to work both in excel and OO calc? Also does something else exist that may work instead of OO calc? The file would be used in excell also so it needs to still work that way.
 
(is all variants correct for this question)
 
Thanks

Try gnumeric.  I couldn't get my macros to work with open office either.  They all work in gnumeric - even the keyboard shortcuts work as in excel.

---

### Post by mk1w86 on 2010-02-04
I've had problems with this and had to get MS Office 2007. :(

I think it is something to do with the macro language used, MS Office uses Visual Basic for Applications (VBA) whereas OpenOffice uses a different language (I'm not sure what it's called).  I've not tried Gnumeric though so it is probably worth a try. ;)

---

### Post by dondiego2 on 2010-02-04
> **mk1w86 said:**
> I've had problems with this and had to get MS Office 2007. :(

I think it is something to do with the macro language used, MS Office uses Visual Basic for Applications (VBA) whereas OpenOffice uses a different language (I'm not sure what it's called).  I've not tried Gnumeric though so it is probably worth a try. ;)


Gnumeric is awesome in my opinion.  I had a macro heavy Excel spreadsheet that just blew up in open office. With Gnumeric everything worked great.  The only problem I had is after adding a few more lines of data it stopped saving the newly added data.  I then checked the save options and I was saving it as an Excel spreadsheet.  Once I changed that to save as a Gnumeric spreadsheet the problem disappeared.

If I ever want to go back to Excel (I doubt it) I can just re-save it as an Excel file.

---

### Post by Jerry N on 2010-02-04
> **dondiego2 said:**
> Gnumeric is awesome in my opinion.  I had a macro heavy Excel spreadsheet that just blew up in open office. With Gnumeric everything worked great.  The only problem I had is after adding a few more lines of data it stopped saving the newly added data.  I then checked the save options and I was saving it as an Excel spreadsheet.  Once I changed that to save as a Gnumeric spreadsheet the problem disappeared. 

PMFJI but how do you get the Excel (Excel 97, in this case) to run in Gnumeric?  My Excel macro pops up a data entry screen and I can't find anyplace in Gnumeric to get it started.

Jerry

---

### Post by dondiego2 on 2010-02-04
> **Jerry N said:**
> PMFJI but how do you get the Excel (Excel 97, in this case) to run in Gnumeric?  My Excel macro pops up a data entry screen and I can't find anyplace in Gnumeric to get it started.

Jerry

I just tried it on some button macros that I have on a work spreadsheet and they did not work.  Apparently it doesn't work with macros assigned to buttons.  I do know there is Python plug-in that you can get and you can write Python scripts.  I am going to check that out when I get home.

---

### Post by Brandon_oma#692 on 2010-02-04
the macros i am using are assigned to buttons. what is another easy way to run them? I will be running one several times per minute.

---

### Post by Jerry N on 2010-02-04
> **Brandon_oma#692 said:**
> Hi all,
 
I use excel at workand would like to work on the files at home. When opened in open office calc everything looks fine but my macros do not function properly..... 

It has been a while since I tried it but I think my Excel 97 macros worked OK when I installed Office 97 using Codeweavers Crossover (which costs money).  I seem to recall that when I tried Office 97 in Wine a couple years ago not everything worked right but I need to try Wine again.  Of course, if you don't have a copy of Office or Excel that you could install in Wine then that avenue isn't available.

Jerry

---

### Post by Jerry N on 2010-02-04
**UPDATE:**  I just now installed the latest version of Wine in Ubuntu 9.04 and used it to install Excel 97.  I loaded my Excel program that has the data input control panel (multiple data entry points and buttons) and it seems to be working just fine.  Now if I could find some way to make Excel 97 work in Windows 7, without upgrading Windows 7 to the professional version and installing a virtual Windows XP.

Jerry

---

### Post by mk1w86 on 2010-02-05
From a quick Google search it looks like installing MS Office 97 on Windows 7 can cause problems with UAC because of the registry changes it makes.  I think the best way to run Office 97 on Windows 7 would be run it on an older Windows version running in a virtual machine, Office 97 will run on all Windows versions all the way back to NT 3.51 (except Vista and 7 of course).

If you want to use MS-DOS based Windows 9x in the virtual machine I would recommend you use Microsoft Virtual PC:

[http://www.microsoft.com/downloads/details.aspx?FamilyId=04D26402-3199-48A3-AFA2-2DC0B40A73B6&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyId=04D26402-3199-48A3-AFA2-2DC0B40A73B6&displaylang=en)

or if you want to use an NT based version of Windows (except 3.51) I would recommend VirtualBox:

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by Thelasko on 2010-02-05
Office 97 is the last version of Office made that doesn't require activation.  In my opinion, Microsoft is trying to kill it off for this reason.  I don't think you will get it to work with the newer versions of Windows without some serious hacking.

---

### Post by mk1w86 on 2010-02-05
> **Thelasko said:**
> Office 97 is the last version of Office made that doesn't require activation.  In my opinion, Microsoft is trying to kill it off for this reason.  I don't think you will get it to work with the newer versions of Windows without some serious hacking.

No, MS Office 2000 is the last version that doesn't require activation.  MS Office 97 has been unsupported by Microsoft for a very long time. ;)

---

### Post by Brandon_oma#692 on 2010-02-05
> **Thelasko said:**
> Office 97 is the last version of Office made that doesn't require activation. In my opinion, Microsoft is trying to kill it off for this reason. I don't think you will get it to work with the newer versions of Windows without some serious hacking.
 
 
how would i get a copy of excel 97 and run it in linux? I am new to this. I am running ubuntu dual booted and trying to get rid of windows eventualy.

---

### Post by mk1w86 on 2010-02-05
To run MS Office 97 on Ubuntu you can use Wine like Jerry N has.

---

### Post by mikechant on 2010-02-05
> how would i get a copy of excel 97 and run it in linux?

You can buy a legitimate copy of MS Office 97 (with Install CDs, license and certificate of authenticity) for a quite small sum.

For example, this place looks legit (it's high up the google rankings and I'm sure MS would have had it taken out and shot if it wasn't)
[http://www.oldsoftware.com/dealers.html](http://www.oldsoftware.com/dealers.html)

They have Office 97 from $34.

This being a respectable website, we can't discuss any way of obtaining this product which does not result in a fully licensed version being installed.

---

### Post by mk1w86 on 2010-02-05
> **Brandon_oma#692 said:**
> how would i get a copy of excel 97 and run it in linux? I am new to this. I am running ubuntu dual booted and trying to get rid of windows eventualy.

I was just thinking, is there a particular reason you want MS Office 97, why not get 2000 or 2003? :-k

Just bear in mind 2003 will require activation. ;)

---

### Post by audiomick on 2010-02-05
> **mk1w86 said:**
> I was just thinking, is there a particular reason you want MS Office 97, why not get 2000 or 2003? :-k

[COLOR=Red]Just bear in mind 2003 will require activation.[/COLOR] ;)
I think that is why. I can understand it too, quite without any intentions contrary to the user agreement from MS. If my box crashes and I have to re-install, I don't want to have to be ringing up some idiot and convincing him I have the right to re-install a program.

---

### Post by Sir Jasper on 2010-02-05
Hi,

SoftMaker is a commercial suite (with a Debian version as well as a windows version) which can read and write most Microsoft Office files.

There is a 30 day trial which you might try to see if it can run your Excel macro. The trial version will not write back to Excel format - though the paid version will (and it may be significantly less costly than Microsoft Office).

My regards

Otherwise, did you try the macro in the latest version of Open Office?

---

### Post by Brandon_oma#692 on 2010-02-05
> **Sir Jasper said:**
> Hi,
 
SoftMaker is a commercial suite (with a Debian version as well as a windows version) which can read and write most Microsoft Office files.
 
There is a 30 day trial which you might try to see if it can run your Excel macro. The trial version will not write back to Excel format - though the paid version will (and it may be significantly less costly than Microsoft Office).
 
My regards
 
Otherwise, did you try the macro in the latest version of Open Office?
 
I would need to write back to an .xls so the trial would not work but i will try it.  I believe i have the latest version of oo how can i be sure?
 
 
If i could make a new macro to do what this one does i could make another button for it and use it in oo at home then use the first macro ar work in excel.

---

### Post by Sir Jasper on 2010-02-05
Hi,

If you had an Open Office macro I doubt that would work because when you save it in Excel format the macro is probably unlikely to work when you reload it back at work.

If you load Open Office, then click on Help, then click the bottom item it will tell you which version you have.

Try the 30 day trial to see if the macro works. If it does then perhaps your employer may help with the cost of the full version.

My regards

---

### Post by Jerry N on 2010-02-05
> **mk1w86 said:**
> No, MS Office 2000 is the last version that doesn't require activation.  MS Office 97 has been unsupported by Microsoft for a very long time. ;)

I stay with Office 97 because it does the job and I don't need Microsoft support on it anyway.  The trial versions of Office 2007 and Office 2010 aren't compatible with my Excel 97 macros any more than OpenOffice.  In my past experiments, I found that Excel 97 ran better in Linux (under wine/crossover) than Openoffice.  

Jerry

---

### Post by Jerry N on 2010-02-05
> **Sir Jasper said:**
> Hi,

SoftMaker is a commercial suite (with a Debian version as well as a windows version) which can read and write most Microsoft Office files.

There is a 30 day trial which you might try to see if it can run your Excel macro.  

I just downloaded SoftMaker and found this in it's documentation (PlanMaker is the spreadsheet component of SoftMaker):

[COLOR="Red"]"PlanMaker is not able to execute macros and VBA scripts stored in Excel documents. When an Excel file is opened that contains macros or scripts, they will be ignored. "[/COLOR]

So I guess I won't install it. 

Jerry

---

### Post by mk1w86 on 2010-02-05
> **Jerry N said:**
> I stay with Office 97 because it does the job and I don't need Microsoft support on it anyway.  The trial versions of Office 2007 and Office 2010 aren't compatible with my Excel 97 macros any more than OpenOffice.  In my past experiments, I found that Excel 97 ran better in Linux (under wine/crossover) than Openoffice.

Jerry

That's fine, I was responding to Thelasko's point (post 13) about Microsoft trying to kill off Office 97 when they effectively killed it off many years ago (as far as they are concerned). ;)

---

### Post by Thelasko on 2010-02-05
> **mk1w86 said:**
> No, MS Office 2000 is the last version that doesn't require activation.  MS Office 97 has been unsupported by Microsoft for a very long time. ;)

Ah, good info!  I don't remember Office 2000 very well.  I remember Office 97, XP (whatever that was), and Office 2003.

---

### Post by mk1w86 on 2010-02-05
> **Thelasko said:**
> Ah, good info!  I don't remember Office 2000 very well.  I remember Office 97, XP (whatever that was), and Office 2003.

I'd say Office 2000 was most similar to Office XP, almost like Office XP without activation. :o

---

### Post by Brandon_oma#692 on 2010-02-05
> **Sir Jasper said:**
> Hi,
 
If you had an Open Office macro I doubt that would work because when you save it in Excel format the macro is probably unlikely to work when you reload it back at work.
 
If you load Open Office, then click on Help, then click the bottom item it will tell you which version you have.
 
Try the 30 day trial to see if the macro works. If it does then perhaps your employer may help with the cost of the full version.
 
My regards
 
 
could i have 2 macros that do the same thing? macro 1 works in excel and have macro 2 work in another software? 
 
 
if this is possible i will be asking how to make "macros" (probably wrong term would like to know the correct one) in gnumeric. oo calc seems to have problems with copy and paste special.

---

### Post by Sir Jasper on 2010-02-05
Hi,

Try loading your spreadsheet into OO calc or another speadsheet that can save to Excel format. Do not worrry if the Excel macro works but just add some data (as a test) then save it in Excel format.

Try the saved spreadsheet at work and if the macro still works (indicating that unreadable macros are ignored - but resaved) then you could try to build a separate identical macro (meaning it does the same thing) as you are suggesting.

My regards

---

### Post by dondiego2 on 2010-02-05
I don't think you can make macros in Gnumeric.  You would have to do all your programming in individual cells.  It is the same as Google Docs.  You can do some pretty powerful stuff with the cell programming in Google Docs and in Gnumeric.  I could be wrong but I didn't see any place for macro programming in Gnumeric.  Last night I was playing around with Python and Gnumeric and so far I have found out that you can program functions using Python for Gnumeric and use those functions in the cells but I did not see a true macro programming like there is in Excel.

I haven't looked at OpenOffice yet to see what the macro capabilites of that program are.  I will maybe take a look at it tonight - I know - another exciting Friday night!

---

### Post by Brandon_oma#692 on 2010-02-05
> **Sir Jasper said:**
> Hi,
 
Try loading your spreadsheet into OO calc or another speadsheet that can save to Excel format. Do not worrry if the Excel macro works but just add some data (as a test) then save it in Excel format.
 
Try the saved spreadsheet at work and if the macro still works (indicating that unreadable macros are ignored - but resaved) then you could try to build a separate identical macro (meaning it does the same thing) as you are suggesting.
 
My regards
 
 
thank you i will try that first.
 
The excel version i use at work is 2003

---

