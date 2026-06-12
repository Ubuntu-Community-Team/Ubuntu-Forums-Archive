---
title: "Keeping my computer secure and private on a wireless internet connection"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by hanzj on 2008-03-02
Hello,

I'm connecting to the internet using a desktop computer with a wireless PCI G card installed. There is a wireless router in one of rooms of my home. 

I can access it just fine. There is no password installed on the network, so anyone can use the internet connection. (This isn't my choice, but my kind room-mate's choice.)

Is it safe for me to use the internet connection? Can people snoop onto my internet activities? What can people (router owner and anybody else on this wireless network) know about me?  Do I have privacy? If not, how can I attain privacy? Does using "https" sites help?
Can they hack onto my Ubuntu PC? Is my Ubuntu PC secure?  Can they see what files are on my computer? (My computer asks for my username and password every time the computer boots.)

There are probably other questions that I should ask, but am not asking. So please tell me everything that I should know.

Thank you.

---

### Post by Hightide on 2008-03-02
HI hanzj

You are using a very insecure network with no protection whatsoever.I would recommend an up to date wireless security protocol  WPA2 (see [here]("http://en.wikipedia.org/wiki/WPA2") for more info)

Also see wiemans01's [thread]("http://ubuntuforums.org/showthread.php?t=318539")

All your mate has to do is set up a shared WPA2 key via his router admin to enable you to access. This will prevent external warchalkers from using his wireless network as they will have to discover the shared key.

Hope this helps


regards

:)

---

### Post by rickyjones on 2008-03-02
> **hanzj said:**
> 
Is it safe for me to use the internet connection? 

I would say that it is perfectly safe. An "open" wireless router just means anyone can connect to it. At that point people could run, say, a network sniffer and find out what IP addresses are in use and what protocols are going there, but really, who is going to take that much time to go after you? 

> **hanzj said:**
> 
Can people snoop onto my internet activities? 

Not without some extra work on the side. An open wireless network is just like someone plugging their computer into one of the LAN ports on the router. I wouldn't worry about it unless you are not using a somewhat secure setup.

> **hanzj said:**
> 
What can people (router owner and anybody else on this wireless network) know about me?  

If they do enough work then they can sniff the traffic. The information they will pull up will include protocols in use and destination IP addresses. Depending on the protocol they might see information that you send and receive. But wading through those log files is time consuming. Do you think people have a vested interest in knowing what you do? Once again, I wouldn't worry about this too much.

> **hanzj said:**
> 
Do I have privacy? If not, how can I attain privacy? Does using "https" sites help?

I think you have plenty of privacy. I run all my business information on my laptop and I constantly do business in local coffee shops that do not have a secured wireless setup. Yes, HTTPS sites will help because all traffic to/from that website will be secured.

> **hanzj said:**
> 
Can they hack onto my Ubuntu PC? Is my Ubuntu PC secure?  Can they see what files are on my computer? (My computer asks for my username and password every time the computer boots.)

Anything is possible. Now, hacking in to your PC will be very difficult as long as you 1) Have not installed extra services (SSH, SAMBA, FTP, etc...) and 2) You use a decent password (at least 7 characters with #s, CAPITALS, and !@#$ symbols).

> **hanzj said:**
> 
There are probably other questions that I should ask, but am not asking. So please tell me everything that I should know.

I can't possibly tell you everything that you should know but I can hopefully provide you with enough information to come to your own reasonably justified conclusions.

> **hanzj said:**
> 
Thank you.
You're welcome!

Sincerely,

-Richard

---

