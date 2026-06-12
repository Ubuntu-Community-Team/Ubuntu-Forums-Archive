---
title: "OpenVPN help..."
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by pzhukke on 2008-05-16
Yo!

I've been trying to get my OpenVPN to run smoothly, and it almost does, here's my situation/problem:

I'm trying to redirect my gateway so I can access internet and do some webbrowsing and so via my VPN, but it doesn't work!

The HOWTO guide says that I should add this to my server.conf file:
```
push "redirect-gateway def1"
```
And then, I need to NAT my server to internet, to handle the packages, and then they gave me this example:
```
iptables -t nat -A POSTROUTING -s 10.8.0.0 -o eth0 -j MASQUERADE
```
Where my subnet (set in the server.conf) is 10.8.0.0 ...
And that shall be it, according to them.

But when I start the server, without any errors, connect the client and try to access internet, nothing happend and it just hangs, but something is happening in my server log:
```
client1/192.168.0.197:3587 MULTI: bad source address from client [192.168.0.197], packet dropped
```
Okey?

By my researches, I found out that this means that the server doesn't know where to route the packages I'm sending to him, so he just drop them.
So my question is:
_How to I solve this f*cking problem that has been hurting my eyes and brain for like 4 hours now?_


I think this is a very common problem, even tho I havn't found any proper solution for it... :/

I'm using the Sample Server Configuration that is available on [**the HOWTO page**]("http://openvpn.net/index.php/documentation/howto.html#server") if you want to take a look at it.
And I've installed OpenVPN via the Ubuntu Responsories (or whatever the name is?).

P.S. Sorry for bad English, I'm a Swedish geek :) D.S.

---

### Post by SpaceTeddy on 2008-05-16
1.) try adding the float option to your client.

2.) try to use the redirect-gateway on the client side and remove it from the server to see if it works then.

3.) make sure your server has internet connection. Also make sure that ip_forwarding is enabled on your server. Furthermore check if your servers even allows the forwarding of pakets (check your iptables).
you can check the iptables with
```
sudo iptables -L FORWARD 
```

no more ideas from me for now :) tell me how it goes :)

PS:  i only push "redirect-gateway" with no def1. Never seen the def1 anywhere. And i know it works (been using it on more than one server)

---

### Post by pzhukke on 2008-05-16
Okey thanks man, here's what I've got:

1) How do I enable that?

2) I added push "redirect-gateway def1" and without def1 aswell, didn't work.

3) Ofc it's got internet ;)
And to enable ip_forwarding, what is the command for that?
I've tried this:
_sudo echo 1 > /proc/sys/net/ipv4/ip_forward_
But it only gives me the error:
**bash: /proc/sys/net/ipv4/ip_forward: Permission denied**

And it doesn't seems like my Iptables is correct, this is what the command gives me:
```
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
```

It doesn't looks allright, does it?
So I guess the problem might be that the NATing (Forwarding?) is wrong?

Thanks.

---

### Post by SpaceTeddy on 2008-05-16
1.) just open the client config and type "float" in a new line :) that's all
2.) remove the push "redirect-gateway" from the server completely. Then restart it, add the line "redirect-gateway" to the client and connect it. Does it work then ?

3.) your iptables looks fine. That Output just means that everything is passing through your computer. The NAT is not shown in that output. To see the nat, use this command:
```
sudo iptables -L --table nat
```

the Command you have for enableing ip_forwarding cannot work in the way you specified it. Also, afaik it is depricated. use this one instead:
```
sudo sysctl -w net.ipv4.ip_forward=1
```

if you want to stick with your command, use it this way
```
sudo "echo 1 > /proc/sys/net/ipv4/ip_foward"
```

cheers :)

---

### Post by pzhukke on 2008-05-16
Okey here we go:

1) Didn't make any difference :P

2) Didn't do a thing either.. :/

3) My NAT table looks like this:
```
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  0   --  10.8.0.0              anywhere
MASQUERADE  0   --  10.8.0.0/24           anywhere
```

And after I entered your fancy ip_forward command, things is starting to happening :D
**Now!!**
Internet is finally working!!
But, how can I be sure that the internet is going via my VPN, and not via my regular Local Area Connection?

Also,the server is still pushing the error "bad source bla bla..."
Do you know how to solve that? :P

---

### Post by SpaceTeddy on 2008-05-16
the change you made with the sysctl command is NOT permanent. To make it permanent (so it stays on after reboot) you will need to edit the /etc/sysctl.conf and enable ip_forwarding there.

As for the error. I think that one is caused when the server receives pakets from the client through the vpn tunnel which do not originate from the client that is registered. 

Example: you have two network cards on your Computer. The tun device is the third and is connected to your computer. Since the real connection to the vpn is not on the tun, but on one of the real network cards, the server is expecting all pakets to be originated from either the real network card or the vpn IP. 
If now, for some reason a paket is send with the IP of the second network card, it will go through the tunnel, but the server does not know the source ip and thus will complain about an unknown source address.

There are three ways to fix this:
1.) create a client config and add the network via an iroute to the client. This is probably overkill for your setup and is not practical (i have never done this either, so i cannot tell you what to do. I only read this when i did a quick search on the net)

2.) use an iptables rule ON THE CLIENT to make sure that all pakets send by the client originate from the proper ip.

3.) ignore the errors  - they don't really hurt :) 

and now i wish you a good night :)

---

### Post by pzhukke on 2008-05-17
Oh, thanks.. AGAIN! :P

Here is what I tried:

**1)** Well yes, I've read about it too, but I don't really understand how the iroute command should look like, but if I have it this way:
*iroute 192.168.0.0/24 255.255.255.0*
The server doesn't give me any errors anymore, which I enjoy :)
But, I don't really know if I should have my 192.168.0.0./24 subnet, since that subnet is from the computer Im connecting from.
Look; Imagine if some friend to me connects to it, and in his router, his ip is 192.168.1.33, then to avoid the errors, I need to have the 192.168.1.0/24 subnet in my ccd file.. right?

This doesn't look right to me, 'cause if I have it this way, I have to know the subnet from the connector and add it to the ccd file to avoid the errors, shouldn't it be a better way to use the iroute command, I mean to use the VPN's subnet or something?
[B]
2)[/B] Ok well this could be a solution, but at the moment, I'm using a Windows (yes I know :/) client to connect to the server, and Windows doesn't have any iptables command built in it, at least what I know?

**3)** Oh yes, this would be a alternative solution :P
But I don't really like it, since my serverlog and terminal window are being spammed to death.
Im sure it doesn't hurt as u say, but it would be cool if I could figure out how to solve this problem properly instead :P


EDIT:
I've read on this page: [http://timhatch.com/ark/2006/06/28/pesky-openvpn-issue-solved]("http://timhatch.com/ark/2006/06/28/pesky-openvpn-issue-solved"),
that you could type *sudo ifconfig tun0 metric -1* and that would solve the problem.
Then I tried it, and it gave me this error:
**SIOCSIFMETRIC: No such device**
So I figured out that that was because the server was downm so I strarted it but hten I got this error instead:
**SIOCSIFMETRIC: Operation not supported**
Hm...
Do you (or anyone else?) know something about this?

---

