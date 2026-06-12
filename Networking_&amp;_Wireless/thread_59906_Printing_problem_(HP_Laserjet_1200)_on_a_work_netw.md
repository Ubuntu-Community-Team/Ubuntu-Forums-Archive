---
title: "Printing problem (HP Laserjet 1200) on a work network"
date: 2005-08-25
forum: Networking &amp; Wireless
---

### Post by borris on 2005-08-25
Hello,

I have set up a dual boot ubuntu/WinXP on my laptop at work.  There is a large network.  My windows computer can print to a printer, which is attached to print server.  I know the server's ip address, and I can successfully ping that server.  I have tried several routes in both Gnome and KDE to set up the printer using the printing wizards, including setting up a SMB (windows) printer, a CUPS printer.  

I have now also tried a few different drivers for the printer (HP Laserjet 1200) including the recommended driver.  

I can browse the network to see the printer server, but it won't let my ubuntu see the printer when browsing (something I can do from WinXP).  

When I send a test to the printer or print from any program, it says "test successfully sent to printer", but nothing happens... it remains "Processing..." for ever.

So I have:
ip of server
name of printer
the printer is not in a workgroup
the printer is not attached to a windows computer as a share
printer type 

Does anybody have any thoughts.  I have followed a whole bunch of previous posts already and none seems to work.

thanks

---

### Post by s_p_a_r_k_y on 2005-08-25
you need to go to System->Administration->Printing and set it up from there. When you mean print server I'm assuming its a "Windows Shared Printer".

If thats the case, you want to use Netork Printer, then Windows Printer

hope it works. HP printing support is great under Linux

---

### Post by borris on 2005-08-25
Tried that, and there are so many things that could go wrong, I am not sure where to start.  For example, is the host case sensitive (I've tried all cases, ALLCAPS, lowercase, Sentence case), drivers, which is the host, the network, the printer... should I use the IP address or the server name.  In any case, I still can't ever browse to the actual printer.  I can browse to the Windows Server that hosts the printer, but not beyond that.

borris

---

### Post by s_p_a_r_k_y on 2005-08-25
when you say print server, what do you mean? Is it hooked up to a windows box and shared? or does it have a jetdirect box? or..?

---

### Post by borris on 2005-08-26
I believe it has a jetdirect box.  I is not attached to a computer with a share.  i.e., the ethernet cable is plugged from the wall to the HP jetdirect box (175 jetdirect).

Does this change things?

Eliot

---

### Post by s_p_a_r_k_y on 2005-08-26
Hi borris, jet direct is usualy quite easy to setup. 

Select Network Printer, HP Jet Direct then type in the host name and port. I think our scan of the ports showed the 515 port open, eventhough the default jet direct is 9100. Try it. Also if you type in the IP addy of the jetdirect box then you should get to its web interface and be able to configure a few settings.

edit
we did not scan the print server. I was mistaken I had someone do that in another tread. try

 nmap IPaddress

and see if port 9100 is open on the jetdirect boxen

---

### Post by borris on 2005-08-26
S p a r k y

So whatever you said inspired greatness.  In the Add printer wizard, I had only tried the HPJetdirect once or twice, always writing the printer server/printer.  This time, I tried just the printer name, nothing else, with the default port 9100.  I got a connection to the printer, but it printed error messages.  I changed to the hpjds driver (or whatever the second printer driver is in the list... not the recommended pxlmono), and IT WORKED!!! 

 Happily printing at work now...  :-P   

Thanks,

---

### Post by s_p_a_r_k_y on 2005-08-26
Good for you : )

Recommend HP printers to friends as right now they seem to have the best supported products for Linux

---

