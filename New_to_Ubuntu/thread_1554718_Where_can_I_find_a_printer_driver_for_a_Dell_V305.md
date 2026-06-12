---
title: "Where can I find a printer driver for a Dell V305?"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by bwallum on 2010-08-17
Hi

I'm setting up a printer on Lucid 10.4. I can't find a printer driver.

How do I install a Dell V305?

---

### Post by jonnywombat on 2010-08-17
According to [openprinting.org]("http://www.openprinting.org/printers/manufacturer/Dell") your printer is not supported.

---

### Post by nongeek2010 on 2010-09-09
Why is this printer not supported, my computer is from dell should be driver for the printer should I contact dell support?

---

### Post by halitech on 2010-09-09
Dell doesn't actually make printers, they buy printers from Lexmark and rebrand them as Dells. Lexmark would almost be considered the anti-linux of all computer hardware providers.

---

### Post by nongeek2010 on 2010-09-09
Thank you for that information it is very helpful will look for a printer that Ubuntu 10.04 Supports.

---

### Post by the-edmeister on 2010-09-09
Take a look at Brother printers. They seem to have Linux drivers for every printer they have made in the last few years.

---

### Post by Jazzy_Jeff on 2010-09-09
I would recommend HP, Brother and Samsung. They seem to have decent support. Make sure you check before you buy one that it will work. I personally only use HP printers and scanners now.

---

### Post by anglican on 2010-09-10
> **bwallum said:**
> Hi

I'm setting up a printer on Lucid 10.4. I can't find a printer driver.

How do I install a Dell V305?Have you tried the equivalent Lexmark printer driver? This printer looks to be just an x4650 (all Dell printers are re-badged Lexmarks)... so the Linux driver for the x4650 might work (you can download it from Lexmark's site).

H

---

### Post by fallenshadow on 2010-09-10
Yes I think this might work. Download the Lexmark driver for x4650 which looks like re-branded Dell v305.

The link to download the driver is here:

[http://support.lexmark.com/index?page=downloadFile&actp=RECOMMEND&productCode=LEXMARK_X4650&id=DR20523&segment=DOWNLOAD&actp=PRODUCT&userlocale=EN_US&locale=en](http://support.lexmark.com/index?page=downloadFile&actp=RECOMMEND&productCode=LEXMARK_X4650&id=DR20523&segment=DOWNLOAD&actp=PRODUCT&userlocale=EN_US&locale=en)

---

### Post by bpicmc on 2010-12-04
> **fallenshadow said:**
> Yes I think this might work. Download the Lexmark driver for x4650 which looks like re-branded Dell v305.

The link to download the driver is here:

[http://support.lexmark.com/index?page=downloadFile&actp=RECOMMEND&productCode=LEXMARK_X4650&id=DR20523&segment=DOWNLOAD&actp=PRODUCT&userlocale=EN_US&locale=en](http://support.lexmark.com/index?page=downloadFile&actp=RECOMMEND&productCode=LEXMARK_X4650&id=DR20523&segment=DOWNLOAD&actp=PRODUCT&userlocale=EN_US&locale=en)

I just tired this was not able to get it to work. The installer does not recognize the printer when it tries to make a print queue so it gives an error message and closes. If anyone can get this method to work let me know.

---

### Post by anglican on 2010-12-06
> **bpicmc said:**
> I just tired this was not able to get it to work. The installer does not recognize the printer when it tries to make a print queue so it gives an error message and closes. If anyone can get this method to work let me know.Well it seems to install the driver OK - just not recognise your printer. Try adding the printer manually by selecting the ppd file yourself - it is at:

/usr/share/cups/model/Lexmark/lx36-46.ppd

Report back if you need more specific instructions on how to do this (it should be fairly obvious when you run through adding a printer).

H

---

### Post by bpicmc on 2010-12-12
> **anglican said:**
> Well it seems to install the driver OK - just not recognise your printer. Try adding the printer manually by selecting the ppd file yourself - it is at:

/usr/share/cups/model/Lexmark/lx36-46.ppd

Report back if you need more specific instructions on how to do this (it should be fairly obvious when you run through adding a printer).

H

Well, I tried to add it manually but it did not work. When I tried to do a test print, the printer did nothing and I got an error message. I think the Dell V305 is a paperweight, at least for now.

---

### Post by JIMJAM1 on 2011-01-15
I was able to get the Dell v305 working with Ubuntu with a bit of a hack. Seems to be OK so far. Slightly vague description follows because I'm writing this from memory and don't have the exact file names to hand.

Installed the Lexmark driver and selected the correct ppd file, as already described in the thread.

Then do lsusb to list the devices connected to the system and note the vendor ID and product ID listed for the printer (the product id is 0x5305 I think).

Then go into /usr/lexinkjet/
cd into the relevant directory for the driver you installed and cd into the etc subdirectory

There are two files which you need to edit using sudo gedit

These are called lxdn.conf and the file which is called 99-lexmark-?????.rules

You need to edit the lexmark vendor Id and product id values to be the correct one to match the dell. This should mean two hex values change in each of the files. In the rules file, you only need to edit any one of the lines.

Then try printing a test page and hope for the best.

If anyone needs more detailed instructions, let me know.

---

### Post by JIMJAM1 on 2011-01-15
I was able to get the Dell v305 working with Ubuntu with a bit of a hack. Seems to be OK so far. Slightly vague description follows because I'm writing this from memory and don't have the exact file names to hand.

Installed the Lexmark driver and selected the correct ppd file, as already described in the thread.

Then do lsusb to list the devices connected to the system and note the vendor ID and product ID listed for the printer (the product id is 0x5305 I think).

Then go into /usr/lexinkjet/
cd into the relevant directory for the driver you installed and cd into the etc subdirectory

There are two files which you need to edit using sudo gedit

These are called lxdn.conf and the file which is called 99-lexmark-?????.rules

You need to edit the lexmark vendor Id and product id values to be the correct one to match the dell. This should mean two hex values change in each of the files. In the rules file, you only need to edit any one of the lines.

Then try printing a test page and hope for the best.

If anyone needs more detailed instructions, let me know.

---

### Post by JIMJAM1 on 2011-01-15
I was able to get the Dell v305 working with Ubuntu with a bit of a hack. Seems to be OK so far. Slightly vague description follows because I'm writing this from memory and don't have the exact file names to hand.

Installed the Lexmark driver and selected the correct ppd file, as already described in the thread.

Then do lsusb to list the devices connected to the system and note the vendor ID and product ID listed for the printer (the product id is 0x5305 I think).

Then go into /usr/lexinkjet/
cd into the relevant directory for the driver you installed and cd into the etc subdirectory

There are two files which you need to edit using sudo gedit

These are called lxdn.conf and the file which is called 99-lexmark-?????.rules

You need to edit the lexmark vendor Id and product id values to be the correct one to match the dell. This should mean two hex values change in each of the files. In the rules file, you only need to edit any one of the lines.

Then try printing a test page and hope for the best.

If anyone needs more detailed instructions, let me know.

---

### Post by JIMJAM1 on 2011-01-15
I was able to get the Dell v305 working with Ubuntu with a bit of a hack. Seems to be OK so far. Slightly vague description follows because I'm writing this from memory and don't have the exact file names to hand.

Installed the Lexmark driver and selected the correct ppd file, as already described in the thread.

Then do lsusb to list the devices connected to the system and note the vendor ID and product ID listed for the printer (the product id is 0x5305 I think).

Then go into /usr/lexinkjet/
cd into the relevant directory for the driver you installed and cd into the etc subdirectory

There are two files which you need to edit using sudo gedit

These are called lxdn.conf and the file which is called 99-lexmark-?????.rules

You need to edit the lexmark vendor Id and product id values to be the correct one to match the dell. This should mean two hex values change in each of the files. In the rules file, you only need to edit any one of the lines.

Then try printing a test page and hope for the best.

If anyone needs more detailed instructions, let me know.

---

### Post by JIMJAM1 on 2011-01-15
I was able to get the Dell v305 working with Ubuntu with a bit of a hack. Seems to be OK so far. Slightly vague description follows because I'm writing this from memory and don't have the exact file names to hand.

Installed the Lexmark driver and selected the correct ppd file, as already described in the thread.

Then do lsusb to list the devices connected to the system and note the vendor ID and product ID listed for the printer (the product id is 0x5305 I think).

Then go into /usr/lexinkjet/
cd into the relevant directory for the driver you installed and cd into the etc subdirectory

There are two files which you need to edit using sudo gedit

These are called lxdn.conf and the file which is called 99-lexmark-?????.rules

You need to edit the lexmark vendor Id and product id values to be the correct one to match the dell. This should mean two hex values change in each of the files. In the rules file, you only need to edit any one of the lines.

Then try printing a test page and hope for the best.

If anyone needs more detailed instructions, let me know.

---

### Post by frozenchia on 2011-01-27
Thank you, the above worked with a little fiddling.  I was beginning to think I was getting tired of having to switch to windows to print every little thing around the house. You guys are lifesavers.

P.S. dont know if its a direct correlation but mine didnt work after the steps above until i unplugged and replugged the usb.

---

### Post by dudeomagic on 2011-02-16
> **JIMJAM1 said:**
> I was able to get the Dell v305 working with Ubuntu with a bit of a hack. Seems to be OK so far. Slightly vague description follows because I'm writing this from memory and don't have the exact file names to hand.

Installed the Lexmark driver and selected the correct ppd file, as already described in the thread.

Then do lsusb to list the devices connected to the system and note the vendor ID and product ID listed for the printer (the product id is 0x5305 I think).

Then go into /usr/lexinkjet/
cd into the relevant directory for the driver you installed and cd into the etc subdirectory

There are two files which you need to edit using sudo gedit

These are called lxdn.conf and the file which is called 99-lexmark-?????.rules

You need to edit the lexmark vendor Id and product id values to be the correct one to match the dell. This should mean two hex values change in each of the files. In the rules file, you only need to edit any one of the lines.

Then try printing a test page and hope for the best.

If anyone needs more detailed instructions, let me know.

Hello, my wife's brother installed ubuntu on our crappy old computer and we have a v305 printer. ubuntu works great, but the printer doesn't, at all.  after reading this forum i am a little relieved, but can you break down the steps for me a little more since i have no idea what most of what you wrote means? i'm about to beat my brother in law since he did this and can't/won't/doesn't want to help figure out how to make the printer work. I appreciate any help you can give. Thanks in advance.

---

### Post by Chronon on 2011-02-16
You should mention what's not clear to you.  Otherwise people will just be paraphrasing the same steps again.

---

### Post by anglican on 2011-02-17
> **dudeomagic said:**
> Hello, my wife's brother installed ubuntu on our crappy old computer and we have a v305 printer. ubuntu works great, but the printer doesn't, at all.  after reading this forum i am a little relieved, but can you break down the steps for me a little more since i have no idea what most of what you wrote means? i'm about to beat my brother in law since he did this and can't/won't/doesn't want to help figure out how to make the printer work. I appreciate any help you can give. Thanks in advance.First open a terminal, there are many ways to do this, I usually right-click on the "Home" icon on my desktop and choose "Open Terminal Here". Then in that terminal type:
```
wget http://downloads.lexmark.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
```
then:
```
tar xvfz lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
sudo ./lexmark-08z-series-driver-1.0-1.i386.deb.sh
```
this will have installed the driver but may have failed to find your printer - this doesn't matter. You then need to install your printer from the Applications menu (on my system it is under System->Printing). At the appropriate point you will need to browse to the ppd file /usr/share/cups/model/Lexmark/lx36-46.ppd. This should be obvious but report back here if you have problems with this step. What follows is the instructions of JIMJAM1 which I can't verify, in the terminal run:
```
sudo lsusb
```which will show the vendor/product ID for your printer, JIMJAM1 reports that the product ID is 0x5305. Then:
```
cd /usr/local/lexmark/08zero/etc
```
you are going to need to edit two files in this directory lxdn.conf and 99-lexmark-08z.rules) changing the vendor/product ID to the one reported by the lsusb command above. To edit the files use ```
sudo gedit lxdm.conf
``` and```
 sudo gedit 99-lexmark-08z.rules
```you need to edit one line only in this second file. Good luck, please report back success/failure. frozenchia reports that you may need to uplug/re-plug your printer after doing all the above.

H

---

### Post by flux=rad on 2011-02-20
> **frozenchia said:**
> Thank you, the above worked with a little fiddling.  I was beginning to think I was getting tired of having to switch to windows to print every little thing around the house. You guys are lifesavers.

P.S. dont know if its a direct correlation but mine didnt work after the steps above until i unplugged and replugged the usb.

I'm glad I found this little thread, I want to destroy this printer but don't want to buy another yet so I'm trying to deal with it. I followed the steps laid out by Chronon but the test page will not print and I receive an error message. I was wondering what you meant Frozenchia by "a little fiddling." I am new to Ubuntu but really want to learn my way around because I like it better than Windows so far.

---

### Post by frotzed on 2011-02-20
> **the-edmeister said:**
> Take a look at Brother printers. They seem to have Linux drivers for every printer they have made in the last few years.

+1 for Brother printers.  I like them because the printer itself does most of the processing (I have a feeling this also results in better compatibility between OS's).

---

### Post by Chronon on 2011-02-20
> **flux=rad said:**
> I'm glad I found this little thread, I want to destroy this printer but don't want to buy another yet so I'm trying to deal with it. I followed the steps laid out by Chronon but the test page will not print and I receive an error message. I was wondering what you meant Frozenchia by "a little fiddling." I am new to Ubuntu but really want to learn my way around because I like it better than Windows so far.
I didn't actually post any instructions.  I just suggested that being specific about what problems are encountered will generally lead to better advice.

You did replace the vendor and product IDs (in both mentioned files) to match your printer and unplugged then replugged your printer?  What specific error message do you get?  Is this the test page that you can print by adding a new printer at System > Administration > Printing?

---

### Post by flux=rad on 2011-02-20
Sorry I meant Anglican's instructions. The error message says "there was a problem processing the document." I edited both files (the .conf and the .root) with vendor and product ID 413c and 5305. However, in addition to those ID's there are "BASE_PRINTER_ID" and "FAMILY_ID" in lxdm.conf., and in the driver file itself there are vendor and product ID's.

---

### Post by ame82 on 2011-03-12
hi guys 
i am also trying to get my dell printer working here , i have ubuntu 10.10 , and the good thing , although i never setup any network , but when i open network i find it listed there as its wireless ,dont know if that could be usfull to install it??
also what the new value for the id and vender names we should edit in the config file after installing lixmark driver
i am new and i am trying to know my ways arround as i prefere linux and wanna do my best to replace windows permanently with linux

---

### Post by cepal on 2011-04-13
I've followed the Lexmark steps here and none worked well. When I changed the two files with the codes, it's still complaining for following error:

A wrong printer is detected. Any printjobs are canceled.

I am sure I used correct codes (VendorID and PrinterID) for the two files. What else could be wrong? CUPS debug log doesn't tell anything useful.

Also, anyone experienced in using the SCANNER? As that's actually what I need at the moment...

Thanks...

---

### Post by tang0delta on 2011-07-02
Although this is an old thread, I though I'd post to say I found the info posted here invaluable in getting my V305 to work (Ubuntu 11.04). Just a note to anyone who comes across this in future and has trouble (as I did):

Rather than editing lxdm.conf, as suggested, I had to edit lxdx.conf, which looks the exact same and requires the same changes. I found this out by looking at the lx36-46 PPD file and seeing the following lines near the top of the file:

*ModelPrefix: "lxdx"
*HPEPrefix: "lxdx"

Maybe these values differ between lxdm and lxdx for different versions of the lexmark driver. Best to check them and ensure you're editing the correct lxd?.conf file.

Anyway, hope this helps anyone who is still trying to get this to work ;)

---

### Post by flux=rad on 2011-07-31
well I finally got the V305 to work with ubuntu 10.10, following tang0delta's suggestion. Too bad there is only a printer driver and not a scanner driver too, so much for all-in-one.

---

### Post by kevib04s on 2011-09-16
This was very helpful in getting my printer to work, had to edit the lxdx as well but now its running fine on  v11.04. Thank you

---

### Post by guidoune on 2011-10-02
Thank you guys for this wonderful thread, i finally got it working by modifying the lxdx.conf file.

---

### Post by gabidospi on 2012-04-12
Hi all, I follow the steps indicated on this tuto, but for me the printer still not works. When I try to print something, the printer wake up, but after a few seconds on the Printer plasmoide the print task passing on "halt" and nothing is printing (the printer turn off either).

I modifying both files lxdx and lxdm. Any tips?

---

### Post by humanracer on 2012-08-07
Hi

Cannot get this to work. I amended the files (pid and vid to 413c and 0x5305 and one line in other file) however it still not working as it says "cannot communicate" with printer. I suspect it is because I am using Ubuntu 11.10 and maybe the support for the printer was for an earlier version. Any ideas?

---

### Post by litz on 2012-12-27
Dear all!
Thank you for this wonderful thread. Everything really worked fine until I upgraded to Ubuntu 12.04 TLS which I am still running on. 
Although I used the same routine as for previous versions, printing was not possible any more. Does anyone have any suggestion for that? (for printing I now have to change to an awfully slow and un-ubuntu-like Wondows Vista)
Thank you in advance,
Happy holidays
Regards
Stefan

---

