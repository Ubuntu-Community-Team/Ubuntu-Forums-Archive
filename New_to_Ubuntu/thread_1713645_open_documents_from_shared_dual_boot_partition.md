---
title: "open documents from shared dual boot partition"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by /mr. matt/ on 2011-03-24
Hello all,

A bit of background: I am dual booting windows 7 and ubuntu 10.10. I need windows because I go to school online and some of the programs do not support linux. I recently tried to consolidate documents onto a shared ntfs partition that I created in windows. The issue I am having is with documents created in Microsoft office. The error states:

title bar: document in use

message: document file "name.doc/docx/xls" is locked for editing by: unknown user
Open document read only or open a copy of the document for editing.


I think it is a windows permission error. And I think theoretically I could just back up that partition to an external drive and repartition the hard drive with gparted. Then move the files back, but I really do not understand Windows file permissions. So it may just get greedy and take permission away from Linux again. Any help is appreciated and if I missed any critical information just ask.

Thanks,
Matt

---

### Post by Paddy Landau on 2011-03-24
I am not entirely sure what is happening with you.

However, I know that when an operating system is not shut down correctly, it can lock the file system.

Boot into Windows; open the document (just to ensure that it opens correctly); close it; and shut down Windows cleanly.

Then boot into Ubuntu and try again. Let us know what happens.

---

### Post by /mr. matt/ on 2011-03-24
Thanks for the quick reply. I tried this solution. Three times just to make sure. Windows shut down properly all three times and the files opened perfectly in word. I was found this error elsewhere in relation to OpenOffice, but the fix I found did not seem to apply.

_Matt

---

### Post by Paddy Landau on 2011-03-25
Matt, I didn't quite understand the last post. Did you find a solution, or do you still have the problem?

If you found the solution, please post it so other people can learn; and mark the thread as solved.

If you are still struggling, can you post a screen-shot of the error message? (When you get the error, press *Alt-Print Screen* to save the screen-shot.) Then we can take it from there.

---

### Post by Dutch70 on 2011-03-25
Did you try opening it in windows and changing the permissions to allow read/write for other users?

---

### Post by /mr. matt/ on 2011-03-25
Still getting the error. I tried changing the permissions in windows the problem is they apply only to windows users. Unless it has something to do with sharing. But since Ubuntu matt is not listed as a user in windows I cannot give ubuntu matt permission to access the files. Here is a screeshot. Again it is only related to .doc and .docx (office files) on that drive. I can open and edit all other files.

Thanks,
Matt

---

### Post by Paddy Landau on 2011-03-25
This is indeed strange. I have not come across something like that before.

I need to check some things:


[LIST=1]
[*]When you say you can open and edit other files, do you mean from the same location (in Storage > Documents)?
[*]And, do you mean other files with Open Office (such as .odt files), or do you mean files with other programs (such as .txt files)?
[*]Are you sure you are opening the files with Open Office and not, accidentally,  something else? Start Open Office from the menu, then open the  file from the Open Office dialogue (File > Open). If it opens successfully, we need to check  your default open for those files.
[/LIST]

---

### Post by /mr. matt/ on 2011-03-25
> **Paddy Landau said:**
> This is indeed strange. I have not come across something like that before.

I need to check some things:


[LIST=1]
[*]When you say you can open and edit other files, do you mean from the same location (in Storage > Documents)?
[*]And, do you mean other files with Open Office (such as .odt files), or do you mean files with other programs (such as .txt files)?
[*]Are you sure you are opening the files with Open Office and not, accidentally,  something else? Start Open Office from the menu, then open the  file from the Open Office dialogue (File > Open). If it opens successfully, we need to check  your default open for those files.
[/LIST]

1. Yes I can open and edit other files in the same folder. ex. pdf, jpg. I just tried and I can open and edit but not save any files to the drive including these sceenshots. 
2. No all documents that would use openoffice by default do not. The error occurs after openoffice splash screen
3. Yes I am sure it is openoffice. They do not open via File>open

I believe it must be something with writing to the drive, since I can open and edit some files but can write nothing to the drive. As seen in screenshot three, I think the issue is that the drive cannot be written to. In screenshot3 I was simply trying to drag and drop a file on to that partition.

thanks
matt

---

### Post by Paddy Landau on 2011-03-25
Ah ha! We have the problem. Yes, you are right, the file system has been mounted read-only.

Please tell us *exactly* how you mount the file system after you log in.

---

### Post by /mr. matt/ on 2011-03-25
HAHA:popcorn:, Thanks so much. I was using storage device manager to automatically mount the drive upon boot. I opened that and change the settings to "default" and it mounts fine I can write to it now. I guess initially I chose the "assisted" option, which maybe was to advanced for my knowledge base. 

Thanks so much for helping me sort this out so quickly.

Matt

---

### Post by Paddy Landau on 2011-03-26
Excellent news. I'm glad you have it working now. The error by OpenOffice is misleading.

---

