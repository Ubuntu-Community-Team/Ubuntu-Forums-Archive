---
title: "help with firestarter and ics"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by manowar689 on 2009-02-25
ok i am having some trouble with firestarter and ics so i will just go a head and explain my complete cofig from start to finish 

i have an acer aspire one which i would like to use to ics wireless from the laptop to the wired on the comp so i will give the config now 

pc1 : 
OS: windows xp 
ipconfig: 
ip add:       192.168.0.2 
subnet:       255.255.255.0 
gateway add:  192.168.0.1 

this computer is directly connected to the acer aspire ones eth0 whos config is 
 
AAO: 
OS: ubuntu 8.10 
ifconfig 

ath0(wireless) 
autoconfig with DHCP 
and configured with a DMZ 
(demilitarised zone)

eth0 (wired) 

ip add:       192.168.0.1 
subnet:       255.255.255.0 
gateway add:  (blank) 

so the setup is like this 

pc1------------------ AAO ))))))))))))))))))))))))) router 

i can access the net and ping the gateway address on pc1 put when i try to play games on gamespy or any general port config it wont work at all i think this is to do with the ICS can anyone shed some much needed godly light lol 

thx in advance

---

### Post by llamabr on 2009-02-25
Hi.  No offense, but it looks like you're no longer an absolute beginner.

If no one comes to your rescue, you may think about taking this to the appropriate forum, where someone with expertise can help you out.

---

### Post by Thelasko on 2009-02-26
Firestarter is no longer supported upstream and has quite a few bugs.  I recommend GUFW instead.

---

### Post by Bearly Able on 2009-02-26
I'm sure I'm just being dim, but I can't find anything called GUFW in synaptic.

---

### Post by ptn107 on 2009-02-26
It's in the universe repository.  Make sure you have that enabled in System -> Administration -> Software Sources.

---

### Post by Bearly Able on 2009-02-26
Thanks, but I do have the universe repository enabled, and can't find GUFW with synaptic.  Is it perhaps not available for 8.04?

---

### Post by SamNSane on 2009-02-26
> **Lesley Lutomski said:**
> Thanks, but I do have the universe repository enabled, and can't find GUFW with synaptic.  Is it perhaps not available for 8.04?

You can find gufw here:

[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

I normally try to avoid installing stuff that isn't in the repositories, but sometimes need for functionality triumphs over caution. I've been using gufw on several Hardy Heron systems. An earlier version (0.26?) gave me some problems, but the current 0.27 version seems to be pretty reliable.

Because it's not in the repositories, you'll need to check back at the home site occasionally to see if there's an updated version you need to download and install.

---

### Post by Thelasko on 2009-02-26
Sorry, I forgot it's not in the default repositories for Hardy.  It was added to the repositories for Intrepid.  You can also get it in Hardy's backports repository.

---

### Post by Bearly Able on 2009-02-26
Thanks, guys, I'll check it out.

---

### Post by kansasnoob on 2009-02-26
The GUFW .deb is perfectly safe!

[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

---

### Post by manowar689 on 2009-02-28
Sorry for the late reply and thx again for the tips i will be sure to check gufw as soon as and reply wit progress or lack of Lmao and thx for sayin im not a noob means alot Lmao

---

### Post by manowar689 on 2009-03-01
i have installed gufw and it doesnt seem to have amenu to allow ics which is the only reason i would need it ya know can anyone help ???

---

### Post by SamNSane on 2009-03-02
> **manowar689 said:**
> i have installed gufw and it doesnt seem to have amenu to allow ics which is the only reason i would need it ya know can anyone help ???

This doesn't look particularly hopeful:

[https://blueprints.launchpad.net/gui-ufw/+spec/gufw-internet-connection-sharing](https://blueprints.launchpad.net/gui-ufw/+spec/gufw-internet-connection-sharing)

The basic firewall in Ubuntu (iptables) can, of course, be configured to enable a system to perform ics, but we're not talking about a basic point-and-click job here.

---

### Post by Thelasko on 2009-03-02
By ICS you mean "Internet Connection Sharing"?  That's called a "bridge" in Ubuntu.

---

### Post by manowar689 on 2009-03-02
well i have been looking into bridgeing lately havent found many how tos or anything like that could you maybe explain how to do this

---

