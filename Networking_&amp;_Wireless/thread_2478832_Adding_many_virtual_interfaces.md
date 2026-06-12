---
title: "Adding many virtual interfaces"
date: 2022-09-06
forum: Networking &amp; Wireless
---

### Post by hmortensen83 on 2022-09-06
Hi

I have a 22.04 server, where I have to add a lot of VLAN interfaces and enslave them to a bridge.

I made a script to run lines like below for 500 interfaces, but the server uses loads of CPU and stalls for 5-10 minutes.
sudo ip link add link eno2.1234 eno2.1234.2 type vlan proto 802.1Q id 2
sudo ip link set eno2.1234.2 up
sudo ip link set dev eno2.1234.2 master br4455

What would be a better way to add them? Create a netplan file, apply it and then delete the file again?

Best regards
hmortensen

---

### Post by SeijiSensei on 2022-09-06
I did this once using ifconfig. Something like this

```

for ((i=1;i<=250;i++)); 
do 
   ifconfig eth$i 10.10.10.$i
done

```
With 500 interfaces, you'll have IP addressing problems since a class-C can only range from 1-254. You could use a class-B address (like 172.16.0.0/16), but the code would be more complex.

You'll need to install the "net-tools" package to do this since ifconfig is no longer included with stock Ubuntu.

---

