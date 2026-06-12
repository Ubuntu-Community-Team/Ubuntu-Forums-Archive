---
title: "how do I Print Test Page using Terminal Commands?"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by ktritty on 2009-05-09
Could not find posted anywhere.

I am wondering how to attept to print a test page using terminal commands?

I am trying to use my server to host my printer at home so I don't need to have my iMac on all the time, nor run downstairs and hook up whatever laptop I am using.  The printer is not-network ready (Brother HL-5140).

Server runs Ubuntu 9.04 server.  I installed CUPS.  My Macintosh's can "see" the printer, but cannot print to it ("error: host busy" OR "connecting to <host> port 631" (hangs/timeout)).

Same problem when ufw disabled.

To troubleshoot, I want to see if I can print stuff from the server as that may be a good start.

Thanks!

---

### Post by spiderbatdad on 2009-05-09
```
man lpr
```might help. Not aware of a test page per se, but you can substitute a file.
Something like: ```
lpstat -a
```to list the printers. Then ```
lpr -P <PrinterName> <file>

```
Most commands have a man page. So, if you want to see more about lpstat...```
 man lpstat 
```

---

### Post by ktritty on 2009-05-09
Well, this may be part of the problem:

[FONT=Courier New][SIZE=3]$ lpstat -a
lpstat: no destinations added[/SIZE][/FONT]

It seems my printer installation was unsuccessful.  That would explain why my Mac's can send jobs to the queue, but the queue appears to be too busy.  Know of any links that can help me get it installed (remember, terminal commands only)?

I always try to check manpages before bugging anybody else, but good reminder.

Also, note the following that I attempted per your reply:

[FONT=Courier New][SIZE=3] $ man lpr
No Manual Entry for lpr
$ sudo apt-get lpr
E: Invalid operation lpr[/SIZE][/FONT]

Thanks

---

### Post by ktritty on 2009-05-09
***
"HERE'S MY SIGN" (blue collar comedy)
***

I forgot the "Install" argument for apt-get.

But the lpstat -a still returns the same, so I still need help installing my printer on the server.

---

### Post by MrWES on 2009-05-09
> **ktritty said:**
> ***
"HERE'S MY SIGN" (blue collar comedy)
***

I forgot the "Install" argument for apt-get.

But the lpstat -a still returns the same, so I still need help installing my printer on the server.


Open a browser from a computer on your server/network and point it to:
[http://IP_Of_Server:631]("http://IP_Of_Server:631")

That should give you the web GUI and you can install your printer on the server from there.

Bill

---

### Post by ktritty on 2009-05-10
> **MrWES said:**
> Open a browser from a computer on your server/network and point it to:
[http://IP_Of_Server:631](http://IP_Of_Server:631)

That should give you the web GUI and you can install your printer on the server from there.

Bill

I tried this, nothing happens.  Maybe I need to set a rule in the firewall to open Port 631?  I have a goofy network at home for a reason that I will spare.  I have two private IP ranges that I use, and I would like to open the 631 port to both ranges, but I am not sure how to do that either.  I run

[FONT=Courier New]$man ufw

[FONT=Arial]but I still don't quite grasp the syntax.

Also, I tried browsing to [http://ip.of.server:631](http://ip.of.server:631) after typing

[FONT=Courier New]$ sudo ufw disable

[FONT=Arial]But the browsing still fails.  Is there also a setting I need to change in /etc/cupsd.conf?  I set a line:
[/FONT][/FONT][/FONT][/FONT][FONT=Courier New][FONT=Arial][FONT=Courier New]Listen "hostname":631
[/FONT][/FONT][/FONT][FONT=Courier New][FONT=Arial][FONT=Courier New][FONT=Arial]and I thought that would do the trick, but no luck still[/FONT][/FONT][/FONT][/FONT]

---

### Post by spiderbatdad on 2009-05-10
I was understanding you had no gui and therefore no way to launch a web browser...
have you tried specifying a path by user@ip:631
for example ```
lpr -P username@192.168.1.1:631 test.txt
```
or lpr -P localhost@ip:631 file.txt

---

### Post by ktritty on 2009-05-10
> **spiderbatdad said:**
> I was understanding you had no gui and therefore no way to launch a web browser...
have you tried specifying a path by user@ip:631
for example ```
lpr -P username@192.168.1.1:631 test.txt
```or lpr -P localhost@ip:631 file.txt

1) I have no GUI on the Ubuntu server, but I have both an iMac and a MacBook (Tiger, Leopard, respectively) so I can run Firefox.  So any remote printer setup would work well.

2) Any time I execute lpr command on the server terminal it returns:
[FONT=Courier New]$ lpr -P "user@IP:631" "text.txt"
lpr: The printer or class was not found[/FONT]

[FONT=Arial]3) Still, any external hits on the server (from Xterm on MacBook / iMac) do not work
[FONT=Courier New]ktritty@MacBook$ ping -c 3 "Server IP"
"Good Echoes"

[FONT=Arial]in Firefox:
[http://serverIP:631](http://serverIP:631)
(Times Out)
[/FONT][/FONT][/FONT]
[FONT=Arial]
[/FONT]

---

### Post by fdmille on 2009-05-10
Try following the instructions to install the drivers on the following Brother Web site: [http://solutions.brother.com/linux/en_us/download_prn.html#HL-5140](http://solutions.brother.com/linux/en_us/download_prn.html#HL-5140)

---

### Post by albinootje on 2009-05-10
> **ktritty said:**
>  Server runs Ubuntu 9.04 server. 

I assume printing worked fine on the Ubuntu server itself ?
Please log in to the Ubuntu server, and type :
```

lpq

```
and post the result.

---

### Post by ktritty on 2009-05-10
> **fdmille said:**
> Try following the instructions to install the drivers on the following Brother Web site: [http://solutions.brother.com/linux/en_us/download_prn.html#HL-5140](http://solutions.brother.com/linux/en_us/download_prn.html#HL-5140)

Drivers were installed already.  I ran:

[FONT=Courier New]$ sudo apt-get install "brother-lpr-iforgettherest"

[FONT=Arial]and it seemed successful.  I got the driver instructions from a similar linux help link.[/FONT]
[/FONT]

---

### Post by ktritty on 2009-05-10
> **albinootje said:**
> I assume printing worked fine on the Ubuntu server itself ?
Please log in to the Ubuntu server, and type :
```

lpq

```and post the result.

No.  I can't print at all (unless i plug USB cable back into my MacBook in which case the Printer is P&P and works automaticaly, but that of course defeats the whole purpose of what I am trying to set up).

Per your request:

[FONT=Courier New]$ lpq
lpq: error - no default destination available

[FONT=Arial]I successfuly set up ssh/scp on my LAN and so I am attaching a copy of my /etc/cups/cupsd.conf file; maybe something there can help.
[/FONT][/FONT]

---

### Post by albinootje on 2009-05-10
> **ktritty said:**
> 
$ lpq
lpq: error - no default destination available

Good. This is something we can work with.

Did you actually configure the printer within Ubuntu ? Installing a driver is not enough.

Can you try :
```

sudo apt-get install lynx links

```
And then : lynx localhost:631 (or with links if you prefer).
And afair the file /etc/cups/printers.conf would be the file where the "per printer" configuration information goes.

---

### Post by albinootje on 2009-05-10
Or, since I assume you didn't configure your printer yet, use this :
```

lynx http://localhost:631/admin?OP=add-printer

```

---

### Post by ktritty on 2009-05-12
Well, there is another problem.  Even when I disable ufw:

[FONT=Courier New]$ lynx localhost:631[/FONT]
[FONT=Courier New]Looking up localhost:631
Making HTTP connection to localhost:631
Alert!: Unable to connect to remote host.

[FONT=Arial]Lynx returns similar error code when I type in the long URI that you gave as well.[/FONT]

Appended:
The file /etc/hosts contains an entry:
127.0.0.1 localhost
Also there is one for ip6
[/FONT]

---

### Post by albinootje on 2009-05-13
> **ktritty said:**
> Well, there is another problem.  Even when I disable ufw:

For the record, ufw should enable connections from localhost to localhost.
> 
Making HTTP connection to localhost:631
Alert!: Unable to connect to remote host.


That's pretty bad, shouldn't happen unless there's something wrong.
Can you post the content of : /etc/cups/printers.conf

---

### Post by ktritty on 2009-05-15
> **albinootje said:**
> Can you post the content of : /etc/cups/printers.conf

I don't have any printers.conf files on that path.  I have attached what is in my /etc/cups/ directory

---

### Post by albinootje on 2009-05-15
> **ktritty said:**
> I don't have any printers.conf files on that path.  I have attached what is in my /etc/cups/ directory

Thanks.
Can you try this :
[http://www.cups.org/doc-1.1/sam.html#4_2_1](http://www.cups.org/doc-1.1/sam.html#4_2_1)

And after doing that, restart cups with :
```

sudo /etc/init.d/cups restart

```

And then try the 631 port again, it's strange that even logged in to your server you cannot use [http://localhost:631](http://localhost:631)

---

### Post by ktritty on 2009-05-17
I've tried a few things over he past few days.  Some progress, getting warmer but still not resolved.

It occurred to me to try a clean install of cups using apt-get:

```
$ sudo apt-get purge cups
$ sudo apt-get install cups
$ lynx http://localhost:631
```

Lynx command successful!  I was able to add the printer locally using the web utility, and can print text files locally on my server.

But, when I try to access from a remote computer
[FONT=Courier New]web browser: [http://server.ip:631](http://server.ip:631)
browser: Failed to connect.  Though the site seems valid, firefox was unable to establish connection.[/FONT]

Also, I tried to install the printer on my MacBook.  The MacOS Printer installer wizard seemed to succeed at detecting the printer and choosing a matching driver for it.  But when I try to print:
[FONT=Courier New]MacBook: Network Printer "printername" is busy.  Will retry "later" [FONT=Microsoft Sans Serif](it never succeeds).[/FONT][/FONT]  (MacOS Trouleshooting wizard can not repair.)

Seems like some sort of network configuration problem.  I find that odd because I can successfully use port 80 (web page) and port 22 (ssh/scp) from any computer I make available in ufw.  I have a ufw allow rule for port 631 with the same syntax as what works for ports 80 and 22.  So I am thinking maybe problem with a network setting in a cups config somewhere?

---

### Post by albinootje on 2009-05-17
> **ktritty said:**
> 
But, when I try to access from a remote computer
[FONT=Courier New]web browser: [http://server.ip:631](http://server.ip:631)
browser: Failed to connect. 

Cool that you got one step further! :)
I've just enabled remote browsing for cups over my local network, see the working /etc/cups/cupsd.conf attached as a dot text file.

---

### Post by ktritty on 2009-05-18
Thank You very much.  The config file works better.  I'd say we are 99% of the way home!  Now I can use the web admin tool from my MacBook and iMac.  I was able to set up printer for internet sharing and also set as default printer, so now I see the Printer ready when I type

$```
 lpq
Brother_HL-5140 is ready
```

It succeeds at printing a test page from the web utility, but, I still cannot get it to work when I try to print from other computers on my LAN.

It is a USB Printer (non-network ready) so I can only hook it up to the server via the USB port.  It is installed as device USB #1.

Any ideas when I set up as a new Printer in my MacBook if I should use LPD or IPP?  I've tried both but neither seem to want to work.  Any thoughts if maybe there is a username problem here?  Should I modify cupsd.conf to accept jobs from any user?  If so, how do I do this?  Thanks.

---

### Post by albinootje on 2009-05-18
> **ktritty said:**
> I was able to set up printer for internet sharing and also set as default printer, so now I see the Printer ready when I type

$```
 lpq
Brother_HL-5140 is ready
```

Good :)
> 
Any ideas when I set up as a new Printer in my MacBook if I should use LPD or IPP?  

You should use ipp. The address would be something like : ipp://ip-address-server/printers/brother_hl-5140
And it's unlikely that you have to change anything else on the server, it's now all a matter of the configuration on the clients.

---

### Post by ktritty on 2009-05-18
I can print when I'm on the same LAN segment as the server, but not from the other segment of my network.  There is one router in between.  When I am hooked up to the LAN, which I cannot normally do, the MacBook detects it automatically as a Bonjour Shared Printer.  When I am in the normal spot (one router away) I cannot get the IPP to work at all.  It says the address you gave me is invalid.  Yet ssh, http, ftp, all work fine from the other side of the router, not to mention the cups web utility on port 631.  I think that is odd.  I have everything working great except the printer.

There should be no firewall on the router, just NAT.  Normally all of my computers are hooked up to the same LAN, but the other side of the router from the server.  Ideas?

---

