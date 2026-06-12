---
title: "Linksys WPS54G Wireless Print Server with HP LaserJet 1320 on Ubuntu"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by pete83 on 2007-08-03
Hi, I recently bought a Linksys WPS54G Wireless print server, to use with my HP LaserJet 1320.

In the end it works now under Ubuntu Linux, but there were a few bumps (including perhaps a Microsoft conspiracy) along the way I thought I might share.

My WPS54G was a V.2 version, and it came with firmware 6050 installed (even though the latest possible firmware to download is 6049).

First, after opening the box I connected the print server to the router BY ETHERNET CABLE to do the setup. After setting it up, you can unhook the ethernet cable, but keep it connected for setting it up. Luckily, the WPS54G comes with an extra ethernet cable if you need it.

Next, I turned it on and had to try to figure out what ip address the printserver got. On my network, my router is configured to give out address starting at 192.168.1.100, and going up. I used the program Wireshark (run it with root sudo privileges) to sniff the broadcasted traffic on my network, and sure enough, there was a device at 192.168.1.102 announcing that it had a print server. So, with that ip address in mind, I took myself to the web interface.

I decided to configure the print server using the handy web interface. **This is where I hit a really terrible, immoral conspiracy:** When I pointed Firefox to the address [http://192.168.1.102](http://192.168.1.102) , I was prompted for my username and password. By default, the username is blank and the password is "admin." After entering the password, I was welcomed by the first page of the web interface. However, it became clear that I could not access any of the other pages, since the print server was crashed by my accessing the web interface in Firefox. I tried Konqueror too, but accessing the print server's web interface with Konqueror also crashed the entire print server. After trying this for a while, I tried accessing the web interface using Internet Explorer 5.5, and it worked perfectly. I tried this a few times to make sure, and it was a consistent result that only Internet Explorer 5.5 would cause the print server not to crash.

This is the conspiracy. But do not worry, you do not need to use Internet Explorer. So, I tried loading Konqueror as my web browser, and in the Konqueror settings, I set the 
"browser identification" to identify as "Internet Explorer 5.5 in Windows 2000" when visiting the site [http://192.168.1.102](http://192.168.1.102) ... and sure enough, now the web interface works perfectly in Konqueror, even though Konqueror used to crash the print server when it was identifying as Konqueror.

**In other words, the Linksys WPS54G seems to be hard-wired to crash on purpose when a browser other than Internet Explorer 5.5 (or maybe 5 or 6 too, I didn't try them) tries to access its web interface. You must tell your browser, such as Konqueror, to claim to be Internet Explorer, and then the Web Interface will work perfectly.**

In the web interface, the first thing you should do is change the password to something other than "admin." Next, I selected the "wireless" tab to configure the wireless network. On the "security" tab I selected my network with WPA-TKIP security, and I entered my password and saved those settings, and then I unplugged the ethernet cable from the printserver. I then unplugged the power from the printerserver, and waited a few seconds, and then plugged it back in. Lo and behold, it worked wirelessly!

So right at this point, my printserver was getting the ip address of 192.168.1.102 assigned to it by my router. But I wanted a more stable ip address, so I can set up a printer and always find the printserver in the same place. I needed to set up a static ip address for the printserver. So I went back into the printerserver's web interface, and I clicked the "Status" tab to see what the "Subnet Mask" and "Gateway Address" were supposed to be. In my particular case, it looked like this:

```

Subnet Mask:255.255.255.0 
Gateway Address:192.168.1.1
 
```

Armed with that knowledge, I then clicked the tab called protocol>>TCP/IP, and I entered this:

```

Use the Following IP Address: 
IP Address 192.168.1.44
Subnet Mask 255.255.255.0
Gateway 192.168.1.1

```

You will notice that I just copied the "Subnet Mask" and "gateway" entries from the "status" tab, but I made up my own unique ip address for the printserver. I chose 192.168.1.44, because my Linksys router is set up to assign addresses from 192.168.1.100 to 192.168.1.149... So 192.168.1.44 will never get taken by anybody else. However, since the subnet mask is 255.255.255.0, I think it is essential that whatever ip address you pick for your printserver, the first three parts will have to be "192.168.1.xxx" ... Anyways, I chose 44. So after saving that, my printserver should now be found at 192.168.1.44 ... I unplugged the printserver for a few seconds, and then plugged it back in

But now the real test, to add a printer!

So in Ubuntu I went to System>>Administration>>Printing, and then I went to "New Printer." I selected "Printer Type: Network Printer" of the "IPP" type. Since my printserver's IP address was 192.168.1.44, I entered in the following URI:

```
ipp://192.168.1.44:631/ipp/P1
```

Then I just selected the appropriate manufacturer and printer driver for my actual printer (in this case an HP LaserJet 1320), and printed a test page. It worked perfectly!

I hope this helps somebody install this print server in Linux, at some point.

---

### Post by lobner on 2007-08-20
Nice - thank you for that walkthrough. I am looking too buy a wireless print server of some sort, and good with a statement saying that this Linksys product works under Ubuntu.

And uses the old driver and everything.

P.S. The issue with the user agent requirement should be able to be fixed in firefox with the [User Agent Switcher](https://addons.mozilla.org/en-US/firefox/addon/59)-extension.

---

### Post by johncudd on 2007-09-25
Thanks man. This REALLY helped me out. It worked just fine. now I've got a WIRELESS PRINTER!!! Thanks.

---

### Post by DoubleR on 2007-10-21
Very helpful indeed.  I installed Ubuntu 7.10 (Gutsy Gibbon) on my laptop yesterday.  Today I set up the print server to use the wireless instead of the Ethernet cable (So I could move the printer to a more convenient location). I installed the new printer and I am printing away in Ubuntu.  The printer is a HP Photosmart 7760.  I found this much easier than I expected.  In fact I had harder time with Vista for when I adopted early.  One comment that may help others.

> **pete83 said:**
> 
So in Ubuntu I went to System>>Administration>>Printing, and then I went to "New Printer." I selected "Printer Type: Network Printer" of the "IPP" type. Since my print server's IP address was 192.168.1.44, I entered in the following URI:

```
ipp://192.168.1.44:631/ipp/P1
```
.


 I did not see "Printer Type: Network Printer" as an available option.  So I picked "other" and then entered in URI.

PS: User agent will not me to use of Firefox to control or set up the print server.  I was able to use a XP box with MSIE 6.0 on it OK.  So it does not have to be 5.5.  When I tried MSIE  7 on an VISTA box I got no where.  I then found the user agent on the XP box by typing javascript:agent(navigator.userAgent) in the address bar and used the result, Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)  to set up a custom user agent in User Agent Switcher for Firefox add on. I selected it and tried again.  The print server still locks up following sign-in as explained in the first post.  I am not using Kubuntu so I don't have conqueror installed to check that out. Lastly, I am updated to the 6049 firmware.

---

### Post by wieman01 on 2007-11-28
Thanks, man. This will help a lot. I plan to buy myself a WPSM54G and I believe the setup is quite the same.

_**EDIT:**_
Awesome, really really awesome. I'll post back if I have tested the device myself. The only drawback is that the WPS54G does not support WPA2 (AES) whereas the WPSM54G does. Therefore I'll go for the WPSM54G although I don't really need Multifunction Printer Support. But better security is worth a few extra bucks.

---

### Post by zzandeamos on 2007-11-29
YES!!!
Thanks guys (and/or gals)  I got my wps54g woking with two xp machines and one ubuntu.
You were very helpful.
Thanks again
zz andeamos

---

### Post by tbedolla on 2007-11-30
Pete,

Your post is just what I'm looking for, I believe. I can print directly from the laptop to the printer...but no luck on the wireless. In your post you use the URI:

ipp://192.168.0.11:631/ipp/P1

I've changed the IP to represent my own, however, I'm not clear on where the ":631" comes in? Is this a static port? Any help is appreciated and thanks in advance for your time.

Regards,

Toma

---

### Post by wieman01 on 2007-12-01
I tried to install & configure the WPS54G yesterday and I gave up after long 2 hours. What a piece of junk... I knew that I would not support WPA2 (AES), so no issue at all. But getting the wireless function to work and making the device associate with my router turned out to be a nightmare. 

After messing around with it for 2 hours I eventually gave up and I will return the device and get myself another brand. It's really silly, I thought Linksys had learned their lesson. This is the 3rd frustrating experience with a Linksys device and that's it, I am over it, I'll no more buy anything from Linksys. Their hardware is such a waste of time. Not because the hardware is bad per se, but their firmware (in general) really sucks.

Sorry for ranting. But hardware you are unable to set up in less than 1 hours as an experienced user is simply not worth it. Shame on Linksys... once again.

_**EDIT:**_
One thing that annoyed me most was that the thing refuses to cooperate with FIrefox or Konqueror. The router crashed after the first welcome screen unless you access it with Internet Explorer. How ridiculous is that?!

I even used Windows and their installation CD to configure it just in case you want to know.

---

### Post by dodgerFanLinuxDude on 2007-12-05
You said: 

>  So in Ubuntu I went to System>>Administration>>Printing, and then I went to "New Printer." I selected "Printer Type: Network Printer" of the "IPP" type. Since my printserver's IP address was 192.168.1.44, I entered in the following URI:

```
ipp://192.168.1.44:631/ipp/P1
``` 

What is the "P1" in your URI? cause my printer conencts to the printserver through a USB port....please help...

---

### Post by jdmelton on 2008-01-02
Thanks for this information. I have a WPS54G with firmware version 6045. It does not seem to have the problem with crashes. I used Firefox 2.0.0.11 on a system76 laptop and Ubuntu 7.10 to configure it.

As described in the first post, I tried to use System -> Administration -> Printing -> New Printer -> Internet Printing Protocol (ipp). That did not work for me. I kept getting error messages that no queues were found.

Next, as another poster above wrote, I used the New Printer -> Other. Where it asks for the  device URI, I used:

ipp://10.1.1.16/ipp/P1

Then I selected my printer, an HP DeskJet 950C.

The printer was added under local printers.

The test page printed.

Due to other issues on my home network, I have returned to the wired ethernet. The printing still works. I did not use the port number after the IP address. I also use a mix of static and DHCP addresses, so I have a hosts and networks file on my computers. I changed the IP address above to the alias in the hosts file. For me, it looks like this:
ipp://printer1/ipp/P1 and my hosts file has 10.1.1.16 printer1

While I am not using the wireless mode at the moment, the setup hints given by this thread worked for me using either wireless or wired.

Thanks again to the originator of this thread.

---

### Post by mensenjh on 2008-02-20
Kudos to this post. After fiddling around with the IP address and my server my first test page got spit out just a minute ago. For setting up the printer I used [http://localhost:631](http://localhost:631) (CUPS Home) but it's all basically the same. Thanks a lot!

---

### Post by hillel213 on 2008-03-26
It was very difficult to setup this Linksys print server; however, it can be done!

There is a great post I would refer you to: [B]
[http://ubuntuforums.org/showthread.php?t=516747]("http://ubuntuforums.org/showthread.php?t=516747")[/B]

However, there is one point that is not clear...

When you input the ipp://[ip address]:631/ipp/P1, for example, ipp://192.168.1.44:631/ipp/P1, what is the 631?

The 631 is the open port.  So, the format is:  ipp://[ip address]:[port]/ipp/P1

You can find the port by typing the following in the terminal:

**sudo nmap [static ip address]**

for example, sudo nmap 192.168.13.254

When you get the result look for the http row.  My port number was 80 instead of 631,



if this does not work, you will need to install nmap prior to the above command...

**sudo apt-get install nmap**


In summary,

1. Read the above post and get the wireless print server to give you a static ip address
2. Add a printer and enter the appropriate ** ipp://[ip address]:[port]/ipp/P1 ** in the Device URI field

Good luck!

---

### Post by Unc0 on 2008-04-01
> **DoubleR said:**
> Very helpful indeed.  I installed Ubuntu 7.10 (Gutsy Gibbon) on my laptop yesterday.  Today I set up the print server to use the wireless instead of the Ethernet cable (So I could move the printer to a more convenient location). I installed the new printer and I am printing away in Ubuntu.  The printer is a HP Photosmart 7760.  I found this much easier than I expected.  In fact I had harder time with Vista for when I adopted early.  One comment that may help others.

```
ipp://192.168.1.44:631/ipp/P
```


 I did not see "Printer Type: Network Printer" as an available option.  So I picked "other" and then entered in URI.
.

i got a Canon PIXMA iP5200 working with the Linksys WPS54G Wireless Print Server in Ubuntu 7.10 (Gutsy Gibbon) as well. i also had to select "other" and then entered the URL in the printer setup.

i too had problems with Firefox, but as per original post, Konqueror identifying as IE 5.5 on Win2K to the Print Server's IP address did the trick.

thanks for the thread, Pete83. it really helped a lot.

---

### Post by Rich43 on 2008-06-06
Thanks, this helped alot. Printer works fine!

---

