---
title: "local printer sharing"
date: 2005-09-03
forum: Networking &amp; Wireless
---

### Post by jrev on 2005-09-03
Hi all,

I connected my 2 PC's both on ubuntu hoary 5.04 with a cable on the Ethernet socket

I already share the internet connection and some files located on the NSF server
what should I add & how to configure in order to be able to use the server's printer from the other PC ? 

Thanks for your detailed answer ( I am still a beginner )

---

### Post by s_p_a_r_k_y on 2005-09-03
OK you will probably want to setup cups. I just set up CUPS on one computer with 2 printers attached to it so the other computers in my dorm room could all print to it. CUPS is not easy to install/configure, especially the one that comes with ubuntu as the webinterface is crippled a bit. try going to [http://localhost:631](http://localhost:631) on the computer which has the printers connected. also read up on some cups documentation,t here is plenty to be found on the net.

---

### Post by jrev on 2005-09-05
I think it is time to make an up-to-date wiki article with the step by step configuration of  the cupsd.conf file changes to be made for a lan printer 

but first I must check my cupsd.conf file and make it work ...

I feel lost in : [http://localhost:631/](http://localhost:631/)

and I still need help 

Thanks

---

### Post by s_p_a_r_k_y on 2005-09-05
does localhost:631 give you the cups administration page? If so, click on printers, there you can add a printer. Or if you add it thru System->Administration->Printing it'll add it on the website as well I believe. To let other printers print to it, edit the cupsd.conf file and look for Location /printers
and make it allow,deny and Allow FROM IPADDRESS

play around with the settings, if your on a local lan, then just allow from all. You can then setup the other Linux computers to print to [http://CUPSSERVERIP:631/printers/PrinterName](http://CUPSSERVERIP:631/printers/PrinterName)

---

### Post by jrev on 2005-09-06
Thanks for your comments :

"To let other printers print to it, edit the cupsd.conf file and look for Location /printers
and make it allow,deny and Allow FROM IPADDRESS"

could you give me the details to add my client 192.168.10.2 in order to be able to print through the server 192.168.10.1 ?

I am still a newborn to ubuntu and cups & I cannot see any reason for this cups site you mentionned (a little bit lost in that world)  

thanks to let me know the practical use of it for my particular case 
I can send you my actual cupsd.conf 

in fact I can see now the print message going through the printing manager of the client (before it was stuck there) and the printer is going through its cleaning job before the printing that doesn't occur at all 

must still be a trick to put forward ...

---

### Post by jrev on 2005-09-06
Everything works fine now

I'll save my new /etc/cups/cupsd.conf 
[B]
_who is going to update the wiki now ?_[/B]

I couldn't find the sharing printer description I was looking for anyway...

---

### Post by jrev on 2005-09-17
I revised the wiki page concerning the printer :

[http://wiki.ubuntu-fr.org/applications/partage_d_imprimante](http://wiki.ubuntu-fr.org/applications/partage_d_imprimante)

thank you for your help...

---

### Post by mark on 2005-09-17
I'm also trying to share a printer.  Mine is an HP LaserJet 6P, connected to my desktop via the parallel port.  All Ubuntu versions (Warty/Hoary/Breezy) see it on my desktop, but not from my laptop, which is connected via a NetGear RP-614 router.

In my case, I think it's simply ignorance - I can't find anything definitive about connecting to a network printer via IPP, CUPS or any other method.

I know it can work - I've got WinXP-toWinXP network printing.  I can even boot WinXP on the desktop and print from Ubuntu on the laptop, using Samba.

Unfortunately, the [http://localhost:631/](http://localhost:631/) address doesn't work - it's been blocked and refers me back to the System/Administration/Printing utility.

Any ideas?

---

