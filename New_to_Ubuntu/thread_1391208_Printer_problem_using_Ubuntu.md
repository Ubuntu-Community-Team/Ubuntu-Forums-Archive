---
title: "Printer problem using Ubuntu"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by Diane Rooney on 2010-01-26
I'm new to Ubuntu and everything works fine except for my Brother MFC440-CN printer and the problem is that now it will only print on full resolution, which is very wasteful when all I need most of the time are draft copies. Has anybody else had this fault and if so, how did they resolve it? Thanks.

---

### Post by hhlp on 2010-01-26
the full instruccion start here :

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-440CN]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-440CN")

---

### Post by Diane Rooney on 2010-01-26
Have already downloaded the drivers from the Brother solutions page, but still have the problem. The printer works fine under Windows. Guess I´ll have to try something else. Thanks, anyway.

---

### Post by hhlp on 2010-01-26
Step 1. Download a driver.
    Download LPR driver.
    
Step 4. Install the driver
    4-1. Turn on the printer and connect the usb, network or parallel cable.
    4-2. Go to the directory where the driver is.
    4-3. Install LPR driver

        Command (for dpkg)  :  dpkg  -i  --force-all  (lpr-drivername)

    4-5. Check if the LPR driver is installed

        Command (for dpkg)  :  dpkg  -l  |  grep  Brother

Step 5. Confirm/Configure a file according to your connection
    5-1. Check the configuration filename for your distribution.

      # Example: /etc/printcap

    5-2. Edit the file according to your connection

      # For USB Connection (Default)
        Check if the parameter of ":lp" is ":lp=/dev/usb/lp0"
        Exapmle 

    5-3. Restart the print system

        Command  (for  lpr):  /etc/init.d/lpr  restart
        Command  (for  lprng)  :  /etc/init.d/lprng  restart

---

### Post by veggiefish on 2010-03-09
I tried your steps and went ok except:

--( will@lucky )--( /etc )-- :)
--$ sudo /etc/init.d/lpr restart
sudo: /etc/init.d/lpr: command not found
--( will@lucky )--( /etc )-- :(
--$ sudo /etc/init.d/lprng restart
sudo: /etc/init.d/lprng: command not found

---

### Post by veggiefish on 2010-03-09
I managed to get it working as the service on my OS was not lpr but lpd

so

/etc/init.d/lpd restart

However this all broke synaptic. I had to remove the brother common wrapper and reinstall as above, but it worked for printing. Scanning however...

---

### Post by veggiefish on 2010-03-09
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html)

And then just be sure to run gimp as sudo

sudo gimp

then "open " file using XSane to scan.

---

