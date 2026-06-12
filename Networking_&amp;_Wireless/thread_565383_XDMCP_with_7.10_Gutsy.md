---
title: "XDMCP with 7.10 Gutsy"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by RoyalPro on 2007-10-02
I just upgraded both my media/mythtv Ubuntu 7.04  and Vmware Ubuntu 7.04 to 7.10.  I have been using the VMware one to XDMCP to the meida one.  After the upgrade I haven't been able to connect to the media pc and when I tried to go from the media to the VM one I can't connect either.  I see the list show up when I try to connect and I have tried typing the ip in too, but neither of them connects.  When I try to connect I get the screen that showed up before and after a connection, but it just flashes black in between the two of them with the black X cursor in the middle of the screen and then goes back to the login on the client.  Is it some security setting that has changed during the upgrade?  Sorry if this isn't the best explanation, but have been up all night trying to figure this out.  Let me know if you need any more info.

---

### Post by RoyalPro on 2007-10-02
Wow so far 32 reads and no one saying hey you just need to do this or that.
I have tried turning it off and back on.  I have put the accessing IP's in host.allow.  I have edited the gdm.conf.  I have installed Firestarter and tried it with privileges and while it is disabled.

---

### Post by kalarr on 2007-10-02
I have a similar problem. I installed Gutsy on a machine to test whether I could upgrade my server at a later point. I setup XDMCP as I have several older computers that act as simple thin clients running a base Linux and minimal GNU with only X installed (no desktop) that use XDMCP to connect to the server to run an Xfce session.

I also use this machine remotely across VPNs for myself and my family as a central location for when we're away from home. A simple USB memory stick with Linux, PoPToP and X on it allows for simple access to the normal home apps and environment used by simply booting a remote computer connected via broadband off the USB stick. Its neither fast, nor elegant, but it works.

After enabling XDMCP on the Gutsy machine, and getting it all setup to accept both direct (-query) and indirect requests from the clients the machines will see the server in the Chooser, however when connecting they get only a black blank screen with the old X11 "X" cursor showing on the screen. There is no greeter from the server and no way short of killing the X session (Ctrl-Alt-Backspace) to disconnect or stop the connection attempts.

When trying to investigate this further on the server side of things to see where it might be dropping, there is nothing showing up in the X.org logs of the server and as far as the client is concerned, its making the attempt without too much hassle.

Running a netstat shows that XDMCP is listening on IPv6 ports, X11 is listening on TCP6 ports and XDMCP is listening on UDP6 ports, but neither are listening on IPv4 ports. Kind of fundamental given my network currently runs on a 192.168.x.x/24 network and there are no plans to upgrade to IPv6 at the present time. Simply no need for it yet.

Looking through the GDM configuration, there is nothing in there that says "only listen on IPv6" or to not listen on IPv4. It should be listening on all interfaces and all available/supported protocols. I'm assuming it is given netstat says SSH is only on TCP6, but I can still connect to it via IPv4.

There are no iptables/netfilter rules blocking this. The machine is inside a trusted network. There are no hosts.allow or hosts.deny rules that are blocking this either.

This problem is a deal breaker. Without XDMCP for the clients (mostly very old machines too slow to run a full X environment locally) I will not be able to consider Gutsy. I refuse to consider VNC a viable alternative when there are multiple client computers connecting to the server at any one time (locally or remotely across a VPN.)

If anyone has some suggestions, I'd also very much appreciate hearing them.

Here is the netstat -ap output for IP sockets. XDMCP is only one aspect I'm intending to test on this machine before upgrading to Gutsy, so yes there are other applications instaled. Ultimately, I need remote X working. I'm at a loss as to why its not. I'm tempted to try something like KDM or even revert back to XDM to see if this is a GDM problem or something with X.org itself. I'd rather not though. I like the simplicity of GDM.

```

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 localhost:mysql         *:*                     LISTEN     -                   
tcp        0      0 localhost:ipp           *:*                     LISTEN     -                   
tcp        0      0 *:3128                  *:*                     LISTEN     -                   
tcp        0      0 *:1723                  *:*                     LISTEN     -                   
tcp6       0      0 *:5900                  *:*                     LISTEN     5593/vino-server    
tcp6       0      0 *:x11                   *:*                     LISTEN     -                   
tcp6       0      0 *:www                   *:*                     LISTEN     -                   
tcp6       0      0 *:ssh                   *:*                     LISTEN     -                   
udp        0      0 *:32769                 *:*                                -                   
udp        0      0 *:32770                 *:*                                -                   
udp        0      0 *:icpv2                 *:*                                -                   
udp        0      0 *:bootpc                *:*                                -                   
udp        0      0 *:mdns                  *:*                                -                   
udp6       0      0 *:xdmcp                 *:*                                -                   

```

Essentially, the current version of this machine that is running live is setup on Dapper (6.06) and effectively emulates the functionality a Windows 2003 SBS terminal server with Zimbra instead of Exchange.

 I want to migrate to 7.10 for multiple reasons, but one of the prime reasons being several of the drivers that are supported by default in Gutsy for some new kit I am intending to get, I have to compile by hand in Dapper, Edgy and Feisty. So being the lazy me, I'd build a new server running Gutsy and then just copy the configs and home directory over from the existing server. Makes things a lot easier and would probably work out faster instead of having to compile/debug drivers myself.

---

### Post by RoyalPro on 2007-10-03
Well thanks for your input and it does look like it is a ipv6 thing.  I have been looking to install or enable ipv6 and have had no luck in figuring that out to see if it works with ipv6.  I liked the XDMCP the way it was because it was simple and worked good.  Security isn't too much of an issue with me as I am behind a good firewall and don't connect to it from out side the lan.  I will keep trying and still looking for suggestions.

---

### Post by RoyalPro on 2007-10-05
I don't know what it was but after applying the latest updates it started working.  I still have my accessing computers in hosts.allow and in my firestarter, but they were there before when it didn't work but now all seems to be good.

---

### Post by RoyalPro on 2007-10-08
After another update it is back to the way it was before(not working that is).  What is up with just leaving it working?

---

### Post by RoyalPro on 2007-10-09
Many more updates after the last the made it stop working again and it is still not working.  Still have the ip's in the hosts.allow and firestarter.  I can log in fine with ssh and my mythtv frontend.  It was so simple before to change setting and get updates and the like by XDMCP-ing into the box but now I have to bring the box out and connect a keyboard/monitor/mouse to changed anything.  Gutsy sucks so far.  I like the new kernel, but that is about it.

---

### Post by RomeoJava on 2007-10-10
I have experienced this too.

I have two machines, first I upgraded one to Gusty and left the other as Feisty. With this setup the Feisty machine could be used to control the Gusty machine but not the other way around. I then installed Gusty on the other machine and now neither way will work. I therefore assume the problem is probably on the side of the machine initiating the connection, rather than the other way around. By the way I have Nvidia cards using Restricted drivers and am using Compiz on each which may be related? As a side note my feisty machine was not running Compiz yet when controlling the Gusty with Compiz all the effects were there which was weird but really cool!

Rj

---

### Post by RomeoJava on 2007-10-10
The daily updates didn't resolve this so I had a look at my syslog and these three entries looked relevant. Maybe this may help somebody understand our problem:

Oct 10 18:55:01 localhost gdmchooser[5284]: GLib-GObject-WARNING: /build/buildd/glib2.0-2.14.1/gobject/gsignal.c:1019: unable to lookup signal "activate" of unloaded type `GtkMenuItem'

Oct 10 18:55:07 localhost gdm[5111]: WARNING: gdm_cleanup_children: child 5288 crashed of signal 11 

Oct 10 18:55:07 localhost gdm[5111]: WARNING: gdm_cleanup_children: Slave crashed, killing its children

Rj

---

### Post by RoyalPro on 2007-10-11
You are so right.  I installed Feisty on a VM and it connects just fine, while both 32 and 64 bit version of Gutsy as clients fails to load.  Well now I can turn my efforts away from the server side and look at what is stopping the Gutsy clients from working.

---

### Post by RoyalPro on 2007-10-14
Well I had been using Feisty successfully as the client and gutsy as the server but after a few updates on both of them it has stopped working.  I did a clean install of Feisty on my VM thinking that it was the update that it got that caused the problem but now The base Feisty don't work as the client either.  I am going to start looking for another way to do it but the XDMCP was built in and was so simple to use before.  :-(  4 Days left for the full release and it don't look like the XDMCP will be working with Gutsy.

---

### Post by Aearenda on 2007-10-18
I have just come across this (or a very similar) problem with an Edubuntu terminal server, where the thin clients fail to connect using XDMCP now that I have updated to the latest Gutsy (this is NOT a standard Edubuntu LTSP setup - I have really old terminals and still use LTSP 4.2). They worked fine with Tribe 5. The error messages I see are the same as quoted in this thread. I have found that setting the remote greeter to be the 'plain with facebrowser' one instead of 'Same as local' works around the problem. This may help some others struggling with this issue.

---

### Post by PaulHuffman on 2007-10-18
How do you enable XDMCP on a Feisty machine?  Maybe that's all I'm missing:  [http://ubuntuforums.org/showthread.php?t=225898&page=2]("http://ubuntuforums.org/showthread.php?t=225898&page=2")

---

### Post by Aearenda on 2007-10-19
PaulHuffman: To enable remote login, on your target machine go to the Login Window tool under System->Administration, move to the 'Remote' tab and change the 'Style' setting to anything other than 'Remote login disabled'. Then restart GDM (simplest and surest way is to reboot, but you can do it by logging out, then logging in to a console session and running 'sudo /etc/init.d/gdm restart' - but if this is meaningless to you, just reboot). 

Note 1: You shouldn't do this on any machine that is open to the Internet, it isn't safe.
Note 2: Best way to test is to install xnest on your local machine, and then use the Terminal Server client to connect to your target machine selecting XDMCP as your protocol.

---

### Post by PaulHuffman on 2007-10-19
I guess I've done that already, made the change in the Remote tab. Still XDMCP with either Xming or Reflection X only gets me as far as gmgreeter.  I'm just trying to window the linux box like I do with my Solaris box from my XP box because the XP box is closer to the heater and the good speakers.  I'm getting good enough results with Xming in one window mode, no launch, and a putty ssh starting gnome-session. Maybe this is more secure as well.  

I haven't tried xnest but it looks like fun.

---

### Post by RoyalPro on 2007-10-19
Well after changing to plain face I am now able to login with 7.04.  Will try 7.10 in just a a few min.

---

### Post by trikke on 2007-10-22
same problem here
the server with xdmcp is listed but i cant connect to it
screen flickers few time then i come back to the gdm screen to login

anyone found the solution yet ?:confused:

---

### Post by Marcel Meijer on 2007-10-23
I just bypassed the problem by selecting:
System -> Administration -> Login Window -> Tab Remote style plain (the third choice)

This option gives me a login window on my terminal client Cygwin/X.

---

### Post by surajvijayan on 2007-10-23
I had problems remote logging into Gutsy via XDMCP. Realized this is a GDM bug. I replaced GDM with KDM and enabled remote login on KDM. This worked. Posting the steps I did below, might help someone:

# apt-get install kdm

Edit /etc/kde3/kdm/kdmrc

Make sure entries shown below are there in this file:

[Xdmcp]
# Whether KDM should listen to incoming XDMCP requests.
# Default is true
Enable=true
# The UDP port on which KDM should listen for XDMCP requests. Do not change.
# Default is 177
Port=177

Edit /etc/kde3/kdm/Xaccess

Make sure the following line in uncommented:

*                                       #any host can get a login window

Make sure /etc/X11/default-display-manager contains: /usr/bin/kdm


Reboot and login via KDM..

---

### Post by timothyyip on 2007-10-25
> **surajvijayan said:**
> I had problems remote logging into Gutsy via XDMCP. Realized this is a GDM bug. I replaced GDM with KDM and enabled remote login on KDM. This worked. Posting the steps I did below, might help someone:

# apt-get install kdm

Edit /etc/kde3/kdm/kdmrc

Make sure entries shown below are there in this file:

[Xdmcp]
# Whether KDM should listen to incoming XDMCP requests.
# Default is true
Enable=true
# The UDP port on which KDM should listen for XDMCP requests. Do not change.
# Default is 177
Port=177

Edit /etc/kde3/kdm/Xaccess

Make sure the following line in uncommented:

*                                       #any host can get a login window

Make sure /etc/X11/default-display-manager contains: /usr/bin/kdm


Reboot and login via KDM..

Hi,

Both need to be kdm to login or just the host?

---

### Post by surajvijayan on 2007-10-25
You just need to change the Display Manager on the host to KDM from GDM, Once this is done, You can login to Ubuntu Gutsy from any XDMCP compliant source (Xming, HummingBird.. on Windows). 

Please note only the Display Manager is being changed, you will still be logging into to 'GNOME' session on Gutsy.

---

### Post by surajvijayan on 2007-10-25
You just need to change the Display Manager on the host to KDM from GDM, Once this is done, You can login to Ubuntu Gutsy from any XDMCP compliant source (Xming, HummingBird.. on Windows). 

Please note, only the Display Manager is being changed, you will still be logging into to 'GNOME' session on Gutsy.

---

### Post by filosofix on 2007-11-02
I have a home/media/server with gutsy installed and a computer with gutsy which I try to connect to the server with xdmcp. This is not working with gdm, so when i change from gdm to kdm on my computer it works fine.

Thats great, but if i want to swith user and log in on my local computer I'm told gdm is not running and therefore unable to switch user. (I'm running a gnome session (local&server) so I guess gdm _should_ be running or am I running a gnome session on the kdm?)

 Is it possible doing a userswitch using the kdm with a gnome session?

---

### Post by wankel on 2007-11-05
Yeah! Mine is working again :-)

It turns out the cause of my problem was not entirely as in the rest of the thread, nonetheless it has pointed me in the right direction. Thanks all :-)

In case someone else is having a problem identical to mine, I'll post my situation and solution:

"Infrastructure":
A. Remote          - Edgy 6.06/LTS Edubuntu+Kubuntu mix, KDM
B. Local OK        - Gutsy 7.10 Kubuntu, clean install, KDM
C. Local, not OK  - Feisty-became-Gutsy 7.04/7.10 broken upgrade, KDM

B -> A OK
C -> A not OK (chooser OK, screen flashes to local shortly, then black with "old-school" X-cursor, after time-out back to local). Aaargh.

Way to solution
- All configuration seemed ok
- Checked whether I was not secretly using GDM on "A", turned out KDM indeed
- Reconfigured to use GDM (unsuccesfully)
- Checked remote "A"'s /var/log/kdm to no avail
- Checked local "C"'s /var/log/kdm, found this 169.x.x.x IP not responding
- Checked my active network interfaces (wifi0 and eth1)
- Brought eth0 down: sudo ifdown eth0
- Try logging in remotely, with succes

All in all, it *should* have taken less time :-)

---

### Post by RoyalPro on 2007-11-06
I haven't messed with it for a while.  I've using old feisty to login with plain face.  I am going to try the kdm thing, but before I do I got this error trying to login gutsy gdm to gutsy gdm.  

"Not starting X display manager (xdm): it is not the default display manager."

Well to edit this I am able to login if I have use kdm on the client machine of gutsy.  It is still with plain face and I am going to try the same as local.

---

### Post by dfme on 2007-11-15
hello,
i have stumbled into the same problem: xdmcp not working even when enabling remote login in gdmsetup (this seems to be a bug??).

to fix this problem edit the gdm.conf file as follows:
sudo gedit /etc/gdm/gdm.conf

find the [xdmcp] entry and enable xdmcp by setting:
Enable=true

Edit: Don't forget to restart your system

now you should be able to remote login

greets

---

### Post by hftb on 2007-11-15
Thank you, thank you, thank you!
I too was having problems logging in via xdmcp on Gutsy, and your little trick worked like a charm.  Thanks again!

Rob.

---

### Post by orbister on 2007-11-20
I've read this thread with interest, but I'm still having no luck with this. I went into gdm.conf and set 

[xdmcp]
enable=true

but when I try to do a remote login I get a bit of a flicker and then back to the local machine. I installed xnest and can get in via Terminal Server Client with xdmcp no problem.

Any bright ideas gratefully received.

Local (10.0.0.7) and remote (10.0.0.8) are both spang-up-to-date gutsies.

Ian

---

### Post by mrtisoy on 2007-11-21
I am also still having problems. Two machines, both Gutsy, one AMD64, the other 32bit, 192.168.0.1/24 lan.

There seem to be a lot of different gdm.conf and gdm.conf-custom files floating around.

I can see my machines in chooser, but when I try to connect then the screen flashes twice and then it takes me back to the local greeter.:confused:

---

### Post by mrtisoy on 2007-11-21
I found a work around that works for me.

It is on Post #3 at [http://ubuntuforums.org/showthread.php?t=605976](http://ubuntuforums.org/showthread.php?t=605976)

---

### Post by JoseArmandoJeronymo on 2007-12-14
Regarding XDMCP, a patch was created and tested: please see [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/150193](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/150193) for details.

---

### Post by Nurkee on 2008-01-07
As per this link: 
[http://utcc.utoronto.ca/~cks/space/blog/linux/IndirectXdmIPv6Bug](http://utcc.utoronto.ca/~cks/space/blog/linux/IndirectXdmIPv6Bug)

add

LISTEN 0.0.0.0

to /etc/kde3/kdm/Xaccess file anywhere after the comments and this will force kdm to listen on IPv4.

---

### Post by PaulHuffman on 2008-01-10
Can't find an Xaccess in my installation, 7.04 Feisty. Not at /etc/kde3/kdm  or at /etc/X11/xdm as in Chris' Wiki

---

### Post by Nurkee on 2008-01-11
Maybe kubuntu-desktop isn't installed properly. Try apt-get install kubuntu-desktop again.

---

### Post by d4ljoyn on 2008-01-14
That patch doesn't work on gutsy as far as I can tell -- I downloaded it and the first problem is it doesn't compile -- gdm-log.h must be included in daemon/verify-shadow.c.  So I fix that and build/install/restart -- no gdm at all.

---

