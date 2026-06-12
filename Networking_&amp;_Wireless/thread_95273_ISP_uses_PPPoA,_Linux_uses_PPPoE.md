---
title: "ISP uses PPPoA, Linux uses PPPoE?"
date: 2005-11-26
forum: Networking &amp; Wireless
---

### Post by handy on 2005-11-26
Can I set Linux to use PPPoA?  I have no experience with this kind of problem.  I am using a Netgear DG632 Modem/Router with 2 machines on a 10/100 switch, both can run on XP, but I am in the process of setting mine up to run Linux, on another drive.  I can not afford to buy my way out of this by changing ISP's at this stage.

Thanks in advance for any help forthcoming.

---

### Post by mips on 2005-11-26
handy,

You do NOT have to run PPPoA on your Linux box or any other OS for that matter. You have a router and it is very capable of handling that function and much easier to configure than doing PPPoE or PPPoA on Linux.

You are using the ethernet interface & not USB, is that assumption correct ?

Connect to the router via a web browser, go to the **Basic Settings** screen, click on **Device Mode**. 
What are the current settings, is it in **modem** or **router** mode ?


**Which ISP are you using ? Give me a Link to their website please !**

I'll come back to you when you provide more info and we'll sort this out in a jiffy ;)

---

### Post by handy on 2005-11-26
mips, thanks for your reply.
Yes ethernet, I've used both modem & router settings, the options
change accordingly.
My ISP says it has no problem with either.  If I use my modem not one of thiers.  If their modem then only PPPoA.  As it happens I'm now using their modem cause after a firmware update the netgear doesn't quite work anymore!  I've now re-downloaded the patch & I'll try that again later.  The current modem/router is a Siemens 4200, set up via Telstra cd.
Telstra bigpond website:  [http://www.bigpond.com/Home/Sitemap/](http://www.bigpond.com/Home/Sitemap/)
You may be sorry that you looked mips.  In the meantime I'll see if there are any changes with linux.
Thanks again
handy

---

### Post by handy on 2005-11-26
Nothing new with linux.
I think I'll go to bed.

---

### Post by mips on 2005-11-26
I looked at the Bigpond site and it sucks. Under the Windows setup in bridged mode they use PPPoE?!

Anyway we want the Siemens 4200 to run in routed mode, **it might already be in routed mode**. 
Do you have acces to the 4200 web interface ? 
You will need its IP address, username&password.
If you know this then great else we can get it from a windows pc that is working via the router.

From [http://www.dslreports.com/forum/remark,12998125]("http://www.dslreports.com/forum/remark,12998125")
> *I actually found how to get onto mine it was using **10.0.0.138** and the username was **admin** password was **admin**.*
-or-
*The modem shipped out from Bigpond is setup as DHCP server, so to find out the IP address, set your PC to request IP from DHCP server and then from a command prompt do "**ipconfig /all**". The dhcp server address is your 4200 modem address, which is normally 10.0.0.138 (BigPond default).*

Please copy and paste the output of your windows command prompt **ipconfig /all** here to verify the above info.

Can you access the router with the above info ?

The manual for the 4200 can be found here, [http://80.127.153.164/Documents/4x%20UM%20007-4035-001.pdf](http://80.127.153.164/Documents/4x%20UM%20007-4035-001.pdf).
This router has a very confusing user interface and looks like a biatch to configure.
I found [**this guide**]("http://bigpond.custhelp.com/cgi-bin/bigpond.cfg/php/enduser/std_adp.php?p_faqid=5778&p_sid=je7UbzVh&p_lva=5757&p_search_text=router+setup&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MjcmcF9wcm9kcz0yJnBfY2F0cz0mcF9wdj0xLjImcF9jdj0mcF9wYWdlPTEmcF9wbGF0Zm9ybT1OJnBfc2VhcmNoX3RleHQ9cm91dGVyIHNldHVw&p_li=#") to setup the username and password on the 4200

See if you cant revert your Netgear back to its original firmware and get it to work. That one is much easier to configure (or should I say familair as I had a DG834).

All you want to do at the end of the day is to ensure that the device is in routed mode, you have selected PPPoA encapsulation, specified the VCI/VPI information (think it is 8/35 for bigpond), Specify the login name & password, ensure the router is acting as a DHCP server & setup DNS. Then all you have to do is setup your PC for DHCP & auto DNS.

---

### Post by handy on 2005-11-27
Thanks for the info.  I can't access the DG632 at all.  I'll take that up with netgear.  The 4200 is accessible with the 10.10.0.138 & admin.  
I have no trouble with winxp.  My problem is that I am a total newB to linux.  I have probably been creating problems when the solution lays elsewhere.  I need to know how to set up the 4200 through bigpond's pppoa with debian or ubunto, is there a difference in the set adsl setup for those 2 disto's by the way?

GA-K8NS Ultra 939
AMD64 3500
2Gb DDR 400
6800 GT
SB Live 128
Intel pro/100+  (until I can get the drivers in for nForce 3)
hp procurve 2124 switch (picked it up new for $30!!)

Any advice is surely gratefully accepted.

Thanks,  handy

---

### Post by mips on 2005-11-27
handy,

You are going in circles here. Lets just forget about the word Linux for now.

First of all, how is the Windows PC configured ?
Does it run a PPPoA client or not ? Does each PC log in individually to the ADSL service or not ?
Open a command prompt and type **ipconfig /all** and paste the output here please.


On your Linux PC go to System->Administration->Networking
Select your ethernet adapter (highlight)
Click on Properties
Tick the "Enable this connection" box
Under Connection settings->Configuration: Select DHCP
All fields below this will be blank.
Click Ok to close the window.

Open a terminal and enter:
**ifconfig**
**route -n**

What output do you get from these commands, please post here.

Do you have a working machine with MSN, Skype or IRC on it, would be eassier & faster if I could talk to you in real time.

The way to setup the 4200 is here:
[http://bigpond.custhelp.com/cgi-bin/bigpond.cfg/php/enduser/std_adp.php?p_faqid=5778&p_sid=je7UbzVh&p_lva=5757&p_search_text=router+setup&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MjcmcF9wcm9kcz0yJnBfY2F0cz0mcF9wdj0xLjImcF9jdj0mcF9wYWdlPTEmcF9wbGF0Zm9ybT1OJnBfc2VhcmNoX3RleHQ9cm91dGVyIHNldHVw&p_li=#](http://bigpond.custhelp.com/cgi-bin/bigpond.cfg/php/enduser/std_adp.php?p_faqid=5778&p_sid=je7UbzVh&p_lva=5757&p_search_text=router+setup&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MjcmcF9wcm9kcz0yJnBfY2F0cz0mcF9wdj0xLjImcF9jdj0mcF9wYWdlPTEmcF9wbGF0Zm9ybT1OJnBfc2VhcmNoX3RleHQ9cm91dGVyIHNldHVw&p_li=#)

Maybe you should contact big pond and ask them for assistance in doing the following:
1. Set the 4200 up to act as a router
2. Set the router up to handle the PPPoA authentication of the Username & Password
3. Tell them that you want the router do perform the loging function and stay permanently connected.
4. Tell then you do NOT want to run any PPPoA client software on your PC.
5. If they dont know what you are talking about ask for a higher level tech support person.

---

### Post by handy on 2005-11-27
Yep xp runs PPPoA, the machines under xp just boot up into the always on adsl - that may or may not answer your 2nd question?

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Mine>ipcconfig /all
'ipcconfig' is not recognized as an internal or external command,
operable program or batch file.

C:\Documents and Settings\Mine>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : Twiglet
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : nsw.bigpond.net.au

Ethernet adapter Local Area Connection 5:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
        Physical Address. . . . . . . . . : 00-0F-EA-E0-28-1A

Ethernet adapter Local Area Connection 7:

        Connection-specific DNS Suffix  . : nsw.bigpond.net.au
        Description . . . . . . . . . . . : Intel(R) PRO/100+ Management Adapter
 #4
        Physical Address. . . . . . . . . : 00-20-E0-60-25-B5
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 10.0.0.3
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 10.0.0.138
        DHCP Server . . . . . . . . . . . : 10.0.0.138
        DNS Servers . . . . . . . . . . . : 10.0.0.138
        Lease Obtained. . . . . . . . . . : Sunday, 27 November 2005 2:46:25 PM
        Lease Expires . . . . . . . . . . : Tuesday, 19 January 2038 2:14:07 PM


Re: Bigpond, they will not support anything but PPPoA on the 4200, it is in router mode, & does stay permanently conected,
re; PPPoA software on my PC there is no option but to run the 4200 in PPPoA mode.  I will not be allowed to change that, atleast as far as support from Bigpond is concerned.

I'm about to put the linux drive in, & follow your instructions for the same, I'll update soonish.
thanks again, I don't have skype.

handy

---

### Post by mips on 2005-11-27
[QUOTE=handy]Yep xp runs PPPoA, the machines under xp just boot up into the always on adsl - that may or may not answer your 2nd question?[/QUOTE]

Not really but I will assume that the PC's are not handling the login.

[QUOTE=handy]
Re: Bigpond, they will not support anything but PPPoA on the 4200, it is in router mode, & does stay permanently conected,
re; PPPoA software on my PC there is no option but to run the 4200 in PPPoA mode.  I will not be allowed to change that, atleast as far as support from Bigpond is concerned.

I'm about to put the linux drive in, & follow your instructions for the same, I'll update soonish.
thanks again, I don't have skype.

handy[/QUOTE]

This confuses me to no end. If the 4200 is in routed mode and it is using PPPoA and it is doing the PPPoA authentication then why in the world does the PC require a PPPoA client. This makes absolutely no sense to me.... :confused:  ](*,) 

Anyway, let me know how it goes.

---

### Post by mips on 2005-11-27
This says it is possible,
[http://whirlpool.net.au/faq-ab.cfm#5.4.1](http://whirlpool.net.au/faq-ab.cfm#5.4.1)

The weird thing is these guys mention they use PPPoE !?!?

Maybe ask some questions to your fellow countrymen on the whirlpool forums.
[http://forums.whirlpool.net.au/](http://forums.whirlpool.net.au/)

---

### Post by handy on 2005-11-27
Ahhh, mips.
I told you I was an absolute beginner with linux.  I have no experience with PPPoE/A, I can setup & maintain simple peer to peer windows networks, no problem.  That & dial up & now adsl internet, no problem.  Well there are some sometimes :-).
I believe that I have misunderstood my own problem here, due to my ignorance of linux, it is like learning another language.  Therefore I have probably misled you on my way through.  For that I am sorry.  I have wasted your time some.  I also know, from windows customers that I have, what it is like.  It is interesting this role reversal.  We don't know what we don't know...
So, back to business.  I am online in linux, NOW!  I messed around trying to get my floppy to work, or to mount a ntfs hdd, to no avail, so that I could send you the info you wanted from linux via my xp drive running in the machine with internet access.  Then it occured to me to see if I could access the internet with the 4200 modem/router.  I can.  I think it is quite a bit slower than windows, I do have absolutely everything installed & running re: web server, ftp you name it I will do a reinstall & trim it down to desktop only.  That may make quite a difference.

In a few months, hopefully I will be able to help out in the forums.  It will certainly be fresh in my mind what a beginner has to go through to get to a plateau.

Thanks again,  handy

---

### Post by mips on 2005-11-27
handy,

No problem, the good thing is that it works.

When you reinstall I suggest the first thing you install is Automatix, it is a very handy GUI installer that will let you pick some of the most usefull stuff to install on your PC. It will also mount your ntfs & fat32 partitions for you, have a look at the link below.

[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

---

