---
title: "Solution for bypassing VPN for certain URLs"
date: 2017-12-04
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2017-12-04
I did a little work over the weekend on this and came up with a solution to bypass routing through a VPN to your local gateway. I did this because some websites have IPs from VPNs blocked, such as Netflix, my ISP's smtp server and Realtor.
First the bash script. I tried using an array for the URLs, but I was not getting the results expected. When going from one URL to the next, it would return two merged IP addresses. I found doing an if statement works. The sleep statement is because it would have a connection timed out error in syslog even though I put in the service file After=network-online.target.
```
#!/bin/bash
#Bypass VPN
sleep 10
GATEWAY="192.168.1.1"
for x in 1 2 3 4
do
   if [ "$x" -eq 1 ]
   then
	URL=smtp.isp.net
   elif [ "$x" -eq 2 ]
   then 
	URL=netflix.com
   elif [ "$x" -eq 3 ]
   then
	URL=realtor.com
   else
	URL=financeplace.com 
   fi
#the URLs above are a mix of real and made up URLs
#using dig to get all of the addresses for a URL. Netflix has many
#I found the following code on a website, but do not remember where. Had to make some modifications for it to run as a BASH script.Credit to whoever wrote this
   IP_LIST=()
   ip=`dig +short $URL`
   IP_LIST+="$ip"
   for ips in ${IP_LIST[@]}
     do
     ips=(`echo $ips | tr " " "\n"`)
     for ip in $ips
       do
         ip route add $ip via $GATEWAY
       done
     done
done
```
Make sure you make the file executable(chmod +x). I put mine in /bin
I then created a service named bpvpn.service. I put this in the /etc/systemd/system folder
```
[Unit]
Description=Bbypass VPN
After=network-online.target
Requires=network-online.target

[Service]
ExecStart=/bin/bpvpn.sh

[Install]
WantedBy=multi-user.target
```
Enable to run at boot```
sudo systemctl enable bpvpn
```
That's it.

---

