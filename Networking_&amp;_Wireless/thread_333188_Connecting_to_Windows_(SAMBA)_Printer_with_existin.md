---
title: "Connecting to Windows (SAMBA) Printer with existing network"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by chudder on 2007-01-07
Hello Everyone,
    My roommate just set up a window printer on our wi-fi connection using peer-to-peer.  I'll admit I don't know the difference between p-to-p vs. network shared printers.  I go to the =>System => Administration => Printing and then select Add Printer => Network Printer => Windows Printer (SMB) and then it asks for all this stuff like:

Host:
Printer:
Username:
Password:

I'm making some guesses as to what each of these are.  If I'm incorrect, please tell me.  Also if you could tell me how to find this information that would be good.  

Host: the network name
Printer: printer make and model (how do I get drivers when the network option is selected?)
Username: ? (are these two my computers username and password?)
Password: ?

Maybe this is just right in front of my eyes and I can't see it.  I don't have much experience with network printers.

Any help would be greatly appreciated.

Thank you very much

Chud

---

### Post by puneit on 2007-01-07
Hi Chud
I am not an expert on this... Just try this.. maybe this works for you

Under Host: Once click on the drop down list, your room-mate computer name should be visible. If not, on his Windows machine, right click on My Computer and look for Computer Name. Use that name in host
For User Name: You need to supply the user name your friend has assigned for sharing. For default Windows machines, its usually "guest" without quotes of course.
For Password: Supply the password your friend has assigned. 
On windows machine, passwords can only be assigned for Windows XP Professional edition and not for XP HOME. I have no idea about other Windows versions.
So, if he has not specified a password, it should be blank. But in case the network can not be established with a NULL password (I don't know why I am saying this) then ask your friend to assign a password for his Guest account. This is different from assigning password to Guest login.
He needs to open Control Panel-> Computer Administration-> There he needs to search for Users on the left pane. On the right pane look for Guest and right click on it and select "Set Password" 
Once through it, a password is set. Now you can add that password.
But before all this you need to be sure, that your friend has enabled printer and file sharing in his machine. For this ask him to "Set up a home or small office network" and share his printer through that. A shared printer will show a hand under the printer icon. Since your thread topic   says existing network, then right click on the printer and share if the hand is not appearing
Once all that is done, and you supply the host name, user name, password clicking on printer, the shared printer should come up.

PS. I myself have never tried this. So, don't completely depend on me to get this working. But if you still face problems and if I can be of any help, I shall surely help you further..

---

### Post by chudder on 2007-01-07
I had my roommate enable file and printer sharing, the potential problem is that it asks that all computers to run the network wizard, but mine is the only linux box and I don't think I can do what that asks.  Should I just go ahead put in the fields that my roommate has given me?

---

### Post by puneit on 2007-01-07
When the wizard ends, he needs to select the message, "Just finish the Wizard", thats the last option.
And once thats done, you do what I told you. After I posted the procedure for you, I tried to connect to my girl friend's printer who is running windows XP  professional; and it worked.
 So go ahead...

---

### Post by chudder on 2007-01-14
The printer installed but the wrong driver was listed in the pre-installed drivers but I followed Brother's instructions. 

> (Other distributions)
If you are using the parallel port on your computer, or your computer is connected over a network you MUST edit the /etc/printcap file. 

 > Network Users:

Ensure that the :rm and :rp lines read as follows:

:rm=xxx.xxx.xxx.xxx\
:rp=lp\

In the example screenshot, you can see that the HL-1670N printer is configured to print to an IP address of 192.0.0.145


( Red Hat )
When you edit the /etc/printcap.local file you MUST restart the lpd service.

( Other distributions )
When you edit the /etc/printcap file you MUST restart the lpd service.

To do this enter:
/etc/init.d/lpd restart

at the command prompt.

I restarted as it said to but how do I edit it the printcap file?  I think if I could edit this, then that would get me on track because I could obtain the IP address.  I looked at the printcap file with gedit but there is no :rm and :rp sections.  Thank you again.

---

### Post by puneit on 2007-01-15
> I restarted as it said to but how do I edit it the printcap file? 
```
sudo gedit /etc/printcap
```
My printcap file
```
# This file was automatically generated by cupsd(8) from the
# /etc/cups/printers.conf file.  All changes to this file
# will be lost.
ML-1710|Shivli's comp:rm=puneit:rp=ML-1710:
PIXMA-iP1000-Ver.2.50|Canon:rm=puneit:rp=PIXMA-iP1000-Ver.2.50:

```

Here ML-1710 is the name of the shared printer
:rm=puneit is my system name (host name of my machine)
:rp=ML-1710: is the printer
The truncated contents of /etc/cups/printers.conf are (only showing shared printer)
```
# Printer configuration file for CUPS v1.2.4
# Written by cupsd on 2007-01-14 09:13
<Printer ML-1710>
Info Shivli's comp
Location Shivli's room
DeviceURI smb://guest:google@SHIVLI/Samsung ML- 1710
State Idle
StateTime 1168183508
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
```
In the line smb://guest:google@SHIVLI/Samsung ML- 1710
guest is the user name that I use to log in the machine SHIVLI
google is the password
So you can replace these accordingly
But I didn't edit this file to get the printer sharing working. 
Hope this helps..

---

### Post by chudder on 2007-01-15
This is the output when I type:

```
sudo gedit /etc/printcap
```

```
# This file was automatically generated by cupsd(8) from the
# /etc/cups/printers.conf file.  All changes to this file
# will be lost.
Stylus-CX5400|Chud's Printer:rm=localhost:rp=Stylus-CX5400:
HL2070N:\
        :mx=0:\
        :sd=/var/spool/lpd/HL2070N:\
        :sh:\
        :lp=/dev/usb/lp0:\
        :if=/usr/local/Brother/lpd/filterHL2070N:
```

It is the Brother HL2070N I want hooked up.  

I was told there should be an IP address for the printer.  Basically, I'm not sure what to do next.  Thank you very much so far for your contributions to help me.  I'm not sure where to go, because I downloaded the drivers as far as I know.

---

### Post by puneit on 2007-01-16
Sorry for replying after a day!
Even I am bumped at this. Have no idea what to do next. I wonder why no one else in the forums is replying to your post

Well, all I can suggest is to Google to results or trial and error. 
You may want to look into this too
[http://localhost:631]("http://localhost:631")
This is the CUPS page for printing. It comes with documentation and help pages.
I am sorry I couldn't be of any help to too..

---

