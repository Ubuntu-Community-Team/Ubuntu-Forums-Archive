---
title: "Printer sharing...through a wireless router"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2007-04-03
Hi

I'm attempting to print, from a XP machine to a Kubuntu machine(the one with the printer).

In the Kubuntu machine, I have printer sharing enabled & have the correct CUPS address to enter into the XP machine.

My question...with a wireless router between the two machines, do I have to do something with port forwording of port 631?

Thanks

---

### Post by Limitlesschannels on 2007-04-05
That's an excellent question.  I could definitely use some information on this, too.  Sorry to post a rather useless response to you and possibly instill false hopes, but maybe I can help bump it up to someone more knowledeable.

---

### Post by dbott67 on 2007-04-05
> **DapperMe17 said:**
> Hi

I'm attempting to print, from a XP machine to a Kubuntu machine(the one with the printer).

In the Kubuntu machine, I have printer sharing enabled & have the correct CUPS address to enter into the XP machine.

My question...with a wireless router between the two machines, do I have to do something with port forwording of port 631?

Thanks

If both computers are connected to the internal network, then no (both computers would be on the same LAN segment).

On the XP computer, click on **START > RUN** and type: ```
\\ip.address.of.CUPS\printername
``` and see if XP will recognize the printer.

If it doesn't, you could always trick XP and re-direct the print output.  For example, you could re-direct anything that tries to use LPT3 to the shared printer:
```
net use lpt3 \\ip.address.of.CUPS\printername
```You can use whatever LPT port number you want (i.e. LPT1, 2, 3, etc.).  I would recommend not using LPT1 as it is a real port that you may wnat to connect something to.

After you've mapped LPT3 to the shared printer, install a local printer on XP (choose the make & model of the printer attached to Kubuntu) and use LPT3.

-Dave

---

### Post by DapperMe17 on 2007-04-05
1

---

### Post by DapperMe17 on 2007-04-06
Dave,


The printer is actually attached to the Kubuntu machine, so it must not technically be a networked printer. I intend to send print jobs from a remote XP machine, thru the wireless router & to the Kubuntu machine that the printer is USB wired to.    


I've enabled printer sharing in the Kubuntu Edgy machine & have NOT edited the CUPS.conf file(...localhost:631).

After a server restart, I attempted to reach the printer via the remote XP machine through the add printer interface, using "http://localhost:631/printers/******* (where ***** is the printer name). I also tried [http://192.168.0.*/printers/******](http://192.168.0.*/printers/******).

**Neither worked**. My XP firewall did allow the outgoing traffic, but I received the "unable to connect to a printer" warning box.



Are you sure that I don't have to change anything in the wireless router? How about Kubuntu's Firestarter? CUPS.conf file? Would I need Samba isf it's not a true network printer?

Thanks

---

### Post by tgalati4 on 2007-04-06
I had to set port forwarding (631) for the IP address that the printer is connected to.  Even though the wirless computers are on the same internal subnet, most routers treat wireless as "outside" the network and perform packet filtering.  This is normally a good thing since wireless is susceptible to outside intrusion.

I have it working from both Mac and Ubuntu laptops.  Don't have a wireless windows machine to test with.  The printers (hp laserjets and Officejets) are hung off of a Dapper machine.

cupsd.conf can get fiddly.  I can post mine if you can't get it work.

Let us know what configuration works for you.

---

### Post by dbott67 on 2007-04-06
Hi dapperMe17,

I haven't shared a printer using CUPS before, although I just set one up now & seemed to have success.

For the record, here are my specs:

1. Router: D-Link DI-614+
2. Desktop PC: Ubuntu 6.06 LTS, Wired Connection, IP: 192.168.1.106
3. Laptop: XP Pro, Wireless, IP:192.168.1.105
4. Printer: HP PhotoSmart 1315 (Parallel) connected via HP JetDirect.  JetDirect connected via ethernet cable 192.168.1.10 port 9100.

Here's the HOWTO I followed:
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

[B]_ A summary of my steps:_

[/B] 1. Installed the printer on my Ubuntu box (as a network printer using **HP JetDirect** connection type)
2. Under **Printers > Global Settings** I selected '**Detect LAN Printers**'
3. Edited **/etc/cups/cups.d/ports.conf file** (slightly different from the HOWTO, as the comments refer you to edit this file instead):
```
dbott@thedrake:~$ sudo nano /etc/cups/cups.d/ports.conf
Listen localhost:631
Listen /var/run/cups/cups.sock
[COLOR=Red]**Listen 192.168.1.106  ***[COLOR=Blue]<-- my Ubuntu IP address[/COLOR]*[/COLOR]

```4. Restarted the CUPS daemon:
```
sudo /etc/init.d/cupsys restart
```5. From my XP box I browsed to [http://192.168.1.106:631/printers/](http://192.168.1.106:631/printers/) and got the page below (see screenshot below).
6. In the Windows 'Add Printer Wizard' I used the following URL:
```
http://192.168.1.106:631/printers/PhotoSmart-P1315
```

So, I would suspect that it's either step #3 above (add your Kubuntu IP to the ports.conf file) or an iptables issue.  Can you post the output of a few commands for me:
```
dbott@thedrake:~$ [COLOR=Red]**netstat -ln -A inet**[/COLOR]
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:46019         0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:5901            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
[COLOR=Red]**tcp        0      0 192.168.1.106:631       0.0.0.0:*               LISTEN ***[COLOR=Blue]<-- this is the key[/COLOR]*[B]
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN[/B][/COLOR]
tcp        0      0 127.0.0.1:49689         0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
udp        0      0 192.168.1.106:137       0.0.0.0:*
udp        0      0 0.0.0.0:137             0.0.0.0:*
udp        0      0 192.168.1.106:138       0.0.0.0:*
udp        0      0 0.0.0.0:138             0.0.0.0:*
udp        0      0 0.0.0.0:177             0.0.0.0:*
udp        0      0 0.0.0.0:68              0.0.0.0:*
udp        0      0 0.0.0.0:631             0.0.0.0:*


```and 
```
dbott@thedrake:~$ [COLOR=Red]**sudo iptables -L**[/COLOR]
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```As tgalati4 suggests, it *may* be the router, but in my experience with routers (mainly the mainstream brands; D-Link, Linksys, Netgear) I have never seen wireless treated differently than any other internal wired connection.  So, it may depend on the make & model of your router.  What type of router do you have?

-Dave

---

### Post by DapperMe17 on 2007-04-08
Wow! Thanks for that, Dave. 

I've seen your prior help & I can't believe how much you go out of your way to help with these issues. High praise goes out to ya!

Just starting the .conf file updat & will let you know how it goes....:popcorn:

---

### Post by DapperMe17 on 2007-04-08
Dave, 

Your directions worked flawlessly & to-a-T!

I'm up & running with the CUPS wireless printing.


Thanks again, for taking the time to be so detailed. It's the sharing of know-how from folks like you that keep the newbies rolling!!! 
It's appreciated.

---

### Post by tgalati4 on 2007-04-08
Great How-to.

I needed to Port Forward 631 on my router as I needed to print from a friend's house to my printer at home.  It also took care of my internal wireless printing problems.  This was using a Netgear A and G Band Wireless, 4-port router.

Your How-To will help others in printer purgatory.

---

### Post by dbott67 on 2007-04-08
@DapperMe17: Glad I could help... I was a newbie not too long ago, so just keep working at it. The only thing I can say is that trying to help other folks has taught me a lot more than I could ever learn on my own.  I like to post in the Network area (it's what I do for a living), but if I see an interesting problem I like to try to offer assistance as it generally teaches me something new to add to the toolkit.

And the reason I like to provide fairly explicit instructions is for a few reasons:

1. I generally don't know the skill-level of the person posting, so I err on the side of newbie! :)
2. It may help someone that is just searching the forums looking for an answer many months from now.
3. It helps me learn.

@tgalati4: Thanks.  You would definitely need to forward port 631 if you were trying to access the printer remotely.  As mentioned earlier, as far as I've seen, internally connected computers would not require port 631 forwarded.

As a bit of a security aside, you may want to change the external listening port on your router from 631 to another number, such as 6310.  You would forward external port 6310 to 631 internally.

If you wanted to connect to your home printer, the URI would be:
```
http://your.external.ip.address:6310/printers/name_of_your_printer
```The router would then forward the request internally to:
```
http://your.internal.cups.pc:631/printers/name_of_your_printer
```It's a bit of "security by obscurity", but with all of those automated scanners looking for "known" open ports (ftp, telnet, ssh, netbios, CUPS, etc.), it may just keep your computer under the radar.  There may be some other security settings that you can employ to protect rogue pranksters from sending a 10,000 page full colour document to your printer.

Just by changing my ssh port from 22 to some other number, I've gone from hundreds of attempts per day to zero.  Not one in over 4 months.  I've also installed DenyHosts from the repos to provide another layer of security.

-Dave

---

### Post by 11hjpphty76lkjj on 2007-04-09
Dave,

Just something to consider--if you are using HPLIP with your HP Photosmart printer you can use the hp-setup tool to automatically configure your networked printer. Regardless of wifi/eth connection if your system can ping the printer (and assuming snmp is working) you can configure the printer in seconds.

Hope this may help you or someone else in the future.

---

### Post by tgalati4 on 2007-04-10
Good tip on port swapping.  I also needed to port forward 631 so that I could access my CUPS server machine (not my localhost:631) so that I could log in remotely (via wireless) to perform some printer and job maintenance.  This was from a wireless Dell runnng Dapper Drake to a wired desktop also running Dapper Drake.  The router was a Netgear WGU624 (wireless A and G band with a wired 4-port.)

I had stateful packet inspection turned on but no other firewalls turned on.  I'm operating this behind a DSL modem.  I don't know if that would make a difference.

Another printing tip for HP printers:

Some printers have a jetdirect or ethernet plug-in cartridge.  If your printer has a slot, you can usually find these on ebay for $20 to $40.  This will convert a USB printer into an networked printer.  Jetdirect also has a web-based interface that allows configuration and ink levels without going through CUPS.  I have such a printer set up through CUPS and directly through ethernet and each works fine allowing a backup up queue if one gets balled up.

One caution, most HP printers that I know of will not allow both USB and Jetdirect ethernet at the same time.  It's an either or proposition.

Good luck all.

---

### Post by DapperMe17 on 2007-09-07
> **dbott67 said:**
> @DapperMe17: Glad I could help... I was a newbie not too long ago, so just keep working at it. The only thing I can say is that trying to help other folks has taught me a lot more than I could ever learn on my own.  I like to post in the Network area (it's what I do for a living), but if I see an interesting problem I like to try to offer assistance as it generally teaches me something new to add to the toolkit.

And the reason I like to provide fairly explicit instructions is for a few reasons:

1. I generally don't know the skill-level of the person posting, so I err on the side of newbie! :)
2. It may help someone that is just searching the forums looking for an answer many months from now.
3. It helps me learn.

@tgalati4: Thanks.  You would definitely need to forward port 631 if you were trying to access the printer remotely.  As mentioned earlier, as far as I've seen, internally connected computers would not require port 631 forwarded.

As a bit of a security aside, you may want to change the external listening port on your router from 631 to another number, such as 6310.  You would forward external port 6310 to 631 internally.

If you wanted to connect to your home printer, the URI would be:
```
http://your.external.ip.address:6310/printers/name_of_your_printer
```The router would then forward the request internally to:
```
http://your.internal.cups.pc:631/printers/name_of_your_printer
```It's a bit of "security by obscurity", but with all of those automated scanners looking for "known" open ports (ftp, telnet, ssh, netbios, CUPS, etc.), it may just keep your computer under the radar.  There may be some other security settings that you can employ to protect rogue pranksters from sending a 10,000 page full colour document to your printer.

Just by changing my ssh port from 22 to some other number, I've gone from hundreds of attempts per day to zero.  Not one in over 4 months.  I've also installed DenyHosts from the repos to provide another layer of security.

-Dave

**Would I change my router's port forwarding & would I have to adjust the CUPS.conf?**

---

### Post by dbott67 on 2007-09-07
> **DapperMe17 said:**
> **Would I change my router's port forwarding & would I have to adjust the CUPS.conf?**

Leave CUPS.conf configured on port 631.  On your router you need to forward external TCP port 6310 to the internal IP address of your server on TCP port 631.

-Dave

---

### Post by DapperMe17 on 2007-09-07
Thanks Dave!

I'll try that.

---

### Post by DapperMe17 on 2007-09-07
Dave,

I'm assuming the changes are to the router's port forwarding section....
one new rule for port 6310, forwarded to my external IP(the static one provided by my IP company) & another rule for port 631, forwarded to the CUPS server PC(192.168.0.xxx)?

---

### Post by dbott67 on 2007-09-07
I've got a D-Link DI-614+ and it's just a single rule on mine in the "Virtual Servers" section (see screenshot).   Then when I need to connect, I connect to the public IP address provided by my ISP:

[http://my.external.ip.address:6310/printers/name_of_printer](http://my.external.ip.address:6310/printers/name_of_printer)

from there, the router forwards the traffic to:

[http://192.168.1.106:631/printers/name_of_printer](http://192.168.1.106:631/printers/name_of_printer)


What make & model router do you have?

-Dave

---

### Post by DapperMe17 on 2007-09-08
I'm running the system thru a D-Link as well, WBR-1310. I don't see a section titled "Virtual Server" in the Advanced section, or the others for that matter. 

Possibly not an option available to me with that router?

---

### Post by dbott67 on 2007-09-08
I found an emulator at the D-Link site ([http://support.dlink.com/emulators/wbr1310_revA/adv_portforward.htm](http://support.dlink.com/emulators/wbr1310_revA/adv_portforward.htm)).  The option is under **ADVANCED > PORT FORWARDING**.

Using the emulator, it appears as though you can't specify a public and private port, although the **SUPPORT > PORT FORWARDING** section, says that there is:
> 
**Port Forwarding **
Port Forwarding can be used to open a port or range of ports to a device on your network . To use them, click the checkbox to Enable the entry, select a pre-defined service from the Application Name drop down menu, select a computer from the Computer Name drop down menu, and click Save Settings. The Application, Computer, and Ports can also be filled in manually if your Application or Computer is not listed in the drop down menus. 
 ***Name *** - The name for the service being provided by the device on your LAN that uses the ports being opened. 
 ***IP Address *** - The server computer on the LAN network that the specified ports will be opened to. 
 ***Application Name *** - This contains a list of pre-defined services. 
  ***Computer Name *** - This contains a list of the devices on your network which have obtained an IP Address from the router. 
  [COLOR=Purple]***Public Port *** - The port number that users on the Internet will use to access the defined service. 
***Private Port *** - The port number of the service being hosted by the server computer on the LAN. [/COLOR]  
 ***Traffic Type *** - The protocol used by the service the device on your LAN is providing.The PUBLIC and PRIVATE port which is where you would actually add the specific ports (PUBLIC=6310, PRIVATE=631).  Perhaps a firmware upgrade will add this feature if your router lacks it.

In my example screenshot, I just set the port to 631, but if your page has the public and private port option, just set it to 6310 and 631, respectively.

-Dave

---

### Post by DapperMe17 on 2007-09-09
Thanks for that, Dave!

Yes, that is the same router firmware that this system is running. 

I'll have to check the firmware update. Although, I hesitate as the router is one of those "cruddy" 524's that most decide to chuck against the wall, but "just happens" to run flawlessly with the 1310 firmware. I cringe at messing with a perfect 524:)

---

### Post by Guns90 on 2007-09-12
Hello everyone.  I would also like to print from my children's XP machine to a printer USB connected to my Feisty machine using my Linksys WRT54GL router.  I'm getting lost in the howto when it comes to IP addresses and servername, printername (I don't know what mine is or how to get them).   Could I get some assistance please?  Thanks Gary

---

### Post by DapperMe17 on 2007-09-13
Follow DBott's reply #7 within this thread. He has a screenshot there as well.

1) On Feisty (which is the server your USB printer is attached to), you should go to your settings for CUPS & allow printer sharing. On the main CUPS page, you'll see your printer name, which you would have entered when originally setting up CUPS printing. 

2) In a Feisty terminal, scan for your IP address(the one for your Feisty machine, not your IP address...should be something like 192.168.0.101 or 102...).

3) Once you have that, go to the Control Panel in XP, & select the Printers & Fax tab. You'll continue with "Add Printer", then select "Network printer....", then select the "URL" line & type in something like 
[http://192.168.0.103:631/printers/HPOfficejet2100](http://192.168.0.103:631/printers/HPOfficejet2100), then continue with selecting the driver that matches your printer & select as default printer. Your done. Both PC's will have to have open internet connections in order to communicate.

Note: in the above http......only change the "192..." to whatever your Feisty IP is (keep :631 at the end), then change only the "HPOfficejet..." to whatever your printer name is on the Feisty CUPS page. Keep the rest the same.

You shouldn't have to do anything with Port Forwarding in your router.

:popcorn:

---

