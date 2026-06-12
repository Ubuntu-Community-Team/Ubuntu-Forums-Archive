---
title: "How to setup UFW to allow local Kubernetes ?"
date: 2020-07-17
forum: Networking &amp; Wireless
---

### Post by such-pirate on 2020-07-17
Hello,

I am currently trying to learn Kubernetes and decided to give a try to microk8s.
The problem is that I am stuck because my UFW rules are blocking microk8s.

I am using a fresh install of Ubuntu 20.04.
Bellow are the command I used to setup a VPN kill-switch (Followed this guide: [https://gist.github.com/Necklaces/18b68e80bf929ef99312b2d90d0cded2](https://gist.github.com/Necklaces/18b68e80bf929ef99312b2d90d0cded2))
```

sudo ufw default deny outgoing
sudo ufw default deny incoming
sudo ufw allow out on tun0 from any to any
sudo ufw allow out 1198/udp
sudo ufw allow in 1198/udp
```

Right after that, I did install microk8s via snap, install the dashboard and see what is the ip of the dashboard:
```

sudo snap install microk8s --classic --channel=1.18/stable
microk8s enable dashboard dns
kubectl get all --all-namespaces
```

When I open Firefox to access the dashboard via the IP I see in the output (10.152.183.90), it is unable to load the page: "Unable to connect".
I thought the problem must be coming from UFW, so I did temporarily disable the firewall and tried to access the page.
Without the firewall enabled, it works fine, I can access the dashboard.

Right after that I did some research, I found some post about similar issues.
It seems that I should unblock a few ports for Kubernetes, and I did add these rules:
```
$ sudo ufw allow 179/tcp
$ sudo ufw allow 4789/tcp
$ sudo ufw allow 5473/tcp
$ sudo ufw allow 443/tcp
$ sudo ufw allow 6443/tcp
$ sudo ufw allow 2379/tcp
$ sudo ufw allow 4149/tcp
$ sudo ufw allow 10250/tcp
$ sudo ufw allow 10255/tcp
$ sudo ufw allow 10256/tcp
$ sudo ufw allow 9099/tcp
```

But that did not help, I am still unable to access the dashboard page if the firewall is active.

I also tried adding this rules, but it doesn't seems to help so I deleted this one.
```

sudo ufw allow out from any to 10.152.183.0/24

```

Any suggestions ?

---

### Post by such-pirate on 2020-07-17
I did some more research and found a solution to my problem on this page: [https://microk8s.io/docs/troubleshooting](https://microk8s.io/docs/troubleshooting)

I was just missing a small rule in UFW : 
sudo ufw allow in on cni0 && sudo ufw allow out on cni0

No need to add all the extra tcp ports

---

