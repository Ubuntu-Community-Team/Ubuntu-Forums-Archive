---
title: "SSH without static ip?"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by jseiser on 2007-08-05
My laptop will be getting here soon ( :) ) and i wanted to be able to access files on my desktop while im at school.  I connect to my internet with dhcp so i cannot just tell my laptop the IP to connect to.  Isf it possible to still ssh into my computer and **** with the files?  I would like to be able to transfer back and forth, and maybe even play the music I have on my desktop on my laptop at school.

---

### Post by dfreer on 2007-08-05
Check out dyndns.com or no-ip.com, or one of several other dynamic host name clients. Basically, you register a domain name, install a piece of software that "phones home" to the respective company with your current IP address, and they map the domain name to that IP address. Everytime your IP address changes or X amount of minutes, it phones home again and updates your current IP.

This normal involves some setup on your part (opening the respective ports on your router, installing the SSH server), but you should be able to accomplish this as long as your ISP doesn't block inbound ports. Best of all, you can do this for free ;)

Let us know if you need help getting it working!

---

### Post by MrFSL on 2007-08-05
Well here is something I do.

I put a small web page out there named ip.shtml containing the following:
```
<!--#echo var="REMOTE_ADDR" -->
```

Connecting to this page simple gives you your real IP address.

Then you can write a small CRON script that uses wget to download this webpage, which, when parsed by your script will just have your IP address. You can then have it email that information off to you at a regular interval. I recommend gnome-scheduler to help setup your CRON job.

---

### Post by jseiser on 2007-08-05
the no ip linux client set-up looks painless and i know i can make it autostart.  MrFSL's , where would i host this webpage? and how would i connect to it if its on my desktop computer if i dont have a ip address to connect to it with?  Im confused by your method :)  I also dont want to run gnome at all and i dont know what CRON is or how to script it :)  The only problem i can see with the no ip way, is how to open ports on my router (Linksys BEFSR41) when i cant tell it what IP to open them on.  I used to open it for bittorrent when I was on windows a year ago because i could set-up a static ip.  I cant seem to set up a static ip on linux (dont know why).   When i log into my admin part of my router, there is a port range forwarding section which i used to open the port for 192.168.1.137 but that doesnt work because thats not my internal ip address.  I can install ssh with just apt-get install ssh so i think i can handle that.  I dont have my laptop yet so i dont know if its worth starting to set-up till it gets here.  My girlfriends computer is plugged into the same router and on windows, so i dont kow if i can test it from hers?


i see i need to port forward port 22 for a standard ssh port, i need a static IP set-up on my lan for this to be able to be done correct?  So i think i will have to set-up a static internal IP?

r?

---

### Post by MrFSL on 2007-08-05
Alrighty...
You connect to the internet using DHCP which dynamically assigns you an IP address.

You could use any free hosting solution like [angelfire]("http://www.angelfire.lycos.com/"). You create a file named ip.shtml containing:
```
<!--#echo var="REMOTE_ADDR" -->
```

You upload this file to your free website. Then you write a script which uses wget to download this webpage. The downloaded file should be a text file which contains your computers dynamically issued IP address. This could be something similar to:
```

#!/usr/bin/perl

#Get Real Local IP Address
system ("wget http:\/\/YOUR_ANGELFIRE_ADDRESS\/ip.shtml -O \/tmp\/ip 2> \/dev\/null");
@ARGV = qw/ \/tmp\/ip /;
chomp ($localip = <>);
print "$localip\n";

```

Then using something like sendmail you can continue this script to create and send you an email with the actual email address of your home computer. You would open up port 23 on your router and point it to your desktop. Using a scheduler (such as cron) you can have this email sent to you at regular intervals. Then, from the laptop you could ssh with this address. 

If I have totally confused you then perhaps I can help you script it all out after you get the laptop.
I have been considering making this into a howto for some time... perhaps the time is now.

---

### Post by dfreer on 2007-08-05
If you do want to use dyndns.com/no-ip.com, the dynamic IP address from your router will need to be changed to static. The best method to set a static IP in linux is, IMO, editing your */etc/network/interfaces* file. Here's some example syntax, you will need to edit this for your specific network:
```
# /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The 1000 MB network interface
auto eth0
iface eth0 inet static
        address 192.168.1.5
        netmask **255.255.255.0**
        network 192.168.1.**0**
        broadcast 192.168.1.**255**
        gateway 192.168.1.**1**

```
The items in bold are kinda important, but you can change them if you know your subnetting ;) Anyways, after that you can restart your network with a:
```
sudo /etc/init.d/networking restart
```
And additionally, it makes things eaiser if you specify in your router config to always assign that static IP to that MAC address, although it will *generally* work without this step. Let us know if you have any problems installing/configuring the client you chose to use (ddclient is in the official repositories, and I'm pretty sure you can find the no-ip client somewhere as well). Good luck!

@MrFSL
I see what you are saying with your method, although using a hostname with your method would be a bit hard. Let us know if you make a how-to thread ;)

---

### Post by MrFSL on 2007-08-06
@dfreer
Now you've convinced me... a howto is on the way. Give me a week or so to script it out.

> lthough using a hostname with your method would be a bit hard
Not if you use [everydns]("http://www.everydns.net/") there you can (FOR FREE NO LESS) setup a dynamic site which can easily be updated using the same cron script.

---

### Post by dfreer on 2007-08-06
@MrFSL
Just checked the site again, but I still get the impression that you have to already have a domain name to use everydns, as in everydns only provides the DNS servers themselves. is this the case, or do they give out names like [http://dfreer.everydns.com?](http://dfreer.everydns.com?)

---

### Post by MrFSL on 2007-08-06
Well, no, you can buy/register your domain name wherever you'd like. (GoDaddy, etc.)

This is helpful if you are running a true server. 

For jseiser, who just needed to ssh to share files, all that is needed is the remote machines current ip address. There are a million different ways to script this out....

1) Using the method I have described so far, a scheduled job can determine if the IP address has changed and send an email off notifying if it does.

2) Alternatively, the script could determine the actual ip, and use ftp to upload a text file containing it. Then on the local machine we could write a script that pulled that text file down and dynamically inserted it into the ssh...  **EDIT** - This would be kinda cool... double click the script and it dynamically inserts the current remote ip and opens an ssh connection using Nautilus file browser. **END EDIT**

etc. etc.

The possibilities are endless as the imagination and the scripting is quite simple too. The script would execute pretty quickly and could be run every 15 minutes and not even take up any real resources.

What you think? Interested?

---

### Post by jseiser on 2007-08-06
its sad im halfway through a networking class and i have trouble with ..networking :)
My router, a lynksys does not support giving a certain mac address the same ip, i saw that mentioned on the internet and thought it would be the easy method, but then saw where my router doesnt do this :(

here is my ifconfig -a, 

eth0      Link encap:Ethernet  HWaddr 00:11:D8:EC:71:8E  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:feec:718e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1269771 errors:0 dropped:0 overruns:0 frame:0
          TX packets:877301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1428301437 (1.3 GiB)  TX bytes:188648213 (179.9 MiB)
          Interrupt:24 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

# The 1000 MB network interface
auto eth0
iface eth0 inet static
        address 192.168.1.101  <-- would be my local IP
        netmask 255.255.255.0  <--my subnet mask
        network 192.168.1.0   <-lowest ip my computer can assign locally on this network?
        broadcast 192.168.1.255 <-highest possible IP on this network.
        gateway 192.168.1.1                <--guessing? lol

Im at lunch from work, or i would just try :) also, do i need to set any other parameters? I thought i had to edit something to do with nameservers?  I had half of the cisco class done, and i still can not ******* subnet, good thing i am not trying to make this a career.  I can telnet into a router and set it up, but once i have to do it on my own im lost :)

---

### Post by dfreer on 2007-08-06
The way you have your interface file setup now is just fine, it should be ready for use. I believe it grabs the nameserver addresses from the default gateway, although I'm not quite sure (this shouldn't be an issue).

I don't have a linksys router with me now, but I'm thinking it gives out addresses in a pool of like 100-150, something like that. So if you want to avoid conflict with other devices, you might want to set the static IP address of your server to a lower number, like 192.168.1.10

If you can't figure out how to configure the router in order to specify the static address, you probably can just ignore that part. 
[http://forums.speedguide.net/archive/index.php/t-204395.html](http://forums.speedguide.net/archive/index.php/t-204395.html)
Sounds like linksys doesn't support it anyways. No biggie.

---

### Post by n2j3 on 2007-08-07
> **MrFSL said:**
> 
What you think? Interested?

Yep,I am definitely interested. That's something I was meaning to do myself but then I realised something rather important... I cannot code or script anything besides simple DOS batchfiles [-X


So far the only dns resolution I get is from the ipcheck package (I believe it's the one on ubuntuguide), but since my ISP and router are not nice to each other my IP changes at least twice per day. The kind of script you're proposing would be a lifesaver :) Pray, continue.... =D>

---

### Post by MrFSL on 2007-08-07
alrighty,

I will get a howto together this weekend.

---

### Post by jseiser on 2007-08-07
My router on its admin page says 
Start IP address - 192.168.1.100
number of address - 50
DHCP address lease range 192.168.1.100 - 192.168.1.149

so i should make my IP above .149 so DHCP doesnt try and give it to my girlfriends windows copmputer connected to the router correct?  so ip 192.168.1.150 would work with all the same settings?

---

### Post by dfreer on 2007-08-07
Above or below, as long as it is between 2 - 99 or between 150 - 254. so yes, that one line should be all you need to change.

---

### Post by jseiser on 2007-08-13
ok i got the desktop with a static ip, the laptop with a static ip, installed ssh on both of them, and now im trying to configure the no ip.

this guide, [http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html](http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html)  doesnt work because i make the file as root, and then when i try and run no-ip2 it says i dont have permission to access the /usr/local/etc/no-ip2.conf file

so i tried to do with without being root and i can't compile the program.  So im kind of confused :)  any help would be great.

---

### Post by dfreer on 2007-08-14
I'm used to using the clients in the repositories:
[http://packages.ubuntu.com/feisty/net/no-ip](http://packages.ubuntu.com/feisty/net/no-ip)
[http://packages.ubuntu.com/feisty/net/ddclient](http://packages.ubuntu.com/feisty/net/ddclient)

As for the guide, you should do everything as normal user until you reach the commands:
```
make
make install
```
You can add *sudo* to the beginning of each command, and it should work. Does it ask you for your email address etc now, or is it still giving you that error message?

---

### Post by jseiser on 2007-08-16
i can install and set the no-ip program up, it just says it cant find the /usr/etc/local/no-ip client or no ip-2 client.

---

### Post by dfreer on 2007-08-17
Try these commands to do a search for the client:
```
sudo updatedb
locate no-ip
```
Maybe also:
```
locate noip
```
```
whereis no-ip
```
```
whereis noip
```

One further location that it might be installed at, /usr/bin/
```
ls -l /usr/bin/
```

If you still can't find it, I'll run through guide and see if I can get it working.

---

### Post by MrFSL on 2007-09-09
@All 
Sorry about the delay. Things have been rather busy.

**The Problem**
You have a server without a static IP and you need to remotely access this computer for whatever reason (be it http, ssh, etc.). How do you know what the ip address is at any given time? This becomes especially difficult if you use NAT and the server's address is not necessarily the same as the actual gateway address. 

**A Solution**
You can build a simple perl script to handle this according to your needs. In summary we are going to create a web page that identifies our real ip address. Upload it to the web and get our real ip. Then we are going to use our real ip to build a webpage that we can access which will notify us of our actual ip address.

****NOTE**** To overcome the NAT issue you need to first configure your gateway (router) to forward the necessary ports to the server. Check with your gateway manufactures as this is beyond the scope of this post.

**Step One**
We need some free space on the great World Wide Web. You can get some free  web space from the people over at Angelfire ([http://www.angelfire.com](http://www.angelfire.com)). Sign up for a free Angelfire account. When you are finished your account should be something like: http://<username>.angelfire.com/ (For example: [http://mrfsl.angelfire.com/](http://mrfsl.angelfire.com/)).

**Step Two**
Copy and paste the following and save it as _fsl.IPUpdate.pl_
****NOTE**** You need to replace "username" and "password" on line 10 and line 11 with your new Angelfire username and password **in quotes**.

```
#!/usr/bin/perl

# fsl.IPUpdate.pl - by: MrFSL (ubuntuforums.org)
# Version 1.0 

use Tie::File;
use Net::FTP;
use LWP::Simple;

# Replace username and password with your angelfire username and password
$username = "username";
$password = "password";

# Create ip.shtml
tie(@ip_webpage, 'Tie::File', "./ip.shtml") or die $!;
$ip_webpage[0] = '<!--#echo var="REMOTE_ADDR" -->';
untie @ip_webpage;

# Upload ./ip.shtml
$ftp_angelfire = Net::FTP->new("ftp.angelfire.com");
$ftp_angelfire->login("$username", "$password");
$ftp_angelfire->put("./ip.shtml");
$ftp_angelfire->quit;

# Getting Current Real IP Address 
#	line 1 should have ip (i.e. $temp[0])
$temp = get("http://$username.angelfire.com/ip.shtml");
@temp = split(/\n/, "$temp");

# Create ip.html
tie(@current_ip_webpage, 'Tie::File', "./ip.html") or die $!;
$current_ip_webpage[0] = $temp[0];
untie $current_ip_webpage;

# Upload ./ip.html
$ftp_angelfire = Net::FTP->new("ftp.angelfire.com");
$ftp_angelfire->login("$username", "$password");
$ftp_angelfire->put("./ip.html");
$ftp_angelfire->quit;

# Clean Up Temp Files
if (-e "./ip.shtml") { unlink "./ip.shtml"; }
if (-e "./ip.html") { unlink "./ip.html"; }

```

**Step Three**
Make the file executable:
```
chmod 744 ./fsl.IPUpdate.pl
```

**Step Four**
Run the file. It should create 2 web pages on your angelfire webspace. If you browse to: [http://username.angelfire.com/ip.html]("http://username.angelfire.com/ip.html") You should see your ip address. (Again replace 'username' with your angelfire username.)

**Step Five**
If everything worked then all you have to do is schedule this script to run as often as you would like. I think gnome-schedule is a good application for setting up this scheduling.
```
sudo apt-get install gnome-schedule
```

**CONCLUSION**
Now whenever you need to access your server you can go to your angefile webpage and find the most current ip address.

For those that want to provide public services (like hosting their own webpages) this can be easily edited to send email notifications when your ip had changed and/or update your dns records. For more information on easily sending email check out sendEmail [http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/).

Personally I use everydns.net as my dns registrator and am able to extend the above script to automatically update my ip address with them should it change.

---

