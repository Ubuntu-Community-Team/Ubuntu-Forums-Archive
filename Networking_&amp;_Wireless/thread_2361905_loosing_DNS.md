---
title: "loosing DNS"
date: 2017-05-22
forum: Networking &amp; Wireless
---

### Post by danielsender on 2017-05-22
Hi,

I have 16.04 installed on a Dell Precision 340 (i686). The problems is that DNS stops working after a while. It's OK right after I boot, but after some time it cannot access a node by its name. On the other hand, if I enter an IP then I can ping or log on.

Thanks.

---

### Post by Jason_Hunter on 2017-05-24
yes, I've had this exact problem and I search all over the net, but onone else had the problem. I've set my dns to static. Sorry, I can't help; just want to chime in that you're not alone;)

what I did was: 

rm /etc/resolv.conf
echo "nameserver 8.8.8.8" >> /etc/resolv.conf

it's a hack, but it works.

---

### Post by danielsender on 2017-05-24
Actually it seems that we're not alone on this. This people ( [https://www.digitalocean.com/community/questions/how-to-fix-the-march-2017-ubuntu-dns-resolution-issues](https://www.digitalocean.com/community/questions/how-to-fix-the-march-2017-ubuntu-dns-resolution-issues) ), had the same issue. I followed the recommendation but I'm not sure that it was the fix, because this problem was occurring when the system was just updated/upgraded. But for some magic reason, that could be because I managed to upgrade again, I get DNS OK. I'll see if the problem re-occurs.

Best,

Daniel

---

### Post by danielsender on 2017-05-25
It lost DNS again, so the upgrade didn't help at all. I wish that one of the networking gurus would take a look at this. The interesting thing is that I have a few different machines on 16.04, both 32b and 64b and this is the only one that has this problem.

---

### Post by mzhussein on 2017-05-25
Hi all,

I'm new to the forum (but been snooping for an age).

I have an ubuntu machine that was working swimmingly till a couple of days ago, I upgraded the CPU/Mobo/RAM (Ryzen 5) and thought it a good idea to upgrade all the packages etc. - It's a Plex server, so DNS downtime is noticed quickly.

I am now losing DNS sporadically (sometimes works for a few hours, other times 10 mins), only comes back after a reboot.

It looks like I'm not the only one having this problem.

Anyone got any ideas here?

(Motherboard: ASUS B350M-a, CPU: Ryzen 5 1500x)

EDIT:
I have subsequently purchased another case, PSU & hdd, so will perform a fresh install on the new kit and roll the old system back to the old (known good hardware) with the upgraded software - hoping to do this tonight.

---

### Post by johndough2 on 2017-05-25
Hi

Apologies, but I am not a regular ubuntu user, and can only offer a windows solution that can be adapted I'm sure, and is the 'automation' of the 8.8.8.8 option above.


[INDENT] 
[LIST]
[*]ping  – command sends an echo request to a given host regularly
[*]8.8.8.8 – is the IP Address for [Google Public DNS]("http://code.google.com/speed/public-dns/docs/using.html")
[*]-t option – instructs ping command to ping the specified host continuously.
[*]-l 0 option – instructs ping command to send only 0 bytes and  receive only 8 bytes of data per request (this is used to avoid unwanted  bandwidth wastage by using default value of 32 bytes)
[/LIST]
 [/INDENT] This will keep a connection open with  Google Public DNS server and server will keep sending data to your  computer, which helps in keeping the internet connection alive. If you  are going to use this command frequently just create a BAT file with  above command and place it in your desktop. [BAT file that can be used to keep internet connection alive can be downloaded HERE]("http://www.ayomaonline.com/?download=KeepAlive.bat").

Adaption is something like this......

[h=2]Create the Keepalive Bash Script[/h] 
[LIST]
[*]Launch the Terminal (located in /Applications/Utilities/)
[*]Type the following command:nano keepalive.sh

[*]Paste in the following, be sure to replace the IP with your own routers:#!/bin/bash
ping -i 5 -n 192.168.1.1

[*]Hit Control+O to Save the contents of keepalive.sh
[*]Hit Control+X to exit from nano
[/LIST]
 [h=2]Run the Wi-Fi Keepalive Bash Script[/h] 
[LIST]
[*]Back at the command line, we have to make the script executable, we do this with:chmod +x keepalive.sh

[*]Now to run the keepalive script, we type:./keepalive.sh & 
[/LIST]
 That last command starts and runs the keepalive.sh script in the  background. Your wireless connection should stay alive now and dropping  should come to an end.
 The idea of creating a simple bash script comes from [Ahmet C. Toker]("http://actoker.blogspot.com/2011/08/mixed-up-confusion-how-i-solved-mac.html"),

---

### Post by danielsender on 2017-05-28
I'm not sure if I can be calling my finding as a SOLVED case, but in any case this is it. Looking at my network manager applet I noticed that the system wrote two instances of the Ethernet connection: "Wired connection 1" and "eth0". They had identical configurations. So I deleted the "eth0" connection and apparently DNS is working now. Don't ask me why.

Daniel

---

