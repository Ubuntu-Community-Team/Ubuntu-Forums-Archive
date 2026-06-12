---
title: "Kea control agent failing to start"
date: 2024-06-09
forum: Networking &amp; Wireless
---

### Post by bradley-coder7 on 2024-06-09
Before I get started, I just want to note that I got things working. The point of this post is to inquire if anyone knows why it stopped working in the first place.

I've been testing some configs for Kea with the high availability hook for a few months now. I started in Ubuntu 22.04, but because the 24.04 release was imminent, I delayed deployment of the production system until after the release so that the system would be running the latest and greatest. I started running my tests on 24.04 as soon as it hit beta. Everything was working fine. I have been using Ansible to make sure my deployments in the test environment were consistent. Then, seemingly randomly, on the day of deployment (2024-06-07), the Kea Control Agent failed to start on both servers. I had run a fresh install in my test environment with exactly the same configs two days before deployment and I had confirmed it was working just fine. But on the day of deployment, it started complaining that the systemd condition wasn't satisfied because it required the /etc/kea/kea-api-password file to be present, so it refused to start. That file had never been present the entire time I was testing, but Kea and its HA hook had been working fine until 6/7.

Having the control agent password protected is a good thing, so I'm fine with the fact that it forced me to go enable it. The control agent in my environment (testing and production) uses a direct patch cable from the primary server to the standby server using a non-routable /29 subnet, so I was comfortable running the control agent without authentication. But I am very confused as to why it allowed me to run it without the password file and related config parameters on one day, and then stopped the next.

The testing and production deployments were done entirely through automation and were using identical automation scripts. The test environment mimics everything in the production environment. So the only thing I can think of that could have changed is a package update, because my playbook updates and upgrades everything when it runs. But I'm not finding anything about updates to the relevant packages anywhere near the dates when it went from functional to non-functional. So I'm really kind of baffled. But if the change was from an update, I would still find it frustrating that an update completely breaks a previously functional (and relatively simple) configuration.

Just in case anyone else runs into this, I'll provide the solution I used.

I added the following to kea-ctrl-agent.conf:
```

"authentication": {  "type": "basic",
  "realm": "kea-control-agent",
  "clients": [ {
    "user": "admin",
    "password-file": "/etc/kea/kea-api-password"
  } ]
},

```
Then I added this to each peer in the kea-dhcp4.conf:
```

"basic-auth-user": "admin",
"basic-auth-password-file": "/etc/kea/kea-api-password",

```
Then I saved a random ASCII string to /etc/kea/kea-api-password and set the permissions to root:_kea 0640

---

