---
title: "How to Install Brother HL2040 as a network printer in Hardy?"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by lardandweed on 2008-09-22
Hi all. Problem as per title. Been trying to get my printer to work the whole of today ... to no avail. Been looking around at various solutions but i couldn't find one with the same setup, i.e. Brother HL2040 + Hardy Heron + network printer

my printer is connected via the router's printer port

Could anyone provide some _thorough_ instructions or post a link to one? I say thorough 'cause i've tinkered with so many settings/commands i probably should wipe all settings clean and start from scratch. lol. sorry newb here. just migrated from windoze ;)

regards,
lardandweed

PS: i realised i might have posted this in the wrong section? Perhaps this should go under "Hardware & Laptops"? Could someone help me move this to the appropriate section?

---

### Post by lardandweed on 2008-09-27
bump

---

### Post by Aearenda on 2008-09-27
I'm not clear what you're trying to achieve.

Is it...
1. You have a HL2040 attached to your Hardy box, and you want other computers (Windows, or Ubuntu etc?) to be able to use it?

2. You have a HL2040 attached to another box (running Windows?), and you want to print to it remotely from a Hardy box?

3. Something else?

---

### Post by lardandweed on 2008-09-28
Nope. option 3) my printer is connected via the router's printer port

---

### Post by Aearenda on 2008-09-28
Oh yes, I see you did say that in your first post... must have been asleep at the wheel.

Ok, so I'm *guessing* that your router is designed to support Windows systems, and presents itself as a Windows shared printer. It probably uses Linux and Samba internally. On the other hand, it may present as a JetDirect or similar device. It would be helpful to know the make and model of the router, and how the instructions tell you to connect the printer to Windows. Also, you haven't told us what you have tried already - I'm assuming you've deleted any non-working printer settings previously tried.

I would suggest that you first connect the printer directly to your Ubuntu system while we get the Brother drivers sorted out. This is because the driver is not supplied as part of Ubuntu, but is instead downloaded from Brother's web site. Alternatively, it might work at 600 dpi using the HL2060 driver, according to some pages I have seen (see [http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2040](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2040)). You might like to try that first! It should be fairly straightforward going through the new printer wizard in System->Administration->Printing.

Caveat: I don't have a HL2040. This may not work - I'm just trying to help you understand what Brother are saying at this point. It looks like the printer is rather like the HL5040, which I *do* have, but which is included in Ubuntu; what I say below assumes there is a correlation between these two as far as network setup is concerned.

Assuming you want to install the Brother HL2040 drivers, the first thing to do is to carefully follow the instructions at [http://solutions.brother.com/linux/en_us/instruction_prn1a.html](http://solutions.brother.com/linux/en_us/instruction_prn1a.html). My notes on reading this through:

1. On Ubuntu, you need the .deb downloads, not .rpm ones, and you use the dpkg commands preceded by 'sudo ' as suggested in Step 1. 

2. Note the pre-requisite for Ubuntu 8.04 - you have to do this first: ```
sudo mkdir /usr/share/cups/model
```

3.It looks to me that in Step 3 the lpr driver you need is the one from [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/brhl2040lpr-2.0.1-1.i386.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/brhl2040lpr-2.0.1-1.i386.deb&lang=English_lpr), and the CUPS driver is from [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperHL2040-2.0.1-2.i386.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperHL2040-2.0.1-2.i386.deb&lang=English_gpl). The installation commands will be ```
sudo dpkg -i --force-all --force-architecture brhl2040lpr-2.0.1-1.i386.deb
```and```
sudo dpkg -i --force-all --force-architecture cupswrapperHL2040-2.0.1-2.i386.deb
```

4. The Brother instructions use the 'localhost:631' CUPS web page to add the printer - you may prefer to use System->Administration->Printing to add the local printer.

Once it is working locally, and only then, we need to plug it back in to the router and make it work remotely - rashly assuming it looks and works like a Windows shared printer, here's how to proceed on Ubuntu:

1. Go to System->Administration->Printing and delete the local printer we used for testing.
2. Click 'New Printer'
3. Click 'Windows printer via SAMBA'
4. On the right, click 'Browse'
5. Find the printer in the browse box that appears and click 'OK'
6. Click the 'Verify' button - if the printer is shown as accessible, proceed, otherwise check 'authentication required', fill in a username and password and try again.
7. Click 'Forward' and wait for the drivers to be listed.
8. Click 'Brother' and then 'Forward'.
9. Choose 'HL2040' (or whatever it calls itself) from the list on the left, and click 'Forward'.
10. Name it how you wish, and optionally fill in the other fields; then click 'Apply'.

That should be it - try a test print! 

Please let us know what you decide to do and how you get on.

---

