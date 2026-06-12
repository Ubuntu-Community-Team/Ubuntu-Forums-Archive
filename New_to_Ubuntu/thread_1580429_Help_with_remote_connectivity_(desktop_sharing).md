---
title: "Help with remote connectivity (desktop sharing)"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by duruttye on 2010-09-23
Hey there!

I installed ubuntu 10.04 on my parents pc, and I need help to help them.

They are really normal users, but they have no knowledge about anything regarding the pc, so, in most cases, just to watch a movie we talk for hours to get VLC installed, or just to make a spreadsheet of somekind.

My question is, how can I make them (on the) phone to allow access to me via Remote Desktop, and what other information do I have to know about the Remote Desktop application.

The idea is, to make them click a few things and to send me a link where I will be able to access their pc, or any ideas.

I have never used the Remote Desktop before, so I can't even identify any problems with them on the phone :)

Thank you very much :)
:guitar:

---

### Post by acreech on 2010-09-23
I have found this is the easiest way to remote connect. 

[HTML]http://www.teamviewer.com/index.aspx[/HTML]

it has to be installed on both computers and then an account set up on both computers. The application needs to be running and it gives you a user name/password to share with who you want to connect with. Then you can get into their computer. 


acreech

---

### Post by Jazzy_Jeff on 2010-09-23
> **acreech said:**
> I have found this is the easiest way to remote connect. 

[HTML]http://www.teamviewer.com/index.aspx[/HTML]

it has to be installed on both computers and then an account set up on both computers. The application needs to be running and it gives you a user name/password to share with who you want to connect with. Then you can get into their computer. 


acreech

Looks a little expensive to me.

---

### Post by BobVila on 2010-09-23
Teamviewer is free for personal use...

---

### Post by Jazzy_Jeff on 2010-09-23
> **BobVila said:**
> Teamviewer is free for personal use...

Cool, glad to hear it.

---

### Post by sydbat on 2010-09-23
> **acreech said:**
> I have found this is the easiest way to remote connect. 

[HTML]http://www.teamviewer.com/index.aspx[/HTML]

it has to be installed on both computers and then an account set up on both computers. The application needs to be running and it gives you a user name/password to share with who you want to connect with. Then you can get into their computer. 


acreechOr, the OP could simply go to Applications > Internet > Remote Desktop Viewer on his box, and tell his parents (over the phone) to go to System > Preferences > Remote Desktop and configure it. The only thing his parents have to do then, is open a Terminal and type in ifconfig to get the IP address so he can connect. 

No visiting untrusted websites to download unknown software. This isn't Windows.

---

### Post by pricetech on 2010-09-23
Have them install Open SSH Server; System - Administration - Synaptic Package Manager.  Search for openssh server and install it.  Then have them reboot.

Configuring Port Forwarding in their router is another story.  How you do that depends upon the router.  I would not attempt to have them set a fixed IP on the computer, but rather have them set up a reserved IP in the router while their configuring it, assuming of course their router supports such a thing.

Once you have SSH and Port Forwarding set up, the rest should be easy.

Have fun.

---

### Post by acreech on 2010-09-23
> **sydbat said:**
> Or, the OP could simply go to Applications > Internet > Remote Desktop Viewer on his box, and tell his parents (over the phone) to go to System > Preferences > Remote Desktop and configure it. The only thing his parents have to do then, is open a Terminal and type in ifconfig to get the IP address so he can connect. 

No visiting untrusted websites to download unknown software. This isn't Windows.

I have tried to use remote desktop several times and have had no luck at it. I can connect in a local network, but not to an external IP. 

When you open up the remote viewer you can use VNC or SSH protocal. Is Host where you put the IP? On SSH there is a username at the bottom. 

I know there is a way to make this work, but I have never figured it out.

---

### Post by sydbat on 2010-09-23
> **acreech said:**
> I have tried to use remote desktop several times and have had no luck at it. I can connect in a local network, but not to an external IP. 

When you open up the remote viewer you can use VNC or SSH protocal. Is Host where you put the IP? On SSH there is a username at the bottom. 

I know there is a way to make this work, but I have never figured it out.Yes, "Host" is where you put the IP. I use this all the time to connect remotely to client boxen. And VNC gives you their desktop, while SSH gives you their file system via terminal.

---

### Post by duruttye on 2010-09-23
Okay, thank you all for your replies.

I think I can make them start the Remote Desktop application and make the pc be shared and I can make them find out their IP address, but they are behind a modem, which I think has another IP address, the pc will be something like: 192.168.0.X and the modem will be something else.

In case I can find out both of them, what do I have to do to see their desktop? :)

Will it be something like 192.168.0.X@modemIP and where do I put that??

Another thing: my remote dessktop application says that my desktop is only reachable over the local network. If their will says the same, what then?

Thank you :)

---

### Post by sydbat on 2010-09-23
> **duruttye said:**
> Okay, thank you all for your replies.

I think I can make them start the Remote Desktop application and make the pc be shared and I can make them find out their IP address, but they are behind a modem, which I think has another IP address, the pc will be something like: 192.168.0.X and the modem will be something else.

In case I can find out both of them, what do I have to do to see their desktop? :)

**Will it be something like 192.168.0.X@modemIP and where do I put that??**

Another thing: my remote dessktop application says that my desktop is only reachable over the local network. If their will says the same, what then?

Thank you :)The bolded part - I think (don't quote me on this) the address is the IP from the router then ":" and the IP assigned by the router to the computer (or a port you set up in the router to forward to the specific computer). It goes in "Host".

So, for example, it might look like this - (external IP) xxx.xxx.xxx.xxx : 192.168.0.xxx (internal IP).

If I am wrong, can someone correct this?

---

### Post by duruttye on 2010-09-23
I'm trying like crazy to connect to them, with the command:

vncviewer {modemIP}:192.168.X.XX

but to no avail...

any ideas?

At them the Remote Desktop application is okay, it should let me connect to it...

---

### Post by spiky001 on 2010-09-23
the 192 xxx xxx ip is that internal?

---

### Post by duruttye on 2010-09-23
> **spiky001 said:**
> the 192 xxx xxx ip is that internal?

Yes, that is what the ifconfig says

---

### Post by spiky001 on 2010-09-23
you will need external ip

---

### Post by duruttye on 2010-09-23
ssh: connect to host xx.xx.xxx.xx port 22: Connection timed out
Couldn't read packet: Connection reset by peer

for the command:  sftp username@modemIP

---

### Post by duruttye on 2010-09-23
> **spiky001 said:**
> you will need external ip

The {modemIP} is the external IP, sorry :)

---

### Post by spiky001 on 2010-09-23
so you have got ssh sever installed on there pc and no firewall configuered

---

### Post by duruttye on 2010-09-23
> **spiky001 said:**
> so you have got ssh sever installed on there pc and no firewall configuered

Exactly, I made them install openssh-server and openssh-client

I'm trying to connect to the pc with the command:


ssh [email]username@xxx.xxx.xxx.xxx[/email]
ssh: connect to host xxx.xxx.xxx.xxxport 22: Connection timed out

---

### Post by acreech on 2010-09-23
I wonder if that should be the device name on the router instead of the user name

this is the problem I always run into.

---

### Post by da burger on 2010-09-23
I could well be wrong but if you use only an external ip it will connect to the router. I think you need to use port forwarding or something of the like to get around this.
Angus

---

### Post by fly-by-night on 2010-09-23
You should not advertise the IP address here - in my opinion.  You've never done this before and your folks will have NO clue who is connected to their computer. Might be you, might be Jack from down under...  

Then again I have never attempted this either so...is advertising it safe?

---

### Post by acreech on 2010-09-23
> **fly-by-night said:**
> You should not advertise the IP address here - in my opinion.  You've never done this before and your folks will have NO clue who is connected to their computer. Might be you, might be Jack from down under...  

Then again I have never attempted this either so...is advertising it safe?

I would think that is not safe. it is usually blocked out in x's

---

### Post by da burger on 2010-09-23
Your IP is not secret. Every time you connect to a web site it gets your IP. Having said that I would not advise that you shout it out on a thread where you are talking about opening up a port for remote access.

The security in these kind of connections should come from things like password authentication, or at least blocking all but the IPs you know should be connecting.

Please feel free to correct me if I've got something wrong as this is not my area of expertise. :) (I love how that makes it sound like I've got an area of expertise)

Angus

---

### Post by duruttye on 2010-09-23
> **acreech said:**
> I would think that is not safe. it is usually blocked out in x's

Yes, I know, it isn't the real address :)
But thank for the headsup

Anyway, they (my parents) ran out of patience, so am I...

This should be an easy task, I think, if not, it shouldn't be included in the distro, I think :)

Anyway, thank you for your help.

And just in case someone comes across this thread, I would like a command for my parents to put in the terminal, and some advice on accessing their pc.

thank you all :)

---

### Post by CharlesA on 2010-09-23
It's an invalid IP address anyway. You can't have any octet greater then 255.

Try to ssh to localhost and see what happens.

Could be that the port isn't forwarded on the router or the isp is blocking port 22.

---

### Post by lisati on 2010-09-23
It's not a real IPV4 address. 
> **da burger said:**
> I could well be wrong but if you use only an external ip it will connect to the router. I think you need to use port forwarding or something of the like to get around this.
Angus
The "timed out" error is what I'd expect too if port forwarding wasn't set up correctly.

Another possibility is that the OPs parents have a dynamic IP address that has changed since someone last looked.

---

### Post by CharlesA on 2010-09-23
Instead of opening SSH to the internet. I would suggest using something like TeamViewer to view their desktop.

It's encrypted like SSH but it isn't open to the internet.

---

### Post by fly-by-night on 2010-09-23
This thread got me back on the remote desktop track, thanks everyone.  I gave up since it looked too risky. I'm very paranoid, but Teamviewer seems like it can simplify everything.

An appropriate title will be a bonus (edit: for this thread).

---

### Post by CharlesA on 2010-09-23
Changed the thread title to be more descriptive.

---

### Post by pricetech on 2010-09-24
The reason you can't connect is because port forwarding has not been set up in the router, though the possibility does exist, as suggested earlier, that their ISP is blocking port 22, though I've never seen that.

A service like Dynamic DNS would be helpful too.  They'll need to access it so the chosen domain name resolves to their IP.

Once that's done, you should be able to connect remotely to their computer and you can install other things that will make your job easier.

---

### Post by Pweg on 2010-09-24
Generally with my experience with remote access you have to do the ip and the port, separated.

First you'll have to set up port forwarding on the router to forward port 22 to the local ip that their computer is on (you'll want to deactivate that afterward, that's a popular port for mischief).

Afterward, you should be able to connect to their external ip and use the port number, for example:

```
rdesktop 209.xx.xx.xx:22

```
This isn't a tried and true method, so I could be entirely wrong, but from my experience in networking its the logical progression.

---

### Post by brcre on 2010-10-16
For those using the LTS Ubuntu 10.04 who are having problems getting it to work I would suggest this:
From Desktop Panel:
System\Administration\Software Sources
add...   ppa:llyzs/ppa
From a Terminal
Applications\Accessories\Terminal
```
sudo apt-get install freerdp-dbg freerdp-x11 libfreerdp-plugins-standard libfreerdp0 tsclient
```
From Desktop Panel:
Applications\Internet\Terminal Server Client
	Enter in the connection information and connect.

Honestly I did not read every post in the past 4 pages and I did catch a few things like redirecting port access and such which I'm not addressing.  However the core issue: Connecting to a remote system is one I was having problems with and this is what I used to fix it.
For those who updated to 10.10 all you need to do is:
From Desktop Panel:
System\Administration\Synaptic Package Manager
Search for freerdp and mark for install the listed packages except tsclient.
freerdp-dbg freerdp-x11 libfreerdp-plugins-standard libfreerdp0
now search for tsclient and mark for install
Apply

That is how I found a usable fix, one of my systems I use to just "play" on was running 10.10 and I got Terminal Services working.  The other which I use to run my life was running 10.04 and I copied the solution used on 10.10 to my 10.04.

---

### Post by brcre on 2010-10-16
I just noticed I missed one critical point...
I'm connecting from Ubuntu to Windows 7 (at school if that matters any)
and I see the original poster was going Ubuntu to Ubuntu.  I haven't tried that.

---

### Post by jonny163 on 2011-02-12
Apologies for necro'ing but you set your parents up on Ubuntu? Very brave

---

