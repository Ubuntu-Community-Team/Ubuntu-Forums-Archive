---
title: "Pptp Vpn In Edgy"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by matthinckley on 2006-10-28
Yes It Works! Just so everyone knows.. I have been fighting with getting pptp to work on my laptop running edgy for almost two weeks now.. 

tried the pptpconfig gui interface to no avail.. and found a thread about a network-maanager-pptp package out on the internet.. found it.. downloaded it.. had to run apt-get install -f and it upgraded out of the edgy repositories.. 

all that needs done is a 'sudo apt-get install network-manager-pptp' then restart NetworkManager and nm-applet. (or you could do a reboot) and there is a new menu in the NetworkManager to configure VPN.. go through the wizard and save it.. then in the NetworkManager there is a new option with the name you gave your vpn connection.. click it and you should connect.

Works like a charm for me.

~Matt

---

### Post by spiderworm on 2006-11-01
after installing that package and rebooting im seeing no noticeable change.  can you please provide detailed instructions of where the pptp option can be found?

thanks.
spiderworm

---

### Post by mattskr on 2006-11-01
> **spiderworm said:**
> after installing that package and rebooting im seeing no noticeable change.  can you please provide detailed instructions of where the pptp option can be found?

thanks.
spiderworm

Log in and log back out and it should show up. I actually had to fully restart mine.

---

### Post by kungfoofool on 2006-11-02
I wrote a quick & dirty tutorial on this here:

[http://www.dailytechnology.net/how_to_setup_vpn_in_ubunty_edgy_eft.php](http://www.dailytechnology.net/how_to_setup_vpn_in_ubunty_edgy_eft.php)

---

### Post by quadrant2 on 2006-11-02
Does this solution also apply to Kubuntu.  I am having the same pptpconfig problem since upgrade to edgy: Cannot determine ethernet address for proxy ARP.

Thanks

Ben

---

### Post by cjnucette on 2006-11-10
thanks, it worked like a charm

---

### Post by lepoete73 on 2006-11-10
> **matthinckley said:**
> Yes It Works! Just so everyone knows.. I have been fighting with getting pptp to work on my laptop running edgy for almost two weeks now.. 

tried the pptpconfig gui interface to no avail.. and found a thread about a network-maanager-pptp package out on the internet.. found it.. downloaded it.. had to run apt-get install -f and it upgraded out of the edgy repositories.. 

all that needs done is a 'sudo apt-get install network-manager-pptp' then restart NetworkManager and nm-applet. (or you could do a reboot) and there is a new menu in the NetworkManager to configure VPN.. go through the wizard and save it.. then in the NetworkManager there is a new option with the name you gave your vpn connection.. click it and you should connect.

Works like a charm for me.

~Matt


Wish it could work for me...  Network-Manager doesn't support my network card.  I've got a wireless ra chipset.

---

### Post by TorenC on 2006-11-12
> **quadrant2 said:**
> Does this solution also apply to Kubuntu.

I second this question. If I try to install network-manager-pptp, it wants to install gobs of gnome libraries. There doesn't seem to be an equivalent knetwork-manager package.

---

### Post by BrendanM on 2006-11-25
I also have the rt61 card, does anyone have a solution that fixes PPTPconfig?

---

### Post by wglenncamp on 2006-11-28
I installed per the directions and I do have the applet running in my toolbar.  I was able to click on the connection and configure my VPN, but I don't see how I can init the VPN connection.  What am I missing?

---

### Post by mishranurag on 2007-02-21
Hi,
I did install knetworkmanager and also configured VPN. The network manager however shows that it is disconnected. When I connect to wireless through the network manager, it stops at 28%(Configuring network manager). 
The option for VPN also stays greyed.
What am I doing wrong?

---

### Post by mishranurag on 2007-02-23
Any answers yet?

---

