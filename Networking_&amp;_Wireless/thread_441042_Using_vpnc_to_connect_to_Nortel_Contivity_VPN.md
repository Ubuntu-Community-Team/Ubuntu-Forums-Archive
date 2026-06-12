---
title: "Using vpnc to connect to Nortel Contivity VPN"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by haxor999 on 2007-05-12
Hi,

after successfully using the proprietary Apani VPN client to connect to my Nortel Contivity VPN at work from Feisty, I set out to find an open-source alternative. I found out that while none of the many VPN solutions support Nortel, this support is currently in an experimental stage in the **vpnc** client.

Currently, this support has been added to an older version of vpnc that you need to download from the subversion repository yourself, and compile yourself. According to the mailing list, the vpnc developers are working to merge the functionality into the latest version. For more background information on this, read their mailing list (particularly the [may '07 archives]("http://lists.unix-ag.uni-kl.de/pipermail/vpnc-devel/2007-May/thread.html")).

*Note: this version of vpnc has not actually worked for me so far, however there are reports that it is working for others. Your mileage may vary :) *

Here's how to download and build the client:
1. You will need at least the **build-essential** and **subversion** packages. I'm not sure what else since I already had a lot of developer packages installed.

2. Open a terminal, navigate to the place where you'd like to download the sources to (a new subdirectory named *vpnc-nortel* will be created in the one you are currently in). Then run:

[FONT="Courier New"]svn co [http://svn.unix-ag.uni-kl.de/vpnc/branches/vpnc-nortel/](http://svn.unix-ag.uni-kl.de/vpnc/branches/vpnc-nortel/)[/FONT]

3. [FONT="Courier New"]cd vpnc-nortel[/FONT]
4. [FONT="Courier New"]make[/FONT]

5. At this point you can execute the *vpnc-connect* script, but you must do so as root since it needs to change your networking setup for the VPN.

[FONT="Courier New"]sudo ./vpnc-connect[/FONT]

You will now be asked first for your Ubuntu password, and then the following VPN info: the IPSec gateway address (the hostname of the VPN router you want to connect to), the IPSec ID (aka group ID), IPSec secret (aka group password), username (your VPN username), and password (your password or the value of your SecurID or other token if you have one).

In order to disconnect, open another terminal, navigate to the same directory as above and run the disconnect script as follows:

[FONT="Courier New"]sudo ./vpnc-disconnect[/FONT]

There are also many options for the vpnc-connect script (use the parameter [FONT="Courier New"]--long-help[/FONT] when calling it to see descriptions of these) to tune the connection and these may be needed for your particular server. Unfortunately, my knowledge of VPNs and the vpnc client ends here (and as I mentioned earlier, it hasn't worked for my VPN yet). The more people that test this and report back (also on the vnpc-devel mailing list, would be good to push for further development of this there) the more likely we will be to get this working!!

---

### Post by NobodySpecial on 2007-05-12
GREAT post.  Thanks for taking the time.

There is one more dependency needed from a fresh install:
```
sudo apt-get install libgcrypt-dev
```

I find myself in the same situation as everybody else, with an "INVALID_EXCHANGE_TYPE" error.  I played around with the settings, but couldn't get it to work.  Hopefully one of the developers will work out the bugs.

---

### Post by click on 2007-05-16
Thanks for this post it is really understandable and easy to apply but I have a problem that I want to ask. 
If I download VPNC from apt-get, it gives "INVALID_EXCHANGE_TYPE" error and when I remove it and install from the given link, at the end of entering my password, it gives "authentication failed" message. All the information that I enter is correct and contivity works in Windows. Can anybody give me some idea about what I should do?

---

### Post by haxor999 on 2007-05-18
well you seem to have gotten further than any of us :)

the reason is that the vpnc you are installing with apt-get is the stable version that does not include nortel contivity support. the one you are downloading is the development version that does (claim to) support nortel.

the people who can help you out further are the developers on the vpnc-devel mailing list (see above for link). best thing to do would be to email to the list and post debug logs from the connection.

---

### Post by Lumar on 2007-06-02
Haxor999, Are you getting the authentication error as well?

---

### Post by mflint on 2007-07-02
Same here - kinda!

The first time I tried it, I got a successful connection. (subversion revision 179)

Then I disconnected and tried to reconnect - and now I only get INVALID_EXCHANGE_TYPE. I restarted networking. I even rebooted the whole machine. But it still fails. :-(

Matthew

---

### Post by pwbrawner on 2007-07-05
I was able to get past that error by entering the group ID for my connection by using a Windows machine with the Contivity client on it and checking the Group ID setting in that. Now if I can get the group password I have a feeling it will work. I will post back when I know more.

---

### Post by NobodySpecial on 2007-07-05
My company uses only username & password authentication, not group security authentication.  But the vpnc client seems to require the IPSEC ID & secret code.

Does anybody else notice this / have this problem??

---

### Post by bpedman on 2007-07-07
Man, I was so close. I work at novell and I can only find instructions for suse distros on how to connect but tried this and I got this error:

/usr/sbin/vpnc: binding to port 500: Address already in use
/usr/sbin/vpnc: response was invalid [1]: ISAKMP_N_INVALID_EXCHANGE_TYPE(7)

I don't know if you guys got the port address already in use error as well as the invalid exchange type?

---

### Post by mhall119 on 2007-07-12
For those of you who downloaded vpnc-nortel from their subversion repo, be aware that the vpnc-connect script doesn't automatically use the local vpnc that you just built, it first tries to find an installed version.  I changed my script to look like this:

       [B] if   [ -x $(dirname $0)/vpnc ]; then
		VPNC=$(dirname $0)/vpnc
	el[/B]if [ -x "`which vpnc`" ]; then
		VPNC="`which vpnc`"
	elif [ -x /usr/local/sbin/vpnc ]; then
		VPNC=/usr/sbin/vpnc
	elif [ -x /usr/sbin/vpnc ]; then
		VPNC=/usr/sbin/vpnc
	else
		echo No vpnc daemon found, aborting...
		exit 1
	fi

So that it will use the vpnc executable in the current directory if one exists, then I was able to connect successfully, though now I'm having routing problems.  Good luck, and let me know if this helps anyone.

---

### Post by Lumar on 2007-07-17
> **mhall119 said:**
> For those of you who downloaded vpnc-nortel from their subversion repo, be aware that the vpnc-connect script doesn't automatically use the local vpnc that you just built, it first tries to find an installed version.  I changed my script to look like this:

       [B] if   [ -x $(dirname $0)/vpnc ]; then
		VPNC=$(dirname $0)/vpnc
	el[/B]if [ -x "`which vpnc`" ]; then
		VPNC="`which vpnc`"
	elif [ -x /usr/local/sbin/vpnc ]; then
		VPNC=/usr/sbin/vpnc
	elif [ -x /usr/sbin/vpnc ]; then
		VPNC=/usr/sbin/vpnc
	else
		echo No vpnc daemon found, aborting...
		exit 1
	fi

So that it will use the vpnc executable in the current directory if one exists, then I was able to connect successfully, though now I'm having routing problems.  Good luck, and let me know if this helps anyone.

MHall119, were you getting the "Authentication Failed" error before fixing the script? I ask because even your script gives me the authentication error.

---

### Post by mhall119 on 2007-07-18
> **Lumar said:**
> MHall119, were you getting the "Authentication Failed" error before fixing the script? I ask because even your script gives me the authentication error.No, I was getting the "INVALID_EXCHANGE_TYPE" or something like that message.  The only time I've gotten the "Authentication Failed" message was when I mistyped my login or password.

---

### Post by haxor999 on 2007-07-19
hi,

quick update from me: I still don't have it working after checking out latest subversion build (main branch) and using the modified script. I'm still getting the "INVALID_EXCHANGE_TYPE" error. I have a securID token and so I believe I should be using the [FONT="Courier New"]--xauth-inter[/FONT] parameter. Also by looking at the windows Contivity client logs I see that the DH group should be 1 instead of the default of 2.

I may try once again sending the debug output to the dev list and hoping for some expert help.. (didn't get very far last time)

---

### Post by mhall119 on 2007-07-19
> **haxor999 said:**
> hi,

quick update from me: I still don't have it working after checking out latest subversion build (main branch) and using the modified script. I'm still getting the "INVALID_EXCHANGE_TYPE" error. I have a securID token and so I believe I should be using the [FONT="Courier New"]--xauth-inter[/FONT] parameter. Also by looking at the windows Contivity client logs I see that the DH group should be 1 instead of the default of 2.

I may try once again sending the debug output to the dev list and hoping for some expert help.. (didn't get very far last time)

Are you sure you're running the vpnc-connect script from the directory with your new build of vpnc?  You can run vpnc directly to make sure.  I'm also using a SecurId token, I didn't have to use the --xauth-inter parameter.  My Contivity client shows DH2, so I didn't have to change that parameter.  These are the only parameters I used in my .conf 

IPSec gateway 
IPSec ID 
IPSec secret 
Xauth username

---

### Post by opensrcrocks on 2007-07-29
[FONT="Georgia"][COLOR="Blue"][SIZE="3"]mhall119,

I recently came across this thread and compiled vpnc as said and can connect to my office VPN without any errors. 

The only thing is, once I am connected and assigned an ip-address, I have no routing into my VPN-ed zone. What am I missing?

I cannot ping any ip-address within the vpn. What do I need to do for routing? I tried to add routes similar to what my windows VPN client would do (nortel contivity) but have no routing.

Any light or insight into this would be greatly appreciated.

Thanks

-GGR
[/SIZE][/COLOR][/FONT]

---

### Post by mhall119 on 2007-07-29
> **opensrcrocks said:**
> [FONT="Georgia"][COLOR="Blue"][SIZE="3"]mhall119,

I recently came across this thread and compiled vpnc as said and can connect to my office VPN without any errors. 

The only thing is, once I am connected and assigned an ip-address, I have no routing into my VPN-ed zone. What am I missing?

I cannot ping any ip-address within the vpn. What do I need to do for routing? I tried to add routes similar to what my windows VPN client would do (nortel contivity) but have no routing.

Any light or insight into this would be greatly appreciated.
[/SIZE][/COLOR][/FONT]
The script ./vpnc-connect should change your routing tables to make the VPN connection your default route.  The only thing I haven't been able to get working is having the VPN's DNS server configured with resolvconf.

---

### Post by Prometheus7 on 2007-07-31
Any success with vpnc? Are all of you using the apani vpn for now and just fiddling around with vpnc? What advantage would vpnc have over the apani version (other than the 95$ hole in your wallet)?

---

### Post by mhall119 on 2007-07-31
> **Prometheus7 said:**
> Any success with vpnc? Are all of you using the apani vpn for now and just fiddling around with vpnc? What advantage would vpnc have over the apani version (other than the 95$ hole in your wallet)?I had success connecting with vpnc (the latest from subversion, not latest release).  I have not used the Apani client.  One advantage of vpnc that I don't think Apani has is integration with NetworkManager, making it easy to switch the vpn off and on.

---

### Post by Prometheus7 on 2007-07-31
so I am definitely getting somewhere with this as I initially got the same "INVALID_EXCHANGE_TYPE" error that everyone else was getting by running the following...

**sudo ./vpn-connect --dh dh1**

(I also edited my vpnc.conf file to mirror all of my settings in the windows version of my contivity client)

but now I get stuck up on my password. for the windows version, I enter a PIN and a secureID token code in two different boxes. I have tried entering only the PIN, only the secureID, and both (PIN followed by secureID), but nothing works!

any suggestions?

---

### Post by mflint on 2007-08-02
> **Prometheus7 said:**
> but now I get stuck up on my password. for the windows version, I enter a PIN and a secureID token code in two different boxes. I have tried entering only the PIN, only the secureID, and both (PIN followed by secureID), but nothing works!

I've successfully used both (PIN followed by secureID).

M

---

### Post by opensrcrocks on 2007-08-03
[COLOR="Blue"][FONT="Georgia"]mhall119,

Got my vpnc working. The reason why I could not ping any ip-addresses was 2 fold:

1. vpn network I login to, uses CCA and since I did not have CCA, I will not see any network.

2. After vpnc gets connected to the vpn server, there seems to be a route missing in the routing table:
route add -host <vpn-gateway>  gw <local-network-gateway>


I noticed that VPNC works in split tunnel mode, which is strange, as Nortel's client does not support it out of the box. Makes me wonder, how secure this is.

With respect to the DNS issue u have, I put in a script wrapper, which calls vpnc-connect. 

-Copy /etc/vpn-only-resolv.conf /etc/resolv.conf
-Restart network services
-call vpnc-connect
-add routes for vpn-network
-ping an ip-address to verify vpn connectivity.

Of course when disconnecting, you will need to have another script wrapper which does similar thing, but copies back the /etc/local-only-resolv.conf to /etc/resolv.conf and restart the network.

-GGR
[/FONT][/COLOR]

---

### Post by Prometheus7 on 2007-08-06
> **mflint said:**
> I've successfully used both (PIN followed by secureID).

M

What settings did you use to get yours working?

---

### Post by mflint on 2007-08-07
I didn't need any funkyness or hacking... just checked out from the SVN repo, built the application and ran it.

I forget the exact details (I'm away from my home machine), but it was something like

$ sudo ./vpc <host ip>
<enter user password for sudo>
<enter group id>
<enter group password>
<enter user id>
<enter 4-digit-pin immediately followed by secureID>

I didn't need to mess around with the routing table, or with starting/stopping network services.

---

### Post by Prometheus7 on 2007-08-07
That must be nice. I am still getting an "INVALID_EXCHANGE_TYPE" error. I have tried to change several parameters including the DH one and the XAUTH one.

---

### Post by kihon on 2007-08-16
Does  anyone know if this can be used when you only have the username and password? (ie no group id)

The Nortel windows client allows this, does vpnc?

Thanks

---

### Post by mhall119 on 2007-08-16
> **opensrcrocks said:**
> [COLOR="Blue"][FONT="Georgia"]mhall119,

Got my vpnc working. The reason why I could not ping any ip-addresses was 2 fold:

1. vpn network I login to, uses CCA and since I did not have CCA, I will not see any network.

2. After vpnc gets connected to the vpn server, there seems to be a route missing in the routing table:
route add -host <vpn-gateway>  gw <local-network-gateway>


I noticed that VPNC works in split tunnel mode, which is strange, as Nortel's client does not support it out of the box. Makes me wonder, how secure this is.

With respect to the DNS issue u have, I put in a script wrapper, which calls vpnc-connect. 

-Copy /etc/vpn-only-resolv.conf /etc/resolv.conf
-Restart network services
-call vpnc-connect
-add routes for vpn-network
-ping an ip-address to verify vpn connectivity.

Of course when disconnecting, you will need to have another script wrapper which does similar thing, but copies back the /etc/local-only-resolv.conf to /etc/resolv.conf and restart the network.

-GGR
[/FONT][/COLOR]

Thanks for the info.  My network uses CCA too, so I've given up using my Linux box as nobody can tell me how to authenticate with the CCA server.

---

### Post by mhall119 on 2007-08-16
> **kihon said:**
> Does  anyone know if this can be used when you only have the username and password? (ie no group id)

The Nortel windows client allows this, does vpnc?

Thanks

The Nortel client uses them too, they're just not displayed in the client window.  I'm not sure how to get that information from the client setup though, I asked a co-worker who already knew what they were.

---

### Post by haxor999 on 2007-08-30
> **mhall119 said:**
> The Nortel client uses them too, they're just not displayed in the client window.  I'm not sure how to get that information from the client setup though, I asked a co-worker who already knew what they were.

I ended up using one of those questionable utilities that unhides password fields in windows to get my group password out of the Nortel client's settings screen. Don't recall which one though.

---

### Post by erchewy on 2007-09-24
hello, after read all the post i cannot connect to my nortel vpn box. In my case, I onlly use username and password to connect in windows client, no group id and no group password. Can anyone resume howto connect to nortel contivity box? thanks in advance. regards.

---

### Post by mhall119 on 2007-09-24
> **erchewy said:**
> hello, after read all the post i cannot connect to my nortel vpn box. In my case, I onlly use username and password to connect in windows client, no group id and no group password. Can anyone resume howto connect to nortel contivity box? thanks in advance. regards.

As mentioned above, the Windows client does indeed use group id and group password, but they are hidden in your local configuration, not displayed on the screen.  Ask your network administrator for this information.

---

### Post by erchewy on 2007-09-24
ok. I will try it. One more question, when i connect to vpn in windows, the vpn box assign me a virtual ip address, vpnc works simillar?? I need to obtain the virtual ip addres, cause only a few ip's address can connect through the firewall. thanks.

regards.

---

### Post by mhall119 on 2007-09-24
> **erchewy said:**
> ok. I will try it. One more question, when i connect to vpn in windows, the vpn box assign me a virtual ip address, vpnc works simillar?? I need to obtain the virtual ip addres, cause only a few ip's address can connect through the firewall. thanks.
vpnc will create a virtual NIC with the new virtual IP address, then (in theory) setup your routing tables to send all VPN traffic through that virtual NIC.  There are options to specify what destination addresses should go through the VPN, which should allow all other traffic to go through your standard internet connection.

---

### Post by erchewy on 2007-09-25
hello, i request to my network admin for the group id and group password, and he tell me that the only authentication options we use is username and password. He tell me that we don't use group id and group password, is absolutly necesary??? I can't connect without this?? thanks.

regards.

---

### Post by erchewy on 2007-09-25
I look at the windows vpn client and in the authentication options, and i have marked the "username and password authentication" option. If I mark the "group security authentication" the vpn don't work. Really, i don't undersand if nortel provides a free windows client, why they don't provide the linux too. thanks.

---

### Post by mhall119 on 2007-09-25
> **erchewy said:**
> I look at the windows vpn client and in the authentication options, and i have marked the "username and password authentication" option. If I mark the "group security authentication" the vpn don't work. Really, i don't undersand if nortel provides a free windows client, why they don't provide the linux too. thanks.

It's possible that your VPN configuration doesn't require a group id and group passoword.  If that is the case, I'm not sure how you need to configure vpnc, sorry.  There is an official linux client for the VPN, but it is commercial and costs about $50, I don't remember who sells it.

---

### Post by asperkins on 2007-10-01
I have successfully connected to our notel contivity vpn. One minor detail. After about 10 seconds the connection stops working. It is consistently about 10 seconds. Any ideas?

Thanks
Tony

---

### Post by turbulence on 2007-10-01
I have tried to connect using SecurID.  However, I receive the following error every time it tries to authenticate.

*** glibc detected *** ./vpnc: free(): invalid next size (fast): 0x00000000006191c0 ***

I get the "INVALID_EXCHANGE_TYPE" error if I enter the incorrect IPSec information.

---

### Post by mhall119 on 2007-10-02
> **turbulence said:**
> I have tried to connect using SecurID.  However, I receive the following error every time it tries to authenticate.

*** glibc detected *** ./vpnc: free(): invalid next size (fast): 0x00000000006191c0 ***

I get the "INVALID_EXCHANGE_TYPE" error if I enter the incorrect IPSec information.
Are you using the Ubuntu package, or the latest from svn?  As far as I am aware, the Ubuntu package doesn't support Nortel's broken IPSEC implementation, but the latest code in svn should (that is the one we've been having some limited success with on here).

---

### Post by asperkins on 2007-10-02
Ok, another clue from the server log file.

OCT 01 12:38:43 <notice,auth> Syslog 0 : Session: IPSEC[sgxxxxx]:545149 Incoming client version (V04_15), minimum version (V04_91) push action (Force Logoff), action applied

So it seems that after 10 seconds or so the server checks my client version and if it's not 4_91 or greater it kicks me off. I can't find where this version is reported to the server. Anyone know?

---

### Post by turbulence on 2007-10-02
> **mhall119 said:**
> Are you using the Ubuntu package, or the latest from svn?  As far as I am aware, the Ubuntu package doesn't support Nortel's broken IPSEC implementation, but the latest code in svn should (that is the one we've been having some limited success with on here).

I am using the latest code from svn

---

### Post by hartown on 2007-10-08
Can you point me to a link as to how to get Apani working under Feisty? I only saw instructions for RedHat and Suse on Apani's site.

---

### Post by NobodySpecial on 2007-10-08
hartown - your question is off topic, but you can find help installing Apani drivers in these posts:
[http://www.ubuntuforums.org/showthread.php?t=222774]("http://www.ubuntuforums.org/showthread.php?t=222774")
[http://www.ubuntuforums.org/showthread.php?t=110843]("http://www.ubuntuforums.org/showthread.php?t=110843")

---

### Post by necrit on 2007-10-27
> **asperkins said:**
> I have successfully connected to our notel contivity vpn. One minor detail. After about 10 seconds the connection stops working. It is consistently about 10 seconds. Any ideas?

Thanks
Tony

Thats due to a firewall error...100% of the time.  open 10000 udp and 500 udp on your local network. (or check your ubuntu firewall settings.  i work with the ACE server ( network server side of contivity client)  they always report that same scenario (connection dropped due to peer disconnect)....is just a firewalll.

> **mhall119 said:**
> As mentioned above, the Windows client does indeed use group id and group password, but they are hidden in your local configuration, not displayed on the screen.  Ask your network administrator for this information.

Goto Options > Authentication Options.  You will at least fine the group id for this connection.  Or you need to locate the installer provided by your company.  In it you will see a set of files.  v6 of the contivity client stores the passwords in the group.ini file and group id's in a *.tbk file.  you may have to get the installer to a box running 7zip so you can right click extract archive on the executable.  Thsi is a farfetched shot only suggested if your companies helpdesk cannot help you by giving you that information.  usually your remote access team will have it under their global network list.  but i digress.  hope that helps.

---

### Post by Chudilo on 2007-11-08
> **erchewy said:**
> hello, i request to my network admin for the group id and group password, and he tell me that the only authentication options we use is username and password. He tell me that we don't use group id and group password, is absolutly necesary??? I can't connect without this?? thanks.

regards.

I've spoken with our Admin. He also told me that we do not use a Group ID /Password for authentication. 
However, I got a group name out him. (This is directly from the vpn concentrator config)
The Group ID looks like this "/xxxx/xxxxxxxxx"
That still did not work with VPNC without a password  

Also for some reason I get prompted for all the parameters twice whether I use a fake group password or not.

I am getting the following errors:
/usr/sbin/vpnc: binding to 0.0.0.0:500: Address already in use
/usr/sbin/vpnc: response was invalid [1]:  (ISAKMP_N_INVALID_EXCHANGE_TYPE)(7)

I am using revision 263 from svn

---

### Post by autarch on 2007-11-22
> **turbulence said:**
> I have tried to connect using SecurID.  However, I receive the following error every time it tries to authenticate.

*** glibc detected *** ./vpnc: free(): invalid next size (fast): 0x00000000006191c0 ***

I get the "INVALID_EXCHANGE_TYPE" error if I enter the incorrect IPSec information.

I was seeing the same issue. I'm pretty sure that this is because the code in question does not work under 64-bit Linux. I tried the same code on a 32-bit system and it worked. Both systems were running Gutsy.

---

### Post by aquaraquar on 2007-11-25
Hi guys,
I'm using subversion 270 form svn and getting an "authentication failed" message although I'm pretty sure that my username and passwords are ok ( works with contivity ). The group authentication thing works fine because when I type a dummy password It warns me to check my group password, but when it is correct it works fine. 

I'm using the same username and password that I use with contivity, should I use sth else ( eg. sb here told to use 4-digit-PIN followed by SecureID ), what are those??? Thanks

---

### Post by rumpelstilz on 2007-11-26
I'm having the exact same problem as aquaraquar. 

In Wireshark, I can see that it does connect and goes through 3 send-recv cycles.

I've had the router admin send me the router log filtered by my IP address, and strangely there is *nothing* in it from my Linux connections. I do see my Windows connections logged, though.

Any hints / ideas?

I've tried mailing to [email]vpnc-devel@unix-ag.uni-kl.de[/email] but it replied that this is a members-only list and an admin will have to review my request and decide if it can be admitted.

---

### Post by ejrives on 2007-12-19
I was able to get this working , but there were a few things that I thought I'd share with everyone.

1. I did not use the vpnc-connect script at all. Just a simple ./vpnc from the dir created from subversion.
2. I had to manually fill in the information after running ./vpnc. Filling out the vnpc.conf gave me the INVALID_EXCHANGE_TYPE" error.
3. My company has over 10 different VPN switches you can connect to. There were a few that gave me the INVALID_EXCHANGE_TYPE error, whereas there are other that would connect. Those of you getting that error try another switch if applicable.
4. routes had to be created and pointed out the tun0 interface
5. nameserver entries had to be made in /etc/resolv.conf

Hope this helps somewhat.

---

### Post by FarJumper on 2008-01-13
I'm trying to connect to my corporate VPN, but the only message I get is:

vpnc: xauth packet unsupported: ATTRIBUTES_NOT_SUPPORTED

Please help.
thanks.

---

### Post by Chudilo on 2008-02-14
I hear that some people are working on merging the Nortel branch back into the main trunk.

---

### Post by boltronics on 2008-02-25
I did find this: [http://www.gossamer-threads.com/lists/vpnc/devel/2209?do=post_view_threaded](http://www.gossamer-threads.com/lists/vpnc/devel/2209?do=post_view_threaded)

It would be so wonderful to have this included in the next version of Ubuntu. I can dream... :)

---

### Post by sionut on 2008-02-29
> **necrit said:**
> 
Goto Options > Authentication Options.  You will at least fine the group id for this connection.  Or you need to locate the installer provided by your company.  In it you will see a set of files.  v6 of the contivity client stores the passwords in the group.ini file and group id's in a *.tbk file.  you may have to get the installer to a box running 7zip so you can right click extract archive on the executable.  Thsi is a farfetched shot only suggested if your companies helpdesk cannot help you by giving you that information.  usually your remote access team will have it under their global network list.  but i digress.  hope that helps.

I'm having the same problem as others before me.. I don't have a groupId or a group password. I went to windows (where I have Contivity installed) and looked in the tkb file. Unfortunately there is no groupid there (it's empty) nor a password.. 
Also, when I go to Options > Authentication Options, I don't see any group there...

Anybody, any other suggestion ?

---

### Post by BigStan23 on 2008-02-29
Thanks for the link.  I downloaded the current development snap shot, compiled it and I got it working.

I can now successfully connect to my work through Ubuntu!  I did have to play around with the routing in order to get split networking to work tough.  Note that this client works slightly different then the (non working for me, previous nortel vpnc build), you need to pass the default script (or one your wrote yourself) when you run vpnc.  I actually had to read the README to figure this out.  I know, the horrors!

Thanks for the heads up!

> **boltronics said:**
> I did find this: [http://www.gossamer-threads.com/lists/vpnc/devel/2209?do=post_view_threaded](http://www.gossamer-threads.com/lists/vpnc/devel/2209?do=post_view_threaded)

It would be so wonderful to have this included in the next version of Ubuntu. I can dream... :)

---

### Post by NobodySpecial on 2008-02-29
BigStan23 - We are all waiting with baited breath for a how-to!  :)

---

### Post by BigStan23 on 2008-02-29
> **NobodySpecial said:**
> BigStan23 - We are all waiting with baited breath for a how-to!  :)

Well this is what worked for me:

1) Download and unzip vpnc-nortel_merge_with_284.tar.gz from here: [LINK.]("http://www.gossamer-threads.com/lists/vpnc/devel/2209?do=post_view_threaded")

2) cd into the directory and type make, this should compile the program.  (if you don't have make/gcc/etc you need to install build-essentials at the least)

3) Create a vpnc.conf file in your /etc directory with the following info (if you don't do this, it will prompt you for it every time, see the readme file for additional info):

# This is a sample vpnc.conf configuration file.
IPSec gateway 127.0.0.1
IPSec ID laughing-vpn
IPSec secret hahaha
Xauth username geoffk

4) According to the readme you may need to modify the included vpnc-script, but I just used the one provided.  Also if you copy the vpnc-script to /etc/vpnc/vpnc-script it will be used by default, but for my example I just referenced the one in the build directory directly

5) At this point you should be able connect the vpn:

sudo ./vpnc --script /somepath/vpnc-nortel/vpnc-script

The password is actually two items for me (in the nortel contivity client), the first is a PIN followed by my secureid number.  You concatenate these two together, so if your PIN is 12345 and the number on the secureid is 987654 the password would be 12345987654. 

6) For me this bought up a vpn, but I could ONLY see my companies network (normal internet traffic no longer worked).  I fixed this with some info from this post:

[http://ubuntuforums.org/showthread.php?t=139947&highlight=vpnc+split+route]("http://ubuntuforums.org/showthread.php?t=139947&highlight=vpnc+split+route")

So right now I do the following to get my internet working again:

sudo route del default gw 0.0.0.0
#This is my local gateway
sudo route add default gw 192.168.0.1
#This is my works IP subnet, we actually have several so I have several route add lines
sudo route add -net xxx.yyy..0.0 netmask 255.255.0.0 dev tun0

And that's it, seems to work great so far.

---

### Post by sionut on 2008-03-04
Did you use the groupname to connect to your vpn provider ? I couldn't realize from your post if you are using one or not...

---

### Post by osx424242 on 2008-03-05
BigStan23, you are a **peach**!  I had Nortel's client working but I'm excited to be using this, plus now I will be able to convince some coworkers to set up Ubuntu at home and use this method :).

sionut, he did use a groupname: "IPSec ID" is the groupname and "IPSec secret" is the group password.  Luckily, my company supports RHEL and has a slideset that includes a (linux-specific) group ID and group password.  I guess, try without those if you don't have one?  Good luck....

By the way, I had to put vpnc.conf _and_ vpnc-script ("sudo ./vpnc --script ./vpnc-script" started the connect process but didn't finish, and complained about not finding vpnc-script when it finished) into /etc/vpnc/ to get it to work (and I had to stop the nortel client (/etc/init.d/netlock stop)) to successfully connect.

---

### Post by Lumar on 2008-03-08
I still get the "vpnc: response was invalid [1]:  (ISAKMP_N_INVALID_EXCHANGE_TYPE)(7)" error...

I know my groupid and group password... it doesn't matter what I do I can't get around this error.

---

### Post by osx424242 on 2008-03-09
The code (search vpnc.c for "response was invalid [1]") apparently doesn't understand the "exchange_type" in the (first?) response (it is expecting 'aggressive' but is getting something else).  Someone who understands vpnc better will have to debug.  On your own, you could try just commenting out the if statement and its reject= line, recompiling, and see what happens :)  Also, if you could stick a printf in there, maybe you can e-mail the output to the guy who got this latest revision working, and ask for help.  But, your network must be set up differently, so not sure others will be able to help.

---

### Post by oldcyberdude on 2008-03-11
I'm in the same boat.  I have valid group id and password and get "vpnc: response was invalid [1]: (ISAKMP_N_INVALID_EXCHANGE_TYPE)(7)" error...    be nice to get vpnc working.   BTW, one posting asked why get vpnc running vs. Apani,  was it the $95.

My answer no!  I just don't like a company that sells an obviously unsupported product, acknowledges it and when provided the fixes still doesn't incorporate them into the product.   AND my company still buys the thing.

---

### Post by oldcyberdude on 2008-03-11
Check this posting 
[http://lists.unix-ag.uni-kl.de/pipermail/vpnc-devel/2007-August/001647.html](http://lists.unix-ag.uni-kl.de/pipermail/vpnc-devel/2007-August/001647.html)

"vpnc currently only supports aggressive mode (3 packet exchange), not
the alternative main mode (6 packet exchange). This makes sense, because
unless you use certificates for Phase I authentication, main mode won't
work. And certificates are not (yet) supported (see TODO). I hope this
explains this a bit. So it's most likely not working because the
concentrator uses a mode that is not supported by vpnc."

I don't quite understand this comment but doesn't sound good

---

### Post by shumifan50 on 2008-04-11
I have a wireless network and it works fine to see other local PCs from ubuntu. I installed vpnc as above after compiling etc and run the program with the supplied sript. It all seems to work fine, asking for my login (groupid/secret setup in conf file) and VPNC goes into the background (can see with ps-A). However I cant see anything on the work network, but I still see all on my local network (through the wireless as wel).

I am by no means a Linux fundi, so any help will be appreciated.

When I do "ifconfig tun0" it shows a 10.63.... ip which matches the work network,also " UP POINTTOPOINT RUNNING NOARP MULTICAST MTU:1412 Metric 1"

Of some concern is that the inetaddr is 10.63.111.x with a netmask of 255.255.255.240 and the machine I try to get to is 10.63.40.31.

Any advice please!

Note this is on a Vostro 1000

Many thanks for the useful post in getting it running!

---

### Post by FarJumper on 2008-04-11
> **necrit said:**
> Thats due to a firewall error...100% of the time.  open 10000 udp and 500 udp on your local network. (or check your ubuntu firewall settings.  i work with the ACE server ( network server side of contivity client)  they always report that same scenario (connection dropped due to peer disconnect)....is just a firewalll.

I have absilutely the same problem with dying in 10 sec. What the solution for that? I don't have firewall on my machine. And at the same time nortel VPN client for windows works fine.

---

### Post by ralfonso on 2008-04-23
Can anyone tell me what the Nortel client reports to the server as its application version string?  I've confirmed that my server checks to make sure the official client is being used and I'm hoping if I can fake it I'll get past the "authentication failed" error that I'm getting.

---

### Post by zfmcdull on 2008-04-27
I followed BigStan23's instruction, works for me. This is fantastic, never need to go back to my windows machine at home. PS. My Ubuntu is 8.04

---

### Post by Mohonri on 2008-05-13
I wish I had seen this thread earlier--I'm trying to do exactly this!

However, while following BigStan23's instructions, I get the following error when I try to run ./vpnc:
response was invalid [2]:  (ISAKMP_N_BAD_PROPOSAL_SYNTAX)(15)

I'm completely new to vpnc, so I don't know what this means, or how to fix it.  What do you suggest?

---

### Post by rkleemann on 2008-06-23
BigStan23, I was able to get a connection also!

Thank you very much for your helpful guide.

But I do have problems... it seems DNS isn't working. I'm not able to get to internal hostnames on the company network.

I haven't yet tried splitting the network, I'm just connecting to the VPN and testing the internal network.

---

### Post by rkleemann on 2008-06-23
Actually I'm having troubles.

vpnc states that I was able to connect. However, once that connection is established, I can't even access the internal network. My routing table is gone.

So apparently the vpn connection is established but it wipes out my routing and I can't do anything.

---

### Post by irregardlessly on 2008-06-30
> **rumpelstilz said:**
> I'm having the exact same problem as aquaraquar. 

In Wireshark, I can see that it does connect and goes through 3 send-recv cycles.

I've had the router admin send me the router log filtered by my IP address, and strangely there is *nothing* in it from my Linux connections. I do see my Windows connections logged, though.

Any hints / ideas?

I've tried mailing to [email]vpnc-devel@unix-ag.uni-kl.de[/email] but it replied that this is a members-only list and an admin will have to review my request and decide if it can be admitted.

I have the same problem.  Let me know if you figure this out.

---

### Post by aquaraquar on 2008-07-19
> **irregardlessly said:**
> I have the same problem.  Let me know if you figure this out.

> **oldcyberdude said:**
> Check this posting 
[http://lists.unix-ag.uni-kl.de/pipermail/vpnc-devel/2007-August/001647.html](http://lists.unix-ag.uni-kl.de/pipermail/vpnc-devel/2007-August/001647.html)

"vpnc currently only supports aggressive mode (3 packet exchange), not
the alternative main mode (6 packet exchange). This makes sense, because
unless you use certificates for Phase I authentication, main mode won't
work. And certificates are not (yet) supported (see TODO). I hope this
explains this a bit. So it's most likely not working because the
concentrator uses a mode that is not supported by vpnc."

I don't quite understand this comment but doesn't sound good

irregardlessly: probably that's the problem, vpnc does not support yet the authentication method that the routers we're trying to connect! that's the reason why vpnc worked for some, failed for others...

---

### Post by area124 on 2008-07-22
I used BigStan23's work instructions and I still had an issue with getting to the external internet. I found that my /etc/nsswitch.conf file had the following:

hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

By moving the 'dns' entry forward solved all my problems; etc,

hosts: dns files mdns4_minimal {NOTFOUND=return ] mdns4

I have to connect to different VPNs, so to make my life easier, I created 
a configuration file for each connection in my /etc/vpnc directory and then a connection script in my bin directory for each config file. 

# /etc/config/conn1.conf
IPSec gateway hostname.domain.com
IPSec ID myTokenGrpId
IPSec secret myTokenGrpIdPw
Xauth username TokenUsrId


#!/usr/bin/ksh
# This is in my 'bin' directory
# Location of VPN builid node.
export VPNC_DIR=/home/myhome/ThirdParty/vpnc-nortel/vpnc-nortel
cd $VPNC_DIR
# Connect using the default scrip and the configuration file located
# in /etc/vpnc
sudo ./vpnc --script $VPNC_DIR/vpnc-script conn1
# Set routes for the connection
echo "Wait for new routes...."
sleep 2
addConn1Routes

The 'addConn1Routes' is per BigStan23's notes.
#!/usr/bin/ksh
# This will set up routes after the VPN has been established.
sudo route del default gw 0.0.0.0
# Set up my local gatway
sudo route add default gw 192.168.1.1
# Set up IP subnet on tunel 0. There may be several.
sudo route add -net xxx.yy.0.0 netmask 255.255.0.0 dev tun0
echo "Done...."

I leave the connection up for days at a time with no problems! :guitar:

BigStan23 you are still the best! Thanks so much for taking the time to put together the detailed work instructions. I hope that others will find these notes helpful as well.

---

