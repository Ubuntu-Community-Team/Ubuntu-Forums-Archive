---
title: "School network issues."
date: 2009-02-03
forum: New to Ubuntu
---

### Post by darkwalt on 2009-02-03
Hi all.  I bought a netbook to use at school, and I've been having issues connecting to the wireless network.  Well, more specifically, the issue isn't connecting, but getting any internet access from the connection.  Other people with windows laptops are able to get internet access, and I can get internet access via wireless perfectly at my house.  Does anybody else know of a way to fix this or check this out?

---

### Post by kestrel1 on 2009-02-03
It is possible that the school is using a proxy server. You need to speak nicely to the network manager or tech support for the correct proxy settings.

---

### Post by avtolle on 2009-02-03
I've a feeling that your school is using an authentication routine on its network that is set up for Windows and Applw OS, but isn't Linux friendly. You're going to need to see if the school's IT folks will give any help to you with this routine (chances are, you won't). You also need to find out, if you can, what scheme your school is using for authentication of users on its network to see if there is a workaround for Linux.

---

### Post by darkwalt on 2009-02-04
Is there a way to check through virtualization?

---

### Post by darkwalt on 2009-02-05
> **darkwalt said:**
> Is there a way to check through virtualization?

Bump.

---

### Post by Virtualboxbuntu on 2009-02-05
> **darkwalt said:**
> Is there a way to check through virtualization?

That wouldn't work, because virtualization doesn't use your internet connection directly, it relies on the host (Linux) already being connected, then passes that connection to the guest (Windows).

Your school might be using a proxy server or something of the sort. Talk to your school's IT person about how the network is set up. Beware that they probably can't help you with configuring it on your Linux computer beyond giving you information about the proxy.

---

### Post by darkwalt on 2009-02-05
Is there a way to view the options in windows and set up ubuntu to mimic it.

---

### Post by bukwirm on 2009-02-05
Does your school have some web page with information about how to use the wireless network? If you give us a pointer to that, somebody might be able to help you adapt the instructions.

---

### Post by darkwalt on 2009-02-06
This has been the only page i've been able to find.

[html]http://www.palomar.edu/atrc/[/html]

---

### Post by newbee70 on 2009-02-06
> **darkwalt said:**
> This has been the only page i've been able to find.

[html]http://www.palomar.edu/atrc/[/html]

take a look at this screen shot, it may help.

---

### Post by jimv on 2009-02-06
This page says that the wireless access is not secured at all:

[http://www.palomar.edu/ATRC/wireless/support.htm](http://www.palomar.edu/ATRC/wireless/support.htm)

So it's rather odd that your connection isn't working.

---

### Post by kestrel1 on 2009-02-06
Why don't you just ask IT support for help. We are not all ogres.
I am a network manager & help any of the users if I can. Most IT support should have some knowledge of linux.
I doesn't hurt to ask.

---

### Post by darkwalt on 2009-02-06
> **newbee70 said:**
> take a look at this screen shot, it may help.

Well, i'm using firefox 3 and all of the computers in the school are using firefox 3 as well.  I'm sorry, but I fail to see how that helps me.

---

### Post by darkwalt on 2009-02-06
> **kestrel1 said:**
> Why don't you just ask IT support for help. We are not all ogres.
I am a network manager & help any of the users if I can. Most IT support should have some knowledge of linux.
I doesn't hurt to ask.

Yeah, I emailed the the closest thing that I can find to the IT department, and I talked to one of the network admins in a networking class, and he said that he didn't know enough about linux to be of any help.  Tomorrow i'm going to go to the main office and see if I can get anybody to help me find the IT department there.

---

### Post by kestrel1 on 2009-02-06
Even if they don't know about Linux , they should still be able to tell you what the settings are.
In my job, I find it useful to know a bit about all OS's, as we have MAC's, PC's & even some very old Acorn Risc machines.
Linux is more of a hoby, but I also have found a certain knowledge of it very useful.

---

### Post by darkwalt on 2009-02-06
> **kestrel1 said:**
> Even if they don't know about Linux , they should still be able to tell you what the settings are.


Ok.  Can you tell me what I should be asking them for?

---

### Post by kestrel1 on 2009-02-06
Ask them if they are using a proxy server to connect to the Internet & if so what is it's IP address & port number.
They may also be using a .pac (Proxt Auto Config) file. You would need to know what it's name is a the full path to it's location i.e. [http://netserver/pacfiles/internet.pac](http://netserver/pacfiles/internet.pac)
Once you know that it is easy to put in to Firefox.
If they are using neither of those, what are they using?

---

### Post by darkwalt on 2009-02-06
IT department was closed.  I sent an email and should get a response by tuesday.

---

### Post by bukwirm on 2009-02-06
newbee70, Blackboard has absolutely nothing to do with Internet access - and it works fine with Firefox 3 on Ubuntu, anyway (I have to use it at school too).

Since you said you could connect to the network, but couldn't use the Internet, and if you're not using a proxy server, I'd suspect a DNS problem - some routers don't give DNS server information when using DHCP and Linux. Try entering the IP address "128.211.240.17" in a browser - that should take you to my website. Let us know what happens.

---

### Post by ugm6hr on 2009-02-07
> **bukwirm said:**
> some routers don't give DNS server information when using DHCP and Linux. 

I think I fell foul of this when staying at a hotel recently (also using a netbook).

Unfortunately, I have yet to find a solution.

---

### Post by bukwirm on 2009-02-07
You should be able to set DNS servers permanently for DHCP by following the instructions [here]("http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html").

---

### Post by ugm6hr on 2009-02-07
> **bukwirm said:**
> You should be able to set DNS servers permanently for DHCP by following the instructions [here]("http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html").

The official instructions are here: [https://www.opendns.com/smb/start/device/ubuntu](https://www.opendns.com/smb/start/device/ubuntu)

But this does not seem to work in all situations - the router itself still interferes somehow.

See my explanation here: [http://ubuntuforums.org/showthread.php?t=1063064](http://ubuntuforums.org/showthread.php?t=1063064)

---

### Post by darkwalt on 2009-02-08
> **ugm6hr said:**
> The official instructions are here: [https://www.opendns.com/smb/start/device/ubuntu](https://www.opendns.com/smb/start/device/ubuntu)


Quick questions.  Can I do that now or do I have to wait until i'm at the site?  Also, are there any more steps after that because it's giving me a registration page.

---

### Post by ugm6hr on 2009-02-08
> **darkwalt said:**
> Quick questions.  Can I do that now or do I have to wait until i'm at the site?  Also, are there any more steps after that because it's giving me a registration page.

You can do it now.

You don't have to register - Step 1 is all that is required.  Registering potentially allows content filtering, aliases etc, but requires you to provide your IP (i.e. is a pain unless you have a fixed IP).

---

### Post by darkwalt on 2009-02-08
Ok, a bit of a problem following your instructions ugm6hr.  After following the directions to do stuff in the terminal, nothing happens.

---

### Post by ugm6hr on 2009-02-09
If you use Intrepid, Number 1 won't work (but is unnecessary anyway).

I don't use Intrepid, but they removed network-admin (apparently).

I believe the Terminal commands to maintain the changes permanently will work anyway.

If nothing happens - copy and paste what you type and the responses you get back here.

---

### Post by darkwalt on 2009-02-09
Ok, here is what I typed in terminal and for some odd reason it's not letting me attach a copy of the dhclient file.  I guess i'll just put it here.

```
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```

---

### Post by ratmandall on 2009-02-09
EDIT:```
Delete me.
```

---

### Post by ugm6hr on 2009-02-09
Well it seems everything worked fine.

Reboot, and you should find that you are now using OpenDNS.

You can check by going to the OpenDNS website - look in the top right corner - it should tell you if you are using their service.

Give it a try and see.  As I said, it may not make a difference to browsing.

---

### Post by darkwalt on 2009-02-09
Ok, now all of a sudden the laptop is getting as far as the boot screen, then shutting down.  I tried booting into safe mode and the same thing happens.  I'm going to reinstall ubuntu and see if that opendns thing caused the problem.

---

### Post by ugm6hr on 2009-02-10
Can't see how the OpenDNS edits have caused this.

PS: there is a apparently a GUI solution for OpenDNS in Intrepid [http://geminianeyes.com/?p=2697](http://geminianeyes.com/?p=2697)

---

### Post by sharon.gmc on 2009-02-10
Just approach your network administrator or the IT expert and they will help you with your school network problems

---

### Post by darkwalt on 2009-02-10
> **sharon.gmc said:**
> Just approach your network administrator or the IT expert and they will help you with your school network problems

Yeah, tried that.  One of them didn't know enough of the linux operating enviroment.  I've emailed the school and they haven't sent me a response.

Also, to ugm6hr, I just reinstalled and did the dhcp3 edit and nothing so far.  Confused as to why the hd would corrupt like that.  Glad I kept backups.

---

### Post by darkwalt on 2009-02-10
> **bukwirm said:**
> Try entering the IP address "128.211.240.17" in a browser - that should take you to my website. Let us know what happens.

Bukwirm was right in that reguard.  IP addresses worked.  I tried using both implementations of opendns, both stand-alone and together, and I got no results in terms of browsing.  I just got an email address from an IT guy in the school, so i'm going to hit him up after I get out of class.

---

### Post by ugm6hr on 2009-02-10
Clearly a DNS issue.  As mentioned, it is likely your school's router is not behaving correctly with Linux & DHCP, since OpenDNS should resolve it in all other circumstances.

I am looking at how the /etc/nsswitch.conf file interacts with dns lookups, but don't fully understand it.

This line:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

If you have a similar [NOTFOUND=return] - try deleting it (or changing to  [NOTFOUND=continue] - I think that may work.  Or try putting dns at the start of the line.

Worth trying (make a backup of the file first).

---

### Post by darkwalt on 2009-02-10
Odd query.  I was looking up the ip address for opendns.com, and when I put the ip address in the browser, it doesn't show me as using opendns.  When I just hit up opendns.com it shows me as using it.

---

### Post by sandyd on 2009-02-10
[FONT=monospace]nvm...
[/FONT]

---

### Post by redseventyseven on 2009-02-10
Complete shot in the dark, but when I had trouble with getting on to my university's wireless network, the solution was to disable TCP window scaling.

See [http://wheel.troxo.com/2008/06/05/tcp-window-scaling-conundrum/](http://wheel.troxo.com/2008/06/05/tcp-window-scaling-conundrum/) for details.

---

### Post by darkwalt on 2009-02-10
> **redseventyseven said:**
> Complete shot in the dark, but when I had trouble with getting on to my university's wireless network, the solution was to disable TCP window scaling.

Sorry, that's not it.  I was able to connect to web pages via ip addresses.

---

### Post by darkwalt on 2009-02-17
> **ugm6hr said:**
> 
This line:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

If you have a similar [NOTFOUND=return] - try deleting it (or changing to  [NOTFOUND=continue] - I think that may work.  Or try putting dns at the start of the line.

Ok, so continue didn't work.  Where exactly would I put in that dns?

---

### Post by ugm6hr on 2009-02-17
> **darkwalt said:**
> Ok, so continue didn't work.  Where exactly would I put in that dns?

Something like this:

```
hosts:          dns files
```

---

### Post by darkwalt on 2009-02-21
Nope.  That didn't do anything either.  Where do I go from here?

---

### Post by darkwalt on 2009-02-23
Bump.

Anybody?

---

### Post by blazemore on 2009-02-23
I had this issue.

It turned out to be an ISA server.

---

### Post by darkwalt on 2009-02-23
> **blazemore said:**
> I had this issue.

It turned out to be an ISA server.

Ok, did you ever find a fix?

---

### Post by Vince4Amy on 2009-02-23
> **darkwalt said:**
> Ok, did you ever find a fix?

You'd need to reconfigure the ISA Server, speak to your Administrator.

---

### Post by blazemore on 2009-02-23
Oh hey Vince

---

### Post by The Cog on 2009-02-23
If you can connect to websites by ip address then it is definitely a DNS problem. You need to find out the IP address of their DNS server and put that in /etc/resolv.conf with a line like this:
> nameserver 192.168.1.1
You could ask a classmate to run **ipconfig /all ** on windows and see if that tells you, or perhaps run the command **route** to get the address of the default gateway and try using that as your DNS server, just in case that's it.

---

### Post by darkwalt on 2009-02-23
Would it be possible to use the GUI version instead?

---

### Post by Vince4Amy on 2009-02-24
> **The Cog said:**
> If you can connect to websites by ip address then it is definitely a DNS problem. You need to find out the IP address of their DNS server and put that in /etc/resolv.conf with a line like this:

You could ask a classmate to run **ipconfig /all ** on windows and see if that tells you, or perhaps run the command **route** to get the address of the default gateway and try using that as your DNS server, just in case that's it.

That's what we did, but the ISA Server still denied access.

---

### Post by The Cog on 2009-02-24
GUI version of what?

P.S. If you run route on windows, it's **route print**. On Linux it's just **route**. But **ipconfig /all** on Windows will tell you what address the DNS nameserver is so this is the best bet.

When you put that line in /etc/resolv.conf, remove any other nameserver lines, or make sure the new line is the first one. You can use these commands to edit it:
> sudo cp /etc/resolv.conf /etc/resolv.conf.backup
gksu gedit /etc/resolv.conf


> That's what we did, but the ISA Server still denied access.
Maybe, but then this is a different problem. In this case, he can connect to websites by IP address, just not by name (he said so), so it's not an authentication problem with the ISA.

---

### Post by darkwalt on 2009-02-25
Yep.  Did everything, and apparently anybody else who is using linux on the two campuses is having a problem.  Apparently there was recently a server change that recently caused all linux distros being used on the school campus to have the same problem as me.  Apparently, they're "working on it", but since linux users are such a small part of the campus community, I doubt that they're going to do anything.  Not sure whether or not to mark this thread solved or not.

---

