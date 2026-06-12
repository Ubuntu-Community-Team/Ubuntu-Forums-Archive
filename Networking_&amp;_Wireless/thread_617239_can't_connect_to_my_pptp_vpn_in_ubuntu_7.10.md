---
title: "can't connect to my pptp vpn in ubuntu 7.10"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by stvdel on 2007-11-19
Hello, I am new at using Ubuntu and usually have used windows for vpn stuff. I have the vpn
connection installed in 7.10 but when I try to connect it will not. How am I supposed to configure
the connection. In the ubuntu vpn config. is the  gateway supposed to be the address used like when you set it up in windows? Also how else should I set up the rest of the settings?

---

### Post by stvdel on 2007-11-20
bump

---

### Post by CHFFriday on 2007-11-20
The gateway is the IP address or Domain Name of you VPN server. Enter that information then enter other information as necessary. You may need to get some help from you companies IT department. You will also need your user name and password.

CHFFriday

---

### Post by stvdel on 2007-11-20
yes I entered in the gateway section the ip address just like I would when setting it up in
windows vpn , when I try to enter the username and password it trys to connect and then
says error cant connect. i have talked to the it  guys but they have no experience setting
up the vpn with linux only windows.

---

### Post by CHFFriday on 2007-11-20
You can try this but with out the info we need it may not work.

1st Go to Configure VPN Connection.
2nd Pick your Connection to work.
3rd On the Connection Tab pick PPTP. It should be the only on.
4th On the Authentication Tab UNCHECK all 
5th On the Compression & Encryption tab CHECK Require 128 bit MPPE and Enable Statefull MPPE
6th On the PPP option tab leave it as is.
7th On the Routing Tab leave it as is.
Click Apply then exit

Then try to connect.

CHFFriday

---

### Post by stvdel on 2007-11-20
Hello, I tried just as you said but it still gets the cant connect error. When you say the information
we need, what information is that exactly. If you can tell me I can ask about this information.

---

### Post by stvdel on 2007-11-21
bump

---

### Post by CHFFriday on 2007-11-21
stvdel,
Check with the IT guy and ask him if they use a MS VPN server or do they use a VPN end point router.

Some infi you can get is from the MS Windows Dial UP connection. On the Windows box Goto Start-> 
Control Panel After the contro panel loads find the Network Connection Icon and open it. Then find the Icon for you work connection. Then right click on it and goto Properties.

You need the information here

On the Options Tab. What is there?
On the Security Tab. What is there?
On the Networking Tab. What is there? 
On the Networking Tab under setting what is there?

DO NOT CHANGE ANYTHING!! Then click on CANCEL

Let me know what you have.

CHFFriday

---

### Post by J1m on 2007-11-23
Hi all,

I also had problems connecting to our VPN at work (and I'm the network admin at work ;D)

If the vpn you have set up is trying to connect but failing then I think it's just a case of getting your check boxes right.  

I think for most Microsoft VPN servers the following setting apply: (Quoted from zveroboy from a related post)

_______________________________-
"Authentication Tab:
Check Refuse EAP.
Everything else unchecked

Compression & Encryption Tab:
Leave all the compression options unchecked
Check all the encryption options, i.e. Require MPPE encryption, Require 128 bit MPPE Encryption, Enable Stateful MPPE

PPP Options Tab:
I think I left everything at default here, but here is a quick run down:
Custom PPP options: <blank>
IP Options: Check Use Peer DNS, Exclusive device access (UUCP-style lock), Debug Output
Packet aprams: MTU 1416 MRU 1416
Delays and Timeouts:
connect-delay (greyed out), lcp-echo-failure: 10, lcp-echo-interval: 10

Routing:
Check Peer DNS through tunnel
Second option Only use VPN connection for these addresses is optional - I am not entirely sure how to use this option.

Now hit 'Forward' button and 'Apply."
__________________________________________-

The setting I have had to use however differ from the above as follows: I have to tick "Refuse MS CHAPS" - "Tick Allow BSD Compression" - UNTICK "Require MPPE encryption" and "Require 128 bit MPPE Encryption"  and my MTU setting is 1400.

I was having al kinds of weird could connect / couldn't connect issues - connected but couldn't do anything issues - and I couldn't decipher the syslog messages or find any posts with the errors I was receiving.

I just decided to go through the settings meticulously changing them one at a time and I finally hit the jackpot.

With a little patience and fiddling - the network-manager-pptp settings manager should be able to get you connected.

Good Luck,

J1m

---

### Post by stvdel on 2007-11-24
CHFFriday- I am still waiting on the IT guys to answer the question about the end point or ms. But I do have the settings from windows for you.

options
check- display progress while connecting
check- prompt for name password certificate etc.
check- include windows logon domain

redialing options
redial attemts- 3
time between dial- 1minute
idle time before hangup- never
check- redial if line is dropped

ppp settings box
check- enable lcp extensions
uncheck- enable software compression
uncheck- negotiate multi link for single link connections

security
typical recommended settings
check- verify my identity
check- require secured password
uncheck- automatically use windows logon name as a password and domain
check- require data encryption disconnect if none

advanced security box
check- require encryption
uncheck- use eap
check- allow these protocols
uncheck- unencrypted password
uncheck- chap
check- microsoft chap 2
uncheck- use windows name automatically

type of vpn
automatic

ipsec settings box
uncheck- use preshared key for authentication
check- use certification for authentication
check- verify the name and usage attributes of servers certificate

nocheck- ipv6
check-ipv4
check-file and printer sharing microsoft
check-Qos packet scheduler
check-client for microsoft networks

That is everything for the vpn settings under vista.

J1m- I tried all the settings you posted and I still get the same cant connect message, I have tried many more odd combos and still the same thing. I will also post back as soon as I find out about the vpn server or end point router. Please help if you can. Thanks

---

### Post by stvdel on 2007-11-25
bump

---

### Post by stvdel on 2007-11-26
Ok, I found out that I am using a ms vpn server. Please help if you can.

---

### Post by tact on 2007-11-26
Must admit I am a little confused after reading all the posts in this thread...  so let me start with a clean sheet...

Have a look at all the attached pics and confirm your setup is as per the pics... (essential for MS PPTP VPN to have the "refuse EAP" checked)....

Once we are sure your config looks like the attached pics...  then I will scratch and think some more.  :)

---

### Post by tact on 2007-11-26
another quick shot in the dark - are you running a firewall?  

Firestarter for example does not permit VPN passthru.  Don't be fooled if it looks like the VPN connected and the little padlock symbol is present on the networkmanager applet icon - nothing will pass thru.  No fix for it.  Just have to turn off firestarter before initiating VPN connection.

(dont forget to reenable when finished on the VPN)

---

### Post by stvdel on 2007-11-26
I tried exactly like you said, the configuration for the vpn matched your settings and I turned off firestarter firewall. It still has the same can't connect error like before. Thanks for the reply though. Any help is appreciated.

---

### Post by tact on 2007-11-26
can you capture a screenshot of the actual error?  post here?

turn your firewall off for a while here....til testing finished.

can you ping the vpn server you are trying to connect to?
Try to ping by name first - in a terminal:
```
ping -w 3 your.vpn.server.name
```

A result like this:
===
user_id@host:~$ ping -w 3 vpn.your.com
PING vpn.your.com (111.333.0.333) 56(84) bytes of data.

--- vpn.your.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2008ms
===
,,,means that at least the name resolved properly to an IP address...  even if it did not respond to pings.

If you got something like this:
===
ping: unknown host vpn.your.com
===
...means either you are typing the wrong address (check typos), or name resolution is not working for you. 

If there are no errors in typing... then you have a couple of options (both require you finding out the VPN host IP address):
1.  place a line in your hosts file that links your vpn host name and its IP address.
2.  refer to the vpn host by its IP address in your VPN configuration.

Test by pinging the IP address...
```
ping -w 3 xxx.yyy.zzz
```

---

### Post by CHFFriday on 2007-11-26
Tact- thanks for your post! I will use this in the future.

Stvdel- Some bad news here (unless someone has a solution)! Looks like when you connect using Vista you are authenticating by using a Certificate.

See from your post:
check- use certification for authentication
check- verify the name and usage attributes of servers certificate

You can verify with your IT guy.
 
PPTP does not use a certificate. 

You may be able to Use KVPN but I have never been able to get this to work. I think it’s because of my router but that’s no concern here.

Tact, do you agree?

CHFFriday

---

### Post by stvdel on 2007-11-26
Hello Tact , I have attached the image of my screen when I try to connect. Also when I 
tried to ping -w 3 10.10.10.10 this is what it said.

PING 10.10.10.10 (10.10.10.10) 56(84)  bytes of data.
From 12.12.12.12 icmp_sec=1 Packet filtered

-----10.10.10.10 Ping Statistics-------
1 packets transmitted , 0 received , +1 errors , 100% packet loss , time 0ms

to the other reply, I will try to find out today about the certificate being needed.

---

### Post by tact on 2007-11-27
> **CHFFriday said:**
> Tact- thanks for your post! I will use this in the future.

Stvdel- Some bad news here (unless someone has a solution)! Looks like when you connect using Vista you are authenticating by using a Certificate.

See from your post:
check- use certification for authentication
check- verify the name and usage attributes of servers certificate

You can verify with your IT guy.
 
PPTP does not use a certificate. 

You may be able to Use KVPN but I have never been able to get this to work. I think it&#8217;s because of my router but that&#8217;s no concern here.

Tact, do you agree?

CHFFriday

Hey CHFFriday - cant really comment as I have zero experience with vista.  Certainly stvdel shows a config is checked  "use certificate".   That may just mean something like a publically available CA cert.    stvdel is going to check with his IT people whether any special cert is needed from them...

---

### Post by tact on 2007-11-27
> **stvdel said:**
> Hello Tact , I have attached the image of my screen when I try to connect. Also when I 
tried to ping -w 3 10.10.10.10 this is what it said.

PING 10.10.10.10 (10.10.10.10) 56(84)  bytes of data.
From 12.12.12.12 icmp_sec=1 Packet filtered

-----10.10.10.10 Ping Statistics-------
1 packets transmitted , 0 received , +1 errors , 100% packet loss , time 0ms

to the other reply, I will try to find out today about the certificate being needed.

Hey stvdel - are you sure your firewall is off?  The ICMP response should not be filtered if thats the case.

Try to ping the vpn server (by name first, then again by the IP address)....  but before doing so:
1.  disable your firewall
2.  verify the firewall is off by going to a terminal and issuing this command:
```
sudo iptables -L
```

You should get output like this (no defined rules):
```
user@host:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

```

If you get a heap more text than above then you have some rules defined and the firewall is not truly off (or left some rules defined when it was turned off).

To clear any and all rules from your iptables config, after firewall has been turned off, you can flush the tables (safe - rules will be put back in place when you next run your firewall)....
```
sudo iptables --flush
```

Now you can again check:
```
sudo iptables -L
```
No rules will be listed.

Now you can try to ping the vpn host by name and IP address.  post the results.

turn firewall back on again ...

---

### Post by stvdel on 2007-11-27
Ok I found out from the IT guys that their is no certificates and none is needed.

Also, I turned off the firewall and entered the commands and it showed just like 
you had in your post so I know the firewall is off. Although this time when I tried
to ping it gave me a different response

tried to ping -w 3 10.10.10.10 this is what it said.

PING 10.10.10.10 (10.10.10.10) 56(84) bytes of data.
From 12.12.12.12 icmp_seq3 Packet filtered

-----10.10.10.10 Ping Statistics-------
3 packets transmitted , 0 received , +1 errors , 100% packet loss , time 1999ms

Also you said ping by name first, what does this mean? I only know the ip address
so this is from pinging the ip address again.

---

### Post by CHFFriday on 2007-11-27
stvdel,
What I think tact wants to know is can you ping the IP address of the Gateway you used in the VPN setup?

When you use Firefox do the pages load or do you get allot of "pages can't load-time outs"? 

Other wise is your Internet connect up to par or is it slow?

 BTY, how do you connect to the Internet? 

CHFFriday

---

### Post by stvdel on 2007-11-27
Hello, yes, the ping information I posted above is when I try to ping the gateway address.
I am currently using a cable modem for my internet connection.

---

### Post by stvdel on 2007-11-27
One more thing though, I am in Asia my vpn server is in the US. when I connect to internet 
my internet has no problem but when I connect to the vpn through windows it is very slow
because of the distance it has to travel.

---

### Post by dnice6363 on 2007-11-27
The firewall that he is trying to connect through could not allow the ICMP request to come through as well.  In the terminal can you try to run the command

telnet (IP) 1723

if it connects you should get a black screen.  If not it sounds like somthing else is still blocking the connection.

---

### Post by tact on 2007-11-27
Hey stvdel

I am in asia too (Kuala Lumpur) and I travel all over asia connecting to my company's VPN server located in New Zealand.  No issues with the distance etc.  VPN connections are very slow no matter what.  (This is why its good to only route the essential traffic thru the VPN and do your regular surfing etc outside of it - thats set on the last page of the configs...)

You still have something blocking both vpn and ICMP activity.  If you have your own firewall turned off then thats good.  

Where the blockage is I can only guess.  Grasping at straws now:
- many internet providers (not just ISP, but also hotels, shared offices, and even many office routers) are not capable of passing thru VPN connections.  So even though you have disabled your firewall you may be still blocked.

You mention being able to connect to the company VPN server when using Vista - correct?   Is that from the same location you are trying to connect via ubuntu?   

Can you test, from the same location, same connection, everything the same - can connect when booted to Vista but cannot connect when booted into ubuntu?

---

### Post by stvdel on 2007-11-28
Hello, first I tried the telnet 10.10.10.10 1723 
it said trying 10.10.10.10
connected to 10.10.10.10
escape character is '^' or something like that.
I didnt get a black screen or anything like that, it just says that in the terminal if I 
followed the command right.
I am in the same place, I have a dual boot config with vista and I can connect with
vista but not ubuntu. I talked with the isp today and told them I was having trouble
connecting to my vpn and if they had any restrictions from me connecting in which
they said no.

---

### Post by tact on 2007-11-28
Ok... 
- you managed to get a "connected" from telnet session under ubuntu.
- you can connect the VPN under Vista but not under ubuntu, all other things unchanged.

That eliminates thoughts about being blocked.

It has to then come back to the ubuntu VPN settings.  Perhaps the VPN server you are connecting to is set up differently from mine and requires different settings...  (example maybe your's does not need the "enable stateful MPPE" setting turned on.)

So how to figure it out...  ?
- Hit & Miss method - change one setting at a time and try to connect....

- More analysis from the Vista side - I guess there are ways to get information about the VPN connection in Vista (sorry I am not familiar so do not know whats there), a log or status thing that will tell you what kind of connection and what protocol was used to make the link, etc...
I mean something that reports the actual connection params when a VPN connection is made under Vista - something more than the config pages you have posted already.

Cant really help further with either of the above methods.  I am out of cards now.

---

### Post by stvdel on 2007-11-28
I have tried many different configs and trying to connect and nothing. Here is the latest one I tried and I will attach the latest log file from where I tried to connect and it came up an error maybe this log file
someone knows how to read and tell me what is wrong.

---

### Post by dnice6363 on 2007-11-28
I was able to look through the logs and see that the connection state appears to initiate so thats not the problem.  I was able to see there was an issue with the Synchronous PPTP option not being active.  Unfortinitly Im at work and can drill into the settings to see what this is referring to but I will search the Internet to see if I can find anything.  

Here is the errors that I was able to pull from the Log.

Nov 28 17:33:36 hg-n-frg-laptop pptp[7206]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 

Nov 28 17:33:47 hg-n-frg-laptop NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'. 

Nov 28 17:33:47 hg-n-frg-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5. 

Nov 28 17:33:47 hg-n-frg-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6. 

Nov 28 17:33:47 hg-n-frg-laptop NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'East Asia' because service was 6.

---

### Post by CHFFriday on 2007-11-28
stvdel,
OK 

This may seam strange but here goes.

1. Gusty has had lots of problems with IPV6 Sooooo disable it. I don't have the link so do a search on the Form and you will find it. 

2. After you disable IPV6 go to the VPN configuation and DELETE your current to Work VPN connection. Then reboot the PC. Then go back to the VPN configuration setup and build a NEW connection using the default stuff. You need to put your in user name,password and Gateway.etc.

3. DO NOT TRY TO CONNECT.

4. Goto System-> Administration->Network.  After it opens click on the DNS Tab And DELETE the DNS server(s) in the DNS Servers box. Close the Network Settings applet. DO NOT browse the Internet!!! 

5. KNOW try to connect using the NEW VPN connection you made in step 2. Do this as quickly as you can!

Let use know what happens.

CHFFriday

---

### Post by dnice6363 on 2007-11-28
I was able to see that the primary connection is established. 

Lets try to change some settings to see if this solves this issue. 

1.Uncheck the option Only use VPN connection for these addresses under the routing tab.  This is only needed for Split tunneling and not what we are using here.  

If this still down not allow you to connect leave the settings as is.  

2. Try to change the Encryption options to just require MPPE encryption.  It seems like one of the settings is off.    If still no luck I would try to change some of Auth options.  Maybe try to uncheck refuse EAP and check off refuse Chap or maybe try to check them all off.  I would look at the advanced properties in Vista to if this could lead to any conclusions or which settings are needed to establish the connections.  If still does not work place the log file on the Forum so we can compare to see if any errors changed or if there is a bigger underlaying problem.  

Cheers.

---

### Post by tact on 2007-11-29
> **stvdel said:**
> I have tried many different configs and trying to connect and nothing. Here is the latest one I tried and I will attach the latest log file from where I tried to connect and it came up an error maybe this log file
someone knows how to read and tell me what is wrong.

Hi stvdel,

From looking at your log I see you have some settings different to mine. (Not the same as those pics I posted).

You have ticked the boxes "Allow deflate compression" and "allow BSD compression".   
Perhaps you should uncheck them.

Your MRU and MTU are set to 1500.  Mine are 1416.  Not sure it makes a difference but no harm trying setting things identical to my setup since it works and give it a try.

Your log of a failed connection compared to my log of a successful connection are identical up to this line in your file....
*Nov 28 17:33:36 hg-n-frg-laptop NetworkManager: <info>  VPN Activation (East Asia) Stage 3 of 4 (Connect) complete, waiting for IP configuration... *

I have the same line but after that I have these lines (missing from your log):
[I]Nov 29 22:44:13 m-neilm-lt pppd[12314]: Plugin nm-pppd-plugin.so loaded.
Nov 29 22:44:13 m-neilm-lt pppd[12314]: nm-pppd-plugin: plugin initialized.
Nov 29 22:44:13 m-neilm-lt kernel: [47838.064000] PPP generic driver version 2.4.2
Nov 29 22:44:13 m-neilm-lt nss_wins[12324]: pppd 2.4.4 started by root, uid 0
Nov 29 22:44:14 m-neilm-lt nss_wins[12324]: Using interface ppp0
Nov 29 22:44:14 m-neilm-lt nss_wins[12324]: Connect: ppp0 <--> /dev/pts/0[/I]

So it seems your networkmanager plug in for PPP is not loading?  I have no idea what that means.  :)

We both have the line:
*Nov 29 22:44:14 m-neilm-lt pptp[12326]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated *

So I suspect that its no problem that synchronous pptp is not activated... ignore that.

---

### Post by Tmanisaur on 2007-11-30
Cheers all, and bump for this thread.

I'm having the same problem of not being able to create any VPN connection with Ubuntu 7.10.  I've been reading this, and other, threads and have installed the packages that everyone suggests.

I've installed Ubuntu 7.10 on a Compaq Presario v6000-series laptop.  I am ONE INCH away from throwing windows out of my workflow, but it is JUST out of reach because of this one issue.

I have installed network-manager-pptp, and have configured the VPN connection as described here: [http://tipotheday.com/2007/11/28/connect-to-windows-vpn-server-pptp-with-ubuntu-gutsy/](http://tipotheday.com/2007/11/28/connect-to-windows-vpn-server-pptp-with-ubuntu-gutsy/) 

I did notice that I was not prompted for the windows domain either in creating/editing the VPN connection or when prompted for my credentials when initiating the connection.

The device I am connecting to is a SNAPGEAR SG565 employed as a stable PPTP server.  I should add that I am admin for both ends of the connection (yippee!).

ANY help would help!! and many thanks in advance.

Here is my sudo tail -f /var/log/syslog

[PHP]Nov 30 17:02:44 helios NetworkManager: <info>  Will activate VPN connection 'XXXXXX', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'trevor', vpn_data 'ppp-connection-type / pptp / pptp-remote / thec3igroup.dynalias.org / usepeerdns / yes / encrypt-mppe / no / encrypt-mppe-128 / yes / encrypt-mppe-stateful / yes / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / yes / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / no / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''. 
Nov 30 17:02:44 helios NetworkManager: <info>  VPN Activation (XXXXXX) Stage 1 of 4 (Connection Prepare) scheduled... 
Nov 30 17:02:44 helios NetworkManager: <info>  VPN Activation (XXXXXX) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 7067) 
Nov 30 17:02:44 helios NetworkManager: <info>  VPN Activation (XXXXXX) Stage 1 of 4 (Connection Prepare) complete. 
Nov 30 17:02:44 helios NetworkManager: <info>  VPN Activation (XXXXXX) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Nov 30 17:02:44 helios NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6. 
Nov 30 17:02:44 helios NetworkManager: <info>  VPN Activation (XXXXXX) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Nov 30 17:02:44 helios NetworkManager: <info>  VPN Activation (XXXXXX) Stage 2 of 4 (Connection Prepare Wait) complete. 
Nov 30 17:02:44 helios NetworkManager: <info>  VPN Activation (XXXXXX) Stage 3 of 4 (Connect) scheduled... 
Nov 30 17:02:44 helios NetworkManager: <info>  VPN Activation (XXXXXX) Stage 3 of 4 (Connect) sending connect request. 
Nov 30 17:02:44 helios NetworkManager: <info>  VPN Activation (XXXXXX) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Nov 30 17:02:44 helios NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 
Nov 30 17:02:48 helios NetworkManager: <info>  VPN Activation (XXXXXX) Stage 3 of 4 (Connect) reply received. 
Nov 30 17:02:48 helios NetworkManager: <info>  VPN Activation (XXXXXX) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Nov 30 17:02:48 helios NetworkManager: <info>  VPN Activation (XXXXXX) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Nov 30 17:02:48 helios pppd[7068]: Plugin nm-pppd-plugin.so loaded.
Nov 30 17:02:48 helios pppd[7068]: nm-pppd-plugin: plugin initialized.
Nov 30 17:02:48 helios pppd[7072]: pppd 2.4.4 started by root, uid 0
Nov 30 17:02:48 helios pppd[7072]: Using interface ppp0
Nov 30 17:02:48 helios pppd[7072]: Connect: ppp0 <--> /dev/pts/1
Nov 30 17:02:48 helios pptp[7075]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Nov 30 17:02:48 helios pptp[7077]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Nov 30 17:02:48 helios pptp[7077]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Nov 30 17:02:48 helios pptp[7077]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Nov 30 17:02:49 helios pppd[7072]: nm-pppd-plugin: CHAP check hook.
Nov 30 17:02:49 helios pptp[7077]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Nov 30 17:02:49 helios pptp[7077]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Nov 30 17:02:49 helios pptp[7077]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 64230). 
Nov 30 17:02:49 helios pppd[7072]: nm-pppd-plugin: CHAP credentials requested.
Nov 30 17:02:50 helios pppd[7072]: MS-CHAP authentication failed: I don't like you.  Go 'way.
Nov 30 17:02:50 helios pppd[7072]: CHAP authentication failed
Nov 30 17:02:50 helios pppd[7072]: Connection terminated.
Nov 30 17:02:50 helios pptp[7077]: anon log[pptp_read_some:pptp_ctrl.c:543]: read returned zero, peer has closed
Nov 30 17:02:50 helios pptp[7077]: anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
Nov 30 17:02:50 helios pptp[7077]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Nov 30 17:02:50 helios pptp[7077]: anon log[pptp_read_some:pptp_ctrl.c:543]: read returned zero, peer has closed
Nov 30 17:02:50 helios pptp[7077]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Nov 30 17:02:50 helios pppd[7072]: Exit.
Nov 30 17:02:59 helios NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'. 
Nov 30 17:02:59 helios NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5. 
Nov 30 17:02:59 helios NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6. 
Nov 30 17:02:59 helios NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'XXXXXX' because service was 6. [/PHP]

Cheers,
T.

---

### Post by makmiler on 2008-01-24
Listen guys,

I will tell you something from my experience with Suse and Ubuntu about using the GUI's for connecting with a Microsoft VPN Server. The answer is, they suck! Sorry, but that's the truth. For all other protocols like OpenVpn, they work beautifully. 

I'm using 2 VPN-Servers now with Suse and Ubuntu without any problems, which I had by trying to setup these GUI's.

So, instead I propose to you all to use the direct pptp without any GUI's.

First you have to set the options for the connection under** /etc/ppp**. There is a file called "**options**". You have to put all the necessary options there, like the require-mppe or 128bit encryption, or use/not use deflate, bsd, etc.. I mean everything. You can find many links on the internet, which options are available. If you are not using a modem to connect to your VPN (like in many cases) you have to comment out the line "modem" and uncomment the line "local". This is very important.

When you are done setting up the "**options**" file, you have to set up the** chap-secrets** file.

You should put there your username and password for connecting with your VPN Server. 
The format is as follows:
```

username     *       password      *
```

Separate the fields with TAB.

Now you are done setting everything up.

The next thing to do is connect to internet as usual, and in the terminal type this:

```
sudo pptp yours.vpn.server.address name username &
```

Do not confuse the word name there. It should stay. You should just replace the "yours.vpn.server.address" with the VPN Server address, and instead of username, use the username you put in the chap-secrets file.

Its better if you start the command with & at the end so it'll stay in background. This should lead you to a successful connect with the vpn server. If something is wrong, then you have a problem in your options file. Try to solve it.

If you connected successfully, type this: 
```
sudo route add default ppp0
```

and Voila! you have VPN connection. Good luck


R.M.

---

