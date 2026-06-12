---
title: "Can't install printer"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2011-01-06
Was running 9.04 and had my Samsung SCX4826FN MFD working perfectly. 

Replaced that computer with a new 64 bit Intel computer, and upgraded to 10.04, but cannot install the MFD. When I tried to print, I got a message saying,

> There is a missing print filter for printer 'Samsung-SCX-4x26-Series'

I tried reinstalling and in this new configuration, trying to print a test page, a page prints out saying,

> %You are using the wrong driver for your printer
0 setgray
initclip newpath clippath gsave stroke grestore pathbox
exch pop exch pop exch 9 add exch 9 sub moveto
/Courier findfont 12 scalefont setfont
0 -12 rmoveto gsave product show grestore
0 -12 rmoveto gsave version show ( ) show revision 20 string cvs   show grestore
0 -12 rmoveto gsave serialnumber 20 string cvs show grestore
showpage

Yet a third attempt prints a series of faint straight lines over several pages.

Tried upgrading the older computer and installing the printer on it due to urgent printing needs, but no cigar there either.

AAt this Samsung support page 

[Samsung](http://www.samsung.com/us/support/downloads/SCX-4826FN/XAA)

there is a 32 MB unified driver download and these instructions:

> [Unified Linux Driver Install Guide] 

1. Make sure that you connect your machine to your computer. 
Turn both the computer and the machine on. 

2. When the Administrator Login window appears, type in root in the Login field 
and enter the system password. 

3. Download and extract the driver 
[root@localhost root]#tar xzf [Downloaded File Name(XXXX.tar.gz)] 

4. The driver will be extracted as ''cdroot'' folder in current path. 

5. Execute installation program. 
[root@localhost root]#./cdroot/autorun 

6. When the welcome screen appears, click ''Next'' and proceed installation. 


[Ubuntu OS Installation]

1. Download and extract the driver 

2. Open ''Root Terminal'' 

3. Execute installation program. 

$ sudo cdroot/autorun

4. After install, PPD path is set again.

$ sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/custom/samsung

5. Execute Configurator, and Add your printer model name by Add Printer

I have attempted to follow the above, but there are lots of choices to be made during the install process and I have no idea if I am entering the right choices. Samsung support says they don't support linux and wash their hands of it.

Can anyone help me with this, please? I badly need to print out some things. TIA.

---

### Post by Odyssey1942 on 2011-01-06
Found this:

[http://ubuntuforums.org/showthread.php?t=341621]("http://ubuntuforums.org/showthread.php?t=341621")

Problem solved. Thanks.

---

