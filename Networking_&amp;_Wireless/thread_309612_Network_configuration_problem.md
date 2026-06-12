---
title: "Network configuration problem"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by impakt on 2006-11-29
Hello again, 

      Hopefully I can ask this question clear enough for someone to respond. 
Heres a little background: Im pretty much a linux newbie. I been using ubuntu for a year but it worked perfectly out of the box. never had to touch a thing so the linux lingo im very very new too. I have only been reading about this now for 2 days. 

I am using a Dlink router with 3 windows computers. 2 wireless and one wired with a ethernet cable. The ISP is verizon FIOS. A year ago they came and installed this system and i plugged my UBUNTU linux box directly into the router and boom. Instant internet, everything worked great. fastforward to a year later. 

I come home to find that my router was unplugged/plugged back in, all windows computers are still up and running fine, wireless SSID and security settings are all fine and dandy. 

only difference is my nice linux box(the better system with all my stuff on it, basically my main computer because i love it so much)  isnt connecting to the internet, network icon shows a yellow !.

Now here are the things i have tried. Resetting the modem, making sure all the cables are good. I plugged the ethernet cable that is normally into my linux computer into a windows computer and it instantly went online. I also tried playing with the settings in the router config. and tried numerous times to set static IP. 

Here is a screen shot of the status for the router.

I have tried pinging every single IP address i can find on my router. I had a little help the other day from someone in the beginner forum but it didnt solve the problem. 
[http://www.ubuntuforums.org/showthread.php?t=302612&highlight=dhcp](http://www.ubuntuforums.org/showthread.php?t=302612&highlight=dhcp)
link is above. 

A few strange things have happened since this has started as well. 

1:In the connection properties window. I can select "LO". the status will change back and forth from idle/sending receiving. activity shows 9367 packets received and the same for sent. 

2: eth0 is no longer available. But i can type eth0 in and teh status will show disconnected. Under support the type shows ethernet and the address is 00:14:85:60:d3:51
If i hit configure: the little icon of a watch will show up but after about 20 seconds it shuts off and the network properties window shuts down. Basically nothing happens. This just started happening. It use to come on so i can either set dhcp or static, dns..ect.ect..

I also found somewhere to run "sudo pppoeconf". I ran earlier today i got a message.
"sorry, I scanned 1 interface, but the access concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running PPoe process which controls the modem "

now i get Sudo: unable to lookup ubuntu via gethostbyname()

please help. Im lost here and i really dont want to uninstall-reinstall everything.  THANKS!

---

### Post by trubblemaker on 2006-11-29
great attempt at getting lots of info into a post!

here's some stuff that you can show me so I can help you.

the quick fix without working, mostly a windows trick, reboot.

but where in linux so why do that why not try this in a terminal:

```
 sudo ifdown eth0
sudo ifup eth0 
```
that get you up a running ? Great!

NO?

please post the output of the following:
```
 
lspci
cat /etc/network/interface
ifconfig

```

---

### Post by dlehman on 2006-11-29
in addition to the above you never pinged your network card as suggested in your other post please post the output of

ping 127.0.0.1

hope we can help

---

### Post by impakt on 2006-11-29
thanks for the response. 

sudo ifdown eth0
sudo ifup eth0

both give me Sudo: unable to lookup ubuntu via gethostbyname()

lspci- gives me a bunch of stuff. God i wish i could copy/paste. 
Lots about the hardware in my pc. The line i think you are looking for:

0000:01:01:0 ethernet controller:INTEL CORPORTATION 82801EB/ER(ICH5/ich5r INTE GRATED LAN CONTROLLER (REV 20)

cat /etc/network/interface: no such file or directory

ifconfig: lo link encap: local loopback 
inet addrL 127.0.0.1 mask 255.0.0.0
inet 6 addr: :: 1/128 scope : host
up loopback running mtu: 16436 metric 1 
rx packets 36807 errors 0 dropped 0 overruns 0 frame 0
tx packets 36807 errors 0 dropped 0 overruns 0 carrier 0
collisions 0 txqueuelen 0
rx bytes 2995636 (2.8mib tx bytes 2995636 2.8 mib


Ping:127.0.0.1 pinged just fine. i ctrl C'd after it rang for a few seconds but i fot 11 packets received 0 packet loss, time 9999ms
rtt min/avg/max/mdev/= 0.040/0.046/0.056/9.008ms 


thanks again.

---

### Post by trubblemaker on 2006-11-29
cat /etc/network/interface[COLOR="Red"]s[/COLOR]
my bad. if you can ping things, then you have internet, looks like you have some bad settings in:
cat /etc/network/interface[COLOR="Red"]s[/COLOR]

so

try the old fashioned way:
```

sudo ifconfig eth0 up
sudo dhclient eth0

```
check 'dmesg' for any bad news about networking, please only post relevant parts.
```

dmesg

```
and lets also post this so we can fix it later:
```
cat /etc/network/interface[COLOR="Red"]s[/COLOR]
```

---

### Post by impakt on 2006-11-29
any time i type in a sudo prompt i get that message i stated previously. But i think i figured out why thats happening, i just have to find out how to fix it now. In a frantic effort trying to get the network up and going i deleted the hosts in the network configuration. So i think pretty much everything i do without me fixing that isnt going to do anything. 

I found a post (below) that should fix my host problem. 
But when i do as followed. I get a screen open that says:
gnu nano 1.3.10      FILE: ext/hosts.


<new file>
^G GET HELP ^O WRITE OUT ^Y PREV PAGE ^K CUT TEXT ..ect.ectti cant edit or change anything

It sounds like your /etc/hosts file is misconfigured.

To edit the /etc/hosts file, you would need to get to a root prompt (as your sudo command will not be working with a misconfigured hosts file). The easiest way to do this is to use the recovery mode option from the grub menu at bootup.

When you get to a root prompt, open up the /etc/hosts file with this command.

Code:

nano /etc/hosts

The /etc/hosts file normally looks something like this...

Code:

127.0.0.1 localhost.localdomain localhost slave # The following lines are desirable for IPv6 capable hosts ::1 ip6-localhost ip6-loopback fe00::0 ip6-localnet ff00::0 ip6-mcastprefix ff02::1 ip6-allnodes ff02::2 ip6-allrouters ff02::3 ip6-allhosts

What you need to do is to edit the first line so that it contains a hostname for your computer. Mine is called 'slave' as you can see above. You can choose any name you like. The current hostname can be found by using the 'hostname' command. By default ubuntu uses the hostname 'ubuntu'.

The first line should look something like this if you were using the hostname, 'ubuntu' for example..

Code:

127.0.0.1 localhost.localdomain localhost ubuntu

An additional command you can look at with regards to hostnames is this command below.

Code:

hostname #returns the current hostname hostname <hostname> #sets the hostname according to the value entered for <hostname>

---

### Post by trubblemaker on 2006-11-29
write. so your all good then or are you asking a question?

try using the "[quote] " and [*quote] (where '*' is replaced with '/')to seperate what you say from someone else

---

### Post by jamesr on 2006-11-30
Hi,

As an example I copied my /etc/hosts file and the code to get to it

```
ashteq@Ashteq:~$ sudo nano /etc/hosts
Password:

```> 
  GNU nano 1.3.12             File: /etc/hosts                                 

127.0.0.1       localhost
127.0.1.1       Ashteq.oawh2.on.cogeco.ca       Ashteq

192.168.123.90          Delly   # X/Ubuntu server 6.10 + X
# 192.168.123.91        Tubby   # Xubuntu server 6.06 Backup
192.168.123.99          HUBA    # printer server
192.168.123.100         AlphaStation
192.168.123.101         Tower1A
192.168.123.102         Tubby   # Backup Server
# 192.168.123.103               Kubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

                               [ Read 18 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell
```


^X

```> 
ashteq@Ashteq:~$ 

The lines referring to my pc on the network are not important nor the lines referring to ipv6.

The hosts file should not affect the sudo command. The way that I read your  reply is that the file does not exist and it is creating a new file.

---

### Post by impakt on 2006-11-30
Thanks..

Its wierd because if I copy that code into terminal with sudo before the code i get the same " Sudo: unable to lookup ubuntu via gethostbyname

If i copy the code with out sudo I get a window in terminal with the following

"
GNU NANO 1.3.10                  File /etc/hosts

# The following lines are desirable for ipv6 capable hosts.






Read 2 lines
^G ^O ^R ect.ect..

"

but i get nothing like you are getting. no lines after "the following lines"

I think without fixing this, im not going to be able to get my network up again:(


THANKS!

---

### Post by jamesr on 2006-11-30
Hi, 

The file /etc/hosts looks almost empty

With you layout I cannot always what is code and what are quotes ie output.

```
cat /etc/hosts
hostname -i

```

---

### Post by impakt on 2006-11-30
got the host fixed . But still can not connect to the internet. I set it up with a static ip and tried dhcp

no luck. When i set it to dhcp and hit activate it hangs with " activating interface 
"etho"

When i set it to static and put the correct IP/dns/gateway/subnet it says cannot activate etho instantly

---

### Post by trubblemaker on 2006-12-01
gui not as good as commandline for trouble shooting as it gives no output.

try these commands and post the output if they fail:

```
ifconfig
sudo ifconfig eth0 up  # may say it's already up no worries
sudo dhclient eth0     # tries to get ip address

```

---

### Post by impakt on 2006-12-03
Just an update. The problem with the network hasnt be found, but fixed. Strangest thing I have ever seen. 

someone here suggested it could be a hardware problem so i went and bought a new network card. I popped in and went into the bios and disabled the onboard lan. Booted up the machine and it wouldnt work. I got pissed and took the ethernet cable out and plugged it back into the standard ethernet slot and boom, it worked but wouldnt connect with anything. I sudo ifdown eth0'd and sudo ifup eth0'd and here i am. Using the onboard lan, with the PCI network card plugged in and the onboard lan disabled. WTF was the problem? and how is it working now??!>! i cant complain!Im happy as a pig in ****:)

---

### Post by impakt on 2006-12-03
Thanks Everyone!

---

### Post by trubblemaker on 2006-12-03
sounds like a kick-to-the-side-of-the-machine fix

fyi for others, I just found a thread that advices adding noapic to the boot parameters for fixing issues with specifically this card.  Same mysterious not working when it should.

The extra card may have shifted the irqs? --> same fix 

who knows,

glad to here your up and  running.

---

