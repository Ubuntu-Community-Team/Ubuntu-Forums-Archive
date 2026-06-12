---
title: "Is there an easy way to connect/work to/on another computer via the Internet"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by drillerccg on 2010-08-25
Edit: I found teamviewer and it works like a charm. Connected under 5 minutes.

[http://www.teamviewer.com/download/index.aspx?os=linux](http://www.teamviewer.com/download/index.aspx?os=linux)



I've been at this now for a week. Have read articles on openSSH, VNC, port forwarding, Remote Help Assistant project ([http://pileofstuff.org/remote-help-assistant/](http://pileofstuff.org/remote-help-assistant/)) but I still cannot connect to my mom's Ubuntu machine in another town. Pretty frustrating. It seems there should be an easy way to do this.

---

### Post by mikewhatever on 2010-08-25
Are you talking about connecting from an Ubuntu machine to another Ubuntu machine? If that's the case, VNC is the easiest, but not as secure as ssh.

---

### Post by alphacrucis2 on 2010-08-25
> **drillerccg said:**
> I've been at this now for a week. Have read articles on openSSH, VNC, port forwarding, Remote Help Assistant project ([http://pileofstuff.org/remote-help-assistant/](http://pileofstuff.org/remote-help-assistant/)) but I still cannot connect to my mom's Ubuntu machine in another town. Pretty frustrating. It seems there should be an easy way to do this.

VNC and SSH should work fine. But you need to to make sure

1. that the SSH server and or VNC server is/are actually running on you Moms PC and are not blocked by a firewall.

2. The router at your mom's house is configured to port forward the ssh and or vnc port to the PC.

3. You need to know the public ip address of your moms router (which may change). Dyndns can help with this.

4. Use **[COLOR="Red"]very strong passwords[/COLOR]** or digital certificates to secure the connections.

---

### Post by LiquidMeson on 2010-08-25
[https://secure.logmein.com/labs/](https://secure.logmein.com/labs/)
look for linux. Haven't use the site in a few years but it used to work wonders.
Download the .deb file

Download the file on both sides and install it.
Make an account on the website,
Go to [https://secure.logmein.com/hamachi/computers.asp](https://secure.logmein.com/hamachi/computers.asp)

Create a Mesh network. Select auto connect (no pass). Finish. Copy the ID code.

On both computers in the terminal run "sudo hamachi login"
sudo hamachi join <ID Code>

Then on your grammies computer go to system> preferences> Allow other to view.
On your computer Applications>Remote viewer, the other pc should show up
Piece of cake, I learned something new today.

---

### Post by LiquidMeson on 2010-08-25
whatever bump

yes i know i'm not supposed to bump for 24 hours.

Oh and U1 I'm looking at you 0_0

---

### Post by mikewhatever on 2010-08-25
> **LiquidMeson said:**
> Bump, finished editing. :D

yes i know i'm not supposed to bump for 24 hours.

Oh and U1 I'm looking at you 0_0

What exactly did you bump for?

---

### Post by LiquidMeson on 2010-08-25
I was full of joy.

---

### Post by drillerccg on 2010-08-25
Newbie here and the ssh and VNC are causing a problem for me. I have installed the server version of openSSH on my mom's. But am not sure what to do next. I would like to click on something and see her desktop. I understand that I have to forward port 22 on my mom's gateway/router so I can get through but not sure how. The router has these settings: name public and private port ranges and ip address. I went to whatismyip.com and found her ip address and plugged it in. Not sure what the public and private ports are all about so I set all of them to 22. Then tried to connect via the Applications/Internet/Remote Desktop Viewer ( I think it's the bundled VNC). No luck!!!

I also don't understand how to relate the SSH and VNC or is it done automatically. I tried to connect with the

ssh username@ipaddress

where I had edited the sshd_config file and entered a username line at the end 
(per [http://www.jonathanmoeller.com/screed/?p=1585](http://www.jonathanmoeller.com/screed/?p=1585) ) but don't know where to go from there. 
It did not connect anyways.

It seems like there is too much to learn and configure. The Remote Help Assistant project appeared to be the
God Sent but that did not work either. It kept looking for the ip and if I entered it manually it would hand and not connect. I basically gave up after a week of frustration. I'm going to give this logmein a try now.

---

### Post by Peter09 on 2010-08-25
try the following command line
 
```
ssh -vv <username>@<ipaddress>
```
 
this should give you a debug output - post it here.
 
Note that I use x11vnc to support my friends.
 
Install it - its in the repositories.
On you Mums PC create a launcher with the command:-
 
```
x11vnc -noxdamage -connect <your-ipaddress>
```
 
on your machine create a launcher with the command
 
```
x11vnc -listen
```
 
You will not need to change you mums router but will need to port forward yours to your machine.
 
When your mum needs support she phones you, you click on your support launcher, then she clicks on hers and you should see her screen.
 
This is a better method because a) there is no application running continuosly on your mums machine that could cause a security leak and
b) the only difficult bit is the router config, and thats local to you.

---

### Post by drillerccg on 2010-08-25
@Peter09: Thanks for the suggestions. I got so frustrated that I un-installed openSSH from both our computers. I don't understand the relation between ssh and VNC. I thought ssh was a "secure tunnel" for VNC to connect. Is that right? You are not using it?

Also, I would apprecite it  (if you have time) to tell me how to start from the begining in a cook-book kind of way so I can set both up. I am not with my mom and have to have her do most of the stuff and that takes a long time (72 years old and very limited computer skills). I did manage to have her install openSSH by emailing her commands. I can try again if I have clear directions. I'd appreciate it.

---

### Post by redbook4574 on 2010-08-25
You could try teamviewer, not wonderful but easy to use.

---

### Post by Peter09 on 2010-08-25
OK - on her machine get her to install x11vnc
 
```
sudo apt-get install x11vnc
```
 
do the same on your machine.
 
On your router port forward vnc to your machine.
 
On your machine, in a terminal, type
 
```
x11vnc -listen
```
 
Ask you mum to type in a terminal
 
```
x11vnc -noxdamage -connect <your ipddress>
```
 
you should then see your mums screen and be able to set up a launcher for her.

---

### Post by mikewhatever on 2010-08-25
For port forwarding, check out the link below.
[http://portforward.com/english/routers/port_forwarding/routerindex.htm](http://portforward.com/english/routers/port_forwarding/routerindex.htm)

---

### Post by CharlesA on 2010-08-25
If you do the method that Peter09 posted, you shouldn't have to forward any ports. :)

However, I don't think you'd be able to see their screen.

The best way would be to tunnel VNC over SSH (which you can do with vino (the "remote desktop" server in Ubuntu) Just create an SSH tunnel for port 5900.

---

### Post by Peter09 on 2010-08-25
Unfortunaly you do have to forward ports on **Your** router as it needs to accept an incoming connection from your Mums machine. Yes you can see and control the remote screen, I do this with several people that I provide support for. Its not ideal in terms of performance but its simple and it works - its best if the remote screen does not have a really complex background. 
 
The real best way is to use FreeNX but that is more complex and needs ports open at the remote end.

---

### Post by CharlesA on 2010-08-25
Meh, still going to be exposing VNC to the internet.

I suppose it would be easier to use something like TeamViewer. I've used it for Windows, and it looks like it's in Beta for Linux, but it would be an easier way to do what you ask.

---

### Post by heviiguy on 2010-08-25
TeamViewer works wonders for me. Is there something I should be aware of when using it? The program/service is a no-brainer when compared to the arcane configurations that one must do on their boxes to get the same functionality. 

Please somebody, tell me why it's not a good idea to use TeamViewer and I'll quickly eviscerate it.

---

### Post by Peter09 on 2010-08-25
I think teamviewer does exactly the same as I have suggested except its in a more convienient package. 
 
As for security, you are right, the packet stream is not encrypted, so someone could if they wanted see the information, however they would find it difficult to break into the remote system as there is no open port, except during the actual debug session.
 
I gues it comes down to what value is the information likely to contain in the data stream.

---

### Post by CharlesA on 2010-08-25
> **heviiguy said:**
> TeamViewer works wonders for me. Is there something I should be aware of when using it? The program/service is a no-brainer when compared to the arcane configurations that one must do on their boxes to get the same functionality. 

Please somebody, tell me why it's not a good idea to use TeamViewer and I'll quickly eviscerate it.

The data sent using TeamViewer is encrypted and it can use a random password to connect.

> **Peter09 said:**
> I think teamviewer does exactly the same as I have suggested except its in a more convienient package. 
 
As for security, you are right, the packet stream is not encrypted, so someone could if they wanted see the information, however they would find it difficult to break into the remote system as there is no open port, except during the actual debug session.
 
I gues it comes down to what value is the information likely to contain in the data stream.

Either way, I wouldn't expose VNC to the internet. It would be safer to tunnel it over SSH, as you don't know what exactly is being transmitted over VNC.

---

### Post by drillerccg on 2010-08-25
@peter: thanks for all yor help. I tried TeamViewer and it was so easy it was scary. I connected to my mom's comuter under 5 minutes. Is it as secure as VNC+openSSH? I have no idea but I can finally connect without any hassle. Thanks for all the help. Will be editing the first post to reflect this. TeamViewer free-ware is the way to go IMHO for us noobs.

---

### Post by stmiller on 2010-08-25
There's a guide here:

[http://www.cyberciti.biz/faq/howto-setup-vnc-server-ssh-client-tunnel-via-internet/](http://www.cyberciti.biz/faq/howto-setup-vnc-server-ssh-client-tunnel-via-internet/)

---

### Post by CharlesA on 2010-08-25
> **drillerccg said:**
> @peter: thanks for all yor help. I tried TeamViewer and it was so easy it was scary. I connected to my mom's comuter under 5 minutes. Is it as secure as VNC+openSSH? I have no idea but I can finally connect without any hassle. Thanks for all the help. Will be editing the first post to reflect this. TeamViewer free-ware is the way to go IMHO for us noobs.

Yeah, it's secure. It uses a randomly generated password as well as encryption.

You can read more about it here: [http://www.teamviewer.com/products/security.aspx](http://www.teamviewer.com/products/security.aspx)

---

### Post by Peter09 on 2010-08-26
Yeah - I tried it yeterday evening - I was confusing it with another application with a similar name but much less sophisticated. Having seen teamviewer I would recommend it, and will use it myself.

---

### Post by jack frost on 2010-08-27
> **drillerccg said:**
> Edit: I found teamviewer and it works like a charm. Connected under 5 minutes.
 
[http://www.teamviewer.com/download/index.aspx?os=linux](http://www.teamviewer.com/download/index.aspx?os=linux)
 
 
 
I've been at this now for a week. Have read articles on openSSH, VNC, port forwarding, Remote Help Assistant project ([http://pileofstuff.org/remote-help-assistant/](http://pileofstuff.org/remote-help-assistant/)) but I still cannot connect to my mom's Ubuntu machine in another town. Pretty frustrating. It seems there should be an easy way to do this.
 
teamviewer worked for me using xp at my work to connect to ubuntu at home; but it is very slow.  I want to try logmein..it is faster?

---

### Post by LiquidMeson on 2010-08-27
You could try the instructions I posted earlier, the windows download can be found at [https://secure.logmein.com/US/products/hamachi2/download.aspx](https://secure.logmein.com/US/products/hamachi2/download.aspx) (reccomend making an account and choosing managed, you don't have to use the command line as much) Not sure if it will be much faster but it might be worth the try.

---

### Post by jack frost on 2010-08-28
> **LiquidMeson said:**
> You could try the instructions I posted earlier, the windows download can be found at [https://secure.logmein.com/US/products/hamachi2/download.aspx](https://secure.logmein.com/US/products/hamachi2/download.aspx) (reccomend making an account and choosing managed, you don't have to use the command line as much) Not sure if it will be much faster but it might be worth the try.

I went back to try teamviewer client on my xp machine at work and the speed is much faster.  I was using the teamviewer weblink the first time to connect to the ubuntu machine at home from work that way is super slow.  I had to wait and install in on my work computer first last night  then test from home today.

---

### Post by Cyber_rader on 2010-09-16
i like to use teamviewer 5 it works well connects via IP or TVID (teamviewer ID) so you can work on a computer behind you or at the north poll i put it on the computers i use so i dont have to move around to get to every computer to do something remote. and a few friends of mine have it too incase they have a tech issue and want my help

---

