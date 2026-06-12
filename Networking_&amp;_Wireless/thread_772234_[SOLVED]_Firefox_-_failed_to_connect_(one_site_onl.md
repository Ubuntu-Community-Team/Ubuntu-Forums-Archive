---
title: "[SOLVED] Firefox - failed to connect (one site only)"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by NDPeter on 2008-04-28
Just upgraded to hardy nearly pain free on 3 systems.  One of those is a web server I have running just for my own messing around.  Another was a laptop that I dual boot with Vista.  

Here's the magic I've managed to pull off.  I can access my website from any other computer, or even Vista on my laptop.  I can also connect via ssh from any other computer or Vista on the laptop.  As you can guess by now, Ubuntu on the laptop won't connect.  And it will connect to anything else I've tried.

In firefox the error i get is a "Page Load Error"  with the following text.

[I]Failed to Connect

Firefox can't establish a connection to the server.      
        

Though the site seems valid, the browser was unable to establish a connection.

    * Could the site be temporarily unavailable? Try again later.
    * Are you unable to browse other sites?  Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing.[/I]


Any ideas how to undo this "magic?"  It's got me stumped how specific it is.

Thanks.

---

### Post by golojo on 2008-04-28
> **NDPeter said:**
> Just upgraded to hardy nearly pain free on 3 systems.  One of those is a web server I have running just for my own messing around.  Another was a laptop that I dual boot with Vista.  

Here's the magic I've managed to pull off.  I can access my website from any other computer, or even Vista on my laptop.  I can also connect via ssh from any other computer or Vista on the laptop.  As you can guess by now, Ubuntu on the laptop won't connect.  And it will connect to anything else I've tried.

In firefox the error i get is a "Page Load Error"  with the following text.

[I]Failed to Connect

Firefox can't establish a connection to the server.      
        

Though the site seems valid, the browser was unable to establish a connection.

    * Could the site be temporarily unavailable? Try again later.
    * Are you unable to browse other sites?  Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing.[/I]


Any ideas how to undo this "magic?"  It's got me stumped how specific it is.

Thanks.

Hi,
Did U try to clean the browser's cache? Also check the proxy set up.

---

### Post by Monicker on 2008-04-28
Can you ping the web server from the ubuntu machine?  Can you resolve dns for the web server from the ubuntu machine?

---

### Post by NDPeter on 2008-04-28
I did try clearing the cache since I hadn't done that...but since this seems to affect trying to reach that machine from any app I wasn't hopeful and it didn't affect anything.

> **Monicker said:**
> Can you ping the web server from the ubuntu machine?  Can you resolve dns for the web server from the ubuntu machine?


This was interesting.  I don't know how to check about the dns.  When I just tried pinging though it never worked.  Got through about 80 tries and I realized I didn't know how to stop it and had to just close the terminal.  I then tried pinging from another machine.  That went normally.  I didn't remember the IP of my server though so both times i used the website name instead of a ping xxx.xxx.xxx.xxx  The troublesome ubuntu machine listed that it was trying a different IP.  Just checked...the reason it was familiar is because it was that machine's wired IP (we're forced to use static IPs where I tend to have it plugged in).

And one more piece to the puzzle.  I just took the IP from the working machine...the given one when I entered the command "ping [website.com]"...and put that IP into the terminal on the ubuntu machine...and after the first line it reverted the addy being pinged to the wrong one (the same wrong one.)

So now what?  The DNS servers control which IPs are reached by a given name right?  So is that what I've got going here?

Thanks again.  Sorry for being so long...wanted to give as much info as possible.

---

### Post by Monicker on 2008-04-28
To check your dns resolution from the ubuntu machine either of the following would work:

```
host www.mywebserver.com
nslookup www.mywebserver.com
```

Ping does name resolution by default, and you seem to have already seen what ip addresses the machines think the web server has.  fyi - you can limit the ping count with the -c switch: ping -c 5 4.2.2.2 - its normal for ping to keep going until you stop it or specify a limit.


I would also take a look at /etc/resolv.conf and see what namserver entries you have there for dns resolution.

---

### Post by NDPeter on 2008-04-28
Just started things up at work where things began breaking on Saturday.  Checked here before I tried may site.  when I entered either command you mentioned the values all were correct now.  So I tried to get to my server and it worked...the web site and everything else I'm playing with.  Tried both the wireless and wired connections too and all is fixed (for the moment I'll say to be safe.)

Can't say I really did anything.  I tried rebooting on Saturday so if it was something about starting up here today I couldn't tell you what was different.

Thanks for everything either way.

---

### Post by Mongoose.wa on 2008-04-28
I'm having the same problem now too. Certain sites produce the same "failed to connect" error in Firefox, including:

answers.com
opera.com
dictionary.com

When I try to ping these websites, I get 100% packet loss:

```
From D-128-95-49-180.dhcp4.washington.edu (128.95.49.180) icmp_seq=1 Destination Port Unreachable
```

I thought the problem might be OpenDNS blocking the sites, but I deleted the OpenDNS servers from the list in network-admin and /etc/dhcp3/dhclient.conf, but the site's still won't load.

This is extremely frustrating, so any help would be greatly appreciated.

---

### Post by alexsabree on 2008-04-28
I hate to say it.. but some websites just hate linux.

I'm not a genius with networking, but I get a lot of websites telling me that both my browser (firefox) and my OS (linux) are not compatible with the website.

---

### Post by rykel on 2008-06-09
Hi,

I am trying to access the following 3 websites and they all give me the same "Unable to connect to server" error. They are all domains purchased from Directnic.com.
[B][LIST=1]
[*][http://www.aenglobal.info](http://www.aenglobal.info)
[*][http://www.ibo21.org](http://www.ibo21.org)
[*][http://www.christian21.org](http://www.christian21.org)
[/LIST][/B]

I am using OpenDNS with no site blocker whatsoever.

btw, I think I can access any other sites, except the 3 above.

Thanks for helping!

---

### Post by bryncoles on 2008-06-18
hi! im also getting this cannot connect error - with yahoo.com, with gmail, with the university of limerick... its most annoying!

i can ping yahoo though, it always worked fine on my old computer, and (yesterday anyway) i could access it using thw wireless. so i would tentatively state that the problem is only with the cable connection...

anyone able to help?

---

### Post by alicemoon on 2008-07-14
I have same problem - works fine on wireless but wired I cannot access certain sites and cannot update. Have not found a solution yet - but am thinking it may be that my lan connection is an integral part of the motherboard (I use a shuttle) - though I cannot see why this means I can only access certain websites -

---

### Post by alicemoon on 2008-07-15
I just solved my access problems by changing the MTU to match the router - see my thread [here]("http://ubuntuforums.org/showthread.php?t=837413") hope this helps - it worked for me

---

### Post by NDPeter on 2008-11-24
I came back to this problem when I was away from work again for Thanksgiving and upgraded to Intrepid.  

Not sure how widely applicable this solution will be...but it fixed things.

[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

Note...I was getting the error "sudo: unable to resolve host HOSTNAME" and it was a different name I found in the /etc/hosts file.  Once those matched life was sweet.

---

