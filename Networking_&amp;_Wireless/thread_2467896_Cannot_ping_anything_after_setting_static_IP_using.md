---
title: "Cannot ping anything after setting static IP using Netplan"
date: 2021-10-11
forum: Networking &amp; Wireless
---

### Post by l1nuxdb on 2021-10-11
Hello.

I think I am going crazy right now. I know that I used to be able to set a static IP in Ubuntu with no issues. I have tried 18 and 20 and still not able to get this to work. If I use DHCP during setup everything will work fine however when I set static IP using /etc/netplan/00-installer-config.yaml the only device I can ping is the NIC itself.

I have tried this yaml code and some other variations as well. I even run netplan generate --debug and there are no issues. I make sure to run netplan apply when done updating the yaml file.

Can someone please help me figure this out. I have spent the last 4 hours straight trying to get this to work. I will update with whatever content that you need from me.

Here is the output of "ip a" after I set the yaml file and everything looks good.

network:
  ethernets:
    ens18:
      addresses: [10.1.60.100/24]
      gateway4: 10.1.60.1
      nameservers:
        addresses: [10.1.101.11, 10.1.101.12]
  version: 2

---

### Post by The Cog on 2021-10-11
Please post that yaml file content inside code tags. The posting above is a massive syntax error because the indentation is wrong. 
When posting, you can hit "Go Advanced" at the bottom and then you get a lot more editor buttons including a '#' button that places code tags round the highlighted text. You also get a preview button so you can check before posting.

Please also post the result of the command "ip address" both having used DHCP and having used the yaml file, so we can compare the results.
Also, make sure that the address 10.1.60.100 is not already in use by another machine.

---

### Post by l1nuxdb on 2021-10-11
I figured this out. Was using the damn wrong gateway address. Sorry to waste your time. How can I delete this?

---

### Post by The Cog on 2021-10-11
I don't think you can. It still serves as an example of something to check if you have this problem.

---

