---
title: "PC unable to connect to the internet"
date: 2020-05-08
forum: Networking &amp; Wireless
---

### Post by Jonners59 on 2020-05-08
An odd one here.  Have a PC called "Media".  It was working fine, but then wouldn't start properly, so I rebuilt it with the latest 20.04LTS.  It installed smoothly, including downloading and installing all the updates.  So far so good.  When I finished setting it up I could browse my LAN and other machines OK and also browse the internet, use Skype and Zoom and the like, it worked flawlessly.  And two days later it stopped being able to view anything on the internet.  It then seemed to work the following day when I decided to investigate and has since stopped for the past 3 days.  I have completely rebuilt my Router from scratch on the back of it, just in case, but see nothing in the settings that make it stand out.  I am a wit's end.  It is on the same network with other devices all of which have no issues.

The PC is connected via a simple LAN switch to a DrayTek 2820 which is used as a local switch and access point on the ground floor, which then links into another DrayTeck 2869 which is the active router and DHCP.  I use static IP Addresses, which the 2860 issues under the MAC Bind.  The PC appears in the list of connected devices in the IP Bind page, though not in the Dashboard, which I am not too concerned as a number of devices which are working fine also do.  ANd I can ping the PC from the router, and it also gives the correct IP address, and it the PC can see all the other devices on the LAN and access them as it should.  It is ONLY internet access that has stopped.

I have not put anything else up as I am not sure what people need to see and what commands people want.

---

### Post by speartip on 2020-05-08
Sounds like a similar problem to mine.
Try following the fix in my 2nd post. If it's not that it's easy enough to reverse.
[https://ubuntuforums.org/showthread.php?t=2442314](https://ubuntuforums.org/showthread.php?t=2442314)

---

### Post by Jonners59 on 2020-05-08
> **speartip said:**
> Sounds like a similar problem to mine.
Try following the fix in my 2nd post. If it's not that it's easy enough to reverse.
[https://ubuntuforums.org/showthread.php?t=2442314](https://ubuntuforums.org/showthread.php?t=2442314)

"Ubuntu resets the TLP configuration, & WiFi power management comes on. To rectify I edited the file,
/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
and changed the value from 3 to 2, rebooted, and voila, problem solved."


Thank you.  I shall take a gander, but this is not WiFi, sorry, should have said.  It is an Ethernet connection.

FYI tried it and it didn't work.

Note that I can ping 8.8.8.8 and ifconfig looks correct, the same as other machines bar it's unique IP address.

---

### Post by Jonners59 on 2020-05-09
SORTED!!!!!!!!!!!

So, in a nutshell.  The problems I was having was that shortly after installing the new OS I stopped being able to view anything on the internet.  I could browse the LAN and devices on the LAN and retrieve files etc, but not the internet.  All the settings in the connection manager were normal and it appeared on my WAN router correctly.

[HTML]ifconf[/HTML] was normal
[HTML]ping -c 4 8.8.8.8[/HTML] gave me an instant 4 good pings, but [HTML]ping -c 4 google.com[/HTML] failed to reach the server.

Searching I found this [HTML]sudo gedit /etc/NetworkManager/NetworkManager.conf[/HTML], change [HTML]managed=false[/HTML] to [HTML]managed=true[/HTML]
[HTML]sudo Network-Manager restart[/HTML]

I also did this, but not sure if it did anything.
[HTML]sudo tee  /etc/resolv.conf <<< "nameserver 127.0.1.1"[/HTML] [HTML]sudo service network-manager restart[/HTML]

I tried to do the pings again and it still failed.  A tad despondent.

I then tried to look at the config file in the Network Manager "Edit Connections" panel drop-down and noticed I could not disconnect the Ethernet connect, nor turn off "Enable Networking" and could not get in to "edit connections" so I just rebooted.

Upon reboot, everything was working.  I could access the browser and all internet sites, the Network Manager dropdown was back.  Hope this helps someone else in the same grief.

Many sites and solutions require the installation of apps and the like or complex scripts and tweaks, all not possible or extremely difficult with no network connection.  this one works and is simple.

---

### Post by Jonners59 on 2020-05-13
Not resolved.  This keeps coming back.  This time I can not fix it.
Can ping and see anything on the LAN.  Can ping via IP addresses eg 1.1.1.1 and 8.8.8.8  Can NOT ping websites, eg. google.co.uk

The output of ```
[SIZE=2]resolvectl status[/SIZE]
```

[HTML]   	 	 	 	  Global

        LLMNR setting: no                   
 MulticastDNS setting: no                   
   DNSOverTLS setting: no                   
       DNSSEC setting: no                   
     DNSSEC supported: no                   
           DNSSEC NTA: 10.in-addr.arpa      
                       16.172.in-addr.arpa  
                       168.192.in-addr.arpa
                       17.172.in-addr.arpa  
                       18.172.in-addr.arpa  
                       19.172.in-addr.arpa  
                       20.172.in-addr.arpa  
                       21.172.in-addr.arpa  
                       22.172.in-addr.arpa  
                       23.172.in-addr.arpa  
                       24.172.in-addr.arpa  
                       25.172.in-addr.arpa  
                       26.172.in-addr.arpa  
                       27.172.in-addr.arpa  
                       28.172.in-addr.arpa  
                       24.172.in-addr.arpa  
                       25.172.in-addr.arpa  
                       26.172.in-addr.arpa  
                       27.172.in-addr.arpa  
                       28.172.in-addr.arpa  
                       29.172.in-addr.arpa  
                       30.172.in-addr.arpa  
                       31.172.in-addr.arpa  
                       corp                 
                       d.f.ip6.arpa         
                       home                 
                       internal             
                       intranet             
                       lan                  
                       local                
                       private              
                       test                 
 
 
 Link 2 (eno1)
       Current Scopes: DNS         
 DefaultRoute setting: yes         
        LLMNR setting: yes         
 MulticastDNS setting: no          
   DNSOverTLS setting: no          
       DNSSEC setting: no          
     DNSSEC supported: no          
          DNS Servers: 1.1.1.1     
                       8.8.8.8     
                       192.168.1.1
           DNS Domain: ~.[/HTML]

Please help, someone.

---

### Post by TheFu on 2020-05-13
it is a DNS problem, not a network problem.  i don't know how to fix it when network-manager is involved.  i purge network-manager from all my systems just after install.  i do not use dhcp reservations for static ips for a number of reasons, except for laptops and android devices and iot stuff where it is impossible to to set a static ip otherwise,

Also, i run an internal DNS server which does all caching, so local workstations don't need to do that.  What all this means is that it disable all the local caching and dns stuff on every workstation, tell the /etc/resolv.conf to point at our internal DNS servers (primary and backup), and forget everything else.

For setting up a static ip on 20.04, here's my setup:
/etc/netplan$ more 01-network-manager-all.yaml ```

network:
    version: 2
    renderer: networkd
    ethernets:
        ens3:
            addresses:
            - 172.22.22.3/24
            dhcp4: false
            dhcp6: false
            gateway4: 172.22.22.1
            nameservers:
                addresses: [ "172.22.22.80","172.22.22.81" ]
                search: [thefu.lan]
```
Note the indentation.  That is absolutely critical.
Then run```

sudo netplan generate
sudo netplan apply --debug
```
to get it working.

$ more /etc/resolv.conf 
```
nameserver 172.22.22.80
nameserver 172.22.22.81
search thefu.lan 
```

Probably more trouble than most people are willing to do. The DNS thing was a project onto itself.

---

### Post by Jonners59 on 2020-05-14
> **TheFu said:**
> 
Oh, I agree it is DNS.  For some reason, it can not get access.  the problem is it also means that I can not browse solutions on the machine to get a fix, so I search on a machine 2 floors away and then have to fumble my way around on the other machine.  It also means that I can not install anything and I think the issue is things are not installed, like RESOLVE.  Looking at things I have found they talk about a resolve config file and symlinks to it in etc.  None of this exists.  But what I don't get is that it worked when I installed the machine.  It then stopped.  I got it working and now it has stopped again.  This time all I did before does not work either.  Is there such a thing as a hate bug that goes around messing up machines for the fun of it :-)  

OK, Your solution.  It would mean that that machine is different from all the others, as it is only the one that is not working.  What you mention I understand but I would need hand-holding to set it up.  What you have done is not quite detailed and idiot-proof as I need.

---

### Post by TheFu on 2020-05-14
> **Jonners59 said:**
> Oh, I agree it is DNS.  For some reason, it can not get access.  the problem is it also means that I can not browse solutions on the machine to get a fix, so I search on a machine 2 floors away and then have to fumble my way around on the other machine.  It also means that I can not install anything and I think the issue is things are not installed, like RESOLVE.  Looking at things I have found they talk about a resolve config file and symlinks to it in etc.  None of this exists.  But what I don't get is that it worked when I installed the machine.  It then stopped.  I got it working and now it has stopped again.  This time all I did before does not work either.  Is there such a thing as a hate bug that goes around messing up machines for the fun of it :-)  

OK, Your solution.  It would mean that that machine is different from all the others, as it is only the one that is not working.  What you mention I understand but I would need hand-holding to set it up.  What you have done is not quite detailed and idiot-proof as I need.

I got tired of DNS complications brought on by people/teams/companies trying to fix something that wasn't broken.  It really comes down to this, 
/etc/resolv.conf is THE file that tells a machine where to get DNS from. It supports primary - tertiary DNS servers, listed by IP.  Everything else is crap meant to screw up.  Local caching. Local DNS on the same machines are all just going to complicate things and break.  All that you need is a way for that file to point at whatever DNS servers you want. That's it. Nothing more.  Anything that points at a local 127.0.0.x IP is just a complication.

Stop and disable all the local DNS stuff - systemd-resolved, resolvconf. You don't need to remove any packages. If you don't disable those packages, they will take over the resolv.conf file again and break it.  But if you set the resolv.conf file the way you want and lock it so nothing can change it, then it will work. On a 20.04 Mate desktop:
```
$ sudo systemctl status  systemd-resolved
&#9679; systemd-resolved.service
     Loaded: masked (Reason: Unit systemd-resolved.service is masked.)
     Active: inactive (dead)
```

And on a 16.04 server:
```
$ service systemd-resolved status
&#9679; systemd-resolved.service - Network Name Resolution
   Loaded: loaded (/lib/systemd/system/systemd-resolved.service; disabled; vendor preset: enabled)
  Drop-In: /lib/systemd/system/systemd-resolved.service.d
           &#9492;&#9472;resolvconf.conf
   Active: inactive (dead)
     Docs: man:systemd-resolved.service(8)
```
The commands are:
```
sudo systemctl stop   systemd-resolved
sudo systemctl disable   systemd-resolved
sudo systemctl mask systemd-resolved
```

Make a /etc/resolv.conf file that looks something like mine, but points at whatever DNS server(s) you like.  8.8.8.8 and 1.1.1.1 or your local home router, if it provides DNS stuff.  Which to use depends on your privacy desires.  You can use the ISP or some external filtering DNS too.  If that file is a symbolic link, break it or move it to a different name.  What needs to be left in place as the /etc/resolv.conf has 2 or 3 simple lines.
You'll find that your system "just works" now.  

Plus, for the last 4 months, Firefox has been providing a DNS-over-HTTPS service and you've been using that regardless of the local DNS config anyway.  That is unless you disabled that default too, within firefox.  I've disabled that in firefox, but I'd rather not have all my DNS queries provided to them or google.

See how you like it or if you even notice any problems.  Many home routers provide DNS caching, so you probably could just point your systems at the router for DNS.  DHCP should do this.  There's little need to have the on-system DNS caching for a non-portable system.

Anyways, that's what I did across all my systems.  The LAN DNS server is actually a Pi-Hole, which is designed to filter tracking and advertisements out of my network experience. It is crazy how well it works. Across 18 client machines, over 43% of all DNS queries are blocked by filters.

Of course, you'll need to find a different DNS solution, if mine doesn't seem possible.  You might want to change the title for this thread to be correct. Internet connections are a different skillset than dealing with DNS.

Hoping you find the solution that meets your needs.

---

### Post by Jonners59 on 2020-05-14
OK, fixed again..  I hope it lasts this time.
SO noticed 
/etc/resolv.conf was missing so manually created it.

```
gedit
```
paste the following in
[HTML]
nameserver 127.0.1.1
nameserver 1.1.1.1
nameserver 8.8.8.8
nameserver 8.8.4.4
[/HTML] then save the doc as resolv.conf

```
sudo nautilus
```
Save and then using nautilus move it to /etc/
Permissions and owner; ensure are the user and not root.

Turn off network and turn back on, it will work immediately.

---

### Post by TheFu on 2020-05-14
Use **sudoedit /etc/resolv.conf** next time.  Running most GUI programs with straight sudo is a dangerous thing. It can break your login under certain conditions.
If you want to use gedit as your EDITOR with sudoedit, add this to the bottom of your ~/.bashrc
export EDITOR=gedit

BTW, I think only 2 nameservers are honored in the resolv.conf AND if you don't actually disable/fix systemd-resolved's configuration, this fix will fail too.

---

### Post by Jonners59 on 2020-05-15
> **TheFu said:**
> Use **sudoedit /etc/resolv.conf** next time.  Running most GUI programs with straight sudo is a dangerous thing. It can break your login under certain conditions.
If you want to use gedit as your EDITOR with sudoedit, add this to the bottom of your ~/.bashrc
export EDITOR=gedit

Thanks, I had no idea.  All the typical instructions never say that, so done it for years and years...


> **TheFu said:**
> ......... BTW, I think only 2 nameservers are honored in the resolv.conf
OK, thank you.  It may then be ignoring the other two.  Don't know, but either way it doesn't seem to matter.

> **TheFu said:**
>  ...AND if you don't actually disable/fix systemd-resolved's configuration, this fix will fail too.
OK.  It still seems to be work, day two, reboot 3.  With no otger information what is or should the systemd-resolved configuration be?  I copied all folders/directories and scripts from another machine that has worked flawlessly for many years....  what am I missing, please?

---

### Post by TheFu on 2020-05-15
> **Jonners59 said:**
>  
OK.  It still seems to be work, day two, reboot 3.  With no otger information what is or should the systemd-resolved configuration be?  I copied all folders/directories and scripts from another machine that has worked flawlessly for many years....  what am I missing, please?

Someone else will have to answer any systemd-resolved question.  I disable it after multiple systems here broke and use my LAN DNS.  For me, with lots of LAN systems, having a centralized way to manage name resolution is necessary. We run lots of internal services that certain clients (cough android, cough) won't resolve without a DNS.  I self-host Plex Media, Nextcloud, Wallabag, Calibre, email, and a few internal-only websites. Without DNS, the android clients would ignore other forms of name resolution.  Plus, I've been blocking advertising for about 20 yrs.  Initially, I used the /etc/hosts method.

Hopefully, someone else will address the "systemd-resolved" question in a way that works for you.

---

### Post by Jonners59 on 2020-05-15
> **TheFu said:**
> Someone else will have to answer any systemd-resolved question.  I disable it after multiple systems here broke and use my LAN DNS.  For me, with lots of LAN systems, having a centralized way to manage name resolution is necessary. We run lots of internal services that certain clients (cough android, cough) won't resolve without a DNS.  I self-host Plex Media, Nextcloud, Wallabag, Calibre, email, and a few internal-only websites. Without DNS, the android clients would ignore other forms of name resolution.  Plus, I've been blocking advertising for about 20 yrs.  Initially, I used the /etc/hosts method.

That does sound interesting.  An issue I am having is Android phones can't seem to log on to my VPN.  But otherwise all is OK, though your system sounds much better all round.  Bit advanced for me though.

---

