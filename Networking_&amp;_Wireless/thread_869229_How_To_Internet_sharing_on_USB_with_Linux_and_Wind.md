---
title: "How To: Internet sharing on USB with Linux and Windows Mobile"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by nukleuzN on 2008-07-24
[B][COLOR="DarkRed"][SIZE="4"][Solution for HTC Touch Pro / HD / Diamond](http://ubuntuforums.org/showpost.php?p=7399890&postcount=55) (And other WM 6.1 < phones. Also works on 6.5)
[/SIZE][/COLOR][/B]

**[COLOR="DarkRed"][SIZE="4"]OTHER WM6.0 > phones, keep on reading:[/SIZE][/COLOR]**

I have been lookin' for a complete guide on "How to connect to HSDPA/3G trough USB with Linux and Windows Mobile 6" - And here is the solution! :D
[B]
To connect your WM6 device via usb to your linux pc do the following:[/B]

On your phone enable internet sharing via usb but do _not connect_ the usb cable yet.

Run the following commands..you may need to install "svn" for this to work: (install by terminal: *sudo apt-get install subversion*)

```
svn co https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite/
cd usb-rndis-lite/
make
sudo ./clean.sh
sudo make install
```

Create the path "/etc/sysconfig/network/", in Hardy Heron the path "sysconfig/network/" doesnt exists, easy with *nautilus* trough terminal:

```
sudo nautilus
```

Nautilus opens, and browse to "/etc/" and create the path "sysconfig/network/" and futher. - Close nautilus.

The create the file "ifcfg-rndis0" in "/etc/sysconfig/network/", easy with *gedit* (gnome's text-editor) trough terminal:

```
sudo gedit /etc/sysconfig/network/ifcfg-rndis0
```

Fill the file with the text below:

```
BOOTPROTO='dhcp'
BROADCAST=''
ETHTOOL_OPTIONS=''
IPADDR=''
MTU='1460'
MRU='1500'
NAME=''
PEERDNS=no
NETMASK=''
NETWORK=''
REMOTE_IPADDR=''
STARTMODE='hotplug'
USERCONTROL='no'
_nm_name='static-0'
```

**So, if you haven't start "Internet Sharing" on your WM-phone yet. Do it now..**

- Now plug the phone into the usb cable going to the pc and if you do a "dmesg" you should see the following (or something similar):
```
[ 6539.589930] usb 5-1: USB disconnect, address 2
[ 6539.590829] rndis0: unregister 'rndis_host' usb-0000:00:1d.2-1, RNDIS device (SynCE patched)
[ 6540.972801] usb 5-1: new full speed USB device using uhci_hcd and address 3
[ 6541.019337] usb 5-1: configuration #1 chosen from 1 choice
[ 6541.628430] rndis0: register 'rndis_host' at usb-0000:00:1d.2-1, RNDIS device (SynCE patched), 80:00:60:0f:e8:00
```

and if you do an ifconfig you should have a new rndis0 device:

```
rndis0    Link encap:Ethernet  HWaddr 80:00:60:0f:e8:00  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::8200:60ff:fe0f:e800/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:8050  Metric:1
          RX packets:3008 errors:2425 dropped:0 overruns:0 frame:225
          TX packets:2993 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1915412 (1.8 MB)  TX bytes:763519 (745.6 KB)
```

----
The rndis0 device will exist both when internet sharing is enabled via usb and when it is NOT....here is how it works:

If internet sharing IS enabled via usb you have access to the internet and will get an IP...default route will be set.

If internet sharing is NOT enabled via usb then the rndis0 device will exist and can be used by programs such as syncE to manage your contact list or transfer files but you will not have internet access (from the phone) and more than likely you will not get an ip address auto assigned (it may keep the ip it used last).

I know this works as I'm connected at the moment via the rndis0 device. I find it to be more responsive than the connection via bluetooth. Hope this helps someone.

Source from: _[http://forums.opensuse.org/1579065-post1.html](http://forums.opensuse.org/1579065-post1.html)_

---

### Post by us3rX on 2008-07-24
Will try this when I get home to my laptop, I been looking for something like this for a while now, thanks XD

I'll post back here how things went. Thanks again.

~us3rX :twisted:

---

### Post by nukleuzN on 2008-07-24
Good, hope it will work for you to. The connection is pretty fast. I allmost think it works better on linux then windows. (faster transferring??)

Remember not to connect ur phone before you have followed the steps and opened and connected throug Internet Sharing. :)

---

### Post by us3rX on 2008-07-24
> **nukleuzN said:**
> Good, hope it will work for you to. The connection is pretty fast. I allmost think it works better on linux then windows. (faster transferring??)

Remember not to connect ur phone before you have followed the steps and opened and connected throug Internet Sharing. :)

Followed it step by step and it worked ^.^ Thanks for the post

~us3rX :twisted:

---

### Post by xiaoyong on 2008-08-10
Thanks.  I followed the instruction and I do succeed.  I am very excited for the solution.  :)

---

### Post by scenkner on 2008-08-12
I was hoping that someone on this board can help me.
First off, when ever I try the code "sudo apt-get install subversion"  It tells me the package cannot be found or something similar to that.  But I dont see that subversion can help me.  I am trying to install usb-rndis-lite because I dont have access to the internet.  The only code that uses subversion is the line "svn co https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite/" which obviously wont do me any good without an internet connection.  I have copied all of the files at [https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite/](https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite/) to a local folder and was hoping that I could install it from there.  However, Ubuntu doesn't seem to like "make" all alone, nor does it like sudo make install, I forget exactly what it says but it seems to expect more info at these lines.  Please help me.  This is all I need to put XP in the garbage.

---

### Post by scenkner on 2008-08-13
Please help!! I know this is easy for someone that has more experience w/ linux.  Why cant I just type 'make' in the terminal when that is what the instructions say???

---

### Post by nukleuzN on 2008-08-14
> **scenkner said:**
> I was hoping that someone on this board can help me.
First off, when ever I try the code "sudo apt-get install subversion"  It tells me the package cannot be found or something similar to that.  But I dont see that subversion can help me.  I am trying to install usb-rndis-lite because I dont have access to the internet.  The only code that uses subversion is the line "svn co https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite/" which obviously wont do me any good without an internet connection.  I have copied all of the files at [https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite/](https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite/) to a local folder and was hoping that I could install it from there.  However, Ubuntu doesn't seem to like "make" all alone, nor does it like sudo make install, I forget exactly what it says but it seems to expect more info at these lines.  Please help me.  This is all I need to put XP in the garbage.

Have you tried to put the usb-rndis-lite in your home folder. So the path will be similar to this:

/home/USERNAME/usb-rndis-lite/

USERNAME is replace by the username you use to login to ubuntu.

Then, in Terminal:

```

$ cd /home/USERNAME/
$ chown root:root usb-rndis-lite/
$ chmod 755 usb-rndis-lite/
$ cd usb-rndis-lite/
$ make
$ sudo ./clean.sh
$ sudo make install
```

THEN, follow the steps futher. Next step will be this one:

*"Create the path "/etc/sysconfig/network/", in Hardy Heron the path "sysconfig/network/" doesnt exists, easy with nautilus trough terminal:"*
[B]
Please let us know if this solution works for you...[/B]

---

### Post by Desmo UK on 2008-09-04
Tried to set this up using my Touch Diamond but can't seem to get it working :(
I can share my connection (Orange UK) via bluetooth but it just doesn't seem to work using the USB cable. Any ideas?

---

### Post by LoermansA on 2008-09-18
Hi,

I'm trying the above steps to get tethering to work on through my HTC Diamond. Everything appears to work, but Linux can't get an IP address. An rndis0 interface appears and an rndis0:avahi interface appears (whatever that means), but rndis0 doesn't get an IP address.

If I disconnect either the phone's usb cable, or terminate the connection on the phone itself, the rndis0 interfaces disappear again. That's something I like!

If only I'd get an IP address...

Thanks,

Arjan

---

### Post by FalloutMan on 2008-09-19
So, does anyone know if this gets detected as phone to pc or just standard data?  I only have the normal none-internet share data pack.

---

### Post by karvec on 2008-09-19
I understand this is for Hardy Heron, and I did an update-manager -d and install the Alpha of Ibex..

The instructions I followed for Hardy were just the 

make
./clean.sh
make install

and that is all I really had to do, however for Ibex I have not been able to get it to work so far.

If anyone has done this with Ibex and can verify will be much apprekiated.

Thanks!

~~karvec

P.S.  This is what it shows up as in Hardy Heron--  Haven't rebooted from installing Nvidia drivers, so if it looks funny...  :P  800x600 res.

On a base in FL w/ no internet, so I have to use my phone.  This works for Internet Connection Sharing, which is pretty freakin cool.

If anyone gets this to work on Ibex, though, please post here.

---

### Post by re98001 on 2008-09-26
.

---

### Post by re98001 on 2008-09-26
> **scenkner said:**
> I was hoping that someone on this board can help me.
First off, when ever I try the code "sudo apt-get install subversion"  It tells me the package cannot be found or something similar to that.  But I dont see that subversion can help me.  I am trying to install usb-rndis-lite because I dont have access to the internet.  The only code that uses subversion is the line "svn co https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite/" which obviously wont do me any good without an internet connection.  I have copied all of the files at [https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite/](https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite/) to a local folder and was hoping that I could install it from there.  However, Ubuntu doesn't seem to like "make" all alone, nor does it like sudo make install, I forget exactly what it says but it seems to expect more info at these lines.  Please help me.  This is all I need to put XP in the garbage.

First you need to install svn (subversion) before you can install rndis-lite. Google subversion for ubuntu or look for it on sourceforge.net. Let me know if you run into a problem.

---

### Post by karvec on 2008-10-10
The problem is...   My phone is my only source of internet, so I am having no luck whatsoever after updating to 8.10...  Because I can't get on the internet because my phone doesn't work.  *boggle.*

It's a vicious circle-  I can get it working in 8.04 and then update, but it's broken after the update.  And then I can't go online to research how to fix it because I can't get on the internet...  Hence I'm using good old Windows XP for now.

If anyone has any luck getting this to work on the Alpha, let me know.

---

### Post by keltose on 2008-10-11
This is amazing!  There are definitley a lot of smart people out there or else I wouldn't be able to make the switch!  Thanks!  I followed the directions and now I am posting with my Compaq laptop connected to my Moto Q9h on AT&T, (I had to do a little hack to override into MediaNet--Easy find through Google).

Thanks again!

---

### Post by PMahoney on 2008-10-11
Thanks for the helpful thread!  I had internet sharing working on my PPC6800 for a few startups, but now I'm having difficult receiving an IP address (I think).  My phone shows I'm connected, my computer shows a connection at rndis0, but I think it fails in receiving an IP address.  Again, it was working for several logins, but has since left me wondering what I've done wrong.

A possible problem is when I tried sudo ./clean.sh or just ./clean.sh during setup, it came back with 'command not found' and 'permission denied' respectively.  So my question here is...what's the purpose of this and could this be part of my problem?

Thanks in advance!

Peter

---

### Post by novicetopro on 2008-10-11
Thanks for the post, I got it to work right away following your instructions. 


Also for the guy who asked about getting it to work on Intrepid . I am using intrepid beta (I upgraded yesterday). So if it didn't work earlier on intrepid, it works now.

---

### Post by pmills on 2008-10-16
Thanks for the how-to, this was the last thing preventing me from ditching xp from my laptop altogether.

---

### Post by nukleuzN on 2008-10-17
> **Desmo UK said:**
> Tried to set this up using my Touch Diamond but can't seem to get it working :(
I can share my connection (Orange UK) via bluetooth but it just doesn't seem to work using the USB cable. Any ideas?

I can confirm that this "how-to" also works on HTC Touch Pro. Havent tried with Touch Diamond.

Now im using Ubuntu 8.10 Beta.

---

### Post by Arabiest on 2008-10-17
Thanks a Million dear friend...you have really solved one of the major issues i was trying my best to solve by reading here and there.

NOW LINUX-UBUNTU is my main OS!

Love you all.

---

### Post by keltose on 2008-10-17
okay...I had it all working good and then all of a sudden- nothing.  I know i downloaded and installed some updates from the repositories last week.  thin could've changed something?  when i get home tonight i will try the steps again and see what happens.  any thoughts?

---

### Post by obriente on 2008-10-17
keltose, I can confirm that every kernel update requires re-installing the modules, it's kind of annoying.

However with the latest update to 2.6.24-21 it won't even install.  I get the following error when I run make.  Any ideas?

make -C /lib/modules/2.6.24-21-generic/build SUBDIRS=/home/obriente/usb-rndis-lite modules
make: *** /lib/modules/2.6.24-21-generic/build: No such file or directory.  Stop.
make: *** [default] Error 2

---

### Post by keltose on 2008-10-17
Well, I reinstalled the module, and it connected as usual, but then the system freezes completely.  Now I am really lost....Sorry, I know nothing in this area.

---

### Post by obriente on 2008-10-17
well unless it deleted you can always boot to the old kernel (2.6.24-19 i believe) which it still works under for me, I was using it earlier... I'll just keep booting to that until someone comes up with a solution or Ibex lands. (I have a feeling the latter will come first)

---

### Post by obriente on 2008-10-20
Issue solved!

well my issue at least... after some forum crawling I came across a user having the same issue with Ubuntu Studio.

For some reason when Ubuntu updated the kernel it didn't install the new headers.  Installed the headers, then usb-rndis-lite installed properly.  Turned on ICS on my Blackjack, plugged it in and everything is up and running fine now.

Sorry I have no idea about the freezing keltose.  Did you follow the steps that have you create an ifcfg-rndis0 file?  Cause I found that it was unnecessary on my PC.  If you did try erasing it, re-installing rndis-lite then simply start ICS on your WiMo device and plug it in.

---

### Post by Xyphoid on 2008-11-05
This worked in Hardy Heron. But after a new install of Intrepid Ibex it doesn't work anymore. My USB port still works if I connect a USB cardreader. But when I connect my HTC TytnII, it doesn't even load. Suggestions anyone?

Edit:
Don't think Intrepid Ibex is causing the problem.
I think my phone just died. Can't load it with normal loader either :(

---

### Post by the3dman on 2008-11-12
In 8.10 everything should work out of the box (my WM6.1 T-Mobile Dash Did) by right clicking on the network icon and select edit connections then click the mobile broadband tab and follow the instructions.

---

### Post by prasenjit007 on 2008-11-19
Hi!
iam a newbie to linux.
since i don't have internet connection in my home so i largely depends upon my windows mobile(HTC P4350)to connect to internet.

First off, when ever I try the code "sudo apt-get install subversion" It tells me the package cannot be found.
The code "svn co https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite/" wont do me any good without an internet connection.

so i have copied all of the files at [https://synce.svn.sourceforge.net/sv...sb-rndis-lite/](https://synce.svn.sourceforge.net/sv...sb-rndis-lite/) to my home folder viz. /home/prasenjit/usb-rndis-lite/

then i executed the following commands in terminal

[CODE]
$ cd /home/USERNAME/
$ chown root:root usb-rndis-lite/
$ chmod 755 usb-rndis-lite/
$ cd usb-rndis-lite/
$ make
$ sudo ./clean.sh
$ sudo make install


but as soon as the command make is executed.....the following error is displayed:

make: Warning: File `Makefile' has modification time 2.5e+04 s in the future

make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/prasenjit/usb-rndis-lite modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'

make[2]: Warning: File `/home/prasenjit/usb-rndis-lite/Kbuild' has modification 
time 2.5e+04 s in the future

  CC [M]  /home/prasenjit/usb-rndis-lite/usbnet.o
  CC [M]  /home/prasenjit/usb-rndis-lite/cdc_ether.o
  CC [M]  /home/prasenjit/usb-rndis-lite/rndis_host.o

make[2]: warning:  Clock skew detected.  Your build may be incomplete.

  Building modules, stage 2.
  MODPOST 3 modules
  LD [M]  /home/prasenjit/usb-rndis-lite/cdc_ether.ko
  LD [M]  /home/prasenjit/usb-rndis-lite/rndis_host.ko
  LD [M]  /home/prasenjit/usb-rndis-lite/usbnet.ko

make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'

make: warning:  Clock skew detected.  Your build may be incomplete.




due to it when i execute the code:
sudo ./clean.sh

it displayes-

-bash: ./clean.sh: /bin/sh^M: bad interpreter: No such file or directory


again when make "install" code is executed it shows:

make: Warning: File `Makefile' has modification time 2.5e+04 s in the future

make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/prasenjit/usb-rndis-lite modules_install

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'

  INSTALL /home/prasenjit/usb-rndis-lite/cdc_ether.ko
  INSTALL /home/prasenjit/usb-rndis-lite/rndis_host.ko
  INSTALL /home/prasenjit/usb-rndis-lite/usbnet.ko
  DEPMOD  2.6.24-19-generic

make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
depmod -ae

make: warning:  Clock skew detected.  Your build may be incomplete.



so after following the rest of the steps iam unable to do the internet sharing...
plz help..

otherwise i don't have any other option rather than switching to windows xp
which i don't want to...

---

### Post by eras2r on 2008-11-23
> **LoermansA said:**
> Hi,

I'm trying the above steps to get tethering to work on through my HTC Diamond. Everything appears to work, but Linux can't get an IP address. An rndis0 interface appears and an rndis0:avahi interface appears (whatever that means), but rndis0 doesn't get an IP address.

If I disconnect either the phone's usb cable, or terminate the connection on the phone itself, the rndis0 interfaces disappear again. That's something I like!

If only I'd get an IP address...

Thanks,

Arjan

So here is the solution for those of you with HTC devices that can't get DHCP to work properly from the phone to the rndis0 device.  All credit to José Oliveira for posting this solution. For the full version please see:

[Original Post]("http://myhowtosandprojects.blogspot.com/2008/11/htc-diamond-as-rndis-modem.html")

The Fix:
```
Step 1 - Install Pre-requisites

open a terminal (use same terminal in next steps)

Code:

$ sudo apt-get install subversion

Step 2 - Get the Source

Code:

$ svn co http://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite
cd usb-rndis-lite/

Step 3 - Modify the source (Diamond only)

Code:

$ gedit rndis_host.c

on line 524, find this bit

Code:

if (tmp <>hard_mtu) {
dev_err(&intf->dev,
"dev can't take %u byte packets (max %u)\n",
dev->hard_mtu, tmp);
goto fail;
}

change it to this

Code:

if (tmp <>hard_mtu) {
dev_err(&intf->dev,
"dev can't take %u byte packets (max %u)\n",
dev->hard_mtu, tmp);
retval = -EINVAL;
/* goto fail;*/
}

save the file

Step 4 - Compile and make and install

Code:

$ make
$ sudo ./clean.sh
$ sudo make install

Step 5 - Start the Internet Connection Sharing

On OLD Tytn II's open Comm Manager on your phone and click on the Internet Sharing Now make sure USB is selected and choose connect

On Diamonds it's a seperate program called Internet Connection Sharing

Step 6 - Plug in the Phone (USB)
```

You may need so select that device in NetworkManager or "sudo dhclient rndis0".

Verified on a HTC AT&T Fuze (Touch Pro)

-e

---

### Post by nukleuzN on 2008-11-25
Thanx, added this solution in the first post.

---

### Post by loudnlownoma on 2008-12-04
Just posted in another thread, but having a similar problem as others - the connection from my xv6900 (Verizon's version of the Touch) is my primary and only connection while home, meaning I can't connect to run the setup properly.  I have installed Subversion and it's required dependencies after downloading them in XP.  I have copied all the files from the URL into a local folder, but can't seem to get the svn command to recognize anything other than URL's, which don't work without Internet   :(  Any suggestions?

---

### Post by karvec on 2008-12-07
Try rebooting with phone plugged in/connected.

Do you have internet connection sharing installed on your phone?  Not that bullcrap WModem stuff that Verizon makes you pay for, I'm talking ICSInstall.cab ......

Look it up if you don't have it, or consider reflashing your phone...  That's what I've had to do, because Verizon rips us off big time.

At the moment, though, I am using the Jaunty alpha and cannot re-plug in my phone if it disconnects, planning on trying the usb-rndis-lite...  Used it before, but it worked out of the box with Intrepid, so I wasn't using it.

---

### Post by ldrn on 2008-12-25
I have a laptop with the lpia kernel, and I cannot get this to work. I am not sure if it is the lpia arch's fault or not, but I get this when I run dmesg:

cdc_ether: disagrees about version of symbol usbnet_get_endpoints

---

### Post by VirtualPirate on 2009-01-06
Thank you very much for the post. It works for me and it is very helpful when in odd places around the coast.

---

### Post by meridianblade on 2009-01-07
ooiii! I followed all the directions on this post, including the ones about changing the source and recompiling...

I have a HTC Fuze im trying to connect to my Dell Mini 9 which uses the lpia kern...

I dont have a rndis0 device to connect to..

ray@ray:~/usb-rndis-lite$ sudo gedit /etc/sysconfig/network/ifcfg-rndis0
does exist and contains:

```
BOOTPROTO='dhcp'
BROADCAST=''
ETHTOOL_OPTIONS=''
IPADDR=''
MTU='1460'
MRU='1500'
NAME=''
PEERDNS=no
NETMASK=''
NETWORK=''
REMOTE_IPADDR=''
STARTMODE='hotplug'
USERCONTROL='no'
_nm_name='static-0'
```

```
ray@ray:~/usb-rndis-lite$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 8655
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:23:08:39:d4:57
Sending on   LPF/eth1/00:23:08:39:d4:57
Listening on LPF/eth0/00:21:70:cc:78:cb
Sending on   LPF/eth0/00:21:70:cc:78:cb
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.103 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.103 from 192.168.1.1
bound to 192.168.1.103 -- renewal in 36396 seconds.

```

```
[   72.410118] eth1: no IPv6 routers present
[  403.733263] usb 5-1: USB disconnect, address 2
[  406.989263] usb 5-1: new high speed USB device using ehci_hcd and address 5
[  407.131361] usb 5-1: configuration #1 chosen from 1 choice
[  740.124893] usb 5-1: USB disconnect, address 5
[ 1373.726706] usb 5-1: new high speed USB device using ehci_hcd and address 6
[ 1373.866911] usb 5-1: configuration #1 chosen from 1 choice
[ 1374.051210] usbnet: exports duplicate symbol usbnet_resume (owned by kernel)
[ 1374.054161] cdc_ether: disagrees about version of symbol usbnet_get_endpoints
[ 1374.054176] cdc_ether: Unknown symbol usbnet_get_endpoints
[ 1374.059002] rndis_host: disagrees about version of symbol usbnet_skb_return
[ 1374.059019] rndis_host: Unknown symbol usbnet_skb_return
[ 1374.059623] rndis_host: Unknown symbol usbnet_generic_cdc_bind
[ 1374.059924] rndis_host: Unknown symbol usbnet_cdc_unbind
[ 1920.848205] usb 5-1: USB disconnect, address 6
[ 2180.423282] usb 5-1: new high speed USB device using ehci_hcd and address 7
[ 2180.626921] usb 5-1: configuration #1 chosen from 1 choice
[ 2180.827143] usbnet: exports duplicate symbol usbnet_resume (owned by kernel)
[ 2180.828664] cdc_ether: disagrees about version of symbol usbnet_get_endpoints
[ 2180.828675] cdc_ether: Unknown symbol usbnet_get_endpoints
[ 2180.830621] rndis_host: disagrees about version of symbol usbnet_skb_return
[ 2180.830631] rndis_host: Unknown symbol usbnet_skb_return
[ 2180.831203] rndis_host: Unknown symbol usbnet_generic_cdc_bind
[ 2180.831508] rndis_host: Unknown symbol usbnet_cdc_unbind
[ 2397.021664] usb 5-1: USB disconnect, address 7

```

---

### Post by nukleuzN on 2009-01-25
> **eras2r said:**
> So here is the solution for those of you with HTC devices that can't get DHCP to work properly from the phone to the rndis0 device.  All credit to José Oliveira for posting this solution. For the full version please see:

[Original Post]("http://myhowtosandprojects.blogspot.com/2008/11/htc-diamond-as-rndis-modem.html")

The Fix:
```
Step 1 - Install Pre-requisites

open a terminal (use same terminal in next steps)

Code:

$ sudo apt-get install subversion

Step 2 - Get the Source

Code:

$ svn co http://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite
cd usb-rndis-lite/

Step 3 - Modify the source (Diamond only)

Code:

$ gedit rndis_host.c

on line 524, find this bit

Code:

if (tmp <>hard_mtu) {
dev_err(&intf->dev,
"dev can't take %u byte packets (max %u)\n",
dev->hard_mtu, tmp);
goto fail;
}

change it to this

Code:

if (tmp <>hard_mtu) {
dev_err(&intf->dev,
"dev can't take %u byte packets (max %u)\n",
dev->hard_mtu, tmp);
retval = -EINVAL;
/* goto fail;*/
}

save the file

Step 4 - Compile and make and install

Code:

$ make
$ sudo ./clean.sh
$ sudo make install

Step 5 - Start the Internet Connection Sharing

On OLD Tytn II's open Comm Manager on your phone and click on the Internet Sharing Now make sure USB is selected and choose connect

On Diamonds it's a seperate program called Internet Connection Sharing

Step 6 - Plug in the Phone (USB)
```

You may need so select that device in NetworkManager or "sudo dhclient rndis0".

Verified on a HTC AT&T Fuze (Touch Pro)

-e

When i get to the step "make", I do get the following in terminal:

```
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/joachim/usb-rndis-lite modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/joachim/usb-rndis-lite/rndis_host.o
/home/joachim/usb-rndis-lite/rndis_host.c: In function ‘rndis_bind’:
/home/joachim/usb-rndis-lite/rndis_host.c:524: error: expected expression before ‘>’ token
make[2]: *** [/home/joachim/usb-rndis-lite/rndis_host.o] Error 1
make[1]: *** [_module_/home/joachim/usb-rndis-lite] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [default] Error 2
```
I think there is an error in the rndis_host.c file, but i dont know what that is. I copy/paste the text abowe.
**/home/joachim/usb-rndis-lite/rndis_host.c:_524_:** error: expected expression before ‘>’ token
[SIZE="6"]
I did find the [COLOR="Red"]error[/COLOR], line 524 has to be changed to:[/SIZE]

```
if (tmp < dev->hard_mtu) {
dev_err(&intf->dev,
"dev can't take %u byte packets (max %u)\n",
dev->hard_mtu, tmp);
retval = -EINVAL;
/* goto fail;*/
}
```
"dev-" was missing in the "if".

---

### Post by csanda87 on 2009-01-25
I think this is a noob problem...I have no problems with anything until the make step.

```
chad@chad:~/usb-rndis-lite$ make
make -C /lib/modules/2.6.24-19-lpia/build SUBDIRS=/home/chad/usb-rndis-lite modules
make: *** /lib/modules/2.6.24-19-lpia/build: No such file or directory.  Stop.
make: *** [default] Error 2
```

---

### Post by nukleuzN on 2009-01-25
> **csanda87 said:**
> I think this is a noob problem...I have no problems with anything until the make step.h
make -C /lib/modules/2.6.24-19-lpia/build SUBDIRS=/home/chad/usb-rndis-lite modules
make: *** /lib/modules/2.6.24-19-lpia/build: No such file or directory.  Stop.
make: *** [default] Error 2[/CODE]

Try to "sudo make" instead of just "make". There can be a permission to a file/folder thats incorrect.

PS! Also see the end of the post above. Cheers.;)

---

### Post by csanda87 on 2009-01-25
> **nukleuzN said:**
> Try to "sudo make" instead of just "make". There can be a permission to a file/folder thats incorrect.

PS! Also see the end of the post above. Cheers.;)

sudo command has the same error...and i did read the post above and followed it directly.

i recieved this dell 9 mini straight from dell with ubuntu on it...this has to be a user problem...something needs to be adjusted to allow the admin to change files...sudo wont work for this step?

anyone else?

---

### Post by csanda87 on 2009-01-26
not sure if this will help find my problem...but i can run the install successfully....for some reason it is on the make command that gives me the errors.  any ideas?

---

### Post by csanda87 on 2009-01-26
> **csanda87 said:**
> I think this is a noob problem...I have no problems with anything until the make step.

```
chad@chad:~/usb-rndis-lite$ make
make -C /lib/modules/2.6.24-19-lpia/build SUBDIRS=/home/chad/usb-rndis-lite modules
make: *** /lib/modules/2.6.24-19-lpia/build: No such file or directory.  Stop.
make: *** [default] Error 2
```

anyone?  Sorry for the bump...just getting lost and can't find the answer anywhere.

---

### Post by csanda87 on 2009-01-26
Maybe the specs will help.

I have a dell mini 9...with the latest supported version of ubuntu.

Any ideas?  something to try?

---

### Post by nukleuzN on 2009-01-27
> **csanda87 said:**
> Maybe the specs will help.

I have a dell mini 9...with the latest supported version of ubuntu.

Any ideas?  something to try?

Hmmm

You must probably install the linux-headers and the linux kernel source. To do so, type the following (and those are back ticks, not single quotes, people!) 

 ```
sudo apt-get install linux-headers-`uname -r` linux-source
```

You'll notice that the source code is installed as a tar file in the /usr/src directory. This is not particularly useful. Let's untar it, do so by typing: 

 ```
sudo tar xjf /usr/src/linux-source-`uname -r`.tar.bz2 -C /usr/src
```

And then create a symbolic link to the source (if there isn't already one) by typing: 

 ```
cd /usr/src
 sudo rm linux
 sudo ln -s /usr/src/linux-source-`uname -r` linux
```

Finally, let's make sure we have the /lib/modules/`uname -r`/build directory pointing to THE HEADERS... NOT THE KERNEL SOURCE. This is the million dollar hurdle, and it bears repeating. The /lib/modules/<your kernel version>/build should point to the correct linux-headers, not the source code of the kernel. (Yes, weird, I know) Type: 

 ```
cd /lib/modules/`uname -r`
 sudo rm build
 sudo ln -s /usr/src/linux-headers-`uname -r` build
```

Now you can go to your *usb-rndis-lite* source directory that you downloaded, and do a 

 ```
make
```

and all should be good with the world. This was a supreme PITA, so hopeful that this will save somebody their sanity. 

If you are having problems with a module not compiling, and it is not important to you, do a 

```
find . -name my_bad_module_name.c -print
```

Then go to the directory that contains it. You will find a Makefile. Edit it and put a # at the start of the line that has the module name. 

[B][SIZE="4"]Retrieved and edited from "http://www.linuxtv.org/wiki/index.php/How_to_build_from_Mercurial".[/[/SIZE]B]

You can try this solution, but im not quite sure this is the problem...

---

### Post by csanda87 on 2009-02-15
thanks nukle....u solved my problem.

However Im still not getting connected through my phone.  

rndis0 doesnt pop up when i run ifconfig in terminal

another test and i get this error
```
sudo dhclient rndis0
There is already a pid file /var/run/dhclient.pid with pid 24837
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
rndis0: ERROR while getting interface flags: No such device
rndis0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

```

when i do a dmesg i get this 
```
[ 5482.724458] usb 5-8: USB disconnect, address 17
[ 5483.896840] usb 5-8: new high speed USB device using ehci_hcd and address 18
[ 5484.036410] usb 5-8: configuration #1 chosen from 1 choice
[ 5484.170758] usbnet: exports duplicate symbol usbnet_resume (owned by kernel)
[ 5484.177442] cdc_ether: disagrees about version of symbol usbnet_get_endpoints
[ 5484.177459] cdc_ether: Unknown symbol usbnet_get_endpoints
[ 5484.182291] rndis_host: disagrees about version of symbol usbnet_skb_return
[ 5484.182308] rndis_host: Unknown symbol usbnet_skb_return
[ 5484.182920] rndis_host: Unknown symbol usbnet_generic_cdc_bind
[ 5484.183227] rndis_host: Unknown symbol usbnet_cdc_unbind

```

do i need to install touch pro drivers or something?

---

### Post by csanda87 on 2009-02-15
just to elaborate a little more....on my phone (touch pro) i open internet sharing...and select usb from dropdown menu....i click connect and that status turns to 

Check USB cable connect

its as if i need a driver or something...the computer doesnt even recognize that it is connected I dont think...maybe there is a command to check if it sees it?

---

### Post by csanda87 on 2009-02-15
Someone else had a similar problem back in 2007 I read....they said 
> Doesn't look like your kernel module is getting loaded..you can try doing a depmod -a or modprobe the module to force it to load.

does that sound like my problem?  if so what would my kernel module be under so i can see if it is loaded or not using 
/sbin/modprobe -l <module_name>

---

### Post by csanda87 on 2009-02-17
bump...anyone?

---

### Post by treeofdeath on 2009-03-13
I'm relatively new at linux so I don't know what modprobe or any commands like that mean. I've followed lots of steps to get stuck at this point; usb-rndis-utils is installed and edited source etc. but when i run sudo dhclient rndis0, I get
```
 There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
rndis0: ERROR while getting interface flags: No such device
rndis0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device 

```And a dmesg results in things like 
```
[ 7545.537352] usbnet: exports duplicate symbol usbnet_resume (owned by kernel)
[ 7545.540537] cdc_ether: disagrees about version of symbol usbnet_get_endpoints
[ 7545.540547] cdc_ether: Unknown symbol usbnet_get_endpoints
[ 7545.542667] rndis_host: disagrees about version of symbol usbnet_skb_return
[ 7545.542677] rndis_host: Unknown symbol usbnet_skb_return

```I don't know where to go from here :( The 'ifconfig' show no rndis0...

---

### Post by Lety on 2009-03-20
Deleted.

---

### Post by ChosenWon on 2009-04-08
> **csanda87 said:**
> just to elaborate a little more....on my phone (touch pro) i open internet sharing...and select usb from dropdown menu....i click connect and that status turns to 

Check USB cable connect

its as if i need a driver or something...the computer doesnt even recognize that it is connected I dont think...maybe there is a command to check if it sees it?

I am a complete noob to Ubuntu. I just received my Dell Mini 9 and would like to use the Internet Sharing from my Cingular 8125 with WM6 upgrade. I am typing all these things in but have no idea what it is doing. I'm having the same exact problem as csanda87 where the computer does not seem to be recognizing my phone. I am at the last step I believe. Please help. I don't want to have to sell my new netbook for one that runs Windows just so I can use my phone as a modem.

---

### Post by smaring on 2009-05-27
I have been tethering my Samsung Blackjack (WM6) in modem mode to Cingular/AT&T Wireless for a few years, but I finally got tired on constantly switching out batteries and decided to give rndis a try again after my upgrade to Jaunty.

First, the basic install instructions for Synce at [http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice](http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice) got me able to browser my cell in nautilus with gvfs and I do get a network device created.

However, the device that is getting created is eth1, not rndis0.  Whether I try compiling usb-rndis-lite from the svn head, comment out the "goto fail", or whatever, I only ever get this eth1.

```

[84894.014341] usb 8-1: new full speed USB device using uhci_hcd and address 10
[84894.214411] usb 8-1: configuration #1 chosen from 1 choice
[84894.351708] rndis_host 8-1:1.0: RNDIS_MSG_QUERY(0x00010202) failed, -47
[84894.359787] eth1: register 'rndis_host' at usb-0000:00:1d.3-1, RNDIS device, 80:00:60:0f:e8:00
[84894.435651] type=1503 audit(1243421597.176:26): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=0 name="/usr/share/synce-hal/dhclient.conf" pid=31472 profile="/sbin/dhclient3"
[84894.435675] type=1503 audit(1243421597.176:27): operation="inode_create" requested_mask="a::" denied_mask="a::" fsuid=0 name="/var/run/dhclient-synce-eth1.lease" pid=31472 profile="/sbin/dhclient3"
[84896.369714] type=1503 audit(1243421599.112:28): operation="inode_create" requested_mask="a::" denied_mask="a::" fsuid=0 name="/var/run/dhclient-synce-eth1.lease" pid=31472 profile="/sbin/dhclient3"
[84904.896064] eth1: no IPv6 routers present

```

and it does seem to get an IP ...

```

eth1      Link encap:Ethernet  HWaddr 80:00:60:0f:e8:00  
          inet addr:169.254.2.2  Bcast:169.254.2.255  Mask:255.255.255.0
          inet6 addr: fe80::8200:60ff:fe0f:e800/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:24 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1997 (1.9 KB)  TX bytes:15101 (15.1 KB)

```

BUT ... I don't get a gateway or dns servers ...

```

# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1

```

asking dhcp to try again doesn't seem to help ...

```

# dhclient eth1
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/80:00:60:0f:e8:00
Sending on   LPF/eth1/80:00:60:0f:e8:00
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 169.254.2.2 from 169.254.2.1
DHCPREQUEST of 169.254.2.2 on eth1 to 255.255.255.255 port 67
DHCPACK of 169.254.2.2 from 169.254.2.1
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
bound to 169.254.2.2 -- renewal in 1213068 seconds.

```

I tried assuming that 169.254.2.1 was the gateway, which I CAN ping, but I can't hit anything on the other side, so perhaps it isn't.

When I connect in modem mode, I do get a gateway and dns ...

```

# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 ppp0
0.0.0.0         10.64.64.64     0.0.0.0         UG        0 0          0 ppp0
# cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 209.183.35.23
nameserver 209.183.33.23

```

-Steve Maring

---

### Post by markvdm on 2009-06-02
Hi Guys

New to the forums, and pretty new to Ubuntu. I have been messing around with it from 8.10, but more as a media centre. I am now trying to get comfortable using it as an everyday machine, and so far so good, except for this one issue.

I have a Sony Ericsson X1 running Windows Mobile 6.1 and using ICS. I have tried numerous setups, now including the steps in this thread, but nothing seems to solve my issue.

Without changing anything on Ubuntu, just activating ICS and plugging my phone in via USB, I get an Eth1 link active on Ubuntu with what seems all the correct DHCP settings. I can happily browse to [www.google.com](www.google.com) or [www.news24.com](www.news24.com) but other sites just never load, but time out after a few minutes. I can ping any site and I receive a reply, but trying to browse to anything just times out. I have then down a full reinstall, followed the above steps, but come up with the same result. I have even tried Opera Browser to rule out something wrong with Firefox.

So, any ideas guys? I'm stumped as to why certain sites would work and others not.

---

### Post by markvdm on 2009-06-03
Sorry for the bump guys, but any ideas? Any kind of trace or network tool I could run to help?

---

### Post by nukleuzN on 2009-06-04
[SIZE="5"][FONT="Arial Black"][COLOR="Red"]This is the solution, but read the fix in the bottom of the post: [http://ubuntuforums.org/showpost.php?p=6614002&postcount=37](http://ubuntuforums.org/showpost.php?p=6614002&postcount=37)

_**Or follow this, fixed solution:**_[/COLOR][/FONT][/SIZE]

**Step 1 -** Install Pre-requisites:

open a terminal (use same terminal in next steps)
```
$ sudo apt-get install subversion
```
**Step 2 **- Get the Source
```
$ svn co http://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite
$ cd usb-rndis-lite/
```
**Step 3 -** Modify the source ( [COLOR="Red"]_Only WM 6.1< phones_[/COLOR] )
```
$ gedit rndis_host.c
```
_on line 524, find this bit_
```
if (tmp < dev->hard_mtu) {
dev_err(&intf->dev,
"dev can't take %u byte packets (max %u)\n",
dev->hard_mtu, tmp);
goto fail;
}
```
_change it to this_
```
if (tmp < dev->hard_mtu) {
dev_err(&intf->dev,
"dev can't take %u byte packets (max %u)\n",
dev->hard_mtu, tmp);
retval = -EINVAL;
/* goto fail;*/
}
```

Save the file

**Step 4 -** Compile and make and install

```
$ make
$ sudo ./clean.sh
$ sudo make install
```

**Step 5 - Start the Internet Connection Sharing**

On OLD WM 6.0>'s open Comm Manager on your phone and click on the Internet Sharing Now make sure USB is selected and choose connect

On WM 6.1< phones it's a seperate program called Internet Connection Sharing

**Step 6 -** Plug in the Phone (USB)[/code]

---

### Post by brimurray on 2009-06-09
This looked promising, as I've been looking for such a solution.
I followed all the steps, all seemed to go to plan but i still cannot get the HTC Touch Diamond to connect the internet in Ubuntu 9.04.
I am at a total loss being a complete newbie. :confused:

---

### Post by sbolten on 2009-06-12
Working perfectly... thx

Regards,

Stephan

---

### Post by Mogge on 2009-08-22
I am using Compaq mini 730 oe with ubuntu 9.04 remix and a sony ericsson x1 mobile (wm6.1). All i have to do is to activate ics on phone and plug it in to the usb port in computer and wait for connection. When the connection is made i have to change the mtu to 1394.  In terminal type  " ifconfig " to check the network interface, in my computer the phone is eth2. Then typ " sudo ifconfig eth2 mtu 1394 ". Have to do this for each connection.. not sure how do make it permanent.

---

### Post by nukleuzN on 2009-08-24
> **Mogge said:**
> I am using Compaq mini 730 oe with ubuntu 9.04 remix and a sony ericsson x1 mobile (wm6.1). All i have to do is to activate ics on phone and plug it in to the usb port in computer and wait for connection. When the connection is made i have to change the mtu to 1394.  In terminal type  " ifconfig " to check the network interface, in my computer the phone is eth2. Then typ " sudo ifconfig eth2 mtu 1394 ". Have to do this for each connection.. not sure how do make it permanent.

[COLOR="Red"]**Have you doen this:**[/COLOR] [http://ubuntuforums.org/showpost.php?p=7399890&postcount=55](http://ubuntuforums.org/showpost.php?p=7399890&postcount=55) ??

---

### Post by jonlowe on 2009-08-25
**Update:  See below.**


I have a Motorola Q9C on Verizon.  I have Internet sharing on the phone, and it works fine with XP either with Bluetooth or USB.  I've gotten Bluetooth sharing to work in eeebuntu 3.0 (Jaunty), but no matter what I do, I cannot get a connection to work via USB. The status of the phone shows connected.  If I left click on the Network Manager icon in the tray, it sees my phone as a Remote Network device, but says it is unmanaged, and is greyed out.

My ifconfig looks like this:
```
rndis0    Link encap:Ethernet  HWaddr 80:fb:00:xx:xx:xx  
          inet addr:169.254.2.1  Bcast:169.254.2.3  Mask:255.255.255.252
          inet6 addr: 2002:4bfe:9dcb:5:82fb:ff:fe00:2919/64 Scope:Global
          inet6 addr: fec0::5:82fb:ff:fe00:2919/64 Scope:Site
          inet6 addr: fe80::82fb:ff:fe00:2919/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1394  Metric:1
          RX packets:55 errors:45 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5493 (5.4 KB)  TX bytes:17783 (17.7 KB)

```

My dmesg looks like this:
```
[ 6840.275243] usb 1-4: configuration #1 chosen from 1 choice
[ 6840.332019] usbcore: registered new interface driver cdc_ether
[ 6842.448108] rndis0 (rndis_host): not using net_device_ops yet
[ 6842.451099] rndis0: register 'rndis_host' at usb-0000:00:1d.7-4, RNDIS device (SynCE patched), 80:fb:00:00:29:19
[ 6842.451201] usbcore: registered new interface driver rndis_host

```

My verbose lsusb looks like this:

```
Bus 001 Device 004: ID 22b8:7009 Motorola PCS 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         3 RNDIS
  bMaxPacketSize0        64
  idVendor           0x22b8 Motorola PCS
  idProduct          0x7009 
  bcdDevice            0.01
  iManufacturer           1 Motorola Inc
  iProduct                2 Motorola USB Remote NDIS Network Device
  iSerial                 3 ffffffff-ff04-ffff-97b9-1f16070xxxxxx
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           62
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      3 RNDIS
      iInterface              0 
      ** UNRECOGNIZED:  05 24 01 00 01
      ** UNRECOGNIZED:  04 24 02 00
      ** UNRECOGNIZED:  05 24 06 00 01
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         3 RNDIS
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```

I've done a "sudo ifconfig rndis0 mtu 1394", but it made no difference.  I've also done a "sudo dhclient rndis0" and get:

```
There is already a pid file /var/run/dhclient.pid with pid 10113
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/rndis0/80:fb:00:00:29:19
Sending on   LPF/rndis0/80:fb:00:00:29:19
Sending on   Socket/fallback
DHCPREQUEST of 169.254.2.1 on rndis0 to 255.255.255.255 port 67
DHCPACK of 169.254.2.1 from 169.254.2.2
bound to 169.254.2.1 -- renewal in 113941 seconds.

```

But I stll cannot connect to the internet thru this connection.  Any ideas anyone?

**Update:  Just after posting this and after many days of screwing around, I got it to work.  I had to turn on "Enable advanced network functionality" under "Menu>Connections Settings>USB to PC" on the phone.  Unlike most other phones, I have to hit Connect AFTER I plug the cable into the PC.  This phone has quirks, and most other Wm6.1 connect info on order and settings just don't seem to work with this thing, to include what I had to do to make internet sharing work via Bluetooth on this phone.**

Jon
eee 900a, 2gb ram, 32gb SSD
eeebuntu 3.0 standard (Jaunty) with .30 kernel

---

### Post by oatcake on 2009-09-08
I have a different problem. I plug my phone (O2 XDA Ignito - Rebranded HTC Touch Diamond) into either 9.04 netbook remix or Fedora 11, and the device is detected and rndis0 is mapped to eth1. NetworkManager  runs DHCP and gets me an IP address.

I can ping Google and BBC News. I can SSH to my business server. However, I can't connect to a server using wget or Firefox.

I tried patching the modules (as per the start of this thread) and it removed an error from dmesg. However, ping and ssh still work, and wget and firefox don't.

From the Fedora machine, without patching, I could also get my e-mails in evolution. This didn't work with netbook remix before the patching - and I didn't check after. Firefox and wget didn't work on either machine.

It's almost as though the mobile phone provider is blocking port 80 - put I'm told this can't be the case as the web browser on the phone uses port 80.

Any ideas? Suggestion of things to try?

---

### Post by oatcake on 2009-09-08
Just followed a guide for connecting by bluetooth. The Blueman method didn't work, but I got bluez-compat and pand working. It paired okay and connected fine. Just need Network Manager support so it isn't such a manual farce.

---

### Post by nukleuzN on 2009-09-09
> **oatcake said:**
> I have a different problem. I plug my phone (O2 XDA Ignito - Rebranded HTC Touch Diamond) into either 9.04 netbook remix or Fedora 11, and the device is detected and rndis0 is mapped to eth1. NetworkManager  runs DHCP and gets me an IP address.

I can ping Google and BBC News. I can SSH to my business server. However, I can't connect to a server using wget or Firefox.

I tried patching the modules (as per the start of this thread) and it removed an error from dmesg. However, ping and ssh still work, and wget and firefox don't.

From the Fedora machine, without patching, I could also get my e-mails in evolution. This didn't work with netbook remix before the patching - and I didn't check after. Firefox and wget didn't work on either machine.

It's almost as though the mobile phone provider is blocking port 80 - put I'm told this can't be the case as the web browser on the phone uses port 80.

Any ideas? Suggestion of things to try?**Did you try out this fixed solution:** [http://ubuntuforums.org/showpost.php?p=7399890&postcount=55](http://ubuntuforums.org/showpost.php?p=7399890&postcount=55) ??

---

### Post by slinkygn on 2009-11-02
That won't work anymore, it seems.  SynCE's usb-rndis-lite won't build against 2.6.31.  Bug report is here: [http://sourceforge.net/tracker/?func=detail&aid=2882668&group_id=30550&atid=399601](http://sourceforge.net/tracker/?func=detail&aid=2882668&group_id=30550&atid=399601) Doesn't seem like the maintainer wants to fix it, anyway.  Looks like we're either going to have to fix usb-rndis-lite ourselves, or somebody's going to actually find out *why* the MTU isn't properly detected and submit a patch to the kernel.  I doubt our previous kludge will pass muster.

---

### Post by paul8472 on 2009-11-28
I'm a bit suspicious that after following this guide my system stopped automounting USB devices.  Has anyone else had a similar experience? Or better, still does anyone have a solution?

[http://ubuntuforums.org/showthread.php?t=1340121](http://ubuntuforums.org/showthread.php?t=1340121)

Many thanks

Paul

---

### Post by paul8472 on 2009-11-29
Ignore message above.  Issue resolved

---

### Post by cleatus99 on 2009-12-03
My impression as to why you can ping and connect..
there is a data packet size issue of some sort?

This worked for me on 9.04
[http://ubuntuforums.org/showthread.php?t=1074090](http://ubuntuforums.org/showthread.php?t=1074090)

However, I haven't been able to get to work with 9.10. :frown:

I've been looking into the Wifi sharing app, but it too doesn't seem to work with the AT&T Fuze with a stock ROM?

---

### Post by alexfish on 2009-12-08
> **cleatus99 said:**
> My impression as to why you can ping and connect..
there is a data packet size issue of some sort?

This worked for me on 9.04
[http://ubuntuforums.org/showthread.php?t=1074090](http://ubuntuforums.org/showthread.php?t=1074090)

However, I haven't been able to get to work with 9.10. :frown:

I've been looking into the Wifi sharing app, but it too doesn't seem to work with the AT&T Fuze with a stock ROM?

Hi 
are you looking for something like this

 just found this humble tool in the source code of the fine [Dovado UMR]("http://www.dovado.com/UMR.html") router, which they publish in compliance with the GPL. So if you want the power of your Wireless Broadband across your local network, but without the "fun" of setting up your own Linux router (as I did), consider investing in such a machine.

---

### Post by harrisupstate on 2009-12-13
> **cleatus99 said:**
> My impression as to why you can ping and connect..
there is a data packet size issue of some sort?

This worked for me on 9.04
[http://ubuntuforums.org/showthread.php?t=1074090](http://ubuntuforums.org/showthread.php?t=1074090)

However, I haven't been able to get to work with 9.10. :frown:

I've been looking into the Wifi sharing app, but it too doesn't seem to work with the AT&T Fuze with a stock ROM?

USB tethering also stopped working for me under 9.10, with my AT&T Tilt.  I tried that "fixed" patch mentioned above (whereby the make wasn't working) but my C file had already been as mentioned.  I am still getting the make error.

Anyway, any help would really be appreciated.  Thanks.

Harris

---

### Post by maestrobwh1 on 2009-12-26
HTC touch2 here.  Verizon.

I am not even seeing the device rndis0 after plugging my phone in when put in modem mode.

Everything builds fine.  I can modprobe the three new modules than do a depmod -ae and plugging in the phone still does not create the device rndis0

Anyone with a HTC TouchPro 2?  Win M0bile 6.1

I have successfully tethered it in XP using Verizon's software:-(  I'd prefer not to have to do that.

---

### Post by Ocyberbum on 2010-01-03
I also seem to be doing something wrong, I am running Kubuntu 9.10 on my Dell mini9, and i followed the instructions on the first post but nothing happens when i plug my phone in with Internet sharing on. It does not show up in the dmesg or ifconfig, 
Ifconfig shows Eth0,Eth1,Lo,Vmnet1,Vmnet8. I tried messing around with my WICD network and ended up crashing everything and had to uninstall + delete the wicd folder to get my network working again.
 It worked before i had to install the Wicd Network to get my wireless working, so im not sure what to do next? :confused:

---

### Post by loudnlownoma on 2010-03-04
> **maestrobwh1 said:**
> HTC touch2 here.  Verizon.

I am not even seeing the device rndis0 after plugging my phone in when put in modem mode.

Everything builds fine.  I can modprobe the three new modules than do a depmod -ae and plugging in the phone still does not create the device rndis0

Anyone with a HTC TouchPro 2?  Win M0bile 6.1

I have successfully tethered it in XP using Verizon's software:-(  I'd prefer not to have to do that.

I'm using the same phone here.  Haven't had as much chance to play with it just yet - but have been having trouble connecting to the Internet in Ubuntu since switching to HTC phones.  :(  But I have just installed 9.10 and gotten my wireless card working - using it now to get updates and such before jumping in and getting my feet wet with the rndis solution.  Will keep you posted here as I get farther!

---

### Post by loudnlownoma on 2010-03-04
The big thing killing me right now is with the Modem Link program running and on, the TP2 doesn't seem to appear to the network manager at all.  If I leave that off (so it won't be able to connect for tethering) it shows up with an rndis connection, but since the phone won't tether this way, it won't receive a connection...

---

### Post by delillod on 2010-03-09
Hi, sorry, I'd like to know if it works in UBUNTU 9.10 ?
I get connected to the phone (HTC DIAMOND), and my laptop get an IP (it recognize a new cable network connection by itself) doing nothing of this post, but can't surf the web.
I'll try it tonight, following the instructions step by step and let you know. Anyway, comments are welcome.
Thanks in advance all of you.
Diego.

---

### Post by nukleuzN on 2010-03-09
> **delillod said:**
> Hi, sorry, I'd like to know if it works in UBUNTU 9.10 ?
I get connected to the phone (HTC DIAMOND), and my laptop get an IP (it recognize a new cable network connection by itself) doing nothing of this post, but can't surf the web.
I'll try it tonight, following the instructions step by step and let you know. Anyway, comments are welcome.
Thanks in advance all of you.
Diego.

Hi,

I have stopped updating this thread. Im now using Linux Based device: Android. If your are a Linux user I think you should consider this phone-OS next time; then you dont have to configure stuff like this.

Hope users that figures out what works between MW-phones and Linux, and "how to work-arounds" will continue posting solutions in this thread. Have you read this and tried it: [http://ubuntuforums.org/showpost.php?p=7921788&postcount=63](http://ubuntuforums.org/showpost.php?p=7921788&postcount=63)?

---

### Post by maestrobwh1 on 2010-04-01
> **loudnlownoma said:**
> The big thing killing me right now is with the Modem Link program running and on, the TP2 doesn't seem to appear to the network manager at all.  If I leave that off (so it won't be able to connect for tethering) it shows up with an rndis connection, but since the phone won't tether this way, it won't receive a connection...

Ahh, that is why I am not seeing rndis0: how annoying.  I don't hate my TP2, BUT, I am going to get the Android or some other linux based phone next time.

So when the phone can tether, the device does not show, but when the phone is set as a modem, it does not.  How defeating...

I do have XP running in VirtualBox with the Verizon Access hardware installed.  I disable the NAT (ethernet in virtualbox XP) and run the program (With USB allowing pass through), I can connect in XP.  

If anyone has a copy of XP, and does not want to run it natively and just wants a modem connection once in a while and internet access, this does work.  Not ideal.

---

### Post by Vinencre on 2010-04-15
Hello,

I am on Ubuntu 9.10 and can't pass the "make" step. :(

I did this: [http://ubuntuforums.org/showpost.php?p=7399890&postcount=55](http://ubuntuforums.org/showpost.php?p=7399890&postcount=55)
and this: [http://ubuntuforums.org/showpost.php?p=6624814&postcount=44](http://ubuntuforums.org/showpost.php?p=6624814&postcount=44)

But always same errors:
```
~/usb-rndis-lite$ make
make -C /lib/modules/2.6.31-20-generic/build SUBDIRS=/home/<user>/usb-rndis-lite modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.31-20 »

  ERROR: Kernel configuration is invalid.
         include/linux/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.


  WARNING: Symbol version dump /usr/src/linux-headers-2.6.31-20/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/<user>/usb-rndis-lite/usbnet.o
cc1: error: include/linux/autoconf.h: Aucun fichier ou dossier de ce type
In file included from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
```And here is the complete "make" result:
```
~/usb-rndis-lite$ make
make -C /lib/modules/2.6.31-20-generic/build SUBDIRS=/home/<user>/usb-rndis-lite modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.31-20 »

  ERROR: Kernel configuration is invalid.
         include/linux/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.


  WARNING: Symbol version dump /usr/src/linux-headers-2.6.31-20/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/<user>/usb-rndis-lite/usbnet.o
cc1: error: include/linux/autoconf.h: Aucun fichier ou dossier de ce type
In file included from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/<user>/usb-rndis-lite/usbnet.c:36:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/processor.h:115: error: &#8216;CONFIG_X86_L1_CACHE_SHIFT&#8217; undeclared here (not in a function)
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/processor.h:115: error: requested alignment is not a constant
In file included from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/<user>/usb-rndis-lite/usbnet.c:36:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/processor.h:161:1: warning: "cache_line_size" redefined
In file included from /usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/processor.h:28,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/<user>/usb-rndis-lite/usbnet.c:36:
include/linux/cache.h:64:1: warning: this is the location of the previous definition
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/processor.h: In function &#8216;load_cr3&#8217;:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/processor.h:192: error: &#8216;CONFIG_PAGE_OFFSETUL&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/processor.h:192: error: (Each undeclared identifier is reported only once
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/processor.h:192: error: for each function it appears in.)
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/processor.h: At top level:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/processor.h:241: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/processor.h:272: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/processor.h: In function &#8216;wbinvd_halt&#8217;:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/processor.h:777: error: implicit declaration of function &#8216;halt&#8217;
In file included from /usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic.h:4,
                 from /usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/thread_info.h:24,
                 from include/linux/thread_info.h:56,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:8,
                 from include/linux/stat.h:60,
                 from include/linux/module.h:10,
                 from /home/<user>/usb-rndis-lite/usbnet.c:36:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h: At top level:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:201: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;atomic64_t&#8217;
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:201: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:213: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:225: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;atomic64_t&#8217;
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h: In function &#8216;atomic64_add&#8217;:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:228: error: &#8216;v&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:227: error: invalid lvalue in asm output 0
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:227: error: memory input 2 is not directly addressable
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h: At top level:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:239: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;atomic64_t&#8217;
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h: In function &#8216;atomic64_sub&#8217;:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:242: error: &#8216;v&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:241: error: invalid lvalue in asm output 0
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:241: error: memory input 2 is not directly addressable
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h: At top level:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:255: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;atomic64_t&#8217;
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h: In function &#8216;atomic64_sub_and_test&#8217;:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:260: error: &#8216;v&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:259: error: invalid lvalue in asm output 0
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:259: error: memory input 3 is not directly addressable
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h: At top level:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:271: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:284: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:299: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:317: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:336: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;atomic64_t&#8217;
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h: In function &#8216;atomic64_add_negative&#8217;:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:341: error: &#8216;v&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:340: error: invalid lvalue in asm output 0
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:340: error: memory input 3 is not directly addressable
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h: At top level:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:353: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;atomic64_t&#8217;
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h: In function &#8216;atomic64_add_return&#8217;:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:357: error: &#8216;v&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:356: error: invalid lvalue in asm output 1
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:356: error: memory input 3 is not directly addressable
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h: At top level:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:362: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;atomic64_t&#8217;
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h: In function &#8216;atomic64_sub_return&#8217;:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:364: error: &#8216;v&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:364: error: too many arguments to function &#8216;atomic64_add_return&#8217;
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h: At top level:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:370: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:375: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/atomic_64.h:425: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
In file included from include/linux/mmzone.h:16,
                 from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/<user>/usb-rndis-lite/usbnet.c:36:
include/linux/nodemask.h: In function &#8216;__first_node&#8217;:
include/linux/nodemask.h:239: error: implicit declaration of function &#8216;find_first_bit&#8217;
include/linux/nodemask.h: In function &#8216;__next_node&#8217;:
include/linux/nodemask.h:245: error: implicit declaration of function &#8216;find_next_bit&#8217;
include/linux/nodemask.h: In function &#8216;__first_unset_node&#8217;:
include/linux/nodemask.h:263: error: implicit declaration of function &#8216;find_first_zero_bit&#8217;
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/<user>/usb-rndis-lite/usbnet.c:36:
include/linux/mmzone.h:18:26: error: linux/bounds.h: Aucun fichier ou dossier de ce type
include/linux/mmzone.h:251:5: warning: "MAX_NR_ZONES" is not defined
include/linux/mmzone.h:253:7: warning: "MAX_NR_ZONES" is not defined
include/linux/mmzone.h:255:7: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/<user>/usb-rndis-lite/usbnet.c:36:
include/linux/mmzone.h: At top level:
include/linux/mmzone.h:288: error: &#8216;MAX_NR_ZONES&#8217; undeclared here (not in a function)
In file included from include/linux/gfp.h:8,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/<user>/usb-rndis-lite/usbnet.c:36:
include/linux/mmdebug.h:4:28: error: linux/autoconf.h: Aucun fichier ou dossier de ce type
In file included from include/linux/elf.h:7,
                 from include/linux/module.h:14,
                 from /home/<user>/usb-rndis-lite/usbnet.c:36:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/elf.h: In function &#8216;start_ia32_thread&#8217;:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/elf.h:165: error: implicit declaration of function &#8216;load_gs_index&#8217;
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/elf.h: In function &#8216;elf_common_init&#8217;:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/elf.h:180: error: &#8216;struct thread_struct&#8217; has no member named &#8216;fs&#8217;
In file included from include/linux/tracepoint.h:18,
                 from include/linux/module.h:19,
                 from /home/<user>/usb-rndis-lite/usbnet.c:36:
include/linux/rcupdate.h:64:2: error: #error "Unknown RCU implementation specified to kernel configuration"
In file included from include/linux/module.h:19,
                 from /home/<user>/usb-rndis-lite/usbnet.c:36:
include/linux/tracepoint.h: In function &#8216;tracepoint_synchronize_unregister&#8217;:
include/linux/tracepoint.h:156: error: implicit declaration of function &#8216;__synchronize_sched&#8217;
In file included from include/linux/slab_def.h:144,
                 from include/linux/slab.h:166,
                 from include/linux/percpu.h:5,
                 from /usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/local.h:4,
                 from include/linux/module.h:20,
                 from /home/<user>/usb-rndis-lite/usbnet.c:36:
include/linux/kmalloc_sizes.h:5:5: warning: "CONFIG_X86_L1_CACHE_SHIFT" is not defined
include/linux/kmalloc_sizes.h:9:5: warning: "CONFIG_X86_L1_CACHE_SHIFT" is not defined
In file included from include/linux/module.h:22,
                 from /home/<user>/usb-rndis-lite/usbnet.c:36:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/module.h:68:2: error: #error unknown processor family
/home/<user>/usb-rndis-lite/usbnet.c:37:27: error: linux/version.h: Aucun fichier ou dossier de ce type
In file included from include/linux/sched.h:55,
                 from /home/<user>/usb-rndis-lite/usbnet.c:38:
include/linux/jiffies.h:18:5: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:20:7: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:22:7: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:24:7: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:26:7: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:28:7: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:30:7: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:32:7: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:34:7: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:36:7: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:39:3: error: #error Invalid value of HZ.
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: error: division by zero in #if
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: error: division by zero in #if
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: error: division by zero in #if
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: error: division by zero in #if
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: error: division by zero in #if
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: error: division by zero in #if
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: error: division by zero in #if
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: error: division by zero in #if
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: error: division by zero in #if
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: error: division by zero in #if
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: error: division by zero in #if
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: error: division by zero in #if
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: error: division by zero in #if
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: error: division by zero in #if
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: error: division by zero in #if
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:31: error: division by zero in #if
include/linux/jiffies.h:257:46: warning: "SHIFT_HZ" is not defined
In file included from include/linux/sched.h:61,
                 from /home/<user>/usb-rndis-lite/usbnet.c:38:
include/linux/mm_types.h:27:5: warning: "CONFIG_SPLIT_PTLOCK_CPUS" is not defined
include/linux/mm_types.h:71:5: warning: "CONFIG_SPLIT_PTLOCK_CPUS" is not defined
In file included from include/linux/sched.h:77,
                 from /home/<user>/usb-rndis-lite/usbnet.c:38:
include/linux/proportions.h: In function &#8216;prop_inc_percpu&#8217;:
include/linux/proportions.h:75: error: implicit declaration of function &#8216;local_irq_save&#8217;
include/linux/proportions.h:77: error: implicit declaration of function &#8216;local_irq_restore&#8217;
In file included from /home/<user>/usb-rndis-lite/usbnet.c:38:
include/linux/sched.h:384:5: warning: "CONFIG_SPLIT_PTLOCK_CPUS" is not defined
In file included from include/linux/mm.h:38,
                 from include/linux/scatterlist.h:6,
                 from include/linux/dma-mapping.h:7,
                 from include/linux/dmaengine.h:26,
                 from include/linux/skbuff.h:30,
                 from include/linux/if_ether.h:124,
                 from include/linux/netdevice.h:29,
                 from /home/<user>/usb-rndis-lite/usbnet.c:40:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/pgtable.h: In function &#8216;pmd_page_vaddr&#8217;:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/pgtable.h:347: error: &#8216;CONFIG_PAGE_OFFSETUL&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/pgtable.h: In function &#8216;pud_page_vaddr&#8217;:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/pgtable.h:418: error: &#8216;CONFIG_PAGE_OFFSETUL&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/pgtable.h: In function &#8216;pgd_page_vaddr&#8217;:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/pgtable.h:463: error: &#8216;CONFIG_PAGE_OFFSETUL&#8217; undeclared (first use in this function)
In file included from include/linux/scatterlist.h:6,
                 from include/linux/dma-mapping.h:7,
                 from include/linux/dmaengine.h:26,
                 from include/linux/skbuff.h:30,
                 from include/linux/if_ether.h:124,
                 from include/linux/netdevice.h:29,
                 from /home/<user>/usb-rndis-lite/usbnet.c:40:
include/linux/mm.h: In function &#8216;virt_to_head_page&#8217;:
include/linux/mm.h:308: error: implicit declaration of function &#8216;__pfn_to_page&#8217;
include/linux/mm.h:308: error: &#8216;CONFIG_PAGE_OFFSETUL&#8217; undeclared (first use in this function)
include/linux/mm.h:308: warning: initialization makes pointer from integer without a cast
In file included from include/linux/scatterlist.h:6,
                 from include/linux/dma-mapping.h:7,
                 from include/linux/dmaengine.h:26,
                 from include/linux/skbuff.h:30,
                 from include/linux/if_ether.h:124,
                 from include/linux/netdevice.h:29,
                 from /home/<user>/usb-rndis-lite/usbnet.c:40:
include/linux/mm.h:444:63: warning: "NR_PAGEFLAGS" is not defined
include/linux/mm.h:492:62: warning: "NR_PAGEFLAGS" is not defined
In file included from include/linux/scatterlist.h:6,
                 from include/linux/dma-mapping.h:7,
                 from include/linux/dmaengine.h:26,
                 from include/linux/skbuff.h:30,
                 from include/linux/if_ether.h:124,
                 from include/linux/netdevice.h:29,
                 from /home/<user>/usb-rndis-lite/usbnet.c:40:
include/linux/mm.h: In function &#8216;lowmem_page_address&#8217;:
include/linux/mm.h:582: error: implicit declaration of function &#8216;__page_to_pfn&#8217;
include/linux/mm.h:582: error: &#8216;CONFIG_PAGE_OFFSETUL&#8217; undeclared (first use in this function)
include/linux/mm.h:919:5: warning: "CONFIG_SPLIT_PTLOCK_CPUS" is not defined
In file included from include/linux/scatterlist.h:8,
                 from include/linux/dma-mapping.h:7,
                 from include/linux/dmaengine.h:26,
                 from include/linux/skbuff.h:30,
                 from include/linux/if_ether.h:124,
                 from include/linux/netdevice.h:29,
                 from /home/<user>/usb-rndis-lite/usbnet.c:40:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/io.h: In function &#8216;virt_to_phys&#8217;:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/io.h:99: error: &#8216;CONFIG_PAGE_OFFSETUL&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/io.h: In function &#8216;phys_to_virt&#8217;:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/io.h:117: error: &#8216;CONFIG_PAGE_OFFSETUL&#8217; undeclared (first use in this function)
In file included from include/linux/dma-mapping.h:7,
                 from include/linux/dmaengine.h:26,
                 from include/linux/skbuff.h:30,
                 from include/linux/if_ether.h:124,
                 from include/linux/netdevice.h:29,
                 from /home/<user>/usb-rndis-lite/usbnet.c:40:
include/linux/scatterlist.h: In function &#8216;sg_set_buf&#8217;:
include/linux/scatterlist.h:112: error: &#8216;CONFIG_PAGE_OFFSETUL&#8217; undeclared (first use in this function)
include/linux/scatterlist.h:112: warning: passing argument 2 of &#8216;sg_set_page&#8217; makes pointer from integer without a cast
include/linux/scatterlist.h:85: note: expected &#8216;struct page *&#8217; but argument is of type &#8216;int&#8217;
In file included from include/net/netns/mib.h:4,
                 from include/net/net_namespace.h:12,
                 from include/linux/netdevice.h:47,
                 from /home/<user>/usb-rndis-lite/usbnet.c:40:
include/net/snmp.h: At top level:
include/net/snmp.h:74: error: requested alignment is not a constant
include/net/snmp.h:82: error: requested alignment is not a constant
include/net/snmp.h:87: error: requested alignment is not a constant
include/net/snmp.h:93: error: requested alignment is not a constant
include/net/snmp.h:98: error: requested alignment is not a constant
include/net/snmp.h:105: error: requested alignment is not a constant
include/net/snmp.h:111: error: requested alignment is not a constant
In file included from include/linux/hardirq.h:10,
                 from include/linux/interrupt.h:12,
                 from include/linux/netdevice.h:1058,
                 from /home/<user>/usb-rndis-lite/usbnet.c:40:
/usr/src/linux-headers-2.6.31-20/arch/x86/include/asm/hardirq.h:29: error: requested alignment is not a constant
In file included from /home/<user>/usb-rndis-lite/usbnet.c:41:
include/linux/etherdevice.h: In function &#8216;is_etherdev_addr&#8217;:
include/linux/etherdevice.h:203: error: implicit declaration of function &#8216;__rcu_read_lock&#8217;
include/linux/etherdevice.h:209: error: implicit declaration of function &#8216;__rcu_read_unlock&#8217;
/home/<user>/usb-rndis-lite/usbnet.c:183:5: warning: "LINUX_VERSION_CODE" is not defined
/home/<user>/usb-rndis-lite/usbnet.c:183:27: warning: "KERNEL_VERSION" is not defined
/home/<user>/usb-rndis-lite/usbnet.c:183:41: error: missing binary operator before token "("
/home/<user>/usb-rndis-lite/usbnet.c: In function &#8216;init_status&#8217;:
/home/<user>/usb-rndis-lite/usbnet.c:186: error: &#8216;SLAB_KERNEL&#8217; undeclared (first use in this function)
/home/<user>/usb-rndis-lite/usbnet.c:189:5: warning: "LINUX_VERSION_CODE" is not defined
/home/<user>/usb-rndis-lite/usbnet.c:189:27: warning: "KERNEL_VERSION" is not defined
/home/<user>/usb-rndis-lite/usbnet.c:189:41: error: missing binary operator before token "("
/home/<user>/usb-rndis-lite/usbnet.c: In function &#8216;rx_complete&#8217;:
/home/<user>/usb-rndis-lite/usbnet.c:441: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/home/<user>/usb-rndis-lite/usbnet.c:565:5: warning: "LINUX_VERSION_CODE" is not defined
/home/<user>/usb-rndis-lite/usbnet.c:565:27: warning: "KERNEL_VERSION" is not defined
/home/<user>/usb-rndis-lite/usbnet.c:565:41: error: missing binary operator before token "("
/home/<user>/usb-rndis-lite/usbnet.c:798:5: warning: "LINUX_VERSION_CODE" is not defined
/home/<user>/usb-rndis-lite/usbnet.c:798:27: warning: "KERNEL_VERSION" is not defined
/home/<user>/usb-rndis-lite/usbnet.c:798:41: error: missing binary operator before token "("
/home/<user>/usb-rndis-lite/usbnet.c:805:5: warning: "LINUX_VERSION_CODE" is not defined
/home/<user>/usb-rndis-lite/usbnet.c:805:27: warning: "KERNEL_VERSION" is not defined
/home/<user>/usb-rndis-lite/usbnet.c:805:41: error: missing binary operator before token "("
/home/<user>/usb-rndis-lite/usbnet.c: In function &#8216;tx_complete&#8217;:
/home/<user>/usb-rndis-lite/usbnet.c:907: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/home/<user>/usb-rndis-lite/usbnet.c:1171:5: warning: "LINUX_VERSION_CODE" is not defined
/home/<user>/usb-rndis-lite/usbnet.c:1171:27: warning: "KERNEL_VERSION" is not defined
/home/<user>/usb-rndis-lite/usbnet.c:1171:41: error: missing binary operator before token "("
/home/<user>/usb-rndis-lite/usbnet.c:1174:38: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/<user>/usb-rndis-lite/usbnet.c: In function &#8216;usbnet_probe&#8217;:
/home/<user>/usb-rndis-lite/usbnet.c:1174: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function)
/home/<user>/usb-rndis-lite/usbnet.c:1181:5: warning: "LINUX_VERSION_CODE" is not defined
/home/<user>/usb-rndis-lite/usbnet.c:1181:26: warning: "KERNEL_VERSION" is not defined
/home/<user>/usb-rndis-lite/usbnet.c:1181:40: error: missing binary operator before token "("
/home/<user>/usb-rndis-lite/usbnet.c:1199: error: &#8216;struct net_device&#8217; has no member named &#8216;change_mtu&#8217;
/home/<user>/usb-rndis-lite/usbnet.c:1200: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/home/<user>/usb-rndis-lite/usbnet.c:1201: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/<user>/usb-rndis-lite/usbnet.c:1202: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/home/<user>/usb-rndis-lite/usbnet.c:1203: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/home/<user>/usb-rndis-lite/usbnet.c:1204: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/home/<user>/usb-rndis-lite/usbnet.c:1205: error: &#8216;struct net_device&#8217; has no member named &#8216;tx_timeout&#8217;
make[2]: *** [/home/<user>/usb-rndis-lite/usbnet.o] Erreur 1
make[1]: *** [_module_/home/<user>/usb-rndis-lite] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.31-20 »
make: *** [default] Erreur 2
```
Thank you for your help. :)

---

### Post by Smarty_T2 on 2010-06-07
HI. I want to connect internet from my mobile(windows mobile 6) to my PC(ubuntu 9.10), but i cannot do what you stated because that requires internet connection on ubuntu which i cannot access until i connect my mobile successfully. I can though download any required things via windows xp, running on the same PC. Can someone please tell me how do i connect internet on ubuntu.
Thanks

---

### Post by gabe17 on 2010-07-11
Hi! I have a problem with installation of usb-rndis-lite. 

```

~$ chown root:root usb-rndis-lite/
chown: mením vlastníctvo `usb-rndis-lite/': Operation not permitted
~$ sudo chown root:root usb-rndis-lite/
~$ sudo chmod 755 usb-rndis-lite/
~$ cd usb-rndis-lite/

~/usb-rndis-lite$ make
make -C /lib/modules/2.6.32-22-generic/build SUBDIRS=/home/gabriel/usb-rndis-lite modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/gabriel/usb-rndis-lite/usbnet.o
Assembler messages:
Fatal error: can't create /home/gabriel/usb-rndis-lite/.tmp_usbnet.o: Permission denied
/home/gabriel/usb-rndis-lite/usbnet.c: In function ‘usbnet_probe’:
/home/gabriel/usb-rndis-lite/usbnet.c:1199: error: ‘struct net_device’ has no member named ‘change_mtu’
/home/gabriel/usb-rndis-lite/usbnet.c:1200: error: ‘struct net_device’ has no member named ‘get_stats’
/home/gabriel/usb-rndis-lite/usbnet.c:1201: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/gabriel/usb-rndis-lite/usbnet.c:1202: error: ‘struct net_device’ has no member named ‘open’
/home/gabriel/usb-rndis-lite/usbnet.c:1203: error: ‘struct net_device’ has no member named ‘stop’
/home/gabriel/usb-rndis-lite/usbnet.c:1205: error: ‘struct net_device’ has no member named ‘tx_timeout’
make[2]: *** [/home/gabriel/usb-rndis-lite/usbnet.o] Error 2
make[1]: *** [_module_/home/gabriel/usb-rndis-lite] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [default] Error 2

```

Btw I have no problem with shareing the connection throught bluetooth, but it doesn't go throught USB. But on my second PC it goes without any problem and without installation of usb-rndis-lite. Can anybody help?

---

### Post by piergen on 2011-01-12
I also struggle with the lack of internet access on my xubuntu box.
Because of that I can not install anything via terminal, and because of all dependencies I must now be able to connect the HTC touch HD to ubuntu and and to internett.

But is there a way I can check if I allready have svn installed? I mean one would think there should be a clever terminal commando for that? 

What does this code actually say? is **svn **all I need before the code below will execute?

 ```
svn co https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite/
cd usb-rndis-lite/
make
sudo ./clean.sh
sudo make install
```

This problem is bad, pls hlp.

---

