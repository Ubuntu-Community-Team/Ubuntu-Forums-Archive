---
title: "Linux/Windows network issue (yes, another one)"
date: 2005-08-12
forum: Networking &amp; Wireless
---

### Post by Synner on 2005-08-12
I need access to my girlfriend's computer.  Her cd burner recently crapped out on her, she's got a 10Gb harddrive that is nothing but XP and music, and she wants it all saved in case the hard drive goes next...I told her I'd copy it all onto my computer and burn it from here.

So we go through Windows, share the entire hard drive, make a note of the workgroup and the computer name, and she went to bed.

I went down the street and connected to her router (gotta love wireless), went to the network folder, opened it, clicked on Windows Network, and nothing.  All it opens is an empty window.

I tried pinging her computer, 100% packet loss.  Go to the router info page, her computer's listed, but inactive.

I know that this will probably be an easy fix, but I'm a complete moron with networking, so I have to ask.  What do I need to do to get this network set up tonight?  As far as I know, the Windows side of things is taken care of, so the issue's got to be stemming from my computer.

---

### Post by blind0wl on 2005-08-12
If you cant ping it, sure she didnt turn it off on you :)

Can you get to a command prompt on the router to try and ping her machine?  Assuming you connected to the router, did it give you an IP through DHCP? Make sure the router is setup to allow more than 1 or 2 IP's to be taken from the DHCP server on it.  You might have nicked hers when connecting

---

### Post by Synner on 2005-08-12
[QUOTE=blind0wl]If you cant ping it, sure she didnt turn it off on you :)

Can you get to a command prompt on the router to try and ping her machine?  Assuming you connected to the router, did it give you an IP through DHCP? Make sure the router is setup to allow more than 1 or 2 IP's to be taken from the DHCP server on it.  You might have nicked hers when connecting[/QUOTE]


How would I go about getting a command prompt on the router?  I'm extremely new to networking, so I'm pretty much left in the dark.

Last time I was down there, I checked the LAN statistics page from the router setup, hers was set to 192.168.1.46, her parents was 192.168.1.45, and I don't remember what mine was, but it was on there too.

---

### Post by blind0wl on 2005-08-12
Well whats your IP currently, when its connected to her router via wireless?

---

### Post by Synner on 2005-08-12
I'll have to go back down to her house and check, I'm home now on a different connection.  Oddly, everything shows up perfectly on this connection, my roommate's computer shows up without a problem.

Thank you both for the quick replies, though!  I'm gonna run back down to her house and get the IP address, is there anything else I should check while I'm there?

---

### Post by blind0wl on 2005-08-12
Im trying to get my head around how your actually connecting to her.  Your using your PC which has a wireless card in it, setting it to talk to the SSID of your girlfriends router?  And your removing yourself from your own home network...maybe disable your ethernet connection....her router should be giving you an IP once you've connected to it successfully, and therefore you should be able to ping her router from your wireless pc....am I correct so far?

---

### Post by heimo on 2005-08-12
May I suggest different approach? Setup ssh server on your Ubuntu box, and use [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php) to push the files to your computer. Probably easier to setup - at least that's what I'd do.

---

### Post by Synner on 2005-08-12
[QUOTE=blind0wl]Im trying to get my head around how your actually connecting to her.  Your using your PC which has a wireless card in it, setting it to talk to the SSID of your girlfriends router?  And your removing yourself from your own home network...maybe disable your ethernet connection....her router should be giving you an IP once you've connected to it successfully, and therefore you should be able to ping her router from your wireless pc....am I correct so far?[/QUOTE]


I'm on wireless here at home, too.  (Inspiron 2650 laptop)  So....go to her house.  change ESSID to the one provided by her router.  Enable wlan0.  Internet connects from down there perfectly, but ping times out.

---

### Post by Synner on 2005-08-12
[QUOTE=heimo]May I suggest different approach? Setup ssh server on your Ubuntu box, and use [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php) to push the files to your computer. Probably easier to setup - at least that's what I'd do.[/QUOTE]

I would, but that would involve waking her up right now to install and work from the windows box.  I need this to be done remotely so I can have her music burned by tomorrow morning so she can take it to work.  Kind of a suprise, she's been freaking out about her cd burner all week since it went toes up on her, and she needs to clear up as much space as possible for school.  And I, personally, don't have physical access to her computer tonight.

---

### Post by heimo on 2005-08-12
[QUOTE=Synner]I would, but that would involve waking her up right now[/QUOTE]

Oh, ok. Both computers are basicly in same local (wireless) network? No firewalls between? In that case, you should be able to ping her computer, unless it's switched off.

And if it was switched off... and has WOL (wake on lan)... I'd use tool like this to switch it on:
[http://packages.ubuntu.com/hoary/net/etherwake]("http://packages.ubuntu.com/hoary/net/etherwake")

You need to know network interface cards MAC address to do that, but that information may be available on the router. :D (disclaimer: People usually freak out if they see their computer swithing on without anyone nearby.)

---

### Post by blind0wl on 2005-08-12
ping times out when you ping the internet or one of her addresses?  Sorry to be specific, but the more detail the better...and your definatley connected to her SSID when your at home?

---

### Post by Synner on 2005-08-12
[QUOTE=heimo]Oh, ok. Both computers are basicly in same local (wireless) network? No firewalls between? In that case, you should be able to ping her computer, unless it's switched off.

And if it was switched off... and has WOL (wake on lan)... I'd use tool like this to switch it on:
[http://packages.ubuntu.com/hoary/net/etherwake]("http://packages.ubuntu.com/hoary/net/etherwake")

You need to know network interface cards MAC address to do that, but that information may be available on the router. :D (disclaimer: People usually freak out if they see their computer swithing on without anyone nearby.)[/QUOTE]
 Got etherwake now, I'm sitting outside her house, tried sending the wake packet, got the response :"sudo:network is down."  I don't see how it's down, I'm sitting outside using it!

---

### Post by Synner on 2005-08-12
[QUOTE=blind0wl]ping times out when you ping the internet or one of her addresses?  Sorry to be specific, but the more detail the better...and your definatley connected to her SSID when your at home?[/QUOTE]

I'm sitting outside her house right now, definitely on her network.  Pinging google gets a response.  Pinging her local address gets nothing.


And for the sake of added clarification, her computer never gets shut off, she leaves WMP running all night so she has background noise when she goes to bed.

---

### Post by heimo on 2005-08-12
Not all computers support / accept WOL. I don't know if this is the case here. You're pretty sure the computer is on? And no firewall blocking access?

If I knew that I have permission to do it, I would port scan to find out if it's alive:
[http://packages.ubuntu.com/hoary/net/nmap](http://packages.ubuntu.com/hoary/net/nmap)

Sometimes just listening on the same network reveals Windows computers - those tend to broadcast a lot. ethereal or tcpdump are best tools for that purpose.

---

### Post by Synner on 2005-08-12
Well, she told me WOL was on, and she'd leave the computer running tonight so I could take care of all this...nmap only shows the router and me, nothing else.

---

### Post by heimo on 2005-08-12
[QUOTE=Synner]Well, she told me WOL was on, and she'd leave the computer running tonight so I could take care of all this...nmap only shows the router and me, nothing else.[/QUOTE]

Sorry, no more ideas what to do, except to check that computer on location.

---

### Post by Synner on 2005-08-12
[QUOTE=heimo]Sorry, no more ideas what to do, except to check that computer on location.[/QUOTE]
 Well, she gets up for work at 6, so I'm SOL until then.  The only thing that's getting me now is that she's still connected to Trillian....weird.  Oh well, I guess I'll take care of it tomorrow.  Thanks to both of you for all the help, sorry it was a fruitless effort!

---

### Post by Synner on 2005-08-12
Well, it turns out she had the XP built-in firewall on, but failed to mention that when I asked if she had a firewall.   ](*,)   So now I can see the computer on the network, but despite the whole drive being shared, I still don't see anything.  If anybody could help with this, I'd really appreciate it!

CLIFFS:  Network fixed, but nothing shows up as shared, despite the whole hard disk on the XP machine being shared.

---

### Post by N8MAN1068 on 2005-08-12
i think by now, I would've grabbed my tower and a patch cable, and sneakernet'd over there.

transfering a cd's worth (6-700mb) of data over wireless (5Xmbps max on a good day) will take awhile, let alone 10gb.
carrying your equipment over there would be less of a headache than dealing w/ packet loss+failed file transfers through wireless.
granted, this might not be the solution to the 'why can't i access her pc' issue, but it is a 'fix' to 'how do i get the data'.
 ;-)

but, you could also do 'smb://machinename(or ip)/c$, enter local admin acount, and be smooth sailing.

---

### Post by Synner on 2005-08-12
[QUOTE=N8MAN1068]i think by now, I would've grabbed my tower and a patch cable, and sneakernet'd over there.

transfering a cd's worth (6-700mb) of data over wireless (5Xmbps max on a good day) will take awhile, let alone 10gb.
carrying your equipment over there would be less of a headache than dealing w/ packet loss+failed file transfers through wireless.
granted, this might not be the solution to the 'why can't i access her pc' issue, but it is a 'fix' to 'how do i get the data'.
 ;-)

but, you could also do 'smb://machinename(or ip)/c$, enter local admin acount, and be smooth sailing.[/QUOTE]

On a laptop, so no problems there.  No patch cable though.

Not allowed in the house, as per her stepdad's rules.

This will probably be a process over a few days, getting as much time sitting on the sidewalk unnoticed as possible.

I didn't even think about smb:// since she disabled the firewall, I've been trying to set up a mount point, and it's been giving me hell.  She set up an admin account for me so I could do this, with no password, but when I try to log in, it either says access denied or share doesn't exist, depending on which variation of the username I'm using.

So with smb://bla.blah.blah.blah/c$, I should be able to log in with the new account through the file browser, right?

---

### Post by N8MAN1068 on 2005-08-12
[QUOTE=Synner]
So with smb://bla.blah.blah.blah/c$, I should be able to log in with the new account through the file browser, right?[/QUOTE]

right.

or, take out the hdd, slave it to a desktop.

---

### Post by Synner on 2005-08-12
[QUOTE=N8MAN1068]right.

or, take out the hdd, slave it to a desktop.[/QUOTE]

And what are the odds that I'll run into the same problem as using the terminal and not be able to log in because there's no password?

---

### Post by Synner on 2005-08-12
[QUOTE=Synner]And what are the odds that I'll run into the same problem as using the terminal and not be able to log in because there's no password?[/QUOTE]
 *BUMP*  Yep.  No password, no access.  No matter how I try it.  Please, does anybody have any ideas for this?  Would something as simple as putting a password on the account work?

---

