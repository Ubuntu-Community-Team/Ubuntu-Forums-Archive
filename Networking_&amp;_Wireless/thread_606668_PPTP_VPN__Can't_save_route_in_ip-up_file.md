---
title: "PPTP VPN : Can't save route in ip-up file"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by TheH on 2007-11-08
I setup a VPN connection to my work using the buildin VPN connector in the top corner of ubuntu 7.10

It contacts properly and after adding the line:

sudo route add -net 10.0.0.0 netmask 255.0.0.0 dev ppp0

I have a fully working vpn , but on reboot it does not remember these settings.

I tried adding them to the /etc/ppp/ip-up file as

/sbin/route add -net 10.0.0.0 netmask 255.0.0.0 dev ppp0

But this doesn't work , also i am not sure on how a normal user can do this automatic without having to use the sudo command (which req. the password)

I think i need to configure it in a other file since i am using the build-in ubuntu vpn connector.

Any help ??

---

### Post by benhall on 2007-11-08
To start to answer your question, you need to let me know a couple of things. Have you installed the available VPN packages in the Add/Remove programs dialogue? If not try installing the one that sounds most appropriate (probably the "PPP Generic" plugin). Configure as described below. Also, is there a reason why you are using the terminal?

If you have installed this, you can set it up without the command line by clicking the icon of 2 computers in the upper right hand corner of the screen. There should now be a "VPN connections" line in the drop down menu which appears. Click this, then configure/edit. In the new dialogue click "Add" and enter your details.

---

### Post by TheH on 2007-11-08
> **benhall said:**
> To start to answer your question, you need to let me know a couple of things. Have you installed the available VPN packages in the Add/Remove programs dialogue? If not try installing the one that sounds most appropriate (probably the "PPP Generic" plugin). Configure as described below. Also, is there a reason why you are using the terminal?

If you have installed this, you can set it up without the command line by clicking the icon of 2 computers in the upper right hand corner of the screen. There should now be a "VPN connections" line in the drop down menu which appears. Click this, then configure/edit. In the new dialogue click "Add" and enter your details.

Hi , 

Yes i am using that one with the two computers

---

### Post by benhall on 2007-11-08
If you click on the icon, do you get the "VPN connections" option in the drop down menu?

(For future reference, this program is Network Manager)

---

### Post by TheH on 2007-11-08
Yes i do , 

I press the two computers and get the following options:

* Wired Network
* VPN Connections > MyworkVPN
                            > Configure VPN
*Manual configuration

---

### Post by benhall on 2007-11-08
Does it not connect when you click on MyworkVPN? It might ask you for a username & password, but you can tell it to remember if for the future.

---

### Post by TheH on 2007-11-10
> **benhall said:**
> Does it not connect when you click on MyworkVPN? It might ask you for a username & password, but you can tell it to remember if for the future.



Let me guess, your getting beans for ever reply you make ? cause the 4 last replies you did   made no sense at ALL !


I setup a VPN connection to my work using the buildin VPN connector in the top corner of ubuntu 7.10

It CONNECTS properly (So VPN WORKS ) and after adding the line:

sudo route add -net 10.0.0.0 netmask 255.0.0.0 dev ppp0

I have a fully working vpn(Another indication that this works !) , 

But on reboot it does not remember these settings. (Does not remember the Rout ADD )

I tried adding them to the /etc/ppp/ip-up file as

/sbin/route add -net 10.0.0.0 netmask 255.0.0.0 dev ppp0

But this doesn't work , also i am not sure on how a normal user can do this automatic without having to use the sudo command (which req. the password)

I think i need to configure it in a other file since i am using the build-in ubuntu vpn connector.

Any help ??



Anyway i doubt that you can help me in anyway and your just trying to get "points" by asking stupid questions so ill take my problem some where else

---

### Post by benhall on 2007-11-15
I'm sorry that you've not found my input helpful. I'm just trying to ascertain why you are editing the route table at all- I've been connecting to VPNs using just the commands I described above since Ubuntu 6.10 (that is, NM->VPN Connections->Connect). If you are determined to run the route command every time on boot you could add a service to do this; it is described in more depth here

[http://ubuntuforums.org/showthread.php?t=533613](http://ubuntuforums.org/showthread.php?t=533613)

However, I have never had to edit the route table to connect to a VPN before, so I wouldn't recommend it unless you were sure it was necessary and comfortable with the commands.

---

### Post by webdr on 2007-11-15
Just a heads up, from what I have seen pptpconfig vpn connections always
have extraordinarily high packet loss rates. I've not located an adequate vpn solution for my beloved linux just yet.

---

