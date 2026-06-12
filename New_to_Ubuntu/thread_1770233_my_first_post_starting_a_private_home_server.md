---
title: "my first post: starting a private home server"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by anarchy_now on 2011-05-28
hello good people of ubuntu forums! although this is not my first time visiting this place, this is my first time posting.

       about a month ago i was just cruising along on my fairly new dell inspiron with win7, and all of the sudden.. BSOD!!! i thought i was hot stuff with my fancy new OS and all the neat graphics and "security software" little did i know that cracks and keygens ARE a SERIOUS threat, and the neat pirated software i was using had infested my system files- all the way to the MBR- with trojans, viruses, and rootkits. after THREE DAYS of intense trial and error and research, i finally managed to get things straightened out with the help of the kapersky rescue disc (which uses a version of linux to boot from). this sparked my interest in linux. after i got back online i started to look around and i found the latest distro of ubuntu, and tried it out. first i made a boot disc and then i installed via WUBI. 
        i was appalled that people are still paying money and installing 250 security updates a week for inferior code, when the open source community offers so much awesome resources! im all about it now. im still learning, (so dont get upset if my terminology is a little off, just correct me) and i would like to try something new. i have a few computers around my house, and the one i am not using at the moment is a late model XP era Gateway, fully functioning. i was thinking about, what with all the new-fangled hype about 'cloud computing', starting my own little home server to store information and other things on at home so that it would be easily accessed remotely. i live out in the country, and there are a lot of people out here who have computers and internet connections, but have no idea how to fix problems they encounter, or even maintain basic security necessities. i thought it would be helpful in my latest IT services business venture, and just for overall learning and messing around with. is there anything out there that could get me started with my "home cloud"?

---

### Post by dFlyer on 2011-05-29
> **anarchy_now said:**
> hello good people of ubuntu forums! although this is not my first time visiting this place, this is my first time posting.

       about a month ago i was just cruising along on my fairly new dell inspiron with win7, and all of the sudden.. BSOD!!! i thought i was hot stuff with my fancy new OS and all the neat graphics and "security software" little did i know that cracks and keygens ARE a SERIOUS threat, and the neat pirated software i was using had infested my system files- all the way to the MBR- with trojans, viruses, and rootkits. after THREE DAYS of intense trial and error and research, i finally managed to get things straightened out with the help of the kapersky rescue disc (which uses a version of linux to boot from). this sparked my interest in linux. after i got back online i started to look around and i found the latest distro of ubuntu, and tried it out. first i made a boot disc and then i installed via WUBI. 
        i was appalled that people are still paying money and installing 250 security updates a week for inferior code, when the open source community offers so much awesome resources! im all about it now. im still learning, (so dont get upset if my terminology is a little off, just correct me) and i would like to try something new. i have a few computers around my house, and the one i am not using at the moment is a late model XP era Gateway, fully functioning. i was thinking about, what with all the new-fangled hype about 'cloud computing', starting my own little home server to store information and other things on at home so that it would be easily accessed remotely. i live out in the country, and there are a lot of people out here who have computers and internet connections, but have no idea how to fix problems they encounter, or even maintain basic security necessities. i thought it would be helpful in my latest IT services business venture, and just for overall learning and messing around with. is there anything out there that could get me started with my "home cloud"?

First, an OS is a personal choice. I do not as most I know don't approve of pirated software. If you truly want to use linux software you have many distro to choose from. Choose wisely and go slow. Ask question when you have them and most of all have fun. If your looking for help in cracking or pirated software you've came to the wrong place.

---

### Post by wlraider70 on 2011-05-29
I would start with identifying what you want to do.

Stream media
Backup files
Access files from the internet (cloud type stuff)


If you are just starting you should go with Ubuntu Desktop 10.10 or 11.04. There are lots of "flavors" to customize your experience but for a beginner start basic.

---

### Post by anarchy_now on 2011-05-29
> **dFlyer said:**
>  If your looking for help in cracking or pirated software you've came to the wrong place.

oh goodness no, gary. i was just sharing on how my ignorance had led me to believe that pirated software was "cool", and that i had learned my lesson the hard way. now i do not condone or advocate such malicious activities. if it were not for my experiences with the hacked software, i may not have ever learned about this and other awesome communities. i know now that there are alternatives to the mainstream proprietary softwares that i was under the impression of being out of my financial league (unless it was stolen.) after finding operating systems like ubuntu, and software like gimp, libreoffice, ect., i have even started to spread awareness to my personal network and let people know that M$ is not the center of the universe.

as far as what it is i want to do, i already have the latest version of ubuntu (as i type this message) and am learning my way around it fairly quickly.
 i am wanting to use one of my extra desktop pc's, that is not being used, and integrate into my home network and also make it accessible from other locations. i want to be able to store files and software so i can quickly get to them if i need it. i would also like to make it kind of a hub where my other in-use computers on my home network can store and share files, and where i can store my backups and other sensitive data. 
can you guys recommend one of the more specialized linux variations to get me started? i know they are out there, im just not sure which one i should go with.

---

### Post by lkraemer on 2011-05-29
You need to checkout FreeNAS and Superb Mini Server to get an idea of some of the servers that are available.

[http://freenas.org/](http://freenas.org/)
[http://sourceforge.net/apps/phpbb/freenas/index.php](http://sourceforge.net/apps/phpbb/freenas/index.php)

[http://sms.it-ccs.com/](http://sms.it-ccs.com/)

But, be warned when you open your Router Ports 21, 22, and any others you WILL be continually probed,
and attacked trying to get access to your server and files.

So, SECURITY for your files is a Very Important part of your setup.  I'd
suggest making a local NAS for now, and not open any Router ports until
you have a good handle on your NAS/Server configuration.


lk

---

### Post by jatoo on 2011-05-29
Hello anarchy,

I run a home server myself, so i can share my experience with you if you like.

Being an Ubuntu desktop user, i picked [Ubuntu server]("http://www.ubuntu.com/business/server/overview") for my server OS.  It has served me well (literally), and i've found it pretty handy.  I think you could go look at something like [Debian]("http://www.debian.org/distrib/"), the reason being Ubuntu is a distro focused on ease of use for desktop users whereas Debian (the distro Ubuntu is built on) is a bit stripped back.  Having said that, Ubuntu does make a release specifically for servers and it has worked well for me.

What prompted me to set one up was i needed a place to store my subversion repositories that i could access anywhere.  So i went out and bought all the compenents i need for $320 (Australian) and had a system running in no time.  So you don't need any  powerful hardware.

Mine is a "headless" server, i.e., it runs with no monitor keyboard and mouse.  Everything is administered remotely, which saves money on hardware.

I use [DynDNS]("http://www.dyndns.com/") (free) for my domain name (though i had to use a bit of a hack to get it working reliably). 

This is some of the stuff i use the server for so far:
[LIST]
[*]ssh server
[*]subversion server
[*]samba server (filesharing) 
[*]ftp 
[*]headless torrent box (accessed via web interface and samba)
[*]web page for web projects
[*]apt-cacher
[*]mediawiki
[*]trac
[*]subsonic (stream music anywhere)
[/LIST]

So as you can see it's been pretty useful.

The reliability of it has improved the longer i've had it running as i've learnt more about it. 

As for using it for a business, i'm not so sure it's the best way to go.  I have had outages that i couldn't fix until i got home (if the power went off, or the DNS didn't update, for example).  I've resolved these problems now, but i'm still not 100% confident in it.  Maybe hiring a VPS would be a better way to go for business purposes.

Anyway, good luck with it, let me know if you have any questions.

---

### Post by CharlesA on 2011-05-29
Use SFTP (and secure it properly), instead of FTP.

It is more secure then FTP and you only have to mess around with opening one port (port 22 in this case, since it uses sshd).

Just make sure to secure SSH properly and you'll not have any problems.

---

### Post by anarchy_now on 2011-05-30
hey everybody, thanks for all the awesome feedback! i have been at the lake all day with my kid so i havent had time to sit down and geek out hahaha. im gonna take a few moments and soak up some of this information. here's a question.. since i have a dynamic ip, and can change my ip address by power cycling my modem, would that help deter the 1337 |-|4x0|25 from trying to sniff my ports, or do they just attack every known ip in existance?

---

### Post by Allavona on 2011-05-30
Hi, don't mean to interject here but in the OP you mention that you installed Ubuntu through WUBI on an infected computer? What type of "security software" were you running?

As for hacked/cracked software...It's a shame you learned the hard way about that. There are way too many Open Source programs out there to choose from to be bothered with hacks/cracks.

---

### Post by wep940 on 2011-05-30
I'm also interested in this - setting up a home server for the first time.  I've thought about using Ubuntu Server 11.04 and making the server headless, but I've had one concern that I *think* fits in this discussion.
 
I have DSL, so I have a DSL modem.  From there, a CAT5 cable runs to a Netgear router.  I know the DSL modem is seen differently as it starts at 192.168.  The Netgear router is set to 10.0.  The wireless on the router is set with WPA/PSK-AES (?) so it is more difficult for someone to get to the wireless side from outside our PC's.  
 
The server will have to be wireless as well.  Are there security issues at the server also when it is wireless to the router?  How do you keep the wireless constantly up on a server? (I had done some playing around with Ubuntu Server a few release ago, and at that time it was like the wireless was timing out - I had to power-reset the server to get it back).
 
Thank you, and I hope I'm not distracting from this thread - I thought the question might fit in with the discussion.

---

### Post by jatoo on 2011-05-30
> **anarchy_now said:**
> hey everybody, thanks for all the awesome feedback! i have been at the lake all day with my kid so i havent had time to sit down and geek out hahaha. im gonna take a few moments and soak up some of this information. here's a question.. since i have a dynamic ip, and can change my ip address by power cycling my modem, would that help deter the 1337 |-|4x0|25 from trying to sniff my ports, or do they just attack every known ip in existance?

I'm not sure that would be the best thing to rely on for security.  You can install fail2ban, which temporarily bans connections from IP addresses which attempt to log in repeatedly.  It's worked pretty well for me.

On top of that, just follow the security advice of each service you set up, and only open the necessary ports on your router.  For example, when setting up an ssh server you can disable password login and only allow key authentication (which can be a little inconvenient if you want to be able to log in from anywhere).

---

### Post by wlraider70 on 2011-05-30
Ports especially ssh (22) ftp (21) are constantly being scanned and are the most likely to be attacked. While turning off the router and/or changing your external ip would break the connection, by the time you realized you needed to do so it would be too late. 

While security is a whole separate topic, do not assume that there is not a real threat to your server. However, proper securing will take care of the danger.

---

### Post by Wim Sturkenboom on 2011-05-30
This might of help: [Linux Home Server HOWTO](http://www.brennan.id.au/)

Although based on Fedora, it (and other sources) helped me when I set up my Slackware server.

And as others stated:
Understanding of security risks and how to implement proper counter measures (e.g. firewall, tcpwrappers, stopping unnecessary services, no root access from the outside world, extremely strong passwords, encrypted connections) is bloody important.

---

### Post by jatoo on 2011-05-30
> **wep940 said:**
> I'm also interested in this - setting up a home server for the first time.  I've thought about using Ubuntu Server 11.04 and making the server headless, but I've had one concern that I *think* fits in this discussion.
 
I have DSL, so I have a DSL modem.  From there, a CAT5 cable runs to a Netgear router.  I know the DSL modem is seen differently as it starts at 192.168.  The Netgear router is set to 10.0.  The wireless on the router is set with WPA/PSK-AES (?) so it is more difficult for someone to get to the wireless side from outside our PC's.  
 
The server will have to be wireless as well.  Are there security issues at the server also when it is wireless to the router?  How do you keep the wireless constantly up on a server? (I had done some playing around with Ubuntu Server a few release ago, and at that time it was like the wireless was timing out - I had to power-reset the server to get it back).
 
Thank you, and I hope I'm not distracting from this thread - I thought the question might fit in with the discussion.

I'm not a security expert but here's my understanding: If you have WPA wireless security, and don't tell people your passphrase, then your wireless connection should be secure in the sense that the link between your computer and your wireless router is secure. If you have ports forwarded from your router to your server, then it is open to the outside world via the internet and you need to have other security there.  

I'm not sure what you mean by keeping the wireless constantly up... why would it go down?  If it is due to a poor signal, then not much you can do other than getting a more powerful signal, higher gain antenna, moving them closer together, or moving the antennas up higher.  I've always found ethernet to be a lot more reliable.

---

### Post by wep940 on 2011-05-30
Great!  Since the server is only intended for "our side" of the network, it should be good - I won't be forwarding any ports as I have no need to have the server accessable external to the wireless network.

As far as the wireless going down......when I tried Ubuntu Server briefly a few years ago, everything was wireless so the server had to be wireless as well.  It was almost as if the system blanked the screen, etc., from the idle timers and also seemed to turn off the wireless.  I never figured out how or why that was happening.  Give the server 10 or 15 minutes of no activity - bingo - everything goes to sleep and the wireless no longer works (or what I was thinking at the time:  the PC was going to into sleep mode and some setting somewhere was set for wake up on wireless activity, if there is such a thing).

---

### Post by Irihapeti on 2011-05-30
While you are just tinkering on your home network, I'd recommend turning off uPNP on your router. That way, you don't have to worry about accidentally forwarding ports and thereby exposing your network to nefarious strangers.

---

### Post by CharlesA on 2011-05-30
> **Irihapeti said:**
> While you are just tinkering on your home network, I'd recommend turning off uPNP on your router. That way, you don't have to worry about accidentally forwarding ports and thereby exposing your network to nefarious strangers.
+1. It can't hurt.

---

### Post by EGamerHDK on 2011-05-30
I'm actually looking into this myself. I'll see how it goes. Good luck to ya.

---

### Post by wlraider70 on 2011-05-30
> **wep940 said:**
> 
As far as the wireless going down......when I tried Ubuntu Server briefly a few years ago, everything was wireless so the server had to be wireless as well.  It was almost as if the system blanked the screen, etc., from the idle timers and also seemed to turn off the wireless.  I never figured out how or why that was happening.  Give the server 10 or 15 minutes of no activity - bingo - everything goes to sleep and the wireless no longer works (or what I was thinking at the time:  the PC was going to into sleep mode and some setting somewhere was set for wake up on wireless activity, if there is such a thing).


Your server MAY have been putting the connection to sleep.
If you use Ethernet you wont have a problem. I run my server with no monitor its underneath my router with a short cable connecting them.

There is a way to wake up sleeping computers over lan its called wake on lan WoL. However, you need to be connected by Ethernet cable, it wont work on wifi.

---

### Post by wep940 on 2011-05-31
Irihapeti - thanks for the info.  Being completely ignorant about what universal plug and play would do on a router, I have to ask.  Also, would turning it off stop me from being able to add devices and computers to the network?  Thanks!
 
wlraider70 - thanks!  I bet that's what was going on - going to sleep.  Now for a dumb idea related to that:  "back in the day" on some of our mainframe communications front-ends we used to have to specify a keep-alive - a way for it to keep a link open.  If one were to write a small script that did nothing more than ping Yahoo, and have it in cron so it runs like every 5 minutes or so, that would keep the wireless alive, right?  I mean there would be activity, so hopefully the server wouldn't go to sleep.  If this would work, would I be disrespectful to fellow internet users and to Yahoo to do a ping like this every 5 minutes?  I don't want to do anything that legally or morally I shouldn't be doing.
 
Thanks!

---

### Post by CharlesA on 2011-05-31
> **wep940 said:**
> Irihapeti - thanks for the info.  Being completely ignorant about what universal plug and play would do on a router, I have to ask.  Also, would turning it off stop me from being able to add devices and computers to the network?  Thanks!

It wouldn't affect the internal network at all.

---

### Post by wep940 on 2011-05-31
Thanks!!  I guess a better way of keep-alive would probably be to just ping one of the wireless printers on our internal network, rather than taking bandwidth on the outside world.  I should of thought of that from the start.
 
I think I have enough to start "playing", so it may be a while, but I'm sure I'll have more questions.  Would it be better to continue posting them in this thread since they would all deal with starting a private home server, or should I post those in another thread when the time comes?
 
Thanks everyone!  I sure hope I didn't hijack this thread - it was not my intention at all.  If I have, please accept my apologies and let me know.
 
;)

---

### Post by anarchy_now on 2011-07-10
hey everyone. sorry about the late reply, ive been really busy. ok so ive gone over what everyone replied. ive gotten some new equipment to play around with as well. from the looks of things i have a LOT of learning to do. i was looking around the other day and i came across this article ([http://www.hackthissite.org/articles/read/1090](http://www.hackthissite.org/articles/read/1090)). it sounds pretty relevant to my interests. how valid is this information? i have a fresh pc (will refer to it as "server pc" from here on) and copy of ubuntu server on disc and am ready to go from here. also, in order to get my wired connection all the way across the house into my battlestation, i had to connect a linksys befsr41 router to my belkin router. im on the wired desktop (will refer to it as "desktop 1" from here on) and have my laptop here connected to the belkin router via wifi as well. will i be needing to make any special configurations to my routers in order to access my website from the net? should i start a new thread for this?

---

### Post by CharlesA on 2011-07-11
Looks fine, but I suggest using sudo with each command instead of just using sudo -i.

---

### Post by jatoo on 2011-07-11
> **anarchy_now said:**
> hey everyone. sorry about the late reply, ive been really busy. ok so ive gone over what everyone replied. ive gotten some new equipment to play around with as well. from the looks of things i have a LOT of learning to do. i was looking around the other day and i came across this article ([http://www.hackthissite.org/articles/read/1090](http://www.hackthissite.org/articles/read/1090)). it sounds pretty relevant to my interests. how valid is this information? i have a fresh pc (will refer to it as "server pc" from here on) and copy of ubuntu server on disc and am ready to go from here. also, in order to get my wired connection all the way across the house into my battlestation, i had to connect a linksys befsr41 router to my belkin router. im on the wired desktop (will refer to it as "desktop 1" from here on) and have my laptop here connected to the belkin router via wifi as well. will i be needing to make any special configurations to my routers in order to access my website from the net? should i start a new thread for this?

I think what you'll probably need to do is enable port forwarding on the router which sees the internet, and forward the ports to the IP address of your server.  This should send it through whichever routers it needs to.  This is the same really as just using one router, except your server's IP address will probably be different.

---

### Post by CharlesA on 2011-07-11
Keep in mind that most ISPs (at least the ones around here) block port 80.

---

### Post by jatoo on 2011-07-11
> **CharlesA said:**
> Keep in mind that most ISPs (at least the ones around here) block port 80.

I had that problem for a while, and my solution was to just use another port, so i would visit my site at [http://myurl.com:8080](http://myurl.com:8080).

I found out though that i could enable port 80 in my ISP settings, which made things a bit nicer.

---

### Post by CharlesA on 2011-07-11
> **jatoo said:**
> I had that problem for a while, and my solution was to just use another port, so i would visit my site at [http://myurl.com:8080](http://myurl.com:8080).

Yep, I've done that too.

---

