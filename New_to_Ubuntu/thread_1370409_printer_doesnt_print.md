---
title: "printer doesnt print"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by johndingli on 2010-01-02
Hi guys I am using ubuntu 9.10 and installed my printer canon ip1500 the printer is ok it is recognized and drivers installed now when i try to print no errors occur but printer doesn't print any help pls

---

### Post by halitech on 2010-01-02
Do you have the Gutenprint drivers installed? According to Openprinting.org it should work mostly with those drivers.

[http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1500](http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1500)

There are also some other drivers available (listed at the bottom of the page)

---

### Post by johndingli on 2010-01-03
Thanks halitech I tried it but no success or im not doing the right thing as I am new to this and don't want to go back to windows because of this problem

---

### Post by Methuselah on 2010-01-03
[http://localhost:631](http://localhost:631)

Unbder the printers tab, select your printer.
In the maintenance dropdown select print a test page.
Watch out for the printer status. What does it say after a while?

---

### Post by johndingli on 2010-01-03
hi Methuselah the printer status says proccesing printer online then turns to idle printer online and on the link you sent me says job done but nothing prints thanks

---

### Post by Methuselah on 2010-01-03
Can you find your device here?
[http://software.canon-europe.com/](http://software.canon-europe.com/)

---

### Post by johndingli on 2010-01-03
Thanks Methuselah I downloaded the driver from the site you gave me now I have another problem I cant install the driver 22415.tgz file any help im really new here thanks

---

### Post by Methuselah on 2010-01-03
First, be certain you downloaded the linux driver for the right printer for your architecture (ie 64 bit or 32 bit).

Assuming you downloaded the driver to your Downloads folder:

```

cd ~/Downloads
tar -xzvf 22415.tgz

```

should extract it.

After you do this and go into the folder with the driver do you see files with the extension .rpm?

---

### Post by johndingli on 2010-01-03
Dear Methuselah yes i see 4 files with extension.rpm

---

### Post by Methuselah on 2010-01-03
Can you post their names...it is really just for my information and it would allow me to make posts that include them or find out whether all four are needed.

In any case, to use any of them you need to convert to .deb because that is the format Ubuntu uses for installation files.

To do this, install a program called **alien**.

Do
```

sudo apt-get install alien

```
in a terminal.

Then 

```

cd ~/Downloads/folder-with-four-files
alien file1
alien file2
alien file3
alien file4

```

Note that when typing any file/directory names in the terminal you can hit TAB and it will autocomplete as far as the file name is unique.
Of course all my names have to be replaced with the actual names as they are on your hard disk.
The result should be four similar files but with .deb extension instead.

---

### Post by johndingli on 2010-01-03
Sorry again Methuselah but it says you must run in root to convert to deb format can you pls tell me how to run in root thanks

---

### Post by Methuselah on 2010-01-03
OK, I didn't realise admin rights would be needed.

```

cd ~/Downloads/folder-with-four-files
sudo alien file1
sudo alien file2
sudo alien file3
sudo alien file4

```

---

### Post by kingofspades8 on 2010-11-04
I'm having a similar problem in ubuntu 10.10.  I got the drivers set up (canon ip1500 v2.50) and the printer appears to be working, but when I try to print a test page it lingers in the print queue and then becomes completed (even though nothing actually printed).  Any ideas?

---

### Post by kingofspades8 on 2011-06-02
Screw it.  I gave up and got an Epson printer/scanner all in one.  Works great, installed the driver automatically.

---

### Post by rvboutin on 2011-12-08
Hi,
I am sorry to say this... but it is bloddy annoying to see that this problem has been going on for a very long time, that the drivers for the IP1500 are in the database you can choose from on Ubuntu 11.10!!! And still the problem remains!!![-(
I have tried installing the Canon driver using the rpm files and converting them with alien, I have tried the drivers provided with Ubuntu 11.10... nothing work!! The printer is there, the pages go through the spooler... but nothing is ever printed. The Printer keeps flashing...
This printer works fine with Windows XP, so it's not a printer problem.
Any one has an idea what's happening?
Cheers,
Rv

---

