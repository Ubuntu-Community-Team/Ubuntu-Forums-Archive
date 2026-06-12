---
title: "Problem with VLAN on ubuntu 22"
date: 2024-01-05
forum: Networking &amp; Wireless
---

### Post by bueno5000 on 2024-01-05
Hello Ubuntu masters,

I have setup a VLAN (192.168.2.0) in my home router, I want to have a separate LAN for a host and its virtual machines. Weird thing for all my VMs (ubuntu servers 20)  I simply go in the /etc/netplan config file and just change my ip to a static one like this: 

network:
  version: 2
  ethernets:
    enp0s3:
      dhcp4: no
      addresses: [192.168.2.101/24]
      gateway4: 192.168.2.1
      nameservers: 
        addresses: [8.8.8.8,8.8.4.4]


And they take that ip and can talk to each other via ssh without any problem in the 192.168.2.0 VLAN, they can also reach the internet. The VMs are all with a bridged network adapter (setup in Vbox in the host). 

However, with the host itself I have problems doing that, when I change the ip to a static one in the same fashion I have my wifi connection that stops to work and has a question mark on it (the host is on Ubuntu 22 desktop)

I'm not very good yet in networking... I asked chat gpt but he took me for a ride of configs for hours and it never worked. 

How can I make my host go on the 192.168.2.0 VLAN and give it a static ip adsress inside that VLAN ?
I've put this and it doesn't work: 
ip 192.168.2.90
gateway 192.168.2.1
netmask 255.255.255.0   (/24)

What I don't understand is if I setup a static ip in the base network that is 192.168.0.0 like this: 
ip: 192.168.0.90
gateway: 192.168.0.1
netmask 255.255.255.0  (/24)
It works and I have my static IP

I don't know if this has a link with tagged packets or routes, I've tried a lot of things but I can't get it to work...

Thanks a lot! JF

---

### Post by TheFu on 2024-01-06
You need to post using forum code tags, or nobody can help you.  Edit the post above and fix that first.  netplan YAML is indention space sensitive.
Any text in a terminal or text config file needs to be wrapped in code tags.

[Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) is how.  It is easy, so if it is hard, you aren't doing it correctly.

Also, you'll need to be specific about the exact version of Ubuntu being used.  There were two releases in 2020 and 2022, so we need 4 digits.

---

### Post by jennafer on 2024-03-16
[COLOR=#000000][FONT=Arsenal]Good idea! If you want exciting entertainment and a chance to win big, check out [/FONT][/COLOR][COLOR=#000000][FONT=Arsenal][to*******sreviews.in/casino/zodiac/]("https://to*******sreviews.in/casino/zodiac/")[/FONT][/COLOR][COLOR=#000000][FONT=Arsenal] Zodiac Casino. With a great lineup of games and an exciting gaming environment, Zodiac Casino offers an unrivaled gaming experience that is sure to keep you on edge.[/FONT][/COLOR]

---

