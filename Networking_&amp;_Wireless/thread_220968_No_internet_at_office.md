---
title: "No internet at office"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by gigaferz on 2006-07-22
Hello.
At my house I have yahoo dsl and it works fine but at the office it doesnt work (ubuntu/kubuntu Live cd)

In windows  I Do the one or manu following things (not in that order,im just typing as I remember).

1st..turn off the router, then after a min. turn it on.

2nc..  ctrl panel, network connections..properties (rightclick)
          and then click Repair 

3rd.  The same thing but I disable the connection..then reenable it.

4.- Try with many settings, ctrl panel, network connection, bring iup the properties. On the device there is a configure button, in there I go to the advanced tab , And i go straight to "LINK Speed & Duplex"..and change it until I get the browser to work properly.

Thats  easy right? ..Now..How do i do the last step in Ubuntu,(kubuntu)?

so far I found about the ethtool.. and tried this
sudo ethtool -s eth0 speed 10 duplex half
and when i just do  ethtool eth0  shows that the speed is still 100mbs full duplex...

Can anyone help??

---

### Post by andre-w on 2006-07-22
Hi gigaferz,

I am an "average-to-basic" Ubuntu user with a similar problem. Right now I am not able to help you, but I think if you give a little more information, someone will.

What kind of network you use at your office? Ethernet or wireless?

What do you see when you open Ubuntu's Network settings? (System > Administration > Networking)

I am using "former-SBC-now-AT&T" Yahoo DSL, so check also my "currently-in-progress" thread: [http://ubuntuforums.org/showthread.php?p=1286181](http://ubuntuforums.org/showthread.php?p=1286181)

Regards,

Andre W.

---

### Post by mips on 2006-07-22
More info, more details....

---

### Post by gigaferz on 2006-07-22
Hi.

Well is ethernet.

I tried KUBUNTU and Ubuntu  on an OLD p3800mhz gateway 
287 mb ram, link  lne 100tx sys ethernet adapter ..and the internet works!!
i tried
dmesg |grep eth0
and found out  that its full duplex (however i dont know the speed)
and there is no IVp6 router

i tried to run ethtool but it says there is no information available..

So the problem is on the other computers..
so far I tried turning off ivp6, editing resolv.conf
and nothing yet..

---

### Post by gigaferz on 2006-07-24
Its working!!!!

However ethtool did not work

I did it usin mii-tool.

I changed the settings to 10mbp Half duplex...

I think you should try this step before anything else...

I found a guide that some python guy did , I'd like to find something like that for this new ubuntu release..Anybody knows what im talking about???

---

