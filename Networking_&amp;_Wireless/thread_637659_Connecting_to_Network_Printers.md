---
title: "Connecting to Network Printers"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by timcallagy on 2007-12-11
Hi Guys,

I'm seeing a strange error message when trying to configure my laptop (running Gutsy) to the network printers in my office. I'm using system-config-printer.py 0.7.75 accessible through System -> Administration -> Printing. I click 'Go to Server' and enter the IP address and Password (empty) of the Network CUPS server. A list of network printers appears in the panel on the left. When I click on a printer, I immediately get this message: Error - Option 'sides' has value 'one' and cannot be edited.'

The option 'sides' that the error message refers to is in the 'Job Options' tab in the section called 'Other Options (Advanced)'. When I remove this option and click apply, I get the same error message. In fact, whenever I try to change anything, I get the same error message and no changes are implemented. 

As a result, my printers are left un-configured, and I cannot print at the moment. However, I can print test pages from the Printing Configuration app mentioned above.  This all worked fine under Feisty,

Any help/ideas are much appreciated,

Thanks in advance

Tim

---

### Post by movrshakr on 2007-12-18
I am watching this thread too as I need to get my Gutsy to print to a network printer, a Samsung SCX-4725FN.  

I have downloaded the linux driver package from Samsung (a tar.gz) but have no idea what to do next.  The printer is on the local net at 192.168.1 202.

Not promising that this has been here a week with no comments.

---

### Post by froy02 on 2007-12-19
On your samsung printer try to configure it using your browser.
type 'http://localhost:631' . click on  printers tab.    
click on modify printer.
follow the steps and  some they are self explanatory but for the next 3 below: 
configure your printer using ipp protocol.
when you get to the host name type 'socket://192.168.1.202'
select the cups driver for your printer.

---

### Post by movrshakr on 2007-12-19
I have been in the [http://localhost:631](http://localhost:631) screens many times.

When you say "when you get to the host name type 'socket://192.168.1.202'"
I don't ever get to a place to enter a hostname.  There is a screen to enter DEVICE URI.  And it provides examples like this:
Examples:

    [http://hostname:631/ipp/](http://hostname:631/ipp/)
    [http://hostname:631/ipp/port1](http://hostname:631/ipp/port1)
    ipp://hostname/ipp/
    ipp://hostname/ipp/port1
    lpd://hostname/queue
    socket://hostname
    socket://hostname:9100
...in all cases substituting the printer's IP for the word 'hostname'.

so I assume that's where you mean.  I will try it. You say to use the ipp protocol, but you are saying here to use socket--but there is an ipp example.  Why say use ipp, but then not put it in here, and use socket instead?  What is the difference in using ipp here vs using socket.  I thought the socket word was used with samba.  Clarification/education needed.

A bit later: OK, I have tried 
    ipp://hostname/ipp/
    ipp://hostname/ipp/port1
    socket://hostname
    socket://hostname:9100
At one point a dialog popped up wanting a cups login name and pwd, so I put in my name/pwd (the only user that is set up in ubuntu).  I also noticed a button for allowed users, so I put myself in there.

None of these four will print a test page, and I've forgotten the configuration I had that did print the messed up test page.

Now at a standstill.

---

### Post by Edho on 2007-12-19
This is wat i noted on a relaese somewhere...
--------------------------------------------------------------------------------

Printing with AppArmor  Ubuntu 7.10 introduces an additional security layer called AppArmor, whose support for CUPS printing is not yet complete.

This will result in printing failures in certain corner cases described below.

 The workaround in each of these cases is to disable the AppArmor CUPS profile by running sudo aa-complain cupsd.
 AppArmor support may be re-enabled by running sudo aa-enforce cupsd. 

  Printing to bluetooth printers does not work with AppArmor enabled. Bug #147800 

  Many third-party printer drivers (especially from printer manufacturers) do not work. Bug #152537

----------------------------------------------------------------------------------

Mayby it's related?

---

### Post by movrshakr on 2007-12-19
'find / -name apparmor' find such files on the machine, but 
'ps -ef|grep apparmor' finds only the grep command running.

So it would appear that apparmor is not running (installed) on my machine.

Still at a standstill on printing.

---

### Post by movrshakr on 2007-12-19
Excuse this long post. but I just found the below on the cups site at 
[http://www.cups.org/articles.php?L274](http://www.cups.org/articles.php?L274) 
and was astounded at how hard it seems to be to get printing to work.  Look at this, and it ends with no one responding that they have found the exact config setups to make it work.
-------------------- BEGIN PASTE FROM CUPS.ORG -------------

Article #274: What Password Do I Use At The Web Interface?
Created at 07:12 May 20, 2005 by steve
Last modified at 11:33 May 27, 2005

Normally, if you are performing an administrative operation such as adding a printer, you need to provide the root or other authorized administrator username and password.

SUSE users click the link below for more help:
[http://www.cups.org/articles.php?L275+I0+TFAQ+P1+Q](http://www.cups.org/articles.php?L275+I0+TFAQ+P1+Q)
MacOS 10.3 users click below for more help:
[http://www.cups.org/articles.php?L191+I0+T+P1+Q](http://www.cups.org/articles.php?L191+I0+T+P1+Q)

I'm not the root user, how do I get authorized to do administrative duties?:

[http://www.cups.org/articles.php?L237+I10+TMine+P1+Q](http://www.cups.org/articles.php?L237+I10+TMine+P1+Q)

Comments

From Anonymous, 15:58 Aug 08, 2006 (score=4)

Didn't work on my Kubuntu Dapper and I followed it exactly [ Reply ]
From robfantini, 21:11 Aug 28, 2006 (score=2)

I use Debian...  this should also work on K/Ubuntu :

try adding your user account to  the  'lpadmin' group.

see /etc/cups/cupsd_conf .  the SystemGroup is usually 'lpadmin'.

lpadmin s/b in /etc/group .

to add a user named joe to lpadmin, from command line:

adduser joe lpadmin .

From Adilson, 18:00 Sep 21, 2006 (score=5)

I am using Ubuntu 6 (dapper) and I have followed the the instructions, but none of them could made me autenticate sucessfully.

Then I've realized that the cupsys user didn't have access to the shadow file, so I've changed my cupsys user to belong to the shadow group and changed the SystemGroup in /etc/cups/cupsys.conf to point to the shadow group.

Then restart the cupsd (killall cupsd; /etc/init.d/cupsys restart) and then I could get my access validated by the Cups web interface. [ Reply ]
From dneary, 05:16 Dec 01, 2006 (score=3)

This is almost exactly right.

cupsys does need to read shadow, so editing /etc/group and adding cupsys to the shadow group is necessary - but that's all you need to do. There's no restart required, and you should leave lpadmin as the printer admin group (cupsys takes care of verifying that the user it authentifies is in SystemGroup).

Thanks for the hint - I would not have gotten it without you.

Dave Neary. [ Reply ]
From mablan, 11:00 Nov 16, 2006 (score=3)

Could you please provide step by step instructions of what is needed to solve the problem? I am a new user and it is not clear from your explanation what I need to do. I will really appreciate it. [ Reply ]
From beansdad, 11:22 Nov 17, 2006 (score=3)

Mablan,

Been through a lot today but got it working. First you need to download the LPR driver and cupswrapper from the Brother Solutions Center as Debian versions. Copy and paste into HOME directory (does work).

Open a terminal window and type "sudo ln -s /etc/init.d/cupsys /etc/init.d/cups" enter (throughout enter password if requested)

Still in terminal type "sudo dpkg -i --force-all (the name of the lpr file you downloaded)" enter

Next "sudo dpkg -i --force-all (the name of the cupswrapper file)" enter

Now vary from the Brother instructions and go to SYSTEM, ADMIN, USERS&GROUPS, GROUPS tab. Check the "Show all users and groups" box. Highlight "shadow" and click on properties. Find cupsys in the left list, highlight it and click on Add, should move to right list. Click OK.

Check the directory File System /etc/cups for either cupsd.conf or cupsys.conf (if you are very new it will probably be the first.

Back in the terminal window type "sudo gedit /etc/cups.cupsd.conf" (Beansdad 9 Dec 2006 - sorry this should read /etc/cups/cupsd.conf) (replace "cupsd" with "cupsys" if you do have the latter) enter. Find where it refers to "# Administrator user group... SystemGroup lpadmin" and change "lpadmin" to "shadow", then do file save as "cupsys.conf" enter

From the above it says to then in terminal "sudo killall cupsd; /etc/init.d/cupsys restart" enter. Not sure this works but we'll do it anyway.

Now close the terminal, shut down and restart (it won't work unless you do!)

When restarted, open your browser type "http://localhost:631" in the page bar at the top and then enter. This should then take you to the CUPS site, click on "Manage Printers" and, hopefully, the next screen will show your printer.

You do need to do this next bit as well, click "Modify Printer" and follow the entries (pick a name, select the connection (mainly USB or LPT#1) etc) through until it asks for your user and password - enter the name and password you use to start Ubuntu. Click OK and you should be there.

I've done this on my laptop and desktop today, both running Ubuntu 6.06 and got a test page out of both OK.

Hope it works for you. [ Reply ]
From henry23_98, 02:00 Jan 25, 2007 (score=4)

Could you mind telling me how to do in command line? Since I don't have xwin or gnome etc. in ubuntu. At least, how to add a group into shadow? Thx a lot [ Reply ]
From jenninju, 20:53 Nov 23, 2006 (score=2)

did not work for me. I have current kubuntu distro up to date. Whenever I get a password challenge I am warned data is being transmitted unencrypted and then access is denied. I think the current implementation of cups is paranoid in the extreme. I understand the risks of open ports, but to not enable a home network setup without endless hassles about passwords is crazy. Much exacerbated by the ubuntu/kubuntu prohibition on root logins. The farther we go the loster I get. I could to this stuff in Redhat 7.2 and 9.0 and now I can't do much of anything. [ Reply ]
From A_dreamer, 13:49 Aug 28, 2006 (score=3)

Hi, I followed the instruction given in: "http://www.cups.org/articles.php?L237+I10+TMine+P1+Q" but it did not work at all. I use Ubuntu (Dapper) and was not able to edit the file cupsd.conf at all, even when I used the "sudo" cmd before the actual cmd.  If someone have any idea about how to continue, I will be very grateful for the help/tips. Regards A_dreamer [ Reply ]
From tigerBITE, 14:20 Sep 03, 2006 (score=3)

have you tried becoming root by using the "sudo -s" first and then use your password to become root and then inter the cmd that you like. [ Reply ]
From dbc254, 05:35 Aug 28, 2006 (score=3)

can't start the cups server.  Running Mandriva 2005 LE.  Can enter command to start cups service, but not thru gui.  Don't know why or what happened.  Can't print now.  Downloaded latest CUPS and Ghostscript software, but cups service won't start..............  Everything else works perfectly tho.

[email]dallas25@voicenet.com[/email] [ Reply ]
From cas194, 06:27 Jun 21, 2007 (score=3)

Did anyone eventually resolve this one? I've tried every suggestion on Dapper and STILL can't get access..... [ Reply ]

---

### Post by movrshakr on 2007-12-19
SOLVED:  Someone in the cups.org forum suggested modifying the cupsd.conf to set 'LogLevel debug'.  I did and reran test.  Log file showed it was failing when running the file 'rastertosamsungspl'.  

I recopied the same one from  my original tar.gz driver file that came from Samsung into  /usr/lib/cups/filter, after deleting the one that was there before.  AND IT WORKS.  Hallelujah!

I don't know why it was failing because the file that was there was one I copied into that location previously out of the same download.  Who knows.  But it is fixed.

Oh, the DRI that ended up working was socket://[host-ip]:9100

---

