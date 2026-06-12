---
title: "Unable to access tplink router configuration page 192.168.0.1"
date: 2021-07-04
forum: Networking &amp; Wireless
---

### Post by hebbal12732 on 2021-07-04
Hi, I have a strange issue. I cannot access my routers configuration webpage. My computer IP address is 192.168.0.174. I have checked the following

1. Internet access --> works
2. Access router page from Windows 10 --> works
3. Ping --> works
4. Access from andriod phone --> works
5. Tried 3 different browsers, Firefox, Edge, Chrome --> None of them work.

I get the error "This site can’t be reached. 192.168.0.1 took too long to respond." When I try [https://192.168.0.1/](https://192.168.0.1/) I get this error. "This site can’t be reached192.168.0.1 refused to connect."

This has got something to do with Ubuntu 20.04 and http. Not sure where. Please help

---

### Post by CharlesA on 2021-07-04
Have you tried connecting over regular http? I've seen some routers that don't support HTTPS out of the box.

If ping is working, but you are unable to access the web GUI, you can try running curl from a terminal and see if you get a response or not.

See here:
[https://unix.stackexchange.com/a/84820](https://unix.stackexchange.com/a/84820)

---

### Post by hebbal12732 on 2021-07-04
The tplink router supports only http. Even in Windows https does not work. http should have worked but... Tried with curl as well. Same issue. Is it because I have setup DNS in my router? I am using Open DNS server IPs. 208.67.222.222 · 208.67.220.220. It works on Windows. Why not Ubuntu? I have dual boot desktop that has Windows 10 & Ubuntu 20.04. When I login to windows my desktop ip is the same as mentioned above. This is something specific to Ubuntu or the browser settings

---

### Post by CharlesA on 2021-07-04
> **hebbal12732 said:**
> The tplink router supports only http. Even in Windows https does not work. http should have worked but... Tried with curl as well. Same issue. Is it because I have setup DNS in my router? I am using Open DNS server IPs. 208.67.222.222 · 208.67.220.220. It works on Windows. Why not Ubuntu? I have dual boot desktop that has Windows 10 & Ubuntu 20.04. When I login to windows my desktop ip is the same as mentioned above. This is something specific to Ubuntu or the browser settings

What message did you get when you tried curl? Can you post the output of the terminal?

You can select it with the mouse and then right click to copy IIRC.

---

### Post by hebbal12732 on 2021-07-04
There is no response. Its stuck. See attachments

---

### Post by CharlesA on 2021-07-04
You missed a /.

```
curl -Is http://192.168.0.1
```

---

### Post by hebbal12732 on 2021-07-04
Nope. Didnt worl. Something is blocking it. Firewall? All settings are default and my network type is set to home.

---

### Post by CharlesA on 2021-07-04
Take the | head -n 1 out and see if it is returning any errors. If it is not, try running this command and see what it shows:

```
traceroute 192.168.0.1
```

---

### Post by The Cog on 2021-07-04
It could be that the router is acception connections but can't process them for some reason (hence the browser is jsut hanging).
Try this to see if it's even accepting TCP connections:
```
nc -vz 192.168.0.1 80
```

I know it sounds trite, but have you tried turning it off and on again?

---

### Post by hebbal12732 on 2021-07-04
curl and nc commands no response. traceroute successful. See attached screenshot. 
Something is blocking the message from reaching the router. https reaches the router, but since it does not support https I get the connection refused error
BTW I did reboot the router multiple times. The fact that windows can connect tells me its something to do with Ubuntu only

---

### Post by CharlesA on 2021-07-04
> **hebbal12732 said:**
> curl and nc commands no response. traceroute successful. See attached screenshot. 
Something is blocking the message from reaching the router. https reaches the router, but since it does not support https I get the connection refused error
BTW I did reboot the router multiple times. The fact that windows can connect tells me its something to do with Ubuntu only

Any logs on the router?

The OS you are connecting from shouldn't affect connectivity.

If you want to try the 'nuke it from orbit' approach, install nmap and do a port scan against the router's IP and see what it returns:

```
sudo nmap -T4 -A -v 192.168.0.1
```

---

### Post by The Cog on 2021-07-04
Another thing I might try, to find out what's going on is to run tcpdump to see exactly what's happening on the interface.
Use this command to see which interface: 
```
ip route get 192.168.0.1
```
Then use that interface in this command:
```
sudo tcpdump -nntp -i <interface> host 192.168.0.1
```
Then use these two commands in a different terminal to generate traffic:
```
ping -c3 192.168.0.1
nc -vz 192.168.0.1 80
```
And post the output from tcpdump.
At the moment, I'm thinking maybe the TCP is not leaving your PC for some reason, but it could be something else. That trace should eliminate a number of odd possibilities.

P.S. Do you have any firewall running on your PC? Try this command, which prints all the iptables rules that are in force:
```
sudo iptables-save
```

---

### Post by Dennis N on 2021-07-04
Start Firefox.
Type 192.168.0.1 in the address bar.
Press Enter and Firefox will connect to the router's login webpage.
This works on my TP-Link Router.

---

### Post by hebbal12732 on 2021-07-04
Found it !!!!. Its all the fault of the tplink router :evil:. Looks like its a bug on part of the router software.

 It blocks access to the configuration page if the mac id is in the parental controls, regardless of whether the time is when internet is allowed. This explains why I had internet access but could not access the routers login page. In my opinion it should have allowed access regardless of whether internet is allowed or not. When its time to block, it should block only internet access and not the router login page.

The computer I was using to access the router was under parental controls. The reason I said it worked in windows and andriod is because when testing, I used my work laptop & the phone which are not in the parental controls. I tried my home laptop(windows) which is in the parental controls & it had the same issue.

Thanks CharlesA  and The Cog for all the suggestions. Hope my experience is useful to others. I will mark the thread as closed

---

### Post by The Cog on 2021-07-05
Thanks for posting the answer. That's one to remember.

---

### Post by jonyblin-3 on 2021-10-20
[COLOR=#000000][FONT=Arial]*I have also started noticing that TP-Link routers have been working lately. Perhaps it has something to do with the change of IP addresses that the manufacturers use? As soon as my old router (and it was a TP-Link) started letting me down, I replaced it with a Linksys, with which I stopped seeing such problems. All I did was call a wizard, who reconnected the ISP network and configured the router via [https://192-168-1-1ip.mobi/](https://192-168-1-1ip.mobi/). I spent all day testing the internet speed to see if it had increased. I noticed that the rate was several times faster. That certainly made me happy.*[/FONT][/COLOR]

---

