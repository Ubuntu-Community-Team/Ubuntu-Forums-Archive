---
title: "Cannot install correctly Epson L355 wifi printer in notebook with Ubuntu 12.04"
date: 2015-04-13
forum: Networking &amp; Wireless
---

### Post by Guaicuru on 2015-04-13
I am not sure if this question should be asked here. Please let me know if that is the case.

I installed a new Epson L355 (wifi) printer in my home router (I did it from the MS Windows boot of my desktop computer). From my desktop computer after booting in Ubuntu 12.04 I could install it and use it without any problem. Later I tried to install it in a Samsung notebook (with Ubuntu 12.04 also) but I am having problems with it. I started installing (in the notebook) the epson-inkjet-printer-201207w_1.0.0-1lsb3.2_amd64.deb driver and installing the printer in CUPS through localhost:631. I could even print a test page correctly from within CUPS.

Then went to the "Printers" option (now I am using classic gnome) but no printer appears. Only a message with something like "not available printer service" (I am translating). If I write "localhost" in the "Connect" button then I can see the printer (I could also print a test page from here). But the printer does not appear when I want to print from within any application. CUPS is currently installed and running (I checked that). I tried reinstalling CUPS and nothing changed. I also looked at the /var/log/cups/error_log file but I don't understand much what is written there. I am attaching the last part of it.

After more investigation and questions in the askUbuntu forum
I accessed the router and choose a static address for the printer 
outside its DHCP range. Nothing changed.

 Apparently the printing administration of the laptop is
 searching for printers in a fixed IP 192.168.1.36 that
 was configured for a different usb printer in that static 
 address for another PC also with Ubuntu (at that moment
the router was also different). I suspect this may be the
problem because in the top of  the Printers Administration 
window  says "Printing 192.168.1.36") and of course nothing is
 found there.
 When I want to add the new printer (in the laptop) 
I cannot find  any in that IP address. If I press the 
 "Connect" button  and write "localhost" there then 
 the printer is  shown (but I cannot use it from my 
 applications).
 
 Tested in the laptop:
 
 ping 192.168.1.100
 
 worked fine (after a few "Host unreachable" messages).
 
 Tried with nmap:
 nmap 192.168.1.100

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2015-04-13 15:09 ART
Nmap scan report for 192.168.1.100
Host is up (0.0085s latency).
Not shown: 997 closed ports
PORT     STATE SERVICE
80/tcp   open  http
515/tcp  open  printer
9100/tcp open  jetdirect
Nmap done: 1 IP address (1 host up) scanned in 14.57 seconds

I checked if cups was running (because a test in the 
printing administration said that apparently cups was
not running):
 
ps ax | grep cups
 1142 ?        Ss     0:00 /usr/sbin/cupsd -F
 3243 pts/1    S+     0:00 grep --color=auto cups

 Some other tests sugested in 
[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) :
 
/usr/lib/cups/backend/snmp 

network lpd://192.168.1.100:515/PASSTHRU "EPSON L355 Series" "EPSON L355 Series" "MFG:EPSON;CMD:ESCPL2,BDC,D4,D4PX,ESCPR1;MDL:L355 Series;CLS:PRINTER;DES:EPSON L355 Series;CID:EpsonRGB;FID:FXN,DPN,WFA,ETN,AFN,DAN;RID:00;" ""
 
 
Any help would be appreciated.

---

### Post by pdc on 2015-04-15
phew; some days the little grey cells struggle to cope with the demands on them; I have worked through your post but if I start this by saying one seems to need to do 3 things to set up a printer:

1) establish a connection
2) install the drivers
3) register the printer on one's system

________

seems like 1) has been done but one could see what is seen with the command ```
/usr/sbin/lpinfo -v
```     .........which asks lpinfo ..........which linux printing info .........which is in /usr/sbin ..............to give a full printout about what it knows ..........-v stands for verbose ...........

........ with the Epson turned on, can you tell us what the command says please? (ie copy the result from terminal and paste here.........)

____________

2) seems like the correct driver was installed but the command ```
dpkg -l | grep epson-inkjet-printer
``` asks your system which Epson drivers are installed........perhaps you tell us that too please ............

____________

3) Canon and Brother supply an install script in the package they provide; that contains the driver; that install script does 3) for one; 

the format is ```
sudo  /usr/sbin/lpadmin -p [printer_name] -m [PPD_filename] -v [device-uri] -E
``` ........so it telling lpadmin to link and use the printer you specify; to a ppd file you specify for a particular device-uri...........so when one clicks an ADD button in a GUI, it is doing that for you. 

_____________

so it seems to be step 3) where you are having all the issues; tell us if you click on this link [http://localhost:631/printers/](http://localhost:631/printers/) ............what printers are listed; their Queue names; and their Make & Model please 

I think a nice option for adding a printer is to access it from the command ```
system-config-printer
``` which opens a GUI; if you click the ADD button there; there is an option for clicking on network printer; and FIND ............. does that find your Epson ??

---

### Post by Guaicuru on 2015-04-15
Dear pdc, thank you so much for your detailed answer.
Here I am writing the answer to the commands you asked me to run.

The command /usr/sbin/lpinfo -v did not give any of that information 
(the printer was turned on and the ping to the static address worked).
It gave as an answer only a message  like (translated from spanish):
```

lpinfo: There is no route to the «host»
```

The driver test gave
```
dpkg -l | grep epson-inkjet-printer
ii  epson-inkjet-printer-201207w           1.0.0-1lsb3.2                           
EPSON L110/210/300/350/355/550/555 Series - Epson Inkjet Printer Driver
```

> 
tell us if you click on this link [http://localhost:631/printers/](http://localhost:631/printers/) ............what printers are listed

This is what was shown:

L355-Series	L355 Series	Epson Wifi Estudio	Epson L355 Series - epson-inkjet-printer 1.0.0-1lsb3.2 (Seiko Epson Corporation LSB 3.2)	Inactiva

L355-Series-2	EPSON L355 Series	Location Unknown	Epson L355 Series - epson-inkjet-printer 1.0.0-1lsb3.2 (Seiko Epson Corporation LSB 3.2) on 192.168.1.42	Inactiva


I believe one of the printers (the first one) is the EPSON I installed from the laptop accessing   [http://localhost:631/printers/](http://localhost:631/printers/) and the second is the same printer shared from the desktop computer.

> 
I think a nice option for adding a printer is to access it from the command 
```
system-config-printer
``` 
This is the program that gives an error like "Printing service not available. Start the service in this computer or connect it to another server" showing no printers. Moreover at the top of the window says something like "Printing 192.168.1.36". When I click the Connect button and write there "localhost" I can see the two printers listed above.

I hope this can help.

---

### Post by pdc on 2015-04-15
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

have a read at this ............. I just wonder if the > Publish shared printers connected to this server  applies to your case ..............meaning that you change the settings on the computer that can print .............

---

### Post by Guaicuru on 2015-04-15
.

---

### Post by Guaicuru on 2015-04-15
Thank you again for your quick reply.

I checked that configuration in the desktop computer (the one that is working) and the settings were those suggested in the NetworkPrintingWithUbuntu page...

I uninstalled the packages of system-config-printer (completely) using synaptic and reinstalled it again. Still nothing changed. That program keeps saying on the top of the window the message "Printing-192.168.1.34" (translated by me) as if it searching for the printers in that IP number. Is there a way to change that IP number were my system seems to be  searching the printers? In the other computers the same system-config-printer program puts instead a "Printing-localhost" or "Printers-localhost" in the title of that window. What could it be?

---

### Post by Guaicuru on 2015-04-17
Following a suggestion in the thread [Why isn't my CUPS spooler starting?]("http://ubuntuforums.org/showthread.php?t=2174219") I typed and obtained:
```

sudo ps -ae | grep cups
 1162 ?        00:00:00 cupsd

```
So It seems that cupsd is running but cups-browsed is not working in my system.
Does this sends any light to my problem?

---

### Post by chili555 on 2015-04-17
> L355-Series-2 EPSON L355 Series Location Unknown Epson L355 Series - epson-inkjet-printer 1.0.0-1lsb3.2 (Seiko Epson Corporation LSB 3.2) on 192.168.1.[COLOR="#FF0000"]42[/COLOR] Inactiva
However:>  Printers Administration
window says "Printing 192.168.1.[COLOR="#FF0000"]36[/COLOR]") and of course nothing is
found there.Does the printer show up in Connected Devices in the router? At what address?

What have you specified in System Settings > Printers? Here is a sample from my machine.

[ATTACH=CONFIG]261388[/ATTACH]

---

### Post by Guaicuru on 2015-04-17
> **chili555 said:**
> However:Does the printer show up in Connected Devices in the router? At what address?

Thanks for beeing interested in this problem. Now I am not at home so I cannot run any tests or send you detailed information.
Apparently the printer is correctly connected to the router at a fixed staic IP address 192.168.1.100. I suppose that was done correctly since I can print from a desktop computer (also with Ubuntu 12.04) using the wifi.
> What have you specified in System Settings > Printers? Here is a sample from my machine.

I suppose that is the same window I get after running system-config-printer. And there is where I get what I described above: an error message and a sentence on the title of the window saying something like "Printing - 192.168.1.36" or "Printers - 192.168.1.36" (or something like that, I am translating) instead of "Printing - localhost" as I found in other installations. I could send you a picture in a couple of hours when I got home. If in this window I press the "Connect" button and write "localhost" instead of 192.168.1.36 then two printers are shown (the one from the desktop that is shared and the L355 in the wifi network (they are both the same physical printer)). Nevertheless, that does not help since after doing that I cannot use them from any of my applications (no printer appears when I choose to print).

---

### Post by chili555 on 2015-04-17
I believe you can print to the printer *EITHER* as a wifi printer* OR* as a shared printer attached to another computer on the network; but not both. If it were my system, I'd physically detach the printer from the other Ubuntu computer and be entirely wireless.

If the printer shows at the router at x.100, then I'd set both Ubuntu computers to something like: ipp://192.168.1.100:631/lpr/Epson.You might have to play with the settings a bit to stumble on the magic combination.

---

### Post by Guaicuru on 2015-04-17
But the printer is only wireless. It is not connected to the desktop computer. Nevertheless I think that one of the two printers appearing when I change the "Connect" option to localhost (as I just described) is the printer installed in the desktop computer seen from the laptop. I might be wrong.
Do you suggest choosing not to share the printer in both computers? 
Because I could not choose to remove the printer that I think is the one shared by the desktop computer (the one I commented) from the menu I have mentioned in my previous post (running system-config-printer in the laptop).
> If the printer shows at the router at x.100, then I'd set both Ubuntu computers to something like: ipp://192.168.1.100:631/lpr/Epson.You might have to play with the settings a bit to stumble on the magic combination. 
I will give a try to that suggestion and tell you after.

---

### Post by chili555 on 2015-04-17
If you can remove either, I'd do it. Then, I'd select Properties on the other and change to the settings I suggested above.

---

### Post by Guaicuru on 2015-04-18
> **chili555 said:**
> 
If the printer shows at the router at x.100, then I'd set both Ubuntu computers to something like: ipp://192.168.1.100:631/lpr/Epson.You might have to play with the settings a bit to stumble on the magic combination.

Now I have choosen not to share the printer in the desktop computer. Deleted every printer in the laptop. Then I ran the printers configuration program and got the Printers.png window (attached), when I choose connect and then write localhost I could choose to add a new printer.
In that menu when I choose "Network printer" then the window that I called SearchingNetworkPrinter.png (attached) appears, and the default configuration is the one in that screenshot. If I choose that suggested options everything seems ok but no printer appears when I want to print.
I do not know what does 192.168.1.100:515 or PASSTHRU mean.

I also tried putting myself the URI 
ipp://localhost:631/printers/EPSON9F84FB
(EPSON9F84FB is the name of the printer when I printed the network information from the printer) 
or 
ipp://192.168.1.100:631/printers/EPSON_EPSON_L355_Series
or 
ipp://192.168.1.100:631/lpr/EPSON_L355_Series
or variations/combinations but still is not working.

I'll keep trying.
Any help would be appreciated.

---

### Post by chili555 on 2015-04-18
I think you want to set up the printer in Network Printer here.

[ATTACH=CONFIG]261397[/ATTACH]

---

### Post by Guaicuru on 2015-04-18
I tried that and obtained an "Error in the cups server" at the end of the process.

---

### Post by chili555 on 2015-04-18
> **Guaicuru said:**
> I tried that and obtained an "Error in the cups server" at the end of the process.When you open, in Firefox:```
127.0.0.1:631
```And select Administration > Manage Printers, are there any shown? If so, I suggest you remove them all and start anew.

---

### Post by Guaicuru on 2015-04-19
When I go to Administration>Manage printers and found just one:

EPSON_EPSON_L355_Series	EPSON EPSON L355 Series		Remote Printer	Inactiva

since I removed all the ones I found before and installed this one.
I'll do it again.
Should I try to install it from the first time starting in 127.0.0.1:631 or using system-config-printer?

---

### Post by chili555 on 2015-04-19
I suggest *system-config-printer* after you have removed every trace of printers everywhere you see one!!!

---

### Post by Guaicuru on 2015-04-20
It finally works!
I found what I think could had be the reason of my troubles. There was an inocent file  /etc/cups/client.conf with the single line in it: ServerName 192.168.1.36. I was probably left after a previous attempt to print to another printer. Apparently after uninstalling completely cups that file was not erased (I thounght everything was erased). I commented that line and started again.
Then after restarting cups I ran system-config-printer again and choose the options that the program offered me by default. So at the end I did not use the ipp option (I could not find the correct path to make it print). I do not know if it is safe or good but the option suggested in the URI address was:

dnssd://EPSON%20L355%20Series._pdl-datastream._tcp.local/

and that works perfectly until now. 
Thank you chili555 for your patience, quick replies and endurance along this process.

---

### Post by chili555 on 2015-04-20
Awesome! Glad it's working!

---

### Post by pdc on 2015-04-20
Hi there Guaicara; well done

if you are still there ..!!

can you run the command ```
/usr/sbin/lpinfo -v
``` and I hope it will show the result > dnssd://EPSON%20L355%20Series._pdl-datastream._tcp.local/

____________________

the command line way to register a printer is 

```
sudo  /usr/sbin/lpadmin -p [printer_name] -m [PPD_filename] -v [device-uri] -E
``` so your device-uri would > dnssd://EPSON%20L355%20Series._pdl-datastream._tcp.local/

and system-config-printer would be doing this: sudo  /usr/sbin/lpadmin -p EpsonL355 -m epson-inkjet-printer-201207w.ppd -v dnssd://EPSON%20L355%20Series._pdl-datastream._tcp.local/ -E

__________________-

as you own the thread, you can edit THREAD TOOLS to say **[SIZE=4]SOLVED [/SIZE]**

---

### Post by Guaicuru on 2015-04-20
Thank  you pdc. I will run that test.
One question for you: do I have to run the code "sudo ..." you mentioned even if I installed the printer using system-config-printer?

---

### Post by pdc on 2015-04-20
no; you shouldn't need sudo: the command is asking lpinfo (linux printing info) to list (ls) and do it fully ie verbose so one uses the -v for that

anyone should be able to find what printers their computer recognises as connected; from that command

---

### Post by Guaicuru on 2015-04-22
I had a problem with me router-modem and lost the internet service for some days. I even had to reinstall the printer and the URI is now a bit different: lpd://192.168.1.100:515/PASSTHRU. 
Now I'm back and I ran the command you suggested ```
 /usr/sbin/lpinfo -v
``` 
and obtained 
```
network dnssd://EPSON%20L355%20Series._pdl-datastream._tcp.local/
network dnssd://EPSON%20L355%20Series._printer._tcp.local/

```
The first line of output coincides with what you said it was expected and I suppose the second one is also fine.
Thanks for the advice.

---

