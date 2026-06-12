---
title: "how to create a /dev file associated with a network printer"
date: 2015-07-21
forum: Networking &amp; Wireless
---

### Post by An_Ngo on 2015-07-21
Hi everyone:
I use a POS software that writes directly ESC/POS sequences (raw data) to EPSON receipt printer. 
When I connect the printer directly to my computer using a USB cable, I have a device file associated with the USB port which is /dev/lp0.
I just configure my software to write to that file (/dev/lp0) then everything is fine. 

When I plug my printer to a router, I can register a generic text only printer with CUPS. 
Now, in the POS software, if I give a name of an ordinary file such as receipt.txt so that it will dump the raw ESC sequences into that file, then I can print that file to my printer using 
$ lp receipt.txt -dmy-printer-name
But I cannot find any device file (in /dev/...) associated with that printer! 

In Windows, I have no problem, all I need to do is 
C:>net use LPT1 path-to-printer /persistent:yes
then I configure the software to print to file LPT1  

Is there any way to do that in Ubuntu? 

Thank you very much


P/S: 
Currently, I am trying this 
+ COnfigure the POS software to write the result into a text file receipt.txt 
+ run this process in background
while [ : ] 
do 
  if [ -f receipt.txt ] then 
    mv receipt.txt xxx 
    lp xxx -dmy-printer-name
    rm xxx 
  fi
  sleep 1
done

This works but not very stable.

Any help?

---

