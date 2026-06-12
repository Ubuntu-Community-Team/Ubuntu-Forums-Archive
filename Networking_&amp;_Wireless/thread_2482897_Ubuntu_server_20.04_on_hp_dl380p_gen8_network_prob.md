---
title: "Ubuntu server 20.04 on hp dl380p gen8 network problem"
date: 2023-01-13
forum: Networking &amp; Wireless
---

### Post by kingslavcho on 2023-01-13
Hello friends, i wanted to ask you how can i fix my network so i can get internet on my hp dl380p gen8 server where i have installed ubuntu server 20.04?
The server has 4 lan ports and i have just inserted cable into the first port and tried to configure the network in the 00-installer-config.yaml file located in the /etc/netplan location but i still do not have internet on the server.. In the pictures you can see the configuration in the file and also that there is an ip on the server assigned manually without DHCP..

Can you please help me so i can set up the network properly on my server..

Thank you


[IMG][[IMG]https://i.postimg.cc/PP8x1vcq/ip-link-show.jpg[/IMG]]("https://postimg.cc/PP8x1vcq")[/IMG]

[IMG][[IMG]https://i.postimg.cc/xJxC3vnX/config-file.jpg[/IMG]]("https://postimg.cc/xJxC3vnX")[/IMG]

[IMG][[IMG]https://i.postimg.cc/SjPRXfg5/ip-addr.jpg[/IMG]]("https://postimg.cc/SjPRXfg5")[/IMG]

[IMG][[IMG]https://i.postimg.cc/vDTDHNtf/pinging-google.jpg[/IMG]]("https://postimg.cc/vDTDHNtf")[/IMG]

---

### Post by chili555 on 2023-01-13
Your netplan file fails to declare DNS nameservers. Please see /usr/share/doc/netplan/examples for a collection of templates.

---

### Post by kingslavcho on 2023-01-13
> **chili555 said:**
> Your netplan file fails to declare DNS nameservers. Please see /usr/share/doc/netplan/examples for a collection of templates.

I do not understand what should i do there?! Can you explain me. Thank you

---

### Post by chili555 on 2023-01-14
Please run:```
cat /usr/share/doc/netplan/examples/static.yaml
```There you will see a template for your yaml file. You will also see that it differs from yours in a few respects. Open another terminal and edit your file to comply with the example:```
sudo nano /etc/netplan/00-installer-config.yaml
```After making changes, save (Ctrl+o followed by Enter) and exit (Ctrl+x). Netplan is very specific about indentation, spacing, etc. so proofread carefully twice.

Follow with:
```
sudo netplan generate
sudo netplan apply
```I'm sorry that I can't give you the exact recipe. I haven't any 20.04 version to examine and netplan changed subtly from one Ubuntu version to the next.

---

### Post by kingslavcho on 2023-01-14
i checked it and it differs from the static.yaml.. I made it like i  think i have to make it but i still don't have internet connection and  says that i have problems with the name resolution..

Here are the  previously configured yaml, the example and the new configured file..  Please tell me what should i do in order to fix it.. Thank you

static example:

[IMG][[IMG]https://i.postimg.cc/YvgTGNPY/static-example.jpg[/IMG]]("https://postimg.cc/YvgTGNPY")[/IMG]

my old configuration:

[IMG][[IMG]https://i.postimg.cc/ZCX15swJ/old-config.jpg[/IMG]]("https://postimg.cc/ZCX15swJ")[/IMG]

my new config according to the example:

[IMG][[IMG]https://i.postimg.cc/3WSsPxp4/new-config.jpg[/IMG]]("https://postimg.cc/3WSsPxp4")[/IMG]

I  have also question about the configuration: What is the meaning of  "search" and routes? I guess the search is the router address and the  routes that my network has to use is the gateway address am i right? I  just have to tell you that i do not have a separate dns server..

---

### Post by chili555 on 2023-01-14
You can safely omit the search line. The spacing and indentation is way, waaay off compared to the example. Please correct it. Follow with:

```
sudo netplan generate
sudo netplan apply.
```

---

### Post by kingslavcho on 2023-01-15
ok i made configuration in the yaml file and it was all good (just to  notice i did not follow the example because i got various of errors with  the netplan generate like to and via ip addresses must be filled, than i  tried to delete the "-" sign and said that the error was there etc..)  with the netplan generate and apply but i still get the same error.. I  also read that i the nameservers are not good and that i had to  configure them in the /etc/resolv.conf file.. But when i change the  nameserver address to 8.8.8.8 there and than restart the  systemd-resolved.service i get the previous default ip address there -  127.0.0.53..

Just to see what i have done:

yaml file:

[IMG][[IMG]https://i.postimg.cc/n9fPB136/yaml-file.jpg[/IMG]]("https://postimg.cc/n9fPB136")[/IMG]

the resolv.conf file:

[IMG][[IMG]https://i.postimg.cc/CnC6Nftd/resolv-conf.jpg[/IMG]]("https://postimg.cc/CnC6Nftd")[/IMG]

ip addr show:

[IMG][[IMG]https://i.postimg.cc/PLccrHYf/ip-addr-show.jpg[/IMG]]("https://postimg.cc/PLccrHYf")[/IMG]

Should  i even touch the resolv.conf file? Because restarting the server just  inputs its old ip into the file.. I read something that i have to input  the nameserver 8.8.8.8 into my router and should just use dhcp4: yes..  But using dhcp4: yes does not give an ip to my ethernet port..

---

### Post by chili555 on 2023-01-15
Your yaml still varies in several places from the example, most especially the route stanza. Please fix it and run:

```
sudo netplan --debug try
```Please show us the result.You needn't change resolv.conf at all.

---

### Post by kingslavcho on 2023-01-17
After fixing the yaml file i executed: sudo netplan --debug try and this is what i got:

[IMG][[IMG]https://i.postimg.cc/Vd5NSWBD/netplan-debug.jpg[/IMG]]("https://postimg.cc/Vd5NSWBD")[/IMG]

And this is the yaml file:

[IMG][[IMG]https://i.postimg.cc/D8Dw14xF/yaml-file.jpg[/IMG]]("https://postimg.cc/D8Dw14xF")[/IMG]

I am going to ask several questions:

Why should i insert the nameservers of google in the yaml file?
Should i add the google nameservers into my router and try again (router address is 192.168.1.1)
What does the route line mean? How to routing will go? Should i insert my router address there?

Thank you again!

---

### Post by chili555 on 2023-01-17
> Why should i insert the nameservers of google in the yaml file?You shouldn't, if you prefer your router. Google's DNS nameservers are commonly used as examples. I suspect they are used as examples simply in case a new user blindly copies the example configuration. Using known working nameservers will still likely work.

Many users set Google nameservers because they are usually faster that those used in your router. Your settings in the yaml file set the Google nameserver as a failover; that is, if 192.168.1.1 doesn't return an answer in a reasonable timeout, the system will go on to 8.8.8.8. I think that's a perfectly reasonable arrangement.
> What does the route line mean? How to routing will go? Should i insert my router address there?Routing is the process of path selection in any network. In your case, it tells the system where traffic from 192.168.1.202 goes; to 192.168.1.1, your router.

Your router, in  turn, also has an IP address and a route; typically that provided by your internet service provider (ISP). The specification of the route, 192.168.1.1, is simply a link in the path: your computer <--> router <--> ISP <-->internet. 

Please confirm that the e in eno1 is aligned perfectly with the e in eno2, eno3 and eno4. If so, run:

```
sudo netplan generate
sudo netplan apply
```Did you get the IP address?```
ip a
```Did you connect?```
ping -c3 www.ubuntu.com
```

You may get a big delay in booting as you have specified eno2, eno3 and eno4 to get a DHCP address. They are not, as far as I gather from your original post, connected to anything that can give an address. In order to allow booting to occur without waiting for those interfaces to activate fully, I suggest you add optional: true to those stanzas:

```
eno2
  dhcp4: no
    optional: true

```
...and so on for the others that are not connected. This can always be changed later.

Reference: [https://netplan.io/examples](https://netplan.io/examples)

---

### Post by kingslavcho on 2023-01-18
ok i updated the yaml file with dhcp4: no for the other ethernet ports  but i go error with the optional part and i deleted it and the netplan  generate passed.. Than i tried to ping google.com and ubuntu.com as seen  on the pictures it was not successful.. Also i wonder why it won't ping  even my router - 192.168.1.1? I guess the yaml file is not correct and i  will have to tune it more.. What should i try next? Thank you

dhcp4:no and optional for the other interfaces:
[IMG][[IMG]https://i.postimg.cc/68yYTQ4V/dhcp4-eno2-3-4.jpg[/IMG]]("https://postimg.cc/68yYTQ4V")[/IMG]

netplan generate problem:
[IMG][[IMG]https://i.postimg.cc/CRXJ8Vb3/eno2-3-4-generate-problem.jpg[/IMG]]("https://postimg.cc/CRXJ8Vb3")[/IMG]

Without optional row generate passes:
[IMG][[IMG]https://i.postimg.cc/MX60vGhc/without-optinal-generate-passes.jpg[/IMG]]("https://postimg.cc/MX60vGhc")[/IMG]

generate and apply and last ip a to show ip of the eno1 interface:
[IMG][[IMG]https://i.postimg.cc/Mf6YwZ8Q/generate-apply-and-ip-a.jpg[/IMG]]("https://postimg.cc/Mf6YwZ8Q")[/IMG]

Again i cant ping and don't have internet  because of nameservers :sad:
[IMG][[IMG]https://i.postimg.cc/14BHHFpc/cant-ping.jpg[/IMG]]("https://postimg.cc/14BHHFpc")[/IMG]

Even my router cant be pinged.. 
[IMG][[IMG]https://i.postimg.cc/xcs60m8T/cant-ping-my-router-also.jpg[/IMG]]("https://postimg.cc/xcs60m8T")[/IMG]

Can you please tell me what should i do? This is madness..

---

### Post by chili555 on 2023-01-19
First of all, the optional: true error is merely an indentation error. Rather than delete it, I recommend that you fix it. Please double-check your spacing.

The little indicator ^ is at the colon. Please try again with:

```
optional: true
```  That is with just one space after the colon. Then try again:

```
sudo netplan generate
```

Is there still an error? Try with two spaces:

```
optional:  true
```

And follow with:

```
sudo netplan generate
```

One of these will generate without error. Whichever produces no errors, follow with:

```
sudo netplan apply
```As to the connection problem, there are several steps that I suggest. First, please verify that the gatewat (router) address is actually 192.168.1.1. Check on any other device on the network. Be certain that it isn't 192.168.1.254 or 192.168.0.1 or some other.

Second, check in the administrative pages of the router. Is the address you've selected, 192.168.1.202, outside of the DHCP pool in the router? Most routers have a Clients listing. Please verify that the x.202 address in not in use by some other device on the network.

Is the cable a known good cable? Are the ethernet LEDs blinking on your server? Are they blinking on the router?

What does this tell us?

```
sudo ethtool eno1
```In particular, does it report Speed, Duplex and Link Detected? There is no need to post a photo; just tell us the result.

---

### Post by kingslavcho on 2023-01-21
I made my connection but i had the weirdest experience ever.. I can not understand how it works but it works..
To explain:
The primary router address is 192.168.1.1 and i have other routers but the DHCP is only working on the primary router.. The server is connected with cable but from a second router that extends the primary network (DHCP on second server is not enabled). The primary router model is ASUS RT-AX55. The weird thing is that when you try to to set static ip address on a some PC (i tried with Windows and Linux) with the enabled DHCP server the PCs do not have internet connection but they see the internal routers and PCs. Hear me now.. I turned off the DHCP server on the primary router and now all the devices had to manually assign an ip address - went to check the server and can you imagine - the server had its internet connection working - but now i had problems with my other PCs that they did not have internet connection - so i started to manually assign the IP addresses for the PCs - for the mobile devices i had to turn on an option called "Enable Manual Assignment" so i can assign IP to the mobile device from the router itself.. I could not understand why the ASUS router did not support manually assigning IPs and DHCP assigning at the same time.. Than i turned on the DHCP again because i have 40 devices connected on my network and it was really exhausting to set manually IP for every device but the option "enable manual assignment" is still turned on.. Went back to the server and it still has the internet connection.. Previously with yaml file set to static and DHCP turned on on the router it did not work but magically it works now.. Can you explain me what could be the problem so my server did not work? Was it a router problem that something might got stuck and the manual and DHCP IP assigning was not working or it was something else?
I would also like to send my kindest regards to you [**[COLOR=#DD4814][B]chili555**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=35909") for helping me with my linux server to set up the network! Very much thank you!

P.S i must get the right answer for this that happened 15 minutes ago 0_o

---

