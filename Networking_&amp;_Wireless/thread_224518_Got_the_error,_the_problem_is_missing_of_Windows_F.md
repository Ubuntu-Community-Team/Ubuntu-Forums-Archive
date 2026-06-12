---
title: "Got the error, the problem is missing of Windows Firewall Client"
date: 2006-07-28
forum: Networking &amp; Wireless
---

### Post by true_friend on 2006-07-28
Hi.
i was stuggling from 10 days or more about my linux internet configuration. the networking was alright but i could not reach the interne, today i tried an idea. i have dual boot system xp + ubuntu DD. i uninstalled the Windows Firewall Client and tried to open a website. the error was same by the firefox that server not found the same error is on linux. now i understand that Windows Firewall Client is the way to connect to internet through my Windows Server 2003 using local server. now i want to know is there any tool available in linux to act just like Windwos Firewall Client???
or any other solution in ur opinion , i think if there is no tool like Windows Firewall Client is available then i have to ask my service provider to off the firewall he is using ( he was denying last time when i confirmed about existing of firewall).
plz plz plz suggest me i am about to reach a solution.
Regards
True_Friend

---

### Post by OpsVentus on 2006-07-28
Hello friend,

Please tell us more about your network.
What configuration do you use on your Windows server?
What settings do you got on you Ubuntu?

Cheers,
Bart.

---

### Post by true_friend on 2006-07-28
thnx for reply. i am just coming after discussing all about the configuration of the server. They are using ISA server. i asked to off the firewall he said he can not because all the clients will go down then. He says that through ISA server he can monitor the systems well. Windows xp 2003 ( i think server edition) and the ISA server as i told is used by my local server. in xp all clients have to install Windows Firewall Client to connect to internet. but in linux there is no WFC so i can not reach the net. and my provider is also denying to change the settings as he sys it will be unserure for him. linux he will not use also as he does not want to change his currenct configuration. so the solution may be something  on my desktop only otherwise i can not get internet on my linux system:rolleyes: :rolleyes: .

---

### Post by true_friend on 2006-07-28
my ubuntu settings are
static ip 
DNS 192.168.0.1
IP 192.168.0.139
Server IP 192.168.0.1
Net Mask 255.255.255.0
Default Gateway 192.168.0.1
Anyhows these are correct 100% surety. as i can access my server's shared folder. only the problem in that ISAserver which is blocking my communication when i try to connect to internet. on xp the Windows Firewall Client is the master key for ISAserver. but on linux:confused: . ISAserver address is also 192.168.0.1.

---

### Post by OpsVentus on 2006-07-28
So your network is like this:
Internet - crappy firewall ISP - Your Windows 2003 server - Ubuntu
?

Option 1, change ISP, he dosn't know what he's doing.
Option 2, share the internet via your windows 2003 server properly.

Bart.

---

### Post by true_friend on 2006-07-28
i am a cable net user. my server means the provider's machine. he is using ISAserver on his xp system. he is connected with isp and i am connected with him. now the problem is to configure my ubuntu system with the local server ( my internet provider's machine) using ISAserver. my xp system is working well. as i told eralier i have dual boot system.xp 2006 + Ubuntu 6.06

---

### Post by tturrisi on 2006-07-28
Find out from your isp exactly what rules are required by the firewall in order to connect to internet.  These rules can then be duplicated using the firewall that is built into ununtu (but OFF by default).  Firestarter is a frontend (GUI) to the iptables firewall in ubuntu.

---

### Post by true_friend on 2006-07-28
he told me during discussion they have all information about the LAN card used by the clent's system. u mean these kind of rules??
or the rules like the ISAserver's address. here in my system its address is 192.168.0.1  .
one thing more the xp's default firewall is not **on**. so how we can configure ubuntu's firewall.

---

### Post by OpsVentus on 2006-07-28
Quick search on the internet and we got an howto:
[http://www.linux.com/howtos/Web-Browsing-Behind-ISA-Server-HOWTO.shtml](http://www.linux.com/howtos/Web-Browsing-Behind-ISA-Server-HOWTO.shtml)

Good luck,
Bart.

---

### Post by true_friend on 2006-07-28
Thnx buddy.
i am reading this article and try its solutions.
thnx a lot

---

### Post by true_friend on 2006-07-28
3. Method #1 - Enable Basic Authentication

As mentioned above, due to Integrated Authentication support configured on ISA server, third party browsers do not work behind it. In this situation you can make use of another authentication scheme called 'Basic Authentication', commonly supported by most browsers and most importantly by ISA Server too. If you work in a security conscious environment this method is not recommended since during basic authentication, the username and password sent are loosely encrypted.

The point here is that to proceed with this method you will have to make sure that you have legitimate access over configuring the ISA Server. If you cannot access the server configuration console, then move on to the second method in the following section.

3.1 Server Side Configuration

All you need to do is fire up 'ISA Management' and follow these steps:

   1. Right-click your server and click on Properties.
   2. Go to the Outgoing Web Requests tab, click the configured listener that you want to change, and then click Edit.
   3. Click Basic authentication, and then select the domain in which the accounts exist that you want to authenticate.
   4. Now it's time to move on to your Linux-based browser.

3.2 Client Side Configuration

In particular, we will take Netscape as an example here.

   1. Start Netscape Communicator.
   2. Click on the Edit menu and click Preferences.
   3. Expand 'Advanced' node and click on 'Proxies'; you will see some options on the left.
   4. Click on Manual proxy configuration, then click on the View button.
   5. Put your ISA Server's IP address in the HTTP: box and the port where web cache is listening (usually 8080, depends what you set).
   6. Click on OK to confirm your changes.
   7. You will return back to the Preferences dialog.
   8. Click on OK to apply your changes.

Load up a test url in your browser, it will ask you for authentication information, In place of user, type DOMAIN\USER, where your DOMAIN being the Windows domain, and USER being a legitimate domain user. In place of password, type the user's password. Click on OK to continue. For example:

User: CABLENET\Raheel
Password: Mypassword

Where CABLENET is my domain, Raheel is the user id
and Mypassword is my password.

You should now see the page loading successfully. If you use a different browser you will need to explore and see if it supports Basic Authentication. 
..........................................................
this method is for netscap cmmunicator. i think i can apply it to  firefox also but what would be the domain, the windows domain as asked here.
..................................................................
Load up a test url in your browser, it will ask you for authentication information, In place of user, type DOMAIN\USER, where your DOMAIN being the Windows domain, and USER being a legitimate domain user. In place of password, type the user's password. Click on OK to continue. For example:

User: CABLENET\Raheel
Password: Mypassword

Where CABLENET is my domain, Raheel is the user id
and Mypassword is my password.
..............................................................
my ip address is my domain????
i have no other domain allotted or i have to ask for a domain.

---

### Post by true_friend on 2006-07-28
thinking to install [NTLM Authorization Proxy Server]("https://sourceforge.net/project/showfiles.php?group_id=69259&package_id=68110&release_id=388621") but it requires python interperator. is there support of pythor interperator in ubuntu 6.06. this software is written in python 1.5.2.

---

### Post by OpsVentus on 2006-07-28
A lot of software in Ubuntu is python, it's supported.

---

### Post by OpsVentus on 2006-07-28
What are the settings your ISP gave you?
Did he gave you and domainname, username and password?

Mail this to your provider, ask him what to do. He should be willing to help.

But again, can you consider changing your ISP? I would not want a ISP if he's not willing to help.

Cheers,
Bart.

---

### Post by true_friend on 2006-07-28
i can not dear. because there is only :( cable net provider in our area. i am in Pakistan. wish could be in some europian country at this time ;) the situation would be very different. but alas it is Pakistan where internet is growing still, will be more comfortable but not now a few time is required.

---

### Post by true_friend on 2006-07-28
no domain name and password given me by the provider also :(

---

### Post by OpsVentus on 2006-07-28
Which settings does he give you to use under Windows?

---

### Post by true_friend on 2006-07-28
Physical Address: 00-20-ED-2C-EF-48
IP Address: 192.168.0.139
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.0.1
DNS Servers: 192.168.0.1, 0.0.0.0
WINS Server:

---

### Post by true_friend on 2006-07-28
(static ip)

---

### Post by OpsVentus on 2006-08-02
And what settings regarding the windows firewall?

---

