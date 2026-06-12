---
title: "traceroute with contradictory results"
date: 2016-11-14
forum: Networking &amp; Wireless
---

### Post by sebastiaopburnay on 2016-11-14
Hi!

I'm trying to automate a script based test to check whether my end-to-end route uses the main GateWay, or the backup gateway.

The strange thing is that:
**I)  **when running my '**traceroute <destiny-IP>**' command in tghe CLI, I always get the expected result (either when I'm using the main or backup route)
**II) **when I use a Cron job, running a shell script (shown below) the output of traceroute written to file does not match with the one I run directly in the CLI 
```

# My Shell Script
#
#!/bin/bash
`traceroute 'destiny-IP' > /routes/route-to-X.txt`


# My Cron Line
#
# */5 * * * * sh /routes/cron_for_route.sh

```

I've tried clearing the ARP cache, but the result is still wrong with the shell script.

Does that ring a bell to you. It is seemingly a verry stupid behaviour

Thank you berry much

---

