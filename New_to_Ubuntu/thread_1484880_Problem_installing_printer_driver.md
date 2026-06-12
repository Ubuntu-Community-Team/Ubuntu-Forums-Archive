---
title: "Problem installing printer driver"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by Newbie2910 on 2010-05-16
How do you "install" a printer driver?

I found the linux driver for my Canon Pixma 330.  I downloaded it and it's sitting in my documents folder:

cnijfilter-mx330series-3.10-1-i386-deb.tar.gz

If I double-click on it, I see it contains a deb file and inside it are two items:

a Package folder and a script (I think it is) "install.sh"

Now, I opened the install.sh in the editor and copied the text to the clipboard, then opened Terminal and pasted it.  Was that the right thing to do?  

The system still won't find the printer.  When I originally installed Ubuntu, it found it but had no driver for it.  I now have choices (in the "add printer" dialog of just "Other" or "network printer".

Ok so what (probably many things) have I done wrong?

On the plus side I am really loving Ubuntu... very stable at this point and I like the way things are thought out.

---

### Post by marshmallow1304 on 2010-05-16
To install the driver, extract the .tar.gz archive (right-click, "Extract Here") then double-click the .deb in the extracted folder.

---

### Post by Newbie2910 on 2010-05-16
Ok, got it to recognize the printer but can't get anything out.  I installed the driver, and now when I print I get the printer selection box (Print to file, then after a few seconds my printer shows up as a choice).  

So I print to it, and I have it's print queue open so I can see it.  It shows the document I sent, (as pending) and the printer makes a few noises and moves stuff around inside, but nothing actually prints.

---

### Post by daviescr on 2010-09-06
A little late but for what its worth here is a little more detailed instructions:
[LIST]
[*]download the package and double click on it. Mine opened up with file roller
[*]select the folder and press extract from file roller
[*]double click the install.sh and it will give you a popup couple choices. I selected run in terminal
[*] now select system --> administration --> Printing
[*] press "add printer" and find **mx330** in the **canon** list

[/LIST]

That was what worked for me.

---

