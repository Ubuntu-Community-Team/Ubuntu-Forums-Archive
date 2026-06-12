---
title: "ssh access"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by insurin on 2008-06-11
I ssh to home from work but I have just changed from port 22 to 5900 to try and reduce ssh attacks, I have set my router at home to forward traffic at port tcp 5900 to my kubuntu box 8.04. It's a standard ssh config. I cannot connect now, I get an error from putty.......

"server unxpectedly closed network connection" 

but if I telnet 

telnet ipaddress 5900

I get the ssh banner stating that it's openssh etc.

Have I missed something here? I only forwarded TCP 5900 no UDP but don't think it's this.

---

### Post by chili555 on 2008-06-11
I wonder if you need to alter */etc/ssh/ssh_config* to change this:```
#   Port 22
```to this:```
    Port 5900
```I have never tried this, so I'm guessing a bit. Also, are you specifying 5900 in the ssh command?```
ssh -l user 274.what.ever:5900
```

---

### Post by Houman on 2008-06-11
the file "/etc/ssh/ssh_config" should not be changed because as far as the ubuntu machine is concerned ssh server is still running on port 22 (since insurin mentioned that the router is forwarding port 5900 to his ubuntu machine's port 22)

But i cant offer any suggestions , if telnet is working then it should be fine, are you sure you entered all the settings correctly in putty? dont forget to specify port 5900 in putty;


regards
H

---

### Post by insurin on 2008-06-11
I have edited sshd_config and specified listen address to 5900. I have verified this by restarting ssh and doing a netstat and I can see 5900 is now listening instead of 22. I have set my router so that requests for port 5900 are forwarded to the internal IP address of my ubuntu box and at port 5900.

Sitting at the ubutnu box now I can ssh to myself on port 5900. The fact that I could telnet to my box from work and I received the ssh banner leaves me to believe there is no issue with my port forwarding. I had done some updates but not rebooted, I will report back tomorrow 1pm gmt with the results.

---

### Post by insurin on 2008-06-12
I am back in work now and it's working, I did a reboot last night so I am putting it down to the updates I had done earlier that morning being the reason it was not working.

vielen dank

---

