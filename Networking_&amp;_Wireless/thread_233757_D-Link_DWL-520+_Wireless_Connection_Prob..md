---
title: "D-Link DWL-520+ Wireless Connection Prob."
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by thistlebrae on 2006-08-10
Hi All-

Wireless Network Recognized but cannot make a connection even though my XP laptop does connect (and has for months so I know the problem is with Ubuntu machine)

Here are the details:

*Ubuntu 6.06 LTS
*DWL-520+ PCI Adapter plugged into the Ubuntu Machine.
*Ubuntu recognized the WLAN adapter from initial install this a.m.

*Configured with the System/Administration/Networking wizard...then ACTIVATED the adapter.

*Using the Firefox browser I verified that I have no internet connectivity and cannot see ICS host on "windows network" browser.

*Read about the ndiswrapper and ndisgtk in the O'Reilly Ubuntu book and did following:

sudo aptitude install ndisgtk
sudo ndisgtk

this opened the Wireless Network Drivers  window
Selected Install New Driver (pointed to the appropriate .inf file)

Adapter then appeared and Hardware present: YES

this is the result of dmesg (looks a bit problematic and may help point to the problem)
_________________________________________
[4298843.350000] wlan0: changing radio power level to 18 dBm (23)
[4298843.428000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[4298911.185000] wlan0: changing radio power level to 18 dBm (23)
[4298911.263000] ADDRCONF(NETDEV_UP): wlan0: link is not ready


____________________________________________



this is the result of iwconfig wlan0
---------------------------------
wlan0     IEEE 802.11b+  ESSID:"CUBTS"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:22 Mb/s   Tx-Power=18 dBm   Sensitivity=176/255
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=70/100  Signal level=58/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



____________________________________________
Still cannot connect.  Any suggestions???
Sorry for the long post but trying to give all of the details I could to avoid a lengthy back and forth dialogue...and hope that others will benefit from the information as well.

FYI this is an adhoc network setup up not using an access point but it works just fine as it is what I am using from my XP laptop to send this very posting.

Would appreciate any help.

---

### Post by kvalis on 2006-08-10
Hello thistlebrae!

I had until today the same problem with exactly the same card. Mine was working in Ubuntu 5.10, but after upgrading to 6.06 the card was found, but not working.

**Dr.Nick** gave me a similar thread about acx drivers that did not work and it seems to be a firmware. You have to add a line to /etc/modprobe.d/options.

This is a read only file so you need to be sudo-root
Open a terminal windows and type:

> gedit /etc/modprobe.d/options

Type **options acx firmware_ver=1.2.1.34** to the bottom and save the file.
I then logged off and back again and typed:


> tore@ubuntu:~$ sudo iwlist wlan0 scan
wlan0 Scan completed :
Cell 01 - Address: 00:14:A5:03:64:04
ESSID:"Nytun"
Mode:Master
Frequency:2.437 GHz (Channel 6)
Quality=49/100 Signal level=28/100 Noise level=0/100
Encryption keyff
Bit Rates:54 Mb/s 

Now I had the Access Point, but when doing ifconfig, there was no IP address.


Downloaded and installed **wifi-radar**.

Ran it, selected my network, wifi-radar informed me that network did not have a profile and if I wanted to create one - I clicked yes, saved profile without adding any changes, and **there was my IP address**.

I am very pleased, I was just about to return to 5.10.
What wifi-radar does,that Ubuntu does not, I do not know, but I am happy.

If you want the thread, it's underneath
[http://ubuntuforums.org/showthread.p...hlight=acx_pci](http://ubuntuforums.org/showthread.p...hlight=acx_pci)

The Solution to the problem was originally a thread posted by **sgusto**

Let me know if it works for you

Kvalis

---

### Post by thistlebrae on 2006-08-10
Thanks,

I am hopeful you have the solution at hand.  A couple of questions for you.  Whey you stated...

"I then logged off and back again and typed:"
did you mean that you typed "sudo iwlist wlan0 scan"?
Just want to be sure that is what you typed and the system responded with the other data in the quote.

Secondly,

WIFI Radar.  Where did you download that from.  Was it in a package and loaded with Synaptic Package Manager?

Have not looked at that thread you quoted yet but will do so now.

Thanks again...
Todd

---

### Post by thistlebrae on 2006-08-10
Also...having trouble getting the thread you quoted.  Takes me to a summary page and I don't see the thread from there.

Is the path/link truncated in the post?

Regards,
Todd

---

### Post by kvalis on 2006-08-10
Hello Todd

The thread:

> [http://ubuntuforums.org/showthread.php?t=208408&highlight=acx_pci](http://ubuntuforums.org/showthread.php?t=208408&highlight=acx_pci)

After I did the change, I logged off and logged back in again, then opened a terminal window and typed the **iwlist** command.

Get hold of **Wifi-radar** by choosing **Applications>Add/Remove** - then click on **Show unsupported applications** and **Show commercial applications**, then enter **wifi-radar** in the search field, and it will show up. Click on it and then press Apply.

Kvalis

---

### Post by thistlebrae on 2006-08-10
Also... can you explain what you mean by saying I need to be Sudo-root?

I found the file and see that it is read only.  How do I logon as sudo-root?

---

### Post by kvalis on 2006-08-10
Ubuntu does not have root account like other distributions, but when you install Ubuntu, you become the administrator. So whenever you need to perform an administrative task, you will be asked for your password. This to ensure that you are not logged in as root the whole time and possibly do damage to your operating system.

When I write that the file is read-only, it means that you can open it, but will not be able to save it unless you issue the sudo command before other parameters.

Open a terminal windows and type:

> sudo gedit /etc/modprobe.d/options.

This command will the open the text editor GEDIT, and you will be able to save the file after you have done your changes.

Sorry if I was unclear!

Kvalis

---

### Post by thistlebrae on 2006-08-10
Kvalis-

You had the magic!

I am online via the DWL-520+ in Ad Hoc mode from the Ubuntu machine and on my Dell Laptop.  All from the Internet Connection Sharing setup on my XP desktop box connected to my HughesNet satellite broadband connection.

As far as the SU ROOT issue..here is what I did.  When I sudo'd that file it opened in READ ONLY access and would not allow me to change.  But I found this command in my O'Reilly Ubuntu book:

$ sudo passwd root

allows you to set a root password.  Once you do that you can logon as: SU
then it asks for the newly assigned ROOT password.

When you enter that it logs you on as ROOT and allows that file to be changed directly.  I guess I now know what the license plate I see everday on my drive to work means :rolleyes: 

Its says "GOT ROOT" :-P 

I suppose I just have to be careful what I do with it and that I remember the password I set :-& 

Thanks for all your help!!!  Now if I could get my video settings to let me do a resolution other than 640x480 I might actually be able to use this new setup!  I have another post out on that and need to go see if I have any answers.  At least I have an NVIDIA graphics card...which seems to be the preferred and less problematic one to get to work with Ubuntu.

Thanks Again!

---

### Post by kvalis on 2006-08-10
Glad that I finally could help someone!:D 

That book you mentioned - is it worthwhile buying. Is it a comprehensive one that tells you all the linux commands as well those things specific for Ubuntu??

Kvalis

---

### Post by thistlebrae on 2006-08-10
I HIGHLY recommend it.  While I bought two different ones this one never leaves my side:

Ubuntu Hacks -- Tips and Tools for Exploring, Using and Tuning Linux

Authors: Oxer, Rankin and Childers

Publisher: O'Reilly

ISBN No:  0-596-52720-9   US$ 29.99

Worth its weight in GOLD!

---

