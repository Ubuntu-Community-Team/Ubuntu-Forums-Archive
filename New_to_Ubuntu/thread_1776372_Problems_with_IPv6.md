---
title: "Problems with IPv6"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by jre6 on 2011-06-06
While many are excited with this World IPv6 Day, I am having problems while connecting testing my IPv6 readiness.

I am on Ubuntu 10.04.2 (updated from 10.04.1) and just wanted to test whether I am IPv6 ready, as I had recently read it on [Slashdot]("http://it.slashdot.org/story/11/06/02/2035204/World-IPv6-Day-On-June-8"). I found these sites, and tested on them.

The problem is that the results vary on Windows XP and Ubuntu. I am sure I haven't done any configurations like 6to4/Teredo etc. One thing that I know for sure is that my ISP can't reach IPv6-only sites because it has no access to the IPv6 internet (or perhaps isn't configured to use it). The results are as below:

**On Ubuntu**

[http://ipv6eyechart.ripe.net/](http://ipv6eyechart.ripe.net/)


[IMG]http://img268.imageshack.us/img268/4180/linripetest.png[/IMG]


[http://ipv6test.google.com](http://ipv6test.google.com)


[IMG]http://img62.imageshack.us/img62/8971/lingoogtest.png[/IMG]


[http://test-ipv6.com](http://test-ipv6.com)


[IMG]http://img863.imageshack.us/img863/6706/lintestipv6.png[/IMG]

**On Windows**

[http://ipv6eyechart.ripe.net](http://ipv6eyechart.ripe.net)

[IMG]http://img59.imageshack.us/img59/4963/winripetest.png[/IMG]

[http://ipv6test.google.com](http://ipv6test.google.com)

[IMG]http://img14.imageshack.us/img14/1062/wingoogtest.png[/IMG]

[http://test-ipv6.com](http://test-ipv6.com)

[IMG]http://img705.imageshack.us/img705/9826/wintestipv6.png[/IMG]

Now, why is this contradiction occuring? Can it be resolved in Ubuntu 10.04.2 by changing settings? If so, how? Otherwise, do I need an upgrade to a later version like 10.10/11.04? Or is this something where my ISP is at fault?

---

### Post by regala on 2011-06-06
> **jre6 said:**
> 
...


does your ISP provide IPv6 connectivity ? if not, all your tests are pointless...

-- 
Mathieu

---

### Post by robsoles on 2011-06-06
> **regala said:**
> does your ISP provide IPv6 connectivity ? if not, all your tests are pointless...

-- 
Mathieu

From the one location, behind (or 'plugged into') the same ISP, the OP indicates less functionality using 10.04.02 than OP got with Windows XP.

> **jre6 said:**
> ...

Now, why is this contradiction occuring? Can it be resolved in Ubuntu  10.04.2 by changing settings? If so, how? Otherwise, do I need an  upgrade to a later version like 10.10/11.04? Or is this something where  my ISP is at fault?

Your ISP is (quite possibly, at least) at fault where the testing website states that as the problem.

I doubt you need to upgrade, I'm running 10.04 on a fairly recent desktop setup and 10.10 on a Samsung netbook and they've both just pulled your 'Windows XP' results (that I can see in your pics) from the [http://ipv6eyechart.ripe.net/](http://ipv6eyechart.ripe.net/) website and I haven't tinkered once regarding IPv6.

Jumping into the network settings on the desktop machine I found the "IPv6 Settings" tab had "Method: Ignore" selected **after** running that test. All the testers I tried stated my ISP wasn't IPv6 enabled but they said my PC and my location were ready for Wednesday.

Would you please post the response of the following from the indicated OS:

**Ubuntu** (Terminal)
```
ifconfig -a
```**Windows** (DOS prompt)
```
ipconfig /all
```If you post both of those somebody might spot if there is a difference in the implementation each is using to access services from your computer.

(remove the HWaddr (Linux) and the "Physical Address" (Windows) numbers if you like but we need to see the rest to be sure they aren't different)

---

### Post by jtarin on 2011-06-06
> **regala said:**
> does your ISP provide IPv6 connectivity ? if not, all your tests are pointless...

-- 
MathieuIf you use a tunnel broker like hurricane or your setup with dns resolvers of opendns or google that statement is not entirely true.

---

### Post by sanderj on 2011-06-06
AFAIK, World IPv6 Day is *not* about testing IPv6 connectivity.


World IPv6 Day is about testing whether (web)servers like Google can safely activate IPv6 on their site (and side), next to existing IPv4, without breaking connectivity to their IPv4-only (and IPv4/IPv6-) users.

For example: a laptop on a IPv4-only connection, might try to connect via IPv6 first (after seeing [www.google.com](www.google.com) has an IPv6/AAAA address), which will time out (because the connection is IPv4-only), after which it will connect via IPv4. Result: a long delay in getting the webpage, so slowness, so an unhappy user. 
This is a fault of the laptop, but if it occurs on a lot of systems, it would be a reason for google *not* to give [www.google.com](www.google.com) an IPv6 address ... protecting their users.

World IPv6 Day is for finding this kind of problematic laptops, setups, etc.

---

### Post by sanderj on 2011-06-06
@jre6

So the RIPE site is reporting you have a bad connection to dual-stack site Python.org? Strange. 

EDIT: RIPE's explanation:

> 
This chart contains tests of connectivity to websites, by fetching an image from that website. The results for a website are:
	<GREEN logo> Content fetched within 10 seconds
	<RED logo> Content not fetched within 10 seconds



/EDIT

So Red means very slow or no connectivity at all to this dual-stack website. So exactly what I described in my earlier post: a Green logo means good connectivity, which might be pure, plain IPv4 (and no IPv6 at all)

So, do a test yourself: what's your output of "time wget python.org"? See mine below as an example.


```


sander@R540:~$ time wget http://python.org/
--2011-06-06 11:56:42--  http://python.org/
Resolving python.org... 2001:888:2000:d::a2, 82.94.164.162
Connecting to python.org|2001:888:2000:d::a2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19229 (19K) [text/html]
Saving to: `index.html.2'

100%[==============================================================================================================================>] 19,229      --.-K/s   in 0.1s    

2011-06-06 11:56:42 (170 KB/s) - `index.html.2' saved [19229/19229]


real	0m0.218s
user	0m0.010s
sys	0m0.010s
sander@R540:~$

```

---

### Post by jre6 on 2011-06-06
For "ifconfig -a" on Ubuntu I get:
```

eth0      Link encap:Ethernet  HWaddr 00:18:8b:d5:b8:6e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4128 (4.1 KB)  TX bytes:4128 (4.1 KB)

pan0      Link encap:Ethernet  HWaddr 3a:78:37:e4:8e:60  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:14.96.4.196  P-t-P:172.29.242.61  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2082 errors:12 dropped:0 overruns:0 frame:0
          TX packets:2088 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2256470 (2.2 MB)  TX bytes:303630 (303.6 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:7a:62:3c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

For "ipconfig /all" on Windows, I get:
```

Windows IP Configuration  
  
        Host Name . . . . . . . . . . . . : foobar-f28d488c  
        Primary Dns Suffix  . . . . . . . :   
        Node Type . . . . . . . . . . . . : Unknown  
        IP Routing Enabled. . . . . . . . : No  
        WINS Proxy Enabled. . . . . . . . : No  
  
Ethernet adapter Local Area Connection:  
  
        Media State . . . . . . . . . . . : Media disconnected  
        Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connection  
        Physical Address. . . . . . . . . : 00-09-6B-DA-82-12  
  
PPP adapter TATA Indicom:  
  
        Connection-specific DNS Suffix  . :   
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface  
        Physical Address. . . . . . . . . : 00-53-45-00-00-00  
        Dhcp Enabled. . . . . . . . . . . : No  
        IP Address. . . . . . . . . . . . : 14.96.174.172  
        Subnet Mask . . . . . . . . . . . : 255.255.255.255  
        Default Gateway . . . . . . . . . : 14.96.174.172  
        DNS Servers . . . . . . . . . . . : 121.242.190.180  
                                            121.242.190.210  
        NetBIOS over Tcpip. . . . . . . . : Disabled 

```

For "time wget python.org" I get:
```

--2011-06-06 17:51:32--  http://python.org/
Resolving python.org... ^C

real    0m7.793s
user    0m0.008s
sys    0m0.000s
supriyo@ubuntu:~$ time wget http://python.org
--2011-06-06 17:51:44--  http://python.org/
Resolving python.org... 82.94.164.162, 2001:888:2000:d::a2
Connecting to python.org|82.94.164.162|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19229 (19K) [text/html]
Saving to: `index.html'

100%[======================================>] 19,229      30.5K/s   in 0.6s    

2011-06-06 17:51:56 (30.5 KB/s) - `index.html' saved [19229/19229]


real    0m11.398s
user    0m0.004s
sys    0m0.012s


```

---

### Post by robsoles on 2011-06-06
What I asked for doesn't tell me as much as sanderj's suggestion went on to tell me:
```
rob@rob-desktop:~$ time wget python.org
--2011-06-06 20:06:55--  http://python.org/
Resolving python.org... 82.94.164.162, 2001:888:2000:d::a2
Connecting to python.org|82.94.164.162|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19229 (19K) [text/html]
Saving to: `index.html'

100%[======================================>] 19,229      24.0K/s   in 0.8s    

2011-06-06 20:06:57 (24.0 KB/s) - `index.html' saved [19229/19229]


real    0m2.093s
user    0m0.000s
sys    0m0.010s
**rob@rob-desktop:~$ wget ipv6.google.com**
--2011-06-06 20:10:00--  http://ipv6.google.com/
Resolving ipv6.google.com... 2404:6800:8004::68
Connecting to ipv6.google.com|2404:6800:8004::68|:80... failed: **Network is unreachable**.
rob@rob-desktop:~$
```My ISP is the roadblock there, I think you will find your ISP the road block too. Maybe it is browser settings that is different between your two installations which causes the difference in outcomes.

Try [http://ipv6.google.com/](http://ipv6.google.com/) 

sanderj is on a completely IPv6 enabled route, we aren't unless we tunnel as jtarin suggests - personally I am going to petition my ISP, and switch ISPs if necessary, when that road block starts bothering me.

---

### Post by sanderj on 2011-06-06
> **jre6 said:**
> 

[/CODE]

supriyo@ubuntu:~$ time wget [http://python.org](http://python.org)
--2011-06-06 17:51:44--  [http://python.org/](http://python.org/)
Resolving python.org... 82.94.164.162, 2001:888:2000:d::a2
Connecting to python.org|82.94.164.162|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19229 (19K) [text/html]
Saving to: `index.html'

100%[======================================>] 19,229      30.5K/s   in 0.6s    

2011-06-06 17:51:56 (30.5 KB/s) - `index.html' saved [19229/19229]


real    0m11.398s
user    0m0.004s
sys    0m0.012s

[/CODE]

Wow: that's bad: it takes 11+ seconds to get that page. That's exactly what the RIPE site reports: "RED because more than 10 seconds"

Now: where is the delay coming from? In your wget I don't see wget trying to connect via IPv6 (which would explain the delay), so what is it? A slow name-lookup? Run some more tests:

time wget -4 python.org
time host python.org
time wget -4 python.org
time host python.org
time wget 82.94.164.162
time wget -6 python.org

And, yes, run some of them twice in this order; I want to see if there is caching.

---

### Post by ratcheer on 2011-06-06
The reason it works on Windows and not on Ubuntu is that Teredo is enabled by default of recent versions of Windows. This is "6 to 4" functionality. If you want the same thing in Ubuntu, you can install the miredo package and go from there.

The better way to get more genuine IPv6 is to create a "6 in 4" tunnel with an outfit such as Hurricane Electric or SixXS. I use Hurricane Electric and have perfect results on all the various IPv6 test pages.

If you decide to set up a tunnel, it is best to have a router that supports IPv6. If it doesn't, at a minimum it will have to pass protocol 41 packets. What I did was flash my router to a version of dd-wrt that supports IPv6.

To the best of my knowledge, only a very small handful of ISP's actually block protocol 41.

Tim

---

### Post by sanderj on 2011-06-06
@robsoles

Rob, IMHO you're mixing up things: 
The OP is complainingg about *dual-stack* sites being very slow / unreachable. That's wat [http://ipv6eyechart.ripe.net/](http://ipv6eyechart.ripe.net/) and the "time wget" reports. That's a serious problem for a normal, plain IPv4 user like the OP.

You, however, are complaing about a IPv6-only site being not reachable. That's something else. With one command on Ubuntu you can solve that. See my signature. No need to switch ISP.

To see the difference, what is *your* report on [http://ipv6eyechart.ripe.net/](http://ipv6eyechart.ripe.net/) ? I guess you get green logo's. No IPv6 needed to get green logo's.

---

### Post by sanderj on 2011-06-06
> **ratcheer said:**
> The reason it works on Windows and not on Ubuntu is that Teredo is enabled by default of recent versions of Windows.

Correct for recent versions of Windows: Vista and Win7. However: The OP says he is using a plain Windows XP. Plain Windows XP has no Teredo installed nor activated.

And still: the problem is his/her Ubuntu is showing red signs on the RIPE page [http://ipv6eyechart.ripe.net/](http://ipv6eyechart.ripe.net/) . That's not good, no matter what kind of connection, no matter what Windows shows: it's bad in itself.

So let's solve that. (And no, realising an IPv6 connection is not needed to solve that; maybe even removing all IPv6 on his machine is needed)

---

### Post by jre6 on 2011-06-06
**EDIT**: Didn't note that order preservation was necessary. Here are the results in the order of the commands:
Output of "time wget -4 python.org ; time host python.org ; time wget -4 python.org ; time host python.org ; time wget 82.94.164.162 ; time wget -6 python.org"
```

--2011-06-06 18:59:59--  http://python.org/
Resolving python.org... 82.94.164.162
Connecting to python.org|82.94.164.162|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19229 (19K) [text/html]
Saving to: `index.html.1'

100%[=============================================>] 19,229      34.5K/s   in 0.5s    

2011-06-06 19:00:05 (34.5 KB/s) - `index.html.1' saved [19229/19229]


real    0m6.181s
user    0m0.000s
sys    0m0.008s
python.org has address 82.94.164.162
python.org has IPv6 address 2001:888:2000:d::a2
python.org mail is handled by 50 mail.python.org.

real    0m3.365s
user    0m0.000s
sys    0m0.012s
--2011-06-06 19:00:08--  http://python.org/
Resolving python.org... 82.94.164.162
Connecting to python.org|82.94.164.162|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19229 (19K) [text/html]
Saving to: `index.html.2'

100%[=============================================>] 19,229      32.8K/s   in 0.6s    

2011-06-06 19:00:15 (32.8 KB/s) - `index.html.2' saved [19229/19229]


real    0m6.348s
user    0m0.008s
sys    0m0.000s
python.org has address 82.94.164.162
python.org has IPv6 address 2001:888:2000:d::a2
python.org mail is handled by 50 mail.python.org.

real    0m3.392s
user    0m0.000s
sys    0m0.016s
--2011-06-06 19:00:18--  http://82.94.164.162/
Connecting to 82.94.164.162:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.python.org [following]
--2011-06-06 19:00:19--  http://www.python.org/
Resolving www.python.org... 82.94.164.162, 2001:888:2000:d::a2
Reusing existing connection to 82.94.164.162:80.
HTTP request sent, awaiting response... 200 OK
Length: 19229 (19K) [text/html]
Saving to: `index.html.3'

100%[=============================================>] 19,229      37.9K/s   in 0.5s    

2011-06-06 19:00:30 (37.9 KB/s) - `index.html.3' saved [19229/19229]


real    0m11.479s
user    0m0.000s
sys    0m0.012s
--2011-06-06 19:00:30--  http://python.org/
Resolving python.org... 2001:888:2000:d::a2
Connecting to python.org|2001:888:2000:d::a2|:80... failed: Network is unreachable.

real    0m5.189s
user    0m0.000s
sys    0m0.008s


```
Another thing to notify: The IPv6EyeChart test is giving a contradictory result even on Ubuntu. When I reload the same page, the scenario rather changes, with Akamai Dual-test the only one failing. I have made a video of it, and I will share the link soon. Just give me some time.

**EDIT**: Here's the video, compressed as ".tar.lzma" : [http://www.mediafire.com/download.php?dd09cx96khpr1px](http://www.mediafire.com/download.php?dd09cx96khpr1px)
and I think "caching" is taking place.

---

### Post by sanderj on 2011-06-06
I don't see the timing output of "time wget 82.94.164.162". Can you post it?

And post the output of "time host nu.nl". On my Ubuntu, that takes 0.113 seconds.

If these two tests take more than 2 seconds (see mine: 0.1 second), you haven't got a dual-stack/IPv6 problem, but you have a plain network (or system) problem. And that's worse ...:(



```

sander@R540:~$ time host nu.nl
nu.nl has address 62.69.179.198
nu.nl mail is handled by 10 smtpscan-nl1.sanoma-uitgevers.nl.
nu.nl mail is handled by 10 smtpscan-nl2.sanoma-uitgevers.nl.

real	0m0.113s
user	0m0.000s
sys	0m0.010s
sander@R540:~$
```

---

### Post by robsoles on 2011-06-06
@sanderj: Agreed I was off on the wrong tangent earlier. Based on current progress my next inquiry would be to compare PPP settings between XP and 10.04.2; If different I would assume XP is using the better set.

Sorry for interrupting, I should be in bed!

---

### Post by regala on 2011-06-06
> **jtarin said:**
> If you use a tunnel broker like hurricane or your setup with dns resolvers of opendns or google that statement is not entirely true.

I hope he knows he uses a broker. doesn't seem likely from the post.

---

### Post by jre6 on 2011-06-06
I don't know what a broker is and I don't think I use it.

---

### Post by ratcheer on 2011-06-06
> **jre6 said:**
> I don't know what a broker is and I don't think I use it.

Correct, you are not using a tunnel broker. Based on your "ipconfig /all", you have no IPV6 connectivity. I have no idea how you are connecting to IPv6 sites from Windows.

I thought in the OP, you were saying you want to get IPv6 connectivity. My previous post was directed to trying to help you with that.

Tim

---

### Post by jre6 on 2011-06-06
Yeah, I want to also get IPv6 connectivity, but is it possible? Can anyone guide me with this thing called "Teredo"? Is it usable on IPv4? My very first post tells that my ISP isn't connected to IPv6?

And, anyway, can anyone explain the mysterious behaviour of the IPv6EyeChart test shown in the video? See my other post for the video.

---

### Post by jre6 on 2011-06-06
Output of "time host nu.nl":
```

nu.nl has address 62.69.179.198
nu.nl mail is handled by 10 smtpscan-nl1.sanoma-uitgevers.nl.
nu.nl mail is handled by 10 smtpscan-nl2.sanoma-uitgevers.nl.

real    0m4.066s
user    0m0.008s
sys    0m0.004s

```

Output of "time wget 82.94.164.162":
```

--2011-06-06 22:35:20--  http://82.94.164.162/
Connecting to 82.94.164.162:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.python.org [following]
--2011-06-06 22:35:20--  http://www.python.org/
Resolving www.python.org... 82.94.164.162, 2001:888:2000:d::a2
Reusing existing connection to 82.94.164.162:80.
HTTP request sent, awaiting response... 200 OK
Length: 19229 (19K) [text/html]
Saving to: `index.html'

100%[======================================>] 19,229      2.10K/s   in 11s     

2011-06-06 22:35:42 (1.78 KB/s) - `index.html' saved [19229/19229]


real    0m22.308s
user    0m0.012s
sys    0m0.000s


```

---

### Post by sanderj on 2011-06-06
> **jre6 said:**
> Output of "time host nu.nl":
```

nu.nl has address 62.69.179.198
nu.nl mail is handled by 10 smtpscan-nl1.sanoma-uitgevers.nl.
nu.nl mail is handled by 10 smtpscan-nl2.sanoma-uitgevers.nl.

real    0m4.066s
user    0m0.008s
sys    0m0.004s

```

Output of "time wget 82.94.164.162":
```

--2011-06-06 22:35:20--  http://82.94.164.162/
Connecting to 82.94.164.162:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.python.org [following]
--2011-06-06 22:35:20--  http://www.python.org/
Resolving www.python.org... 82.94.164.162, 2001:888:2000:d::a2
Reusing existing connection to 82.94.164.162:80.
HTTP request sent, awaiting response... 200 OK
Length: 19229 (19K) [text/html]
Saving to: `index.html'

100%[======================================>] 19,229      2.10K/s   in 11s     

2011-06-06 22:35:42 (1.78 KB/s) - `index.html' saved [19229/19229]


real    0m22.308s
user    0m0.012s
sys    0m0.000s


```

So your plain IPv4 name lookup is very slow: 4 seconds!

Your wget is also very slow (22 seconds). Theoretically that might be caused my IPv6, but I don't think so. 
Easy final test "time wget www.nu.nl" (which is IPv4 only).

Conclusion: you have a very slow systems and/or Internet connection. That's why the RIPE site is showing red logo's. I has nothing to do with IPv6.

Getting IPv6 on your system is easy: "sudo apt-get install miredo". But at the current state of your system/connection I think you have more urgent things to do: make your system and/or Internet connection faster. I can only understand your slowness if:
- you're on dialup Internet, and/or
- you have minimum requirements system (like < 512 MB RAM)
- your system is overloaded
- your Internet connection is heavily used, for example bittorrent using the full upstream connection

So if you want to solve that, start new thread.

HTH

---

### Post by jre6 on 2011-06-06
Miredo installed. And after that:

[http://ipv6eyechart.ripe.net](http://ipv6eyechart.ripe.net)

[IMG]http://img593.imageshack.us/img593/4849/teredoripe.png[/IMG]

[http://ipv6.google.com](http://ipv6.google.com)

[IMG]http://img27.imageshack.us/img27/8551/teredoipv6goog.png[/IMG]

[http://test-ipv6.com/](http://test-ipv6.com/)

[IMG]http://img825.imageshack.us/img825/2995/teredotestipv6.png[/IMG]


[http://ipv6test.google.com](http://ipv6test.google.com)

[IMG]http://img694.imageshack.us/img694/3205/teredolingoog.png[/IMG]

Although everything is a little slower now. As for the speed of my connection, it is max 3.1 Mbps and at the time of this writing it is 1.2 Mbps. Is this slow?

---

### Post by jre6 on 2011-06-06
If you see the video ([http://www.mediafire.com/download.php?dd09cx96khpr1px](http://www.mediafire.com/download.php?dd09cx96khpr1px)), you will notice that everything has just become more worse after Teredo. Many connections are failing even after a reload.[]("http://www.mediafire.com/download.php?dd09cx96khpr1px")

---

### Post by sanderj on 2011-06-06
> **jre6 said:**
> Miredo installed. And after that:

<snip>

Although everything is a little slower now. As for the speed of my connection, it is max 3.1 Mbps and at the time of this writing it is 1.2 Mbps. Is this slow?


Good: your IPv6 works. Easy, isn't it?

3.1 and 1.2 Mbps are not explanations for your slow Internet connection. As a said: open a new thread with subject "Slow Internet". It's not IPv6 related.

---

### Post by jre6 on 2011-06-06
But I am still confused, why should the problem occur only in Ubuntu? It doesn't occur in Windows. And Google tells me that I still ain't ready on Ubuntu. Before miredo, I got many red logos on [http://ipv6eyechart.ripe.com/](http://ipv6eyechart.ripe.com/) and that would be resolved (the Akamai dual test was the only one that failed) if I reloaded the page. Now, 8-17 tests fail even after reloading.

---

### Post by jtarin on 2011-06-07
My IP doesn't support IPv6 yet but using either a tunnel broker or miredo in 10.10 all test indicate good to go here.
BTW quit quoting those pics every page.....not necessary and not doing so can prevent horizontal scrolling carpal tunnel syndrome.:p

---

### Post by lemming465 on 2011-06-07
Windows XP doesn't support IPv6 by default (run ipconfig /all; no ipv6 addresses will be visible.)  In contrast, Ubuntu - like windows 7 - *does* have IPv6 on by default.

If you check your test-ipv6.com results, you'll see that the two OS's are actually seeing the **same** upstream connectivity.  The pie chart differences appear to be due to DNS resolution timing, not to differences in IPv4 versus IPv6 transport.

Ironically, while you don't appear to have native IPv6, Tata is one of the world IPv6 day participants.

If you want to experiment with IPv6 using a tunneling technology, the simplest would be Teredo; do *sudo apt-get install miredo* and it will be live.  However, native IPv4 connections will rightly be preferred to tunneled IPv6, so it won't be used except with IPv6-only sites, of which there are very few at present.

For more serious IPv6 R&D, I prefer setting up a point to point link with a tunnel broker.  In the USA, the 3 main free choices are [www.tunnelbroker.net](www.tunnelbroker.net), [www.sixxs.net](www.sixxs.net), or the "freenet6" service from gogo6.com.  Setup details vary slightly.  If your ISP offers something, that would be better than any of the free services.

---

### Post by novinick on 2011-06-11
here's my eyechart FTW :cool:

6to4 seems not doing badly (those circles should be red X's i think)
at least comparing to teredo as i see

to bad it is going deprecated , 6to4 :(
[http://www.getipv6.info/index.php/Customer_problems_that_could_occur#Use_of_transitional_IPv6_connectivity](http://www.getipv6.info/index.php/Customer_problems_that_could_occur#Use_of_transitional_IPv6_connectivity)
in documents
"I-D.vandevelde-v6ops-harmful-tunnels"
"I-D.ietf-v6ops-6to4-to-historic"

---

### Post by VOT Productions on 2011-06-11
Well... if your ISP doesn't support it, then you can't do IPv6.
Also, if that's the case, there is nothing to worry about, you will just use IPv4.

---

### Post by ratcheer on 2011-06-11
> **VOT Productions said:**
> Well... if your ISP doesn't support it, then you can't do IPv6.
Also, if that's the case, there is nothing to worry about, you will just use IPv4.

No, you can do IPv6 whether your ISP supports it or not. The only reason you could not do it is if the ISP actively chooses to block protocol 41 packets.

Tim

---

