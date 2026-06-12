---
title: "Problem accessing Printer connected to the network.."
date: 2005-08-25
forum: Networking &amp; Wireless
---

### Post by arunsub on 2005-08-25
I have installed Airlink101 print server. It's connected to my wireless router. How do I install it in Ubuntu? If I select the network printer option, then should i select CUPS? If i select CUPS, then i have to enter the URL. I entered the print server's IP address in the URL, but when i print a test page it doesn't print. Can someone tell me how to configure the network printer?

Thanks.

---

### Post by s_p_a_r_k_y on 2005-08-25
often network printers work over the jetdirect HP protocol. Give that a try. Also can you run an nmap of the server for us?

nmap print_server_ip

if it says command not found, then install nmap

---

### Post by arunsub on 2005-08-25
This is what i got when i ran nmap print_server_ip
Interesting ports on ip address:
(The 1658 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
21/tcp   open  ftp
80/tcp   open  http
139/tcp  open  netbios-ssn
515/tcp  open  printer
9111/tcp open  DragonIDSConsole

Nmap run completed -- 1 IP address (1 host up) scanned in 12.078 seconds

---

### Post by s_p_a_r_k_y on 2005-08-25
um you may want to add the cups url as ipaddress_of_printer:515

as it seems that the 515 will be your printer port? I'm not sure have never set one up. Can you read through the documentation to see how to add it to windows and see what they tell you to do if you are adding it as a network printer?

---

### Post by arunsub on 2005-08-26
[QUOTE=s_p_a_r_k_y]um you may want to add the cups url as ipaddress_of_printer:515

as it seems that the 515 will be your printer port? I'm not sure have never set one up. Can you read through the documentation to see how to add it to windows and see what they tell you to do if you are adding it as a network printer?[/QUOTE]
I'll try that. It is comparatively simple in Windows since I got installation CD for Windows. I install the driver etc and then select the print server name and assign my printer to that print server through the software they provided. The package says Linux as one of the OSes supported, but there's no manual. I'll try the option you said when I go home. Thanks for the help.

---

### Post by s_p_a_r_k_y on 2005-08-26
Things tend to be "easier" in windows bc vendors tend to release software specific for it. With Linux ya end up having to do a bit of the setup yourself, but you also learn a few things while your doing it which help in your troubleshooting skills for when things go wrong...Windows admins tend to not know what to do when they can't access a printer or the such...we have nmap and ethereal and other fun tools to help solve networking woes.

Can you see what port windows is using to print to? Usually if you go to Start->Printers and faxes (control panel) and go to properties of your printer you can go to one of the tabs where it has connections. Then ya click the one wiht the checkmark and hit configure (someone correct me I'm doing this from memory)? It should give the IP addy and port its using

---

### Post by arunsub on 2005-08-29
sorry for the late reply. I was little busy. I checked as you said in the windows. It's showing the port as \\PS-576903\PS-576903-U3. 
The port name once came when i select Places - Network servers. I couldn't get that after. I get only Windows Network. Nothing else.
I tried different options in the printer configurations also like CUPS, HP something etc.

---

### Post by s_p_a_r_k_y on 2005-08-30
[QUOTE=arunsub]sorry for the late reply. I was little busy. I checked as you said in the windows. It's showing the port as \\PS-576903\PS-576903-U3. 
The port name once came when i select Places - Network servers. I couldn't get that after. I get only Windows Network. Nothing else.
I tried different options in the printer configurations also like CUPS, HP something etc.[/QUOTE]

Ok thats a windows share so you'll want to use the SMB protocol with server name PS-576903 and printer share PS-576903-U3
don't know if you will need a username/password

---

### Post by arunsub on 2005-08-30
[QUOTE=s_p_a_r_k_y]Ok thats a windows share so you'll want to use the SMB protocol with server name PS-576903 and printer share PS-576903-U3
don't know if you will need a username/password[/QUOTE]
How do i do that? I'm not a Linux Techie, so please help me.

---

### Post by s_p_a_r_k_y on 2005-08-31
just like you would have added the other, system->administartion->printing, new printer
then select network printing and Windows Share (SMB).

then type in your info.

---

### Post by arunsub on 2005-08-31
[QUOTE=s_p_a_r_k_y]just like you would have added the other, system->administartion->printing, new printer
then select network printing and Windows Share (SMB).

then type in your info.[/QUOTE]
I'll try that and get back to you.

---

### Post by arunsub on 2005-08-31
[QUOTE=s_p_a_r_k_y]Ok thats a windows share so you'll want to use the SMB protocol with server name PS-576903 and printer share PS-576903-U3
don't know if you will need a username/password[/QUOTE]
It has host, printer, username, password when i select Windows SMB. It doesn't have server name and printer share. I tried different option in that and they didnt work.

---

### Post by arunsub on 2005-08-31
[QUOTE=arunsub]It has host, printer, username, password when i select Windows SMB. It doesn't have server name and printer share. I tried different option in that and they didnt work.[/QUOTE]
Edit: Firestarter blocked some connection. I changed it to allow those. I then closed Firestarter and still no luck.

---

### Post by arunsub on 2005-09-01
This is the reply I got from Airlink support:

Unfortunately, we don't provide technical assistance for linux.

Check the documentation for your distro and find out how to set up LPR
printing over tcpip.  That is how you will want to configure it.

---

### Post by s_p_a_r_k_y on 2005-09-02
host = server, printer share = printer

---

### Post by arunsub on 2005-09-07
Sorry, I was on vacation and came back today. I'll give it a try when i go home today.

---

### Post by assan on 2005-09-07
[QUOTE=s_p_a_r_k_y]often network printers work over the jetdirect HP protocol. Give that a try. Also can you run an nmap of the server for us?

nmap print_server_ip

if it says command not found, then install nmap[/QUOTE]
==================================

Hi,

I have similar problem. I can't access my OKI network printer. I know IP but it doesn't work.
So i run nmpa and there is an answer:

Starting nmap 3.75 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-09-07 17:56 CEST
Failed to resolve given hostname/IP: print_server_ip.  Note that you can't use '/mask' AND '[1-4,7,100-]' style IP ranges
WARNING: No targets were specified, so 0 hosts scanned.
Nmap run completed -- 0 IP addresses (0 hosts up) scanned in 0.399 seconds

What to do next?

---

### Post by s_p_a_r_k_y on 2005-09-07
assan did you actually use the right IP address? From your nmap output it seems like it never connected correctly

---

### Post by assan on 2005-09-07
[QUOTE=s_p_a_r_k_y]assan did you actually use the right IP address? From your nmap output it seems like it never connected correctly[/QUOTE]

Well, my printer answer on the same ip by ping. So someting is wrong with CUPS setup. What is you suggestion?

PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_seq=1 ttl=255 time=11.7 ms
64 bytes from 192.168.1.100: icmp_seq=2 ttl=255 time=3.19 ms
64 bytes from 192.168.1.100: icmp_seq=3 ttl=255 time=4.91 ms

---

### Post by s_p_a_r_k_y on 2005-09-08
it seems like you were pinging your own computer? Whats your IP and what is the IP of the printer?

---

### Post by assan on 2005-09-08
[QUOTE=s_p_a_r_k_y]it seems like you were pinging your own computer? Whats your IP and what is the IP of the printer?[/QUOTE]

It is ping of my printer. My laptop have different ip.
Printer is installed in windows in other laptop under this ip and it works.
I have linksys router, one desktop, two laptops (wireless) and two oki network printers.
Everything was working under windows so it shoul work under ubuntu.
Definetely it was ip of my printer. I checked config on display of printer.
Do you have any idea how to check what  is wrong?
Another test?
I have ppd file to setup this printer.

---

### Post by s_p_a_r_k_y on 2005-09-08
[QUOTE=assan]Well, my printer answer on the same ip by ping. So someting is wrong with CUPS setup. What is you suggestion?

PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_seq=1 ttl=255 time=11.7 ms
64 bytes from 192.168.1.100: icmp_seq=2 ttl=255 time=3.19 ms
64 bytes from 192.168.1.100: icmp_seq=3 ttl=255 time=4.91 ms[/QUOTE]
it says that you are pinging 192.168.1.100 from 192.168.1.100 which means you are pinging it from the machine you are one.

So what is the IP of your printer? do you have IRC or want to do this on AIM?

---

### Post by assan on 2005-09-10
Finally OKI B4350 Network printer is working

Finally I have managed to get my OKI B4350 network printer to work. It took me few weeks to do it. But main problem was lack of write ppd file on local page of OKI.
Many thanks to **s_p_a_r_k_y**, he managed to find out network interface of printer.
It should be [http://xxx.xxx.xxx.xxx:631/ipp/lp](http://xxx.xxx.xxx.xxx:631/ipp/lp), where xxx are printer's IP number. It can be set via printers panel (follow instruction).
You should see panel of B4350 when you will open that address in webbrowser.

Now PPD file (printer drivers for CUPS). It is tricky!
OKI have two ppd files for this printer, because there are two  types of this printer one with postscript and second without postscript.

Depending on national page of oki printing solution they have two versions or just one driver for postscript.

For PCL version B4350 is           ok4300pcl.ppd (the same as for B4300)
when you will view this file you will find in the beginning:
Printer Description File for OKI B4300/B4350 (PS)

**For Postscript version B4350 is  ok4350u1.ppd**

So first you have to obtain from OKI's page appropriate ppd file.

Then you open System==>Administration==>Printing

Add new printer , network printer (CUPS Printer IPP) you put in address  [http://xxx.xxx.xxx.xxx:631/ipp/lp](http://xxx.xxx.xxx.xxx:631/ipp/lp)

Install Driver indicate ppd file and that's it.
It should work.

I had small problem after installation of drivers, when adding new printer drivers where not visible on write place under OKIDATA, but after restart everything was ok, drivers on good place.
I hope my story will help you. :grin:
Thanks to s_p_a_r_k_y  again

---

### Post by arunsub on 2005-09-12
The IP didn't work for me for couple of days, so i reconnected the printer directly. I'll connect it to network again in couple of days and see if i can fix it.

---

### Post by assan on 2005-09-12
[QUOTE=arunsub]The IP didn't work for me for couple of days, so i reconnected the printer directly. I'll connect it to network again in couple of days and see if i can fix it.[/QUOTE]

So you managed you printer to work or not?
It started to work and after some time stopped?
My hint is listen to s_p_a_r_k_y.

---

### Post by s_p_a_r_k_y on 2005-09-12
assan's advice is good >  listen to sparky  : )

---

### Post by arunsub on 2005-09-12
[QUOTE=assan]So you managed you printer to work or not?
It started to work and after some time stopped?
My hint is listen to s_p_a_r_k_y.[/QUOTE]
It's connected directly now. I'll try to reconnect the print server as soon as i get time and ofcourse I'll contact Sparky to get it work.  :)

---

### Post by arunsub on 2005-09-12
Ok. I connected the printer back to the print server. If i enter the print server ip in Windows, i get the configuration page. If i enter the same in Ubuntu, it says page not found. I tried ping and got the following:
ping 192.168.2.254
PING 192.168.2.254 (192.168.2.254) 56(84) bytes of data.
64 bytes from 192.168.2.254: icmp_seq=1 ttl=255 time=5.80 ms
64 bytes from 192.168.2.254: icmp_seq=2 ttl=255 time=2.76 ms
64 bytes from 192.168.2.254: icmp_seq=3 ttl=255 time=2.73 ms
64 bytes from 192.168.2.254: icmp_seq=4 ttl=255 time=3.11 ms
64 bytes from 192.168.2.254: icmp_seq=5 ttl=255 time=2.76 ms

I tried namp and got the following.
nmap 192.168.2.254

Starting nmap 3.75 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-09-12 17:24 CDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0Nmap run completed -- 1 IP address (0 hosts up) scanned in 4.036 seconds

It works from WIndows.

---

### Post by assan on 2005-09-12
[QUOTE=arunsub]Ok. I connected the printer back to the print server. If i enter the print server ip in Windows, i get the configuration page. If i enter the same in Ubuntu, it says page not found. I tried ping and got the following:
ping 192.168.2.254
PING 192.168.2.254 (192.168.2.254) 56(84) bytes of data.
64 bytes from 192.168.2.254: icmp_seq=1 ttl=255 time=5.80 ms
64 bytes from 192.168.2.254: icmp_seq=2 ttl=255 time=2.76 ms
64 bytes from 192.168.2.254: icmp_seq=3 ttl=255 time=2.73 ms
64 bytes from 192.168.2.254: icmp_seq=4 ttl=255 time=3.11 ms
64 bytes from 192.168.2.254: icmp_seq=5 ttl=255 time=2.76 ms

I tried namp and got the following.
nmap 192.168.2.254

Starting nmap 3.75 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-09-12 17:24 CDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0Nmap run completed -- 1 IP address (0 hosts up) scanned in 4.036 seconds

It works from WIndows.[/QUOTE]

Did You tryied 192.168.2.254:631 ?
Do you have some kind of firewall?

**One more thing. Please write which one of Airlin 101 print server do you have? There are 4 types!**

Try to use galeon o dillo, another webbrowser.

One more idea, did you changed IP of you computer in Linux? Different IP then in Windows?

---

### Post by arunsub on 2005-09-12
[QUOTE=assan]Did You tryied 192.168.2.254:631 ?
Do you have some kind of firewall?

**One more thing. Please write which one of Airlin 101 print server do you have? There are 4 types!**

Try to use galeon o dillo, another webbrowser.

One more idea, did you changed IP of you computer in Linux? Different IP then in Windows?[/QUOTE]
If i give 192.168.2.254:515 I got a message in firefox saying access to port number given has been disabled for security reason.
if i give just 192.168.2.254 i get page not found.
I tried with Mozilla browser also (not firefox).
My print server is Airlink 101 3 port print server (APSUSB2) and my printer is Epson Stylus C80.

---

### Post by arunsub on 2005-09-12
I use Firestarter as firewall. I disabled it when i tried those.

---

### Post by arunsub on 2005-09-13
I could access the print server ip address earlier from Ubuntu Firefox when i started this thread. I couldn't now. I moved to K7 kernel and I'm not sure if i moved before that or after that. I also got a kernel version upgrade couple of days back. I don't know if any of those is creating problems in accessing the print server ip address.

---

### Post by arunsub on 2005-09-13
I somehow did something and the print server ip works now. I then ran nmap and got the following result
 nmap 192.168.2.254

Starting nmap 3.75 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-09-13 20:53 CDT
Interesting ports on 192.168.2.254:
(The 1657 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
21/tcp   open  ftp
23/tcp   open  telnet
80/tcp   open  http
139/tcp  open  netbios-ssn
515/tcp  open  printer
9111/tcp open  DragonIDSConsole

I created new printer with cups and [http://192.168.2.254:515/ipp/lp](http://192.168.2.254:515/ipp/lp). I printed a test page and nothing got printer.

---

### Post by s_p_a_r_k_y on 2005-09-14
[QUOTE=arunsub]I somehow did something and the print server ip works now. I then ran nmap and got the following result
 nmap 192.168.2.254

Starting nmap 3.75 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-09-13 20:53 CDT
Interesting ports on 192.168.2.254:
(The 1657 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
21/tcp   open  ftp
23/tcp   open  telnet
80/tcp   open  http
139/tcp  open  netbios-ssn
515/tcp  open  printer
9111/tcp open  DragonIDSConsole

I created new printer with cups and [http://192.168.2.254:515/ipp/lp](http://192.168.2.254:515/ipp/lp). I printed a test page and nothing got printer.[/QUOTE]
 if you go to the website of the print server, then you should be able to see a few things. Its weird that port 631 and 9100 aren't open on it

---

### Post by arunsub on 2005-09-14
I checked their website and couldn't find anything regarding this. If you see the product description, Linux is compatible and if you see the printer supported, my printer (Epson Stylus C80) is supported. I couldn't find anything more. assan wrote something about indicating ppd file etc. What is that and how do i do that? Is that something that's stopping me from printing? Again, I was unable to find any ppd file in Epson website.

---

### Post by assan on 2005-10-09
[QUOTE=arunsub]I checked their website and couldn't find anything regarding this. If you see the product description, Linux is compatible and if you see the printer supported, my printer (Epson Stylus C80) is supported. I couldn't find anything more. assan wrote something about indicating ppd file etc. What is that and how do i do that? Is that something that's stopping me from printing? Again, I was unable to find any ppd file in Epson website.[/QUOTE]

Please chack page: [http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C80](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C80)
Maybe with help by Sparky you will be able to print. 
Your printer is working perfectly with linux according to linuxprinting.org
There is epson thread on forum. I hope it will help

assan

---

### Post by arunsub on 2005-10-11
[QUOTE=assan]Please chack page: [http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C80](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C80)
Maybe with help by Sparky you will be able to print. 
Your printer is working perfectly with linux according to linuxprinting.org
There is epson thread on forum. I hope it will help

assan[/QUOTE]
Thanks Assan for the link. I got busy with some rearranging work in my home. I also installed a new SATA drive and I'm going to order a new case for my PC. I didn't get time to sit and find the problem. I told Sparky that I'll contact him whenever I'm ready to do it, but i didn't get time to do that. I'll give it a try soon.

---

