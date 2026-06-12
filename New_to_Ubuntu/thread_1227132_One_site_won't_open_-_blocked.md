---
title: "One site won't open - blocked?"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by LearningPerson on 2009-07-30
Hello,

One site is blocked: Tualatin Valley Water District, [www.tvwd.org](www.tvwd.org), Domain ID: D2894244-US, Registrant ID: 25098294


If I go to the Microsoft "side", I can get into this site but not on the Ubuntu/Mozilla side.  This is a new problem since I re-installed Hardy Heron. 

I have looked at Preferences, IVPtable 6 (although I don't understand that) and everything else available through Google search.

Please help.

Thanks,  Sharon

---

### Post by pmlxuser on 2009-07-30
may be its the settings in ~/.mozilla/firefox

try 
```

home$ rm -r .mozilla

```

and see what happens.

Ps: u might loose some of the installed addons

---

### Post by llamabr on 2009-07-30
NB: running that command will not 'possibly lose some add-ons', it will certainly delete all of your settings.  Furthermore there's absolutely no reason to believe that it will work.

Strangely, I also tried that link, and it won't load.  i changed my useragent to ie7 with win vista, and I still can't get it to load.  I don't own a copy of windows to test, but I'll take your word for it.

Email the webmaster and ask what the hell is going on.  There's possibly a good reason to exclude all non-windows computer users from paying their bills, but if his isn't one of them, he/she should correct this practice.

(Don't run that command)

---

### Post by sydbat on 2009-07-30
The site loaded for me without a problem. Maybe it was down for awhile??

---

### Post by wojox on 2009-07-30
Check Port:

    Port 80 is open

Ping Results:

    PING 208.252.64.5 (208.252.64.5) 56(84) bytes of data.

    --- 208.252.64.5 ping statistics ---
    5 packets transmitted, 0 received, 100% packet loss, time 4006ms

Resolve

    [www.tvwd.org](www.tvwd.org) resolves to 208.252.64.5

---

### Post by LearningPerson on 2009-07-30
Thanks, folks.  I HAVE talked to the webmaster and she just keeps saying it works for her.  As I have tried it at all hours and it is the only site which doesn't open for me, I'm inclined to think it could be something on their end or with Hardy Heron updates.

BTW, wojox, does your reply mean that you were able to open it?  I entered 208.252.64.5  and it still wouldn't open.  Any advice?

Thanks,  Sharon

---

### Post by wojox on 2009-07-30
Look at my ping results. It's them.
No I couldn't open it either.

---

### Post by stalkier on 2009-07-30
Does not work for me either.

---

### Post by LearningPerson on 2009-07-30
> **LearningPerson said:**
> Thanks, folks.  I HAVE talked to the webmaster and she just keeps saying it works for her.  As I have tried it at all hours and it is the only site which doesn't open for me, I'm inclined to think it could be something on their end or with Hardy Heron updates.

BTW, wojox, does your reply mean that you were able to open it?  I entered 208.252.64.5  and it still wouldn't open.  Any advice?

Thanks,  Sharon

OK, I went to Admin, Network Tools and when I ping 208.252.64.5  it says "the address cannot be found".  

What now?  Thanks, Sharon

---

### Post by LearningPerson on 2009-07-30
> **wojox said:**
> Look at my ping results. It's them.
No I couldn't open it either.
Thanks, wojox.  I'm stumped.  Sharon

---

### Post by egalvan on 2009-07-30
Since **Tualatin ** is part of the Win-Tel Name Conglomerate, 
is anyone surprised that Linux is not welcome at their party? :D

BTW, tried accessing from FF / Hardy, and no joy.

FF / WinXP loaded fine. 

Conspiracy, says I...  :P

---

### Post by oldsoundguy on 2009-07-30
> **egalvan said:**
> 
BTW, tried accessing from FF / Hardy, and no joy.

FF / WinXP loaded fine. 

Conspiracy, says I...  :P

Actually there is an issue at the site as I had the same as above.  It is shutting out Linux.  (and that is a NO NO for a public agency, especially in Oregon!)

---

### Post by LearningPerson on 2009-07-30
> **oldsoundguy said:**
> Actually there is an issue at the site as I had the same as above.  It is shutting out Linux.  (and that is a NO NO for a public agency, especially in Oregon!)

Ok, called another guy at TVWD and he said tow other people with Linux had had a problem.

One said to install Firestarter and another said to do something with scaling: 
"Most modern Linux systems have a sysctl.conf file someplace like /etc/sysctl.conf, you can just add the line below to make the setting persist across reboots: net.ipv4.tcp_window_scaling = 0"

I'm thinking installing Firestarter would be easier than maybe messing up on the terminal.

What do you think?

Sharon

---

### Post by QIII on 2009-07-30
For the OP:

I own a home in the TVWD.  I'm downtown right now, and I was able to access the site using FF 3.5 on a Windows machine.

I'll try to remember to see if I can access it from Ubuntu (Jaunty, sorry) through FF 3.5 when I get home.

---

### Post by LearningPerson on 2009-07-30
> **oldsoundguy said:**
> Actually there is an issue at the site as I had the same as above.  It is shutting out Linux.  (and that is a NO NO for a public agency, especially in Oregon!)
Hi oldsoundguy,

I installed Firestarter but couldn't start the firewall as it gave me an error: "the device eth0 is not ready"

I tried the sudo /etc/sysctl.conf but it said "command not found"

Am going crazy.

sharon

---

### Post by egalvan on 2009-07-30
> **LearningPerson said:**
> Hi oldsoundguy,

I installed Firestarter but couldn't start the firewall as it gave me an error: "the device eth0 is not ready"

I tried the sudo /etc/sysctl.conf but it said "command not found"

sharon

I SERIOUSLY doubt that the firewall is the issue.
I've been running a Hardy install since Apr-08, and have never run into connect problems...

As for etc/sysctl.conf, that's a system file, not a command.
You really should NOT be messing with this,
unless you have good info on it.

this is how it starts...
```
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

```

And again, I doubt this is the problem....

---

### Post by benfindlay on 2009-07-30
You can figure out is its a firefox or system thing by using telnet

Open a terminal and put the following into it:

```
telnet www.tvwd.org 80
```and press enter

Then enter the following: ```
GET / HTTP/1.0
``` and press enter twice.

If its connecting successfully, then you should see the page source code in terminal. I've just tried it in windows command prompt and Mac OS X Terminal, and it worked for both. Doing this through my ubuntu server returns a hanging terminal. Furthermore, accessing the site via links (a command prompt based web page viewer in Linux) displays similar failed results.

So no, this isn't your firewall. This makes me think that they are filtering connections on grounds of operating systems.

I wonder why...

---

### Post by niteshifter on 2009-07-30
Hi,

There's a problem alright, but not with the OP's system - not accessible from here in Tennessee by any OS/browser. Not responsive to pings either.

It is not a problem that edits to sysctl.conf can fix, nor tinkering with a client firewall.

It may be the site itself or their NSP. As one poster in the area indicated they could connect it may be an idiot web-monkey: attempting to restrict access to the local population (bad idea, people do travel). Or said web-monkey used MS templates without configuring them for the real world. PEBKAC occurs on the server end at times.

As I'm able to traceroute the domain, I'm leaning toward IP restriction.

{PEBKAC - Problem Exists Between Keyboard And Chair}

---

### Post by benfindlay on 2009-07-30
> **niteshifter said:**
> As I'm able to traceroute the domain, I'm leaning toward IP restriction.{PEBKAC - Problem Exists Between Keyboard And Chair}

As I understand it, traceroute uses ICMP packets to work, which do not identify their operating system of origin, therefore a traceroute would still work from a blocked OS. I may be wrong there though, any thoughts?

> **niteshifter said:**
> As one poster in the area indicated they could connect it may be an idiot web-monkey

Yes indeed, or perhaps some IP address blacklisting tool, which blocks access to IP addresses known to have given them trouble (e.g. hacking) and you have simply been unfortunate enough to be assigned that IP for your current session by your ISP, but that will change again, in time.

---

### Post by LearningPerson on 2009-07-30
> **benfindlay said:**
> As I understand it, traceroute uses ICMP packets to work, which do not identify their operating system of origin, therefore a traceroute would still work from a blocked OS. I may be wrong there though, any thoughts?



Yes indeed, or perhaps some IP address blacklisting tool, which blocks access to IP addresses known to have given them trouble (e.g. hacking) and you have simply been unfortunate enough to be assigned that IP for your current session by your ISP, but that will change again, in time.

Here is what I got: 

sharon@t:~$ telnet [www.tvwd.org](www.tvwd.org) 80
Trying 208.252.64.5...
Connected to [www.tvwd.org](www.tvwd.org).
Escape character is '^]'.
GET / HTTP/1.0

HTTP/1.1 200 OK
Connection: close
Date: Thu, 30 Jul 2009 22:28:32 GMT
Server: Microsoft-IIS/6.0
X-Powered-By: ASP.NET
Set-Cookie: ASP.NET_SessionId=0h0anziml1bwuevunutxfe55; path=/; HttpOnly
Cache-Control: private
Content-Type: text/html; charset=utf-8
Content-Length: 18622


Any clue what it means?

Thanks, Sharon

---

### Post by benfindlay on 2009-07-30
Right, you got a 200 series message; this means that there has been a proper response received. Lets try this one:

```
telnet www.tvwd.org 80
``` and press enter

Then enter this (note the important differences from last time, in **_Bold and underline_**):```
GET / HTTP/**_1.1_**
```Press enter **_ONCE_** then type this:```
Host: index.htm
``` and press enter **_twice_**. If successful you should see lines of text scroll by, and finish with </html>

If you get this then the site is properly accessing over telnet. If not, then it seems that something else is going on.

---

### Post by LearningPerson on 2009-07-30
> **benfindlay said:**
> Right, you got a 200 series message; this means that there has been a proper response received. Lets try this one:

```
telnet www.tvwd.org 80
``` and press enter

Then enter this (note the important differences from last time, in **_Bold and underline_**):```
GET / HTTP/**_1.1_**
```Press enter **_ONCE_** then type this:```
Host: index.htm
``` and press enter **_twice_**. If successful you should see lines of text scroll by, and finish with </html>

If you get this then the site is properly accessing over telnet. If not, then it seems that something else is going on.
Hi benfindlay,

Here is what I got:
Trying 208.252.64.5...
Connected to [www.tvwd.org](www.tvwd.org).
Escape character is '^]'.
GET / HTTP/1.1        
Host: index.htm

HTTP/1.1 200 OK
Date: Thu, 30 Jul 2009 22:49:59 GMT
Server: Microsoft-IIS/6.0
X-Powered-By: ASP.NET
Set-Cookie: ASP.NET_SessionId=w5dx5d45jrc1hi55bqiyn545; path=/; HttpOnly
Cache-Control: private
Content-Type: text/html; charset=utf-8
Content-Length: 18622


????
Sharon

---

### Post by benfindlay on 2009-07-30
Right, you are getting some information, but it's not serving you all of the content. Thats very odd. I've tried this on Mac OS X just now and I get the normally expected results (lines and lines of text - the website's source code). Since I get strange results using my ubuntu server, it makes me think that they are identifying the OS you are using, and intentionally blocking it.

---

### Post by QIII on 2009-07-30
I contacted the webmaster via my Windows machine.  Text of message follows.

```
I own a home in the TVWD.

I have found out through the Ubuntu (Linux) community that your website denies access to those running Linux operating systems.  When I attempted to do so a few minutes ago on a Linux machine, I was unable to connect.

I am now on a Windows machine.

I do not complain.  I take action.

If the situation is not rectified when I check again on Monday, I will contact the Attorney General and explore the possibility of a Class Action.
```

---

### Post by niteshifter on 2009-07-30
> **benfindlay said:**
> As I understand it, traceroute uses ICMP packets to work, which do not identify their operating system of origin, therefore a traceroute would still work from a blocked OS. I may be wrong there though, any thoughts?

ping uses ICMP echo reply and echo request. The OS is not material here. Just the originating IP address is. traceroute (*nix variants) sends a UDP , so it doesn't look like a ping - but the source address is there as well. Windows' tracert uses ICMP echo request, btw.

So, we have the possibility of a site that is blocking "ping ICMP" but some here state they have pinged it, so let's toss that out. If some can but other's can't ping and the only data available to the server is IP address ... they're filtering on IP and protocol. They may may be filtering on OS but that's further up the software stack.

---

### Post by egalvan on 2009-07-30
> **niteshifter said:**
> Hi,

There's a problem alright, but not with the OP's system -

It may be the site itself or their NSP...
 attempting to restrict access to the local population (bad idea, people do travel). 

I live in Deep South Texas..
as I stated in a previous post
I can access TVWD.org using MS-Windows, either IE6/7 or FF3.0x
but not FF under Linux...

> 
**Or said web-monkey used MS templates without configuring them for the real world.**
PEBKAC occurs on the server end at times.

As I'm able to traceroute the domain, I'm leaning toward IP restriction.

[COLOR="Red"]{PEBKAC - Problem Exists Between Keyboard And Chair}[/COLOR]

I am inclined to believe in severe Server-Side-PEBKAC. :)

---

### Post by QIII on 2009-07-30
I just tried the website (I live in the TVWD) from both an Ubuntu machine and a Windows machine, both using FF 3.5 and behind the same firewalled router and cable modem.

Windows -- no problem.

Ubuntu -- no dice.

---

### Post by QIII on 2009-07-30
Now, just tried from the previous windows machine booted to the Ubuntu drive.

Same NIC, router, modem.

-- No dice.

---

### Post by QIII on 2009-07-30
Fired up third machine:  Karmic/XP

XP:  Go

Karmic:  No Go

Again.  Same NIC, router, modem.

That's three machines behind the same router and modem.

Three NICs.

All Windows OSs (Vista 64 bit, Vista 32 bit, XP) are able to access the site using FF3.5.

No Ubuntu OSs (Jaunty 64 bit, Jaunty 32 bit, Karmic 64 bit) are able to access the site using FF3.5.

---

### Post by QIII on 2009-07-30
Got a nice response back from TVWD's automated email response...  Basically thanking me for my email and that they would get back to me in two business days.

My response:

Suggest you move more quickly than that.  I will contact the Attorney  General on Monday. 

I have three computers.  Each is a dual boot machine with one version of  Windows and a version of Ubuntu.  From behind the same firewalled router  and cable modem, the Windows operating systems can access your site.   The Linux operating systems cannot. 

I have been on the Ubuntu Forums site several times tonight and have  found that many posters confirm this behavior. 

Either by commission or omission you are blocking traffic based on OS.   I will be sure that the AG knows. 

Have a nice weekend.

---

### Post by benfindlay on 2009-07-31
> **niteshifter said:**
> ping uses ICMP echo reply and echo request. The OS is not material here. Just the originating IP address is. traceroute (*nix variants) sends a UDP , so it doesn't look like a ping - but the source address is there as well. Windows' tracert uses ICMP echo request, btw.

So, we have the possibility of a site that is blocking "ping ICMP" but some here state they have pinged it, so let's toss that out. If some can but other's can't ping and the only data available to the server is IP address ... they're filtering on IP and protocol. They may may be filtering on OS but that's further up the software stack.

I didn't know that about unix/linux traceroutes being different to Windows ones! Thats good to know, thanks!

Looking back at the posts regarding pings, it seems that the pings are showing 100% failure rates, which suggests they are blocking pings full stop. As it is, I'm connecting from another country; but I wonder how these results would change if we tried a proxy server.

---

### Post by LearningPerson on 2009-07-31
> **benfindlay said:**
> I didn't know that about unix/linux traceroutes being different to Windows ones! Thats good to know, thanks!

Looking back at the posts regarding pings, it seems that the pings are showing 100% failure rates, which suggests they are blocking pings full stop. As it is, I'm connecting from another country; but I wonder how these results would change if we tried a proxy server.

Hi benfindlay,

I would sure like to try a proxy server but don't know how to set it up?

Thanks, Sharon

---

### Post by sydbat on 2009-07-31
I posted earlier in this thread (first page) and had no problem connecting to the site. I tried again a few minutes ago and can still access it. 

I am in Canada and am running Hardy 64bit exclusively.

I am not entirely sure that the access problem encountered by those in Oregon has anything to do with their OS...although I could be wrong. I do know that default behaviour of a Microsoft server is to deny all Operating Systems except Windows (still waiting for the anti-trust on THAT one), but it is simple enough to configure and open up the server to everyone.

It is a baffling problem considering people from other countries (and other states?) can access this site, but those in the region cannot...at least with Linux.

---

### Post by wonderwhatthe on 2009-07-31
> **LearningPerson said:**
> 
 
This is a new problem since I re-installed Hardy Heron. 
 

 
 
Hi Sharon,
 
Does that mean you were able to access their site under Ubuntu before re-installing Hardy Heron?

---

### Post by LearningPerson on 2009-07-31
> **wonderwhatthe said:**
> Hi Sharon,
 
Does that mean you were able to access their site under Ubuntu before re-installing Hardy Heron?

Yes, I was able to access them a few months ago.  Weird, huh?!

Sharon

---

### Post by benfindlay on 2009-08-01
If access has been possible in the past, does anyone think that perhaps this may be a DNS issue? I know that when I upgraded to Hardy it did funny things to my network configurations at first, and I had to go and edit stuff within the network manager.

I still find it odd however, that I can access this site via Windows and Mac OS X, but it won't load using my ubuntu box. Also, I am connecting from an entirely different continent to others on this post, so I think that the likelihood of it being geographical based blocking is low.

Any thoughts?

---

### Post by jacklinux on 2009-08-01
i have this same problem on the none admin accounts. they block everything. Even using the Mozzila search in ubuntu brings back them all blocked.

---

### Post by benfindlay on 2009-08-01
Just come across these articles [here]("http://ubuntuforums.org/showthread.php?t=1174741&page=4"), [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89160") and [here]("http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon")
Might not be the reason, but they're suspiciously similar.

Hope this helps!

Ben

---

### Post by Stevie78 on 2009-08-01
Hmm got no problems whatsoever accessing the site. (Jaunty 9.04 and Firefox 3.0 from Portugal)

---

### Post by benfindlay on 2009-08-01
Just been looking at the error message I get when telnetting to port 80 (which is essentially what a browser does, then interprets the code for a better human viewing experience). I get a 400 error, which means bad request. This means that either the request to the server is 'malformed' or that the web server can't understand the query.

That got me thinking; could this be an issue with the IPv6 implementation in ubuntu, as I used to have problems (back in the days of 6.06) with IPv6 in Firefox and website loading. Anyway, we can check this:

Go into Firefox and type this into the address bar:```
about:config
```
Then in the filter box immediately below the address bar type: ```
ipv6
```
There will be an option called > network.dns.disableIPv6
which is set to false by default. Double click it and it will change to **true**.

Shut down firefox, reopen it and try connecting again (maybe reboot your system for luck! ;)).

Any joy?

Ben

---

### Post by LearningPerson on 2009-08-03
> **benfindlay said:**
> Just been looking at the error message I get when telnetting to port 80 (which is essentially what a browser does, then interprets the code for a better human viewing experience). I get a 400 error, which means bad request. This means that either the request to the server is 'malformed' or that the web server can't understand the query.

That got me thinking; could this be an issue with the IPv6 implementation in ubuntu, as I used to have problems (back in the days of 6.06) with IPv6 in Firefox and website loading. Anyway, we can check this:

Go into Firefox and type this into the address bar:```
about:config
```
Then in the filter box immediately below the address bar type: ```
ipv6
```
There will be an option called 
which is set to false by default. Double click it and it will change to **true**.

Shut down firefox, reopen it and try connecting again (maybe reboot your system for luck! ;)).

Any joy?

Ben

Hi Ben,

Printer broke so getting back to this problem.  I did as you suggested above but still no luck.  I'll try the ideas from your previous post.

Would it be a good idea to go back and change the ivp6 to "False"?


Thanks, Sharon

---

### Post by LearningPerson on 2009-08-03
> **benfindlay said:**
> Just come across these articles [here]("http://ubuntuforums.org/showthread.php?t=1174741&page=4"), [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89160") and [here]("http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon")
Might not be the reason, but they're suspiciously similar.

Hope this helps!

Ben

Hi again Ben,

Changed the ipv6 back to False.  Then tried "sudo vi /etc/sysctl.conf" 
but didn't know where or how to put 
"net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760"

I get the idea but had 2 mistakes and had to "rm /etc/sysctl.conf.swp" twice.  Which scared me enough that I will need more info such as exactly where to put these two lines of text.  Do I write some text first referring to the situation?

The terminal ends at "=1" where the cursor is right on the "1".

Thanks,  Sharon

---

### Post by wojox on 2009-08-03
I found their router:

[http://gtwy-rt.tvwd.org](http://gtwy-rt.tvwd.org)

---

### Post by ridetheteapot on 2009-08-03
Ummm, you guys answered this in like the first couple of posts. TURN OFF tcp windows scaling. they are prolly behind an old router
[http://lwn.net/Articles/92727/](http://lwn.net/Articles/92727/)

---

### Post by LearningPerson on 2009-08-04
> **wojox said:**
> I found their router:

[http://gtwy-rt.tvwd.org](http://gtwy-rt.tvwd.org)

Um, Wojox, how does that help me?  I really am a newby.

I tried the s TCP window scaling but messed up:
Entered:  "sudo vi /etc/sysctl.conf"

but didn't know where or how to put
"net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760"

I get the idea but had 2 mistakes and had to "rm /etc/sysctl.conf.swp" twice. Which scared me enough that I will need more info such as exactly where to put these two lines of text. 

The terminal ends at "=1" where the cursor is right on the "1".  Can I enter a #sign and start typing some text referring generally to the situation?

Thanks, Sharon

---

### Post by QIII on 2009-08-05
The TVWD firewall blocks all pings, regardless of OS, so that behavior is explained.

I was given the following suggestion from one of the employees at TVWD and it worked for me:

I installed Firestarter and started it.  

In addition to that suggestion, I selected "Disable Firewall", set the property "Minimize to tray on window close" and clicked the close icon.  That left Firestarter on my Gnome panel, disabled.

I was then able to access the site.

While that is an effective work-around, it is still a work-around.  And the fact that the suggestion was given by a TVWD employee convinces me that they DO recognize the issue (despite what I and a couple of other posters have been told by them).

Why, after all, would you have a ready work-around to an issue you do not think exists?

---

### Post by LearningPerson on 2009-08-05
Thanks to all of you for your help.

I did not know how to make  &#8220;sudo vi /etc/sysctl.conf&#8221; work for me so instead:
In the terminal, type "sudo gedit /etc/sysctl.conf'.* You should then be asked for your password.* Enter it.

A new window will open.* Enter by hand the following text in a blank line or row: 
net.ipv4.tcp_wmem=4096 16384 131072
net.ipv4.tcp_rmem=4096 87380 174760
then Save by clicking on the Save icon &#8211; duh.

The site can now be accessed but the problem would appear to be theirs as they are the only site I can't access.  I wrote to them with that news and the fix.

Will also install Firestarter.

Sharon

---

### Post by jcreyf on 2010-02-04
Hi All,

I'm also a TVWD customer who is running Linux at home (in Oregon, Beaverton).
I've been struggling with the same issue for more than a year now (when I kicked out my last Windows install at home).  I could no longer access [www.tvwd.org]("http://www.tvwd.org") and I got the same remark from the their webmaster that it's a problem on my end.
I've tried many different things to get this working but never succeeded ... until now :P

I have a Fedora 12 machine.
The fix is rather simple.  Find file /etc/sysctl.conf and add this line:
```
**net.ipv4.tcp_window_scaling = 0**
```I am now able to access [www.tvwd.org]("http://www.tvwd.org") on my Linux machine and pay my bills on-line.  Guess I have some catching up to do ;)

Here is how my file looks like now:
```
/etc]# ls -la
-rw-r--r--.   1 root root     899 2010-02-04 17:35 sysctl.conf
``````

/etc]# cat sysctl.conf
# Kernel sysctl configuration file for Red Hat Linux
#                                                   
# For binary values, 0 is disabled, 1 is enabled.  See sysctl(8) and
# sysctl.conf(5) for more details.                                  

# Controls IP packet forwarding
net.ipv4.ip_forward = 0        

# Controls source route verification
net.ipv4.conf.default.rp_filter = 1 

# Do not accept source routing
net.ipv4.conf.default.accept_source_route = 0

# JCREYF - fix to get www.tvwd.org accessible
[COLOR=Red]net.ipv4.tcp_window_scaling = 0                                [/COLOR]

# Controls the System Request debugging functionality of the kernel
kernel.sysrq = 0                                                   

# Controls whether core dumps will append the PID to the core filename.
# Useful for debugging multi-threaded applications.                    
kernel.core_uses_pid = 1                                               

# Disable netfilter on bridges.
net.bridge.bridge-nf-call-ip6tables = 0
net.bridge.bridge-nf-call-iptables = 0 
net.bridge.bridge-nf-call-arptables = 0
```

---

### Post by ridetheteapot on 2010-02-25
as they say in mortal kombat "whoopsie"

---

### Post by MooPi on 2010-02-25
Here is an interesting tidbit. after I attempted to connect I check my firewall log and minutes later your Water Authority was pinging my address.?hmmmmmm :(

---

