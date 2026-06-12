---
title: "Computer-to-computer communications on the local wifi network are blocked... why?"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by dewdrop_world on 2013-10-20
Hi,

I suspect this is not strictly an Ubuntu question, but I definitely see it on my Ubuntu machine and it's very likely that somebody here knows more about the problem than I do.

I used to be able to communicate between machines that are connected to the same wifi router, e.g., I'm running a WebDAV service on my Linux machine and other computers and mobile devices could access it by IP in the past. Now, all such communication is blocked.


[LIST]
[*]I've tested multiple ports (80 for WebDAV, 57120 for Open Sound Control messages to and from SuperCollider) -- no success 
[*]It affects both TCP and UDP 
[*]It affects multiple computers 
[*]Disabling the computers' firewalls doesn't make a difference -- and in any case, I had already opened 80/tcp and 57120/udp in ufw, and everything was fine before. 
[/LIST]

The most likely culprit, it seems to me, is the wifi router itself. In fact, a few days ago, I was trying to troubleshoot an IMAP connectivity problem and I tried a power-off, power-on cycle on the router. I suppose this caused some router configuration switch to get flipped so that now, local-area communications are broken.

I have no idea which option that could be, and unfortunately, search terms like "wifi router configuration problem" bring back whole slews of results having to do with setting up your *computer* to connect to wifi... seems not to be the problem here... in other words, the search engines are not making the haystack any smaller.

If anyone has some guesses -- even just a more specific search term -- I'd be happy with that. I'm good with search engines but the only search terms I can think of are just too vague.

The reason why I need this: I'm in a computer musician and I want to control my next piece using TouchOSC (running on an Android device). TouchOSC sends UDP packets with Open Sound Control messages over a local wifi network... but, obviously, if the local WiFi network is blocking all traffic, then I wouldn't be able to do that.

TIA,
hjh

---

### Post by Andy_Lee on 2013-10-20
Hi.

Try to disable "AP isolation" in your Wireless Router.

---

### Post by dewdrop_world on 2013-10-23
Sorry for the late reply -- ubuntuforums was first down, then extremely slow, when I first tried to reply.

Thanks, I'll look at that the next time the problem occurs.

The situation actually resolved itself -- magically -- later in the day. That's a bit uncomfortable, since I don't know why it broke and I can't make a plan to fix it if it happens again (other than look at AP isolation).

A musician friend suggested connecting the mobile directly to the computer's wifi card (Atheros AR9285). I looked into that, since it would save me the trouble of carrying a wifi router to gigs. I had some success at first with a hostapd-based solution, but then the dhcp side of it stopped working (mobile couldn't get an ip address) and I haven't had a spare second to look at it since then. Also the internet sharing failed, despite the script [1] running

```
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -s 10.10.0.0/16 -o \$ext_interface -j MASQUERADE
```

Still playing with it... but at least, if I can get the dhcp side working again, then the mobile's UDP messages do get through to my lappy.

hjh

[1] [https://gist.github.com/dashohoxha/5767262](https://gist.github.com/dashohoxha/5767262)

---

