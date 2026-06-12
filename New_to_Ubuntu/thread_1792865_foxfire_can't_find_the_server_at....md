---
title: "foxfire can't find the server at..."
date: 2011-06-28
forum: New to Ubuntu
---

### Post by dulce on 2011-06-28
well i know nothing...

suddenly sunday afternoon my computer went out and all the tabs said 'modum'.

interestingly at the same time the landline phone went out 'in my area' and i couldn't call the provider, telmex/infinitum until the next day (i'm in mexico). i dont know if thats related or not. the guy i talked to wasn't interested. he had me reset the modum and refused to talk to me any further because i don't have windows or mac. 'get a new computer or we can't help you' he said. hah!

well now foxfire is hooked up like normal. the connection applet says its ready, the network connection stuff says 'wireless network connection active 100%'. the wireless network menu says my infinitum is connected but there is a little lock there, just as there is on the other types of connections, the ones i don't use.

anyway i can't call up anything: i get 'problem loading page-- server not found--foxfire can't find the server at...', just as if it isn't connected at all.

this seems minor. i realize it may not be an ubuntu thing at all but i like this forum. 

i know you geniuses will rescue me as you have before. i humbly await your responses. will be checking here at the neighbor's every afternoon... :)

---

### Post by spiky001 on 2011-06-28
Have you tried ping ```
www.google.com
```

---

### Post by dulce on 2011-06-28
> **spiky001 said:**
> Have you tried ping ```
www.google.com
```

*(sigh)* what does that  mean? how and where do i ping a code? why google (i do use gmail tho...)?

---

### Post by SoFl W on 2011-06-28
I have had loss of ISP problems, when I restart Firefox, it works again, if not reboot the system.


To "Ping" something, go to the terminal (command line) and type "Ping www.google.com" and it will start printing information... or alert you of a failure.

```
 ping www.google.com
```

Should return something like
```
 ping google.com
PING google.com (123.456.789.123) 56(84) bytes of data.
64 bytes from qy-in-f103.1e100.net (123.123.123.123): icmp_seq=1 ttl=49 time=49.1 ms
64 bytes from qy-in-f103.1e100.net (123.123.123.123): icmp_seq=2 ttl=49 time=49.1 ms
64 bytes from qy-in-f103.1e100.net (123.123.123.123): icmp_seq=3 ttl=49 time=48.2 ms
64 bytes from qy-in-f103.1e100.net (123.123.123.123): icmp_seq=4 ttl=49 time=48.6 ms

```

Press control-C to stop it.

---

### Post by spiky001 on 2011-06-28
If you open terminal and type in ```
ping www.google.com
``` you should get a response like mine.
To stop ping press Ctrl+c
That will show you are get a response from internet. If you get packet loss then you are not getting out on internet, Then you have a problem with internet connection, if you get a response back then a firefox problem

---

### Post by dulce on 2011-06-28
> **spiky001 said:**
> If you open terminal and type in ```
ping www.google.com
``` you should get a response like mine.
To stop ping press Ctrl+c
That will show you are get a response from internet. If you get packet loss then you are not getting out on internet, Then you have a problem with internet connection, if you get a response back then a firefox problem

thank you spiky. i have written all that down and will head back across the road to try it. one question tho:

> you should get a response like mine.

what does that mean?

---

### Post by dulce on 2011-06-28
oops--didn't see your reply sof, thanks.

---

### Post by spiky001 on 2011-06-28
Sorry file didn't upload it has now  "SoFl W" beat me to it

---

### Post by jtarin on 2011-06-28
Is your modem provided by the internet service provider? In a terminal, issue the command ```
ifconfig
``` and can you post the results?

---

### Post by dulce on 2011-06-28
this is great, all these replies.

first of all:

the response to the ping google thing was 'unknown host'

then i went to wireless troubleshooting at ubuntu help:

*5.2.1 check that the device is on* they mean a hardware switch. if i have one i'm not aware of it and didn't touch it. it seems to be on.

*5.2.2 check for device recognition* ran another terminal, they said i should see output (i guess i did) along with words 'claimed, unclaimed, enabled or disabled'. i saw none of these. so i stopped right there altho there are 7 steps altogether.

---

### Post by dulce on 2011-06-28
> **jtarin said:**
> Is your modem provided by the internet service provider?

yes

>  In a terminal, issue the command ```
ifconfig
``` and can you post the results?

ok. sounds hopeful. :) i'm going to wait for the other replies and go do that.

---

### Post by dulce on 2011-06-28
jtarin: i went back across the street to my computer and did that but have no way of sending the results anywhere. to top things off i'm out of black ink and know from past experience there is no way to get around that. a friend took the cartridge to get another but hasn't done it...going to be one of those weeks i can see....

here's what i gleaned:  the info says that eth0, eth1 and lo are up and running.  eth0 has no errors. eth1 has 314 RX packet  errors and 356 TX packet errors. lo has 72 RX packet errors and 72 TX packet errors. 

its just after 6pm here and i am going to quit until tomorrow afternoon. thanks again everyone.

---

### Post by jtarin on 2011-06-28
If your using Network Manager use it to edit your connection and use eth0 as your connecting device and see what results you get. If you have the Live CD try to boot with that and get a connection.....and use "ifconfig" to see what card it connects with.

---

### Post by dulce on 2011-06-28
> **jtarin said:**
> If your using Network Manager use it to edit your connection and use eth0 as your connecting device and see what results you get. If you have the Live CD try to boot with that and get a connection.....and use "ifconfig" to see what card it connects with.

ok. not sure what the live cd is but a cd did come with the modum, maybe thats it.  the rest isn't clear to me (absolute beginner you know) but perhaps i'll know more tomorrow...

g'night all--really :)

---

### Post by jtarin on 2011-06-28
> **dulce said:**
> ok. not sure what the live cd is but a cd did come with the modum, maybe thats it.  the rest isn't clear to me (absolute beginner you know) but perhaps i'll know more tomorrow...

g'night all--really :)The Live CD is the one you used to install Ubuntu. Boot,select "TRY" get to the desktop and try to connect.

---

### Post by dulce on 2011-06-29
> **jtarin said:**
> The Live CD is the one you used to install Ubuntu. Boot,select "TRY" get to the desktop and try to connect.

i did not install ubuntu. this computer was rebuilt and given to me as a donation for  consulting that i do. ignorant as i am i would have been better off with windows, especially since there is no one around that i know of who works on ubuntu.

but i still have faith! the cd that i have installs infinitum, the provider. a technician came to the house and did that.

i'm going  to get hold of the person who built it and see if he can send me the live cd. that could take a long time tho, since he's in the states and i'm in mexico.

---

### Post by dulce on 2011-06-29
> **jtarin said:**
> If your using Network Manager use it to edit your connection and use eth0 as your connecting device and see what results you get. If you have the Live CD try to boot with that and get a connection.....and use "ifconfig" to see what card it connects with.

auto eth0 is my connecting device. is that the same thing? in order to change it i need a _M_AC# which i have been unable to locate.

---

### Post by jtarin on 2011-06-29
[Here]("http://mirror.corbina.net/ubuntu-cd//") is a listing of Ubuntu Live CD's to download and burn to a blank CD, then you can use this to repair your system or reinstall if necessary. Choose your appropriate version and download. If you choose to reinstall I would upgrade but stay away from the 11.04 version for now.....it is very troublesome for new people.

---

### Post by jtarin on 2011-06-29
> **dulce said:**
> auto eth0 is my connecting device. is that the same thing? in order to change it i need a _M_AC# which i have been unable to locate.You can get the MAC number by issuing the command ```
ifconfig
```The first line will look similar to this```
eth0      Link encap:Ethernet  HWaddr **00:10:4C:25:7A:3F**  
```the part after **_HWaddr_** is the MAC address in this example.

---

### Post by dulce on 2011-06-29
> **jtarin said:**
> [Here]("http://mirror.corbina.net/ubuntu-cd//") is a listing of Ubuntu Live CD's to download and burn to a blank CD, then you can use this to repair your system or reinstall if necessary. Choose your appropriate version and download. If you choose to reinstall I would upgrade but stay away from the 11.04 version for now.....it is very troublesome for new people.

i have 10.04. what would you recommend? what happens to  my files, photos,etc doing that?

you sound pretty sure its an ubuntu problem.....

---

### Post by pimentel28 on 2011-06-29
Mhmm, I think this may actually be an issue with the network itself, and not Ubuntu.

Can you please post your signal levels (go to your modems' page and post it here (don't post your MAC address!)) 

Also post the modem logs, do you know what time/date the phone went out (see if there's a correlation in the modems' logs)?

---

### Post by dulce on 2011-06-29
> **jtarin said:**
> You can get the MAC number by issuing the command ```
ifconfig
```The first line will look similar to this```
eth0      Link encap:Ethernet  HWaddr **00:10:4C:25:7A:3F**  
```the part after **_HWaddr_** is the MAC address in this example.

ok. but you are saying auto eth0 is not eth0, and to change it?

---

### Post by dulce on 2011-06-29
> **pimentel28 said:**
> Mhmm, I think this may actually be an issue with the network itself, and not Ubuntu.

Can you please post your signal levels (go to your modems' page and post it here (don't post your MAC address!)) 

Also post the modem logs, do you know what time/date the phone went out (see if there's a correlation in the modems' logs)?

i've never noticed a modem page. where will i find that? i just know that when i tried to call telmex shortly after, the phone was out too. the guy i eventually reached wasn't interested. also wouldn't help me any further because of ubuntu.

oh-- and i am at the neighbor's. i can't send anything from my machine, can't even print atm, for other reasons, but i will have a look if you tell me where to find it and what to look for.

---

### Post by ktmom on 2011-06-29
I can stay on-line for awhile so we can try things and I'll wait if you are ok with running back and forth across the street.

I'm nobody's expert, but I'm willing to bet we can get to the bottom of this although it may be a meandering route.  It sounds to me like you are missing a connection to a DNS server.

If you'd like to try, then my first question is, are you using a cable to connect directly to  the modem from the computer?  It looks like a large telephone type connector.  Or maybe it's a cable going to a router that then connects to the modem.

Otherwise, are you using a wireless connection of one sort or another to either connect wirelessly to the modem or through a router?

Have you rebooted all of the related hardware?  That means turn off the computer, and the modem and any hardware between like a router for at least 30 seconds.  Then turn on the modem, any hardware between the modem and computer and after all of that is on, turn on the computer.  Even if you have, if you would do that now, it would give us a base to start from.  

After it all comes back up again, look at the attached picture, and compare it to the top right corner.  DO either of these icons look like what you have?

---

### Post by jtarin on 2011-06-29
> **dulce said:**
> i have 10.04. what would you recommend? what happens to  my files, photos,etc doing that?

you sound pretty sure its an ubuntu problem.....I'm not saying its an Ubuntu problem amybe only a configuration problem. You might try to create a newuser and login in with that and try. If it works then you can transfer all your files to that user later.

---

### Post by dulce on 2011-06-29
> **ktmom said:**
> I can stay on-line for awhile so we can try things and I'll wait if you are ok with running back and forth across the street.

I'm nobody's expert, but I'm willing to bet we can get to the bottom of this although it may be a meandering route.  It sounds to me like you are missing a connection to a DNS server.

If you'd like to try, then my first question is, are you using a cable to connect directly to  the modem from the computer?  It looks like a large telephone type connector.  Or maybe it's a cable going to a router that then connects to the modem.

Otherwise, are you using a wireless connection of one sort or another to either connect wirelessly to the modem or through a router?

Have you rebooted all of the related hardware?  That means turn off the computer, and the modem and any hardware between like a router for at least 30 seconds.  Then turn on the modem, any hardware between the modem and computer and after all of that is on, turn on the computer.  Even if you have, if you would do that now, it would give us a base to start from.  

After it all comes back up again, look at the attached picture, and compare it to the top right corner.  DO either of these icons look like what you have?

that is so kind of you and lol-- your signature is so apt. 

guess what? my neighbor tells me she's leaving in 15 minutes and will be gone 2 hours. i will go do all that and come back later and see who's still with me.

if that attachment is the network notification, mine has a sort of energy beam circling 2 dots while its connecting and then resolves into something that looks like a pan flute when connection is made. and i'm getting the connection icon but foxfire can't locate anything.

---

### Post by dulce on 2011-06-29
... and yes, i'm using the cable. there is no other hardware. gotta go in about 10 minutes, back in 2 hours.

---

### Post by jtarin on 2011-06-29
Post your /etc/network/interfaces file

---

### Post by ktmom on 2011-06-29
> if that attachment is the network notification, mine has a sort of energy beam circling 2 dots while its connecting and then resolves into something that looks like a pan flute when connection is made. and i'm getting the connection icon but foxfire can't locate anything.

That sounds like you are using a cable.  

OK, try doing the complete shutdown and reboot while you are wating for your friend to come back.  After rebooting, try the ping google.com thing again.  If that works, then try opening your browser.  If it doesn't work, then let us know.

My thought is that you may find it easier to find the problem if one person steps you through so that you are not having an ADHD episode ;-)

---

### Post by dulce on 2011-06-29
> **jtarin said:**
> Post your /etc/network/interfaces file

my machine at home is not connected to internet so i can't post anything.

bye everyone, bqack in 2 hours.

---

### Post by ktmom on 2011-06-29
Oh, and if the ping google.com doesn't return a bunch of lines like;

> 64 bytes from 74.125.225.17: icmp_seq=1 ttl=53 time=152 ms
64 bytes from 74.125.225.17: icmp_seq=2 ttl=53 time=191 ms


then try ping 74.125.225.17 and see if that works.  If it does there is a DNS problem.

Use a Ctrl-C to exit the ping

---

### Post by dulce on 2011-06-29
> **ktmom said:**
> That sounds like you are using a cable.  

OK, try doing the complete shutdown and reboot while you are wating for your friend to come back.  After rebooting, try the ping google.com thing again.  If that works, then try opening your browser.  If it doesn't work, then let us know.

My thought is that you may find it easier to find the problem if one person steps you through so that you are not having an ADHD episode ;-)

lol-- it is getting thick. bye for now---

---

### Post by jtarin on 2011-06-29
I think I'll back out from this post as it seems you have someone else dedicated to helping you and better to track you.

---

### Post by dulce on 2011-06-29
guess what everyone-- don't get mad! :D

i turned everything off and rebooted as per ktmom's instructions. actually had to do it twice but here i am at home and everything works and seems normal...

i will say in my defense that the telmex guy told me not to turn off the modum. 

must have been a telmex glitch?

so thanks for your patience with this absolute beginner, likely to remain an absolute beginner. i'm not in the grew-up-with-computers generation, haven't taken classes. just got on internet 5 years ago, just got my own computer a year ago. what would i do without this forum?

---

### Post by ktmom on 2011-06-29
Then good for you.  You dove in where my teenager would have just pouted.  It's not uncommon for there to be a glitch within the hardware after a loss of service like you had.  The telmex guy was an idiot.  The first line of defense when you lose internet is to reboot everything and take your time about it.  It's almost always the modem, or router if there is one in the home network.

---

### Post by dulce on 2011-06-29
> **ktmom said:**
> Then good for you.  You dove in where my teenager would have just pouted.  It's not uncommon for there to be a glitch within the hardware after a loss of service like you had.  The telmex guy was an idiot.  The first line of defense when you lose internet is to reboot everything and take your time about it.  It's almost always the modem, or router if there is one in the home network.

i actually knew that about rebooting but never had rebooted the modum (which is wireless after all, not connected to the computer).

---

### Post by pimentel28 on 2011-06-30
> **dulce said:**
> guess what everyone-- don't get mad! :D

i turned everything off and rebooted as per ktmom's instructions. actually had to do it twice but here i am at home and everything works and seems normal...

i will say in my defense that the telmex guy told me not to turn off the modum. 

must have been a telmex glitch?

so thanks for your patience with this absolute beginner, likely to remain an absolute beginner. i'm not in the grew-up-with-computers generation, haven't taken classes. just got on internet 5 years ago, just got my own computer a year ago. what would i do without this forum?

Great to hear, dulce!

---

