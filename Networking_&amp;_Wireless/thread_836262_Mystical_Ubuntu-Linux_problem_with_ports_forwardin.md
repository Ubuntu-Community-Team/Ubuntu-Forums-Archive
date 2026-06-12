---
title: "Mystical Ubuntu-Linux problem with ports forwarding"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by volmark on 2008-06-21
I have installed Ubuntu server with LAMP package as a web-server. I have connected it directly to the Internet just to be sure that that it is running and can be seen on the Internet. All worked perfectly.
Then I have placed a router-ferewall Level1 unit (FBR-1418TX) between my computer and the Internet as DoS defender. 
Despite forwarding of all corresponding ports and opening DMZ tunnel I couldn&#8217;t get through the firewall-router. I could NOT open web or ftp sites or SSH connection.
When I&#8217;ve connected another computer with Windows XP with some servers running on (HTTP-80, FTP-21, Smtp) instead of Ubuntu machine, I could easily open HTTP-80 and FTP-21 but not SSH. (There is something always wrong with SSH and firewall-router :o(
I wonder what the difference between Linux and Windows IP-protocol processing is. Why Web and FTP servers can be seen through the firewall if they running on Windows platform and vise versa if they running on Linux-Ubuntu???

PS I&#8217;ve also tried ZyWALL 10 firewall-router with the same results

Very strange problem &#8230;

---

### Post by volmark on 2008-06-21
Are there no ideas??
I’m going to move my production sites to this host but I cannot do it without protection against DoS

---

### Post by SpaceTeddy on 2008-06-21
mhm... strange.
can you please draw a picture of your network (as simple as possible), give me the internal addresses of the firewall and server as wenn as the output of the following commands on the server:

```
ifconfig
route -n
iptables -L -vnx
```

also, does the server answer internally on any requests, or is it denying those aswell ?

hope we can figure this out :)

---

### Post by volmark on 2008-06-21
The server is responding both internally and externally as it should. As soon as I placing firewall-router between the server and external network the problems begin. 
The most confusing is that the same standard services runnig fine on Windows platform also through firewall.

Here is the output sample and come configuration files


DELETED FOR SECURITY REASONS

---

### Post by volmark on 2008-06-21
By the way SSH has newer worked through firewall despite I tested it on both Windows and Linux and used diffrent ports

---

### Post by volmark on 2008-06-22
This is a message posted privately by SpaceTeddy. I&#8217;m posting it just for keeping logical thread and he was going to post it self anyway.

[I]Originally Posted by volmark 
Thanks for your help 
In connection with my post &#8220;Mystical Ubuntu-Linux problem with ports forwarding&#8221; I have created test user on the server. You can try to login and look around
[/I]
thanks for the trust !

anyway, i won't be able to make it until later today, as i am supposed to be in a workshop until 19:00 (GMT).
I'll definetly check it out tonight tho. 

One quick notice when i read over your post - you seem to have multiple default gateways set. Make soure you only have one, and make sure it is the correct one. Even if you have multiple (virtual) network cards, you can only have ONE default gateway.

i'll also post this in the thread later on, but don't have the time now. 

cheers

---

### Post by volmark on 2008-06-22
Yes, I have multiple gateways because in the test faze I need to move from one IP range to another. The host machine is placed in basement and it is a pure Linux box without display and keyboard. It can only be managed through remote terminal. 
When I’m connecting the machine through firewall-router it should be placed on private address range (192.168.111.222, gateway 192.168.111.111) and when I’m going to test direct connection it should be placed on public address range (85.218.184.8, gateway 85.218.184.1)
If I disable the public IP configuration hiding the host behind the firewall on private address range and it’s going wrong I will need to bear the machine on my neck 3 floors up for fixing the problem. 
I can see the point with multiple gateways and I’m ready to sacrifice my laziness for the holy Linux matter that’s why I’m taking deep breath and commenting some gateways. 
God, help me …

---

### Post by volmark on 2008-06-22
I’ve commented out some gateways and left only one – 192.168.111.111 (router private address). Unfortunately no visible results were happened. I can easily ping (192.168.111.222) the host from LAN interface of the router but still cannot open default web page or connect with FTP or SSH.:(

---

### Post by SpaceTeddy on 2008-06-22
alright... now i am confused.

i've just looked over the configuration of the linksys router - it seems perfectly fine !

Then (out of desperation) i tried sshing the box - and got an answer. So i used the username and password for the linux box you supplied... And i could log in ! I've create a file called [COLOR="DarkRed"]dummy[/COLOR] in the test users home dir for you to verify that i was on the right server. 

But for me, the apache as well as the ssh server respond ! The FTP does not work because the firewall does not seem to support passive FTP pass through, and active FTP requires port 20 and port 21. 

I have connected to your given address, using standard ports and it worked. So i am a little confused here.

Mhm - just had an idea. Did you try to connect from inside your lan, or from the internet ? cos if you tried to connect from the inside, the linksys box will NOT forward you - it will only do this for requests that genuinely come from the internet... 

i am mainly confused right now...

---

### Post by volmark on 2008-06-22
I’m very confused too… 
I establish connection from my home network through the home router with public address on the same range as Level1 router. My home router public address is 85.218.185.105 and Level1 router has 85.218.184.8 (the same provider) and my home network is totally disconnected by home firewall from outside networks.
I still cannot get connected to the Linux host at any protocol from my home network but you can from you’re the outside!!!
The strangest thing is that I can open at least HTTP-80 server if it’s running on Windows platform.
Now I’m going to basement to switch connection and then I should look at your “dummy” file. You will hear shortly from me …

---

### Post by volmark on 2008-06-22
Wow &#8230; wow&#8230;. 
&#8220;access works fine for me...&#8221; - it&#8217;s content of your dummy file. Something totally wrong &#8230; I suspect my provider. I think it&#8217;s very odd and chaotic network configuration they have created. Could be other reasons for this strange behavior???

---

### Post by SpaceTeddy on 2008-06-22
i have no idea now... i am as confused as you are - really. 
Let me think and sleep over this - maybe i can think of some ideas with some time... 

[EDIT]

since this network setup does not make any sense at all to me at the moment, let's rethink what the facts are (while i watch the last 10 minutes of italy vs. spain)
If i connect the linux box directly - the access works.
If you connect the linksys firewall and forward the ports:
 - the access works for me
 - the access does NOT for you

So far, so good. 
Now, let's ask ourselves some question... 
Can this be related to a configuration error ? - Unknown, but unlikely on your side ... 

If there was a smiley for a lightbulb - now would be place to use it. Let me quickly check something... 

[COLOR="Red"][SIZE="6"]i got it[/SIZE][/COLOR][SIZE="1"]i think[/SIZE]

the subnet size of your internal network ist 255.255.252.0. This means, if you connect from the outside network (your home), the Linux machine will try to send the paket back via broadcast on the local subnet. Since it does NOT direct it back to the gateway, you can reach the linux box, but CANNOT sent the replies back.
The reason it works with windows is that windows usually ignores a subnet like this one and changed it to 255.255.255.0 - this would explain why windows works and linux does not. 

Change the subnet of your Linux box to 255.255.255.0 on eth0 and see what happens... 

This also explains why it works for me and not for you. You are in those 512 addresses that do not work... the rest of the internet works just fine... 

i really think this is it...

---

### Post by volmark on 2008-06-22
Tried ... Nothing changed :o(  Going to bad and crying :O(

---

### Post by SpaceTeddy on 2008-06-22
so you did not - i am still logged in on your linux box, and the subnet is still 255.255.252.0.
i can see it !!!

> test@venturetour:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.111.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
85.218.184.0    0.0.0.0         **255.255.252.0**   U     0      0        0 eth0
0.0.0.0         192.168.111.111 0.0.0.0         UG    100    0        0 eth0


you must change this in your /etc/network/interfaces

> test@venturetour:~$ cat /etc/network/interfaces
[snip]
# Fixed Internet address
auto eth0
iface eth0 inet static
address 85.218.184.8
**netmask 255.255.25[COLOR="Red"][SIZE="5"]5[/SIZE][/COLOR].0**
network 85.218.184.0
broadcast 85.218.184.255
[snip]

and reload the network config or restart the machine.

or am i on a logged in on a different machine ?

---

### Post by volmark on 2008-06-22
I have changed firewall mask instead. May be it was wrong &#8230;
But now I&#8217;m completely confused. The host is sitting behind firewall using private address range. Router = 192.168.111.111 and host = 192.168.111.222. The both must be on the same network (192.168.111.0).
The public address of the host 85.218.184.8 should not be seen at all from the outside of router because the communication between router and host take place on the internal part of the network (LAN 192.168.111.0) and public address 85.218.184.8 on the host doesn&#8217;t play any role because it is public address for the firewall now. My home network completely disconnected by own router-firewall from the other networks and Linux host. 
Tomorrow I&#8217;ll try to change it and see what happens.

---

### Post by volmark on 2008-06-23
I have changed the mask to 255.255.255.0 and lost connection completely :(
It is responding only on HTTP:80
Now I have a trouble because I need to carry the computer up to 3. floor because there is no system consol in basement and I&#8217;m no able to change configuration back :(
I&#8217;m going to do it tonight &#8230;

---

### Post by SpaceTeddy on 2008-06-23
Ok, i think i need to explain myself here. Sorry for the confusion. I really did a bad job on explaining what happened... Sorry again.

First, this is how i understand your network setup

Your computer
(eth0 - some IP)
|
(en0 - some IP)
Linksys@home
(ppp0 - 85.218.185.105)
|
Internet
|
(ppp0 - 85.218.184.8)
Linksys firewall
(en0 - 192.168.111.111)
|
(eth0 - 192.168.111.222)
Linux box.

This is your setup as i see it, or as i understood it. Now, what i am talking about is in my last post. On your Linux box, you have a route set that classies the network 85.218.184.0/22 to be on the local subnet - i.e. attached to eth0) that is the bold line in my last post. 

Now, what happens when you send a paket from your home computer to the server ? The paket will have the source address of your paket will be rewritten to 85.218.185.105, go through the internet, reach the linksys and is forwarded to the linux box. There the paket is processed and a reply is generated. But because of the rule that the 85.218.184.0/22 network is attached to eth0 the paket is NOT sent towards the default gateway, but instead the kernel tries to find you (85.218.185.105) on the local subnet. As you are not there, this will NOT happen. 

Acctually, i was wrong entirely last night (too tired, too excited and the soccer game did not help either) - that route on the linux box should not be there. As soon as that is gone, the replies will flow normal back to the default gateway. 

Does this make more sense now ?

Sorry again for the confusion... i sometimes get carried away when my brain starts fireing ideas...

---

### Post by volmark on 2008-06-23
Dear ST
I&#8217;ve just come home and tried to connect through the router. It was big surprise but I could connect to the host (behind the router) through all the ports &#8230; Hurra, hurraaaa &#8230;
Now I should carefully reread your posts to find out why it could happened.
It was really great help &#8230; My full respect to your competence &#8230; May be I&#8217;ll send some questions after rereading of your posts.
Thanks a lot &#8230;
I would like ask you for a favor. Could you please to test the connection again just to be sure that it is still reliable connection from the outer world.

---

### Post by SpaceTeddy on 2008-06-23
Access works for me. I've created a second file called SecondLogin in the test account. I'll also try to send you a screenshot with the details of what i did through pm.

And also i am glad that it works now :)

---

### Post by volmark on 2008-06-23
Yes, I&#8217;m impressed. All works fine now&#8230; both inside and outside &#8230;
It&#8217;s my first serious experience with Linux-Ubuntu and I&#8217;m very impressed by the collaboration between people. 
You are going to expect some additional questions about this case :)

---

### Post by volmark on 2008-06-23
Now CAN connect FTP with passive mode on. Is there possibility to switch FTP modes??

---

