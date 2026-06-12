---
title: "can i open a Microsoft word 7 documents  in open office"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by blake7 on 2010-01-26
yea and can i edit it and save as well

thank yuo

ps if i cant how can i.

---

### Post by benfindlay on 2010-01-26
If you mean office 2007 files, like the .docx files then yes you can. Although I believe that they will be read only, but you can save them as normal (older) .doc files through open office and edit them as normal.

Hope this helps

---

### Post by blake7 on 2010-01-26
cheers thatnk you for that

---

### Post by SirBismuth on 2010-01-26
> **benfindlay said:**
> If you mean office 2007 files, like the .docx files then yes you can. Although I believe that they will be read only, but you can save them as normal (older) .doc files through open office and edit them as normal.

Hope this helps

I have successfully opened .docx and .xlsx files in OpenOffice and been able to edit and save them, as well as the older .doc and .xls files.

Note that you should be careful about formatting issues when editing and saving MS Office files with OpenOffice.  Although, I haven't noticed too many issues with the latest versions of OpenOffice, maybe I've just been lucky.

B

---

### Post by cb951303 on 2010-01-26
You can but almost 9 out of 10 times your docs will be ill formatted and formulas/graphs may not be readable.

I definitely wouldn't count on *.docx support of openoffice for serious work.

I had better luck with google docs.

---

### Post by benfindlay on 2010-01-26
> **SirBismuth said:**
> I have successfully opened .docx and .xlsx files in OpenOffice and been able to edit and save them, as well as the older .doc and .xls files.

Note that you should be careful about formatting issues when editing and saving MS Office files with OpenOffice.  Although, I haven't noticed too many issues with the latest versions of OpenOffice, maybe I've just been lucky.

B

Looks like things have improved since I last tried to use docx  files, that's good to know, thanks!

---

### Post by anaconda on 2010-01-26
yep,
And if you like you can also install office2007 on your ubuntu machine.

I did, and it works well with wine.... (you will need a new version of wine though..)

---

### Post by blake7 on 2010-01-27
cheers i try loading office on to my mashine cheers again

---

### Post by anaconda on 2010-01-27
Here is the info from wineHq for installing office 2007
Word, excel and powerpoint work... outlook doesnt..

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)


No overrides are needed to install Office 2007 in 1.1.3 or later. Do not file bug reports for the installer if you have used any native dlls.

Once installed, the following overrides are needed to run:

    * riched20:Set riched20 to 'native' in Winecfg. DO NOT INSTALL IT YOURSELF. Office 2007 comes with its own version of riched20. Without using it, Powerpoint will not launch, and other features may be lacking. 
    * Windows Scripting Host (jscript): Needed for the thesaurus; install it with winetricks wsh56js.
    * symbol.ttf: For versions of Wine prior to 1.1.16, this font must be installed for bullets and equations to display properly
    * usp10: Set usp10 to 'native,builtin' in winecfg for the equation toolbar in Word. There is no need to install it; simply set the override.

---

