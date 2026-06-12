---
title: "Can no longer connect to network server after Hardy upgrade"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by Talegater on 2008-04-26
I upgraded from 7.10 to 8.04 last night (probably my mistake as I've never had luck doing an upgrade instead of a reformat) and I can no longer access my windows server 2k3 protected shares.

When I go to Places -> Connect to Server and type in my windows box I get the following message:

Can't display location "smb://192.168.1.10/"
No application is registered as handling this file

I can successfully get it to mount via terminal but seeing as I'm the only one in the house comfortable enough to do that I need to get this way fixed. 

Any ideas?

---

### Post by andrewbrown22 on 2008-04-26
I am having the same issue, I cannot access any windows shares...

---

### Post by acracker on 2008-04-26
Maybe you could try uninstalling/re-installing samba? Go to System->Synaptic Package Manager and then search for Samba. Un-check samba-common and smbclient and then re-install them after and try again.

---

### Post by jelofson on 2008-04-26
Same issue here. Not sure what the problem is HOWEVER, try going to Places->Network->Windows Network. You should see your shares there. 
Also, you can type smb://server/share in a nautilus window (like Places->home) and it should allow browsing. There is some bug in the "Connect to server" from places.

If I figure anything else out, will let you know

---

### Post by Talegater on 2008-04-27
Tried navigating to it in Nautilus as well as viewing the windows network. Neither worked, doesn't error out but lists 0 files/folders.

---

### Post by Martym on 2008-04-27
I used an IP address instead of DNS name when the shares would not connect.  I will look into it later as I am not concerned about it since the shares will be going away once I move the data to another (much larger) shared drive.

---

### Post by Talegater on 2008-04-27
> **acracker said:**
> Maybe you could try uninstalling/re-installing samba? Go to System->Synaptic Package Manager and then search for Samba. Un-check samba-common and smbclient and then re-install them after and try again.

No success there either. I guess as a temporary fix I'll have to do all my swapping by logging into the server and connecting to my hardy notebook.

---

### Post by jelofson on 2008-04-27
What happens if you type this at the console:

```

smbclient //windowsbox/share

```

---

### Post by Talegater on 2008-04-27
> **jelofson said:**
> What happens if you type this at the console:

```

smbclient //windowsbox/share

```

it just goes to the next line in the console. No message, nothing.

---

### Post by VictorR on 2008-04-27
According to this
[http://ubuntuforums.org/showthread.php?t=762525]("http://ubuntuforums.org/showthread.php?t=762525")
it is just a bug, which should be fixed (hopefully soon).
So far typing in Nautilus the IP address like
```
smb://192.168.0.100/
or
smb://192.168.0.100/sharename

```
seems to be a workaround. (192.168.0.100 - is one of my Windows machines, so you have to put yours here).

---

### Post by Ouchy on 2008-04-28
> **VictorR said:**
> According to this
[http://ubuntuforums.org/showthread.php?t=762525]("http://ubuntuforums.org/showthread.php?t=762525")
it is just a bug, which should be fixed (hopefully soon).
So far typing in Nautilus the IP address like
```
smb://192.168.0.100/
or
smb://192.168.0.100/sharename

```
seems to be a workaround. (192.168.0.100 - is one of my Windows machines, so you have to put yours here).

I'm having the same problem. 0 files and folders are listed. The IP address temporary fix also doesn't work for me. This all worked under Gutsy.

---

### Post by vishnu on 2008-04-28
same problem for me.  i share using the new nautilus-share app and i can't see any of my shares from other computers or even my own!

maybe it's because when i share i can't select SMB?
hope this is fixed soon.

---

### Post by joes_meat on 2008-04-28
Have you tried mounting the smb drive through fstab, or the mount command?

---

### Post by Talegater on 2008-04-28
> **VictorR said:**
> According to this
[http://ubuntuforums.org/showthread.php?t=762525]("http://ubuntuforums.org/showthread.php?t=762525")
it is just a bug, which should be fixed (hopefully soon).
So far typing in Nautilus the IP address like
```
smb://192.168.0.100/
or
smb://192.168.0.100/sharename

```
seems to be a workaround. (192.168.0.100 - is one of my Windows machines, so you have to put yours here).

Thanks VictoR, I tried searching in the forums first to see if anyone else was having problems but I guess they called it something else.

Anyway, typing the smb://xxx.xxx.x.xxx/ doesn't work for me either, it just sits there working for about a two minutes and then shows nothing. Perhaps it's trying to authenticate without me typing in a user and password?

---

### Post by Talegater on 2008-04-28
> **joes_meat said:**
> Have you tried mounting the smb drive through fstab, or the mount command?

I can mount it via terminal and everything looks like it runs successfully, but when I try to access the drive.... nothing.

---

### Post by golojo on 2008-04-28
Hi, didf U try to sniff with Wireshark (do filter **ip.addr==192.168.1.10**  to see the 2k3 server), just to see who is not responding and why?
Did u tried to define the new 8.04 PC on the 2k3 server as a legal user of shared files/dirs?

---

### Post by c0rwyn on 2008-04-28
I have a similar issue.  I can actually get to the samba server directories, but not to the root.  (i.e. smb://server/mydir works, but just smb://server does not).

---

### Post by joes_meat on 2008-04-28
Can you mount an NFS drive, or ssh mount?

---

### Post by Talegater on 2008-04-28
> **golojo said:**
> Hi, didf U try to sniff with Wireshark (do filter **ip.addr==192.168.1.10**  to see the 2k3 server), just to see who is not responding and why?
Did u tried to define the new 8.04 PC on the 2k3 server as a legal user of shared files/dirs?

No, I didn't try to sniff it or anything... since all my other boxes (windows and ubuntu (not hardy though)) could see it just fine I didn't think of it. 

Nope, it doesn't authenticate by machine nor does it tie into Active Directory in any way.... just a simple user/pass combo.

---

### Post by Talegater on 2008-04-28
> **joes_meat said:**
> Can you mount an NFS drive, or ssh mount?

Since I have no NFS or ssh drives I haven't tried. I'll set up an ssh on my box tonight and see if it'll let me.

---

### Post by PokerJoker on 2008-04-29
> **jelofson said:**
> What happens if you type this at the console:

```

smbclient //windowsbox/share

```

only seems to work when using the ip (for both the -L or the no option):

```
hoek@scaleo-gg:~$ smbclient -L ubu
Server's Role (logon server) NOT ADVISED with domain-level security
Connection to ubu failed (Error NT_STATUS_BAD_NETWORK_NAME)

```
```

hoek@scaleo-gg:/home/alex$ smbclient -L 192.168.1.244
Server's Role (logon server) NOT ADVISED with domain-level security
Password: 
Domain=[AAVANDERHOEK] OS=[Unix] Server=[Samba 3.0.26a]

	Sharename       Type      Comment
	---------       ----      -------
	home            Disk      Network Logon Service
	mp3             Disk      Muziek
	pics            Disk      Plaatjes
	backups         Disk      Backup
	IPC$            IPC       IPC Service (ubuntu-srvr server (Samba, Ubuntu))
Domain=[AAVANDERHOEK] OS=[Unix] Server=[Samba 3.0.26a]

	Server               Comment
	---------            -------
	ACER                 Acer Aspire 1406LC
	UBUNTU-SRVR          ubuntu-srvr server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	AAVANDERHOEK         UBUNTU-SRVR
hoek@scaleo-gg:/home/alex$ 

```

Using the ip and share name i was able to connect using Nautilus...

---

### Post by dacool25 on 2008-05-02
The only way I know of fixing this (Temporarily), is by entering the full share.  For example instead of entering just smb://hostname ..Enter smb://hostname/share

Hopefully they get this fixed soon, but that should work as a temporary fix.

---

### Post by makmiler on 2008-05-02
I have the same problem, except I can see all the Windows Computers connected in the Windows Network, but when I enter one of them, there is no directory listing. It's just empty. And yes, after clicking the computer name, I go and make myself a coffee, and when I come back it enters it, although empty. The same is with full share path. 

So, instead of doing smb://comp-name, try entering the name of the folder you are sharing, for example if you have a folder called 'public'. which is shared through a windows pc, then type : 'smb://computer-name/public', and you will get inside with a normal directory list. On my Hardy only the Root Directory doesn't show anything. I had no such problem 2 days ago, when I had 7.10. I ask myself, why the hell did I do an upgrade.
I also lost compiz, because of the new ati drivers. I have ati x700 on the first laptop.

Anyone has an explanation?

---

### Post by dacool25 on 2008-05-02
No there is no explanation yet.  It is probably just a bug.  But as explained by my post or the one above me, you can enter smb://hostname/share as a temporary fix.

---

### Post by bgreenaway on 2008-05-02
This is a real pain in the ****. My SMB connections to shares on my W2K3 server were working fine under 7.10. Now all of them have disappeared under 8.04. I was very careful to keep my original smb.conf when doing the upgrade (it prompted me).

I can get them back by connecting manually (eventually), but it is flaky at best and they all disappear as soon as I log out. Hope there is a fix forthcoming as this is preventing me from going live with 8.04.

---

### Post by wmf on 2008-05-02
I am having a variation of this problem. I can connect to our windows file server with a smb://[IP Address] and can freely browse those shares that have full access to Everyone. However, any share with permissions set fails with a "You don't have permissions necessary to view the contents of *xxx*" In 7.10, the keyring would kick off, I would provide the username/password, tell it to remember it and from then on, it would connect without a hitch. It seems that I cannot find a place to offer my username/password to connect.

---

### Post by Hellaxe on 2008-05-02
Do you wanna see some STUPID issue????
So this is the deal with nautilus:

- I have on my desktop (still using Feisty 7.04) some shares. One of them is a Fat32 partition. I used to enter from the laptop and in Gutsy, to login in that partion, used```
smb://user@server_IP
```
Then i choose the share and the password window was prompt. It was working very well.
Now with Hardy it simply does not mount the share. The password window is showed and i gave it the password but it can't mount the share.
This is stupid........ well........very stupid.
Another thing: if i want to access to my /home/user/share it doesn't show me the user/password window. It shows the directories but in some of them it says that i don't have the permissions. Of course not the password was not asking to me.

Last:
I'm also having problems to connect to printers shared in other machines (windows). I can't browse them. 

I don't know why they made this radical change!!!!!
Samba was working perfectly in Feity, very good in Gutsy and very very badly in Hardy.
By the way the smbclient works perfectly.

---

### Post by ThaDiggler on 2008-05-02
I think the problem with Nautilus you can connect/view shares fine with Konqueror and Dolphin file/web browsers.

---

### Post by andrewbrown22 on 2008-05-02
Any idea when Hardy will get updated to fix this issue?
Surely it isn't that hard to do, it worked fine in Gutsy.  I know the devs have a lot going on, but surely this is an easy fix.

---

### Post by InSearchOf on 2008-05-03
Same problem here... It's most likely related to this official bug: [https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/209520](https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/209520)

In my case though, I am able to browse the shares on 2 of the Windows computers in our home-network, we have about 6. Nautilus is able to access our workgroup and display the list of computers, but when accessing the other Windows computers Nautilus displays "0 items". No error msg. I do have another ubuntubox (8.04) with samba shares, which I can access from all the computers with no problems whatsoever... This was not a problem before the 8.04 upgrade.

Hopefully all this is related to the abovementioned bug, and will be fixed a.s.a.p. 

-isof

---

### Post by JudgeBob on 2008-05-03
I've solved the problem uninstalling SAMBA and replacing my 'smb.conf' with 'maintainer version'.

Of course, later I've had to recreate my shares, but, at least it is working again.

Regards,

---

### Post by Talegater on 2008-05-03
I finally broke down and just mounted all my shares smb://xxx.xxx.x.xxx/share/
It works, it looks horrible now as my desktop is cluttered with numerous shares instead of just one "server" icon.... oh well, guess this will have to do until the bug gets fixed.

---

### Post by keykero on 2008-05-04
Crazy.  Did this get fixed yet?  I'm surprised they rushed the release out with this crucial problem.  I can't even connect to a local BSD FTP server via Nautilus, yet a simple FTP client connects fine.

---

### Post by questant on 2008-05-04
I found this problem after an upgrade as well.  Apparently Hardy reinstalls samba without taking into consideration previous configurations.  I found only smbclient installed.  I also found smb.conf to be generic.  The situation was complicated because there were Master Browser problems in relation to the WXP systems on the network.  I solved the problem and regained a relatively seamless network by doing the following:
1.  I installed the full samba package through Synaptic.
2.  I edited the smb.conf file to reflect the parameters of my network: gksudo gedit /etc/samba/smb.conf
[There's lots of good Samba information out there for that.  You can cut to the chase with google smb.conf +edit > "I'm feeling lucky"
3.  I tested the edited smb.conf with testparm
4.  I restarted samba: sudo /etc/init.d/samba start
5.  I tested to see if I had smb shares:  smbstatus
I was, of course, somewhat disappointed with the paucity (read nonexistence) of results [I think smbclient -L wserver will do the same thing].
5.  I went to the (very few) XP machines to determine if:
     a.  the Computer Browser service was running.
     b.  there was a Master Browser functioning somewhere.
If there is no MB, no shares for the the smb/cifs file system will not be found and the network virtually doesn't exist.
[On some versions of XP this service will be set to run automatically but it will be shut off.  If you have that dll file it needs to be replaced with one which will start and stay running.  M$ has a discussion of this problem and yet the solution cannot be downloaded.  One must call M$ to ask for a patch (that's a requirement apparently to keep "pirates" from getting it).  It can be found at [www.geocities.com/equazcion1/winxpsp2fixcompbrowser.zip]](www.geocities.com/equazcion1/winxpsp2fixcompbrowser.zip])
If your Ubuntu machine had provided the MB function before the upgrade, the smb network would be lost in any event.  Although XP/2Kx should force a negotiation for that function, when the dll isn't running on the windows machines, the Ubuntu machine won't find an MB because no negotiations took place and there is no MB.  One can REQUIRE a Win machine to be an MB by changing its MB status from FALSE to TRUE.  Even without the full samba, that should cause your smbclient to spring to life.  I have not tested that last statement so if users find their experience to be otherwise please forgive that indiscretion.]
6.  I set an XP machine to be the MB:
HKLM\System\CurrentControlSet\Services\Browser\Parameters\IsDomainMaster
By default this is set to false and I actually prefer it that way but in this instance wanted a quick test solution.  Change the value from FALSE to TRUE.  If memory serves me correct there were multiple places for that change (3).  One can find them all by searching for IsDomainMaster.  Usually the registry change with a running ComputerBrowser service will force the negotiation and the MB function will be available.  Having said that, I rebooted anyway.  After all, it's MS.  Sometimes their magic works and sometimes it doesn't.
7.  I retested for the network with smbstatus.  Voila!
8.  I used sudo smbpasswd to set the smb password for the current default user.  If you have to set a user name: sudo smbpasswd -a username and then put in the password as prompted
The user name must exist on all the machines smb is to access for relatively seamless operation.  One will be asked for the user name and password when connecting to an smb share on a Linux box from a Win box.  While Samba correlated to the username/password of a Linux box, it will not, on its own, use the password from the local Linux machine.  You have to put it in Samba as well.
SMB can be used to share Linux with a Windows machine just as it shares win with lin.  smbpasswd MUST be set for access from the win-to-lin direction as well as the reverse if there is a win password in place.
There are lots of samba commands and lots of good places to find them.  Hope this helps.  If there are mistakes here, I humbly apologize.  I pretty much did this from memory because I didn't keep detailed notes as I worked.

Oh, by the way.  The upgrade blew away the cups configuration as well on my system  That's a whole other issue to solve (not to difficult, however).

---

### Post by heatpumpcontrol on 2008-06-06
OK, after much reading and doing and undoing, I still cannot connect to windows (xp) server shares from Hardy _but_, I can from Feisty (laptop). 

I have tried 

1-Add the following line to /etc/samba/smb.conf:

  client lanman auth = yes 

2-installed gnome-vfs package

3- remove and re-install samba and samba-common and smbclient
using --purge

4- installed smbfs

5- uninstalling SAMBA and replacing my 'smb.conf' with 'maintainer version'.

Only way to view the windows server shares:

1-typing in the server/share name in the address bar

2-adding a (symlink?) under Places-> Connect to Server-> Windows Share

Does anyone have an exact solution please. I thought this would have been resolved by now or a solid workaround put in place.

Now there was an update just yesterday 6/5/08 (June 5th) for samba and it asked me if I wanted to keep the old file and I said yes.

helllllllllllp.... as I fall down a cliff clinging to my laptop because it's the only one that work as it should... Hardy? hmmm. not pleased with the result of this issue. :mad:

Miguel

---

### Post by Tills on 2008-07-19
Has anyone heard if this issue has been resolved yet ??

---

### Post by Efros on 2008-07-23
I believe it is something to do with authentication or rather non authentication issues with gvfs which nautilus uses to mount browsed network drives. I have given up on knocking my head against the wall and can access my shares either through fstab or by typing smb://IPADDRESS/SHARENAME in nautilus, pain in the butt, It will have to do until this issue is fixed.

---

### Post by karlos876 on 2008-07-23
I have struggled with this issue for the last couple months. It is the main reason I went back to Gusty.

---

### Post by blmartech on 2009-10-04
over a year later and still not fixed, wow

---

