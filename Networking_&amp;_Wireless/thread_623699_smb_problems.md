---
title: "smb problems"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by Anders J on 2007-11-26
Running 7.04 since 9 months and have had my windows/smb network with no problems, I have seen other (win-) machines and network disks. But suddenly this has changed, under Places/Network an icon Windows Network is there (expected) and then my network "hem" (expected) and when I try to go into this there is a dialogue box "Authentication Required" , "You must log in to access guest@hem" with username = my ubuntu login name, Domain = HEM and then it prompts for a password.

My ubuntu login pw (or empty pw) is not correct and I have difficulties to understand why this is so and I haven't a clue how to find out the pw.

My daughters Vista laptop was on the network during the weekend, but then it was only accessing internet and not any drives/PC's on the network.

There are lots of smb commands, but it not obvious how they should be used.

And, I am really stuck without the network disks.

smb.conf submitted. What did/did I not do?

---

### Post by salvor_hardin on 2007-11-26
If this is happens when you try to enter Windows machine, then try adding acount on Windows platform and connect through that account.

---

### Post by dmizer on 2007-11-26
you have to add your ubuntu user id to the samba group with the following commands:

```
sudo smbpasswd -L -a ubuntu_username
sudo smbpasswd -L -e ubuntu_username
```

---

### Post by Anders J on 2007-11-26
Did that, no change. Besides I still don't realise why it has worked perfectly so long. See screen dump.

(salvor_ hardin: No, the problem is I can't access the network from my ubuntu PC, all units on the network are perfectly available through other Windows PC's.

Edit: I realise that the login dialogue prompts me do login to a domain, while this is never what I wanted to do and never did, I just want to connect to my network!

---

### Post by dmizer on 2007-11-26
i understand that it has worked for so long, but something has changed otherwise it would still be working.

have you recently installed firestarter?

---

### Post by Anders J on 2007-11-26
I have made no attempts to install Firestarter, don't know what that is.

I uninstalled (and deleted the config file) samba and started with a new samba out of the box. It works exactly as before, prompts for the same login as before.

I only need LAN access like I used to have.

Each time I read a new howto, there are always a new set of sudo gedit commands, always different depending who wrote them, extremely time-consuming to read then all trying to find out which one to use.

Current file transfer is via a Windows laptop and USB memeory sticks, simply awkward!

Edit: Searched for firestarter and found file /usr/share/app-install/desktop 1.8 KB 2007-05-03

More edit: Hooked up my ubuntu laptop, which hasn't been connected to the local network for a couple of weeks. IT SHOWED EXACTLY THE SAME BEHAVIOUR! Hard to believe but true. Did the Vista PC to anything unrecoverable to the local network?

---

### Post by JKyleOKC on 2007-11-26
Look at line 91 of your smb.conf file; it has the security mode commented out, which forces Samba to use its default mode. You may want to try removing the semicolon at the front of the line, and changing "user" to "share" to avoid the login screen.

Have you possibly run an automatic update recently? I did an update last night and noticed that it included a new version of the Samba programs, which might have caused this change. However my smb.conf file did not change with the update, so this may not be what happened to you...

---

### Post by netztier on 2007-11-26
> **Anders J said:**
> Did the Vista PC to anything unrecoverable to the local network?

I wouldn't think so -  but ithe Vista PC) might have fiddled around with becoming the Master Browser of the Windows network neighborhood - I could'n however pinpoint a reason why this should influence the other PCs in a way you indicated.

The seem to have decided to now ask for a password for an incoming SMB request. Were there any upgrades done to some of the Windows machines ?

I don't exactly know if Ubuntu's SMB client can fall back to using "guest" as user account if authentication with a remote SMB server fails. I know that some versions of Windows's SMB clients used to do that. So as long as the "guest" user account on the SMB server was active, things would work. When it got disabled, some things suddenly stopped working, because users had never cared about keeping usernames/passwords in sync across their set of windows PCs.

The fact that you get prompted for "guest@hem" implies that there's something going on with the guest account.

So you need to check the user account(s) on the Vista machine and see if the one you're trying to use is still active and matches the one you are using on the Ubuntu machine when it prompts you for a username/password for the connection to the SMB server.

My suggestion: disable the guest account everywhere you encounter it, and make sure that you have consistent username/passwords across all PCs involved, then start over.

[COLOR="Silver"]Keeping usernames/passwords in sync is a very tedious task if the number of PCs starts to grow - which is exactly why there is things like "Domains", ActiveDirectory, LDAP or NIS.
[/COLOR]

best regards

Marc

---

### Post by Andra on 2007-11-26
Anders,

it's not clear how did you get to the Windows shares previously? Was there a login box or did you just hit enter on computer icon in network places?
Which domain is the Windows domain - HEM? Is it just w workgroup or do you have some computer as a domain controller?
Some months ago I had a ubuntu server that I was definitely possible to connect to the Windows shares. The smb.conf is quite like yours. But you must make sure that you login a Windows share using user credentials of the particular Windows computer (or domain user, if domain).

And maybe do one more update of the system.

---

### Post by Anders J on 2007-11-26
No there weren't any upgrades to the Windows machines, nor are there any logins whatsoever in the system (except for the ubuntu machines). The Vista PC was only here a few hours, so it is gone. I have read soem samba documentation and it would appear as if I would not need samba at all, only smbfs!

But it seems everything is in a bit of mess presently and I might need to spend another day to sort this out. I hate it.

Edit: Andra. iif I recall things right I did nothing whatsoever, just hooked up and the "open" windows network devices were just present, more or less right out of the box!

More edit: Perhaps better to explain. Little office network, only user myself and close family. Two Win XP machines with no login and shared "shared folder", two network disks, one D-link and one LaCie, both of them with shared file systems without authentication, no server, a couple of Ethernet switches a D-link broadband router to a cable modem. I hav eno interest to access the WinXP machines, but I badly need my network disks. I do not need samba, only smbfs.

All this behaved well only a couple of days ago and I was a happy man. There should be a simple method to com eback to this shouldn't it?

---

### Post by dmizer on 2007-11-26
> **Anders J said:**
> More edit: Hooked up my ubuntu laptop, which hasn't been connected to the local network for a couple of weeks. IT SHOWED EXACTLY THE SAME BEHAVIOUR! Hard to believe but true. Did the Vista PC to anything unrecoverable to the local network?

check to see if your windows computer has a firewall on it.  there were some windows updates released not too long ago, and that can reset firewall settings in your windows.

the problem now appears to be on your windows computer.  may be related to vista, but i don't think so.  check for firewall settings on your windows computer (disable temporarily for testing if  you need to).

---

### Post by Andra on 2007-11-26
try username: guest, domain: whatever domain that is for the Windows computer.
Look at how the Windows share is shared - do it on the Windows computer, click shared folder, right 
mouse, choose Sharing,...
If you previouslu did not do anything to log in, then it seems either the right credentials were provided some time before and afterwards being remembered, or the Windows share was truly open for guests in all the world or the local network.

---

### Post by jonandrews on 2007-11-26
Hi.  I've written a simple step-by-step guide to networking Ubuntu / XP machines aimed at users more used to Windows than Ubuntu. Give it a try..

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by Anders J on 2007-11-26
I am soon starting to feel bad about this, You are all trying to help. I am most grateful.

Dmizer: No, even if I disconnect the Win PC's and am alone on the network with the network disks it works the same way.

Andra: As stated there are no logins for the other computers NOR for the network disks.

Jonandrews: Very nice. but already at section 1, "D/clicking on mshome (in my case "hem") will display all the Windows pc's currently on your network..." it deviates, since this does not happen. I also saw a presentation along the same ideas.

With my PC, after reinstallation of samba through Synaptic, nothing whatsoevere happens after clicking on "Windows network", although on the notebook, I still get this login screen (but with the default MSHOME) with unknown password.

So I am grateful but sad after losing so many hours of work...

Edit: I now again tried the "best samba server howto" and typed my through that very carefully, no error reports or unclarities, but still, clicking "Network"/"Windows Network" produces no result whatsoever. There must b esome way to get this going at least as it did when first installed?

Edit again: Found a 7.04 kubuntu CD and booted from this. Same behaviour as with the laptop and with my desktop previously, requested login to smb://anders@hem and I have no ideas whatsoever how to set login in a peer to peer Windows network, yet finding out the password or from where it came. There is something quite rotten in here. I cannot quite get out of my head that this may have something to do with Vista? The problem must be in Winows somewhere, but connected XP computers work like a charm and ubuntu is completely stuck.

Edit 3rd time: Some signs of life! Did run "smbclient -L EDMINI", entered pw and got a reasonable answer, see screen dump. I can see windows machines in the same way. This actually means that ubuntu is aware of the existance of network devices but it is still a question how to get any reaction when D-clicking "Network"/"Windows Network". Anyway this shows that there are still room for some actions from within ubuntu to getthis going.

---

### Post by dmizer on 2007-11-26
okay ... that's great.  now do this:
```
sudo aptitude install smbfs
```
and do:
```
smbtree
```
with a windows machine turned on.

---

### Post by Anders J on 2007-11-26
Dear Dmizer-san!

I did and the result is posted. Stopped and started samba, but still no response in clicking "Wiindows Network".

But we are getting closer!

JEFF and EVAS-CEL are XP PC's, while DLINK is one of the network drives.

---

### Post by Björn Felten on 2007-11-26
> **jonandrews said:**
> Hi.  I've written a simple step-by-step guide to networking Ubuntu / XP machines aimed at users more used to Windows than Ubuntu. Give it a try..

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

Now **that's** what I call the best guide on the subject I've ever seen!

All this time I have been struggling with all kinds of different tools, and yet it was so easy.

Thanks a million, jonandrews!!!

---

### Post by dmizer on 2007-11-26
Okay ... hopefully we'll get it this time.

edit your nsswitch file as follows:
```
gksudo gedit /etc/nsswitch.conf
```
look through the file (it's short) and find the line that looks like this:
```
hosts:          files dns mdns
```
it may not look exactly like that, but it WILL start with "hosts".

add "wins" to that line (in front of dns) so it looks something like this:
```
hosts:          files [COLOR="Red"]wins [/COLOR]dns mdns
```

now install winbind for windows netbios name resolution:
```
sudo aptitude install winbind
```

restart your network:
```
sudo /etc/init.d/networking restart
```

then try to browse to your shares.

---

### Post by Anders J on 2007-11-27
Björn: Good for You!

Dmizer-san: Thanks. I did exactly that, but no difference.

---

### Post by dmizer on 2007-11-27
okay ... that seems strange.

if your windows computer named "jeff" is turned on, can you ping it by name?

```
ping jeff
```

---

### Post by Anders J on 2007-11-27
Yes!

(added recent config file)

Edit: Inserted the kubuntu CD into Jeff and tried out that. Did not perform any actions whatsoever other than just click on the Samba and ot works just as it should. All units available and browsable, no login prompts, just as it used to be. Someone has an idea on how to come back to what was once working?

---

### Post by Andra on 2007-11-27
okey, a bit more (if you do not mind to put those things publicly)
1) what is written in your /etc/hosts.allow ?
2) what is written in your /etc/resolv.conf ?
3) what is  output of
iptables -n -L

Actually, I myself do not think that it's a good idea to show this to all...sorry.

---

### Post by Anders J on 2007-11-27
Replaced the computer name with computername, but I have submitted so much info here already so it isn't the end of the world anymore!

/etc/hosts: (no file with allow extension)
127.0.0.1 localhost
127.0.1.1 computername.Hem

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

/etc/resolv.conf:
domain HEM
nameserver 192.168.0.1

anders@computername:~$ iptables -n -L
WARNING: Error inserting x_tables (/lib/modules/2.6.20-16-generic/kernel/net/netfilter/x_tables.ko): Operation not permitted
FATAL: Error inserting ip_tables (/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ip_tables.ko): Operation not permitted
iptables v1.3.6: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.

It would appear to me as if there is something wrong with iptables.

Edit: realised that sudo iptables is probably a better command:

sudo iptables -n -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by Andra on 2007-11-27
maybe add the files. Btw, I was quite surprised when in June I installed one server and it appeared that Feisty comes with no those files, and some connection problems arised...
   /etc/hosts.allow
   /etc/hosts.deny

chmod 0644, user: root, group: root:


#
# hosts.allow	This file describes the names of the hosts which are
#		allowed to use the local INET services, as decided
#		by the '/usr/sbin/tcpd' server.
#
ALL: 127.0.0.1
ALL: 192.168.0.



#
# hosts.deny	This file describes the names of the hosts which are
#		*not* allowed to use the local INET services, as decided
#		by the '/usr/sbin/tcpd' server.
#
# The portmap line is redundant, but it is left to remind you that
# the new secure portmap uses hosts.deny and hosts.allow.  In particular
# you should know that NFS uses portmap!

;ALL: ALL
ALL:ALL EXCEPT localhost:DENY

---

### Post by Anders J on 2007-11-27
So where should the chmod line go?

Edit: I did put in the allow file.

No change.

Funny thing now is that the login dialogue as previously requested by my ubuntu laptop is now gone.

In view of the time lost, it would have been much much cheaper to get a new disk and to install ubuntu from scratch, but reinstallation as a way out of funny problems is a bit "windowish", isn't it?

---

### Post by Andra on 2007-11-27
run
/etc/init.d/networking restart
to apply changes.

and chmod goes
chmod 0644 /etc/hosts.allow

do it as root. Or sudo.

---

### Post by Anders J on 2007-11-27
Networking restart produced a lot of of output, ending with:

Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.101 -- renewal in 227157 seconds.

As far as I can judge the operation requested new IP from the DHCP.

smbtree looks the same and there is no change in behaviour.

I can ping and watch all devices with smbclient but I cannot browse them. Seems like everything is as it should, apart from the little annoyance that it doesn't work at all. 

Would it be a good idea to try to to take back smbfs to some kind of out of the box status it obviously had when I first installed ubuntu, since it always worked then?

---

### Post by Andra on 2007-11-27
it somehow seems that something is changed in announcing hosts.

As far as I understand it's ok to connect using explicit command:
smb://computername/sharename

---

### Post by Anders J on 2007-11-27
If You mean that I should run

smb://computername/networkname

it only responds

bash: smb://computername/networkname No such file or directory

All attempts to run smb: as a command produces

bash: smb:: command not found

---

### Post by Björn Felten on 2007-11-27
Anders, I don't think you should do any more changes to your Ubuntu machine, it's fairly obvious that the error is on the Windows side, and -- as you suspect -- most likely it's Vista that messed up your network.

One thing that a Windows network has a habit of doing is changing PDC (Primary Domain Controller) at a whim (or rather election). This often causes mysterious changes in the network.

1) Can you ping all your Windows machines from Ubuntu?

2) Are you using DHCP or fixed IP addresses?

3) Have you tried rebooting your Windows machines? 

4) If you do 'ipconfig -all' on your Windows machines, does the output look OK?

5) If you have browstat.exe on any of your Windows machines, can you check what machine is master and what are backups.

---

### Post by Andra on 2007-11-27
sorry, I do not do these things every day :)
smbclient //computername/sharename
replace computername, sharename with actual values.
But it does not meen much - just to check that it's allright with samba. And that the problems lies in announcing computers in the network.

---

### Post by Anders J on 2007-11-27
Björn:

1. Yes, both by name and IP.

2. DHCP for the computers, fixed for netdisks.

3. Haha, oh yes. Many times.

4. Yes.

5. I haven't. But smbclient shows me this. As long as the network disks are powrered, the D-link one is the master.

I am not sure You are right about Vista, since I can browse all units from my ubuntu laptop and from the kubuntu live-CD machine.

Andra:

smbclient tells me everything looks good. But there is still something wrong here.

---

### Post by Björn Felten on 2007-11-27
Now I'm getting a little confused. :)

Are you saying that your netdisks have their own OS? If so, what OS?

You said earlier that you got exactly the same "error" when you tried to access your netdisks from your laptop, are you saying that this is no longer the case, or do I misunderstand "can browse all units"?

---

### Post by Andra on 2007-11-27
btw, on my ubuntus
/etc/hosts
127.0.0.1       mycomputername   localhost.localdomain   localhost
127.0.1.1       mycomputername

And I agree you should determine Master Browser. With adding Vista to the network it may be changed. I havent gone deep in your description of your network configuration, but it seems there is mixed environment - linuxes, Xp, what else...

---

### Post by Anders J on 2007-11-27
Most of these netdisks are Linux-based internally if I have understood this right.

Yes, this is the case with the ubuntu laptop. When this nightmare started, it did prompt me for login (which was impossible since it did not exist) but now it just works as ubuntu should. I did *nothing* with it.

But I have fiddled so much and lost so much time and money with my desktop that I am actually consdiering ditching it abd start from scratch with a new PC. There is probably a  line somewhere with a mis-placed charactre somewhere.

---

### Post by Björn Felten on 2007-11-27
> **Anders J said:**
> Most of these netdisks are Linux-based internally if I have understood this right.Yes, probably. So, do you have a web interface or is it purely CLI via SSH when you want to administer them? Maybe studying the log files in the netdisks can give you a clue?

But I tend to agree with you, after all the changes you've made, a fresh install is probably simplest. You might try to completely uninstall smdb and nmbd and then install it again, and see if that helps. But then I guess you might have problems reaching the internet so you'd better burn the latest version on CD first...

Edit: If you don't need to share any resources on your Ubuntu machine, you can delete Samba (I think I saw somewhere that you installed it?).

        And if you go for the uninstall suggestion, remember to also delete all config files. You may have to do this manually in Synaptic (if they are not deleted they show up in a special "folder" if you select Status in the left menu).

---

### Post by Anders J on 2007-11-27
I have one Dlink dual RAID disk unit (not recommended, unstable SW) and one LaCie, they both have web interface. After some months of use, the LeCie unit seems to be rock solid, while the Dlink needs firm restarting by power cycling sometimes.

Anyway, I have now uninstalled samba. That does not change anything, I can still examine the network units using smbclient but, as expected, it still doesn't work. If there could only be a way of restoring the settings to the original ubuntu installation defaults it probably would and I would be a happy man again.

It has many times surprised me that connecting a camera, a cellphone or a USB harddisk always work without any tweaking or installation.

---

### Post by Andra on 2007-11-27
ok, one more try: did you reinstall all smb*, samba* packages? From the command line?
Btw, one of my ubuntu servers that was able to access Windows shares when it was connected to the local office network, and it did not share anything itself, has only samba-common and smbclient installed.
sudo apt-get install -reinstall samba-common smbclient

---

### Post by Anders J on 2007-11-27
Yes, uninstalled everything including conf and installed samba-common and sambaclient.

No change. I sometimes get a feeling that the "Windows Network" symbol under "Network" is only text and that nothing whatsoever happens when I click  it.

I am running out of ideas now and moving towards giving up this attempt to set things right. The response below looks reasonable right?:

anders@anders-ubuntu:~$ smbtree
Password: 
HEM
       [INDENT] \\JEFF                          Martin
                [INDENT]\\JEFF\C$               Default share
                \\JEFF\ADMIN$           Remote Admin
                \\JEFF\SharedDocs     
                \\JEFF\IPC$             Remote IPC[/INDENT]
        \\EDMINI                        LaCie Ethernet Disk mini
                [INDENT]\\EDMINI\ADMIN$                 IPC Service (LaCie Ethernet Disk mini)
                \\EDMINI\IPC$                   IPC Service (LaCie Ethernet Disk mini)
                \\EDMINI\anders[/INDENT][/INDENT]

But perhaps someone has an idea what could have happened?

---

### Post by jetsam on 2007-11-27
Hi.  You must be very frustrated by now, and I'm not sure that I can help, but if you're still willing to try something, I'd recommend the following:

I don't think you want winbind installed.  I believe it's for connecting unix and NT domains, while you don't want anything to do with domains at all.  

```
sudo apt-get --purge remove winbind
```

Will uninstall it.  

Then, I'd shut down everything on the network, xp computer, ubuntu computer, and network drives.  I'd restart in the following order:

start network drives
start ubuntu computer

then look to see if the drives are visible on the ubuntu computer. If not, well...  tear hair out.  

If they are, then start the windows computers, and cross your fingers that they don't mess things up.  Netbios is very temperamental, and the order in which things appear on the network can affect it.

---

### Post by Anders J on 2007-11-27
Will do that. I am not in principal against domains, but I think the solution to the problem I see should involve understanding what happened and why!

This is interesting, I am now running on the same computer as usual but from the Gutsy live CD and guess what?

It DOES see my network HEM but it DOES require this weird non-existing authentication!

So this actually means that:
- Computers running XP have no problems to access my network, no logins, no trouble..
- Computers running 7,04 live cd ubuntu also no problem.
- My updated 7,04 refuses to see my network from the desktop, while it is visible although not usable through smbclient.
- My 7.04 laptop worked fine, although it is updated, but at this very moment it does not see any units in the network but it does on th eothre hand not require login.

Can anyone explain what is going on?

With some 4 PC's and 2 other network devices there would be a considerable number of possible combinations. This little test does not show me that ubuntu linux is a very good route forward. I have been extremely happy with ubuntu up to this nonsense.

Please anyone! How would it be possible to find out what is going on?

Edit: Purging winbind made no difference!

---

### Post by Anders J on 2007-11-27
Here's what I did.

Closed down all computers and switches in the network.

Powered up router, switch and LaCie netdisk and then ubuntu desktop.

Network not visible.

smbtree detects disk.

smbclient -L edmini shows:
Password: 
Domain=[EDMINI] OS=[Unix] Server=[Samba 3.0.22]

        Sharename       Type      Comment
        ---------       ----      -------
        anders          Disk      
        IPC$            IPC       IPC Service (LaCie Ethernet Disk mini)
        ADMIN$          IPC       IPC Service (LaCie Ethernet Disk mini)
Domain=[EDMINI] OS=[Unix] Server=[Samba 3.0.22]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        HEM                 EDMINI 
anders@anders-ubuntu:~$ ping edmini
ping: unknown host edmini
anders@anders-ubuntu:~$ ping 192.168.0.33
PING 192.168.0.33 (192.168.0.33) 56(84) bytes of data.
64 bytes from 192.168.0.33: icmp_seq=1 ttl=64 time=6.56 ms
etc

Then started Dlink netdisk

smbtree lists LaCie disk and then only
 \\DLINK-7FA5CA                  DNS-323
cli_start_connection: failed to connect to DLINK-7FA5CA<20> (0.0.0.0)

and then as this is repeated a couple of minutes later only LaCie disk and not Dlink disk at all anymore.

anders@anders-ubuntu:~$ smbclient -L Dlink-7fa5ca
Connection to Dlink-7fa5ca failed

Pinging Dlink disk by IP is OK but not by name (unknown.host link...)

Does this tell us anything?

---

### Post by jetsam on 2007-11-27
It mostly tells me that what I suggested didn't work very well.  

I think the bugs you're experiencing are causing more than a few people grief with Gutsy, but I also think they're very difficult to track down...

Before, I was developing the theory that the Vista computer made some kind of change to the behavior of the SMB network that had perpetrated itself since that time.  It's pretty clear now that isn't the case, and that one of your computers simply isn't browsing the network right in Nautilus.  

The D-link drive might actually be happier with a windows computer on the network.  

I just came across an interesting diagnostic command:

```
gnomevfs-ls network:///
```
and 
```
gmonevfs-ls smb:///
```

These may add another tidbit of information.  Gnome vfs is an abstraction layer over the unix filesystem that Nautilus reads.  gnomevfs-ls is a command line interface to that layer.  Running the above commands a few times did seem to just now refresh my network view in Nautilus, although it may have been coincidental.  Even if they don't work miracles, they may give interesting output.

I share your frustration with how difficult this stuff is to diagnose.

---

### Post by dmizer on 2007-11-27
**here is a detailed explanation for what's causing your problem**:

there was a samba update late last week.  this would have been at about the same time the vista machine was connected to your network.  this samba update appears to have broken you, this is why the live cd works and your install does not (the live cd does not have the most recent version of samba).  i'm sorry that i was not able to provide more information for you yesterday evening as i was extremely busy at work.

**following up on some of the work you did since my last post**:

you need winbind for netbios name resolution.  you need netbios name resolution for nautilus to see the the names of the windows computers on your network.  you need a samba server installed so that your ubuntu machine is listed on the same domain as your windows computers.

you can get name resolution one of three ways:

[INDENT]1) by adding each computers ip and host name to the /etc/hosts files of all computers on your network (must be a static network)
2) using a local dns server (lots of effort)
3) using winbind.[/INDENT]

connecting to your network attached storage devices might cause problems.  however, connecting to an actual windows computer should be seamless, and i'm trying all the tricks in know to get things to work properly.

to address some specifics:
1) the work you did with Andra on page 3 did nothing because /etc/nsswitch.conf has wins listed before dns (in other words dns changes effect nothing regarding your samba network because netbios is resolved before dns).
2) a fresh install will fix nothing because you will just install the samba update and break everything again.  so don't waste your time.

**here's your to do list**:

you'll need to reinstall winbind or get name resolution from a local dns server, or /etc/hosts.  i suggest you reinstall winbind.
```
sudo aptitude install winbind
```

then, disable ipv6.  follow this guide for disabling ipv6 on your ubuntu computer: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?)

restart your computer, try pinging your windows computer by name again:
```
ping jeff
```

i also want to suggest some changes on your windows computer that may help:
i did not have a time to capture a screen shot for you in windows, but on at least ONE windows computer you will need a netbeui protocol installed so it can be your netbios domain host.

on your windows machine, look at the properties of your network adapter and see if there is a listing for netbeui protocol like so:
start > control panel > networking > 
right click on "local area connection" and select properties and see if "netbeui" is listed.

if it is not, try adding it like so:
in "local area connection" properties, click on > "install" > select "protocol" and click on "add" > select "netbeui protocol" and click on "ok".

you may have to reboot after this.  this is not an ideal fix, but if it works, it /should/ fix your network storage devices as well.

after doing this, try to browse to your samba shares.  if this still prompts you for a password, i have more tricks up my sleeve.  bear with me, this is a new problem.

---

### Post by Anders J on 2007-11-28
Dmizer-san, I am so very grateful for all Your efforts. I am extremely busy but will try this out during the afternoon european time.

---

### Post by Anders J on 2007-11-28
I had some time to spare.

Performed all Your suggested actions, although I haven't figured out how to install netbeui yet. 

See uploaded screenshot.

Interesting that jeff and edmini both agree that they are on the HEM network while my ubuntu PC still claims to be on MSHOME.

Currently, after another re-boot, smbtree does not list ubuntu at all, but still MSHOME and HEM.

I am benginning to think that this is tricky and that other people may have similar troubles.

Will be busy again a couple og hours.

---

### Post by dmizer on 2007-11-28
i thought we had that fixed.

let's do that now.
```
sudo aptitude install samba
```

let's make a backup of your current samba configuration so we can revert to it if necessary.
```
sudo /etc/init.d/samba stop
sudo mv /etc/smb.conf /etc/smb.conf-backup
sudo touch /etc/smb.conf
```

now let's make a small samba configuration file tailored to your network.
```
gksudo gedit /etc/smb.conf
```
and paste the following into the file:
```
[global]
    ; General server settings
    netbios name = ANDERS-UBUNTU
    workgroup = HEM
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    name resolve order = hosts wins bcast

    wins support = no
```

save the file, and exit.

restart samba and your network:
```
sudo /etc/init.d/samba start
sudo /etc/init.d/networking restart
```

do your sambatree again, and try pinging jeff.  if you can ping jeff, try connecting to the shares on jeff.

---

### Post by Anders J on 2007-11-28
Right.

But samba was already installed and the samba files are in /etc/samba/, but I am learning and resolved that myself. Reinstalled and made sure the word MSHOME is not in the smb.conf or in JEFF.

Result of smbtree:

anders@anders-ubuntu:~$ smbtree
Password: 
MSHOME
HEM
        \\JEFF                          Martin
                \\JEFF\C$               Default share
                \\JEFF\ADMIN$           Remote Admin
                \\JEFF\Eddie izzard   
                \\JEFF\SharedDocs     
                \\JEFF\IPC$             Remote IPC
        \\EDMINI                        LaCie Ethernet Disk mini
                \\EDMINI\ADMIN$                 IPC Service (LaCie Ethernet Disk mini)
                \\EDMINI\IPC$                   IPC Service (LaCie Ethernet Disk mini)
                \\EDMINI\anders         
        \\ANDERS-UBUNTU                 anders-ubuntu server (Samba, Ubuntu)
                \\ANDERS-UBUNTU\LaserJet-1200   LaserJet-1200
                \\ANDERS-UBUNTU\pdf_printer     pdf_printer
                \\ANDERS-UBUNTU\IPC$            IPC Service (anders-ubuntu server (Samba, Ubuntu))
                \\ANDERS-UBUNTU\print$          Printer Drivers

***
Not very encouraging right? Perhaps better to giv ein and call the network MSHOME?

Anyway, have to leav my computer for a few hours now, thanks again and no change in behaviour yet!

---

### Post by jetsam on 2007-11-28
What you put in your last post looks promising to me, Anders.  The indentation got stripped, but I believe that everything that should be showing up under HEM is showing up under HEM.  The MSHOME workgroup could be just be a "ghost" on the netbios network that may disappear with time.   It won't do any harm.

---

### Post by Anders J on 2007-11-28
I actually gave up, changed the network name to MSHOME on all units, should have done that long ago to minimise typing.

Anyway, all units ping by name and IP, smbtree and smbclient look as they should. Furthermore, my ubuntu machine is visible from the PC's although non-browsable since it prompts for a password (which i didn't set, it is in any case not my ubuntu login).

So despite all work, I haven't moved forward a single millimeter.

There should be more users having the same problems out there if the problem is caused the way dmizer-san says?

---

### Post by jetsam on 2007-11-28
> There should be more users having the same problems out there if the problem is caused the way dmizer-san says?

...I think there probably are, but it's a user here and a user there, not all Ubuntu Samba installs.  There are many variables so it's hard to pinpoint.

---

### Post by dmizer on 2007-11-28
there are loads of people with your problem.  it's been an ongoing issue since dapper.  i solved the problem by bypassing nautilus completely and mounting with /etc/fstab instead.  if you're interested in that solution it will take some more effort, but it WILL fix you.

just found this, and it looks interesting:

post the output of
```
vfs-test smb://jeff
```

also, double check to make sure the windows xp firewall is disabled.

---

### Post by Anders J on 2007-11-29
bash: vfs-test: command not found

---

### Post by jetsam on 2007-11-29
dmizer: I don't have vfs-test either, and I couldn't find it in the repositories.  I think you may have to compile samba to get it?

Anders: I think you should go with dmizer's fstab solution, as it has worked in the past.  

The problem you have is, at least largely, a disconnect between gnome/nautilus and samba.  Samba is working right: smbtree shows this.  Nautilus, however, doesn't agree.  If you mount your shares at start-up, gnome will see them differently.  You may even get a performance improvement when you copy large files over the shares.  It isn't as flexible as network browsing, but it's a very good workaround and should remain stable through the future.

---

### Post by Anders J on 2007-11-29
I agree, fstab, here I come!

But it actually means that a described basic functionality in ubuntu/Nautilus just doesn't exist in a proper way and that's not good.

---

### Post by rdowell2002 on 2007-11-29
> **JKyleOKC said:**
> Look at line 91 of your smb.conf file; it has the security mode commented out, which forces Samba to use its default mode. You may want to try removing the semicolon at the front of the line, and changing "user" to "share" to avoid the login screen.

Have you possibly run an automatic update recently? I did an update last night and noticed that it included a new version of the Samba programs, which might have caused this change. However my smb.conf file did not change with the update, so this may not be what happened to you...

Thanks JKyleOKC,

I had just installed the Samba programs and was having the same problem;  Able to see the Ubuntu shared folders on my Windows network but unable to open them (login dialog box). Your tip on the smb.conf file did the trick for me.

Thanks,
Bob

---

### Post by Anders J on 2007-11-30
Trying then to mount a NAS, looking like::
```
$ smbtree
Password: 
MSHOME
        \\EDMINI                        LaCie Ethernet Disk mini
                \\EDMINI\ADMIN$                 IPC Service (LaCie Ethernet Disk mini)
                \\EDMINI\IPC$                   IPC Service (LaCie Ethernet Disk mini)
                \\EDMINI\anders
```
using cifs should then, with my still primitive knowledge and dmizer's guide, look like:
```
sudo mount -t cifs //MSHOME/anders /EDMINI/anders -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```
This only produces:
mount: mount point /EDMINI/anders does not exist

Yes I know, all information about everything is always available in the manual text, but ut quickly gets so recursive that I get lost. The main reason I dared migrate to ubuntu was the fact that I tried it and it worked like a charm. Maybe I should have realized...

---

### Post by Björn Felten on 2007-11-30
Let me see if I've got this straight? You want to access your netdisks but have no interest in sharing anything on your Ubuntu machine, right?

If so I still think that Samba should not be needed on your Ubuntu machine, but then again I'm no expert... 

One thing struck me though: since it obviously is your netdisk that asks for a log-in, can it be that the netdisk performs automatic updates when new firmware is available? If so maybe it's your netdisk that has installed a new version of Samba that overwrote the old config file?

I'd check out the netdisk config if I were you.

---

### Post by Anders J on 2007-11-30
Correct, samba would not be needed, I would only click "Places/Network/Windows Network "and off I would go to browse connected units.

And that's exactly how ot worked a week ago and that is how it should work. Frustrating, right?

It reminds me what I have heard a few times from Microsoft support, "It shouldn't work like that", or even worse "If what you describe would have been the case, we would have known, so it isn't"!

The netdisks were not upgraded.

---

### Post by Björn Felten on 2007-11-30
So you never had to set up any users or passwords on your netdisk, they worked directly with no real set-up needed, is that correct?

If so, maybe it uses NetBEUI (NetBIOS Extended User Interface). Then, if after the latest upgrade of your Ubuntu machine, Ubuntu suddenly starts using TCP/IP I guess you could expect a result similar to what you've experienced.

Do you know if your Windows machines have NetBEUI enabled? 

Yes I know, this is a really far fetched theory, but we seem to run out of probable theories so I guess it must be allowed...? :)

---

### Post by Anders J on 2007-11-30
Correct.

I never deliberatly installed NetBEUI, so I very much doubt that.

---

### Post by Björn Felten on 2007-11-30
Well, Win2K and earlier installed NetBEUI by default, on XP you have to manually copy Nbf.sys and Netnbf.inf from the CD to get it. So it all boils down to the question: do you have XP? And I seem to recall that you do, so there goes that theory I guess...

---

### Post by Anders J on 2007-11-30
XPH on one and XPP on the pther one, so I guess so.

7 pages and still no progress whatsoever, quite amazing...

---

### Post by Björn Felten on 2007-11-30
There's still the question about what the log files on your netdisk has to say. Because you must admit that it appears to be the linux installation on your netdisk that asks for a log-in, don't you?

Usually on small dedicated systems like a netdisk, router, wlan AP and so on, they have very little memory, so logging usually is disabled. On some of those systems you can instruct them to save the log on a remote disk, maybe that could be an approach for you?

---

### Post by Anders J on 2007-11-30
Noone asks for log-in, that was long ago, when I D/click Windows Network from Nautilus, NOTHING whatsoever happens.

---

### Post by Björn Felten on 2007-11-30
Ehh... Now I'm lost. What do you mean nothing happens? Don't you even get Nautilus up and running? If so you must now have a completely different problem AFAICS.

Reinstall Nautilus perhaps?

On my Swedish install it says 'Platser' between 'Program' and 'System'. Under 'Platser' I have 'Nätverk' down the menu list. When I click on 'Nätverk' I get 'Nätverk - Filbläddrare' showing all the computers in my home network ('FELTEN') -- where does it go wrong when you try the same?

---

### Post by Anders J on 2007-11-30
Exactly the same structure here (although English) and then when I come to the step where I ckick "Windows Network" this is a dead end with no action whatsoever.

Last Friday i then saw my home network as the next step and then when I clicked that the units were there.

But not anymore. You can see I am frustrated?

---

### Post by Björn Felten on 2007-11-30
Hmmm... So, Nautilus doesn't work at all, or only when you try Network? I.e. What happens if you click any of the other choices in that menu such as desktop, home, music, and so on?

If I were you I'd try the following in Synaptic:

1. Reinstall nautilus.

If that doesn't help:

2. Reinstall ubuntu-desktop.

---

### Post by Björn Felten on 2007-11-30
> **Anders J said:**
> 7 pages and still no progress whatsoever, quite amazing...I'd say that we've made a lot of progress!

First you complained about your netdisk asking for log-in. No word about this netdisk actually being a dedicated linux server. Yet we seem to have discovered that it was all a matter of your temporary Vista visit on the network, that trashed the entire network setting -- not entirely unusual when you have to put up with Microsoft's miserable implementation of TCP/IP networks.

Then on about every two pages you encounter a totally different problem. Once we've tried to direct you somewhere to solve this NEW problem, you seem to have solved it, but immediately encounter a NEW problem. Now we're long away from the original problem, right?

---

### Post by Anders J on 2007-11-30
Hunting a moving target eh?

Nautilus works great, but there appears to be a slight problem between Nautilus and samba, dmizer-san decribes that as a common and known problem.

---

### Post by fdreed on 2007-12-01
> **Anders J said:**
> 

Interesting that jeff and edmini both agree that they are on the HEM network while my ubuntu PC still claims to be on MSHOME.



This gives me an idea. I think that all the changes you have made may now have muddied things a bit... may I suggest:

1) Make a live CD of Gutsy (7.10)
2) Boot the computer that used to have good network access with this.
3) Go to menu System-->Administration-->Network, it should come up with "roaming mode" enabled.
4) Click On the General tab.
5) Host name will be "ubuntu"
6) Carefully type in the Domain Name to match (I don't know if you have HEM or MSHOME now) MAKE NO OTHER CHANGES.
7) Choose Close.
8) Go to menu Places-->Network and give it a try.

This has worked for me in a similar situation to yours, returning my access to Windows shares AND network drives, but even if it doesn't work it will give some information.

---

### Post by froy02 on 2007-12-01
In your original smb.conf . you need 2 things in [Global];

security = SHARE
domain master = no

After you changed your smb.conf run 'etc/init.d/samba restart'.  It may take a while to for each computer to see each other. Be patient.

If you want password protection see this thread:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by maybeway36 on 2007-12-01
Have you tries changing the resolve order in smb.conf? I changed it to bcast once and my network browsing started to work.

---

### Post by Anders J on 2007-12-01
fdreed: Been there, done that...

froy02: Did that, restarted networking and samba. Looks good with smbtree and smbclient,  no difference. 

maybeway36: Tried that, restarted samba. Looks good with smbtree and smbclient, no difference.

Feels like this is a dead end and it is time to close the subject. I'd better learn more linux terminal commands so I can figure out how to mount using cifs, have ordered a couple of books on the subject. I had a real nightmare with the graphics/xorg thing when I was in the beginning of the migration process (that should be better now?) and I have to admit the truth in "Linux is not Windows" and that despite enormous efforts the truth is that anyone going for a Windows/(kx)ubuntu migration should be prepared for a rather intense learning period.

---

### Post by vtcat on 2007-12-01
This may be too obvious, and something you've already looked at, but I had the same problem with the recent update to samba.

The fix was that under System>Administration>Network on the General tab, the workgroup name had been deleted.  When I filled in the correct workgroup name I regained access to my network shares.

---

### Post by Anders J on 2007-12-01
It could very well be something little like that that I or no one else relized, but no.

---

### Post by JKyleOKC on 2007-12-01
I just wound up a most frustrating week of network problems. I run a 6-station LAN in my home office with a mix of Xubuntu, Mandrake, Mandriva, and Win98 machines. Last Tuesday two of the machines lost their network connectivity completely. I tried every diagnostic I could think of for two full days, with no solutions at all. Couldn't even pin the problem down between hardware and software; tried three different new NIC adapters in one of the machines with no change. Connected the other machine direct to my DSL modem to see whether my LAN switch (one of only two things common to both failed systems) was the problem, but nothing changed. The next morning I realized that I hadn't changed the network configuration on that machine to go direct to my ISP rather than through my Linux-based router box, so I made the configuration changes. This time the machine worked, pretty well pinning down the LAN switch as the culprit. The fact that it had been running 24/7 for some 9 years added to my conviction, so I went out and bought a new switch to replace it.

However, after moving stuff around to get full access to the sockets on the switch in preparation for the changeover, I decided to try power cycling the switch itself by removing its power, letting it stand for 15 seconds or so, then reconnecting the power cable.

And both machines came back to life immediately. Never did open the box of the new switch.

Apparently something had caused the switch to get into a state in which it no longer performed its function correctly for the two affected ports, and the power-cycle action put it back into normal condition. While it's a far-fetched jump of logic, it's possible that something of this sort is what you have been dealing with -- and it doesn't take much time to give it a try! Most networking components are designed as finite state machines (FSMs) and if an FSM ever does get into an undefined state there's not much way to get it back on the track. However, power cycling it does force it back into the defined start-up state...

---

### Post by jetsam on 2007-12-02
It's a good idea, but...

...yes, he restarted the whole network 3 or 4 pages back.  It's truly been a saga...

I think (read: hope) you're almost there, Anders.  I believe you need to figure out the details of your mount commands, and then modify them so you can put them in your fstab.  

Are you still at this point?

> Trying then to mount a NAS, looking like::
Code:

$ smbtree
Password: 
MSHOME
        \\EDMINI                        LaCie Ethernet Disk mini
                \\EDMINI\ADMIN$                 IPC Service (LaCie Ethernet Disk mini)
                \\EDMINI\IPC$                   IPC Service (LaCie Ethernet Disk mini)
                \\EDMINI\anders

using cifs should then, with my still primitive knowledge and dmizer's guide, look like:
Code:

```
sudo mount -t cifs //MSHOME/anders /EDMINI/anders -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```

This only produces:
mount: mount point /EDMINI/anders does not exist

If you are, you need to first make a directory as a mount point:
```
sudo mkdir /media/edmini
```
/media/ is a good place to put mount points because successfully mounted drives show up on your desktop automatically if you put them there.  

That directory then becomes the second path in your mount command, and I believe in the first path you want to refer to shares by their hostnames and not by workgroups::
```
sudo mount -t cifs //EDMINI/anders /media/edmini -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```

For your kubuntu machine, you might want to try a program called smb4k.  This worked fairly succesfully as a workaround in this thread: [http://ubuntuforums.org/showthread.php?t=622411]("http://ubuntuforums.org/showthread.php?t=622411")  It's not ideal, but it's a simple thing to try.

---

### Post by Anders J on 2007-12-02
Still struggling:
```
mount: wrong fs type, bad option, bad superblock on //EDMINI/anders,
       missing codepage or other error
```
I obviously made a completely different interpretation on how to use the mount command, but it looks like I am in good company here!.

---

### Post by jetsam on 2007-12-02
gah!

Try 
```
sudo mount -t smbfs //EDMINI/anders /media/edmini -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```

I'm thinking your drive doesn't support cifs, but I thnk it should support smbfs.

---

### Post by Anders J on 2007-12-02
Sorry, but "mount: wrong fs type....etc"

Is there no need to use the MSHOME net name somewhere in the command?

---

### Post by jetsam on 2007-12-02
I'm sure your workgroup name isn't needed for the mount command. 

What I'm not sure of is what's wrong...

I just now used an analogous command with the exact same syntax to mount a test windows share from an XP laptop to my Ubuntu desktop.  I don't have name resolution set up, so I'm using ip addresses, but I don't think that's a significant difference.  I'm thinking it's the drive being, typically, recalcitrant.  

Can you try mounting a share from JEFF (right name?), the windows computer?  You can  use cifs with xp.    

You'll want a different mountpoint...  /media/jeff  maybe.

Edit: It may not be the drive.  See the post below.  It could still be easier to start with the windows computer, though, as drives can be problematic.

---

### Post by jetsam on 2007-12-02
Have you installed smbfs?  

```
sudo apt-get install smbfs
```

You need this, and not having it would explain the error message.

---

### Post by Anders J on 2007-12-02
I've followed so many different types of advice from different persons so it is getting hard to do a proper trackback. I was absolutely sure smbfs was already installed.

However, doing this wiith DLINK netdisk and with JEFF ACTUALLY WORKS! This took many, many hours. They just show up under "Places" and when I click them Nautilus opens the file structure.

However, the LaCie netdisk EDMIN still fails.

```
anders@anders-ubuntu:~$ sudo mount -t smbfs //EDMINI/anders /media/edmini -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
11019: tree connect failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
```

This is however a major breakthrough.

Next obvious question is how do I unmount shares, right-clicking and "Unmount" is not allowed and there should be some method. I'd have expected an "unmount" command, like "sudo unmount"? But I suppose they will just evaporate each time I shut down, so it wouldn't be a problem.

---

### Post by jetsam on 2007-12-02
:)Forward progress at least!  

```
sudo umount <mountpoint>
```

Unmounts a share.  So, for example:

```
sudo umount /media/jeff
```
would work if the share was mounted at /media/jeff.  

That's a better looking error message (if that makes any sense) coming from trying to mount the  Edmini drive, but I'm not sure what the exact problem is...

---

### Post by Anders J on 2007-12-02
Thanks!

Perhaps I should try the units with login authentication, it is a rather sensible idea for many reasons anyway. But I'm still a bit puzzled about what has really happened.

---

### Post by jetsam on 2007-12-02
I'm speculating, but many of your problems point back toward the LaCie disk.  Maybe it's giving gnome indigestion after the samba update?

You could try pulling it off the network, waiting a few minutes, and then restarting the Ubuntu computer to see if you get network browsing back.

---

### Post by Anders J on 2007-12-02
Nope.

---

### Post by Anders J on 2007-12-04
I found a box to tick "enable guest" and now I can mount the LaCie disk. At last. I promise to be a better human and arrange password protection. But I never touched that box before and it is still unknown to me why everything worked from Nautilus before.

But now into next question. I used:
```
sudo mount -t smbfs //EDMINI/anders /media/edmini -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```
which does not work out well with national characters in file or folder names. Which character encoding was used in "the old times" (= the week before last) when this data were copied to the netdisks using Nautlus (without the "mount smbfs...")? Whatever character set was used also appears to be identical with what Windows is using.

---

### Post by jetsam on 2007-12-04
Can you change the drive mount back to cifs?  I think it has better unicode support. 

 When you switched to smbfs for the mount command, I was barking up the (probably) wrong tree that your drive didn't support it.  That error actually turned out to really be not having the smbfs package installed, so the drive may support cifs after all.  

Confusing, but cifs support is also in the smbfs package.

sudo mount -t cifs...  etc...

Be sure to umount the old mount first before you try.  

It's great you've solved the access problem.

----

On the larger question, I do think the samba update broke your setup and a handful of other forum poster's.  The open question I think is: what makes your situation different than most?  There's something different and not too common in your network setup or your configuration that made the update so much trouble for you.  Unfortunately, it's a hard question to answer.

---

### Post by Anders J on 2007-12-04
I was actully just going to write another post, since browsing shares with Nautilus made Nautilus freeze and also remove all icons from the desktop.

Mounting with cifs gets rid of this problem and I think I am finally closing in now on a stable solution.

But it is unbelievable how much time this has taken and I also think that I have taken up more than my share of space here.

Thanks all!

---

### Post by zeugma7663 on 2008-01-06
All

I guess I have a similar problem

Easy access to Windows folders (XP & Vista) soon after 7.10 install
Disappeared after one or two updates
After following a few tricks found here, smbtree is OK, but Nautilus gives only "Please select another viewer and try again", or time-out story

Best advice?

Thanks, Michel

---

### Post by mimada on 2008-01-15
Hello,

I was browsing the forums looking for an answer to a similar problem. Have you tried disabling the firewall (iptables)? The easiest way to do this (if you don't like typing) is to install firestarter. Once installed, you can bring it up through System>Administration>Firestarter. Just click on the "Stop Firewall" button then check to see if you can access your shares.

Mike

---

### Post by Anders J on 2008-03-15
Hi again all!

I just hate to bring this thread up again, but something is obviously unstable here and this seems to be a never-ending story..

Tried to mount one of my network drives using the usual

```
sudo mount -t smbfs //EDMINI/anders /media/edmini -o guest,rw,file_mode=0777,dir_mode=0777
```

This produces the "edmini" media  icon on the desktop (and under "Places"), I can browse the unit and read files but it turns out that the owner of the file directory on this unit is root, so have no write permissions in daily use.

Started Nautilus using "gksudo nautilus" and tried to change owner, only to be confronted with "The owner could not be changed".

Also tried

```
sudo chown -R anders:anders /media/edmini
```

which only produced a massive number of lines with 

```
chown: changing ownership of `/media/edmini/directory/filename': Operation not permitted
```

Why is this so? It appears to me that this whole Samba thing is unstable.

---

### Post by Nythain on 2008-03-15
ok, make sure that the network drive is UNMOUNTED before you tried to chown its mountpoint
sudo umount /media/edmini

then
sudo chmod 755 /media/edmini
sudo chown anders:anders /media/edmini

finally remount the network drive
sudo mount /media/edmini

also, im nto sure about with smbfs, but with cifs, adding
noperm
to the list of options helps fix the issue where every time you tried to copy/move somethign to the network drive, it wants to change permissions (wich it cant do)


hopefully at least some of that helped

---

### Post by Anders J on 2008-03-15
Nope.

Did exacty that:
- unmounted
- sudo chmod 755 /media/edmini
- sudo chown anders:anders /media/edmini
- sudo mount /media/edmini

Owner is still root.

Luckily I have installed an extra 500 GB disk in the computer as sdb1 and I am using that to keep a copy of vital data.

I will try to do it all over again and I will try with cifs also. But the attempt to do network disk access under Linux has already taken to much time and too much help so I guess connectig the drives via USB is a better idea in the long run.

---

