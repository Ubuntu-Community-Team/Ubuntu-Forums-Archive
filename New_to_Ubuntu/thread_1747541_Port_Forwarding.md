---
title: "Port Forwarding"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by Arwen17evenstar on 2011-05-02
I have a linksys router and I've read a ton of guides about how to port-forward. So what I'm doing should work, but for some reason its not working. I know ISPs sometimes block port 80, but I can't seem to get any port to say its open. I tried using port 6112 thinking that surely the ISP wont be blocking that port because it is used by World of Warcraft people. But it didn't work.
I even tried sticking my computer in the DMZ and it still said ports were closed. why won't this work? It should be as simple as pie to forward a single port.

My internal ip address is 192.168.1.123 and that's what I'm using in my router port forwarding settings.
I'm using two different websites to scan my external ip looking to see if the ports are open.
[http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)
[http://www.t1shopper.com/tools/port-scan/](http://www.t1shopper.com/tools/port-scan/)

I just want a port to say its open instead of "closed closed closed".
Is there a specific port I should try that the ISP would be sure to have open?
Shouldn't sticking my computer in the DMZ make all computer ports not already being blocked by the ISP open?

and just for the hell of it, I tried turning off windows firewall as well to see if that was blocking the port somehow.
Is there something else that could be blocking the ports??

oh and sorry I am doing this on windows at the moment. The eventual plan is to do it on a ubuntu server if I could just get a single port open on my windows computer.

Update: ok DMZ seems be working now. and it looks like my ISP blocks a ton of ports, but I did manage to find at least one open now. So now I know the port forwarding on the router is indeed working.

---

