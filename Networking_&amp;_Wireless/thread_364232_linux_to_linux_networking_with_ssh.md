---
title: "linux to linux networking with ssh"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by maniacmusician on 2007-02-18
I have a couple of questions.

1. I've gotten ssh to work over my network using IP addresses. However, I'd like to be able to use hostnames for it instead ('ssh [user]@[hostname]' instead of 'ssh [user]@[IP address]')

2. ssh is great and all for remote working...But I'd like to be able to make it even easier than having to type a command every time. I want to mount a drive remotely over the network...I know that for Window to Linux I can use smbfs or cifs to mount it. Is there an easy solution for Linux? Can I use ssh to mount a remote drive? (*Note: I know about fish:// with Konqueror, but I want something more permanent*) If not ssh, is there another way to do this?

Thanks a bunch, you guys are great.

---

### Post by koenn on 2007-02-18
> 1. I've gotten ssh to work over my network using IP addresses. However, I'd like to be able to use hostnames for it instead ('ssh [user]@[hostname]' instead of 'ssh [user]@[IP address]')
for this part, you need "name resolution", i.e. something that translates hostnames to ip addresses.

The easiest is to use the /etc/hosts file : you just add all hosts that a certain computer needs to know about + their ip addresses in the /etc/hosts of the computer you 

```
127.0.0.1 localhost 

192.168.0.1     stargate.space.xx      stargate
192.168.0.2     storax.space.xx     storax

```

The advanced way is to use DNS. It's basically the same as /etc/hosts but in stead of maintaining a hosts file on every computer that needs name resolution, you maintain a  "zone file'"  that translates names to addresses, on a DNS server. You can look at it as a centralised hosts file for all computers on a network, as opposed to an separate hosts file  on each computer

---

### Post by koenn on 2007-02-18
> 2. I want to mount a drive remotely over the network...I know that for Window to Linux I can use smbfs or cifs to mount it. Is there an easy solution for Linux? Can I use ssh to mount a remote drive? (Note: I know about fish:// with Konqueror, but I want something more permanent) If not ssh, is there another way to do this?

If the remote Linux is running samba, you should be able to mount the shares same as you do with 'Windows to Linux'.

With Nautilus (gnome, ubuntu) you can also browse/use remote filesystems over ssh - but seeing that you're using Kubuntu ...

Here's some discussion to get you going : 
[http://ubuntuforums.org/showthread.php?t=103860](http://ubuntuforums.org/showthread.php?t=103860)

---

### Post by maniacmusician on 2007-02-18
> **koenn said:**
> for this part, you need "name resolution", i.e. something that translates hostnames to ip addresses.

The easiest is to use the /etc/hosts file : you just add all hosts that a certain computer needs to know about + their ip addresses in the /etc/hosts of the computer you 

```
127.0.0.1 localhost 

192.168.0.1     stargate.space.xx      stargate
192.168.0.2     storax.space.xx     storax

```

The advanced way is to use DNS. It's basically the same as /etc/hosts but in stead of maintaining a hosts file on every computer that needs name resolution, you maintain a  "zone file'"  that translates names to addresses, on a DNS server. You can look at it as a centralised hosts file for all computers on a network, as opposed to an separate hosts file  on each computer
What an awful solution! So I either have to setup a DNS server, which I don't have the resources or knowledge to do, or I have to modify the /etc/hosts file every single time I do a reinstall (which can be quite often). 

Are you sure there's no better method for name resolution? I'd be surprised to hear that Windows actually has an edge in something network-related.

> **koenn said:**
> If the remote Linux is running samba, you should be able to mount the shares same as you do with 'Windows to Linux'.

With Nautilus (gnome, ubuntu) you can also browse/use remote filesystems over ssh - but seeing that you're using Kubuntu ...

Here's some discussion to get you going : 
[http://ubuntuforums.org/showthread.php?t=103860](http://ubuntuforums.org/showthread.php?t=103860)

Actually Konqueror can browse/use remote filesystems as well, I just wanted to have something I could permanently mount and access quickly from any application. The link you provided seems to be able to do the job. I'll try that out tonight.

---

### Post by christhemonkey on 2007-02-18
Something like sshfs?

```
sudo apt-get install sshfs 
```

Then you can mount it just like anything with your fstab:
```
sshfs#USERNAME@REMOTE_HOST:REMOTE_PATH MOUNT_POINT fuse SSHFS_OPTIONS 0 0
```

eg:
```
sshfs#guest@guest.login.com:data /mnt/guest fuse uid=1003,gid=100,umask=0,allow_other 0 0
```


and a dns server really isnt that hard.

Just install bind9 and your away.
```
sudo apt-get install bind9 
```

---

### Post by dmizer on 2007-02-18
i've found that samba is the best solution i've been able to accomplish.  set the samba server (one on each of the machines you want to ssh into) to do nothing more than broadcast netbios names.  you can enable that by installing samba and using the following /etc/samba/smb.conf configuaration:
```
[global]
    ; General server settings
    netbios name = YOUR_HOSTNAME
    server string =
    workgroup = YOUR_WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    wins support = no

    name resolve order = hosts wins bcast
```
of course replacing "YOUR_HOSTNAME" and "YOUR_WORKGROUP" with the respective needs of each of the computers you wish to ssh into.

then, on your clients (computers you want to ssh _from_), you'll need to install winbind, and add the 'wins' option to the "hosts" line in your /etc/nsswitch.conf file:
```
hosts:          files dns mdns [COLOR="Red"]wins[/COLOR]
```

i've been meaning to look into configuring a dns server as well.

---

### Post by maniacmusician on 2007-02-19
dmizer: I've done that before, but I'm looking for a relatively permanent solution that won't vanish when I reinstall. for example, I have a separate /home partition. so, when I reinstall, all I have to do to get ssh capability is install openssh-server, and I'm off. I don't want to have to configure stuff each time.

christthemonkey: Yeah, koenn pointed me to a link with sshfs, and that's working out great. sshfs is amazing. And for some reason, I highly doubt setting up a DNS server is that easy :)

Within the next couple of days, I'm going to be setting up a Linux-based file server on my home network. If I can find out how to do so, I may set up DNS capabilities on that as well.

But aside from that, I'm still looking for a good solution to my hostname resolution problem.

---

### Post by dmizer on 2007-02-19
well ... since host name resolution comes from a part of networking which is not locally configured, i think you're going to have a difficult time filling your needs.

best i can suggest would be to write up a simple script which would expedite your system setting changes, save it in your home partition, and execute it any time you need to reinstall as a part of your openssh-server install routine.

---

### Post by gradedcheese on 2007-02-19
> 
Are you sure there's no better method for name resolution? I'd be surprised to hear that Windows actually has an edge in something network-related.


I have a beautiful solution for this, if you're willing to follow a few instructions :)

0) fire up Avahi on each of your Linux PCs (recent Ubuntu versions ship with it, otherwise install it)
```

sudo apt-get install avahi-daemon avahi-discover avahi-discover

```

1) make sure each PC is doing mdns:

```

sudo apt-get install libnss-mdns

```

Now "sudo gedit /etc/nsswitch.conf" and find the line "hosts: dns", add 'mnds' to it so it reads something like "hosts: dns mdns", save and exit.

2) on each Linux PC, do this:
```

sudo gedit /etc/avahi/services/ssh.service

```

and paste in:

```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
<name>put_a_descriptive_name_here</name>
<service>
<type>_ssh._tcp</type>
<port>22</port>
</service>
</service-group>

```

and then save.  Now restart avahi:

```

sudo /etc/init.d/avahi-daemon restart

```

The result: each PC advertises an SSH service via Zeroconf.  You can resolve the PC's names to ssh into pcname.local or you can right-click on a Panel, add applet, and add the 'service discovery' applet, select the PC you want from its menu and you have SSH :)

For example, if your PC's host name is "linus", then you should be able to SSH into "linus.local" from another PC.

---

### Post by maniacmusician on 2007-02-19
> **dmizer said:**
> well ... since host name resolution comes from a part of networking which is not locally configured, i think you're going to have a difficult time filling your needs.

best i can suggest would be to write up a simple script which would expedite your system setting changes, save it in your home partition, and execute it any time you need to reinstall as a part of your openssh-server install routine.
No, what I meant was, openssh-server works like that already, because the ssh files are already in my home partition from before.

I want something that easy for hostname resolution; something that I don't have to configure each time I reinstall.

@gradedcheese: That's pretty cool, and this method seems to be the best I've seen thus far....but still needs to be redone with every install. Why doesn't Ubuntu create a setup like that out of the box? It doesn't seem hard to do at all...the only thing they would have to do is include the required packages and replace "put_a_descriptive_name_here" with the hostname chosen during the installation.

---

### Post by gradedcheese on 2007-02-19
> 
Why doesn't Ubuntu create a setup like that out of the box? 


It does.  Well, it does half of it.  Avahi is new, and it's not fully built-in yet, but I bet Fiesty or the next one will be that way.  Actually by default, Avahi advertises a "workstation service" that works much like you describe.  However ubuntu doesn't ship with an ssh server running by default, so you need to add that manually.  You'll see more Avahi integration in all sorts of Gnome apps shortly, in fact Banshee (for example) already can share your music much like iTunes does using Avahi, via the click of a checkbox.

This type of networking is called Zeroconf, it was created by a guy at Apple to replace AppleTalk.  All Macs use it to great effect.  Microsoft of course doesn't, they have Netbios and UPnP, which really suck (but work enough to do browsing in "Network Neighborhood" and so on).

The issue with name resolution is that a DNS server needs to be set up to handle it.  Zeroconf instead uses Multicast DNS, which is a very nice serverless solution that is much easier for users to set up.

EDIT: I left out an important step!

you need to edit the following file (with sudo) **/etc/default/avahi-daemon**
it contains one line, change it to say **AVAHI_DAEMON_START=1** (why they do this, I don't know)

---

### Post by maniacmusician on 2007-02-19
Yes Zeroconf does sound a lot nicer than a DNS server...wonderful. Too bad it's not implemented yet.

You have obviously seen my other thread on this board, about the file server. I was thinking of setting it up as a DNS server as well, until Zeroconf is implemented by default in Ubuntu. Of course I still have to research how to do that, but that doesn't seem like too big of a deal.

Thanks a lot for your dedicated answers, and that includes everyone who responded. I at least learned some new things during the course of this day.

---

### Post by gradedcheese on 2007-02-19
Zeroconf is implemented!  And avahi is totally stable (not some beta-quality stuff).  It's just not fully utilized by default, which indeed makes you do a little work to set it up.  

What I'd like to see in a future Ubuntu is something like, when you enable the SSH server (via a GUI?) the system asking "would you like to advertise the SSH service?", same when you enable Samba networking, and so on.  As long as that's done nicely and respectfully, I think users will really like it.  Then we'll be on par with Macs as far as painless networking goes, and Windows users will keep suffering with their Netbios and assorted MS 'stuff' :)

oh, by the way, you can right-click on your Service Discovery applet and in Preferences add services to discover.  If you have any HP network printers on your LAN, chances are you'll find them.  it turns out they're all zeroconf-enabled right from the factory :)

---

### Post by maniacmusician on 2007-02-19
Well, the "little work" is what I meant by "implemented." I guess it is truly implemented, but as you said, it still needs to be fully utilized.

I don't mind that I have to install an SSH server myself. It certainly isn't something that **has** to be included by default. I'd be happy if I could just ping using hostnames right out of the box. And then, when I do install SSH, it would ask me (as you mentioned) if I wanted to "advertise" it. We're really pretty close to this. I don't think it would have to be through a GUI. Apt could initiate the query whenever it detects that an advertisable package has been installed (of course, we'd have to add flags for this in the packages...)

Your last paragraph doesn't apply to me, I'm using KDE. Do you know where that option is in KDE? I'm sure it's hiding somewhere.

---

### Post by gradedcheese on 2007-02-19
hmm... I don't know much about KDE.  You can do this though:

sudo apt-get install avahi-discover

(and then run avahi-discover).  It's a very basic Avahi discovery program written in Python, it uses GTK (ie: Gnome's toolkit of choice) but it will run fine in KDE.  I don't know if anyone wrote an Avahi applet for KDE yet though.  If you want, you can use Avahi from the command line too (type avahi-<tab> to see a list of tools).  Unfortunately you need to know a bit about services and stuff for that to make sense.  Try:

```

avahi-browse _workstation._tcp

```

(control-C kills it).  This will show you any Avahi-enabled workstations nearby.  Similarly,

```

avahi-browse _ssh._tcp

```

as far the the 'implemented' -- I think all they need is to enable mdns in nsswitch by default in Ubuntu, plus ensure that Avahi always runs.  That would take care of name resolution.  I will try out Fiesty Fawn this week and I hope to see it there.

---

### Post by maniacmusician on 2007-02-19
Cool, thanks, that all looks good.

If name resolution works in feisty, that'd be perfect. It amazes me how far Linux and Ubuntu have come.

---

### Post by keithweddell on 2007-02-19
You could look at something like Dnsmasq for an easy DNS Server.  A basic configuration reads the /etc/hosts file on the server (so you only have to maintain one /etc/hosts file on the network) and broadcasts the hostnames to the rest of the network.  It can get more complicated if you need to but a basic configuration is very simple.

Keith

---

### Post by RandomJoe on 2007-02-19
Ah, someone beat me to it - I was going to suggest dnsmasq as well.  I use that here. 

What do you use for a gateway/firewall?  I have put an old (700MHz) system into service for that function (and that's overkill - I used to have a 233MHz machine there) and its primary functions are to run iptables for a firewall/masquerade (NAT), and dnsmasq to provide DHCP for my LAN and DNS as well.  It's a single config file, insanely easy to configure when compared to 'bind', and runs great.

There are two ways to handle internal mappings.  First, as mentioned, you can add internal machines to the /etc/hosts file of the machine running dnsmasq (doesn't have to be a firewall machine, just one that you aren't reinstalling all the time! ;) ) and it can get them there - but this requires either fixed IPs for all machines or setting in the dnsmasq.conf file a specific IP for each MAC address.  

The alternative (and what I do) is to simply uncomment the first line of /etc/dhcp3/dhclient.conf on each Ubuntu machine and set the hostname to whatever I want that machine to be called.  Dnsmasq will then record the hostname provided when it gives out an IP.  This annoys me a bit - I don't have to do this with Slackware or (cough) Windows!  Both of those will by default send the hostname along when requesting and IP.  But it's a simple edit.  (Granted, one you have to do each time you reinstall...)

---

### Post by hugmenot on 2007-02-19
Can&#8217;t your router add the DHCP leases as hostnames into its own DNS repeater?
That sounds awful but it really is only a checkbox on my router&#8217;s config.

---

