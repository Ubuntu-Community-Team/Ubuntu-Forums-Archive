---
title: "Added ubuntu to a &quot;windows&quot; lan. can't access internet."
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by JoaoCarlosCorreia on 2007-11-06
Hi everybody,

I installed ubuntu 7.04 in my machine. Was really easy, I have internet and everything. I had a router directly connected with a cable to my machine. After installed everything I "added" my machine to an already existing network with only windows machines. I added my machine to the network with a cable. My problem now is that I can't access internet. However, I can see all other computers in the network, ping, browse in the network, everything. can't ping anything outside the lan or access any internet site. 
Does anybody now any kind on configuration I have to do in my ubuntu or in my router to make this work?

Thanks a lot,

João

---

### Post by jimod4 on 2007-11-06
I would check your dns settings. If your set to dhcp, ubuntu sometimes does not configure the dns server correctly.  ping debian.org and see if you get a reply.  then ping 192.25.206.10, which is debian.  if you get a reply from the ip address but not the name you have a dns problem.  you can use verizons dns server which is 151.197.0.39, I use it all the time.

---

### Post by JoaoCarlosCorreia on 2007-11-06
I tried your tip but wasn't that the problem.
With [www.debian.org](www.debian.org) I got the error: unknown host [www.debian.org](www.debian.org)
With the ip 192.25.206.10 returned no output for a few minutes. I stopped it with CTRL-C and returned 0 packets received, 100% packets lost or something like that (i'm in another computer since I don't have internet in that one).
MY problem is something else. 
thanks for your help anyway and will appreciate everybodys help

Joao

---

### Post by timcredible on 2007-11-06
is your linux machine using dhcp?  if not, set it to use dhcp so you can get the default gateway and dns server info.

if that's not it, then see if you're using a proxy on your windows machine (check IE network settings), and if yes, put same settings in firefox on your linux machine

---

### Post by noob12 on 2007-11-06
Check your default gateway
```

route -n

```

Look for a line with UG in the Flags column and make sure the Gateway column shows your router's IP address and the Iface column shows that it is associated with the interface that is actually connected.

If you can manage to post the output of these it would help diagnosis:

```

ifconfig -a

route -n

cat /etc/resolv.conf

```

---

### Post by jimod4 on 2007-11-06
if you type ifconfig you will see your network settings.  Maybe try hard coding an ipaddress.  also check the obvious.  is the network card enabled?

---

### Post by JoaoCarlosCorreia on 2007-11-06
Everything looks good... 
Here everybody (windows) uses firefox either.
Could be some kind of limitation of my router or something? to many accesses, I don't know...
thanks for your time,

João

---

### Post by JoaoCarlosCorreia on 2007-11-06
Here is the output of the commands you asked me to:

I'm already using a static IP.

How can I check if the network card is enabled? Propably is because I can access the LAN...

Thanks for your help
```

user@VOD:~$ route -n 
eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:19:21:ED:3D:CB  
          inet end.: 192.168.1.213  Bcast:192.168.1.255  Masc:255.255.255.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1 
          pacotes RX:1150 erros:0 descartados:0 excesso:0 quadro:0 
          Pacotes TX:567 erros:0 descartados:0 excesso:0 portadora:0 
          colisões:0 txqueuelen:1000 
          RX bytes:104600 (102.1 KiB) TX bytes:48531 (47.3 KiB) 
          IRQ:20 

lo         Encapsulamento do Link: Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1 
          pacotes RX:113 erros:0 descartados:0 excesso:0 quadro:0 
          Pacotes TX:113 erros:0 descartados:0 excesso:0 portadora:0 
          colisões:0 txqueuelen:0 
          RX bytes:8825 (8.6 KiB) TX bytes:8825 (8.6 KiB) 


user@VOD:~$ route -n 
Tabela de Roteamento IP do Kernel 
Destino         Roteador        MáscaraGen.    Opções Métrica Ref   Uso Iface 
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0 



user@VOD:~$ cat /etc/resolv.conf 
nameserver 80.251.160.3 
nameserver 80.251.160.2 
domain TVNET 
```

---

### Post by noob12 on 2007-11-06
Looks fine.  Card is seeing traffic and if you're able to access the LAN it should be fine.   If you configured the gateway manually, are you sure the router is at 192.168.1.1 and not 192.168.1.254 ? 

Are you able to ping the router?  (**ping 192.168.1.1**) 

Are you able to ping one of your configured DNS servers? (**ping 80.251.160.3**)

Another thing that might be helpful is to post the result of  running (the Windows command) **ipconfig /all** on one of your Windows hosts.

---

### Post by JoaoCarlosCorreia on 2007-11-07
I guess I solved the problem for now.
Here's what i've done, maybe could help someone else.
I read about this file /etc/network/interfaces.

I looked at that and everything looks fine.

So I tried to /etc/init.d/networking restart. Couldnt do that because there was more than one entry to eth0.  I commented the line auto eth0, made de restart and is working. The wierd thing is that now the file has a new line auto eth0 down the one I commented...

Maybe the restart solved my problem, or maybe it will still came. hope not.

Anyway thanks everybody for your tips, If the problem become i'll be back too ;-)

hugs,

João

---

### Post by JoaoCarlosCorreia on 2007-11-07
Damn!
It worked for a few hours, but now I don't have internet again.
A can't ping my gateway (192.168.1.1) nor my DNS servers (80.251.160.3).
It's really strange that I have internet for a while and then simply disappears. I had have internet a few days ago either, so it must be some kind of conflit in my router, I don't know
This is my ipconfig /all in one of the windows machines:

```
Configuração IP do Windows

        Nome do sistema anfitrião. . . . .: Escrito1
        Sufixo DNS principal. . . . . . . :
        Tipo de nó. . . . . . . . . . . . : Desconhecido
        Rota IP activado. . . . . . . . . : Não
        WINS Proxy activado . . . . . . . : Não

Adaptador ethernet Ligação de área local:

        Sufixo DNS específico da ligação. :

        Descrição . . . . . . . . . . . . : SiS 900-Based PCI Fast Ethernet Adapter
        Endereço físico . . . . . . . . . : 00-11-5B-3C-D9-06
        DHCP activado . . . . . . . . . . : Não
        Endereço IP . . . . . . . . . . . : 192.168.1.133
        Máscara de sub-rede . . . . . . . : 255.255.255.0
        Gateway predefinido . . . . . . . : 192.168.1.1
        Servidores DNS. . . . . . . . . . : 80.251.160.2
                                            80.251.160.3
```

Please give me some light if you find something.

Thanks,

João

---

### Post by noob12 on 2007-11-07
Can you post the output of **cat /etc/network/interfaces** ?

Based on the windows output,  the static setup that was shown earlier in your [Bifconfig -a[/B] output looked correct.

I notice that you have no default domain suffix in Windows; you are using TVNET on Ubuntu, which would affect name resolution but only after we've established that you have connectivity to the internet at all.  Also, the order of your nameservers is reversed, but they both seem to be up, at least they are both responding to pings from my location. 

When things fail do you see any error messages in the output of **tail /var/log/kern.log**  after you try pinging an external address?

---

### Post by JoaoCarlosCorreia on 2007-11-08
Here is the output of cat /etc/network/interfaces:

```
user@VOD:/$ cat /etc/network/interfaces

auto lo

iface lo inet loopback


iface eth0 inet static

address 192.168.1.213

netmask 255.255.255.0

gateway 192.168.1.1


#auto eth1

#iface eth1 inet dhcp


#auto eth2

#iface eth2 inet dhcp


#auto ath0

#iface ath0 inet dhcp


#auto wlan0

#iface wlan0 inet dhcp


auto eth0



```

in the kernel log there is no output, I can see that from the time ie each line.


Now I can "turn on" internet if I go to my linksys interface (192.168.1.1 in one of the windows machines) and turn of firewall and turn on again. After that I make the restart in /etc/init.d/networking restart,
With this procedure The internet start working, but sometimes go away a few minutes after,
I'm not sure if the trick is in the router firewall, or in the restart of the network or if it's all a big coincidence...
Should I config something in the router to access internet from my ubuntu?

thanks, 

João

---

### Post by noob12 on 2007-11-08
That file looks ok (I'm assuming the extra blank lines are a result of posting and not actually in your file).  

I don't have any definite idea about what is going on.  Everything looks ok on the Ubuntu host.  You shouldn't need to configure anything in the router specially.

If you have any Access Restrictions enabled on your linksys router, make sure the ubuntu host is allowed to access the internet.

Most of the linksys routers have a range for DHCP addresses and a range for static addresses below that.  For example, by default they are typically configured to distribute addresses by DHCP in the range 192.168.1.100 and above.  They expect you to use addresses below 100 for static assignments.  You might try that.  

Also you might want to make sure your router firmware is upgraded to the latest version available from linksys.

I don't have any other ideas, sorry.

---

### Post by JoaoCarlosCorreia on 2007-11-08
I have this other clue.

If I keep restarting the network with '/etc/init.d/networking restart' I have internet.
if, when I have internet, I open a terminal "pinging" to my router all the time, it never goes away.
I must be using the connection all the time. 

Isn't this wierd??!!



João

---

### Post by loaderboy on 2007-11-08
I have been having a very similar problem. I set up an ubuntu server and when I connect it to my network  it kills my internet. It is just a box and I acsess it with realvnc from one of my windows boxes. I can get to it through vnc but it knocks out my network. If I try to see it through my workgroup from XP it's not there.
  I can reboot my D-Link router and everything is fine for a few minuets but then it kills the network again.
I can't keep it on long enough to find out what it is doing before it drop kicks my router again.
 Even when the network is down realvnc still works.
I will keep an eye on this thread and hopefully when you get yours fixed I can try it on mine.

---

### Post by noob12 on 2007-11-09
JoãoCarlos:  are you by any chance running a firewall on the ubuntu host?

The output of this should tell us:
```

sudo iptables -nL

```

---

### Post by JoaoCarlosCorreia on 2008-04-16
Hei, Loaderboy, did you get any solution already?

What i'm doing is keeping it "pinging" allday to the router.
With this it don't loose the connection.

I tried IPTables -F when having problems, but diidn't work either

---

