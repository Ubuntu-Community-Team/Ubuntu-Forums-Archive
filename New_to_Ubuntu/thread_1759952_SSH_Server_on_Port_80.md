---
title: "SSH Server on Port 80"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by Chrissd on 2011-05-16
Hi all,

Just wondering of any security risks or any other problems I should consider before running my SSH Server on port 80. The reason for this is my university on it's public wifi has many ports closed, so I was thinking of running it on port 80 as an obviously open port. I would then use SSH as a secure proxy outwards.

I do have an apache server, but don't need to access it from university, so will change the port it runs on (only used for test access).

Many thanks!

---

### Post by tkelito on 2011-05-16
As has been suggested before with SSH for true security use a Private and Public Key instead of password authentication.


Edit: [http://www.debuntu.org/ssh-key-based-authentication](http://www.debuntu.org/ssh-key-based-authentication)

---

### Post by Lars Noodén on 2011-05-16
You can [test other ports](http://www.canyouseeme.org/), but port 22 ought to be open.  Use keys for authentication if you are concerned about security.

---

### Post by Chrissd on 2011-05-16
I use keys and passwords are disabled, but I'm by no means a computer expert nor do I pretend to understand the complex bits. I know what I know by reading (lots). I study health care, not computers. :lol:

Port 22 is definitely closed since I cannot connect to any other SSH sites! I can't even ping sites to give you some idea of how weird this network is setup.

Do I understand that's it's no added security risk? Apologies to be such a newbie! :(

---

### Post by Lars Noodén on 2011-05-16
> **Chrissd said:**
> 
Port 22 is definitely closed since I cannot connect to any other SSH sites! I can't even ping sites to give you some idea of how weird this network is setup.

:(   :(  

> **Chrissd said:**
> 
Do I understand that's it's no added security risk? Apologies to be such a newbie! :(

Moving the port has no effect on security in and of itself.  You might consider using port 443 (for HTTPS) since that is also encrypted and the traffic might not stand out as much.  Not that SSH is going to look like SSL on close inspection.

---

### Post by Chrissd on 2011-05-16
Perhaps you guys might be able to confirm or bust a concern I have. Many forums that I visit (this one included) don't send the username and password encrypted. I can see many with the use of wireshark. I don't like visiting these sites on an unencrypted network (or even an encrypted network that I don't trust) since I fear my user name and password being stolen.

Is that a real possibility or am I just being paranoid?

---

### Post by tkelito on 2011-05-16
So I classify sites in two ways:

1) Sites that can hurt me (financially, socially, etc) - Email/Usernames/Passwords set A
2) Sites that are just sites - Email/Usernames/Passwords set B


I use different usernames and password sets for each.  So my ubuntu forums password has never and will never be used for my Twitter account.

My username never crosses that threshold either.  Also to go along with this they each link to different emails.  When I register for a site or use a service I classify it in one category.  

Paranoid yes, but it is a legit concern.  Set B would be the sites that either do or do not use https and pass data unencrypted, but if I were to have that password stolen it is a minor inconvenience.  Sites in group A I will not use unless they are SSL, and it is really a small subset, my Gmail/Facebook/Twitter/Bank.  Where as Group B is much much larger.  I really take the time to question a site on whether it is even worth signing up.  I do not use Facebook Connect, ever.

---

### Post by JKyleOKC on 2011-05-16
> **Chrissd said:**
> Perhaps you guys might be able to confirm or bust a concern I have. Many forums that I visit (this one included) don't send the username and password encrypted. I can see many with the use of wireshark. I don't like visiting these sites on an unencrypted network (or even an encrypted network that I don't trust) since I fear my user name and password being stolen.

Is that a real possibility or am I just being paranoid?It's a real possibility if you are on a shared network. That is, if you can run wireshark and see traffic from other users of your network, then they can see your traffic as well. If the network is managed with a switch rather than a hub, so that you can see only your own traffic and no one else's, then it's relatively safe.

Of course, you still have to trust the upstream providers at every point you can see reported on a traceroute, but these spots carry such heavy traffic that the likelihood of anyone sniffing it is low (unless you happen to be a "person of interest" to law enforcement, in which case paranoia should be your normal condition).

Categorizing sites is a good idea...

---

### Post by Lars Noodén on 2011-05-16
Privacy is a valid concern. About twenty years ago Phill Zimmermann [wrote PGP](http://www.mit.edu/~prz/EN/essays/) to help protect privacy.  When you can, use HTTPS.

---

### Post by Chrissd on 2011-05-16
Aces.

Thanks guys, I understand what you mean with regards to the sites, and I do this as a normal caution anyway. Also, I understand a hub sends all the data to everyone and a switch sends only your traffic to you, but I have no idea how to tell the difference. To me, at a site I don't trust 100% (but for the convenience use) such as University, Starbucks with free wi-fi etc, SSH secure proxy sounds like a sensible precaution. Using it on port 80 means that the outbound port will also be available, unlike my silly Universities setup and any other future places I'm likely to use it.

Many thanks guys.

I appreciate your time, advice and effort. :)

---

### Post by JKyleOKC on 2011-05-16
> **Chrissd said:**
> I understand a hub sends all the data to everyone and a switch sends only your traffic to you, but I have no idea how to tell the difference.Wireshark can tell you. If you see traffic from others, you're on a hub; if you don't, on a switch.

Note that you will still see packets from others that are addressed to you, but if your IP is not either the "from" or the "to" address that indicates you may be on a hub. Also, you will see broadcast packets, of course.

---

