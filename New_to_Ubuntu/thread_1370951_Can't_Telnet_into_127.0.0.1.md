---
title: "Can't Telnet into 127.0.0.1"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by Husar on 2010-01-02
I have installed Apache2, PHP, and MySQL. I can hit localhost and 127.0.0.1 in the web browser. But I can't seem to telnet into 127.0.0.1 port 5331.  Can someone tell me why?

Thanks in advance.

---

### Post by sandyd on 2010-01-02
> **Husar said:**
> I have installed Apache2, PHP, and MySQL. I can hit localhost and 127.0.0.1 in the web browser. But I can't seem to telnet into 127.0.0.1 port 5331.  Can someone tell me why?

Thanks in advance.
you need to install openssh-server [[click here to install]]("apt://openssh-server")

---

### Post by falconindy on 2010-01-02
What are you expecting to accept your connection at port 5331? Telnet is an outdated (unsecure) protocol used in fewer and fewer applications. Incidentally, I don't think it will ever disappear from SMTP.

---

### Post by Husar on 2010-01-02
openssh and and ssh appear to be installed according to the Synaptic Packages Manager.

The only reasons I need telnet is to test the connections. I am working on a physical computing project communication between software and hardware.  Telnet validates that the software can communicate with the hardware.  Which I am having problems with. Serproxy is what does the final communications and not Telnet. But Telnet let's me confirm all is working as expected.

Any other ideas or settings I need to look at to set Telnet working?

---

### Post by falconindy on 2010-01-02
> **Husar said:**
> openssh and and ssh appear to be installed according to the Synaptic Packages Manager.

The only reasons I need telnet is to test the connections. I am working on a physical computing project communication between software and hardware.  Telnet validates that the software can communicate with the hardware.  Which I am having problems with. Serproxy is what does the final communications and not Telnet. But Telnet let's me confirm all is working as expected.

Any other ideas or settings I need to look at to set Telnet working?
A simple ping indicates connectivity on the network level and is just as effective if your end goal does not use telnet. If you'd really like something more substantial than a ping, use SSH.

---

### Post by mike_yung on 2010-01-03
> **Husar said:**
> I have installed Apache2, PHP, and MySQL. I can hit localhost and 127.0.0.1 in the web browser. But I can't seem to telnet into 127.0.0.1 port 5331.  Can someone tell me why?

Thanks in advance.

Well it's either a problem with telnet or with the service you are trying to test.  Do you know telnet works?  If you're not sure, try this.

```
telnet freenet.victoria.bc.ca
```If telnet is working but you can't connect to 127.0.0.1:5331 please tell us what service you have running on port 5331 so we can help further.

---

### Post by Husar on 2010-01-03
I am able to telnet into VIFA. So Telnet appears to be working.

I am trying to use Serproxy to connection an Arduino to an application I have written. On OS X I have no problem at all using Serproxy to do this. Serproxy works just fine on Ubuntu (just not for me). If you are not familiar with Serproxy the configuration file looks like this....


-------------------------------------------
# Config file for serproxy
# See serproxy's README file for documentation

# Transform newlines coming from the serial port into nils
# true (e.g. if using Flash) or false
newlines_to_nils=true

# Comm ports used
comm_ports=1,2,3,4

# Default settings
comm_baud=115200
comm_databits=8
comm_stopbits=1
comm_parity=none

# Idle time out in seconds
timeout=300

# Port 1 settings (ttyS0)
net_port1=5331

# Port 2 settings (ttyS1)
net_port2=5332

# Port 3 settings (ttyS2)
net_port3=5333

# Port 4 settings (ttyS3)
net_port4=5334

#OS X  sensors
#serial_device1=/dev/cu.usbserial-A6008jFy

#Linus sensor
serial_device1=/dev/ttyUSB0

-------------------------------

Serproxy let me connect physical hardware (an Arduino) to my application written in FLEX.  As I mentioned this works perfect on OS X. I have confirmed that /dev/ttyUSB0 is the correct USB port. I can use the Arduino IDE to confirm this and track the data just fine in Ubuntu.  But when I try to use Serproxy I have not luck.

I know from testing on OS X that if I can telnet into 127.0.0.1 5331 then the Arduino should be fine.  That was the reason for starting this thread with the Telnet bit.

So I think the question is do I need to do anything special on Ubuntu to activate the 5331 port. Or maybe this is a rights issue?  

But regardless of what else I am doing if I can telnet into 127.0.0.1 5331 I would be okay.

Thanks in advance.

---

### Post by mike_yung on 2010-01-03
> **Husar said:**
> ...  So I think the question is do I need to do anything special on Ubuntu to activate the 5331 port. ...

Yes, since the test you did with telnet proved that the service is not listening you will need to make some changes so that it is.

With the other distributions I've used before the link between the TCP/UDP ports #'s and the actual programs was in /etc/initd.conf.  Ubuntu seems to do things a little differently & I'm still wrapping my head around the differences.

I'm sure now that we understand your question someone who knows how this is done in Ubuntu can step in.  If not, try the networking forum.

By the way, if you installed an Ubuntu Serproxy package a bug should be reported since it didn't work as it should have.

---

### Post by Husar on 2010-01-03
I am making a little progress. I found a very old post that mentioned installing xinetd. I get that a try. Now I can telnet into localhost and I could not do that before.

Here are several tests I ran.

telnet localhost 25
Trying ::1...
Trying 127.0.0.1
telnet: Unable to connect to remove host: Connection refused

telnet localhost 80
Trying ::1...
Connected to localhost
Escape character is '^]'

telnet localhost 5331
Trying ::1...
Trying 127.0.0.1
telnet: Unable to connect to remove host: Connection refused

I am starting to think that there is a configuration some where I need to set to allow telnet to get into 5331 or any other port I need.

Any suggestions?

---

### Post by The Cog on 2010-01-03
Firstly, all /dev/* devices are only accessible to root. So you will have to sun serproxy using sudo in order for it to be able to work, e.g. **sudo serproxy**. 

Secondly, I think that serproxy isn't running and therefore port 5531 isn't open, which is why you get "connection refused". I can think of two tests to prove this: firstly, the command **ps -ef | grep serproxy** should show you a line if serproxy is running. Secondly, the command **netstat -lnt** will show you all the tcp ports that are open and listening for connections - I think you'll find that port 5531 is not listed amongst them.

I don't know why serproxy isn't running (unless it's crashing because it doesn't have access rights to the serial ports), but the above tests should at least confirm whether serproxy is listening for connections.

---

### Post by mike_yung on 2010-01-03
> **Husar said:**
> I am starting to think that there is a configuration some where I need to set to allow telnet to get into 5331 or any other port I need.

Any suggestions?

I agree.  You are on the right track.

I have no suggestions.  You need to stand by for someone who knows how this is done in Ubuntu to step in or try the networking forum.

---

### Post by Husar on 2010-01-03
I am 100% sure serproxy is running.  I do run it as root, sudo serproxy. I get a response back from it saying,

[INDENT]**Serproxy - (C)1999 Stefano Busti - Waiting for client**
[/INDENT]
Then I open up another terminal window and type,

[INDENT]**telent 127.0.0.1 5331**
[/INDENT]
the response back in the serproxy window is,

[INDENT]**Failed to open comm port - connection refused**
[/INDENT]
then back in the terminal window it responds as,

[INDENT]**Connection closed by foreign host.**

[/INDENT]when I type** ps -ef | grep serproxy **I get the following,[B]

root     8090      8090     0    12:24 pts/0     00:00:00      serproxy
ed        8151     8109      0    13:29 pst/1     00:00:00 grep --color=auto  serproxy

[/B]

---

### Post by Husar on 2010-01-03
Also, here is what i get on the netstat.  

ed@Ed-netbook:~$ netstat -int
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0         0      0      0 0             0      0      0      0 BMU
eth2       1500 0     45444      0      0 0         40097     20      0      0 BMRU
lo        16436 0       346      0      0 0           346      0      0      0 LRU

---

### Post by The Cog on 2010-01-03
There are clues there. Fitrstly, serproxy is complaining it couldn't open the comm port. Then telnet says "Connection closed by foreign host". This telnet message means that the connection was accepted and then closed, which is consistent with the idea that serproxy accepted the connection, then failed to open the comm port and therefore closed the connection again. So I now think that you need to look into the serproxy configuration a little closer. Since it's running as root, I don't think it's a permissions issue - maybe check that it's trying to open a port that actually exists - maybe check that it's configured for /dev/Stty0 rather than just ttyS0, and make sure it exists.

At a push, use strace to see what it's doing, as in **strace serproxy** but it will be hard work wading through all the output.

---

### Post by Husar on 2010-01-03
The serproxy cfg file is so basic that I am starting to thing that this is a bug related to Ubuntu.  Here is the config for serproxy.  There is not much you can screw up.

# Config file for serproxy
# See serproxy's README file for documentation

# Transform newlines coming from the serial port into nils
# true (e.g. if using Flash) or false
newlines_to_nils=true

# Comm ports used
comm_ports=1,2,3,4

# Default settings
comm_baud=115200
comm_databits=8
comm_stopbits=1
comm_parity=none

# Idle time out in seconds
timeout=300

# Port 1 settings (ttyS0)
net_port1=5331

# Port 2 settings (ttyS1)
net_port2=5332

# Port 3 settings (ttyS2)
net_port3=5333

# Port 4 settings (ttyS3)
net_port4=5334

#sensors
serial_device1=/dev/ttyUSB0

But totally not related to serproxy is still the fact that I cannot telnet into 127.0.0.1 5331.  

If we took serproxy out of the picture entirely right now how would I make sure 5331 is open and able to let me telnet in?  Or any other port for that mater?

---

### Post by The Cog on 2010-01-04
Port 5331 **is** open. Your telnet session is saying the remote host closed the connection. It only says this after the connection has been accepted (otherwise it would be saying connection refused). Post #12 in this thread. So your problem lies entirely within serproxy, accepting and then closing the call. And its message "cannot open comm port" is a huge clue although it doesn't say which port or what the error is.

Does /dev/ttyS0 exist? (ls -l /dev/ttyS0)
Does /dev/ttyUSB0 exist? (ls -l /dev/ttyUSB0)

Oh, and it's **netstat -lnt** (lower-case -LNT) that shows the listening TCP ports. l:listening ports, n:numeric list, t:TCP protocol.

---

### Post by The Cog on 2010-01-04
I just tried serproxy here. Downloaded and untarred it. Used these commands:
> ./make
sudo cp serproxy.cfg /etc
sudo ./serproxy
and then from another window:
> telnet localhost 5331
Although I couldn't test the serial connection (nothing to connect to just here), serproxy accepted the call and said it was launching a thread. I was able to type in the telnet window, and I suspect that if I had a serial device attached, I would have been talking to it.
I tried with both the default serproxy.cfg and the one you posted - both worked as far as I can tell.

---

### Post by The Cog on 2010-01-04
Additional note:
I was trying serproxy version 0.1.2. On closer inspection, it seems that this version will ignore the config line:

serial_device1=/dev/ttyUSB0

which is a good job for me since I don't have such a device. What version of serproxy were you using?

---

### Post by The Cog on 2010-01-04
Sorry for all the posts - I'm behind a proxy that blocks yahooapis so I can't edit my earlier posts.

I found the 0.1.3 serproxy. All I can guess is that you don't have a /dev/ttyUSB0 device - you'll have to look in your /dev folder and figure out what the name of your USB serial port is.

---

### Post by Husar on 2010-01-04
Yes, the /dev/ttyUSB0 is found. I think I did a ls on that the other night.  But I think I am going to blow away my serproxy install and reinstall. I am wondering now if I did the build not as root. Not sure if that is possible or not.  I think when I installed it I put it in my Downloads folder and did the build there. But I can't remember if I did that as root or not. I am not in front of my machine right now but will do this tonight right away and see if that makes any different. I will also look at the netstat -lnt again and try the ls -l /dev/ttyS0.

Thanks.

---

### Post by Husar on 2010-01-10
Okay, after many, many tests I was able to get things working.  I am a little embarassed to say that it all came down to the right version of serproxy.   Looks like I was one version behind on serproxy. Make sure you get version 0.1.3 and not 0.1.2. Big difference in results!  

After removing and installing 0.1.3 I was golden.  Everything worked as expected.  A big thanks to everyone that tried to help me along the way.  I really appreciate the effort.

Cheers.

---

### Post by raydot on 2010-03-18
Any progress on this?  I'm having the exact same problem.  Is it maybe rolling back to 9.04 that I need to do?

---

