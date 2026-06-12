---
title: "Internet Connection Very Slow After Adding Wireless Router"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by infidel on 2006-12-30
Hello, everyone. I have cable internet through Comcast and just added a Linksys Wireless-G broadband router to the mix. Where my Edgy box once plugged directly into the cable modem, it now plugs into one of the wired jacks in the router (there's a Windows machine elsewhere in the house using the wireless connection). 

Everything works following a reset of the cable modem and a reboot of the Edgy box, but my internet connection is now almost unspeakably slow. Like dialup-slow. 

Is there something I should have actively done in terms of configuration? As it is, I didn't have to do anything but plug in the cables and reset the modem. Is there anything "under the hood" that I need to look after?

Any guidance would be greatly appreciated. Thanks very much in advance.

---

### Post by infidel on 2006-12-30
Oops. Never mind. A *second* reboot (not sure why it took two...) appears to have made my connection as fast as it ever was.

Sorry to have wasted everyone's time. Thanks anyway.

---

### Post by jasciu on 2007-01-11
I have a comcast cable modem providing an internet connection to a Netgear WGT624 wireless router. The router directs a lan cable from it to the desktop computer and generates a wireless signal to rest of the house for the wireless laptops. 

The problem was that internet speeds slowed down considerably when using automatically detect ip and dns settings in the computer and router. The solution is to specify the computer ip settings and dns setting in the computer and router. 

1) Go into Internet Explorer... Options...Connections....LAN....unclick automatically detect setttings

2) Make sure your general browser security setting Phishing, tool bar ad-block and virus protection programs are not holding up particular sites.

3) Go into your control panel....click local area connections...General....click Internet Protocol (TCP/IP) and make sure Obtain an IP address automatically is enabled and Obtain DNS server automatically is disabled. Use the following list to plug in the particular DNS server your ISP uses. Plug it into the primary and secondary slots 

3) Find out which DNS servers that your ISP uses to resolve web addresses in this list:

Australia

QLD
144.140.70.29
144.140.71.15
144.140.70.16

Westnet (ADSL)
203.21.20.20
203.10.1.9


--------------------------------------------------------------------------------

Canada

Shaw Cable
64.59.144.16
64.59.144.17

Telus(BC)
154.11.128.129
154.11.128.150
154.11.128.1
154.11.128.2
154.11.128.130
209.53.4.150


--------------------------------------------------------------------------------

China

I-Cable 
(Hong Kong)
210.80.60.1
210.80.60.2


--------------------------------------------------------------------------------

Italy

Alice 
212.216.112.112
212.216.172.62


--------------------------------------------------------------------------------

Malaysia

Schoolnet (ADSL)
202.75.44.18
203.106.3.171
202.75.44.20 

Tmnet Streamyx (ADSL)
202.188.0.132
202.188.0.133 
202.188.0.147
202.188.0.161
202.188.0.181
202.188.0.182
202.188.1.4
202.188.1.5
202.188.1.23
202.188.1.25


--------------------------------------------------------------------------------

Mexico

Cablemas (Cable 128kbps)
69.44.143.245 
200.79.192.3 


--------------------------------------------------------------------------------

Nederland
Hetnet
10.0.0.5
10.0.0.2
10.0.0.3 

Planet Internet
195.121.1.34
195.121.1.66


--------------------------------------------------------------------------------

New Zealand

Xtra (DSL)
202.27.158.40
202.27.156.72

Paradise (DSL)
203.96.152.4
203.96.152.12


--------------------------------------------------------------------------------

Portugal

Netvisão (Cable) 
213.228.128.6
213.228.128.5

TVTel
195.22.0.204 
195.22.0.205


--------------------------------------------------------------------------------

Sweden

Tele2
130.244.127.161
130.244.127.169 


--------------------------------------------------------------------------------

United Kingdom

AOL
205.188.146.145

Blueyonder/Telewest (Cable)
193.38.113.3
194.177.157.4

BTInternet
194.73.73.172
194.73.73.173
194.72.9.44
194.72.9.38 (Cardiff, S.Wales)
194.72.9.39 (Cardiff, S.Wales)

Bulldog Broadband
Ns3.bulldogdsl.com . 83.146.21.5 (South)
Ns4.bulldogdsl.com . 83.146.21.6 (South)
Ns5.bulldogdsl.com . 212.158.248.5 (North)
Ns6.bulldogdsl.com . 212.158.248.6 (North)

Nildram (ADSL)
213.208.106.212
213.208.106.213 

NTL (Cable) and Virgin.net (ADSL)
194.168.4.100
194.168.8.100

Pipex (ADSL)
62.241.162.35 
62.189.34.83

Silvermead (Satellite, DSL, ISDN)
62.55.96.226
62.55.96.109 (unchecked)

Telewest (Cable)
62.31.176.39
194.117.134.19

Tiscali, Screaming.net, Worldonline, Lineone
212.74.112.66
212.74.112.67
212.74.114.129 (Cambridge)
212.74.114.193 (Cambridge)

Wanadoo UK (ADSL)
195.92.195.94
195.92.195.95

Zen Internet
Primary DNS: 212.23.8.1
Secondary DNS: 212.23.3.1


--------------------------------------------------------------------------------

United States of America

Adelphia
67.21.13.4 Los Angeles, CA
67.21.13.2 Los Angeles, CA
24.48.217.226 Santa Monica, CA
24.48.217.227 Santa Monica, CA
68.168.1.42 Florida
68.168.1.46 Florida 

Bellsouth Fast access DSL:
Georgia
205.152.37.23
205.152.37.24
205.152.37.25
205.152.144.24
205.152.144.25

Charter Comms (Cable)
68.116.46.70

Comcast (pick the nearest!)
68.87.66.196 Comcast (national) Primary DNS Server.
68.87.64.196 Comcast Secondary DNS Server.
68.57.32.5 (Virginia)
68.57.32.6 (Virginia)
216.148.227.68 (Denver, Colorado)
204.127.202.4 (Denver, Colorado)
68.42.244.5 (Taylor, Michigan)
68.42.244.6 (Taylor, Michigan)
68.62.160.5 (Huntsville, Alabama)
68.62.160.6 (Huntsville, Alabama)
68.87.96.3 (Pennsylvania)
68.87.96.4 (Pennsylvania)

Cox HSI (Cable)
68.12.16.25 (Oklahoma - Primary)
68.12.16.30 (Oklahoma - Secondary)
68.2.16.30 (Oklahoma - Tertiary)

Cox.net
68.10.16.25
68.10.16.30
68.9.16.30

Earthlink - seem to be shared by Cable and DSL users in several states. Georgia and Florida confirmed.
207.69.188.187
207.69.188.186
207.69.188.185
209.86.63.217 (Cable) - Charlotte, NC 

Harrisonville Telephone Company (HTC)
216.114.114.130 (Illinois)
216.114.114.132 (Illinois)

Horry Telephone Coop
66.153.128.98 (Horry County, South Carolina)
66.153.162.98 (Horry County, South Carolina) 

ORSC Public Access DNS Nameservers (Anyone can use these, no matter what ISP)
199.166.24.253
199.166.27.253
199.166.28.10
199.166.29.3
199.166.31.3
195.117.6.25
204.57.55.100

Roadrunner (Cable)
24.25.195.1 (San Diego, CA)
24.25.195.2 (San Diego, CA)
24.25.195.3 (San Diego, CA)

SBC Yahoo DSL
206.13.31.13
206.13.28.60
206.13.31.5
206.13.28.31 

Speakeasy (pick any two!)
66.93.87.2 (Washington state and Oregon)
216.231.41.2 (Washington DC - probably)
216.254.95.2 (NY, Massachusetts and Pennsylvania)
64.81.45.2 (Los Angeles, California)
64.81.111.2 (Denver, Colorado)
64.81.127.2 (Dallas, Texas)
64.81.79.2 (Sacramento, California)
64.81.159.2 (Baltimore and Washington DC)
66.92.64.2 (Boston, Massachusetts)
66.92.224.2 (Philadelphia)
66.92.159.2 (Washington DC)
216.27.175.2 (Atlanta, Georgia. Serves Florida too)

Sprintlink (nationwide)
204.117.214.10
199.2.252.10
204.97.212.10

TimeWarner
24.93.1.119 (Rochester, NY)

Unicom 
216.104.64.5 (Grants Pass, OR)
216.104.72.5 (Portland, OR)

FrontierNet / Citlink / New North DNS addresses:
66.133.170.2 (Rochester, NY)
170.215.255.114 (Rochester, NY)
216.67.192.3 (Arizona)
207.173.225.3 (Arizona)
207.173.225.3 (California)
216.67.192.3 (California)
170.215.255.114 (New York (areas other than Rochester))
66.133.170.2 (New York (areas other than Rochester))
170.215.184.3 (West Virginia)
170.215.126.3 (West Virginia)
170.215.126.3 (Tennessee, Georgia)
170.215.184.3 (Tennessee, Georgia)
67.50.135.146 (Illinois)
66.133.191.35 (Illinois)
66.133.191.35 (Wisconsin, Minnesota, Iowa, North Dakota and Nebraska)
170.215.255.114 (Wisconsin, Minnesota, Iowa, North Dakota and Nebraska)

Verizon (Level3) - these are not restricted to Verizon customers
4.2.2.1
4.2.2.2
4.2.2.3
4.2.2.4
4.2.2.5
4.2.2.6 

Wave Broadband
24.113.32.29
24.113.32.30

4) Go into the setup program (sometimes over the internet via login) of your wireless router manufacturer

5) Choose to use a static IP address rather than a dynamic address in the setup program (Netgear sees your address and has the information greyed out in the disabled option). If your router setup doesn't have this information greyed out, use the dos prompt and type the command ipconfig

6) Plug in your primary and secondary DNS server rather than Get automatically from ISP. 

My computer wired computers and wireless computers are now blazingly fast.

---

### Post by spd106 on 2007-01-11
That's a very nice list you have there, can I ask where you found it?

I'll definitely have to bookmark it.

---

### Post by quincywalltech on 2007-10-19
That list is inaccurate notice the 10.0.0 .x private class ips!

Um I think its better to check [http://DNSServerList.org]("http://DNSServerList.org") for a more uptodate list. And use the tool to find a server closer to you.

QW

---

