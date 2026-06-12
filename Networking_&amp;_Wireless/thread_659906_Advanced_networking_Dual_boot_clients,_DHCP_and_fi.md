---
title: "Advanced networking: Dual boot clients, DHCP and fixed IP addresses"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by mdrescher on 2008-01-06
Hi folks,

hope you can help me out with this one:

I have a LAN with several client machines, totalling to 6 (currently):
[LIST]
[*]2 Apple Laptops
[*]4 dual boot (Windows/Linux) PCs
[/LIST]

I have got a DNS server configured (ISC Bind9), and a DHCP server (ISC Dhcp3).

All works fine so far, I have clients configured with fixed IP addresses via the DHCP server (to have client deployments being as generic as possible), etc.

I am still bugged by the clients booted into Windows being able to access the Internet just like that. To solve this, I thought of configuring the network as follows via DHCP:
[LIST]
[*]Apple laptops get their IP addresses as before
[*]PC clients booted into Linux get their IP addresses just like that
[*]PC clients booted into Windows get an IP address from a special range
[/LIST] 

That way I can restrict Internet access for the Win clients in an IP basis, e.g. allow only windows update etc.

Now, how do I do that? I tried to use the DHCP option "dhcp-client-identifier" which I believe is a free-form text field that I can use on the clients (configure special strings per client) and on the DHCP server to match on that option and assign a special IP address.

I have tried so far to configure Windows 2000 with a client identifier, according to a MS Knowledge Base article, but I think Windows does only support hexadecimal values.

But I also believe I use the option wrongly in my DHCP server configuration:

```

host Doodle-Win {
        hardware ethernet       00:11:22:33:44:55;
        option dhcp-client-identifier "Doodle-Win";
        option host-name        "Doodle";
        fixed-address           192.168.0.111;
}
host Doodle-Linux {
        hardware ethernet       00:11:22:33:44:55;
        option dhcp-client-identifier "Doodle-Linux";
        option host-name        "Doodle";
        fixed-address            192.168.0.150;
}

```

The rest of the network configuration is set elsewhere in dhcpd.conf and works just fine.

However, the clients seem not to pick up the settings special to them - but I have tested clients booting windows so far, only.

Can anybody shed some light on how I should use this DHCP option?

Cheers,
Michel

---

