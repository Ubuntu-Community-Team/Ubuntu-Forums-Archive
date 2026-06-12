---
title: "Kubuntu network configuration problem"
date: 2005-04-11
forum: Networking &amp; Wireless
---

### Post by aliban on 2005-04-11
Hello, I tried to install Kubuntu on my (old) Sony Vaio SR1K.

As the CD-ROM is plugged in the only PCMCIA i was not able to setup my PCMCIA eth card. The installer is able to detect and setup the eth card but unfortunately the CD-ROM is not found after switching the PCMCIA card again. Therefore i installed Kubuntu without network configuration.

The system boots fine, and KDE starts, too. Then I go to "Control Center" and added IP, gateway and dns  in "Network Settings" in Administrator mode.

The IP seems to work (can ping other machines) but the gateway and DNS refuses. The textcontrols of the gateway ip is always empty when i reload the dialog and i am not able to reslove an url. ifconfig says that eth0 is up but there is no DNS/gateway. Another strange thing is that when i try to add a DNS server it says "You have to type an alias first"... no idea what this means... This is already the second time I installed Kubuntu. last time the whole KDE refused to open any dialogs that require admin rights (each time i entered a pwd the dialog(s) imediately disapeared)

Help me please...

Another thing is that the gfx driver is not working corretcly? in some controls in KDE I can see strange colors/lines...

what is up here?

---

### Post by hbchrist on 2005-05-03
I am having this same issue with "You have to type an alias first." As I am still newish to linux, this is beyond my experience.

I am using a static IP. I used the exact same IP, gateway, and DNS settings on a WinXP system, and I could access the internet with no problems. With the (K)ubuntu computer, I can ping the gateway, but I can not ping the DNS servers nor can I access the internet. 

When I try to ping the DNS servers from a terminal session, I get "network is unreachable", yet it *is* reachable from with WinXP. For the record, the DNS servers and the gateway are on different subnets.

I hope someone can explain this. I have and am still pouring over the forums to see if this has been discussed, but, besides these two posts, I haven't seen exactly this issue reported.

TIA,
hbchrist

---

### Post by hbchrist on 2005-05-03
I found a solution that works for me in a thread at linuxquestions.org.

The Kcontrol interface has the option of adding the default gateway, but whatever I put in there never "sticks". So I used the command:

sudo route add default gw xxx.xxx.xxx.xxx

This change actually "stuck", and I was immediately able to get out to the internet. By not having a default gateway, DNS traffic was not routed to the DNS servers, which were on a different subnet. 

hbchrist

---

### Post by hbchrist on 2005-05-04
Followup:

After powering down the laptop, I rebooted to discover that all of my internet settings had remained *except* the default gateway. I had reset to empty, but executing the route add command from the post above once again freed me up to net access.

I don't know why this issue persists. I don't experience anything like it in Ubuntu, so maybe there is something odd about the Kubuntu build? This is strangely out of place as is the need to run "sudo kcontrol" from the terminal session in order to edit network settings. 

I'll report the bugs so hopefully these two items can be fixed or someone can fix me.  :wink: 

hbchrist

---

### Post by dmorgan on 2005-06-10
Well, I'm sure you've already solved your problem by now, but to help those in web-search land....  I've had this same problem.

Backup, and edit the file /etc/network/interfaces.  You should see a section like this:

# The primary network interface
iface eth0 inet static
address xxx.yyy.zzz.qqq
netmask 255.255.255.0


Note the absence of a "gateway" entry.  Just add the following line:

gateway xxx.yyy.zzz.qqq

but with your appropriate gateway, of course.  Then restart your networking:

./etc/init.d/networking restart.

Hopefully, you should be all set!

 \\:D/

---

### Post by berserker on 2005-06-26
[QUOTE=hbchrist]sudo route add default gw xxx.xxx.xxx.xxx[/QUOTE]

Beautiful!  Worked for me too.

---

