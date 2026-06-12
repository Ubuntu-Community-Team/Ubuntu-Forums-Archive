---
title: "internet connection disconnecting and reconnecting on its own"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by famouscoco on 2007-11-29
My system specs:
intel d101 motherboard
adsl connection through huawei sterlite modem
2 gb ram
intel 3 ghz processor
My problem:
my internet connection disconnects and reconnects on its own,which i know from the system log.i am pasting that at the end of this thread.as a result,i can surf pages in the web for 3 to 4 minutes,then the connection resets,which takes about 1 to 1.5 minutes,and i can not access any page during that time.if i was in the middle of downloading some package through synaptic,it also has to be cancelled,and resumed.(luckily,ubuntu keeps the half-downloaded file and restores the download later when i start)
i have Wind*ws *p installed on pc where the connection works fine.
i hope someone here can point me to a solution.
Solutions I tried:
disabling IPv6 (problem persists)
changing dns (problem persists)
Extra details:
My broadband service provider gives "dynamic IP" connection,so i get a new IP each time the connection reconnects.can this be a prob? i think noy because i know friends who have same net connection and are running net in ubuntu fine.the provider provides 2 mbps connectin,though while downloading i get maximum 30 to 32 kbps (27 kbps is most common)
THE SYSTEM LOG (I deleted the IP addresses from there,for security purposes :mad: )
Nov 29 15:42:49 stuntman-desktop pppd[4372]: Using interface ppp0
Nov 29 15:42:49 stuntman-desktop pppd[4372]: Connect: ppp0 <--> eth0
Nov 29 15:42:50 stuntman-desktop pppd[4372]: CHAP authentication succeeded: Authentication success,Welcome!
Nov 29 15:42:50 stuntman-desktop pppd[4372]: CHAP authentication succeeded
Nov 29 15:42:50 stuntman-desktop pppd[4372]: peer from calling number 00:E0:FC:4D:2E:BF authorized
Nov 29 15:42:50 stuntman-desktop pppd[4372]: replacing old default route to eth0 [192.168.1.1]
Nov 29 15:42:50 stuntman-desktop pppd[4372]: local  IP address 
Nov 29 15:42:50 stuntman-desktop pppd[4372]: remote IP address 
Nov 29 15:42:50 stuntman-desktop pppd[4372]: primary   DNS address 218.248.240.208
Nov 29 15:42:50 stuntman-desktop pppd[4372]: secondary DNS address 218.248.240.135
Nov 29 15:43:05 stuntman-desktop pppd[6137]: No response to 4 echo-requests
Nov 29 15:43:05 stuntman-desktop pppd[6137]: Serial link appears to be disconnected.
Nov 29 15:43:05 stuntman-desktop pppd[6137]: Connect time 3.0 minutes.
Nov 29 15:43:05 stuntman-desktop pppd[6137]: Sent 5856 bytes, received 26892 bytes.
Nov 29 15:43:05 stuntman-desktop pppd[6137]: restoring old default route to eth0 [192.168.1.1]
Nov 29 15:43:11 stuntman-desktop pppd[6137]: Connection terminated.
Nov 29 15:43:11 stuntman-desktop pppd[6137]: Modem hangup
Nov 29 15:43:47 stuntman-desktop pppd[6137]: PPP session is 8952
Nov 29 15:43:47 stuntman-desktop pppd[6137]: Using interface ppp1
Nov 29 15:43:47 stuntman-desktop pppd[6137]: Connect: ppp1 <--> eth0
Nov 29 15:43:47 stuntman-desktop pppd[6137]: CHAP authentication succeeded: Authentication success,Welcome!
Nov 29 15:43:47 stuntman-desktop pppd[6137]: CHAP authentication succeeded
Nov 29 15:43:47 stuntman-desktop pppd[6137]: peer from calling number 00:E0:FC:4D:2E:BF authorized
Nov 29 15:43:47 stuntman-desktop pppd[6137]: replacing old default route to eth0 [192.168.1.1]
Nov 29 15:43:47 stuntman-desktop pppd[6137]: local  IP address 
Nov 29 15:43:47 stuntman-desktop pppd[6137]: remote IP address 
Nov 29 15:43:47 stuntman-desktop pppd[6137]: primary   DNS address 218.248.240.208
Nov 29 15:43:47 stuntman-desktop pppd[6137]: secondary DNS address 218.248.240.135
Nov 29 15:45:10 stuntman-desktop pppd[6860]: No response to 4 echo-requests
Nov 29 15:45:10 stuntman-desktop pppd[6860]: Serial link appears to be disconnected.
Nov 29 15:45:10 stuntman-desktop pppd[6860]: Connect time 4.5 minutes.
Nov 29 15:45:10 stuntman-desktop pppd[6860]: Sent 32958 bytes, received 375666 bytes.
Nov 29 15:45:16 stuntman-desktop pppd[6860]: Connection terminated.
Nov 29 15:45:17 stuntman-desktop pppd[6860]: Modem hangup
Nov 29 15:45:49 stuntman-desktop pppd[4372]: No response to 4 echo-requests
Nov 29 15:45:49 stuntman-desktop pppd[4372]: Serial link appears to be disconnected.
Nov 29 15:45:49 stuntman-desktop pppd[4372]: Connect time 3.0 minutes.
Nov 29 15:45:49 stuntman-desktop pppd[4372]: Sent 2527 bytes, received 156 bytes.
Nov 29 15:45:49 stuntman-desktop pppd[4372]: restoring old default route to eth0 [192.168.1.1]
Nov 29 15:45:52 stuntman-desktop pppd[6860]: PPP session is 7077
Nov 29 15:45:52 stuntman-desktop pppd[6860]: Using interface ppp2
Nov 29 15:45:52 stuntman-desktop pppd[6860]: Connect: ppp2 <--> eth0
Nov 29 15:45:52 stuntman-desktop pppd[6860]: CHAP authentication succeeded: Authentication success,Welcome!
Nov 29 15:45:52 stuntman-desktop pppd[6860]: CHAP authentication succeeded
Nov 29 15:45:52 stuntman-desktop pppd[6860]: peer from calling number 00:E0:FC:4D:2E:BF authorized
Nov 29 15:45:52 stuntman-desktop pppd[6860]: replacing old default route to eth0 [192.168.1.1]
Nov 29 15:45:52 stuntman-desktop pppd[6860]: local  IP address 
Nov 29 15:45:52 stuntman-desktop pppd[6860]: remote IP address 
Nov 29 15:45:52 stuntman-desktop pppd[6860]: primary   DNS address 218.248.240.208
Nov 29 15:45:52 stuntman-desktop pppd[6860]: secondary DNS address 218.248.240.135
Nov 29 15:45:56 stuntman-desktop pppd[4372]: Connection terminated.
Nov 29 15:45:56 stuntman-desktop pppd[4372]: Modem hangup
Nov 29 15:46:31 stuntman-desktop pppd[4372]: PPP session is 4022
Nov 29 15:46:31 stuntman-desktop pppd[4372]: Using interface ppp0
Nov 29 15:46:31 stuntman-desktop pppd[4372]: Connect: ppp0 <--> eth0
Nov 29 15:46:31 stuntman-desktop pppd[4372]: CHAP authentication succeeded: Authentication success,Welcome!
Nov 29 15:46:31 stuntman-desktop pppd[4372]: CHAP authentication succeeded
Nov 29 15:46:31 stuntman-desktop pppd[4372]: peer from calling number 00:E0:FC:4D:2E:BF authorized

Please help people,i am totally in LOVE with ubuntu,only this slight nag keeps me from quitting that crappy OS i used before...

---

### Post by ilanesh on 2008-04-19
this is a waste of time to post in this forum, you never will receive rsponse here,
I also have constantly wireless disconnections in ubuntu, this is not good when they dont fix this.
I use Linux Mint, this is the best distro, and no disconnections from wireless, eventhought it is based on ubuntu 7.10, so how this can be?
well I actually use now ubuntu studio who works better then the only ubuntu, but still the same disconncetions, why?
on linux mint and windows xp I stay online, butn not with ubuntu or ubuntu studio.
strange.

windows and linux mint both of them runs best and out of the box.

---

