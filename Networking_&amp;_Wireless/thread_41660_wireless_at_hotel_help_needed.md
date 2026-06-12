---
title: "wireless at hotel help needed"
date: 2005-06-14
forum: Networking &amp; Wireless
---

### Post by banditti on 2005-06-14
I am at a hotel, that provides wireless.  They are one of the ones that you have to bring up a web page to connect.  I can see the AP's, but can't pull DHCP or bring up that web page.  Any thoughts?

---

### Post by Gandalf on 2005-06-14
[QUOTE=banditti]I am at a hotel, that provides wireless.  They are one of the ones that you have to bring up a web page to connect.  I can see the AP's, but can't pull DHCP or bring up that web page.  Any thoughts?[/QUOTE]
 i have the same problem, at university it's wifi no-secure but neither DHCP nor pages open, i need to put a code before connect, windoze works smooth with it, but didn't try harder yet to get it working,
any thoughts?

---

### Post by nocturn on 2005-06-14
[QUOTE=banditti]I am at a hotel, that provides wireless.  They are one of the ones that you have to bring up a web page to connect.  I can see the AP's, but can't pull DHCP or bring up that web page.  Any thoughts?[/QUOTE]

I have no idea how these work...  Maybe call the front desk, tell them you want to connect but can't.   (if it didn't say you required Windows to stay at their hotel, they should help you).

---

### Post by python on 2005-06-14
[QUOTE=nocturn]I have no idea how these work...  Maybe call the front desk, tell them you want to connect but can't.   (if it didn't say you required Windows to stay at their hotel, they should help you).[/QUOTE]

Very doubtful they will be able to help.

Can you ping the AP?

---

### Post by anders.ostling on 2005-06-14
here is what I do when I came to Hilton, New Orleans last week.

1. Make sure that the wifi driver is loaded (modprobe ipw2100)
2. Find out what the hotels "id" is (iwlist scan). Look for "ESSID"
3. Set the id manually (iwconfig eth1 essid ESSID)

Make sure that you picked up an access point. Type iwconfig and look for a MAC address, not zeros but a real address. 

4. Grab an IP address (dhclient eth1). 

If this succeeds, then the tricky part can be to find the "pay-gateway" that you need to access. I usually look at the default gateway and try to access that one using Firefox. Worked fine last time ;-)

Anders

---

### Post by banditti on 2005-06-14
I can iwlist and see the essid and all other info.  I iwconfig everything and make it match, but no dhcp.

---

### Post by kleeman on 2005-06-14
Sometimes this can happen if the signal is weak. What does dhclient show?

---

### Post by anders.ostling on 2005-06-15
Could it be that the AP has an ACL that only allowed certiain (pre-paid) mac addresses to have an IP address. Sounds not very easy to administer, so there is probably something else that is the problem. Do you have any firewall that prevents the DHCP replies to reach you? Have you tried tcpdump to see what actuall is transmitted and recieved by your machine?

Anders

---

### Post by nocturn on 2005-06-15
Anyone knows how this kind of thing works in Windows?

I mean, it pops up a list of available AP's, you select it and then?  How do you know to which page IE has to go?

---

### Post by somuchfortheafter on 2005-06-15
this is funny as it works fine at the hotel i just stayed at... are you guys using the latest 2200 b/g drivers assuming that is what card you are using...

---

### Post by kleeman on 2005-06-15
From what I have seen you get a dhcp address and all browser requests are shunted to a fixed webpage where you need to put in your credit card details. Interestingly I find you can still use nmap to scan the lan (in linux) and many silly winblows users are often wide open. Not advisable to try to exploit this situation- probably end up in jail!    ;-)  ;-)

---

### Post by tread on 2005-06-15
My college has a similar scenario .. log in at a webpage .. and it works fine. I'll just repeat what the person above said .. it might be a firewall issue.

---

### Post by ssck on 2005-06-15
i am not sure if the situation i have is similar to this post :

in starbucks (kuala lumpur, malaysia), when you select a particular essid, it will automatically redirect to a webpage where you are required to enter a login id and password (both of which are provided).you will then be able to access the internet.this service is free and is paid for by starbucks.this was when i was still using win xp.

i have not tried this with ubuntu yet.if i do pop by starbucks, will try out and see if it works like it used to.

---

### Post by nocturn on 2005-06-16
[QUOTE=ssck]i am not sure if the situation i have is similar to this post :

in starbucks (kuala lumpur, malaysia), when you select a particular essid, it will automatically redirect to a webpage where you are required to enter a login id and password (both of which are provided).you will then be able to access the internet.this service is free and is paid for by starbucks.this was when i was still using win xp.

i have not tried this with ubuntu yet.if i do pop by starbucks, will try out and see if it works like it used to.[/QUOTE]

Hi SSCK

What does you nick mean? (I work at a place called SCK, so I was curious).

Back to the topic, how does it redirect you to the webpage?  I mean, does it open IE (or do you have to do that), does it change the homepage IE goes to?
I have never done this, so I'm curious and if we find the mech used, we can see if it can work on Linux.

---

### Post by trivialpackets on 2005-06-16
[QUOTE=nocturn]Hi SSCK

What does you nick mean? (I work at a place called SCK, so I was curious).

Back to the topic, how does it redirect you to the webpage?  I mean, does it open IE (or do you have to do that), does it change the homepage IE goes to?
I have never done this, so I'm curious and if we find the mech used, we can see if it can work on Linux.[/QUOTE]
 I have this issue as well and get it whenever I switch to a different AP.  I don't know the resolution, but the workaround that I was able to employ, and it seems to work with my university, here and parent's home, is that I boot into Ubuntu.  The network manager in gnome allows me to change AP's, but the tools in Kubuntu do not.  I have no idea as to why, but it has worked for me in the past, may be worth a try if it Ubuntu is installed as well.  Good luck, and I'll keep posted.

---

### Post by ssck on 2005-06-16
[QUOTE=nocturn]Hi SSCK

What does you nick mean? (I work at a place called SCK, so I was curious).

Back to the topic, how does it redirect you to the webpage?  I mean, does it open IE (or do you have to do that), does it change the homepage IE goes to?
I have never done this, so I'm curious and if we find the mech used, we can see if it can work on Linux.[/QUOTE]


the nick are the initials to my name.when i was using win xp, it will automatically redirect  to the website.then i will logon from there using the login id and password provided.

---

### Post by nocturn on 2005-06-17
[QUOTE=ssck]the nick are the initials to my name.when i was using win xp, it will automatically redirect  to the website.then i will logon from there using the login id and password provided.[/QUOTE]

Yes, but how does it redirect?  Does the browser pop up?  Or when you open the browser, does it show the page with the login?

---

### Post by ssck on 2005-06-17
[QUOTE=nocturn]Yes, but how does it redirect?  Does the browser pop up?  Or when you open the browser, does it show the page with the login?[/QUOTE]

i am not sure how it redirects but yes, the browser window will automatically pop open  for me to login

---

### Post by circussideshow on 2005-06-17
I was recently at the Hilton in Waikiki and had similar issues.  Most of setups I have seen like the ones you describe here use some sort of firewall that blocks web/ssl/im/etc but allow icmp before you authenticate.  In windows, normally you have to open up IE and this should attempt to load your home page, which will send stuff via port 80.  The system detects this and redirects you to their login site where you just login or pay for use.  After you login, all ports should be opened for your particular IP or MAC.  At least this is how I *think* it works.  When I am on ubuntu, I just hop on an AP and get an IP via DHCP and point my browser to the default gateway, or I war-ping to find any local machines to log into.  This has always worked for me.  Like someone else said, I would use tcpdump or ethereal to grab some packets to check what exactly is going on.  I hope this helps. :)

---

### Post by antwerx on 2005-06-17
Hello - I was recently at a Comfort Inn.

This is how it worked there. I checked my Wireless monitor, Gnome, top right of screen on the tollbar.

Go to properties and check for the AP, mine was Goldentree, then select it. Make sure your Wireless card is set to dhcp, then make sure you set the wireless card as the default device, mine is ath0.

Then pull up your browser and put any internet addy in and hit enter. This will pull up the internal splash page were you must accept their terms via check box, At Comfort Inn you then needed to put in a username password. The user name was the room number , password was requested via calling the front desk.

Most all hotels operate in the same manner. Also the internal splash page will outline all your requirements to connect.

Hope this helps.  :smile:

---

### Post by ssck on 2005-06-17
[QUOTE=circussideshow]I was recently at the Hilton in Waikiki and had similar issues.  Most of setups I have seen like the ones you describe here use some sort of firewall that blocks web/ssl/im/etc but allow icmp before you authenticate.  In windows, normally you have to open up IE and this should attempt to load your home page, which will send stuff via port 80.  The system detects this and redirects you to their login site where you just login or pay for use.  After you login, all ports should be opened for your particular IP or MAC.  At least this is how I *think* it works.  When I am on ubuntu, I just hop on an AP and get an IP via DHCP and point my browser to the default gateway, or I war-ping to find any local machines to log into.  This has always worked for me.  Like someone else said, I would use tcpdump or ethereal to grab some packets to check what exactly is going on.  I hope this helps. :)[/QUOTE]

i suppose there should be no problems detecting the AP.i guess you will have to find out which website to go to to access the login page since we are not using IE which would fire up automatically.

---

### Post by sanicki on 2007-07-23
Anybody find a solution? I'm unable to get my hotel internet (though at one point I did get as far as their login page in Firefox) or local free community wifi. Yet convention center wifi works like a charm.

---

### Post by mastergunner on 2007-08-13
.....

---

### Post by wirelessmonkey on 2007-08-13
Typically this is done by proxy.  You select or define which network to connect to, dhcp an IP address.  Open a web browser of choice and attempt to browse anywhere... their router or authentication server will redirect your browser to their authentication page. Enter required information and your MAC address will be authenticated and you will be able to browse normally.

---

### Post by mastergunner on 2007-08-13
I am staying at a Crown Plaza and I can not even connect to their server. It gets to the point of IP Config and it stops there and then times out. I am using Kubuntu 7.04 and would like a little help from the forum. I am a noob so careful instructions would be helpful. I am typing this on the guest computer. Thanks for all og you guys help.

---

