---
title: "Installing Ubuntu 13.10 client for free public person vpn server (VPN Reactor)"
date: 2014-02-24
forum: Networking &amp; Wireless
---

### Post by Gustav_Toppa on 2014-02-24
[B]EDIT:  [SIZE=4]After reading scores of similar threads (found by googling  "[ubuntu no valid vpn secrets ubuntu]("https://www.google.com/search?client=ubuntu&channel=fs&q=no+valid+secrets+ubuntu&ie=utf-8&oe=utf-8#channel=fs&q=no+valid+vpn+secrets+ubuntu")")  where nobody seems to know what's going  on and everyone appears to be shooting blindly in the dark (like I am), I think what  we really need is a clear definition of what a VPN secret is, and specific steps of how to  diagnose whether or not the vpn secret is valid. </ edit >

[/SIZE][/B][SIZE=4]Do you have experience in debugging personal VPN errors?[/SIZE]

I googled for what most people use and [VPN Reactor came up as a common personal vpn server for Ubuntu]("http://www.vpnreactor.com/linux_openvpn.html").
After a few hours, I'm "close" to getting it working for the first time - but I'm consistently getting an error that I don't know how to debug. 
[ATTACH=CONFIG]250646[/ATTACH]
VPN Connection Failed
The VPN connection "VPN Reactor" failed because of invalid VPN secrets.

Do you have experience in debugging such VPN errors?

---

### Post by Gustav_Toppa on 2014-02-24
To give you an idea of the setup, here's a summary of how I installed the Ubuntu saucy salamander client:

I clicked on the confirmation link sent to my email when I [selected "Basic" at the VPN Reactor]("https://www.vpnreactor.com") web site, and, in about an hour or two, I received the "your account is active" email.

I then set up the Ubuntu client, mostly as per [these instructions]("https://www.vpnreactor.com/linux_openvpn.html"), but, modified for the Ubuntu 13.10 setup:
$ sudo apt-get install network-manager-pptp
$ sudo apt-get install network-manager-openvpn
$ sudo service network-manager restart
$ sudo restart network-manager
$ sudo wget -O /etc/openvpn/ca.vpnreactor.crt [https://www.vpnreactor.com/OpenVPN/ca.vpnreactor.crt](https://www.vpnreactor.com/OpenVPN/ca.vpnreactor.crt)

Network Manager->VPN Connections->Configure VPN
Network Connections->Add
Choose a VPN Connection Type->OpenVPN->Create
VPN->Editing VPN connection->Connection name=VPN Reactor
VPN->Editing VPN connection-> Gateway = vpn.vpnreactor.net
VPN->Editing VPN connection-> Type: select Password
VPN->Editing VPN connection-> User name: (I put in my VPN Reator username)
VPN->Editing VPN connection-> Password: (I put in my VPN Reactor password)
CA Certificate: = /etc/openvpn/ca.vpnreactor.crt
Click Advanced... near the bottom of the window.
General->Use LZO data compression = [x].
OK->Save

I then try to connect to the free personal vpn server:
Network Manager->VPN Connections->VPN Reactor

But, every time I try to connect using this newly set up free personal VPN server, I get the error message above.
**How do I debug vpn failures such as these?**

[ATTACH=CONFIG]250649[/ATTACH]

---

### Post by Gustav_Toppa on 2014-02-25
[According to this article, it's a known unfixed bug in Ubuntu]("http://www.ibvpn.com/billing/knowledgebase/38/Invalid-VPN-secret-error-in-Linux-GUI.html"), but that doesn't help me (or anyone else) use VPN with Ubuntu:
> 
The OpenVPN** plugin** for **Gnome NetworkManager** is somehow **broken**, at least in various Ubuntu releases. 
Even with proper configuration it runs into a **NeedSecrets** error although the same command with the same configuration from shell via sudo works just fine.


The original content of my[ /etc/NetworkManager/system-connections/VPN Reactor]("http://www.ibvpn.com/billing/knowledgebase/38/Invalid-VPN-secret-error-in-Linux-GUI.html") file was:
```

[connection]
id=VPN Reactor
uuid=d3e7e019-fc4b-4c5a-a82f-392933ecd8a9
type=vpn
permissions=user:usr1:;
autoconnect=false

[vpn]
service-type=org.freedesktop.NetworkManager.openvpn
username=vpnreactoruser1
comp-lzo=yes
remote=vpn.vpnreactor.net
connection-type=password
password-flags=1
ca=/etc/openvpn/ca.vpnreactor.crt

[ipv4]
method=auto

```

As per the workaround insructions, I tried [changing the password flag from 1 to 0]("http://www.ubuntugeek.com/ubuntu-tiphow-to-connectdisconnect-vpn-from-the-command-line.html#"), and then adding the following:
```

[vpn-secrets]
 password=MyPassword

```

And then I restarted the network manager (although [some say they had to reboot]("http://ubuntuforums.org/showthread.php?t=1750132&p=11389742#post11389742") to get any fixes to work):
$ sudo service network-manager restart

But, to no avail.

---

### Post by Gustav_Toppa on 2014-02-25
I tried the following [all-users suggestion]("http://ubuntuforums.org/showthread.php?t=1671130&p=10784110#post10784110") to the infamous "[vpn secrets]("http://ubuntuforums.org/showthread.php?t=1750132&p=10772614#post10772614")" bug, also to no avail:
NetworkManager:VPN Connections->Configure VPN->VPN Reactor->Edit->General->[x]All users may connect to this network

Which changed the /etc/NetworkManager/system-connections/VPN Reactor file by removing the "permission" line:
```

$ sudo diff "VPN Reactor" "VPN Reactor saved"
> permissions=user:usr1:;

```

[ATTACH=CONFIG]250657[/ATTACH]

---

### Post by Gustav_Toppa on 2014-02-25
And, I tested the password provided by VPN Reactor by logging into the web site:
[https://secure.vprsecure.com/login](https://secure.vprsecure.com/login)

[ATTACH=CONFIG]250658[/ATTACH]
But, I still get the infamous Ubuntu VPN secrets error when I try to start the VPN connection:
$ nmcli con up id "VPN Reactor"
*The VPN connection "VPN Reactor" failed because of invalid VPN secrets.*

---

### Post by Gustav_Toppa on 2014-02-25
I tried this method of [adding a policy for user="at_console"]("https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/738849") with the same contents as user="root, again, to no avail.
```

$ sudo vi /etc/dbus-1/system.d/nm-openvpn-service.conf 

<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
        <policy user="root">
                <allow own="org.freedesktop.NetworkManager.openvpn"/>
                <allow send_destination="org.freedesktop.NetworkManager.openvpn"/>
        </policy>
        [B]<policy user="at_console">
                <allow own="org.freedesktop.NetworkManager.openvpn"/>
                <allow send_destination="org.freedesktop.NetworkManager.openvpn"/>
        </policy>[/B]
        <policy context="default">
                <deny own="org.freedesktop.NetworkManager.openvpn"/>
                <deny send_destination="org.freedesktop.NetworkManager.openvpn"/>
        </policy>
</busconfig>

```

But, still got the same Ubuntu "invalid secrets" message when I start the vpn connection:
$ nmcli con up id "VPN Reactor"

---

### Post by Gustav_Toppa on 2014-02-25
This method of manually [connecting to the network without network manager]("http://forum.hidemyass.com/index.php/topic/13671-ubuntu-invalid-vpn-secrets-question/") shows promise because it eliminates the problematic gnome network manager (which is the reputed cause of the common issue).
Unfortunately, one needs to know what to enter at the command line interface.
 I wasn't sure what to put for each of the five necessary questions (note that [vpnc is suggested as one possible solution]("http://ubuntuforums.org/showthread.php?t=1750132&p=11389742#post11389742") to the infamous vpn secrets bug):

```

$ sudo vpnc-connect
Enter IPSec gateway address: vpn.vpnreactor.net
Enter IPSec ID for vpn.vpnreactor.net:  **VPN_Reactor <== What does it want here?**
Enter IPSec secret for [EMAIL="vpnreactoruser1@vpn.vpnreactor.net"]VPN_Reactor@vpn.vpnreactor.net[/EMAIL]: **<== What is the "secret" to put here?**
Enter username for vpn.vpnreactor.net: MyUserName
Enter password for MyUserName[EMAIL="nicehomeowner@vpn.vpnreactor.net"]@vpn.vpnreactor.net[/EMAIL]: ThePasswordAssignedToMe
$ vpnc-disconnect
```

[COLOR=#a52a2a]** If someone reading this knows what specific text to enter for the IPSec ID and IPSec Secret, that advice would be invaluable to me, and to all who run into this reputed Gnome network-manager bug.**[/COLOR]

---

### Post by Gustav_Toppa on 2014-02-25
The infamous vpn secrets Ubuntu error has quite a few articles on it, but, this one, [which suggests that the password must not have special characters]("https://www.privateinternetaccess.com/forum/index.php?p=/discussion/1095/invalid-vpn-secrets-error/p1"), didn't do the trick (as my password is all numbers).

---

### Post by Gustav_Toppa on 2014-02-25
This article implies[ there is a related "secrets" problem with Ubuntu regarding the "keyring]("http://ubuntuforums.org/showthread.php?t=991144")", but I'm not sure WHERE that keyring is supposed to reside.
Certainly I don't have anything named "keyring" in my .gnome2 directory:

```

$ ls ~/.gnome2/
=> accels  Vim

```

[COLOR=#a52a2a]**So, if this so-called keyring thing is related to the problem, users need a way to identify and debu their keyring information.**[/COLOR]

---

### Post by Gustav_Toppa on 2014-02-25
This article implies that[ the only real solution]("http://ubuntuforums.org/showthread.php?t=991144&p=7510238#post7510238") to the vpn secrets problem is to get rid of the Gnome Network Manager.
> 
AHHH this is such an annoying error. Unfortunately, none of the info I  could find online really fixes it. You can connect if you do not store  your password in the key ring, but if you get disconnected, you have to  do it all over again every time. 
However, I found a real solution. Uninstall the Gnome Network Manager  applet and install the KDE one instead. The bug in in the Gnome applet.  The KDE applet also works with Gnome, so you don't need to run KDE. If  you need PPTP install Kvpnc as well. I am successfully running both with  Gnome, configured them to use PPTP and it worked on the first try, no  more errors. It uses the KDE keyring and remembers your password as  well. 
This is a serious bug that needs to be fixed, fortunately KDE can save you here.

I'm not sure how to install "just" the KDE network manager though ...

[COLOR=#a52a2a]**So, if someone has instructions for replacing the problematic Gnome network manager with the more stable KDE network manager on an otherwise stock saucy salamander system, that would help many users!**[/COLOR]

---

### Post by Gustav_Toppa on 2014-02-25
After having read [scores of "no valid vpn secrets" threads]("http://ubuntuforums.org/showthread.php?t=2207653&p=12940562#post12940562"), the amazing thing is that nobody, least of all me, knows what they're doing.
The poor users just shoot in the dark, trying different things (all of which I've tried, as shown above), only about 1/3 of which seem to result in a solution (none of which worked, yet, for me - but some are still pending for lack of knowledge).

But that's no way to solve a Linux problem.

What we need to do is to UNDERSTAND what the problem is caused by, which, even after reading the threads, I don't even KNOW what a vpn secret is!

Googing for "what is a vpn secret", [I find only a single reference]("https://help.riseup.net/en/vpn-secret") which claims to define what a VPN secret is.
> 
**What is a VPN Secret?[¶]("https://help.riseup.net/en/vpn-secret#what-is-a-vpn-secret")**

 A **VPN Secret** is a special password that can be used in place of your regular riseup.net password to access the RiseupVPN.
 Using a VPN Secret is often better than using your regular password because many VPN clients do not store the password securely.
 **What happens if an attacker learns my VPN Secret?[¶]("https://help.riseup.net/en/vpn-secret#what-happens-if-an-attacker-learns-my-vpn-secret")**

 *If you are using PPTP*, then your VPN Secret is sensitive information. It can be used to decrypt your traffic. You should generate a new VPN Secret immediate. Also, if an attacker recorded a history of your prior traffic, they might be able to decrypt it. (update: PPTP has been [shown to be insecure]("http://news.cnet.com/8301-1009_3-57481855-83/tools-boast-easy-cracking-of-microsoft-crypto-for-businesses") and is disabled.)
 *If you are using OpenVPN*, then the VPN Secret is not so important. If an attacker learns your VPN Secret, the worse they can do is use the RiseupVPN using your account. It is still a good idea to generate a new VPN Secret when you can, but you don&#8217;t need to worry about your data being compromised.
 **How do I generate a VPN Secret?[¶]("https://help.riseup.net/en/vpn-secret#how-do-i-generate-a-vpn-secret")**

 
[LIST=1]
[*]Login to [user.riseup.net]("https://user.riseup.net") 
[*]Click **VPN** on the left sidebar 
[*]Click **New VPN Secret** 
[/LIST]



It seems what we ALL need is a DIAGNOSTIC approach to working around the extremely common "invalid VPN secrets" [Gnome bug]("http://ubuntuforums.org/showthread.php?t=991144&p=7510238#post7510238").
[ATTACH=CONFIG]250669[/ATTACH]

EDIT: I'm not the first person to ask [the question of what is a VPN secret]("http://crypto.stackexchange.com/questions/9926/what-is-the-shared-secret-used-for-in-ipsec-vpn"), but nobody really seems to know the answer.

---

### Post by Gustav_Toppa on 2014-02-26
Here are 25 very similar Ubuntu threads (most either wholly unanswered or filled with mostly undirected shots-in-the-dark):[URL="http://ubuntuforums.org/showthread.php?t=2193559"]
[/URL]   
[LIST=1]
[*]**[Installing Ubuntu 13.10 client for free public person vpn server (VPN Reactor)]("http://ubuntuforums.org/showthread.php?t=2207653&highlight=vpn+secrets"), by [[B][COLOR=#000000]Gustav_Toppa[/COLOR]**]("http://ubuntuforums.org/member.php?u=1901347")[/B] 
[*][VPN connection fails on 13.10 with "invalid VPN secrets" error]("http://ubuntuforums.org/showthread.php?t=2193559"), by [**[COLOR=#000000]pvictory5[/COLOR]**]("http://ubuntuforums.org/member.php?u=1889945")[URL="http://ubuntuforums.org/showthread.php?t=2178660"]
[/URL] 
[*][ hma open vpn - invalid vpn secret]("http://ubuntuforums.org/showthread.php?t=2178660"), by [**[COLOR=#000000]jgw[/COLOR]**]("http://ubuntuforums.org/member.php?u=382468")[URL="http://ubuntuforums.org/showthread.php?t=1933442"]
[/URL] 
[*][ OpenVPN]("http://ubuntuforums.org/showthread.php?t=1933442"), by [**[COLOR=#000000]carranty[/COLOR]**]("http://ubuntuforums.org/member.php?u=1070930") 
[*][openvpn - invalid secrets error]("http://ubuntuforums.org/showthread.php?t=2042922"), by [**[COLOR=#000000]qwertyjjj[/COLOR]**]("http://ubuntuforums.org/member.php?u=595620")[URL="http://ubuntuforums.org/showthread.php?t=1193786&highlight=vpn+secrets"]
[/URL] 
[*][ Invalid VPN Secrets driving me mad!]("http://ubuntuforums.org/showthread.php?t=1193786&highlight=vpn+secrets"), by [**[COLOR=#000000]jegan21[/COLOR]**]("http://ubuntuforums.org/member.php?u=844963")[URL="http://ubuntuforums.org/showthread.php?t=1894345&highlight=vpn+secrets"]
[/URL] 
[*][ Tried everything and still "No VPN secrets found!"\.]("http://ubuntuforums.org/showthread.php?t=1894345&highlight=vpn+secrets"), by [**[COLOR=#000000]koohyar[/COLOR]**]("http://ubuntuforums.org/member.php?u=1480348")[URL="http://ubuntuforums.org/showthread.php?t=991144"]
[/URL] 
[*][ The VPN connection 'xxxxx' failed because there were no valid VPN secrets.]("http://ubuntuforums.org/showthread.php?t=991144"), & [The VPN connection 'xxxxx' failed because there were no valid VPN secrets.]("http://ubuntuforums.org/showthread.php?t=991144") by [**[COLOR=#000000]giesen2[/COLOR]**]("http://ubuntuforums.org/member.php?u=515664") [URL="http://ubuntuforums.org/showthread.php?t=1841925&highlight=vpn+secrets"]
[/URL] 
[*][ "No VPN Secrets" + Not storing password]("http://ubuntuforums.org/showthread.php?t=1841925&highlight=vpn+secrets"), by                                                                                      [**[COLOR=#000000]HangukMiguk[/COLOR]**]("http://ubuntuforums.org/member.php?u=90235") 
[*][OpenVPN fails with no valid secrets]("http://ubuntuforums.org/showthread.php?t=2097223"), by [**[COLOR=#000000]yedd[/COLOR]**]("http://ubuntuforums.org/member.php?u=1768570") 
[*][Re: PPTP VPN connection is failed after awhile]("http://ubuntuforums.org/showthread.php?t=1428224&p=9189779#post9189779"), by [**[COLOR=#000000]demuxer[/COLOR]**]("http://ubuntuforums.org/member.php?u=926857")[URL="http://ubuntuforums.org/showthread.php?t=1881124&p=12599384#post12599384"]
[/URL] 
[*][ Re: How to Connect to PrivateTunnel.com Service Under Ubuntu 11.10]("http://ubuntuforums.org/showthread.php?t=1881124&p=12599384#post12599384"), by [**[COLOR=#000000]xylo04[/COLOR]**]("http://ubuntuforums.org/member.php?u=453042")[URL="http://ubuntuforums.org/showthread.php?t=1815802&highlight=vpn+secrets"]
[/URL] 
[*][ Invalid VPN secrets]("http://ubuntuforums.org/showthread.php?t=1815802&highlight=vpn+secrets"), by [**[COLOR=#000000]Deathmoon[/COLOR]**]("http://ubuntuforums.org/member.php?u=179443")[URL="http://ubuntuforums.org/showthread.php?t=1528840&highlight=vpn+secrets"]
[/URL] 
[*][ VPN PPTP 'No VPN secrets!']("http://ubuntuforums.org/showthread.php?t=1528840&highlight=vpn+secrets"), by [**[COLOR=#000000]newbiefly[/COLOR]**]("http://ubuntuforums.org/member.php?u=702573")[URL="http://ubuntuforums.org/showthread.php?t=1671130"]
[/URL] 
[*][ invalid VPN secrets]("http://ubuntuforums.org/showthread.php?t=1671130"), by [**[COLOR=#000000]haloflightleader[/COLOR]**]("http://ubuntuforums.org/member.php?u=544906")[URL="http://ubuntuforums.org/showthread.php?t=1655562"]
[/URL] 
[*][ VPN - failed because of invalid VPN secrets]("http://ubuntuforums.org/showthread.php?t=1655562"), by [**[COLOR=#000000]chuckNbanna[/COLOR]**]("http://ubuntuforums.org/member.php?u=458230")[URL="http://ubuntuforums.org/showthread.php?t=1530144"]
[/URL] 
[*][ Getting "No valid secrets" when trying to connect]("http://ubuntuforums.org/showthread.php?t=1530144"), by [**[COLOR=#000000]jancogo[/COLOR]**]("http://ubuntuforums.org/member.php?u=484700")[URL="http://ubuntuforums.org/showthread.php?t=1595209"]
[/URL] 
[*][ "No valid VPN Secrets"]("http://ubuntuforums.org/showthread.php?t=1595209"), by [**[COLOR=#000000]altjx[/COLOR]**]("http://ubuntuforums.org/member.php?u=1005100")[URL="http://ubuntuforums.org/showthread.php?t=1600971"]
[/URL] 
[*][ invalid VPN secrets]("http://ubuntuforums.org/showthread.php?t=1600971"), by [**[COLOR=#000000]mogambo[/COLOR]**]("http://ubuntuforums.org/member.php?u=1168650")[URL="http://ubuntuforums.org/showthread.php?t=1532655"]
[/URL] 
[*][ VPN Connection Error "no valid VPN secrets."]("http://ubuntuforums.org/showthread.php?t=1532655"), by [**[COLOR=#000000]Mega_Fauna[/COLOR]**]("http://ubuntuforums.org/member.php?u=232419")[URL="http://ubuntuforums.org/showthread.php?t=1307345"]
[/URL] 
[*][ Ubuntu 9.10 - the vpn connection 'xxx' failed because there were no valid vpn secrets]("http://ubuntuforums.org/showthread.php?t=1307345"), by [**[COLOR=#000000]sweisler[/COLOR]**]("http://ubuntuforums.org/member.php?u=435730")[URL="http://ubuntuforums.org/showthread.php?t=1569357"]
[/URL] 
[*][ There were no valid vpn secrets error from NetworkManger]("http://ubuntuforums.org/showthread.php?t=1569357"), by [**[COLOR=#000000]hq4ever[/COLOR]**]("http://ubuntuforums.org/member.php?u=26304")[URL="http://ubuntuforums.org/showthread.php?t=1179848"]
[/URL] 
[*][ no valid VPN secrets]("http://ubuntuforums.org/showthread.php?t=1179848"), by [**[COLOR=#000000]DeViLDuD3[/COLOR]**]("http://ubuntuforums.org/member.php?u=832863")[URL="http://ubuntuforums.org/showthread.php?t=1215168"]
[/URL] 
[*][ How I fixed my "invalid VPN secrets" problem]("http://ubuntuforums.org/showthread.php?t=1215168"), by [**[COLOR=#000000]Roadcrew[/COLOR]**]("http://ubuntuforums.org/member.php?u=574005")[URL="http://ubuntuforums.org/showthread.php?t=1316052"]
[/URL] 
[*][ OpenVPN No Secrets error when connecting.]("http://ubuntuforums.org/showthread.php?t=1316052") by [**[COLOR=#000000]T3kG33k[/COLOR]**]("http://ubuntuforums.org/member.php?u=758662") 
[/LIST]
 etc.

One by one, I'm trying the suggested solutions, but, all seem to be the type that auto mechanics call "throwing parts at the problem". 
None seem to be intelligent diagnostic sequences.

---

### Post by Gustav_Toppa on 2014-02-27
[B]What we need is a decent vpn secrets debugging sequence!
[/B]
At the moment, here are the unanswered questions, which, when answered, will help everyone:

[LIST]
[*]What is a VPN secret (and how do we validate it outside of the problematic Gnome network manager)? 
[*]How can we replace the problematic Gnome network manager with the more stable KDE network manager? 
[*]How can we find and validate the users Gnome keyring (especially when there is no keyring file in ~/.gnome2)? 
[*]What should we enter for the following vpnc-connect command-line questions?
[LIST]
[*]a. Enter IPSec gateway address <== provided by the VPN service 
[*]b. Enter IPSec ID for that gateway address 
[*]c.** Enter IPSec secret for that IPSec ID **[COLOR=#b22222]**[B]<**== this is the big kahuna ... how do we obtain & validate this outside of Gnome network manager![/B][/COLOR] 
[*]d. Enter username for that gateway address 
[*]e. Enter password for that username at that gateway address 
[/LIST]
   
[/LIST]

---

### Post by Gustav_Toppa on 2014-03-01
> **Gustav_Toppa said:**
> 
[LIST]
[*]How can we replace the problematic Gnome network manager with the more stable KDE network manager?
[/LIST]


Do you think this will screw up the OS?

$ sudo apt-get purge network-manager-gnome
$ sudo apt-get install network-manager-kde

---

### Post by sudodus on 2014-03-02
It will bring av lot of KDE packages (unless you have them anyway). I think you can live with that, but if you have a spare HDD or pendrive (at least 8 GB), you can make a test system without tampering with you main operating system. Or you can do it in a separate partition of your [only] hard disk drive.

---

### Post by Gustav_Toppa on 2014-03-02
> **sudodus said:**
> It will bring av lot of KDE packages (unless you have them anyway).

I was afraid of that but thank you very much for the help because I feel so alone, neglected, and lost without any help from anyone.

To answer your concern about KDE, I have a stock Ubuntu 13.10, so, I would guess that means I don't have a single KDE package installed.

What's dismaying about this problem is that it's extremely common (google and you'll see hundreds of people with the problem), but there is not a single debugging sequence whatsoever.
Everyone is just 'throwing parts' at the problem.

In fact, there's only one definition of what a 'vpn secret' is on the whole net, and who knows if that one definition is correct.
Worse yet, there is no mention of a VPN secret on the entire VPN Reactor web site!

But, I'd really like to try out a free vpn service (any free vpn service), if for no other reason than to know whether it will work in Ubuntu before I plunk down my hard-earned money!

Trying to be diagnostic, I'm still trying to figure out why the VPN Reactor instructions for installation don't make any mention of a VPN secret.
Unfortunately, VPN Reactor doesn't have instructions for setting up the freeware; they only show how to set up the payware.
But, they do have [a freeware FAQ]("https://www.vpnreactor.com/freeaccounts.aspx") which says the only server we can use is vpn.vpnreactor.net, which only supports PPTP security (**but you have to  figure out on your own how to change the instructions below to PPTP**).

[Here are the Ubuntu installation instructions]("http://www.vpnreactor.com/linux_openvpn.html") that I had followed:
> 
                   
[LIST]
[*]Open Terminal. 
[*]Install **network-manager-openvpn** by typing:
[LIST]
[*][COLOR=red]sudo apt-get install network-manager-openvpn[/COLOR]
[LIST]
[*]Press Enter 
[/LIST]
                                     
[/LIST]
  
[*]You will be prompted: "Do you want to continue? Y/n" Type Y and hit Enter. 
[*]Once installation is complete, restart Network Manager by typing:
[LIST]
[*][COLOR=red]sudo restart network-manager[/COLOR]
[LIST]
[*]Press Enter 
[/LIST]
                                     
[/LIST]
  
[*]To download the VPNReactor Certificate Authority (CA) certificate, type (all one command, ignore line breaks):
[LIST]
[*][COLOR=red]sudo wget -O /etc/openvpn/ca.vpnreactor.crt [https://www.vpnreactor.com/OpenVPN/ca.vpnreactor.crt](https://www.vpnreactor.com/OpenVPN/ca.vpnreactor.crt)[/COLOR]
[LIST]
[*]Press Enter 
[/LIST]
                                     
[/LIST]
  
[*]Click on the Network Manager icon (top right menue bar), expand VPN Connections, and choose Configure VPN... 
[*]A Network Connections window will appear with the VPN tab open. Click Add. 
[*]A Choose a VPN Connection Type window will open. Select OpenVPN in the drop-down menu and click Create... 
[*]In the Editing VPN connection window, enter the following:
[LIST]
[*]Connection name: VPNReactor OpenVPN 
[*]Gateway: one of
[LIST]
[*]chicago.vpnreactor.net - Middle U.S. 
[*]denver.vpnreactor.net - Middle U.S. 
[*]denver2.vpnreactor.net - Middle U.S. 
[*]denver3.vpnreactor.net - Middle U.S. 
[*]fremont.vpnreactor.net - Southern California 
[*]houston.vpnreactor.net - Middle U.S. 
[*]la.vpnreactor.net - Southern California 
[*]ny.vpnreactor.net - East Coast U.S. 
[*]nl.vpnreactor.net - Europe 
[*]uk.vpnreactor.net - Europe 
[/LIST]
  
[*]Type: select Password 
[*]User name: Your VPNReactor username 
[*]Password: your VPNReactor password 
[*]CA Certificate: browse and select /etc/openvpn/ca.vpnreactor.crt 
[/LIST]
  
[*]Click Advanced... near the bottom of the window. 
[*]Under the General tab, check the box next to Use LZO data compression. 
[*]Click OK, then click Apply. 
[/LIST]
                             
                                **How to Connect**

               
                                
[LIST]
[*]Click on the Network Manager icon in the panel bar. 
[*]Click on VPN Connections 
[*]Select VPNReactor OpenVPN. 
[*]The Network Manager icon will begin spinning. You may be  prompted to enter a password. If so, this is your system account  keychain password, not your VPNReactor password. 
[*]The Network Manager icon will begin spinning. You may be  prompted to enter a password. If so, this is your system account  keychain password, not your VPNReactor password. 
[/LIST]
               
                                **How to Connect**

               
                                
[LIST]
[*]Click on the Network Manager icon in the panel bar. 
[*]Click on VPN Connections. 
[*]Select Disconnect VPN.. 
[*]Once disconnected, the lock will disappear from next to the Network Manager icon. 
[/LIST]
               



Given those instructions and the freeware FAQ, I guessed at the freeware setup being the following (***but notice there is no place to put in PPTP as a setting***):

[LIST]
[*]Connection name: **VPN_Reactor_OpenVPN** <== I originally had spaces in the name, but, during CLI debugging, spaces drove me crazy. 
[*]Gateway: **vpn.vpnreactor.net** <== I think [this is the *only* web site]("https://www.vpnreactor.com/freeaccounts.aspx") you can use for the freeware? 
[*]Type: **Password **<== there is no option to put PPTP here? 
[*]User name: (my VPNReator username, let's call it **gustav**) 
[*]Password: (my VPNReactor password, let's call it **toppa**) 
[*]CA Certificate: **/etc/openvpn/ca.vpnreactor.crt** <== I previously downloaded this as described in the instructions above 
[*]Use LZO data compression: **yes** 
[/LIST]

To debug on the CLI, what would I put for the following questions to set it up for PPTP?

[LIST=1]
[*]$ sudo vpnc-connect 
[*]Enter IPSec gateway address: **vpn.vpnreactor.net** 
[*]Enter IPSec ID for vpn.vpnreactor.net: **VPN_Reactor_OpenVPN <== **I doubt this matters, right? 
[*]Enter IPSec secret for [EMAIL="VPN_Reactor_OpenVPN@vpn.vpnreactor.net"]VPN_Reactor_OpenVPN@vpn.vpnreactor.net[/EMAIL]: **<== what do we put here for the VPN secret?** 
[*]Enter username for vpn.vpnreactor.net: **gustav** 
[*]Enter password for [EMAIL="MyUserName@vpn.vpnreactor.net"]MyUserName@vpn.vpnreactor.net[/EMAIL]: **toppa** 
[*]$ vpnc-disconnect 
[/LIST]

---

### Post by Gustav_Toppa on 2014-03-11
Just for the record, I guess we can mark this solved because I simply gave up.
I just don't have the knowledge, or energy, or is there enough assistance to get a VPN service set up on Ubuntu 13.10.

---

