---
title: "settings network connected - no internet"
date: 2024-06-25
forum: Networking &amp; Wireless
---

### Post by jgw on 2024-06-25
This is another attempt at dealing with a machine where the settings network is connected but ubuntu doesn't accept it.  Below is an effort to help with the solution.  I should also note that I am getting all this stuff together with two computers.  There are photos of settings/network connect - One works with internet and the other doesn't (that is the one with Ethernet involved).  All the testing involve the machine that has no internet. 

This time I am not going to say this is solved until I can open and close a functional system for at least a couple of days.

variety of tests of network:
[https://paste.ubuntu.com/p/2rd5h5KP5k/](https://paste.ubuntu.com/p/2rd5h5KP5k/)

Hardinfo reports on working and not working systems.
[https://paste.ubuntu.com/p/2rd5h5KP5k/](https://paste.ubuntu.com/p/2rd5h5KP5k/)

If you want more tests just ask.  Also tell me if you need them on the system that works and does not work or just the one that works. 

Thank you...................

---

### Post by currentshaft on 2024-06-25
What does "no internet" mean?

Can you resolve DNS? "dig a google.com" and "dig a google.com @8.8.8.8"

What does "curl -Lfv google.com" return?

---

### Post by jgw on 2024-06-26
"No internet" means that I have a system wherein my settings network is connected (see photos) but ubuntu does not use or connect to it so I cannot access the internet.

---

### Post by wildmanne39 on 2024-06-26
Moved to networking and wireless sub-forum.

---

### Post by currentshaft on 2024-06-26
> **jgw said:**
> "No internet" means that I have a system wherein my settings network is connected (see photos) but ubuntu does not use or connect to it so I cannot access the internet.

I don't have the ability to view images. Please run the troubleshooting commands I suggested in my previous post instead.

---

### Post by jgw on 2024-06-27
I apologize, I thought I had this in my last and screwed up.  Here are the answers:

```
greg@greg-desktop:~$ dig a google.com

; <<>> DiG 9.18.24-0ubuntu0.22.04.1-Ubuntu <<>> a google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 41926
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		16	IN	A	172.217.14.206

;; Query time: 20 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Thu Jun 27 12:57:24 PDT 2024
;; MSG SIZE  rcvd: 55

greg@greg-desktop:~$ dig a google.com @8.8.8.8
;; communications error to 8.8.8.8#53: connection refused
;; communications error to 8.8.8.8#53: connection refused
;; communications error to 8.8.8.8#53: connection refused

; <<>> DiG 9.18.24-0ubuntu0.22.04.1-Ubuntu <<>> a google.com @8.8.8.8
;; global options: +cmd
;; no servers could be reached


```

I ran the curl request but, when I tried to put the results here I got:
Forbidden
You don't have permission to access this resource.

I tried parts of it, etc. but Ubuntu just didn't like it.

I put it here: [https://paste.ubuntu.com/p/RhqkJjkZYr/](https://paste.ubuntu.com/p/RhqkJjkZYr/)

---

### Post by currentshaft on 2024-06-27
Is the gateway/router applying some sort of firewall rules?

---

### Post by jgw on 2024-06-27
I have no idea nor do I know how to find out.  Might be but have no idea......

---

### Post by morovan on 2024-06-28
Looks like you are connected to internet, but google reject to serve you. Dirty IP perhaps? If that would be the case, checking IP reputation may give you some clue, but not sure if your problem doesn't stop you from finding out your own public IP address.

Could you try to run same command against hosts less picky than google?

```

dig a google.com @1.1.1.1
curl -Lfv https://example.com/

```

---

### Post by jgw on 2024-06-28
Morovan - here is one from 
[https://paste.ubuntu.com/p/DZMgqXTwbP/](https://paste.ubuntu.com/p/DZMgqXTwbP/)

---

### Post by morovan on 2024-06-28
Thanks.  Yes you are indeed connected to internet - output of curl command returns valid response from website example.com. Though DNS request was refused, just like earlier with google. However your local DNS resolver seems OK. Either I was wrong about cloudflare not being picky or there is some UDP packet manipulation taking place on the route.  I am guessing you identified issue while attempting to use web browser... Could you use it to visit [https://example.com/](https://example.com/) and [https://1.1.1.1](https://1.1.1.1) Do you get an error message?

---

### Post by jgw on 2024-07-02
Thank you for the reply..........

Yesterday I was connected but my system was completely screwed up (little things like not accepting my passwords, amongst other things).  Today I got things cleaned up and working but, first, I turned on the machine and it was not connected.  I then re-booted and now I am up and using the bad machine.  I have no idea what happened as I did nothing.  Perhaps you might have done something?  Anyway its up and running.  I am going to test it for a bit before I start using it again.  My other machine has become my main machine for a while now so I have to make sure the other machine is actually running right all the time.  The strange thing is that the bad machine still has the pci ethernet (not connected) and the ethernet (which is connected) in settings.  On the machine I am using now there is no ethernet stuff in settings just 'wired'.  This is all very strange which is why I want to try it for a while before I believe its dandy.  Another thing I just noticed that this is now page 1 of 2 (I think) I will post this and see what happens.  After posting I was back on page 2 so I guess that was alright.  I have two other machines I use and they are both 'wired'.  Have no idea how I got to the ethernet stuff (or how the machine got completely screwed up)

Thank you!

---

### Post by jgw on 2024-07-03
Today I turned on the bad machine.  It came up but did not connect with the internet.  I then re-booted the machine and, this time, it was connected to the internet.  In both cases it turned on firefox.  It was also connected to about 9 different places.  I had set firefox to have two connections, Yahoo and Mail, that's it.  I have no idea why its connecting with all that stuff the first time it comes up.  This machine behaves very oddly.

Thoughts?

---

### Post by currentshaft on 2024-07-03
Run tcpdump on the active interface when network connectivity is out. It sounds like another device on the network has the same IP address lease, but it's hard to say without seeing packet capture output.

---

### Post by morovan on 2024-07-04
>  ... turned on firefox.  It was also connected to about 9 different places.  I had set firefox to have two connections, Yahoo and Mail, that's it.  I have no idea why its connecting with all that stuff ... 

I am not suggesting to follow below article and turn it all off, but it gives you an idea why firefox makes various connections on start-up:
[https://support.mozilla.org/en-US/kb/how-stop-firefox-making-automatic-connections](https://support.mozilla.org/en-US/kb/how-stop-firefox-making-automatic-connections)

---

### Post by jgw on 2024-07-04
Today I turned on the bad machine and it was actually attached to the internet.  Firefox too was just fine.  I have no idea why.  Nothing else, as far as I can tell has changed.  its a mystery!  I will just keep on testing it to see what happens.  The system settings are also entirely different from two other machines.  Strange.............

---

### Post by jgw on 2024-07-05
I am marking this as solved - thank you!!

---

