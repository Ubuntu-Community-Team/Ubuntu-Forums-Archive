---
title: "Sharing CUPS Printer"
date: 2005-05-01
forum: Networking &amp; Wireless
---

### Post by darthsabbath on 2005-05-01
Hey all, finally got a Linux compatible printer, and it works like a charm on my desktop.  However, I want to set it up to share over my network (to a laptop running Hoary as well).

However, I'm bloody lost.  I've followed the various threads on here... included this
in my /etc/cups/cupsd.conf file

```

User cupsys
Group lpadmin
RunAsUser Yes
Port 631
SystemGroup lpadmin
<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.1.*
</Location>

```

Then I go to Printers, and add a network printer, pointing the URI to:
ipp://myservername/printers/Deskjet_5700

The printer is a HP DeskJet 5740.  The Device URI in CUPS on the desktop is listed as hp:/usb/Deskjet_5700?serial=MY49D1W1C1040S

I've also tried pointing the URI to ipp://myservername/usb/Deskjet_5700.  That doesn't work either.  

Any other relevant fields I could look into, or a user friendly CUPS interface? 

Very frustrating here. :/

Granted... I'm learning a lot, so that's good at least. ;-)

If I need to post any further information, please let me know

Phil

---

### Post by darthsabbath on 2005-05-02
Just wanted to see if I have this in the right section... should I have posted elsewhere? 

Sorry if I've misposted. :-)

Phil

---

### Post by darthsabbath on 2005-05-06
It was an ID10T error... accidentlly put the wrong subnet into my Allow From in cupsd.conf.

*crawls back into his corner to hide his shame*

Phil

---

### Post by Rodrigo on 2005-05-06
LOL, dont worry, the thread help me to understan better the proces of sharing printers with cups  :grin:

---

### Post by darthsabbath on 2005-05-07
That's great to hear!  Isn't that what Ubuntu is all about? :D 

Printing is one of the few things I'm unhappy with in Linux, and one of the few things I feel Microsoft gets right.  With Windows, it just works... I can understand the need for turning off CUPS listening on port 631 for security reasons, but in a small home LAN (which is where I would imagine Ubuntu is being used the most), it seems kludged for it to be off by default.

Just as a tip (and forgive me if I don't have the steps exact... I'm typing this from my parents' WinXP box)... make sure you have the printer applet set to detect printers over the LAN on both machine the printer is hooked up to and the system you're trying to print from.  

Then makesure you issue the command "sudo adduser shadow cupsys," and have your cupsd.conf set to something like mine... took a lot of work for something that could've been done in a few clicks.  

Don't get me wrong, I'm not afraid to edit conf files... but what about ESR's [Aunt Tilly](http://www.catb.org/~esr/writings/cups-horror.html) [The Luxury of Ignorance]?  

I'm teaching myself programming, and I think for one of my first projects, I'm going to try and hack together a UI that will allow for more advanced printer and share configuration than what's currently in GNOME.  

Anyway, didn't mean to rant here. ;-) 

Phil

---

### Post by occy on 2005-05-07
Ok, I have tried to use this thread to get printing working, and what is recommended here did not work.  I've also tried what can be found here:

[How can I share my printer on my LAN?](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions) (you have to scroll half-way down this page)

These have not worked.  Here is my setup.

Ubuntu Hoary Laptop(Upgraded from Warty) 10.10.0.25 [wireless]
(NO PRINTER ATTACHED)

Ubuntu Hoary Desktop (Brand new Install) 10.10.0.7 [eth0 - wired]
(Printer installed and working locally - HP 1100A)

I'm trying to get the laptop, to print remotely to the desktop.  

Here is my Desktops /etc/cups/cupsd.conf

```
DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 10.10.0.1.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>
``` 

Here is my laptops /etc/cups/client.conf

```
ServerName 10.10.0.7
``` 


You would think there would be some easy clicky clicky stuff with all of the niceness that Ubuntu/GNOME has with setting up things.  This is one of the areas apparently that is yet to work easily / seamlessly.

Any help on this matter would be greatly appreciated.

 ](*,) 

Thanks,
Trae

PS. Yes, I can ssh to the laptop from the desktop and vice versa in case someone wanted to know if networking was in proper order.

---

### Post by darthsabbath on 2005-05-08
In this section of cupsd.conf...

```

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 10.10.0.1.*
</Location>

``` 

Should probably be

```

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 10.10.0.*
</Location>

```

This is almost exactly what I did.  For my "Allow From" entry, I had 192.168.1.*, when it should have been 192.168.0.*

I agree fully with you that this is a matter that should be fixed... the command line is an invaluble, powerful tool, and while I enjoy learning the inner workings of conffiles, when I would rather be doing something else, I just want my OS to work.

Hope this helps. :D

Phil

---

### Post by occy on 2005-05-08
THAT DID IT!

You know, I was half-way thinking about checking that.  As it sorta looked dubious.  I should have known better.  I guess this is what you were talking about. ;)

Thanks again,
Trae

---

### Post by occy on 2005-05-08
[Occy's Guide to Printer Sharing.](http://occy.net/printing) 

I've made a quick little page that is a reference to setting up a printer within Ubuntu.  It bascially weeds out the foo that is here and provides a good, quick, concise walk through of the exact files you need to edit and such.  

Catch me on #ubuntu or #ubuntuforums if you have problems with it and still need help.

Trae

---

### Post by chandra on 2005-06-08
The file /etc/cups/cupsd-browsing.conf sets Browsing Off by default.  This disallows access from other PCs on the LAN.

To turn browsing on, either edit /etc/cups/cupsd-browsing.conf and change "Off" to "On" or go to /usr/share/cups and do

./enable_browsing 1

Then, (sudo) edit /etc/cups/cupsd.conf to comment out the following line so:

# Listen 127.0.0.1:631

and uncomment, as appropriate, to have these entries:

Port 631
Browsing On
BrowseAddress @LOCAL
<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From @LOCAL
</Location>

Finally, 

sudo /etc/init.d/cupsys restart

and your CUPS printer should be visible from other PCs on the LAN.

---

### Post by usergentoo on 2005-07-15
I couldnt get mine to work so I checked the log and seen this.

```
E [15/Jul/2005:15:41:50 -0400] StartListening: Unable to bind socket for addres7f000001:631 - Address already in use
```


Solved

Had to edit /etc/cups/cupsd.conf and comment out the line

# Listen 127.0.0.1:631

And edit /etc/cups/cupsd-browsing.conf and change 

Browsing Off

to

Browsing On

---

### Post by neocon2005 on 2005-07-27
I have one Ubuntu box (192.168.0.102) and one WinXP (192.168.0.101). Canon i320 connected to Ubuntu via USB. WinXP on wireless G. Essentially copied and pasted the cupsd.conf code from below (except changed the 10.10.0.25 to 192.168.0.101). On XP, entered printer location as [http://192.168.0.102:631/printers/tp0](http://192.168.0.102:631/printers/tp0) (name of the printer on Ubuntu). Prints from both Ubuntu and WinXP like a charm. Thanks a bunch for the .conf file! Greatly appreciated!


[QUOTE=occy]Ok, I have tried to use this thread to get printing working, and what is recommended here did not work.  I've also tried what can be found here:

[How can I share my printer on my LAN?](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions) (you have to scroll half-way down this page)

These have not worked.  Here is my setup.

Ubuntu Hoary Laptop(Upgraded from Warty) 10.10.0.25 [wireless]
(NO PRINTER ATTACHED)

Ubuntu Hoary Desktop (Brand new Install) 10.10.0.7 [eth0 - wired]
(Printer installed and working locally - HP 1100A)

I'm trying to get the laptop, to print remotely to the desktop.  

Here is my Desktops /etc/cups/cupsd.conf

```
DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 10.10.0.1.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>
``` 

Here is my laptops /etc/cups/client.conf

```
ServerName 10.10.0.7
``` 


You would think there would be some easy clicky clicky stuff with all of the niceness that Ubuntu/GNOME has with setting up things.  This is one of the areas apparently that is yet to work easily / seamlessly.

Any help on this matter would be greatly appreciated.

 ](*,) 

Thanks,
Trae

PS. Yes, I can ssh to the laptop from the desktop and vice versa in case someone wanted to know if networking was in proper order.[/QUOTE]

---

### Post by ubuntu-nerd2005 on 2005-08-12
[QUOTE=occy][Occy's Guide to Printer Sharing.](http://occy.net/printing) 

[/QUOTE]

I just want to say how thankful I am for this.

I have been knocking myself out for days trying to set up network printing on my home network.

What you suggested worked for me.

Just got to get the sound working now.

Unfortunatly the whole experience reminds me of the bad old days of Win98 :-(

---

### Post by Imgonna on 2005-09-04
Thanks all

After putting off connecting my laptop to desktop via CUPS (for printing) just followed this thread and in less than 5 mins I now have shared two printers so my wife can not only shop online from the bedroom, but also print receipts....

Cheers

Glen

---

### Post by mumushi on 2005-09-21
ei iwas reading about how to share printer but i got i problem i can't edit the cupsd.conf file. i provided the sudo su command so i could have super user previleges but it said i can't edit it. where did i went wrong. pls help me with this i'm a newbie in ubuntu. thanks in advance.
 :)

---

### Post by darthsabbath on 2005-09-22
What was the exact command you entered? Was it in the same format at this?

```

sudo *editorname* /etc/cups/cupsd.conf

```

From there, what was the error message?  If entering that command doesn't work, try 

```

ls -al /etc/cups/cupsd.conf

```

And let us know what the output is... you should see something like...

```

-rw-r-----  1 cupsys lpadmin 22929 2005-08-28 16:43 /etc/cups/cupsd.conf

```

Phil

---

### Post by zero0w on 2005-10-30
[QUOTE=darthsabbath]Should probably be

```

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 10.10.0.*
</Location>

```

This is almost exactly what I did.  For my "Allow From" entry, I had 192.168.1.*, when it should have been 192.168.0.*

Phil[/QUOTE]

In my case it is the opposite, I've tried to set Allow From 192.168.**0**.*, but that doesn't work (although the printer is detected, it won't print). When I have set it to Allow From 192.168.**1**.*, it works immediately! I guess it may be due to the difference in router boxes or their setup.

One thing to notice is that Firestarter (a GTK Firewall software) will interfere with the network printer detection of CUPS on the client side (I need to turn off Firestarter in order to detect a LAN printer); while Shorewall works okay. So make sure it is not a firewall problem when sharing CUPS printer on a network.

---

### Post by foxy123 on 2005-11-21
Hi, I followed Occy's guide and network printer popped up in gnome-cups-manager. However the problem is that my printing server is a dual boot desktop. When it is booted in Windows and my client.conf on my laptop has a line:
```
ServerName 10.0.0.11
```

gnome-cups-manager gives me an error:
```
** (gnome-cups-manager:7957): WARNING **: IPP request failed with status 1280 ** (gnome-cups-manager:7957): WARNING **: IPP request failed with status 1280
```
and error message:
```
The CUPS server could not be contacted.

```
As soon as I comment this line, I can launch gnome-cups-manager and print to a desktop, booted in Windows, but cannot print when desktop is booted in Ubuntu.

I am on Breezy now, but did not have this problem on Hoary. I was able both prit to my network printer regardless haw was my deskto booted. I wonder what has changed and how to fix it?

---

### Post by ollyshaw on 2006-02-13
I had exactly the same problem as zero0w. All working nicely now, compared to how easy ubuntu is now, this was a pain!

Olly

---

### Post by caraboy on 2006-04-19
I installed my hp deskjet 450 printer using cups interface on port 631, I can connect and print from an XP box, but when I select print test page from cups admin interface I get the following error: client-error-not-possible. Of course, it doesn`t print anything. How can I fix this? ](*,)

---

### Post by connellr on 2006-05-09
Ok, this is VERY similar to what others have said, but I had ran into some problems when I followed the above steps exactly (partially because I wanted to use both a local and a network printer on my client machine)

So, the following setup allows you to Have 1 machine (from now on I will call this machine "The Server") with a printer runing Ubuntu, and another machine (I'll call it "The Client") that has both a locally attached printer, and has access to the printer on the server.  The client computer can be running either Linux or Windows XP (probably other OSs too, but those are the only ones I tested)

edit **/etc/cups/cupsd.conf** to be as follows:
*Note: Change 192.168.0.201 to be "The Server's" IP address, and 192.168.0.* to your subnet.*

```

DefaultCharset notused
ConfigFilePerm 0600
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Listen 127.0.0.1:631
Listen 192.168.0.201:631
#Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>

```

On client station:
set up a new network printer to use internet address 

**[http://192.168.0.201:631/printers/Printer-Name](http://192.168.0.201:631/printers/Printer-Name)**

If the client machine is linux you MAY need to enable *Detect LAN Printers*   (System > Administration > Printing >> Global Settings Drop-Down)

You DO NOT need to edit your client.conf file as mentioned in a previous post ... In fact doing so will prevent you from using locally attached printers.

---

### Post by pizzipie on 2006-05-28
Subject: Printer Sharing

Hi, I am running ubuntu 5.10 Breezy.

I am a newbie in spades and the answer to my problem is probably, I
hope,; some really simple thing I didn't do but .......

At present when I go to Administration / Printing I get this
message;;;;;;; "**The CUPS server could not be contacted.**"; I
don't have a teeny clue as to what to do now since I can no longer
print to even the physically connected printers, on either computer. 
There are no printers !! I also use 'webmin' to help with configuration
but it now reports 'no printers'.; Something I did wiped out all my NFS
stuff. However,the 'hosts' file and the 'exports' file are still the
same as they were.

Desired print system as follows:

PC- host name - gateway(192.168.1.101)
LAPTOP- host name - hp(192.168.1.102)

(Computers were able to ping each other and pass files back and forth.
No more.)

gateway connected to: epson-1280 via usb, deskjet-812C remote
hp connected to: deskjet812C via parallel, epson-1280 remote

Each computer would connect to it's respective physically connected
printer and print files. On the remote side, apparently connection was
made but nothing printed. Looking at the print job stats, the files
were pending . 

;To try and fix this I got looking into the Ubuntu forums and found
your "http://occy.net/Printing" article. I am enclosing my hosts,
exports,; cupsd.conf, cupsd-browsing.conf and client.conf files in
hopes something is wrong here as all the BIG problem started after I
tried printing with the new config file. A little knowledge is
dangerous eh?

Thank you much in advance for your help.

Rick P.

 **Following are files involved in this**

 filename="client.conf"

#

ServerName hp


 filename="cupsd-browsing.conf"

#
# Browsing: whether or not to broadcast and/or listen for CUPS printer
# information on the network.  Disabled by default.
#

Browsing On


 filename="cupsd.conf"

#
#
# From [http://OCCY.net/printing](http://OCCY.net/printing)
########################################################################
#                                                                      #
# 
#

DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631

Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location/>
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From gateway
#192.168.0.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>




 filename="hosts"

127.0.0.1 localhost.localdomain localhost gateway

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


192.168.1.103	rhino
192.168.1.102	hp


 filename="exports"

#		to NFS clients.  See exports(5).


/home	192.168.1.102(no_root_squash,rw) 192.168.1.103(no_root_squash,rw)
 

filename="printers.conf"

# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Fri May 26 18:46:52 2006

<Printer Deskjet-812C>
Info General Printer
DeviceURI ipp://102.168.1.102/Deskjet-812C
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0

</Printer>
<DefaultPrinter Stylus-Photo-1280>
Info Stylus-Photo-1280
DeviceURI usb:/dev/usb/lp0
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

---

### Post by pizzipie on 2006-05-28
Sorry, I had sent the above message to occy.net. Still same problem so I' m just throwing the problem to many people in hope of a fix.

Thanks, RP

---

### Post by connellr on 2006-05-29
Pizzipie,

Check and make sure that you have the CUPS server installed on your system.  You can check this under Synaptic Package Manager.  If this is not yet installed that is your problem.  If it is already installed you may need to make sure the service is configured to start at boot.  Let us know if you have questions on how to do any of this.

RJ

> **pizzipie]Subject: Printer Sharing

Hi, I am running ubuntu 5.10 Breezy.

I am a newbie in spades and the answer to my problem is probably, I
hope, said:**
> http://OCCY.net/printing[/url]
########################################################################
#                                                                      #
# 
#

DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631

Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location/>
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From gateway
#192.168.0.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>




 filename="hosts"

127.0.0.1 localhost.localdomain localhost gateway

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


192.168.1.103	rhino
192.168.1.102	hp


 filename="exports"

#		to NFS clients.  See exports(5).


/home	192.168.1.102(no_root_squash,rw) 192.168.1.103(no_root_squash,rw)
 

filename="printers.conf"

# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Fri May 26 18:46:52 2006

<Printer Deskjet-812C>
Info General Printer
DeviceURI ipp://102.168.1.102/Deskjet-812C
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0

</Printer>
<DefaultPrinter Stylus-Photo-1280>
Info Stylus-Photo-1280
DeviceURI usb:/dev/usb/lp0
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

---

### Post by pizzipie on 2006-05-29
CUPSYS is running!! see ..
[ATTACH]10238[/ATTACH] Maybe there is hope. I was just about to start all over again by re-installing Breezy but found your message. As of now Systems->Admin->Printer reports New Printer-> "no printers detected" instead of "no CUPS ..." message.

---

### Post by pizzipie on 2006-05-29
Connellr;

I was just horrified to see that half the desktop items on the other computer (hp) were wiped out. The two (gateway and hp) are definitely talking to each other. Swearing at each other is more like it. I will go ahead and reinstall Breezy on hp and hope you will guide me from here.

rp

---

### Post by connellr on 2006-06-05
[QUOTE=pizzipie]Connellr;

I was just horrified to see that half the desktop items on the other computer (hp) were wiped out. The two (gateway and hp) are definitely talking to each other. Swearing at each other is more like it. I will go ahead and reinstall Breezy on hp and hope you will guide me from here.

rp[/QUOTE]

When you go to add the printer to the remote machine you'll have to choose network printer and put in the address (see [This Post]("http://ubuntuforums.org/showpost.php?p=997110&postcount=21") for an example.  So in your case you would use the address you would enter on your pc to use your deskjet-812C would be [http://192.168.1.102:631/printers/deskjet-812C](http://192.168.1.102:631/printers/deskjet-812C)   and the address you would use on your laptop to access the epson would be [http://192.168.1.101:631/printers/deskjet812C](http://192.168.1.101:631/printers/deskjet812C)

(Note: you need to make sure the last part of the address is the exact name of the printer on the other machine ... I was making assumptions)

The code you want to use in your /etc/cups/cupsd.conf on your PC is
```

DefaultCharset notused
ConfigFilePerm 0600
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Listen 127.0.0.1:631
Listen 192.168.1.101:631
#Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.1.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>

```

And on your Laptop use the code
```

DefaultCharset notused
ConfigFilePerm 0600
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Listen 127.0.0.1:631
Listen 192.168.1.102:631
#Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.1.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>

```

Of course if you have any firewall on either machine, or on your network, you'll need to make sure that communications on port 631 are allowed between the two machines.  This method only requires CUPS, there are other ways to share with NFS/Samba, but I've never used them because I think CUPS is easier.  Let me know if you run into problems and I'll try to help you stumble through them.

I hope Im not tottaly misunderstanding your situation and off in left field ... Good luck.

RJ

---

### Post by pizzipie on 2006-06-05
connellr;

Thanks for the reply. I will give your instructions a try. 

rp

---

### Post by thelarster on 2006-07-03
This thread has been a great help sharing my HP Photosmart 7660 w/ my Windows Lap Top from Ubuntu desktop.

But... I can connect to this printer from the Windows printer wizard, but it doesn't recognize or have listed the model number when it wants to install the driver. Is this some setting somewhere or just a 'Windows issue.'

---

### Post by lonetree on 2006-07-06
I have been using ubuntu 5.04 since it was released until last few days where I decided to upgrade to 6.06, I did a clean install and configures my new machine to act as a file server, PDC, and as well as printer server.

In 5.04, I shared the printer to my windows machines using cups, by mean od ipp. Got it work from a guide by occy.

However, now, I am facing a problem with 6.06. When I first install my Minolta PagePro-1300W, 6.06 detected the printer and I install the driver successfully, but when I try to print, it didn't print until I do a search from the forum that I need to change some settings in /etc/cups/printers.conf. After which, printing start with no error.

Next, I have enable smb printing and also cups. I tried installing the networked printer in windows, at first, I tried using cups by mean of ipp, [http://servername:631/printers/printername](http://servername:631/printers/printername), that didn't work for me, nothing was printed out. Then i tried to add printer using smb printing, again, printer is reflected in windows, I connected the printer and installed the driver, this time, after the printer is added, it shows there, "access  denied, unable to connect", tried test print, but it still doesn't print.

However, one strnage thing I notice when I check the print job via cups web interface, it shows that all these test prints were completed.

What could I have done wrong here?

Last thing I did to make sure that print share is working, I tried printing from another ubuntu machine, and it printed out without fail.

Hope someone can help me on this, now all my windows machines cannot print at all.

regards,

---

### Post by mvaranda on 2006-07-09
Have you created a raw printer in Ubuntu machine ?
Did you download the proper driver in Windows machine ?

I am using a Ubuntu machine to serve either Ubuntu clients and XP in my local home LAN.

note: do not use the latest cupsys 1.2.1
It has a bug. Use cupsys 1.2.0

Also, I could not add the raw printer using the GUI.
So add it manually:

mvaranda@mv-home-linux:~$ sudo cat /etc/cups/printers.conf
Password:

# my /etc/cups/printers.conf
#
# Printer configuration file for CUPS v1.2.0
# Written by cupsd on 2006-06-13 21:04
<Printer Stylus-CX3810>
Info Epson Printer on basement
Location /usr/local/printerSpool
DeviceURI usb://EPSON/Stylus%20CX3800
State Idle
StateTime 1150247048
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer
</Printer>
#
# raw printer for XP machines
#
<Printer ForWindows>
Info Raw driver - Epson Printer on basement for Window
Location /usr/local/printerSpoolWin
DeviceURI usb://EPSON/Stylus%20CX3800
State Idle
StateTime 1150247048
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer
</Printer>

---

### Post by connellr on 2006-07-10
> **thelarster said:**
> This thread has been a great help sharing my HP Photosmart 7660 w/ my Windows Lap Top from Ubuntu desktop.

But... I can connect to this printer from the Windows printer wizard, but it doesn't recognize or have listed the model number when it wants to install the driver. Is this some setting somewhere or just a 'Windows issue.'

Aah, thats Windows Plug-and-pray for ya.   You need to download/install the driver for your printer

(I've saved you the trouble of searching, you can find it [here]("http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?product=305364&lc=en&cc=us&dlc=en&submit.y=10&submit.x=7&cc=us&lang=en"))

---

### Post by coolmig on 2006-07-31
Hey thanks for your post! It has been days to configure my printer on a two-Ubuntu home network, I was disappointed because I thought that IPP was not going to work and I was going to try it through Samba then. Even using a port-scan the port 631 didn't appear on the open ports. Using your very simple configuration guide for cups.conf finally I saw my printer on the LAN and it prints! Thanks a lot!!!!!!!!!

PD: Sorry for my bad english. ;)
Another happy Ubuntu user

---

### Post by wilberfan on 2006-08-25
> **occy said:**
> [Occy's Guide to Printer Sharing.](http://occy.net/printing) 

I've made a quick little page that is a reference to setting up a printer within Ubuntu.  It bascially weeds out the foo that is here and provides a good, quick, concise walk through of the exact files you need to edit and such.   

Man, I'm new enough at this (two weeks?) that I'm always shocked --pleasantly-- when I find advice like this...*and it works!*   :shock: 

(Using Dapper 6.06)

Thanks for your advice, dude!

---

### Post by matrix_83 on 2007-06-24
Hi,
I'm using CUPS ver 1.2.8 on Ubuntu 7.04. I have an Epson670 and a router USR9108a (my print server). I followed this guide:

[http://www.usr.com/support/9108a/9108a-ug/install_printer.htm](http://www.usr.com/support/9108a/9108a-ug/install_printer.htm) (go to "linux computer")

but pinter doesn't work. What is wrong? How can I configure CUPS? Thanks.

---

### Post by ThomasNovin on 2008-04-29
FYI; Manually modifying CUPS configuration and/or sharing with Samba isn't neccessary.

On my print server, in system-config-printer > Server Settings, I just checked "Share published printers on the network" and also "Allow printing from the Internet" (maybe not needed).

On the client, I checked "Show printers shared by other systems".

After a few minutes when I re-entered system-config-printer, my printer from the server was installed.

---

