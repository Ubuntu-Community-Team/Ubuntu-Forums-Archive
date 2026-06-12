---
title: "Wireless network problems"
date: 2005-05-27
forum: Networking &amp; Wireless
---

### Post by Hardi on 2005-05-27
Hy.
I just installed Ubuntu and wanted to connect to the internet, but I can't.
I have 2 OS on my computer: XP professional and Linux Ubuntu.
Ubuntu detected my ethernet card, which's name is Realtek RTL8139/810x Family Fast Ethernet NIC.
I configured the ip addresses - same as on my XP. But I can't connect to the internet - when opening for example [www.ubuntuforums.org](www.ubuntuforums.org) with FireFox, it just says in the status bar : "Looking www.ubuntuforums.org". Finally it says "... Could not be found"(or something like that).
Please help.

Hardi

---

### Post by wbeck85 on 2005-05-27
[QUOTE=Hardi]Hy.
I just installed Ubuntu and wanted to connect to the internet, but I can't.
I have 2 OS on my computer: XP professional and Linux Ubuntu.
Ubuntu detected my ethernet card, which's name is Realtek RTL8139/810x Family Fast Ethernet NIC.
I configured the ip addresses - same as on my XP. But I can't connect to the internet - when opening for example [www.ubuntuforums.org](www.ubuntuforums.org) with FireFox, it just says in the status bar : "Looking www.ubuntuforums.org". Finally it says "... Could not be found"(or something like that).
Please help.

Hardi[/QUOTE]
 Hardi, when you say "I configured the ip addresses - same as on my XP" you dont mean that it has the same ip address, do you? That would be your first problem if that's what you did.

Another thing: your thread title says "Wireless network problems", however, the ethernet card that you listed, the realtek card, is not a wireless card. Are you trying to connect wirelessly with it? 

ut, lets say that you do have a wireless card that was detected properly by ubuntu.
How is your XP machine connected to the web? are you using broadband with a wireless router? Is the XP machine connected wirelessly or with an ethernet card? Is your router set up to use DHCP? Are you using Windows Internet Connection Sharing (In which case, you would not set up your router to use DHCP and would assign the host computer (the sharer of the connection) with 192.168.0.1 and your ubuntu laptop with 192.168.0.x (That x can be replaced by anything between 2 and 255). If you have a broadband modem to wireless router and have set it up properly, open "network-admin" select your wireless card and click "Properties." Check the "This device is configured" box, set the essid of the router in the ubuntu network-admin app and select DHCP in "Configuration" and the WEP key (if you are using one). then click "OK" then "OK again to get out of network-admin. Then in a terminal, type "sudo /etc/init.d/networking restart" Let it work and you should be good.

If you don't have a wireless card on your computer and the "WIreless" part of your title was a fluke, do this:
   Is your XP set up for broadband using a modem to router to computer setup?
      if so, is your router set up for DCHP?
      If so, follow the above directions, negating the wireless specific parts (essid, wep)
   Is your XP machine connected directly to the broadband modem?
      If so, you need to get a router, or you need another NIC in your XP box (so you can use           ICS)
   Is your XP machine connected to the internet using dialup?
      If so, you need to use ICS. Once you have set that up, connect your ubuntu box to the XP machine witht he ehternet cable, set the XP NIC to use the IP 192.168.0.1 and the ubuntu box to use 192.168.0.x  YOu can use the default subnet mask. Set the gateway on the ubuntu machine to use the XP machine NIC's IP address. then, in network-admin, on the DNS tab, set the first DNS server address to be the XP NIC's IP address as well.

Uh, I think I covered most of the possibilities for networking setup troubles. I didnt cover all of them, and none of them absolutely clearly, sorry about that.

In your next post, try to be a bit more thorough with your description of your problem. It is easier to diagnose and solve issues when the entire story is known. good luck with ubuntu!

---

### Post by Hardi on 2005-05-27
So.
Here's the deal:
I have 2 OS on my computer.
And 1 integrated modem and 1 not integrated modem(that is the Realtek card).
I connect to the internet using the Realtek card.
Here's how my wireless network works:
In our village we have 2 radio towers which provide people with internet.
Under 1 tower, there are tens of people.
In my computer, there is a modem, which is connected to a wire which leads to a dish(the thing that sends out signals and receives them).
Ip = 192.168.1.20
Gateway = 192.168.1.1
mask = 255.255.255.0
And that's how I configured the network card with XP and Linux Ubuntu.
On XP, the internet works.
On Ubuntu, it doesn't, but in the Network tools, it shows that my realtek card is sending and receiving packages all the time.
Yes, I use 1 modem with 2 OP sys and I configured the card the same way with those OS'es.
My card may not be a wireless card, but it does connect to the internet wirelessly remotley. I think, the dish is the main dude( :D ), it sends and receives and just gives me my data through a modem.
Thank you for your long post :).
I'll try those advices that you gave in your post.
Please reply to this post, because I beleive, that I can't get my internet configured(again :( ).

PS.
I can't understand those abbreviations: DHCP, ISP and so on.
They are like Chinese.

---

### Post by xristos on 2005-05-27
> In our village 

May I ask where do you live ?
Where is that village that offers wirelles internet ?
I want to move there ...

with best regards

---

### Post by Hardi on 2005-05-27
Heh, I guess you are joking at me.
I live in Estonia, In Pärnu county in Vändra vald

---

### Post by xristos on 2005-05-27
So my next trip in Europe is Estonia !!!

As for your problem I think you should check your DNS IP .

Maybe you have internet but your DNS server is not set .

Question : Are you connecting through a vpn server ?

---

### Post by wbeck85 on 2005-05-27
[QUOTE=xristos]May I ask where do you live ?
Where is that village that offers wirelles internet ?
I want to move there ...

with best regards[/QUOTE]
 DHCP = Dynamic Host Configuration Protocol: "An Internet protocol for automating the configuration of computers that use TCP/IP. DHCP can be used to automatically assign IP addresses, to deliver TCP/IP stack configuration parameters such as the subnet mask and default router, and to provide other configuration information such as the addresses for printer, time and news servers." ~[www.dhcp.org](www.dhcp.org)
ISP = Internet Service Provider: The provider of your internet connection (The broadcaster of your wireless signal
ICS = Internet Connection Sharing: Service built into Windows XP that allows the XP computer to share its connection with other computers through it
NIC =  Network Interface Card: Your ethernet card.
DNS = Dynamic Name Server: "Short for Domain Name System (or Service or Server), an Internet service that translates domain names into IP addresses. Because domain names are alphabetic, they're easier to remember. The Internet however, is really based on IP addresses. Every time you use a domain name, therefore, a DNS service must translate the name into the corresponding IP address. For example, the domain name [www.example.com](www.example.com) might translate to 198.105.232.4. The DNS system is, in fact, its own network. If one DNS server doesn't know how to translate a particular domain name, it asks another one, and so on, until the correct IP address is returned. " ~[www.webopedia.com](www.webopedia.com)

Well, you're welcome. 96 posts I have and i think 8 of them have been informative. Just helping out, paying my dues for the help I have already recieved :)

So, let me get this straight your realtek card is set up in the following manner:
ip = 192.168.1.20
Gateway = 192.168.1.1
mask = 255.255.255.0

The dish's ip address is 192.168.1.1, then, right? That is good. It seems to me, that if you have set that stuff up in ubuntu, just as you have it, it should work. I am not entirely sure what you should do about the DNS setup in your case, however. Do you know how it is set up in XP? I would set the first DNS Server to 192.168.1.1 (the address of your dish) then click add and the second one to 192.168.1.20 (your NIC address) Hopefully one of those will work.
Now you can click ok so get out of network-admin. open up a command console and type "sudo /etc/init.d/networking restart" this should reset your card, (I think) and hopefully, the internet will be accessable!

In a console, can you ping a site, like google.com? type "sudo ping -c 4 google.com" If you can, you should be able to access the internet. If you can't try pinging your dish "sudo ping -c 4 192.168.1.1" and then try pinging another computer's ip in your village, so see if you are at least to the network. You are experiencing probably a DNS problem.

I wish I had a system working like that for me, with the dish and broadcasting towers and such. I am currently stuck with a dialup connection. Very slow. Good luck with ubuntu!

---

### Post by Hardi on 2005-05-28
Hy.
No, don't want that. The first year, when I got my internet, It stopped 1 day after it was set up  ](*,) 
The Internet provider thought that I am a fool and don't know anything about computers - I know very much about XP and I am a programmer(not working for someone. just for my own fun. (I am 14 years old)). So I started to annoy him until he put up a dish, which now works quite well.
before, I had a little white box that was on the roof of my apartment and the white box was connected to my NIC(Yes, I am using new abbreviations :D ) by a tiny white cable. Often it said: "Wireless connection unavaible".
Ok.
Explanation:
I think my NIC address is 192.168.1.196
The dish address is 192.168.1.246 (although I am not sure)
The tower, which my dish connects thorough air(that's why it's called "Wireless")
has an address 192.168.1.1

The reasaon why I am gussing this, is because I pinged my NIC and it was <1ms.
Then I pinged the .246, and the ping was around 3 ms.
Then I pinged .1 and the ping was around 20ms.
That means - NIC is near, pind is small.
Dish is about 10 metres away - ping is slower - 3 ms.
And the tower is about 100 metres from the dish - the ping is more slower.
Sometimes the ping between me and the tower is 1000 ms :(

So, where can I set my DNS?
On xp, it asks my preferred DNS and alternate DNS.

But on Ubuntu, it just asks for IP, mask and gateway.

---

### Post by Hardi on 2005-05-28
I went to Ubuntu. Opened the Root Terminal.
typed 
sudo ping -c 5 192.168.1.1
sudo ping -c 5 192.168.1.196
sudo ping -c 5 192.168.1.246

And none of them answered.
It said: "Destination host unreachable"
If my NIC address is really 192.168.1.196
then why can't it get an answer from there !?

---

### Post by Hardi on 2005-05-28
A really odd fact, is that when  I delete my DNS address from Network Connections>Properties of my connection>Internet Protocol>Properties
then my internet still works on XP.
But why does Ubuntu need DNS so much(I guess that's the problem).
And where can I set a DNS for my NIC in Network Tools window.

---

### Post by Hardi on 2005-05-29
Can anyone help please?

---

### Post by Hardi on 2005-05-29
Ok, I went to /etc/resolv.conf
It contained this text:
nameserver 192.168.1.1

Which is correct!
My xp has that DNS too!
But why doesn't my internet under Ubuntu work  :|

---

### Post by Hardi on 2005-05-29
Ok, my internet is now working :)

---

### Post by mohaham on 2005-05-29
How did you get the Internet Connection to work..
This may be helpful to other people too...

---

### Post by wbeck85 on 2005-05-30
[QUOTE=Hardi]Ok, my internet is now working :)[/QUOTE]
 HAHA! Excellent, glad to see you got it. I've been away at my computer for a while, so I missed the latter half of this thread while it was going on, or I would have tried to been of more use. But, again, glad to figured it out. Was the solution as simple as merely setting up the correct ip addresses and nameserver?

Good luck to you with everything!

---

### Post by Hardi on 2005-06-01
Heh. The tip was in going to Administration>Networking> disabling a device and enabling an another and putting my network cable into the enabled device's hole.
The point is: I have 2 NICs.
1 is integrated and 2th is from my internet's provider - Realtek.

But I can't figure out, why my provider's card didn't work - it was enabled and integrated NIC was disabled and no internet.

But no my network is running on the integrated card, so... :)

---

### Post by sadiini on 2005-06-02
Pole esimene kord, kui üks kaart teisega läbi ei saa. Vahet pole ju, milline sul signa tuppa toob :)
It`s not first time, when two pieces of iron do not get along. What difference it makes, which card does the job :)

---

### Post by Hardi on 2005-11-01
Lol, you won't believe what happened. I reinstalled ubuntu and now I have the same problem(i think it's the same) and the previous tips ain't working anymore :S
So, any other suggestions?

---

