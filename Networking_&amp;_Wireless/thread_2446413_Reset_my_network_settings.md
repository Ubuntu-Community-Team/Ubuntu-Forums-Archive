---
title: "Reset my network settings"
date: 2020-06-30
forum: Networking &amp; Wireless
---

### Post by crooklar on 2020-06-30
ive have a server running ubuntu 18 for a few months, installed and tried to configure things how i would like - mainly by following online guides.

in that process, i think i have messed up my network settings and have a number of things id like to fix.

everytime i restart my box i have to enter: 

```
sudo iptables -P INPUT ACCEPT && sudo iptables -F INPUT  && sudo iptables -P OUTPUT ACCEPT && sudo iptables -F  OUTPUT
```

This line was used following me installing NordVPN and the line was  given to me by one of their agents to get the machine working with  NordVPN, i no longer use NordVPN.

I cannot use SSH on a local machine following a reset until i enter this, i dont think i should have to enter this every time - how do i fix this?

---

### Post by TheFu on 2020-06-30
Wow!  That agent just wanted you to go away. I suppose that would let their VPN work ... by flushing all firewall rules on the system. Did they have you run some iptables commands before providing that line with 4 commands to effectively stop iptables from doing anything useful?

sudo iptables -L

So you should dump all the firewall rules and start over. It isn't like what you have is being used. I'd get a list of the rules setup by iptables and ufw, save those off somewhere for reference and start over.

If all you want is to allow inbound ssh and outbound everything else, then I'd do
```
sudo ufw enable
sudo ufw allow ssh
sudo apt install fail2ban
```
This assumes that any iptables settings have been flushed.

If you want a more complex firewall solution, there are some posts in these forums about that.  You can look up CSF scripts and see if that would be helpful.

---

