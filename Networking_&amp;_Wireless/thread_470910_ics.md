---
title: "ics"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by TheOtherLinuxFreak on 2007-06-11
hi,
i just converted my parents to ubuntu! there pc is running ubuntu 704. 
i cant figure out how to make the ubuntu box to share its internet connection with the xubuntu box. they are connected with a crossover cable. the ubuntu box has 2 network cards.  the ubuntu box is connected to a dsl internet connection. i can ping between them. this worked in windows. also i installed firestarter in the ubuntu box and it says that "eth0 is not ready" maby that has something to do with it?

thanks for your help:)

---

### Post by TheOtherLinuxFreak on 2007-06-11
now i figured something else out.
the Ubuntu box doesn't connect to the internet if the ip isn't set to dhp. firestarter doesn't work unless eth0 has a static ip.

---

### Post by TheOtherLinuxFreak on 2007-06-11
ok now i fixed firestarter but the ics (internet connection sharing) still doesn't work.

---

### Post by hartz on 2007-06-11
If you use PPPoE you will have to install something on your Ubuntu machine to do the Internet connection sharing with NATing.  If all you need is web access, then a Web Proxy server is sufficient, otherwise you will need something more advanced.

If your router does the NATing, you can just make the Ubuntu machine route between the networks.

These are two quite different topics, so you need to first answer this question. Do you use PPPoE (With your Router in bridge mode) to connect to the internet, or does the router itself log in and perform NATing and Firewalling?

If you really don't know there are many ways to find out, eg how did you set up your internet connection, what IP does your Ubuntu machine have on the port connected to the Router, or is it a USB modem, Does your router have a web based interface by which you can manage it, What is the default gateway address on the Ubuntu box, etc.

This may sound like a very confusing post and may not help you at all, but actually what I'm doing here is I'm just throwing a bunch of ideas at you, you may recognize one or more of them and be able to give more information on your setup.  That will help us help you.

So some basic questions:
1. Can you check your network configuration on the Ubuntu machine, (The one sharing the internet connection out).  You can get network details from these two commands, which you enter in a terminal:
ifconfig -a
netstat -rn

2. How is your internet connection set up?  Did you configure it manually, eg by setting up a Modem connection in the Networking Tool under System->Administration->Network

3. Do you have a USB router?  If not, does your router have additional Ethernet ports?  If not, do you have a spare Ethernet switch/hub lying around?

4. Would you want to set up caching web proxy on the Internet connection sharing machine even if you can get away with a simpler setup, i.e. to get the benefit of caching?

---

### Post by TheOtherLinuxFreak on 2007-06-11
the ubuntu box act like a router. it is connected to the internet. the xubuntu box is hooked up to it with a croos over cable. the pcs all have static ips.  this worked fine when what is now the ubuntu box had windows xp. oh and yes i use pppoe

---

### Post by hartz on 2007-06-12
With PPPoE it means your Ubuntu box is "directly" connected to the internet.  In this case Ubuntu is not routing (as in the TCP/IP meaning).

You have two options.
1. NAT/masquerading :- Here is an [Internet Connection Sharing Guide]("https://help.ubuntu.com/community/InternetConnectionSharing").
 ... or ...
2. If all the Xubuntu machine needs is Web access (HTTP), then a Proxy server (oops, polipo, squid, even non-caching proxies like tinyproxy) will all work.  Polipo is very easy to get to work.  Search for a web proxy server in Synaptic and pick your poison from there.

Option Nr 1 allows you to access Instant messaging, VoIP, Games, Peer-to-peer, etc from the Internet.  Basically anything which wants to make incoming connections becomes possible (but doesn't become easy)

Option Nr 2 Allows only HTTP, and possibly some other protocols like SMTP or FTP, and is fairly simple to setup (Install and forget)

Option nr 1 requires that the xubuntu system be given the name of the Ubuntu box as default gateway.  You can do this in the System->Administration->Network applet, go to the properties of the network connection, and then set the Default Gateway address to the IP of the Ubuntu box.

Option nr 2 requires you to set the IP of the Ubuntu box in the Proxy Server field of the web browser on the xubuntu box.  You also need to tell apt that the ubuntu box is the proxy server.  There is a System->Preferences->NetworkProxy applet where you can also set it.

---

### Post by TheOtherLinuxFreak on 2007-06-13
i couldnt get the internet connection sharing guide or the proxy server to work. can you explain step by step how to do option nr 2? im still a linux newbie:)

---

### Post by hartz on 2007-06-14
OK, the simplest is to install Squid3 Proxy software.

When I talk about the [COLOR="Red"]Proxy machine[/COLOR], I mean the one directly connected to the Internet, and when I talk about the internal network, I mean the network, cables, interfaces, etc that connect the two Linux systems to one another.  The "client" the the computer that doesn't have a direct connection to the internet.

Squid is a caching proxy server. and you will find it in the apt package repositories if you search (using synaptic for example).  You need to install it only on the [COLOR="Red"]Proxy machine[/COLOR].

This program runs in the background as a service and accepts ("intercepts") connections for web page requests from any machines on your internal network.  It then re-issues the the requests itself to the website, downloads the pages, and passes the page data back to the client that originally requests it.

At the same time as it passes the data back to the client, it keeps a copy on local disk (Stored under /var/spool/squid3 on the Proxy machine), so that a future request for the same page can be served from this cache, even if a different client requested the page, thus saving bandwidth and time.  There are many rules implemented, for example https (secure pages) cannot be cached in a meaningful way, and other pages are dynamically generated, so they should not be cached as it doesn't make sense.  Pages stored in the cache also expire after some time, usually several days - this is something which can be set by the web site, based on how often their information changes, and you can override some of the rules in the squid3 configuration.

So on to configuring Squid.  The installation comes with a well documented config file.  Open the config file in your favorite text editor.  You may use this command (in a terminal):
```
sudo gedit /etc/squid3/squid.conf
```

(The sudo bit at the front means you will assume root use (Super-User) privileges, which allows you to save changes the squid config file.  This config file is rather large but you only need to change a few things.

Basically you just need to allow "Remote clients" on your internal network to connect, so look for the line about halfway through the config file that reads 
```
#http_access allow our_networks
```

Uncomment this line (remove the leading #-sign), and add a newline to define "our_networks" above it.  When you're done it should look like this:
```
acl our_networks src 192.168.24.0/24
http_access allow our_networks

```

Replace the network address where I've got [COLOR="SeaGreen"]192.168.24.0[/COLOR] with whatever applies to the network between your two directly connected systems.

Everything else should work with default values, but you can also change the listening port if you like.  This value is near the top of the config file.

Once done, save your changes.

For the changes to take effect, you need to restart Suid.  This command will do that:
```
sudo /etc/init.d/squid3 restart
```

Now you have Squid running you need to configure the web browser(s) to use it.  On the client machine(s), fire up Firefox (gedit?) and go to Edit -> Preferences -> Advanced -> Network -> Connection Settings.  Select Manual Proxy and enter the IP address of the proxy machine (The internal address that is).  Also enter the port number, use whatever you have specified in the squid.conf file (If you did not change this, the default value is port nr 3128)

For best results you should do the same change to the web browser running on the proxy machine itself!  Even though it COULD access the web directly, many pages that you access from this machine will be cached on disk and then be faster to access fro the cache for the other client running on the xubuntu system, and visa versa.

Note:  There are other programs that may need to be configured to use the Proxy service.  Most notably Synaptic (Settings -> Preferences -> Network), and it is sometimes useful to set it in The Gnome menu under System -> Preferences -> Network Proxy.  Getting all of your Linux machines to download updates and software via the cache of the proxy can save you considerable bandwidth!!!!

I believe for automatic updates to work you need to edit the apt config file on the client.  Right now the format of this file evades me, but you can search for it.

---

