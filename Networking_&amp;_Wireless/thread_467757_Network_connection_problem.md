---
title: "Network connection problem"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by youngbill on 2007-06-08
I am a new Lenix and ubuntu user.  I installed WinXP Pro x64 and ubuntu 7.04 for dual booting on my new  Core 2 Duo computer.  I have a wired LAN with Linksys router, static addressing, and DSL modem.  My new XP Pro OS connects to my LAN, sees all the devices on my LAN (including a print server), and connects to the Internet through my router and DSL modem.  The LAN works properly.

I installed ubuntu 7.04 using the 64-bit live CD.  The installation was smooth without problems.  I configured network settings using the same static IP address, subnet mask, gateway, and DNS servers that I use successfully in WinXP Pro.  I confirm that my wired connection is activated (little box is checked).  But, ubuntu does not appear to connect to my LAN.  When I go Places  > Network, a Windows Network icon appears, but clicking on it shows none of the components on my LAN.  Firefox cannot access the Internet.

I tried a different static IP address for ubuntu without success.  I booted the Live CD and got exactly the same results when I setup the network.

Since the WinXP Pro OS on the same computer is successful, I assume the problem is not the network hardware.

My Ethernet is on my MSI P965 Platinum motherboard.  MSI manual says supports 10/100/1000 PCI Express by Realtek8111B.  WinXP Pro device manager reports: Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC.  Any known problem or special driver needed for Linux/ubuntu with this network hardware?

Following is a listing from the ifconfig command:

eth0   Link encap:Ethernet  HWaddr 00:19:DB:4E:62:03
          inet addr:192.168.1.25  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9228 (9.0 KiB)  TX bytes:9228 (9.0 KiB)

Any clue here?  The inet address is what I assigned for ubuntu.  I do not see the gateway address for my router (192.168.1.1).  I do not know what Bcast means.

I hope I am missing something simple.  I searched ubuntu help documents and the online forums without finding anything useful for my problem.

I would appreciate some help.  I am brand new to Linux and ubuntu so keep your suggestions simple.

 Thanks

---

### Post by croto on 2007-06-08
Hi,

I suspect there's a problem with the routing table. How did you setup the network? I suggest doing it through System->Administration->Network. Make sure that in addition to the IP and netmask you specify a gateway. You can check the routing table with the command "route -n". Please post the output of that command. Another possible problem is that you may not have set DNS servers. Under System->Administration->Network, there's a tab DNS.
I guess this problems you're having are because you don't seem to be using DHCP. When you use it, all these things get set up automatically.

OK, summaryzing:

1) After configuring the network, try: ping 192.168.1.1    If you get replies, it means that you can talk to the router, which is a good thing.
2) If #1 worked, try ping 64.233.169.104     If that works, you are talking to google.com, so you are getting to the internet.
3) Then try ping [www.google.com](www.google.com)    If you get something like unresolved host, it's indicating there's a problem with DNS settings.

---

### Post by youngbill on 2007-06-08
Thanks for your suggestions.

I setup network parameters by System > Administration > Network.  As I said in my original message, I used the  IP address, Subnet mask, Gatewaay address, and DNS Servers that work successfully in WinXP Pro.

I have five components on my LAN: three computers, printserver and network hard drive.  Several years ago, I had problems with DHCP reassigning different IP addresses.  I switched to static addressing and have had no problems since, except now getting ubuntu to connect.

The results of the route -n command are:

Kernal IP routing table
Destination       Gateway          Genmask               Flags    Metric   Ref      Use   Iface
192.168.1.0     0.0.0.0            225.225.225.0      U          0           0             0    eth0
169.254.0.0     0.0.0.0            225.225.0.0          U          1000     0             0    eth0
0.0.0.0             192.168.1.1    0.0.0.0                  UG        0           0             0    eth0

Any clues here?

Pinging my router (192.168.1.1) by System > Administration > Network Tools > Ping gives no results.  All times are zeros.

I failed to note in my original message that I am using the 64-bit version of ubuntu 7.04.

---

### Post by croto on 2007-06-08
How about the netmasks in the ouput of route? Was that a typo? Insted of 225 it should be 255.

EDIT: I was doing some research and it seems that you may have to install the driver manually. Check [http://www.realtek.com.tw/download](http://www.realtek.com.tw/download). I'll post again if I find something out.

EDIT2: Could you post the output of dmesg, lsmod, and lspci ?

---

### Post by youngbill on 2007-06-09
Hi Croto,

Thanks for responding.  I relisted the routing table (route -n).  You are right the 225s should be 255s.  My mistake.  I should have cut and pasted.

If I need to manually install a driver, I will need some instructions.  I am new to Linux and ubuntu.

As you requested, I attached txt files for the output of dmesg, lsmod, and lspci.  dmesg was too big for your upload so I broke it into two files, dmesg1 and dmesg2.

I am waiting with interest for your analysis of my connection problem and, hopefully, a solution.

Thanks again for helping me.

---

### Post by croto on 2007-06-09
Hey Bill,

The command lsmod lists all kernel modules (drivers) that are loaded. You will notice that there's a module r8169. dmesg shows the kernel messages, and there is a line that indicates that r8169 is being used for the ethernet card (eth0). I believe that that's not the right driver for your card. So what you would have to do is remove that driver and install the right one. 
The output of lspci (which lists the pci devices in your system) shows your network card is RTL8111/8168B PCI Express. I went to the Realtek web page, and they have a linux driver for that card:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

You want to download the "Linux driver for kernel 2.6.x (Support x86 and x64)". This is where the problem might begin, because you don't have any working network card in your computer. Any chance you might get another network card? Ok, I'll assume for now that's solved.

Once you have that driver, you'll have to compile it. What you downloaded is the source code and you need to convert it to machine code to run it. For that you need to install some tools necessary for compiling. With a running network connection, run the following commands:
```
sudo aptitude install build-essential
sudo aptitude install linux-headers-`uname -r`
```
All right, now you have to unpack the driver source: run
```
 tar xjf 8168-8.001.00.tar.bz2
```
in the folder where you downloaded the driver.
That will create a folder, r8168-8.001.00, so change there and compile the source:
```

cd r8168-8.001.00
make clean modules
sudo make install
sudo depmod -a

```
(if something goes wrong here, please post the output of those commands)

That should compile it and copy it to the system folder where it has to be. Well, if everything went fine, it's time to load it in the kernel. First unload the incorrect driver:
```

sudo modprobe -r r8169

```

and then load the newly compiled one:
```

sudo modprobe r8168

```

You can check that it's loaded by running lsmod, and checking the driver it's there. If you run ifconfig -a, you should see the network interface (eth?). Try to configure the network and see if it works. If it doesn't please post the output of dmesg after loading the new driver.

If it works, I'll send you instructions to make these changes permanent. Good luck!

---

### Post by youngbill on 2007-06-09
Hi Croto,

Thanks, you have suggested good things for me to do.  However, I have no network connection in ubuntu, hence cannot download.  I can download in my WinXP, save to CD, and read CD into ubuntu.  If this works, I know how to download the driver from Realtek and save to CD, but how do I down load the Linux tools?  From what website?  What tools?  How would your commands change to work from a CD?

Thanks again.

---

### Post by croto on 2007-06-09
Yep, I was afraid that was going to be problematic.... I think the packages you need are on the Ubuntu CD. Try this: insert the Ubuntu CD and type the following:

```

sudo apt-cdrom add
sudo apt-get update
sudo aptitude install build-essential
sudo aptitude install linux-headers-`uname -r`

```

Did it do the trick?

---

### Post by youngbill on 2007-06-12
Unfortunately, that did not work.  I attached a txt file showing the results of your first three commands.  I assume E: means an error.  There are four of them.  Not so good I think.

What next?  Thanks for your help.

---

### Post by croto on 2007-06-12
did u have synaptics package manager open at the same time? It has to be closed while you use apt-get.

---

### Post by youngbill on 2007-06-13
No.  To the best of my new-user knowledge synaptics package manager was not open.  Tonight, I restarted ubuntu.  I went System > Administration > System Monitor and could find no process that looked like synaptics package manager.  There is nothing on my desktop that looks like synaptics package manager.  However, I am not familiar with synaptics package manager.  Could it be running in the background? 

I reran your first three commands and got the identical results that I sent you in the attached txt file of  my previous post.

What now?  Is there a tutorial somewhere that details what we are trying to do?  I would like to learn what we are doing.

Thanks

---

### Post by croto on 2007-06-13
Hey, I'm sorry this is taking long, I hope it's not too frustrating to you ;) You're gonna get that card up and running soon. 

I don't know why you're getting that error message. It may be caused by some problem or crash during a previous apt-get operation. The thing is I googled it and I found this guy who seems to solve it: [http://www.openrhino.com/?q=node/9](http://www.openrhino.com/?q=node/9) . After doing that, you don't need to run the **sudo apt-cdrom add**, just run the other commands. I hope it's gonna work this time, let me know!

As for a tutorial, you could try [https://help.ubuntu.com/](https://help.ubuntu.com/) Check out the "Adding and Removing Software" section.

---

### Post by youngbill on 2007-06-14
I leave tomorrow morning for two weeks out of town.  I will pick this up when I return and let you know the progress.

Thanks for your help.

---

### Post by youngbill on 2007-07-07
Finally, I am back from out of town and have time to return to this problem, namely  not connecting to my local network and the Internet with my newly installed Fiesty Fawn 7.04 64bit.  Previously, I had tried different things off and on for several weeks.  See previous posts.

I started up my computer, after it being off for three weeks.  Low and behold it was connected to the Internet and offering 68 software updates to Fiesty Fawn.  I do not know what happened, but my problem is solved for now without me doing anything but being away for three weeks.   Updates are installed and I can browse.  Thanks Grotto for your suggestions.  I have printed them in case I need them in the future.  Any ideas why my network connection suddenly worked?

---

### Post by Wizang on 2007-07-07
I'm almost sorry to see this problem resolved so miraculously. It seems I have the same exact issue with my Realtek card of the same version. Any more insight into how it got fixed?

---

### Post by croto on 2007-07-07
Hey youngbill, I'm glad to hear the problem is solved! I'm a bit puzzled about how it got fixed... I have no idea what happened, because as far as I knew that card wasn't supported by ubuntu, even though the linux drivers existed. Apparently I was wrong. I would like to know if you're using the same driver as before. Could you please post again the output of ** dmesg ** and ** lsmod **?

Wizang: if you check this thread you'll see the only thing we did was trying to install the C compiler to compile the drivers. I wonder if that did anything... I don't know if youngbill downloaded a new ubuntu CD (that may have kernel updates??), if they got installed, or what... I hope youngbill's new dmesg and lsmod will shed some light on this miracle.

---

### Post by youngbill on 2007-07-10
The miracle has gone away!  I can no longer connect to the Internet.  I had several days of bless as I strove to switch from Windows to Ubuntu.

Same problem as before when I started this thread.  I restarted the computer, no success.  I shutdown and restarted, no success.  I recycled my router, no success.  Recall, this is a dual-boot computer with Win XP x64 and Ubuntu 7.04 64-bit.  Booting into WinXP x64, the Internet connection works, as before.

I prepared the listings Groto requested and started Firefox to send them using Ubuntu, but as reported above Firefox will not connect.  I copied the files to my old computer and am sending them from my old computer.  (My new computer has a shared FAT32 partition between WinXP and Ububtu, so transferring files is easy.)  The files are attached.  Again, dmesg is too large for the Ubuntu forum, so I split it into two files: dmesg3 and dmesg4.  Recall, that dmesg1 and dmesg2 are the files I previously sent.  I appended a 2 to the other two files to distinguish them from the files I sent earlier.

In answer to your pondering, I have not downloaded and installed a new Ubuntu.  When the Internet connection was working, I got an automatic message about 68 new updates.  I downloaded and installed these updates.  I believe one of the updates was a new kernel.

So, an intermittent problem.  This may change your diagnosis.  I conclude that it is not a hardware problem, since WinXP x64 connects.  I await your recommendations after you review the attached files.

---

### Post by croto on 2007-07-12
Hey, how is it going? 

I checked your dmesg, it looks the same as the ones you sent before... if it happens to work again, try to get again the output of dmesg, so we can compare. One thing you can try is to unload the driver and load it again to see if it helps (since there seems to be some randomness, I figured it wouldn't hurt...):

```

sudo modprobe -r r8169
sudo modprobe r8169

```

On a more systematic approach, why don't you try to compile the driver (the one I thought is the right one) you downloaded before? I remember you were trying to install the compiler from the CD. I'd suggest we should go in that direction.

---

### Post by Rui Pais on 2007-07-19
> **youngbill said:**
> The miracle has gone away!  I can no longer connect to the Internet.  I had several days of bless as I strove to switch from Windows to Ubuntu.
Hi.
You miracle probably happened cause you had your computer disconnect from power for a long time... and come back later when you reconnect using Windows.
Theres [a knowing problem with that cards+wake-on-lan]("http://gentoo-wiki.com/HARDWARE_RTL8168#Troubleshooting") that linux can't handle but Window does ok.

Seems that the problem can be workaround by set wake-on-lan on (enabled), using windows device manager.

*Edit:*
seems that the previous link (to gentoo-wiki) is down most of the time.
[here is a link]("http://forums.notebookreview.com/showpost.php?p=2077619&postcount=39") to a post in a forum that explains how-to do it with images.

You may give it a try.
Good luck

---

### Post by nickgraber on 2007-07-25
I am also attempting to use the same card I works with the inluded ubuntu driver and the compiled one from realtech but it runs at speeds slower than a 100Mb/s card :(  I will atemp your directions here tomarrow.  I have also noticed that ethtool cant seem to turn off the autoneg to off.

---

### Post by armand_v on 2007-07-25
I'm having a very similar problem also with a realtek 8168 network card, the network interface only gets an ip assigned from dhcp if the cable was plugged before boot, if I plug the cable after linux loads I have exactly the  same behavior as youngbill, the interface shows up on iface but is unable to get a dhcp lease from the router (wrt54g dd-wrt).
I followed the recomended steps and downloaded the drivers files from the realtek web page and compiled them, they created a new module called r8168.ko instead of the r8169.ko that comes with ubuntu, if I type in the command line **sudo modprobe -r r8169** and then **sudo modprobe r8168** the interface gets recreated and I'm able to get a lease from the router, but I have to type the former commands to get it working every time I power up the machine and is a hassle.
I need the instructions to make the changes permanent or maybe a script to get it done automagically :)
I'm running Kubuntu Feisty, I also have and Intel 3945 wireless card.
Please help :confused:
Sorry for my bad english

---

### Post by croto on 2007-07-26
Hey Armand, nice to hear that the new driver seems to be working better. To make the changes permanent, you'd have to tell Ubuntu not to use the driver r8169. For that you need to edit the file /etc/modprobe.d/blacklist   (you need to be root). I guess you can use the command

```

gksudo gedit /etc/modprobe.d/blacklist

```

and append at the end the following line:

**blacklist r8169**

then save the file. That will prevent the kernel from loading the r8169 driver. I expect, but I may be wrong, that then it will load the new driver when you boot up. Please give it a try. If something goes wrong, please indicate if it loaded or not the new driver. If it didn't we'll try to force ubuntu to load it. 

Good luck!

---

### Post by armand_v on 2007-07-26
I just tried to blacklist the r8169 module, but it keeps loading, I read some where that is not possible to blacklist some kind of modules, so maybe that is the case.

But anyways if I unload the module manually and then load it again it works properly, with any of the two drivers.

Could there be a way to make this with a script?

Thanks for your help.

---

### Post by croto on 2007-07-26
you can put those two commands in the /etc/rc.local   in the line right before the ** exit 0 **. That script gets executed after the computer boots up. See if that does the trick. I'll post back if I find a more elegant solution. I'll see also if I find something about blacklisting that module.

---

### Post by armand_v on 2007-07-26
Thanks, that did the trick.

---

### Post by youngbill on 2007-08-01
Hi All,

Youngbill is back.  I had to go out of town for about three weeks.  I am now back on my connection problem.  Since my computers were turned off during my absence, I was hoping I could connect to my network and the Internet, as happened once before automatically when my computers were off for several weeks.  (See my earlier posts.)  No miracle this time -- no connection.  Firefox cannot connect to the Internet.

However, I get a pop-up message that updates are available.    How did ubuntu on my computer know updates are available if there was no network/Internet connection?  When I use Update Manager, the update is for libmagick9.  I get a warning that the install software cannot be authenticated.  Should I be concerned?  When I proceed, the update will not download.  After a long wait I get the error message: "W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick9_6.2.4.5.dfsg1-0.14ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick9_6.2.4.5.dfsg1-0.14ubuntu0.1_amd64.deb)
  Could not resolve 'security.ubuntu.com."

Again, how did ubuntu on my computer know updates were available?  Do I have connection at a lower level but not at the user level?  Recall that I was connected successfully for several days.  (See my earlier posts.)

I am pleased to see the suggestions others have offered.

On July 12, post 3009141, croto suggested unloading and reloading my network  driver.  I did that with no success.

Further, croto suggested that I download the proper driver from RealTek for my RTL8111/8168B network card, compile it, and install it.  I downloaded r8168-8.001.00tar.bz2 from RealTek.  I tried to load compilation tools from my ubuntu CD without success.  I got error messages.  Croto looked at the errors and suggested I try [http://www.openrhino.com/?q=node/9](http://www.openrhino.com/?q=node/9) that describes a solution for my errors.  I have copied the instructions from this website.  I will try them and report progress.

On July 19, post 3046423, Rui Pais suggested a wake-on-lan solution.  In Windows, I confirmed that wake-on-lan is disabled.  Thus, I conclude that this is not my problem.  Is this a proper conclusion?

On July 25, post 3082030, armand_v reported a problem similar to mine.  In the subsequent series of post between armand_v and croto, armand_v successfully got a network connection.  This is good news!  I have hope that I also can be successful.

So, using the info from the above posts, I am ready to try again.  Will let you know my progress.

---

### Post by youngbill on 2007-08-03
Hi croto,

Recall that I am trying to install a new network card driver.  I successfully downloaded the driver.  Now, I must compile it.  Since I cannot connect to the Internet, you gave me a set of commands to get the compiler software from my Ubuntu CD.  Your first two commands are:

sudo apt-cdrom add
sudo apt-get update

Previously, the second command produced a cannot lock error.  You sent me to openrhino for a solution.  I used the commands in that solution.  Next, I repeated your above two commands.  Now, the second command no longer causes a cannot lock error.  Good.  A little progress.

However, now the second command tries to connect to the Internet, which of course it cannot do.  After reporting failure to connect, it tries again.  This continued until I closed the terminal session.  I attached a txt file of my terminal session.  I deleted the many retrys to connect.

What next? Do I really need your second command?

---

### Post by croto on 2007-08-03
Hi Bill! How are you doing? The command **apt-get update** is trying to see what packages are available from the sources indicated in the file /etc/apt/sources.list   That file typically points to the Ubuntu repositories and the CDROM. Every time you change the list of repositories (as for example when we added the cdrom) you need to run **apt-get update**  so that your system knows what new packages are available (and what packages are not available any more). I'd suggest the following:

1) Make a backup copy of /etc/apt/sources.list:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

```

2) Comment out all lines in /etc/apt/sources.list that refer to repositories on the internet. Leave uncommented the line referring to the cdrom only (every line that starts with a symbol "#" is a comment and is ignored by apt-get). You'll need to edit the file as superuser though:
```

gksudo gedit /etc/apt/sources.list

```

3) Run **sudo apt-get update** again.

Good luck!

---

### Post by Frans-Joost on 2007-08-06
Hello Bill, Croto and Rui Pais,

I have had the same problem with the same ethernet card.
At first I installed a XP-version without any ethernet drivers,
this was followed by the Ubuntu feisty instalation and the dual boot worked perfectly.
Until I installed the ethernet drivers in windows. It seems that the windows drivers influence the drivers in ubuntu or something like that.
I reinstalled everything without succes.

I read this Thread and saw that Rui Pais was talking about the wake-on-lan setting in windows, I also noticed Bill said this wasn't the problem as it was disabled.

I turned my wake-on-lan settings on and booted ubuntu.
The card seems to be working flawless now so I hope this will help you Bill.

I hope this is a permanent solution, I do not know why this worked.
If somebody knows please tell me.

Thanks everybody!

---

### Post by youngbill on 2007-08-07
Hi All,

Finally, I ran all of Croto's commands to install the proper network driver (RealTek 8168) for my computer without generating errors.  Ubuntu had installed 8169.  The RealTek website reports that 8168 should be used on my computer.  Croto suggested that this causes my failure to connect in Ubuntu.

However, despite successfully running his commands, I still cannot cannot connect to the Internet in Ubuntu on my dual boot WinXP Pro/Ubuntu computer. WinXp Pro connects successfully.   Before I get back to Croto for more help, I want to review armand_v's experience and study the readme file that came with the 8168 network driver.  Maybe I can resolve this myself.  I like to try.

Before I had time to do the above tasks, I got Frans-Joost's post that ENABLING WAKE-ON-LAN IN XP may fix the problem.  I immediately shutdown Ubuntu, booted WinXP Pro, enabled wake-on-lan, shurdown XP, rebooted Ubuntu, and immediately connected to the Internet through Firefox.  I assume that the 8169 driver is still installed, since I have not made 8168 permanent.  I will confirm this.

WHAT A WEIRD SOLUTION.  As Frans-Joost said, can someone explain this?  The wake-on-lan info must be stored outside the operating systems on the motherboard somewhere.  My LAN hardware is on my motherboard.  I carefully read my motherboard manual, especially the LAN part, and found no mention of wake-on-lan.  I scanned my BIOS setup and found nothing about wake-on-lan.  I Googled "wake-on-lan xp linux" and got over 300K hits.  An understanding must be therein.  When I have more time I will explore these websites.

Is this a common problem on dual boot XP/Ubuntu systems?

I surely misunderstood the post from Rui Pais about wake-on-lan.  I should have tried both enable and disable.

In the next few days, I want to try to get my proper network driver (8168) working.  Since armand_v was successful without, I assume, enabling wake-on-lan, I expect success eventually.  Later, I will post my progress and seek help from Croto if I need it.

Thanks to all for your help.

---

### Post by youngbill on 2007-08-15
Hi Grotto,

Following your commands, I have succesfully installed the new driver r8168.  When I run lsmod, the driver is listed.  When I run ifconfig -a, there is no eth? --  only a lo.  When I go System>Administration>network, only the modem connection shows -- no wired connection.

Any suggestions for enabling eth0?

With wake-on-lan enabled and the r8169 driver that Ubuntu installed, I can successfully access all my network components -- other computers, print server, network harddrive, and the Internet.  I go Places>Network and type smb://"the_IP_adress" in Location to access the network components.  Although the Windows Network and my Workgroup appear, when I click on Workgroup I get a message that the folder contents could not be displayed.

With wake-on-lan enabled, the r8168 driver does not access the network.  Although r8168 is my proper driver according to RealTek, should I give up and just use r8169, which is working?  Any thoughts.

Bill Young

---

### Post by Rui Pais on 2007-08-18
Hi everybody,
late answer, just return from my holidays now :)

> **Frans-Joost said:**
> ...
I have had the same problem with the same ethernet card.
At first I installed a XP-version without any ethernet drivers,
this was followed by the Ubuntu feisty instalation and the dual boot worked perfectly.
Until I installed the ethernet drivers in windows. It seems that the windows drivers influence the drivers in ubuntu or something like that.
...

Glad it that my suggestion worked.
The windows driver do not in fact influence ubuntu drivers in anyway (that would be impossible). 
The change the card (the hardware) directly, turn it off when windows shuts down.
Linux drivers isn't capable of turn it on again (not even to check if it's off or absent, i think).
Lucky theres that workaround with wake-on-lan setting :)


**@youngbill**

Hi,
sorry my suggestion was too vague :( 
i will change my post to make it more clear.. specially since it seems that the link (to gentoo-wiki, where the issue it's described in detail) seems to be down most of the time latetly.

About your question on which driver use, i would stick with ubuntu default one, as long as it works. usually Linux drivers by outside sources, manufacturers included, are not very good, nor well tested.

---

