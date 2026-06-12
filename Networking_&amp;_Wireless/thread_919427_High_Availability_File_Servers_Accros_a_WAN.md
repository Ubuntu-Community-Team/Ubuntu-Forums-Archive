---
title: "High Availability File Servers Accros a WAN"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by kd7gab on 2008-09-14
Hello everyone,

I am searching for a solution for my company. We are moving and will be occupying two buildings separated by a couple of miles. The plan is to deploy a file server at each building and synchronize the files between the servers. This will give us not only faster file access but also a significant level of redundancy. Ultimately, we would prefer to accomplish Synchronous locking between the servers. 

So far the best solution that I have been able to find does not really fulfill our needs as it is a cycling replication system without locking. We'll be starting with only a few hundred gigs of data and less than 100 users but we expect to see dramatic growth in both users and data. Our users tend to access the same files between different departments so locking is a pretty high priority. We are not doing any web hosting, so the servers are serving data to in house users only. The machines will be quite fast and running Ubuntu. So far the prospective wan link will most likely be in the range of 15 to 30 Mbps, possibly faster depending on availability. Does anyone have any helpful ideas or solutions that you can recommend? 

Thank you all,

Jon

---

