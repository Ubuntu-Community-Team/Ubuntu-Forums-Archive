---
title: "DNS problem with Huawei E226 ubuntu 8.10"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by fduppa on 2008-10-29
I have Ubuntu 8.10, and today I received a usb dongle to have mobile broadband. I followed the cute wizard that Network Manager gives me, and the modem connects.

The problem is that ubuntu selects "10.11.12.13" and "10.11.12.14" as DNS servers.. and those are not working. (if I type google's IP in firefox I can get to googles webpage, so the connection works, it's just a DNS problem)

I edited these two files
/etc/ppp/resolv.conf
/etc/resolv.conf

removed the wrong ones, and placed the DNS servers from my provider, but it didn't work. I restarted the pc (just in case :confused:) and tried... it didnt work.

Then I checked the resolv.conf files and 
/etc/ppp/resolv.conf was like it was at the beginning: 10.11.12.13 and 10.11.12.14. no signs of my edits.

Then I tried to go to networkmanager, mobile tab, click on edit and went to the tab about IPv4 conf. and placed DNS manually to 127.0.0.1 (I have my own DNS)... after connecting, the DNS for the connections are "10.11.12.13"

It is ignoring _completely_ which dns i want it to use. It just goes with 10.11.12.13 and 10.11.12.14.

How can I fix this?

¿Is there a way to redirect outbound connections to 10.11.12.13 to 127.0.0.1 or any other DNS service like OpenDNS?

---

### Post by miclaro on 2008-11-03
I get the same problem, it ignores my dns settings saved to the network manager profile.
But if I manually edit /etc/resolv.conf after the connection is made and enter the correct DNS values, I get it working.

Any help would be appreciated.

---

### Post by fduppa on 2008-11-04
thank god i'm not the only one with this problem. I thought I was crazy.

---

### Post by superprash2003 on 2008-11-04
try this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Exavier on 2008-11-09
To fduppa

Where did you find the driver for Huawei e226 for Ubuntu 8.1? Thanks!

---

### Post by caue.rego on 2008-11-21
> **superprash2003 said:**
> try this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

Just caching the relevant steps of that link in here:
> 
This is a small tutorial to help you configure DNS servers in linux.Typically ISP's DNS servers are very slow primarily because they are overloaded and cannot handle so many requests.opendns a DNS service has some really good DNS servers which are faster,more secure and definetly more reliable..The most important being FASTER.So this tutorial will help you change your DNS server from your ISP's DNS servers to OPENDNS servers.
Firstly, so that you know, opendns server ips are 208.67.222.222 and 208.67.220.220 .. typically two server ips are given,even from your isp.The first one is called Primary DNS server and the second is called Secondary DNS server.
OK, now on to the procedure..Its simple!!

Step 1:Go to Applications->Accessories->Terminal and type
sudo gedit /etc/dhcp3/dhclient.conf . You will be asked to type in the sudo password.After which the dhclient.conf file will open
Step 2:This is where you enter the DNS information.Go to the end of the file and add the following line to the END of the file
prepend domain-name-servers 208.67.222.222,208.67.220.220;
Step 3:Save the file and close it.
Step 4:Thats all, now you will be using opendns servers whenever you use the internet

I have experienced a major change in the speeds while using opendns servers.They are indeed very fast.Hope this helps! 

It seems like a nice idea: make the DHCP set up always the same DNS, pointing to a good, reliable fast server. The only problem is that it didn't work, and I still have to freaking edit /etc/resolv.conf and manually add my nameservers there everytime I connect to my huawei modem.

This also doesn't help:
[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)
It only says to do the samething I already do. I certainlly will research more into this later, but in the meantime I'd appreciate if someone could clarify what's going wrong and how to fix this.

---

### Post by andis.machine on 2008-11-25
Hi there!
I read this post and it was some help for me.
But I digged myself a bit in the configuration because I had to configure this modem in the 8.04 version.
 What I suggest is to edit the file '/etc/ppp/peers/provider' and to comment the line 'usepeerdns'. To commento meens to put a '#' at the beginning of the line.
Obviously I still edited the '/etc/resolv.conf' and '/etc/ppp/reslv.conf'.
 I also commented the same line (usepeerdns) in the file '/etc/ppp/peers/wvdial'.
I don't know which one is the one that matters, maybe all are. The thing is after I did this the dns that appear are no longer replaced by 10.11.12.14. But they use the ones I placed mannualy.
I hope it helps!

---

### Post by caue.rego on 2008-11-26
> **andis.machine said:**
> Hi there!
I read this post and it was some help for me.
But I digged myself a bit in the configuration because I had to configure this modem in the 8.04 version.
 What I suggest is to edit the file '/etc/ppp/peers/provider' and to comment the line 'usepeerdns'. To commento meens to put a '#' at the beginning of the line.
Obviously I still edited the '/etc/resolv.conf' and '/etc/ppp/reslv.conf'.
 I also commented the same line (usepeerdns) in the file '/etc/ppp/peers/wvdial'.
I don't know which one is the one that matters, maybe all are. The thing is after I did this the dns that appear are no longer replaced by 10.11.12.14. But they use the ones I placed mannualy.
I hope it helps!

i'm sure that will help someone who isn't using NM 0.7, which isn't exclusive for ubuntu 8.10, but you don't get it by default on 8.04 and ppl usually have solved wireless broadband issues with wvdial and pppconfig, which is probably what you're using. so, thanks for sharing and contributing! :)

in my case, as soon as it disconnects, NM will clear resolv.conf, so that alone already shows editing a line "usepeerdns" wouldn't solve my issue. i've also been trying using resolvconf package with no luck so far... and i still find man pages quite confusing and lacking good examples of usage, specially NM ones.




btw...

> **Exavier said:**
> To fduppa

Where did you find the driver for Huawei e226 for Ubuntu 8.1? Thanks!

as far as I know, linux don't use "drivers", and intrepid ibex doesn't even need anything added to work with any Huawei.

---

### Post by caue.rego on 2008-11-26
ok, I got it working now, and in a good way.

i still don't know how the hell network manager works, but, i do know that resolvconf exists exactly because of programs like network manager conflicting with one another fighting for setting the machine nameserver (which is done in /etc/resolv.conf).

so, i got resolvconf working after reading this:
[http://ubuntuforums.org/showpost.php?p=712483&postcount=10](http://ubuntuforums.org/showpost.php?p=712483&postcount=10)

all i did was setting my **/etc/resolv.conf** right (as usual) and then typing:
```

$ resolvconf -u

```

but it could also have been done by direct editing /etc/resolvconf/run/resolv.conf

there's still some odd behavior, but i'll read more on that later on. at least it's working. [/lazy] :P

---

### Post by luispic on 2008-12-05
Hello everyone!! I'm configuring a small imedia linux distribution on a minibox embedded board to build a home made open source router for my "tigo" hawei E226 modem, and I was having the same problem, I found the solution after reading this thread and doing a couple more things:

First I added this line in thw wvdial.conf (which for my distro is in /etc/wvdial.conf):

Auto DNS = off

Because my problem was that the DNS my provider "sents", or at least my modem detects, wheren't any good either, so with that line on the wvdial.conf you avoid your "resolv.conf" file from being written over by the wvdial dialer. More info on this ([http://linux.about.com/od/commands/l/blcmdl5_wvdialc.htm](http://linux.about.com/od/commands/l/blcmdl5_wvdialc.htm))

I commented the line on my /etc/ppp/wvdial file "usepeerdns" (like andis.machine suggested) and finnaly I ran "pppoe-setup" and specified my two DNS servers.

In the end I Re-edited the /etc/resolv.conf and put the correct DNS servers, and it has been working ever since.

hope this info helps! :guitar:

---

