---
title: "Have set up network printer in Ubuntu 12.04 but can't print test page"
date: 2014-02-27
forum: Networking &amp; Wireless
---

### Post by davidjohnston31 on 2014-02-27
I have Win 8 and Ubuntu 12.04 dual booting on Lenovo ideapad Z500.  I've set up my network printer (Canon MP970) in Ubuntu (it works perfectly in Win 8) and although it's there, Canon PIXMA MP970 - CUPS+Gutenprint v5.2.8-pre1, cnijnet:/00-00-85-CC-D8-A4, I haven't succeeded in printing a test page... "Idle - Printing page 1, 5%" The computer connects to a wireless router that is on a private home network.  The printer has a static IP address 192.168.1.32, otherwise the network is DCHP.  I haven't been able to apply this IP address anywhere.  I'm very much a newbie to Ubuntu and vaguely remember using DOS but am not geekie. Help.....!

---

### Post by chili555 on 2014-02-27
I'm not quite sure what you mean by, ' I've set up my network printer (Canon MP970) in Ubuntu...and although it's there.' How and where is it set up?  

My network printer works perfectly with the setup I've attached. Generally, networked printers work best with ipp. A very few work with a variant ipp14. I am one of the lucky few. I'd suspect your printer would use something like:```
ipp://192.168.1.32:631/lpr
```

---

### Post by davidjohnston31 on 2014-02-27
Thanks Chilli555.. that has helped in that when I hit the print test page button it seems to be doing something and indicates 19% but then reverts to idle with nothing printed.  The printer is physically in another room and connected to the network by ethernet.  I am "feeling" my way around Ubuntu at this stage but need to be productive at the same time.  I'm on a slow learning curve.  I can ping the IP address and I can access the printer through Firefox but it's like as though something is missing...

---

### Post by chili555 on 2014-02-27
Are there any interesting clues here?```
cat /var/log/cups/access_log | tail -n20
```Or in:```
cat /var/log/cups/error_log | tail -n20
```

---

### Post by davidjohnston31 on 2014-02-27
You tell me....

david@dj-lap:~$ cat /var/log/cups/access_log | tail -n20
localhost - david [27/Feb/2014:19:26:37 +0000] "POST /admin/ HTTP/1.1" 200 133 Resume-Printer successful-ok
localhost - david [27/Feb/2014:19:26:37 +0000] "POST /admin/ HTTP/1.1" 200 133 CUPS-Accept-Jobs successful-ok
localhost - david [27/Feb/2014:19:26:37 +0000] "POST /admin/ HTTP/1.1" 200 133 CUPS-Set-Default successful-ok
localhost - david [27/Feb/2014:19:26:37 +0000] "POST /admin/ HTTP/1.1" 200 155 CUPS-Add-Modify-Printer successful-ok
localhost - david [27/Feb/2014:19:26:37 +0000] "POST /admin/ HTTP/1.1" 200 168 CUPS-Add-Modify-Printer successful-ok
localhost - - [27/Feb/2014:19:26:42 +0000] "POST /printers/Canon-PIXMA-MP970 HTTP/1.1" 200 419 Print-Job successful-ok
localhost - david [27/Feb/2014:19:27:28 +0000] "POST /admin/ HTTP/1.1" 200 133 CUPS-Delete-Printer successful-ok
localhost - david [27/Feb/2014:19:27:41 +0000] "POST /admin/ HTTP/1.1" 200 133 CUPS-Delete-Printer client-error-not-found
localhost - - [27/Feb/2014:19:27:56 +0000] "POST / HTTP/1.1" 200 153 Cancel-Subscription successful-ok
localhost - - [27/Feb/2014:19:28:00 +0000] "POST / HTTP/1.1" 200 253 Create-Printer-Subscription successful-ok
localhost - - [27/Feb/2014:19:28:06 +0000] "POST / HTTP/1.1" 200 153 Cancel-Subscription successful-ok
localhost - - [27/Feb/2014:19:34:50 +0000] "POST / HTTP/1.1" 200 153 Cancel-Subscription successful-ok
localhost - david [27/Feb/2014:19:38:04 +0000] "POST / HTTP/1.1" 200 186 Renew-Subscription successful-ok
localhost - david [27/Feb/2014:19:52:04 +0000] "POST / HTTP/1.1" 200 186 Renew-Subscription successful-ok
localhost - david [27/Feb/2014:20:06:04 +0000] "POST / HTTP/1.1" 200 186 Renew-Subscription successful-ok
localhost - david [27/Feb/2014:20:20:04 +0000] "POST / HTTP/1.1" 200 186 Renew-Subscription successful-ok
localhost - david [27/Feb/2014:20:34:04 +0000] "POST / HTTP/1.1" 200 186 Renew-Subscription successful-ok
localhost - david [27/Feb/2014:20:48:04 +0000] "POST / HTTP/1.1" 200 186 Renew-Subscription successful-ok
localhost - david [27/Feb/2014:21:02:04 +0000] "POST / HTTP/1.1" 200 186 Renew-Subscription successful-ok
localhost - david [27/Feb/2014:21:16:04 +0000] "POST / HTTP/1.1" 200 186 Renew-Subscription successful-ok
david@dj-lap:~$ 


and

  	 	 	 	   [FONT=Ubuntu]david@dj-lap:~$ cat /var/log/cups/error_log | tail -n20 [/FONT]
 [FONT=Ubuntu]W [27/Feb/2014:19:24:54 +0000] [Job 24] The printer is busy. [/FONT]
 [FONT=Ubuntu]W [27/Feb/2014:19:24:55 +0000] [Job 24] The printer is busy. [/FONT]
 [FONT=Ubuntu]E [27/Feb/2014:19:25:52 +0000] Returning IPP client-error-not-possible for CUPS-Add-Modify-Printer (ipp://localhost/printers/Canon-PIXMA-MP970) from localhost [/FONT]
 [FONT=Ubuntu]W [27/Feb/2014:19:26:37 +0000] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-PIXMA-MP970-Gray..' already exists [/FONT]
 [FONT=Ubuntu]W [27/Feb/2014:19:26:37 +0000] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-PIXMA-MP970-RGB..' already exists [/FONT]
 [FONT=Ubuntu]W [27/Feb/2014:19:26:37 +0000] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon-PIXMA-MP970' already exists [/FONT]
 [FONT=Ubuntu]W [27/Feb/2014:19:26:37 +0000] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-PIXMA-MP970-Gray..' already exists [/FONT]
 [FONT=Ubuntu]W [27/Feb/2014:19:26:37 +0000] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-PIXMA-MP970-RGB..' already exists [/FONT]
 [FONT=Ubuntu]W [27/Feb/2014:19:26:37 +0000] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon-PIXMA-MP970' already exists [/FONT]
 [FONT=Ubuntu]E [27/Feb/2014:19:26:37 +0000] Failed to update TXT record for Canon PIXMA MP970 @ dj-lap: -2 [/FONT]
 [FONT=Ubuntu]W [27/Feb/2014:19:26:37 +0000] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-PIXMA-MP970-Gray..' already exists [/FONT]
 [FONT=Ubuntu]W [27/Feb/2014:19:26:37 +0000] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-PIXMA-MP970-RGB..' already exists [/FONT]
 [FONT=Ubuntu]W [27/Feb/2014:19:26:37 +0000] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon-PIXMA-MP970' already exists [/FONT]
 [FONT=Ubuntu]W [27/Feb/2014:19:26:37 +0000] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-PIXMA-MP970-Gray..' already exists [/FONT]
 [FONT=Ubuntu]W [27/Feb/2014:19:26:37 +0000] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-PIXMA-MP970-RGB..' already exists [/FONT]
 [FONT=Ubuntu]W [27/Feb/2014:19:26:37 +0000] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon-PIXMA-MP970' already exists [/FONT]
 [FONT=Ubuntu]W [27/Feb/2014:19:26:49 +0000] [Job 25] The printer is busy. [/FONT]
 [FONT=Ubuntu]W [27/Feb/2014:19:26:54 +0000] [Job 25] The printer is busy. [/FONT]
 [FONT=Ubuntu]W [27/Feb/2014:19:27:04 +0000] [Job 25] The printer is busy. [/FONT]
 [FONT=Ubuntu]W [27/Feb/2014:19:27:19 +0000] [Job 25] The printer is busy. [/FONT]
 [FONT=Ubuntu]david@dj-lap:~$ [/FONT]

---

### Post by chili555 on 2014-02-27
> ipp://localhost/printers/Canon-PIXMA-MP970Have you changed this? Isn't it now ipp://192.168.1.32:631/printers/Canon-PIXMA-MP970 or some such? What does this report?```
sudo cat /etc/cups/printers.conf
```Are you making these adjustments in System Settings > Printers > Properties? Or...where?

---

### Post by davidjohnston31 on 2014-02-28
I've been trying different combinations through Dash Home/Printing/Properties.  I've also uninstalled the printer and reinstalled through Dash Home/Printing and also tried through localhost:631/printers.  It's as though the printer is "seen" ok but no communication.  The print queue shows "Pending-Not Connected?".  I really haven't a clue what I'm doing and am frustrated because Ubuntu is supposed to be so easy to use... I suppose it is if you're a programmer but it's far from user-friendly if you're not. The following outputs are probably self-explanatory...

                        david@dj-lap:~$ sudo cat /etc/cups/printers.conf 
 [sudo] password for david:  
 # Printer configuration file for CUPS v1.5.3 
 # Written by cupsd 
 # DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING 
 <DefaultPrinter Canon-PIXMA-MP970> 
 UUID urn:uuid:9e80437c-9b6a-3dde-6ff1-efdb4cef8f22 
 Info Canon PIXMA MP970 
 Location  
 MakeModel Canon PIXMA MP970 - CUPS+Gutenprint v5.2.8-pre1 
 DeviceURI ipp14://192.168.1.32:631/lpr 
 State Idle 
 StateTime 1393620311 
 Type 45084 
 Accepting Yes 
 Shared Yes 
 JobSheets none none 
 QuotaPeriod 0 
 PageLimit 0 
 KLimit 0 
 OpPolicy default 
 ErrorPolicy retry-job 
 </Printer> 
 david@dj-lap:~$  
 

 

 david@dj-lap:~$ sudo cat /etc/cups/printers.conf 
 [sudo] password for david:  
 # Printer configuration file for CUPS v1.5.3 
 # Written by cupsd 
 # DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING 
 <DefaultPrinter Canon-PIXMA-MP970> 
 UUID urn:uuid:9e80437c-9b6a-3dde-6ff1-efdb4cef8f22 
 Info Canon PIXMA MP970 
 Location  
 MakeModel Canon PIXMA MP970 - CUPS+Gutenprint v5.2.8-pre1 
 DeviceURI ipp://192.168.1.32:631/printers/ 
 State Idle 
 StateTime 1393620630 
 Type 45084 
 Accepting Yes 
 Shared Yes 
 JobSheets none none 
 QuotaPeriod 0 
 PageLimit 0 
 KLimit 0 
 OpPolicy default 
 ErrorPolicy retry-job 
 </Printer> 
 david@dj-lap:~$  
 

 

 david@dj-lap:~$ sudo cat /etc/cups/printers.conf 
 [sudo] password for david:  
 # Printer configuration file for CUPS v1.5.3 
 # Written by cupsd 
 # DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING 
 <DefaultPrinter Canon-PIXMA-MP970> 
 UUID urn:uuid:9e80437c-9b6a-3dde-6ff1-efdb4cef8f22 
 Info Canon PIXMA MP970 
 Location  
 MakeModel Canon PIXMA MP970 - CUPS+Gutenprint v5.2.8-pre1 
 DeviceURI ipp://192.168.1.32:631/ipp 
 State Idle 
 StateTime 1393620769 
 Type 45084 
 Accepting Yes 
 Shared Yes 
 JobSheets none none 
 QuotaPeriod 0 
 PageLimit 0 
 KLimit 0 
 OpPolicy default 
 ErrorPolicy retry-job 
 </Printer> 
 david@dj-lap:~$


I should add that I am in effect trying to communicate directly with the printer on the network, not via another computer/server.

---

### Post by Easy Limits on 2014-02-28
12.04 has a hard time getting some networked printers to work.  Try the command:  system-config-printer

---

### Post by davidjohnston31 on 2014-03-01
Thanks EasyLimits... I've tried that and it simply gives me the same "Printing - Localhost" dialogue box.  Setup MP970 on IP address 192.168.1.32 using URI ipp://192.168.1.32:631/ipp and click on Print Test Page.... "Printer processing Page 1 19%" then "Processing - the printer is busy". but nothing is printed.  Document Print Status says "Pending not connected" or "Processing not connected".  I have to confess to not understanding the structure of the URI designation.  I've tried every combination but nothing seems to work. The following is the Terminal output before the "Printing - Localhost" dialogue box appeared.  Is there a way of configuring the printer purely through the Terminal?

---

### Post by chili555 on 2014-03-01
I noticed, in the Network Setup Guide, that the machine needs to be set up for LAN connections while initially configured by USB. May I assume this was done? [http://gdlp01.c-wss.com/gds/3/0300000413/01/mp970_nsg_us_v1.pdf](http://gdlp01.c-wss.com/gds/3/0300000413/01/mp970_nsg_us_v1.pdf)

I am mystified that any new computer added to the network needs to have Canon's software run on it, too, in order to get the printer and computer to see each other. I hope it is the driver and not necessarily the network piece.

Can you confirm that port 631, the port cups listens on, is open on the printer's IP address?```
nmap 192.168.1.32
```On my networked printer, I get:```
Nmap scan report for PrinterServer (192.168.1.19)
Host is up (0.77s latency).
Not shown: 995 closed ports
PORT     STATE SERVICE
80/tcp   open  http
139/tcp  open  netbios-ssn
515/tcp  open  printer
[COLOR="#FF0000"]631/tcp  open  ipp[/COLOR]
9100/tcp open  jetdirect
```

---

### Post by davidjohnston31 on 2014-03-01
I have setup the MP970 on USB and successfully printed to it.  Still no joy on the network.  I've continued to try ipp and also appsocket to no avail.  the output from nmap is:

david@dj-lap:~$ nmap 192.168.1.32

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2014-03-01 17:24 GMT
Nmap scan report for 192.168.1.32
Host is up (0.072s latency).
Not shown: 998 closed ports
PORT    STATE SERVICE
80/tcp  open  http
139/tcp open  netbios-ssn

Nmap done: 1 IP address (1 host up) scanned in 14.04 seconds
david@dj-lap:~$ 


It seems that 631 and 9100 aren't open.  I've tried <ufw allow 9100/tcp> and <ufw allow 631/tcp> but makes no difference.

---

### Post by chili555 on 2014-03-01
It's official! I now more about Canon printers than I do my own Samsung! Yikes!

I saw this: [http://blog.gmane.org/gmane.comp.printing.cups.bugs/page=108](http://blog.gmane.org/gmane.comp.printing.cups.bugs/page=108)> "ghost" image on Pixma MP970

Hello all,
When printing, the color parts generate like a "ghost image", that is larger than the original and located
on the right, but lighter and in grey. Other than this "ghost image", the print is fine.

- Debian Squeeze, i386
- cups 1.4.4-3
- cups-bjnp-0.5.4
- Driver:	Canon PIXMA MP970 - CUPS+Gutenprint v5.2.6 (color, 2-sided printing)
- Connection:	[COLOR="#FF0000"]bjnp://canon-mp970:8611[/COLOR]
- printing over the network

Does anybody have an idea on how to correct this problem? (BTW, the scanner is just doing fine over the network).
And this: [https://help.ubuntu.com/community/HardwareSupportComponentsPrintersCanonPrintersCanonMP620](https://help.ubuntu.com/community/HardwareSupportComponentsPrintersCanonPrintersCanonMP620)>  The Canon printer URI built itself to form as [COLOR="#FF0000"]bjnp://192.168.1.150:8611[/COLOR] I'm not sure if or how this will help us because port 8611 is also among those not open! However, since we are low on ideas/talent/mojo,etc., I suggest you install the package:```
sudo apt-get install cups-backend-bjnp
```Then see if you can use the web-based interface as described here: >     Open the CUPS Admin interface by opening either [http://localhost:631/](http://localhost:631/) or [http://127.0.0.1:631/](http://127.0.0.1:631/) in your web browser.

    In the CUPS Admin interface, click Administration -> Find Printer and select Canon MP620 series <ip-address> (where <ip-address> will depend on the IP address of your printer).

    Click Add Printer, give it a name and push Continue.

    On the following screen you will be able to choose the Device. Pull down the list and select Canon MP620 series ip-address.

    Click Continue and at the next screen select Canon MP620-630 series from the list.

        Note: Do NOT search for Canon PIXMA something, search for Canon MP620-630, without the PIXMA bit! 
    When asked for a login and password, use whatever you configured CUPS to use. This is your Ubuntu username and password by default.
    Send a test page to the printer. 

Note 1: You may need to change the paper size in the CUPS printer setup box.

Note 2: The Canon printer URI built itself to form as bjnp://192.168.1.150:8611

And now you should have Bob as a very close relative .... Happy printing!!Of course, substitute your details here.

The settings in ufw only affect your computer, not the printer.

---

### Post by Easy Limits on 2014-03-01
You may want to give the printer an IP address that is outside of your network IP address range.  For example, if you have 192.168.1.1 through 192.168.1.49 as your range then set the printer as 192.168.1.50.  

Is the printer connected via a printer server or is it connected to the router?

---

### Post by davidjohnston31 on 2014-03-02
Folks, this is crazy... I'll have to revert to Windows for my network printing requirements which is a nuisance for something that should be simple.  I will first try changing the ip address of the printer to a higher number as Easy Limits suggests.  The printer is physically connected to a router in my garden office (remote from my house).  I've tried downloading the cups backend bjnp suggested by Chili555 but it's been updated, is from January 2014 and is a gz file the contents of which need to be compiled.  It's aimed at administrators which I am not and although I can be adventurous that's way, way beyond my capabilities.  I really don't know why I've been putting myself through this... life's too short and I'm too old.

---

### Post by chili555 on 2014-03-02
We'll be sorry to see you go. If you change your mind and want to try once more, I suggest you install 13.10 and then cups-backend-bjnp.

This is a suggestion from a guy undoubtedly older than you! Do you have any great-grandchildren like me? Retired more than 15 years??

---

### Post by davidjohnston31 on 2014-03-03
Thanks Chili555 and Easy Limits for trying to help out.  I've dumped my 12.04 and will try again with 13.10 or 13.04 or maybe wait for 14.04 but I'm giving Ubuntu a rest for the time being.  I'm not sufficiently dedicated as a pioneer and see a computer as a tool for work rather than constantly having to tinker and tweak things in order to fulfil basic tasks.  See you on the next go-around!

---

