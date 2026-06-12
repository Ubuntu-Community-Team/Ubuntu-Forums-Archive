---
title: "I'm Not Sure How To/How I Should Configure Firestarter"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by TortureQueen on 2010-07-27
Hi, all.  I am not sure of how to--**and how I should** configure Firestarter.  If anyone has any tips or input for me, that would be greatly appreciated.  In the mean time, I will do some reading on firewalls and Firestarter, and I will also browse the forums for more information.  I am a total newbie with Ubuntu, but I am determined to keep it as my OS. . One question.  How secure are the default settings of Firestarter?

---

### Post by endotherm on 2010-07-27
well, first off, firestarter is an acceptable solution, it is no longer well supported and is widely considered a dead project.
the new tool-du-jour is called gufw, and while it lacks some features firestarter has, it does clarify what the tool is for.

both gufw and firestarter are configuration frontends for iptables (well, gufw is a ufw front, and ufw is a cli front for iptables, which is a frontend for the kernels netfilter...), so you should only need to run them when you need to modify your firewall configuration. that took me a while to figure out.

Ubuntu does not need a firewall by default, since it has no network services listening for input, and thus no open ports. the firewall is useful if you want to open a particular port but still maintain some security on it, like ensuring that the connection comes from inside your network, etc. if you want to open a port and not restrict it further, then you still don;t need a firewall.


so all that said, my recomendation for firewall config is always to deny all unsolicited incoming connections, and to specifically open ports that remote programs need to access. you can leave the outbound policy permissive (allow all outgoing connections) unless you are using apps you don't trust, in which case you should block their ports outbound. 

iptables is stateful, so a response from outside to a connection you initialted from the inside will be allowed, but unsolicited connections will be dropped.

hth

---

### Post by Rubi1200 on 2010-07-27
Hi,
read this please:
 
>  
A source of confusion sometimes occurs when users feel the need to be running firestarter/Guarddog for their firewall to be active. **This is untrue !** Keep in mind that these applications are not firewalls, but rather configuration tools for ip tables. These applications should be run *only to configure your firewall*. Once configured, IP tables (the actual firewall) is active (at boot) *without having to run firestarter/guarddog*. firestarter will monitor traffic, but it runs as root and there are better monitoring programs, so configure you firewall, shut down firestarter/grauddog, and let IP tables do the rest

 
Here is the source:
 
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
 
The security sticky by bodhi.zazen makes for essential reading.
 
Read the section on firewalls. By the way, if you have a router with firewall you probably do not need an additional firewall.
 
Good luck!

---

### Post by TortureQueen on 2010-07-27
> **endotherm said:**
> well, first off, firestarter is an acceptable solution, it is no longer well supported and is widely considered a dead project.
the new tool-du-jour is called gufw, and while it lacks some features firestarter has, it does clarify what the tool is for.

both gufw and firestarter are configuration frontends for iptables (well, gufw is a ufw front, and ufw is a cli front for iptables, which is a frontend for the kernels netfilter...), so you should only need to run them when you need to modify your firewall configuration. that took me a while to figure out.

Ubuntu does not need a firewall by default, since it has no network services listening for input, and thus no open ports. the firewall is useful if you want to open a particular port but still maintain some security on it, like ensuring that the connection comes from inside your network, etc. if you want to open a port and not restrict it further, then you still don;t need a firewall.


so all that said, my recomendation for firewall config is always to deny all unsolicited incoming connections, and to specifically open ports that remote programs need to access. you can leave the outbound policy permissive (allow all outgoing connections) unless you are using apps you don't trust, in which case you should block their ports outbound. 

iptables is stateful, so a response from outside to a connection you initialted from the inside will be allowed, but unsolicited connections will be dropped.

hth

 Thank you so much, Endotherm.  Your reply does raise a question for me.  Right now, I do not know how to deny all unsolicited incoming connections.  I want to learn how to do that.

---

### Post by TortureQueen on 2010-07-27
> **Rubi1200 said:**
> Hi,
read this please:
 

 
Here is the source:
 
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
 
The security sticky by bodhi.zazen makes for essential reading.
 
Read the section on firewalls. By the way, if you have a router with firewall you probably do not need an additional firewall.
 
Good luck!

 Thank you so much for using that quote!  Just that little bit explains so much.  I will take a look at the posts you suggested.  Thank you

---

### Post by endotherm on 2010-07-28
> **TortureQueen said:**
> Thank you so much, Endotherm.  Your reply does raise a question for me.  Right now, I do not know how to deny all unsolicited incoming connections.  I want to learn how to do that.
gufw there is a checkbox (or radio button) to control whether you are denying or allowing by default. it's been some years since i used firestarter, but i recall a similar checkbox on the main page. if not, check in preferences and you should find it.

---

### Post by TortureQueen on 2010-07-31
Thank you Endotherm.  I have switched to GUFW.

---

### Post by Paqman on 2010-07-31
> **TortureQueen said:**
>  Right now, I do not know how to deny all unsolicited incoming connections.

The default configuration in Ubuntu does exactly that. There are no service listening on any port, so anybody trying to connect will find no way in. You don't need to take any action.

---

