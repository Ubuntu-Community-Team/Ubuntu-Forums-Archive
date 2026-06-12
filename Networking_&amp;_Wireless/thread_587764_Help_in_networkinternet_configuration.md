---
title: "Help in network/internet configuration"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by damyhonn on 2007-10-23
I'm almost desperate.
I have no idea how to fix it.
I've just installed Gutsy in a dual boot with Vista. I have an ADSL connection with a modem D-link 500G being a router. My connection is configured without DHCP like that:
I choose an ip address 10.1.1.X, mask: 255.255.255.0, gateway: 10.1.1.1, DNS: xxx.xxx.xx.xxx/xxx.xxx.x.xx.
In windows vista it works perfectly. But in Gutsy I don't have internet. But I can ping to any domain.
I think it's a DNS problem, but the DNS domains are correct, even because they work in Windows.
see that:
[[IMG]http://img134.imageshack.us/img134/8148/capturadatela2ms1.th.png[/img]](http://img134.imageshack.us/my.php?image=capturadatela2ms1.png)

if I type any address in firefox it doesn't connect.

Thanks for any help.
I don't want to use only Windows Vista Millenium II :(

---

### Post by dagowop on 2007-10-23
It shouldn't be a dns issue if you ping a domain and your computer resolves the address.  If you want to be sure it's not a dns issue ping a domain, copy the resolved ip address and paste it into a browser.  If the site opens and navigates without a problem then maybe I was wrong.  But I don't think so.

Quick Fix:  Buy a router.
                         or
                    Try Opera or any other browser for that matter

---

### Post by damyhonn on 2007-10-23
Thanks for help.
I tried to paste the address into firefox but without success.
And about your suggestions, I can't understand how I would have to buy another router if it's working nice with windows :( and I'll download Opera to see if it works.
But the big problem is that I don't want to navigate only, I want Synaptic and wget (for example) working too. And now they aren't.
But thank you very much for help.
And anyone who have another solutions, thanks too.

---

### Post by mve-lamb on 2007-10-23
Hi, you said:
> I choose an ip address 10.1.1.X, mask: 255.255.255.0, gateway: 10.1.1.1, DNS: xxx.xxx.xx.xxx/xxx.xxx.x.xx.

try instead first DNS xxx.xxx.xx.xxx to use DNS 10.1.1.1,always press "ENTER" when finish with editing/adding new DNS, and when you make any changes to Network Manager, close it, and after that go and double check that the settings are there...try to reboot Ubuntu, and come back to report what's up?
Do you have any firewall installed like firestarter or etc. don't you?

paste the output from fallowing commands: ifconfig , route -n, iptables -L 

lamb

---

### Post by damyhonn on 2007-10-24
Hi mve-lamb, and thanks for help.

I tried what you said (to put DNS as 10.1.1.1) but, unfortunately it doesn't works. :(
And here are the outputs of the commands you ask:

```
damyhonn@DAMYHONN-PC:~$ ifconfig
eth0       Encapsulamento do Link: Ethernet  Endereço de HW FF:FF:FF:FF:FF:FF  
          inet end.: 10.1.1.9  Bcast:10.1.1.255  Masc:255.255.255.0
          endereço inet6: fe80::fdff:ffff:feff:ffff/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:138 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:101 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:11700 (11.4 KB) TX bytes:9194 (8.9 KB)
          IRQ:19 Endereço de E/S:0xd400 

lo         Encapsulamento do Link: Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

damyhonn@DAMYHONN-PC:~$ 

```

```
damyhonn@DAMYHONN-PC:~$ route -n
Tabela de Roteamento IP do Kernel
Destino         Roteador        MáscaraGen.    Opções Métrica Ref   Uso Iface
10.1.1.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.1.1.1        0.0.0.0         UG    100    0        0 eth0
damyhonn@DAMYHONN-PC:~$ 

```

```
damyhonn@DAMYHONN-PC:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
damyhonn@DAMYHONN-PC:~$ 

```

Thanks for any help.

---

### Post by mve-lamb on 2007-10-24
Hi, everything looks like normal except this:
```
damyhonn@DAMYHONN-PC:~$ ifconfig
eth0       Encapsulamento do Link: Ethernet  Endereço de HW FF:FF:FF:FF:FF:FF  
```
but I assume that you change this HW to FFFFFF......  to hide your real MAC, isn't it?

If thats the case, i have no idea what can be the problem...:mad:

Lamb

---

### Post by damyhonn on 2007-10-24
Hi mve-lamb,

I don't know why the real MAC is hide.
In a few months ago I've used the program AMAC in Windows to change my MAC. But I've formatted my pc so many times from there. I thought its change was just virtual. Maybe it has damaged my network card.
Do you think if I try to put another network card in my pc it will work?
I guess I'll try it.

Thank you.

---

### Post by damyhonn on 2007-10-24
Hi mve-lamb,

I don't know why the real MAC is hide.
In a few months ago I've used the program AMAC in Windows to change my MAC. But I've formatted my pc so many times from there. I thought its change was just virtual. Maybe it has damaged my network card.
Do you think if I try to put another network card in my pc it will work?
I guess I'll try it.

Thank you.

---

### Post by damyhonn on 2007-10-25
Hi,

Trying and trying again I found a solution for this case.
Looking for mve-lamb advice where he said the MAC of my card was weird I tried to change it with these commands:
```
$ifconfig eth0 down
$ifconfig eth0 hw ether 00:D0:3F:67:2C:05
$ifconfig eth0 up
```

so after that I did all configurations again (ip, mask, gateway, dns) and WALAA my connection is up. :guitar:
I don't know why but now it's all fine. And I don't know if I would have to change card's MAC everytime I log on Ubuntu. And due to all this time trying I don't want to test if it will work after boot. heheheh
So thank you so much mve-lamb and dagowop.
Any news I'll post here.

---

### Post by mve-lamb on 2007-10-25
Happy to hear that you made it!

This is wire problem :confused: , but curious what will be the situation after reboot? 

there is program in Ubuntu for change MAC adderss -> sudo apt-get install macchanger , serch forum for more detailed help.

After restart, if you lose your MAC again you can try to put in /etc/network/interfaces
> sudo gedit /etc/network/interfaces
I don't know for sure which of two types will work for you-I think 1st one:

> auto eth0
iface eth0 inet static
       hwaddress ether 01:02:03:04:05:06
       address 192.168.0.8
       netmask 255.255.255.0
       network 192.168.0.0
       broadcast 192.168.0.255

> 
auto eth0
iface eth0 inet static
        pre-up ifconfig eth0 hw ether XX:XX:XX:XX:XX:XX
        address 192.168.0.8
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255


You need to restart network -> sudo /etc/init.d/networking restart

I don't think, that you damage your network card with changing MAC address under windows, but you never know?I did it myself twice or more times, and still everything is working...

Lamb

---

### Post by damyhonn on 2007-10-25
Oh thank you so much again mve-lamb ..
I did what you said, booted my system and now it's everything ok.
That's the big advantage in being part of linux community. Everyone is like each other's brother. I would like to have more time and experience to help so many new users.

Cheers.

---

### Post by mve-lamb on 2007-10-26
[COLOR="RoyalBlue"]Therefore all things whatever you would that men should do to you, do you even so to them: for this is the law and the prophets. Matthew 7:12 [/COLOR]

Nice to hear that things are going OK with you! You are Welcome!

Lamb:lolflag:

---

