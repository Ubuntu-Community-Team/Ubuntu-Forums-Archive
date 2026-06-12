---
title: "OpenOffice Spreadsheet - month entry for cell"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by wstay on 2009-03-03
I enter the month FEB into a cell using OpenOffice Spreadsheet and when I press enter it becomes Feb. I would like it to be in capital letters FEB.
How can I format the cell or is there any configuration option to do it?

---

### Post by Tamlynmac on 2009-03-04
I found the easiest way to do this is to type in the data for all the cells you wish to use upper case lettering for and then simply highlight the cells and select: 
Format/Change Case/Uppercase.

You can highlight all the cells in the same column or row by click and drag or hold down the CTRL key on your keyboard to highlight cells in different columns or rows.

Hope this helps.

---

### Post by wstay on 2009-03-04
> **Tamlynmac said:**
> I found the easiest way to do this is to type in the data for all the cells you wish to use upper case lettering for and then simply highlight the cells and select: 
Format/Change Case/Uppercase.

You can highlight all the cells in the same column or row by click and drag or hold down the CTRL key on your keyboard to highlight cells in different columns or rows.

Hope this helps.

Thanks for your help.
What I find strange is that why after typing say JAN or FEB .....in Uppercase and pressing enter, we get Jan or Feb ........(the first letter is Uppercase and the rest of the letters after that become Lowercase).

---

### Post by Tamlynmac on 2009-03-04
One other thing you can do:
You can uncheck autoinput under tools/cell contents/autoinput.
This will turn off your automatic text & number completion. See explaination below.

This will definitely correct your problem and permit your capitalization entires without hesitation. Be sure to read the explaination below. Of course you can always try it and if you find an issue, turn it back on.

Good Luck



  	 	 	 	 	> By default, OpenOffice.org automatically corrects many common typing errors and applies formatting while you type. You can immediately undo any automatic changes with Ctrl+Z.
 The following shows you how to deactivate and reactivate the automatic changes in OpenOffice.org Calc:
 **Automatic text or number completion**

 When making an entry in a cell, OpenOffice.org Calc automatically suggests matching input found in the same column. This function is known as **AutoInput**.
 
[LIST]
[*]To turn the AutoInput on and off, set or 	remove the check mark in front of [**Tools 	- Cell Contents - AutoInput**]("http://ubuntuforums.org/vnd.sun.star.help://scalc/text/scalc/01/06130000.xhp?Language=en-US&System=UNIX&UseDB=no&DbPAR=scalc").
[/LIST]
 **Automatic conversion to date format**

 OpenOffice.org Calc automatically converts certain entries to dates. For example, the entry **1.1** may be interpreted as January 1 of the current year, according to the locale settings of your operating system, and then displayed according to the date format applied to the cell.
 To ensure that an entry is interpreted as text, add an apostrophe at the beginning of the entry. The apostrophe is not displayed in the cell.
 **Quotation marks replaced by custom quotes**

 Choose **Tools - AutoCorrect**. Go to the **Custom Quotes** tab and unmark **Replace**.
 **Cell content always begins with uppercase**

 Choose **Tools - AutoCorrect**. Go to the **Options** tab. Unmark **Capitalize first letter of every sentence**.
 **Replace word with another word**

 Choose **Tools - AutoCorrect**. Go to the **Replace** tab. Select the word pair and click **Delete**.
 

---

### Post by wstay on 2009-03-05
Thanks. 
I got the problem solved from Tools-Cells Content-AutoInput by de-selecting the Check-Box.

---

