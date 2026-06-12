---
title: "No internet after upgrade 16.04 &gt; 18.04"
date: 2019-04-29
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2019-04-29
Hi all,

Pretty much as the title says. No internet after online upgrade from Xubuntu-core 16.04 > 18.04 (not clean install of 18.04). Doing this for a friend and the machine has no bells and whistles and few moving parts. Xubuntu-core install used almost solely for watching movies and emailing. I did the original install when the machine was new and has only ever run Xubuntu-core. 

Last time I worked on the machine I upgraded from 14.04 > 16.04 online without a glitch. This time, everything went great ... until reboot. Everything except internet is still working great, but regardless of what I've tried, can't get internet working using wired or wireless.

Wired and wifi connect to router and LAN without a problem, but can't get out of the router to WAN. Getting IP from router DHCP server. Upgraded using same router, same ethernet cable, so no difference in hardware. All was working fine pre-upgrade. Problems started on first 18.04 restart after upgrade. 

I haven't found a fix from any of the threads I have seen, but have made a bit of progress identifying what's happening (see update posts below). 
Don't hesitate to ask for further info, but remember: the problem machine is not online so I am limited. (Update: I can now get the machine online until I reboot, so it is possible to give information directly from the problem machine.)

It doesn't seem to be a 'wireless issue' as both wireless and ethernet cable are seeing and connecting to the router fine with great connection speed. Just not getting out.

Cheers.

PS: I have several other devices connecting to the same router and the internet without issue (the one I'm typing on, for instance). Just this one machine that won't. I installed Xubuntu on this machine back in 2014 when it was brand new and it has only ever had Ubuntu installed. No issues until now. I have upgraded it once since the first install, tweaked a bit, and that is about it.

---

### Post by Bucky Ball on 2019-04-29
This fixes it temporarily: using the solution in the last post here from Eftychia Thomaidou (thanks, Eftychia).

[https://askubuntu.com/questions/1021888/ubuntu-18-04-beta-cannot-connect-to-wifi-internet](https://askubuntu.com/questions/1021888/ubuntu-18-04-beta-cannot-connect-to-wifi-internet)

Add

```
nameserver 8.8.8.8
```

at the end of the file /etc/resolv.conf then restarted using 

```
sudo /etc/init.d/networking restart

```

Gets me online ... until I reboot.  When I reboot, my change has vanished and the machine is offline.

I guess the question is: how can I make that change stick or is there another way of doing this? When I check the /etc/resolv.conf file on a (18.04) computer that is connecting to internet, I have only 'nameserver 127.0.0.53' at the end of the file.

On the misbehaving computer, I have 
```

nameserver 127.0.0.53
options edns0
```

Perhaps this gives a clue as to what might be happening?

PS: Just noticed at the top of the /etc/resolv.conf file is the instruction, 'Do not edit'. So I presume I need to make these same changes elsewhere for them to stick. Wonder where? I'll keep digging.

---

### Post by Bucky Ball on 2019-04-30
Just going to add to this thread as I discover things in the hopes it might spark a fire for someone. When I run 

```
systemd-resolve --status
```

on the misbehaving machine, it shows no DNS servers for wifi (or eth for that matter). When I run it on the working machine, at the end of that section, I have DNS servers, like so:

```
Link 2 (wlp1s0)
      Current Scopes: DNS
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no
         DNS Servers: 61.9.226.33
                      61.9.226.1
```

On the misbehaving machine, there is no 'DNS Servers' entry at the end of the output, like so:

```
Link 3 (wlan0)
      Current Scopes: none
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no
        
```

As well as the missing DNS section at the bottom, 'Current Scopes' shows 'none' whereas on the working machine it shows 'DNS'.

---

### Post by Bucky Ball on 2019-04-30
Bumpity.

Wouldn't normally so soon, but friend needs computer for work. Will have another go at it tomorrow morning then, failing a fix, will be doing a clean install of 18.04 and crossing my fingers that does the trick, although I would really prefer not to as this machine is setup just right and rather not have to set up a clean install. Shame to use the elephant gun approach when the only problem with this install is, from what I can gather, some simple setting somewhere in a file.

Strange thing is, I did exactly the same upgrade using exactly the same method on the very computer I'm typing on not more than three weeks ago and not a problem. None. Just booted into 18.04 and worked first time. Researching the problems I'm having with the upgrade on friend's machine I realise that there has been some big changes in networking with 18.04 and appears I have fallen victim to one of them when I went from 16.04 to 18.04. Maybe there's some left over network related file or setting from 16.04 network setup?

I've reached a dead-end for now. I have some idea of what's going on, but resolving it is beyond my expertise. Hopefully, I'll find more clues in the morrow.

---

### Post by Bucky Ball on 2019-05-01
This did it.

[https://askubuntu.com/questions/907246/how-to-disable-systemd-resolved-in-ubuntu/907249#907249](https://askubuntu.com/questions/907246/how-to-disable-systemd-resolved-in-ubuntu/907249#907249)

I'd been comparing various files I thought might be relevant on the online machine and the problematic one and finding no differences or anomalies. I did a bit more research, found the link above, and when I compared /etc/NetworkManager/NetworkManager.conf, I noticed the file on the problem machine had extra lines the online machine's file didn't have.

I changed the file to replicate the online machine's file, made the other change to that file suggested in the link above (add 'dns=default' at the bottom of the [main] section in that file), restarted network manager and bingo: I'm online.

I then restarted the machine and it connectied 'automagically', as it should and as it was doing before the upgrade. And still online. Restarted the machine three or four times and tested each time and still working. :)

So I consider this solved. For anyone that is interested, my /etc/NetworkManager/NetworkManager.conf file now looks like this.
```

[main]
plugins=ifupdown,keyfile
dns=default

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no
```

Hope that can help someone in future if they upgrade to 18.04 and find themselves with no internet. Check that file first and see if yours looks like mine. The only weird thing is, the same file on my own upgraded 18.04 machine with working internet is exactly the same as the file above ... but without the manually added 'dns=default' line in the [main] section. Go figure. Like I said earlier, I upgraded that machine about three weeks ago and everything 'just worked'. 

Good luck.

---

