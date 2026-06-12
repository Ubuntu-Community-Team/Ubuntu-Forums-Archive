---
title: "The maximum allowed clients from your host FTP error"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Sejanus on 2011-01-31
Hello,
I keep getting the "sorry, the maximum allowed clients from your host (10) are already connected" error whenever I try to transfer a large number of files. At first I thought it's a filezilla bug, however I get the same error basically with every FTP client I've tried, including Total Commander under Wine. I do not get that error using Windows. I did try to limit maximum allowed connections for Filezilla, both in server settings and in global settings, it didnt change anything. I did try to switch between passive and active modes (not sure if it's related at all, just last desperate attempt), and it didnt change anything either.

When I try to use native ftp client (not sure how is it called, the one in Places -> Connect to a server) I get abstract "connection refused" error every time I  transfer large number of files. Connection is refused for separate particular files, if I click "Ignore" each time the rest of files are transfered perfectly well, so I assume it's the very same error. 

Anything I could do? This really drives me mad, transfering large numbers of files is a part of my everyday job...

P.S. and this happens with many different FTP servers. Also I dont get this error in Windows. So I assume it's not a server problem.

---

### Post by robsoles on 2011-02-01
I contact several different FTP servers every week and I sometimes transfer hundreds of files to or from them.

I use filezilla in both Linux and Windows and I don't get your error, ever. I configured 3 of the four FTP servers myself and the fourth is configured by someone that I know 'knows about as good as I do'. I've had to deselect stuff named with terminology like "Limit connections from individual clients" in both an MS FTP setup and ProFTPD, although it might be an FTP server awfully like ProFTP that I used in CentOS upon a time that I can't find a reference to right now!

**I'm going to suggest that the FTP Server in question isn't actually all that brilliantly configured** and just because you are probably using an edition of Windows that has a hard limit of 10 simultaneous internet connections doesn't make it Linux's fault for granting the 'calling program' as many internet sockets as it asks for, at least to a much a greater limit than the people at MS thought certain editions of their stuff should have.

Please tell me what version of Windows it is you have there - if it's not a server edition and it precedes Windows 7 then it's ***very likely*** got the '10 internet sockets' hard limit - I can't speak for Windows 7 but I bet MS still thinks the average home user (including professional) should never need more than 10 sockets and it's probably an internet attack if they ask for them!

Sorry I am not telling you anything very clever that will fix it for you: Set up a Windows VM and run filezilla in there if you can't correct that FTP server.

Are you using FTP or SFTP protocol?

<edited-in>I went and had a poke through my copy of FileZilla and found that the current settings are tamely 'Maximum simultaneous transfers: [2  ] (1-10).

I don't think I even looked at those settings when I first grabbed FileZilla. Are you using FileZilla from Ubuntu Software Centre in Ubuntu 10.04 LTS? </edited-in>

---

### Post by lavinog on 2011-02-01
What happens when you use ftp in the command line?

---

### Post by Sejanus on 2011-02-01
> 
I'm going to suggest that the FTP Server in question isn't actually all that brilliantly configured

Actually there are 2 of them I use frequently, and I get this error with both of them. Yes, based on my previous experience with these servers and their admins, it's very likely they aren't brilliantly configured. It's very likely it's an understatement :) Nevertheless, I must use them and I cannot change their configuration :( And since it's possible in Windows, I hope there's a way to make it work with Linux clients too.

Now I didn't know OS can or does limit connection for FTP clients, though I suspected as much after I started getting this error. That explains :/ 

I use **Windows 7** at the moment, but **Windows Vista** and **Windows XP** used to work with the very same servers **just as fine**.

**Filezilla** not sure where aptitude downloads it from, the package is named **filezilla_3.3.1-1ubuntu2_i386.deb.** I did apt-get install filezilla.

I use **FTP**, not SFTP.

So basically it's still a filezilla bug? That I cannot limit number of connections?

---

### Post by robsoles on 2011-02-01
> **Sejanus said:**
> Actually there are 2 of them I use frequently, and I get this error with both of them. Yes, based on my previous experience with these servers and their admins, it's very likely they aren't brilliantly configured. It's very likely it's an understatement :) Nevertheless, I must use them and I cannot change their configuration :( And since it's possible in Windows, I hope there's a way to make it work with Linux clients too.

Now I didn't know OS can or does limit connection for FTP clients, though I suspected as much after I started getting this error. That explains :/ 

I use **Windows 7** at the moment, but **Windows Vista** and **Windows XP** used to work with the very same servers **just as fine**.

**Filezilla** not sure where aptitude downloads it from, the package is named **filezilla_3.3.1-1ubuntu2_i386.deb.** I did apt-get install filezilla.

I use **FTP**, not SFTP.

So basically it's still a filezilla bug? That I cannot limit number of connections?

The specific error message given is solely a message from the server - the client has connected the maximum allowable per individual client and requested another connection and that should be the only reason to get this error.

So is that Windows 7 home, pro, student, server? The non Server editions of MS Windows XP that I checked out had hard limits of 10 simultaneous connections just as some or other source made me think to check - it's been a while and I sort of wish I hadn't mentioned it.

You have the copy of filezilla from the Ubuntu repository that is for a 32 bit architecture where I have the same thing, but for a 64 bit arch instead.

@lavinog

FTP (unless you've done configuration I haven't checked out, ftp at command line is same) is a "clear-text" protocol with no encryption. It's been a while since I went poking into anything like ProFTPd and it may be possible to set the Server to refer the client to a secure connection if it 'dials in the nude', so to speak, these days.

Try 'man ftp' and 'man sftp' into terminal sometime.

Back to you, Sejanus.

I'm not sure I'd rush into pinning a bug on FileZilla from what you've said. Would you please tell us what the "Edit"->"Settings" in FileZilla says, in your copy, on the "Transfers" root page.

---

### Post by Sejanus on 2011-02-01
[[IMG]http://img209.imageshack.us/img209/5200/settingsl.png[/IMG]](http://img209.imageshack.us/i/settingsl.png/)


By the way, in Filezilla bug reports, I found this bug already reported, *twice*, and both times rejected as "not our fault". So chances are it's not Filezilla's fault... or at least not entirely their fault. Which still doesnt help me much ;)

P.S. I just tried to change Maximum Simultaneous Transfers to 1, still same error.

---

### Post by lavinog on 2011-02-01
> **robsoles said:**
> 
@lavinog

FTP (unless you've done configuration I haven't checked out, ftp at command line is same) is a "clear-text" protocol with no encryption. It's been a while since I went poking into anything like ProFTPd and it may be possible to set the Server to refer the client to a secure connection if it 'dials in the nude', so to speak, these days.

Try 'man ftp' and 'man sftp' into terminal sometime.



I was recommending using the command line for troubleshooting.
If they use the command line to connect (shouldn't need to even login) and they get the same error, then it would show that the problem isn't specific to filezilla.
Because the OP mentioned that they use FTP and not SFTP, i assumed logging in wouldn't be an issue anyway.  Performing a file transfer with the command line ftp client can also isolate the issue to filezilla initiating too many connections.

---

### Post by Sejanus on 2011-02-01
> 
 then it would show that the problem isn't specific to filezilla.

Oh I am pretty sure it isn't. I get the very same error with Total Commander under Wine and some other FTP clients.

---

### Post by Sejanus on 2011-02-01
> 
 then it would show that the problem isn't specific to filezilla.

Oh I am pretty sure it isn't. I get the very same error with Total Commander under Wine and some other FTP clients. But Filezilla allows you to limit number of simultaneous connections and it (apparently) doesnt work :\ Not sure how it is with Total Commander, didn't find anything like that in options. 

Not sure what you mean by "shouldn't need to login".

Sorry for double post, I misclicked edit ;\

---

### Post by robsoles on 2011-02-01
> **lavinog said:**
> I was recommending using the command line for troubleshooting.
If they use the command line to connect (shouldn't need to even login) and they get the same error, then it would show that the problem isn't specific to filezilla.
Because the OP mentioned that they use FTP and not SFTP, i assumed logging in wouldn't be an issue anyway.  Performing a file transfer with the command line ftp client can also isolate the issue to filezilla initiating too many connections.

You seem to be talking about anonymous FTP, if they aren't challenged for login credentials (and nothing in their client provides them due to any preconfiguration). If you are allowing uploads in anonymous FTP without a mechanism to vet uploaded files before showing them for download then I think you are taking risks I wouldn't.

@Sejanus:
Try FileZilla with one concurrent upload and download each.

---

### Post by Sejanus on 2011-02-01
> 
Try FileZilla with one concurrent upload and download each.

Same :(

Edit:

this is getting increasingly retarded, pardon my French.
I just rebooted PC, launched Filezilla, connected to the server. No uploads, no nothing, just connected. Then I tried to connect to the same server from NetBeans IDE (just wanted to test if the newly configured connection is OK). And immediately got the same **530 Sorry, the maximum number of clients (10) from your host are already connected.**

---

### Post by robsoles on 2011-02-01
It is a tricky one for sure. I assume you quit FileZilla before starting the NetBeans IDE connection - did you choose 'disconnect' in FileZilla before quitting?

Maybe if you watch the output of netstat while trying the FTP clients you can confirm how many connections the buggers are making
```
netstat -n -W -c | grep [COLOR=Purple]<ip-address-being-ftp'd>[/COLOR]
```into terminal will run continuously updating list of connections (and their states, pay attention to states) for "ip-address-being-ftp'd" - stop all other internet activity (if torrenting or anything like that in the background) on the machine in question and see if you can spot FileZilla making ten connections in the output.

To stop the command in terminal press [CTRL]+[C] while the terminal has focus.

---

### Post by Sejanus on 2011-02-01
> 
It is a tricky one for sure. I assume you quit FileZilla before starting the NetBeans IDE connection - did you choose 'disconnect' in FileZilla before quitting?

Actually I didn't quit FileZilla at all. If FileZilla used 1 connection and NetBeans another 1, that makes 2 of them, still not 10 :| 

But if the connections stay alive after closing FileZilla without manually disconnecting it first, that explains why I wasn't even able to connect to the server (same error) for the last half hour, even if I closed FileZilla after each attempt. 

All right. Thanks a lot for your help and patience by the way ;) 

Now, netstat doesn't produce any output in terminal whatsoever. Not sure why. Though when I typed just **netstat --tcp --programs** I got the following output:

```
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 sejanus.home:34563        myftpadress.inquestion.l:ftp TIME_WAIT   -               
tcp       69      0 sejanus.home:33802        myftpadress.inquestion.:ftp CLOSE_WAIT  2670/gvfsd-ftp  
tcp        0      0 sejanus.home:49029        xx-xx-xx-xxx.stati:3030 ESTABLISHED 2305/skype      
tcp        0      0 sejanus.home:34572        myftpadress.inquestion.l:ftp TIME_WAIT   -               
tcp        0      0 sejanus.home:34573        myftpadress.inquestion.l:ftp TIME_WAIT   -               
tcp        0      0 sejanus.home:34574        myftpadress.inquestion.l:ftp TIME_WAIT   -               
tcp        0      0 sejanus.home:34564        myftpadress.inquestion.l:ftp TIME_WAIT   -               
tcp        1      0 sejanus.home:60884        xxx-xxx-xxx-xx.cust:www CLOSE_WAIT  2469/clock-applet
tcp        0      0 sejanus.home:34570        myftpadress.inquestion.l:ftp TIME_WAIT   -               
tcp        0      0 sejanus.home:43482        c-xxx-xxx.marinet:30763 ESTABLISHED 2305/skype      
tcp        0      0 sejanus.home:55729        myftpadress.inquestion.l:ftp ESTABLISHED 6858/filezilla  
tcp        0      0 sejanus.home:34571        myftpadress.inquestion.l:ftp TIME_WAIT   -    
sejanus@sejanus:~$ 

```

That's 9 connections at once if I get it right? Probably it could be more (maybe filezilla paused for a second after getting the error, etc.)

And **after I closed** filezilla, the same netstat command produce the same output, i.e. I can still see the connections. After about two minutes after closing FileZilla there's only one connection remaining, I guess it will disappear soon too.

Any ideas whats going on and what to do? ;)

P.S. just for the record, also tried ncftpput and it died exactly after 10 successful file transfers, 10 being the number of connection allowed :/

---

### Post by robsoles on 2011-02-01
Can you confirm that you ran the command in Ubuntu 10.04 or Ubuntu 10.10 ?


Are you really telling me that you opened FileZilla (or any FTP program) while the command I gave you was active in terminal, with the -n (numeric, don't resolve  addresses) -W (don't truncate addresses) and -c (do it continuously), and you got no output in terminal whatsoever?

---

### Post by robsoles on 2011-02-01
Sorry, still asleep when I posted directly above this post. It will be the grep portion of the syntax if you didn't get the IP address of the host you are connecting to and replace the purple text, in my first post with the command, with it.

For the command to work in the format that I gave you you need to get the IP address of the host in question:```
user@host:~$ nslookup www.example.com
Server:  <omitted>
Address:  192.168.203.249

Non-authoritative answer:
Name:    www.example.com
Address:  192.0.32.10

user@host:~$ netstat -n -W -c | grep 192.0.32.10
```

When used this way you need to wait till you have no connections to the host you are 'wondering about'.

---

### Post by Sejanus on 2011-02-01
Ubuntu 10.04

My bad. With an IP adress it apparently works. Though I am not sure what to make of it since I dont know what's the expected behavior. 

I am getting lines printed continuously, like this: 

**tcp        0      0 xxx.xxx.x.xxx:[COLOR="Red"]38038[/COLOR]     xx.xx.xx.xx:50359       TIME_WAIT**

TIME WAIT part is occasionally substituted with FIN_WAIT2 or ESTABLISHED. This is after I started real transfers. Until then it was only ESTABLISHED. 

Number in red varies. A lot. Now sorry for nubish question but how shall I know how many connections at the time it represents? New lines like the one above were produced continuously, if every line represents new connection that would be one hell of connections.

---

### Post by robsoles on 2011-02-02
Yeah, it is the painful feature of running netstat continuously while grep'ing an IP address - no separator between iterations.

If you wait till it's "dead" and then start more than 1 connection to 'ip address' then you should see a slight pause between iterations/repeats.

Please switch FileZilla to passive mode and try solely with FileZilla - it is the one with which I am at least a bit familiar, I expect that in passive mode with only 1 concurrent connection it will not make more than two connections - I should positively test it myself using the instructions I've given you, back soonish ;)

---

### Post by lavinog on 2011-02-03
Isn't gvfsd-ftp for mounting ftp shares?
```
tcp       69      0 sejanus.home:33802        myftpadress.inquestion.:ftp CLOSE_WAIT  2670/gvfsd-ftp  

```

Do you have an icon on your desktop for the server?
If so unmount it.

---

### Post by Sejanus on 2011-02-07
Sorry, I was away for the weekend. 

No I don't have anything on my Desktop, I do have icon in Places (the menu @ top left of the screen). Not sure if it's the same thing for practical purposes, but I have had this problem even before I mounted FTP there. All right, I just umounted it, whats next? ;)

---

