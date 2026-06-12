---
title: "Two network printing problems..."
date: 2014-11-11
forum: Networking &amp; Wireless
---

### Post by l-taylor-123 on 2014-11-11
Hi all, new here!!!

I have searched around and found a few answers to my questions, but none of them have helped me sort two problems out...

The first problem is:

I have samba running a file and print server. File server is working well on Ubuntu and windows machines. The print server using cups is being a bit more difficult. I have two printers plugged into my server via USB cables. One is an epson scanner/ink jet job and the other is a samsung monochrome laser. On the windows machine the epson printer works fine, but the samsung one prints junk rather than what I have told it. 

Now, I suspec the problem may be drivers. The epson printer plug'd and play'd perfectly, but the samsung printer was not recognised. I downloaded a linux driver for the printer and installed it and got it working perfectly when printing from the server. However, when I try and print from the windows machine it does just prints what looks like an sertup file dump and that is it. I tried the origional print driver which came with it, a new windows print driver and a generic samsung driver with the same results. 

Any ideas on how I might be able to resolve this.


The second problem is:

When trying to use the printers from another Ubuntu machine, the print job get  stuck in the queue needing authentication. If I try to authenticate it, it doesn't work. I have tried editing the cups config files to allow all users to print, but with no luck. It is like the cups server is using a different login/password to the samba account.

Any idea?


Thank you in advance for any help you might be able to offer. I really appreciate it.

Lewis

---

### Post by l-taylor-123 on 2014-11-18
Bump for any help please - I still have not managed to get to the bottom of either of my two issues. Thanks

---

### Post by SeijiSensei on 2014-11-18
For problem one, you might try printing with [Adobe's Universal Postscript driver]("http://www.adobe.com/support/downloads/thankyou.jsp?ftpID=1500&fileID=1438").  CUPS likes Postscript.  I used to use the Color Postscript driver for Apple Laserwriters, but it's not shipped with Windows any more.

You may encounter a few problems while installing the driver.  Windows gave me the opportunity to rerun the installer after it failed the first time, and I could then complete the installation.  This is on 32-bit Win7.

---

### Post by l-taylor-123 on 2014-11-18
Thanks for the advice - I have tried to re-install, but it tries to use the samsung driver I installed. I have tried to delete it using synaptic package manager, but it still defaults to this driver and doesn't allow me to try to use a different driver. Any tips for that?

---

### Post by SeijiSensei on 2014-11-18
You don't want to remove the Samsung driver from the Linux box.  You want to add the Postscript driver to the Windows clients.  Then Windows will send Postscript to the CUPS on the Linux box, which it will translate with the Samsung driver.

---

### Post by l-taylor-123 on 2014-11-18
Ah, got you. Thanks. I will try that tomorrow. Appreciate the advice.

Thanks

Lewis

---

### Post by l-taylor-123 on 2014-11-19
[SIZE=3][FONT=arial][SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") - thanks for your help. I managed to install a generic printer driver (not the adobe one as the installer would not navigate through the server to the printer in question). I did find a generic postscript MS print driver and that has done the trick. So thanks again.

Now I just need to get my Ubuntu machine to authenticate and I am golden![/FONT][/SIZE]

---

