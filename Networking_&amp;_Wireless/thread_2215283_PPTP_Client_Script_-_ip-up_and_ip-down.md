---
title: "PPTP Client Script - ip-up and ip-down"
date: 2014-04-05
forum: Networking &amp; Wireless
---

### Post by Owen_Murphy on 2014-04-05
I'm connecting to a VPN server using PPTP Client (also call PPTPD?) and I've finally gotten everything configured where it will connect and route all my traffic to the VPN server when I type "sudo pon vpn-test" in the terminal.  (vpn-test is the name I created)

Right now I'm trying to get it to run scripts when I connect or disconnect from the VPN, but I can't get it to work.  I'm sure it's something pretty simple that's I'm missing, since I've never actually tried to create a script before.

Here's what I have:
/etc/ppp/ip-up.local:
```
/etc/ppp/ip-up.d/vpn-test.sh
```

/etc/ppp/ip-up.d.vpn-test.sh
```
notify-send "TEST"
```

I'm just trying to test whether or not the script works by sending a notification that says "TEST".  I've read that, while the "ip-up" script is executed when you first connect, you should put any custom script in ip-up.d and call them in ip-up.local.  I'm not sure how accurate that is, or if it even pertains to my situation.  I am what one might call a n00b when it comes to both Linux and networking.

In case it matters, here's what I have for my PPTP configuration files:
/etc/ppp/options.vpn-test
```
lock
noauth
nodetach


refuse-pap
refuse-eap
refuse-chap
#refuse-mschap

nobsdcomp
nodeflate
novj

require-mppe
nomppe-stateful
require-mppe-128

usepeerdns

defaultroute
replacedefaultroute
```

```
remotename vpn-test
linkname vpn-test
ipparam vpn-test
pty "pptp <vpn address> --nolaunchpppd "
name <"username">

file /etc/ppp/options.vpn-test
```

Any help would be appreciated.

Thanks

---

### Post by Owen_Murphy on 2014-04-06
I figured it out.  In the options file, you need to put: ```
connect <ip-up script>
disconnect <ip-down script>
```

I  used /etc/ppp/ip-up for the connection script and /etc/ppp/ip-down for  the disconnection script.  When they are executed, they call ip-up.local  and ip-down.local, respectively.

---

