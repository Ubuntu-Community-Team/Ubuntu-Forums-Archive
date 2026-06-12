---
title: "AT&amp;T aircard 875 help"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by SanMateo on 2007-11-06
I configured my AT&T 875 aircard using the directions found here:
[http://redmonk.com/sogrady/2007/09/14/how-to-use-a-cingular-sierra-wireless-875-card-on-ubuntu-gutsy/](http://redmonk.com/sogrady/2007/09/14/how-to-use-a-cingular-sierra-wireless-875-card-on-ubuntu-gutsy/)
Then using sudo tail -f /var/log/messages I see this:
Nov  6 17:25:17 matt-laptop chat[6699]: send (ATDT*99***1#^M)
Nov  6 17:25:17 matt-laptop chat[6699]: expect (CONNECT)
Nov  6 17:25:17 matt-laptop chat[6699]: ^M
Nov  6 17:25:17 matt-laptop chat[6699]: ATDT*99***1#^M^M
Nov  6 17:25:17 matt-laptop chat[6699]: CONNECT
Nov  6 17:25:17 matt-laptop chat[6699]:  -- got it 
Nov  6 17:25:17 matt-laptop chat[6699]: send (\d)
Nov  6 17:25:18 matt-laptop pppd[6697]: Serial connection established.
Nov  6 17:25:18 matt-laptop pppd[6697]: Using interface ppp0
Nov  6 17:25:18 matt-laptop pppd[6697]: Connect: ppp0 <--> /dev/ttyUSB0
Nov  6 17:25:21 matt-laptop pppd[6697]: Could not determine remote IP address: defaulting to 10.64.64.64
Nov  6 17:25:21 matt-laptop pppd[6697]: local  IP address 166.214.12.249
Nov  6 17:25:21 matt-laptop pppd[6697]: remote IP address 10.64.64.64
Nov  6 17:25:21 matt-laptop pppd[6697]: primary   DNS address 66.102.163.231
Nov  6 17:25:21 matt-laptop pppd[6697]: secondary DNS address 66.209.10.201

But can't do anything, no email, no internet, nothing.  I am a noob that is trying to dump Vista and if I can get this to work. It is gone.  So far I love Ubuntu, just need this one last thing.

Thanks for your help.

---

### Post by sidcypher on 2007-12-07
I tried like everything...I have a 875..try this

[http://ubuntuforums.org/showthread.php?t=633869](http://ubuntuforums.org/showthread.php?t=633869)

---

### Post by bill.blankenship on 2007-12-14
Hi SanMateo,

It looks like you're running into the same problem that I had when I was trying to get my AirCard 875 up and running:

[INDENT]- The card acts like it connects
- You get a valid local IP
- You get valid DNS IPs
- You're getting the following message in the log:

      [INDENT]"Could not determine remote IP address: defaulting to 10.64.64.64"[/INDENT]

- You can't get a working connection to the internet[/INDENT]

I struggled with this for a while, and finally found someone to help me out. (See [[COLOR="Blue"]http://www.itguyonline.com/blog/2007/03/14/cingular-aircard-875-2/[/COLOR]]("http://www.itguyonline.com/blog/2007/03/14/cingular-aircard-875-2/") and a BIG thanks to Josh!) I created the files just like they are on the site. At first, I thought I had messed something up, because everyone was saying that it was SO easy to do... ;)  Luckily, Josh ran into the same problem that I had and knew more about networking on Linux.

Here's the steps I follow. I'm sure there might be an easier way, but this works for me, and I don't mind a few keystrokes... ;-)

[INDENT]1. After booting up, I open a console window and enter "route" to see my routing table.

2. I turn off whatever interfaces are listed. For example, my wifi usually shows up as "eth1", even though it doesn't have a valid connection. Since I can't GET a wifi connection (otherwise, why try to use the AirCard?), I don't need it anyways, so I enter the following command:
   
   [INDENT]sudo ifconfig eth1 down[/INDENT]

3. I verify the routing table is empty by entering "route" again.

4. I pop in the AirCard 875 and wait for it to initialize, then enter "pon cingular"[/INDENT]

This works like a champ. I can tell you that this WILL work for both 2G and 3G connections. If you're still having problems after trying this, let us know so we can help.

Happy Hacking!

---

### Post by mikemike on 2008-01-08
I followed the instructions in the link you posted and the light changed from amber to blue for 3G.  But I still cannot browse to a webpage.  The Network manager icon in the upper right of the screen says there is "No network connection".  Let me know if you need more info to help me.  I'm running Ubuntu Live CD on a Compaq Evo N610c laptop.

update: I've gotten it to connect 2 times since my original post.  But it is not consistent.  I've tried over 20 times.  Each time it did not connect, the primary DNS address is 10.11.12.13 and the secondary is 10.11.12.14.  The 2 times it has connected, these numbers have been different.  I'm not sure if this helps to determine the cause of the problem, but any advice will be appreciated.

---

### Post by bill.blankenship on 2008-01-09
mikemike,

IMHO, it looks like a majority of the problems using the AirCard 875 on Ubuntu fall into two different groups. 

The first group deals with the routing table and the AirCard being "last on the list". Everything LOOKS good on the connection, but priority is given to the other interfaces on the route table. Once everything is cleared out before trying to connect (leaving the the ppp interface as the only interface on the route table), the connection works just fine. (This is the problem I was running into...)

The second group is the problem you're experiencing, which is tied to DNS resolution. You are correct... the two DNS IPs 10.11.12.13 and 10.11.12.14 are bogus. (BTW, thanks for the update... that DID help...)  Take another look at [[COLOR="Blue"]http://www.itguyonline.com/blog/2007/03/14/cingular-aircard-875-2/[/COLOR]]("http://www.itguyonline.com/blog/2007/03/14/cingular-aircard-875-2/"), specifically the post by "Nic Pottier" on May 22nd, 2007. He provides a script that tries to determine what the actual DNS IPs should be. I honestly can't say whether it works or not though, because I didn't need to try it. (And, as always, take a good hard look at what the script does before running it... just to be safe...)

On another note, if you're using the Live CD, how are you saving the files required for the connection scripts? (/etc/ppp/peers/cingular, /etc/chatscripts/cingular, etc.) Are you copying these in each time you boot from the Live CD?

Happy Hacking!

---

### Post by mikemike on 2008-01-10
Bill, thanks for your reply.  I read the links you suggested.  But I don't know how to run scripts.  I'd need a bit more instructions to know how and where to write the code.  I've only just recently figured out how to use the terminal window in order to follow ITGuy's instructions.  But I took your other suggestion and have done a full install of Ubuntu on my laptop.  I'm still getting the same problems, though.  Sometimes it connects, sometimes it doesn't.

Is it possible to give me more detailed instructions on how to correct the problems.  

Here is what I get when I can't connect.

Jan 10 15:52:16 mikemike-laptop pppd[20546]: Could not determine remote IP address: defaulting to 10.64.64.64
Jan 10 15:52:16 mikemike-laptop pppd[20546]: local  IP address 10.104.27.207
Jan 10 15:52:16 mikemike-laptop pppd[20546]: remote IP address 10.64.64.64
Jan 10 15:52:16 mikemike-laptop pppd[20546]: primary   DNS address 10.11.12.13
Jan 10 15:52:16 mikemike-laptop pppd[20546]: secondary DNS address 10.11.12.14

And here is what I get when I can connect.

Jan 10 15:54:35 mikemike-laptop pppd[21394]: Could not determine remote IP address: defaulting to 10.64.64.64
Jan 10 15:54:35 mikemike-laptop pppd[21394]: local  IP address 10.4.117.103
Jan 10 15:54:35 mikemike-laptop pppd[21394]: remote IP address 10.64.64.64
Jan 10 15:54:35 mikemike-laptop pppd[21394]: primary   DNS address 66.102.163.231
Jan 10 15:54:35 mikemike-laptop pppd[21394]: secondary DNS address 66.102.163.232

---

### Post by joiningtheherd on 2008-01-12
Heya,
   As Blankenship was saying there seem to be two categories of problems.  I believe mine falls in the first.  When I clear out my routing table, then pop in the card and run 'pon cingular' the tail of /var/log/messages runs through the connection process showing a connection with an IP of 166.128.X.X which is right in line with those I get when I connect under windows.  The DNS servers are assigned as with the same values as under windows. Under 'ifconfig' the ppp0 interface says that it's generally sent 10-60 packets and recieved from 5-12 packets with zero packet loss.  
   All of this leads me to believe that it must be a routing problem, because I'm guessing that somehow commands aren't making it to the interface.  I'm not really well versed in how the kernel routing table works or how to really go about troubleshooting this.   Here's a synopsis of how the various outputs look

'tail -f /var/log/messages':
```

Jan 12 13:21:50 trevor-laptop pppd[6420]: pppd 2.4.4 started by dailyuser, uid 1001
Jan 12 13:21:51 trevor-laptop chat[6422]: abort on (BUSY)
Jan 12 13:21:51 trevor-laptop chat[6422]: abort on (NO CARRIER)
Jan 12 13:21:51 trevor-laptop chat[6422]: abort on (VOICE)
Jan 12 13:21:51 trevor-laptop chat[6422]: abort on (NO DIALTONE)
Jan 12 13:21:51 trevor-laptop chat[6422]: abort on (NO DIAL TONE)
Jan 12 13:21:51 trevor-laptop chat[6422]: abort on (NO ANSWER)
Jan 12 13:21:51 trevor-laptop chat[6422]: abort on (DELAYED)
Jan 12 13:21:51 trevor-laptop chat[6422]: send (ATZ^M)
Jan 12 13:21:51 trevor-laptop chat[6422]: expect (OK)
Jan 12 13:21:51 trevor-laptop chat[6422]: ATZ^M^M
Jan 12 13:21:51 trevor-laptop chat[6422]: OK
Jan 12 13:21:51 trevor-laptop chat[6422]:  -- got it 
Jan 12 13:21:51 trevor-laptop chat[6422]: send (AT+CGDCONT=1,"IP","ISP.CINGULAR"^M)
Jan 12 13:21:52 trevor-laptop chat[6422]: expect (OK)
Jan 12 13:21:52 trevor-laptop chat[6422]: ^M
Jan 12 13:21:52 trevor-laptop chat[6422]: AT+CGDCONT=1,"IP","ISP.CINGULAR"^M^M
Jan 12 13:21:52 trevor-laptop chat[6422]: OK
Jan 12 13:21:52 trevor-laptop chat[6422]:  -- got it 
Jan 12 13:21:52 trevor-laptop chat[6422]: send (ATDT*99***1#^M)
Jan 12 13:21:52 trevor-laptop chat[6422]: expect (CONNECT)
Jan 12 13:21:52 trevor-laptop chat[6422]: ^M
Jan 12 13:21:52 trevor-laptop chat[6422]: ATDT*99***1#^M^M
Jan 12 13:21:52 trevor-laptop chat[6422]: CONNECT
Jan 12 13:21:52 trevor-laptop chat[6422]:  -- got it 
Jan 12 13:21:52 trevor-laptop chat[6422]: send (\d)
Jan 12 13:21:53 trevor-laptop pppd[6420]: Serial connection established.
Jan 12 13:21:53 trevor-laptop pppd[6420]: Using interface ppp0
Jan 12 13:21:53 trevor-laptop pppd[6420]: Connect: ppp0 <--> /dev/ttyUSB0
Jan 12 13:21:54 trevor-laptop pppd[6420]: CHAP authentication succeeded
Jan 12 13:21:54 trevor-laptop pppd[6420]: CHAP authentication succeeded
Jan 12 13:21:56 trevor-laptop pppd[6420]: Could not determine remote IP address: defaulting to 10.64.64.64
Jan 12 13:21:56 trevor-laptop pppd[6420]: local  IP address 166.128.106.163
Jan 12 13:21:56 trevor-laptop pppd[6420]: remote IP address 10.64.64.64
Jan 12 13:21:56 trevor-laptop pppd[6420]: primary   DNS address 209.183.48.11
Jan 12 13:21:56 trevor-laptop pppd[6420]: secondary DNS address 209.183.48.10
```

'ifconfig ppp0':
```
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:166.128.106.163  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:62 (62.0 b)  TX bytes:659 (659.0 b)
```

route:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     *               255.255.255.255 UH    0      0        0 ppp0
default         *               0.0.0.0         U     0      0        0 ppp0
```

The messages show all the correct responses, but all ping requests return host unknown, or timed out.  Routing right?  Help me fix this... I'm reading up on routing, but there's a lot of studying to be done as well, and house, and yard work abounds.  Thanks.

---

