---
title: "2 WAN Connections-- Would like to direct traffic by PORT"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by pcpete on 2007-06-29
Hello all, and thanks for the help you have given me in the past. I am looking for a solution for a small office using two WAN connections. Here is the scenario: 

Clients typically browse the internet (port 80, 443), use Citrix client for remote servers (port 1496?), VPN for remote email access (port 2223) and use Microsoft Exchange. There are also a few other programs, but these are not currently significant. **I am looking for a means of directing web traffic over our Comcast Cable line, and use a NEW MPLS connection for all other programs..**

Here is a general network diagram of the systems in place: 
[IMG]http://img528.imageshack.us/my.php?image=springfieldddwrtnoipfi9.jpg][IMG]http://img528.imageshack.us/img528/7043/springfieldddwrtnoipfi9.th.jpg[/IMG]

I have plenty of old PIII systems laying around that can be used as firewalls..... And yes, a computer with 3 NICs is fine with me. I have fresh Ubuntu systems ready in an environment riddled with Windows computers :) 

I have looked at FireStarter, ShoreWall and IPTables as a means of redirecting the traffic. Is there an easy way of accomplishing my goal? Otherwise an order for SonicWall will be in place 

Let me know if there are any specific Qs!

Thanks

---

### Post by pcpete on 2007-06-29
I'm sorry, don't why the diagram wasn't intserted... here's a link:

[[img=http://img341.imageshack.us/img341/1175/springfieldddwrtnoiphm1.th.jpg]](http://img341.imageshack.us/my.php?image=springfieldddwrtnoiphm1.jpg)

Needless to say, I was checking out some cool IPtable tricks, but this didn't exactly answer my question and it was mad complicated. 

[http://tweako.com/iptables_explained_part_3_creating_a_complex_iptables_script_easily](http://tweako.com/iptables_explained_part_3_creating_a_complex_iptables_script_easily)

---

### Post by pcpete on 2007-06-29
Anyone have ideas? I'll start relooking into this and post if I find a solution... I think IPtables is the way to go, but I don't have the know-how to put it all together. 

Thanks!

---

### Post by pcpete on 2007-07-03
Starting to look into this again-- if no go, I'm afraid another SonicWall is going to be purchased :)

---

